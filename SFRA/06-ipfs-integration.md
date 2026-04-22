---
title: 06 - IPFS Integration
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 7/10
tags: [infrastructure, ipfs, storage, technical]
---

## Overview

IPFS provides permanent, censorship-resistant storage by distributing encrypted content across global nodes. Bridge nodes act as lightweight gateways: they accept uploads from the mesh, forward to external pinning services (Pinata/Web3.Storage), and cache locally for fast retrieval. External pinning is mandatory—unpinned content gets garbage collected within days.

**Critical: IPFS is NOT automatically permanent. Content must be actively pinned by 2+ external services.**

---

## Requirements

### Content-Addressed Storage

**Must provide:**
- Files identified by cryptographic hash (immutable)
- Global distribution (thousands of nodes worldwide)
- Censorship resistance (no central authority)
- Integrity verification (hash proves unchanged)

**How IPFS works:**
- Upload content → receive hash (e.g., `QmT5Nv...yCxX`)
- Hash is permanent address
- Any IPFS node can retrieve by hash
- **BUT:** Only if content is actively pinned somewhere

**IPFS Reality Check:**
- Upload ≠ permanent storage
- Unpinned content = garbage collected in hours/days
- Must explicitly pin on multiple services
- Losing all pins = content gone forever

### Bridge Node Implementation

**Architecture: Lightweight Gateway (NOT Full IPFS Node)**

Bridge nodes do NOT run full IPFS daemon. They act as mesh-to-IPFS gateway.

**What Bridge Runs:**
- Simple HTTP service (Go/Python)
- Accepts encrypted uploads from mesh
- Forwards to external pinning services via API
- Local cache only (100GB storage, 30-day retention)
- RAM usage: 50-100MB (vs 300MB for full daemon)

**Why This Approach:**
- 60% less RAM (more stable on Raspberry Pi)
- Simpler = fewer failure modes
- External services handle DHT/distribution
- Bridge focuses on gateway role only
- API-based pinning more reliable than local DHT

**Bridge Upload Flow:**
1. Receive encrypted content from mesh (HTTP POST)
2. Upload to Pinata (primary pinning service)
3. Upload to Web3.Storage (redundancy)
4. Verify both return same hash (integrity check)
5. Cache locally (optional, for speed)
6. Return hash to mesh
7. Broadcast hash through mesh network

### External Pinning Services

**Required: Pin to 2+ commercial services**

**Service 1 - Pinata (Primary):**
- Free tier: 1GB storage, 100MB files
- Paid: $20/month for 100GB
- API-based pinning (reliable)
- Dashboard for monitoring
- Geographic redundancy built-in

**Service 2 - Web3.Storage (Backup):**
- Free tier: 100GB storage
- Filecoin-backed (decentralized)
- API-based pinning
- Built on IPFS + Filecoin network

**Service 3+ - Partner Organizations (Critical Content):**
- Human rights orgs, journalists, legal teams
- Receive monthly list of critical hashes
- Manual pinning via their IPFS infrastructure
- Geographic distribution (different jurisdictions)
- Survives even if commercial services shut down

### Pinning Monitoring

**Bridge must actively monitor pin health:**

**Daily Checks:**
- Verify pins still exist on Pinata
- Verify pins still exist on Web3.Storage
- Alert if any pin lost
- Re-pin immediately if missing

**Dashboard Metrics:**
- Total content pinned
- Content with 2+ pins (target: 100%)
- Content with <2 pins (CRITICAL ALERT)
- Pinning service API status
- Failed pin attempts (retry queue)
- Monthly external verification results

**Automated Monthly Verification:**
- Query: "Does Pinata still have hash XYZ?"
- If missing: Re-pin immediately
- Alert operators if re-pinning fails
- Generate report for partner organizations

### Encryption Before Upload

**All content MUST be encrypted BEFORE IPFS upload**

**Process:**
1. Generate unique AES-256 key per file
2. Encrypt content with this key
3. Encrypt key separately for each recipient (wallet public keys)
4. Upload encrypted blob to IPFS
5. Distribute hash + encrypted keys via Matrix

