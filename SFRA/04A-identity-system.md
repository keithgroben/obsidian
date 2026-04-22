---
title: 04A - Identity System
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 8/10
tags: [communication, identity, web3, security, wallet]
---

## Overview

Users are identified by crypto wallet addresses rather than phone numbers, emails, or usernames. This provides pseudonymous identity without central databases, enables cryptographic message signing, includes built-in payment rails, and allows community-based vetting to prevent Sybil attacks. Each wallet's 12-word seed phrase becomes the master key for identity, encryption, and authentication across the entire network.

---

## Requirements

### Identity System
**Must provide:**
- Pseudonymous identity (not linked to real name/phone)
- No central user database or registration system
- Cryptographic verification (prove message authenticity)
- Portable identity (survives device loss if seed backed up)
- Secure key storage on device (hardware-backed if available)
- User-friendly representation (shortened addresses, QR codes)
- Integration with Matrix Protocol as user ID

**Wallet format:**
- Ethereum-compatible: `0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb`
- Displayed shortened: `0x742d...5f0b`
- Matrix user ID: `@0x742d35Cc...@mesh.local`
- QR code for easy scanning and sharing

### Wallet Management
**Creation:**
- Generate 12-word BIP39 seed phrase
- Derive private/public keys from seed
- Store private key in Android Keystore (hardware-backed)
- Show seed phrase once with backup quiz
- Never store seed phrase on device
- Allow wallet import via seed phrase

**Recovery options:**
- Traditional: Seed phrase recovery (user responsibility)
- Social recovery: M-of-N guardian system (3 of 5 guardians can help transfer identity)
- Time-locked recovery (7-day delay, user can cancel if unauthorized)

### Authentication
**Message signing:**
- All messages signed with wallet private key
- Signature proves authenticity without revealing private key
- Recipients verify signature matches sender's address
- Prevents message forgery and spoofing
- No passwords needed (wallet is authentication)

### Vetting Mechanism
**Problem:** Anyone can create infinite wallets (Sybil attack).

**Solution:** New users must be vouched for by existing trusted users.

**Four-tier system:**
1. **Invitation Codes** (Bootstrap): Initial network seeding by operators
2. **Endorsements** (Web of Trust): Existing users vouch for new users
3. **Reputation Scores** (Earned Trust): Positive behavior increases standing
4. **Staking** (Optional): Small deposit ($5-10) demonstrates commitment

### Wallet Privacy & Hygiene

**Critical Understanding:**
Blockchain is transparent by design. All on-chain activity (votes, transactions, interactions) is publicly visible and permanently recorded. Wallet addresses are pseudonymous but traceable through chain analysis.

**User Education (During Onboarding):**

"Your wallet address is your identity on this network. It's like a username, not completely anonymous.

⚠️ CRITICAL: Never connect this wallet to cryptocurrency exchanges (Coinbase, Binance, etc.) or any service requiring identity verification. Doing so links your real identity to your wallet permanently.

✅ Safe: Use this wallet only for mesh network governance and messaging
❌ Dangerous: Buying/selling cryptocurrency with this wallet"

**Privacy Rules:**
1. **Use separate wallets:** One for mesh network, different ones for other crypto activities
2. **Never mix funds:** Don't send crypto between your identity wallet and other wallets
3. **Avoid KYC services:** Never use exchanges requiring ID verification with mesh wallet
4. **Understand blockchain permanence:** All votes and transactions are public forever

**Regional Risk Levels:**

**High-Risk Regions** (Active Persecution):
- Use wallet ONLY for mesh network
- Never connect to any external blockchain service
- Consider using wallet without any on-chain activity
- Governance participation creates permanent public record

**Medium-Risk Regions** (Surveillance Present):
- Strict wallet separation enforced
- No cryptocurrency purchases with identity wallet
- Awareness that votes are public

**Low-Risk Regions** (Relatively Safe):
- Still practice wallet hygiene
- Understand governance transparency
- Maintain pseudonymity as best practice

---

## Implementation Notes

**Blockchain Selection:**
- Ethereum Layer 2 (Polygon or Base recommended)
- Low transaction fees ($0.01-0.05 per transaction)
- Fast confirmation (1-3 seconds)
- Broad wallet library support

**Wallet Library:**
- Use ethers.js or web3.js for wallet generation
- Android Keystore for secure key storage
- Hardware security module when available

**Gas Subsidy:**
- Meta-transactions or relay service
- Operators cover gas costs for users
- Budget: ~$0.05 per user per month
- Prevents financial barrier to participation

**Governance Transparency Disclosure:**

Before first vote, users must acknowledge:

"✅ I understand my votes are public on the blockchain
✅ I understand my wallet address will be visible
✅ I understand this transparency prevents corruption
✅ I will never connect this wallet to KYC services"

---

## Success Criteria

**Functionality:**
- Wallet creation takes <2 minutes
- Seed phrase backup enforced (quiz passes)
- Message signing automatic and transparent to user
- Social recovery works within 7 days when needed
- Wallet import restores full identity and history

**Security:**
- Private keys never exposed to application code
- Hardware keystore used when available
- Sybil attacks prevented by vetting mechanism
- No central identity database to compromise

**Privacy:**
- Users acknowledge wallet privacy limitations during onboarding
- Users acknowledge public governance votes before first vote
- Wallet separation enforced through education
- KYC risk warnings clearly communicated

**Performance:**
- Transaction confirmation <5 seconds (when online)
- Gas costs <$0.05 per transaction
- 1000 active users supportable for <$200/month gas subsidy

---

## Status

**Well-Defined:**
- Wallet-based identity fully designed
- Four vetting mechanisms specified
- Blockchain selection with rationale (Ethereum L2)
- Social recovery mechanism documented
- Privacy education framework complete
- Governance transparency disclosure workflow

**Needs Work:**
- Specific smart contract code for governance/vetting
- Wallet library integration details
- Gas subsidy implementation (meta-transaction relay)
- Real blockchain testing and transaction validation
- Offline transaction queuing implementation

**To Reach 10/10:** Smart contract deployment, wallet library integration, field testing with real users.

---

## Dependencies

- **04B Governance Series:** Votes are cast using wallet signatures
- **05 Mesh Networking:** Wallet addresses route messages
- **08 Security & Encryption:** Wallet private keys protect identity
- **09A UX - Onboarding:** Onboarding creates wallet and educates users