---
title: Security Overview
version: 2.0
last_updated: 2025-10-23
status: Production-Ready
parent: 08-security-encryption
related:
  - 08-01-security-encryption-keys
  - 08-02-security-panic-mode
  - 08-03-security-ipfs-threat-model
  - 04A-identity-system
  - 04-communication-protocol
tags: [security, encryption, threat-model, architecture]
---

## Purpose

Security is paramount—users face imprisonment or death if communications are intercepted or identities revealed. This document defines the security architecture that protects user content, metadata, and identity across the mesh network.

**Success criteria:** An adversary who compromises a relay node, captures a phone, or intercepts network traffic cannot decrypt messages, identify users, or compromise past/future communications.

## Core Security Principles

### End-to-End Encryption
- All message content encrypted from sender to recipient only
- Relay and bridge nodes cannot read message contents
- Encryption keys never leave user devices
- Perfect forward secrecy for past messages
- Future secrecy for future messages

### Defense in Depth
- **Application layer:** Matrix E2E encryption (Olm/Megolm)
- **Transport layer:** TLS 1.3 or libp2p Noise protocol
- **Storage layer:** Android Keystore with hardware backing
- **Physical layer:** Panic mode for instant data destruction

### Key Management
- Web3 wallet seed phrase derives Matrix encryption keys
- Single backup phrase for both identity and encryption
- Hardware-backed key storage when available
- Device verification prevents MITM attacks

## Threat Model

### Defended Against ✓

**Passive Network Monitoring:**
- Cannot decrypt message content (E2E encryption)
- Cannot link addresses to real identities (pseudonymous)

**Relay Node Compromise:**
- Cannot decrypt messages (E2E encryption)
- Cannot forge messages (wallet signatures)

**Device Seizure (Locked):**
- Cannot decrypt messages (Android Keystore)
- Panic mode wipes keys instantly

**Compromised Account:**
- Cannot decrypt past messages (forward secrecy)
- Cannot impersonate other users (separate keys)

### Accepted Risks

- **Traffic analysis:** Who talks to whom, when, frequency
- **Network disruption:** Blocking, jamming, node shutdown
- **Social engineering:** Phishing, impersonation attempts
- **State-level correlation:** Multiple attack vectors combined

## Security Components

1. **Encryption & Keys** - Matrix Olm/Megolm, Web3 wallet integration
2. **Panic Mode** - Instant data wipe under duress
3. **IPFS Security** - Media encryption before upload
4. **Transport Security** - TLS/Noise for mesh connections

## Audit Requirements

Before production launch:
- Third-party security audit
- Penetration testing under realistic threat scenarios
- Code review by cryptography experts
- Regular vulnerability updates

## Related Documents

- **08-01:** Encryption keys and Matrix integration
- **08-02:** Panic mode implementation
- **08-03:** IPFS threat model and media encryption
- **04A:** Identity system and wallet architecture
