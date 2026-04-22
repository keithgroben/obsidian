---
title: 02 - Architecture
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 8/10
tags: [core, technical, architecture]
---

---

## Overview

Three independent layers create resilient communication without traditional infrastructure. Local mesh enables offline communication via WiFi Direct and Babel routing. Bridge nodes provide internet gateways for IPFS uploads. IPFS ensures permanent global storage via external pinning services. Architecture prioritizes decentralization and community ownership over low latency.

---

## Requirements

### **Layer 1: Local Mesh Network (Offline Core)**

**Must provide:**

- Device-to-device communication without internet/cellular
- Multi-hop routing (minimum 7 hops, ~1-2 mile range)
- Automatic route discovery and self-healing
- Store-and-forward for disconnected devices
- Operates offline indefinitely

**Technology:**

- Transport: WiFi Direct (Android native APIs)
- Discovery: BLE (Bluetooth Low Energy)
- Routing: Babel protocol (babeld daemon on relay nodes)

**Node types:**

**User phones (leaf nodes):**

- Send/receive own messages only
- No relaying traffic for others
- Power-efficient by design
- Standard de-googled Android devices

**Relay nodes (always-on backbone):**

- Forward traffic 24/7
- Run babeld daemon
- Raspberry Pi 4 + external WiFi antenna
- Strategic placement (homes, gathering areas)
- 200-500 foot coverage per node

**Hub nodes (optional high-performance):**

- Handle video transfer at critical locations
- Mini PC with WiFi 6
- Deploy 3-5 per network at high-traffic areas
- Same babeld daemon (just faster hardware)

**Coverage calculation:**

- Single hop: 200-500 feet (WiFi Direct range with amplification)
- 7 hops maximum: ~1-2 mile effective range
- Target: 50-100 relay nodes per 5,000-person community
- Dead zones acceptable if <5% of target area

---

### **Layer 2: Bridge Nodes (Internet Gateway)**

**Must provide:**

- Simultaneous mesh participation AND internet connectivity
- IPFS gateway for uploads (not full daemon)
- Software update distribution
- Encrypted VPN tunnel for internet traffic
- Redundancy: Minimum 3 bridges (survives 2 failures)

**Technology:**

- Mesh: babeld daemon (same as relay nodes)
- IPFS: Lightweight HTTP gateway + external pinning API
- Internet: Starlink or cellular backup
- Security: WireGuard VPN tunnel

**Bridge functions:**

**As Relay Node:**

- Participates in Babel routing
- Forwards mesh traffic like standard relay
- Provides WiFi connectivity to nearby users

**As Internet Gateway:**

- Accepts IPFS upload requests from mesh
- Forwards to Pinata/Web3.Storage via API
- Caches locally (100GB, 30-day retention)
- Returns IPFS hash to mesh
- Distributes software updates when available

**Bridge requirements:**

- Satellite internet (Starlink preferred) or high-reliability cellular
- Hidden location with clear sky view (Starlink)
- Emergency shutdown (hardware kill switch)
- Network continues if all bridges down (mesh-only mode)

**Resource allocation:**

- 50% bandwidth: IPFS uploads
- 30% bandwidth: Mesh traffic relay
- 20% bandwidth: Software updates, monitoring

---

### **Layer 3: Permanent Storage (IPFS)**

**Must provide:**

- Content-addressed storage (files = cryptographic hash)
- Global replication via external pinning services
- Censorship resistance (no central authority)
- Content retrieval from anywhere
- External partner pinning (human rights orgs, journalists)

**Architecture: Gateway Model (NOT Full IPFS Node)**

**Bridge nodes run:**

- Lightweight HTTP gateway service (50-100MB RAM)
- NOT full IPFS daemon (would use 300MB RAM)
- Local cache only (100GB storage)
- API client to external pinning services

**External pinning services (MANDATORY):**

- Pinata (primary, $240/year for 96GB)
- Web3.Storage (backup, free for public good)
- NFT.Storage (alternative, Filecoin-backed)

**CRITICAL: Content NOT permanent without external pins**

- Upload to IPFS ≠ permanent storage
- Unpinned content garbage collected in hours/days
- Must actively pin to 2+ external services
- Losing all pins = content gone forever

**Upload flow:**

1. User uploads encrypted content via mesh
2. Bridge receives at HTTP endpoint
3. Bridge forwards to Pinata (primary pin)
4. Bridge forwards to Web3.Storage (backup pin)
5. Verify both return same hash (integrity)
6. Cache locally (optional, for speed)
7. Return hash to mesh network
8. Log critical content for partner pinning

**Retrieval options:**

- Local cache (fastest, if available)
- Public IPFS gateways (ipfs.io, dweb.link)
- Any IPFS node globally (with hash)
- Shareable URLs for journalists/lawyers

**All content encrypted before IPFS upload**

