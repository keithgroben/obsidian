---
title: Security - Encryption & Key Management
version: 2.0
last_updated: 2025-10-23
status: Production-Ready
parent: 08-security-encryption
related:
  - 08-00-security-overview
  - 08-02-security-panic-mode
  - 04A-identity-system
  - 04-communication-protocol
tags: [security, encryption, keys, matrix, e2ee]
---

## Purpose

Defines the encryption architecture and key management that protects message content, ensures forward secrecy, and prevents unauthorized access—even when relay nodes or devices are compromised.

## End-to-End Encryption

### Protocol Requirements

**1-to-1 Messaging:**
- Matrix's Olm (Signal Protocol's Double Ratchet)
- Perfect forward secrecy per message
- Future secrecy after key compromise
- Automatic key rotation

**Group Messaging:**
- Matrix's Megolm (optimized group encryption)
- Efficient key distribution
- Session management
- Device verification support

**Media Files:**
- Encrypt before chunking
- Decrypt after reassembly
- Symmetric encryption (AES-256-GCM)
- Keys sent via E2E encrypted channel

### Critical Properties

**Perfect Forward Secrecy:**
- Past messages remain secure even if current keys compromised
- Session keys destroyed after use
- No single key decrypts message history

**Future Secrecy:**
- Future messages secure after key compromise detected
- Key rotation automatic
- System recovers from compromise

**Post-Compromise Security:**
- System detects compromise via device verification
- New keys established independently
- Previous sessions invalidated

### Why Matrix?

- Battle-tested (millions of users)
- Handles key rotation automatically
- Device verification built-in
- Open source and audited
- Don't reinvent cryptographic primitives

## Key Management

### Web3 Wallet Integration

**Key Derivation:**
- Ethereum wallet seed phrase → Matrix encryption keys
- Deterministic derivation (BIP-39/BIP-44 standard)
- Single backup phrase for identity + encryption
- Consistent keys across device recovery

**Benefits:**
- One phrase to backup/protect
- Wallet address = user identity
- Keys mathematically linked to identity
- Standard derivation ensures compatibility

### Key Storage

**Android Keystore:**
- Hardware-backed when available (TEE/Secure Element)
- Software fallback for older devices
- Encrypted at rest with device PIN/biometric
- Keys never exposed to application layer

**Protection Requirements:**
- Never written to logs or debug output
- Wiped on app uninstall
- Wiped on panic mode trigger
- Isolated from app memory space

### Device Verification

**User-to-User Verification:**
- QR code scanning (preferred)
- Emoji comparison fallback
- Out-of-band verification supported
- Cross-signing for multi-device trust

**Security Modes:**
- **Standard:** Warn on unverified devices
- **High-security:** Block unverified devices
- **Verified-only:** Require verification before messaging

**Cross-Signing:**
- Verify once, trust across devices
- Master signing key on primary device
- Device signing keys per device
- User signing key for verifying others

## Transport Security

### Mesh Connection Encryption

**Protocol:**
- TLS 1.3 or libp2p's Noise protocol
- Ephemeral keys per connection (forward secrecy)
- Certificate pinning for known relay nodes
- Authentication prevents MITM

**Relay Node Authentication:**
- Persistent public keys per relay
- Signed advertisements
- Identity verification before connection
- Prevents malicious relay impersonation

### Defense in Depth

**Separation of Concerns:**
- Transport encryption protects network layer
- E2E encryption protects content layer
- Relay compromise reveals routing only
- Content remains encrypted end-to-end

**Accepted Limitation:**
- Relay nodes see routing metadata (sender/recipient IP)
- Perfect metadata protection requires onion routing (future)
- Trade-off: Performance vs. metadata protection

## Implementation Requirements

### Matrix SDK Integration
- Use official Matrix SDK where available
- Olm for 1-to-1, Megolm for groups
- Enable all device verification flows
- Implement key backup mechanisms

### Android Keystore Usage
- Request hardware-backed storage
- Test on multiple device types
- Verify keys never exposed to app
- Handle older devices gracefully

### Key Backup & Recovery
- Encrypted backup to user's secure location
- Recovery via seed phrase
- Device verification on restore
- Warning on unverified restored devices

## Security Testing

**Verification Requirements:**
- Captured traffic cannot be decrypted
- Compromised relay cannot read messages
- Seized locked device reveals nothing
- Forward secrecy confirmed via testing

**Code Review:**
- Cryptography experts review implementation
- No custom crypto primitives
- Standard library usage verified
- Key handling audited

## Related Documents

- **08-00:** Security architecture overview
- **08-02:** Panic mode and data destruction
- **04A:** Identity system and Web3 wallets
- **04:** Communication protocol and Matrix
