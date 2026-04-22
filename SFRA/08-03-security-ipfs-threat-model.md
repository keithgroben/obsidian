---
title: Security - IPFS Threat Model & Media Encryption
version: 2.0
last_updated: 2025-10-23
status: Production-Ready
parent: 08-security-encryption
related:
  - 08-00-security-overview
  - 08-01-security-encryption-keys
  - 06-ipfs-integration
tags: [security, ipfs, encryption, media, threat-model]
---

## Purpose

IPFS provides permanent, distributed storage for media evidence—but public IPFS networks pose privacy risks. This document defines the encryption model that preserves evidence immutability while controlling access.

## Threat Model

### IPFS Privacy Risks

**Public Network Exposure:**
- IPFS hashes publicly visible on network
- Anyone can attempt to fetch content by hash
- Pinning services see encrypted content
- Network observers see upload/download patterns

**Metadata Leakage:**
- File sizes visible (reveals media type)
- Upload timestamps trackable
- IP addresses of uploaders/downloaders
- Pinning service knows upload source

**Trust Assumptions:**
- Pinning services (Pinata, Web3.Storage) see encrypted blobs
- Bridge nodes see what content users upload
- Bridge operators could log activity
- External IPFS nodes could track hash requests

### What We Accept

**Limited Metadata Protection:**
- File sizes reveal approximate media type
- Upload patterns visible to bridge operators
- Pinning services know upload frequency
- Perfect metadata protection requires onion routing (future)

**Pinning Service Trust:**
- Services see encrypted content (not plaintext)
- Could correlate uploads to payment methods
- Could comply with government data requests
- Mitigation: Content encrypted, keys separate

**Network Analysis:**
- Adversary could monitor IPFS DHT queries
- Could identify bridge nodes
- Could correlate hash requests to users
- Mitigation: Tor/VPN for bridge connections (future)

## Encryption Architecture

### Media Encryption Model

**Process Flow:**
1. User captures photo/video
2. App generates unique symmetric key (AES-256-GCM)
3. Media encrypted locally before chunking
4. Encrypted file uploaded to IPFS via bridge
5. IPFS returns hash of encrypted blob
6. Encryption key sent to recipients via Matrix (E2E encrypted)
7. Recipients fetch encrypted file, decrypt locally

**Key Properties:**
- IPFS hash points to encrypted content
- Public hash useless without decryption key
- Key never transmitted over IPFS
- Multiple recipients = multiple key transmissions (not key re-encryption)

### Symmetric Encryption

**Algorithm:** AES-256-GCM
- 256-bit key strength
- Authenticated encryption (integrity + confidentiality)
- Nonce/IV generated per file
- Authentication tag prevents tampering

**Key Generation:**
- Cryptographically secure random number generator
- 256 bits of entropy per key
- One key per media file (no key reuse)
- Keys stored only until transmission complete

**Key Distribution:**
- Sent via Matrix E2E encrypted channel
- Embedded in message metadata
- Recipients decrypt with Matrix session keys
- Key transmission secured by Olm/Megolm

### Content Verification

**IPFS Hash Properties:**
- Content-addressed (hash = cryptographic digest)
- Proves file integrity (tampering changes hash)
- Verifies downloaded file matches uploaded file
- Works with encrypted content

**Verification Flow:**
1. Sender uploads encrypted file → receives hash
2. Sender sends hash + key via Matrix
3. Recipient fetches file by hash from IPFS
4. IPFS verifies hash matches content
5. Recipient decrypts with provided key
6. Result: Guaranteed authentic, unmodified evidence

## Bridge Node Security

### Bridge Architecture

**Trust Model:**
- Bridge operators see encrypted IPFS uploads
- Cannot decrypt without keys
- Could log upload metadata (times, sizes, IPs)
- Could rate-limit or censor content

**Mitigation Strategies:**
- Multiple bridge options (no single point of trust)
- Bridges see only encrypted blobs
- Keys transmitted separately via Matrix
- Users can run personal bridges (advanced)

### Pinning Services

**What They See:**
- Encrypted file content (binary blob)
- File size
- Upload timestamp
- Requesting IP (bridge node, not user)

**What They Cannot See:**
- Plaintext content
- Who sent the content (user identity)
- Who will access the content (recipients)
- Decryption keys

**Service Selection:**
- Pinata (primary) - established, reliable
- Web3.Storage (backup) - web3-native
- Future: Filecoin integration (paid, guaranteed storage)

## Security Analysis

### Attack Scenarios

**Scenario 1: Adversary Controls Pinning Service**
- Sees encrypted files only
- Could correlate upload patterns
- Cannot decrypt without keys
- **Result:** Content protected ✓

**Scenario 2: Adversary Compromises Bridge Node**
- Sees what users upload
- Cannot read encrypted content
- Could block uploads (disruption)
- **Result:** Availability risk only

**Scenario 3: Adversary Monitors IPFS Network**
- Sees hash requests on DHT
- Cannot link hashes to users (pseudonymous)
- Cannot decrypt content
- **Result:** Metadata exposure only

**Scenario 4: Adversary Seizes User Device**
- May see decrypted media in app cache
- Panic mode wipes cache and keys
- Cannot decrypt IPFS content without keys
- **Result:** Panic mode mitigates ✓

### Advanced Threats

**Correlation Attacks:**
- Bridge operator + pinning service + ISP = upload timing correlation
- Metadata analysis could identify high-value users
- **Mitigation:** Tor/VPN for bridges (Phase 3+)

**Traffic Analysis:**
- Large uploads indicate video evidence
- Could identify documentation campaigns
- **Mitigation:** Upload scheduling, dummy traffic (future)

**Long-Term Storage Risks:**
- Encrypted content persists forever on IPFS
- Future cryptanalysis could break AES-256 (unlikely within decades)
- Quantum computing threat (post-quantum crypto future)

## Best Practices

### For Users
- Upload only when necessary
- Delete local copies after successful upload
- Use panic mode if device at risk
- Trust bridge operators carefully

### For Operators
- Minimize logging on bridges
- Use VPN/Tor for bridge connections
- Rotate bridge IP addresses
- Don't correlate uploads to users

### For Developers
- Verify AES-GCM implementation
- Use standard crypto libraries (no custom crypto)
- Test encryption/decryption roundtrip
- Audit key handling

## Related Documents

- **08-00:** Security architecture overview
- **08-01:** Encryption and key management
- **06:** IPFS integration architecture
