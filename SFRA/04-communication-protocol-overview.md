---
title: 04 - Communication Protocol - Overview
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 8/10
tags: [communication, protocol, matrix, overview]
---

---

## Overview

The communication layer integrates three critical subsystems to enable censorship-resistant messaging: Matrix Protocol for encrypted message transport, Web3 wallet-based identity for pseudonymous authentication, and decentralized governance for community moderation. This architecture provides end-to-end encryption, operates without central servers, and resists capture by adversaries.

---

## Three-Part Architecture

### 1. Matrix Protocol (Message Transport)

**Purpose:** Secure, decentralized messaging

**Features:**

- End-to-end encryption using Olm (1-to-1) and Megolm (groups)
- Text, photo, video, and voice messages
- Store-and-forward for offline recipients
- WebRTC for voice/video calls
- Can operate peer-to-peer or via homeserver on bridge nodes

**Why Matrix (not Signal)?**

- Supports decentralized operation (no central server dependency)
- Native E2E encryption is battle-tested (used by French government, German military)
- Can self-host or run P2P mode
- Open source and auditable
- Federation capability (if needed later)

### 2. Web3 Identity (User Authentication)

**Purpose:** Pseudonymous identity without central databases

**Features:**

- Users identified by Ethereum wallet addresses (not phone numbers)
- Wallet seed phrase derives encryption keys
- Cryptographic signatures prove message authenticity
- Social recovery via 3-of-5 guardians
- Payment rails available (future enhancement)

**Why Web3 Wallets?**

- No registration required (no email, phone, or ID)
- Single backup phrase for identity + encryption
- Enables blockchain-based governance
- Resistant to Sybil attacks through vetting mechanisms

**See:** [[04A-identity-system]] for complete details

### 3. Decentralized Governance (Moderation & Rules)

**Purpose:** Community-driven content moderation without central control

**Four-Tier Structure:**

1. **Personal Blocks** – Individual users block others locally
2. **Moderators** – Community-elected, limited powers
3. **DAO Votes** – Community votes on major decisions
4. **Smart Contracts** – Automated enforcement and upgrades

**Why Blockchain for Governance?**

- Votes are permanent and auditable (prevents manipulation)
- Smart contracts enforce rules automatically
- Transparent decision-making (votes public)
- Moderators accountable (all actions logged)
- Users retain sovereignty (personal blocks always work)

**See:** [[04B - Governance - Overview]] for complete framework

---

## Message Flow

**Typical Message Journey:**

1. **User sends message** → Encrypted with recipient's key (Matrix E2E)
2. **Message signed** → With sender's wallet (proves authenticity)
3. **Routed through mesh** → Via relay nodes using Babel routing
4. **Stored if offline** → Queued at relay node until recipient connects
5. **Delivered to recipient** → Who decrypts with their key
6. **Media uploaded** → Photos/videos automatically backed up to IPFS

**See:** [[05-mesh-networking]] for routing details, [[06-ipfs-integration]] for media storage

---

## Security Model

### What's Protected (Private)

✅ **Message content** – E2E encrypted, relay nodes can't read  
✅ **User identity** – Pseudonymous wallet addresses  
✅ **Media files** – Encrypted before upload to IPFS  
✅ **Encryption keys** – Never leave user devices

### What's Public (Transparent)

⚠️ **Governance votes** – Intentional transparency prevents corruption  
⚠️ **Wallet addresses** – Pseudonymous but visible  
⚠️ **Routing metadata** – Who talks to whom, not what they say  
⚠️ **IPFS hashes** – Content identifiers are public

### Trade-offs Accepted

**Governance transparency vs. messaging privacy:**

- Votes are public on blockchain (prevents manipulation)
- Messages are private via E2E encryption
- Users educated on this trade-off during onboarding

**Pseudonymity vs. perfect anonymity:**

- Wallet addresses are pseudonymous (not linked to real names)
- Blockchain is traceable (pattern analysis possible)
- Users warned never to connect wallet to KYC exchanges

**See:** [[08 - Security & Encryption]] for complete threat model

---

## Message Types & Performance

**Text Messages:**

- <10 seconds delivery across 7 hops
- Store-and-forward when recipient offline
- Delivery confirmation and retry logic

**Photo Messages:**

- Compressed to 200-500KB
- EXIF data stripped (no GPS/device metadata)
- Uploaded to IPFS for permanent storage
- <1 minute delivery

**Video Messages:**

- Compressed to 480p, 3-5MB per minute
- Chunked into 256KB pieces for transmission
- Uploaded to IPFS with multiple pinning services
- <5 minutes delivery for 1-minute clip

**Voice Calls:**

- 32 kbps, acceptable through 7 hops
- WebRTC over Matrix for signaling
- <500ms latency target

**Video Calls:**

- 128-256 kbps, best through 1-3 hops
- Adaptive bitrate based on bandwidth
- May require hub nodes for quality

**See:** [[07-video-handling]] for media compression details

---

## Key Design Decisions

**Delay-Tolerant Design:**

- Accept minutes for delivery, not instant
- Store-and-forward for offline recipients
- "Queued" is normal, not an error
- Clear status indicators (sending → sent → delivered)

**Offline-First Mindset:**

- All features work without internet
- Media queued locally until bridge available
- Network self-heals when nodes fail
- Clear communication about delays

**Decentralized Operation:**

- No central servers to shut down
- Community-operated infrastructure
- Resistant to censorship and capture
- Users can fork network if needed

---

## Components Detail

**For Complete Information:**

- **Matrix & Message Types** → [[04 - Component 3 Communication Protocol]] (full spec)
- **Identity & Wallets** → [[04A-identity-system]]
- **Governance Framework** → [[04B - Governance - Overview]]
    - Moderator System → [[04B1-governance-moderators]]
    - Smart Contracts → [[04B2-governance-smart-contracts]]
    - Operator Management → [[04B3-governance-operators]]
    - Conflict Resolution → [[04B4-governance-conflicts]]
- **Message Routing** → [[05-mesh-networking]]
- **Media Storage** → [[06-ipfs-integration]]
- **Encryption Details** → [[08 - Security & Encryption]]
- **User Experience** → [[09-ux-principles]]

---

## Status

**Well-Defined:**

- ✅ Protocol stack selected and justified
- ✅ Identity system integrated
- ✅ Governance framework complete
- ✅ Security model documented
- ✅ Message types and flows specified

**Needs Work:**

- ⚠️ Matrix P2P mode testing
- ⚠️ Homeserver configuration details
- ⚠️ Matrix-wallet authentication implementation
- ⚠️ Call quality benchmarks over mesh

**To Reach 10/10:** Field testing, performance validation, refined integration

---

## Related Documents

- [[04 - Component 3 Communication Protocol]]: Full technical specification
- [[04A-identity-system]]: Web3 wallet implementation
- [[04B - Governance - Overview]]: Governance architecture
- [[05-mesh-networking]]: Message routing protocols
- [[08 - Security & Encryption]]: Security requirements