**Why:**
- IPFS hashes are public (anyone who knows hash can access)
- Encryption provides access control
- Only recipients with key can decrypt
- Adversary controlling IPFS node sees encrypted blobs only

### Mobile Client

**User phones do NOT run IPFS nodes**

**What They Do:**
- Upload: `POST http://bridge-node:8080/upload` with encrypted content
- Download: `GET http://bridge-node:8080/ipfs/{hash}` returns encrypted content
- Bridge handles all IPFS operations

**Why:**
- Full IPFS node uses 100-300MB RAM (too much for phones)
- Battery drain unacceptable
- HTTP client is <1MB, minimal impact
- Bridge does heavy lifting

### Bandwidth Management

**Upload Priority Queue:**
1. Critical: Evidence flagged by user
2. High: All videos (documentation value)
3. Medium: Photos
4. Low: Routine content

**Queue Rules:**
- Process highest priority first
- Limit 1-2 concurrent uploads (prevent overload)
- Drop low-priority if queue >100 items
- Resume interrupted uploads automatically
- Starlink upload: 10-20 Mbps (50% allocated to IPFS)

### Content Retrieval

**Multiple retrieval methods:**

**Local (Fastest):**
- `GET http://bridge-node:8080/ipfs/{hash}`
- Returns from local cache if available
- Falls back to external fetch if not cached

**Public Gateways:**
- ipfs.io/ipfs/{hash}
- dweb.link/ipfs/{hash}
- cloudflare-ipfs.com/ipfs/{hash}
- Works from any web browser
- Shareable with journalists/lawyers

**Any IPFS Node:**
- Anyone running IPFS can fetch by hash
- Global distribution
- Censorship resistant

**All retrieval returns encrypted content. Decryption requires key (distributed separately via Matrix).**

---

## Implementation Notes

**Storage Constraints:**
- Bridge cache: 100GB maximum
- LRU eviction when full
- External services: Pay-per-GB beyond free tier

**Bandwidth Constraints:**
- Starlink: 10-20 Mbps upload total
- Must share with mesh traffic
- Video upload: 5MB = 4-8 seconds at full speed
- Queue builds during high activity

**Network Constraints:**
- IPFS upload requires internet (bridge only)
- Bridge offline = uploads queued locally
- May take hours if bridge down
- Local mesh continues working (IPFS is background)

**Cost Constraints:**
- External pinning: $250-500/year (100GB storage)
- Required for permanence (not optional)
- Budget in annual operating costs

---

## Success Criteria

**Upload Performance:**
- Video pinned to 2+ services within 10 minutes
- Hash returned to mesh after first pin
- Queue handles 10+ simultaneous users
- Failed uploads retry automatically

**Permanence Verification:**
- 100% of critical content pinned to 2+ services
- Monthly verification: all hashes still retrievable
- Automated re-pinning if pin lost
- Zero content loss after 90 days deployment

**Reliability:**
- System tolerates bridge offline (queues uploads)
- System tolerates one pinning service failure
- Content survives bridge destruction (external pins)
- Retrieval works from multiple sources

**User Understanding:**
- Users know content is pinned externally
- Users understand what "permanent" means
- Clear status: "Pinned to 2 services" vs "Cached only"

---

## Status

**Well-Defined:**
- Lightweight gateway architecture specified
- External pinning strategy clear
- Encryption-before-upload required
- Monitoring and verification automated
- Multiple retrieval methods available

**Needs Work:**
- Bridge HTTP service implementation
- Pin monitoring dashboard
- Partnership agreements with external pinners
- Testing with real upload volumes

**To Reach 10/10:** Bridge service deployed, pinning partnerships established, 90-day field validation showing zero content loss.

---

## Dependencies

- **05 Mesh Networking:** Bridge nodes connect to mesh
- **07 Video Handling:** Large files require chunked upload strategy
- **08 Security & Encryption:** Content encrypted before IPFS upload
- **10 Deployment:** Bridge node installation and configuration