- See Component 7 for encryption details
- IPFS stores encrypted blobs only
- Decryption keys distributed separately via Matrix

---

## Constraints

**Technical:**

- User phones not reliable relays (battery, mobility)
- Maximum 7 hops (latency accumulation)
- WiFi Direct: 200-500 feet per hop
- Starlink needs clear sky view (limits bridge placement)
- IPFS upload requires internet (bridge only)

**Environmental:**

- Hostile: Assume active surveillance/disruption
- Intermittent power: Nodes survive outages (solar/battery)
- Limited expertise: Operators have minimal training
- Geographic spread: May cover 1-2 square miles
- No central coordination: Autonomous operation required

**Resource:**

- Budget: $10k-15k initial for 5,000-person community
- Maintenance: Must be community-sustainable
- Hardware: Consumer-grade only (no enterprise gear)
- Bandwidth: 10-20 Mbps shared across bridge node

**Operational:**

- Covert deployment (low visibility)
- Minimal daily expert intervention
- Self-healing without central management
- Users operate with minimal training

---

## Layer Interaction

**Normal Operation (Bridge Available):**

```
User phone → Relay node → ... → Relay node → Bridge node
                                                    ↓
                                            [IPFS Gateway]
                                                    ↓
                                    Pinata API + Web3.Storage API
                                                    ↓
                                            Global IPFS Network
```

**Internet Shutdown (Bridge Unavailable):**

```
User phone → Relay node → ... → Relay node → Hub node
                                                ↓
                                        Store-and-forward
                                                ↓
                                        Queue for later upload
                                                ↓
                                        Mesh continues operating
```

**Failover Scenario:**

```
Bridge 1: DESTROYED
Bridge 2: Takes over IPFS uploads within 1 minute
Bridge 3: Standby backup

Mesh network: No disruption (routes around Bridge 1)
IPFS uploads: Resume via Bridge 2 automatically
User experience: Transparent (queued uploads resume)
```

---

## Success Criteria

**Functionality:**

- ✅ Text messages: <10 seconds across 7 hops
- ✅ Photos: <1 minute delivery
- ✅ Videos: <5 minutes delivery (chunked)
- ✅ Survives 50% relay node failure
- ✅ Operates indefinitely without internet
- ✅ IPFS uploads complete within 30 minutes of bridge available

**Reliability:**

- ✅ >99% message delivery rate
- ✅ <1% network downtime over 30 days
- ✅ Automatic recovery from failures <5 minutes (Babel convergence)
- ✅ Bridge failover <1 minute
- ✅ Mesh continues during internet shutdown

**Coverage:**

- ✅ >90% population coverage in target area
- ✅ <5% dead zones (no connectivity)
- ✅ Every user within 3 hops of relay node
- ✅ Redundant paths between population centers

**Security:**

- ✅ No single point of failure
- ✅ Content persists globally after local destruction
- ✅ Network identity untraceable to individuals
- ✅ Traffic patterns not externally analyzable

**Usability:**

- ✅ Users perceive as "just messaging app"
- ✅ Works without internet (feature, not bug)
- ✅ Clear status indicators (connected/offline/queued)
- ✅ Graceful degradation on failures

**IPFS Permanence:**

- ✅ 100% critical content pinned to 2+ external services
- ✅ Monthly verification: all hashes still retrievable
- ✅ Automated re-pinning if pin lost
- ✅ Zero content loss after 90 days

---

## What Changed (From Previous Version)

**Layer 3 (IPFS) Updates:**

1. ❌ Removed: "Bridge nodes run go-ipfs daemon"
2. ✅ Added: "Bridge nodes run lightweight HTTP gateway"
3. ✅ Clarified: External pinning is mandatory (not optional)
4. ✅ Added: Unpinned content gets garbage collected
5. ✅ Added: Gateway model architecture diagram
6. ✅ Updated: RAM requirements (50-100MB vs 300MB)

**Why Changed:**

- Expert feedback: Full daemon too resource-intensive
- Reality check: IPFS not automatically permanent
- Reliability: External services more stable
- Simplicity: Gateway model easier to maintain

---

## Dependencies

- **Component 2:** Hardware specs (bridge node capabilities)
- **Component 4:** Babel routing protocol details
- **Component 5:** IPFS implementation specifics
- **Component 7:** Encryption before IPFS upload
- **Component 9:** Budget (external pinning costs)

---

## Status

**Completeness: 9/10** ⬆️ **INCREASED FROM 8/10**

**Why increased:**

- ✅ IPFS layer clarified (gateway model)
- ✅ External pinning requirement emphasized
- ✅ Resource allocation specified per layer
- ✅ Failover scenarios documented

**Needed for 10/10:**

- Network topology optimization tools
- Detailed bridge failover protocols
- Coverage calculation formulas
- Community split/merge procedures

**Status: Developer-ready.** Architecture specified for implementation.