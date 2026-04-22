---
title: 09C - UX - Security Interface
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 8/10
tags: [user-facing, ux, security, interface]
---

---

## Overview

Security features must be both visible and accessible. Users must always know their security status, be able to verify contacts, and access emergency features instantly. This document defines security indicators, panic mode interface, and security settings.

---

## Security Status Indicators

### Always-Visible Header

**Top Status Bar (Present on Every Screen):**

```
[🔒 Encrypted] [Network: 3 hops] [Queue: 2] 
```

**Color Coding:**

- 🔒 Green = Encrypted and secure
- 🔒 Yellow = Encrypted but warning (unverified contact)
- 🔓 Red = Not encrypted (should NEVER appear)

### Network Connection Indicator

**States:**

**Connected:**

```
[Network: ● 3 hops]
Green dot, shows hop count
```

**Searching:**

```
[Network: ○○○]
Gray animated dots
```

**Offline:**

```
[Network: Offline]
Gray, but not alarming
```

**Tap for Details:**

```
Network Status

Connected via mesh
├─ 3 hops to internet
├─ 2 relay nodes nearby
└─ 15 active users

Signal Strength: Strong
Bandwidth: Normal

[View Network Map] [Settings]
```

---

## Encryption Indicators

### Message-Level Encryption

**Every Message Shows:**

```
Alice • 2:45 PM
"Are you safe?"
🔒 End-to-end encrypted

[Reply]
```

**Contact Verification Status:**

**Unverified Contact:**

```
Alice (Unverified)
⚠️ Not yet verified

Messages are encrypted, but you 
haven't confirmed this is really Alice.

[Verify Identity] [Learn More]
```

**Verified Contact:**

```
Alice ✓
Endorsed by 2 contacts

Messages are encrypted and 
identity verified.

[View Endorsements]
```

---

## Panic Mode Interface

### Activation Methods

**Method 1: Physical Buttons**

```
Press and hold:
Power + Volume Down (3 seconds)

[Illustration of finger positions]

Screen goes black immediately
All keys wiped in background
```

**Method 2: Duress PIN**

```
Lock screen:
[Enter PIN]

If duress PIN entered:
→ App opens normally (looks real)
→ All keys destroyed silently
→ Next open: Fresh start
```

**Method 3: In-App Trigger**

```
Settings → Security → Panic Mode
[TEST PANIC MODE] [ACTIVATE PANIC MODE]

Confirmation:
"This will destroy all encryption keys.
Your account cannot be recovered."

[Cancel] [Confirm Wipe]
```

### Post-Panic Experience

**App Behavior After Panic:**

```
Screen: Black immediately
Background: Keys wiped (takes 2-5 seconds)
Next open: Fresh onboarding

Result:
• All messages deleted
• All contacts removed
• Wallet keys destroyed
• App looks unused
```

**What Survives:**

- Nothing (intentional total wipe)
- IPFS content may still exist (explain this in education)

---

## Security Settings

### Security Settings Menu

**Access:** Home → Settings → Security

**Menu Structure:**

```
SECURITY SETTINGS

Identity & Encryption
├─ View Wallet Address
├─ Export Public Key
├─ Backup Recovery Phrase
└─ Security Audit Log

Panic Mode
├─ Test Panic Mode (safe)
├─ Change Duress PIN
└─ Panic Mode Education

Contact Verification
├─ Verify Contacts
├─ Request Endorsements
└─ View Endorsers

Privacy
├─ Wallet Hygiene Guide
├─ Block List
└─ Data Export

Advanced
├─ Key Management
├─ Encryption Details
└─ Security Audit
```

---

## Wallet Address Display

### Share Wallet Address

**Access:** Settings → Identity → Wallet Address

**Display:**

```
Your Wallet Address

0x742d35Cc6634C0532925a3b844Bc9e7595f0bEbF

[Copy] [Show QR Code] [Share]

⚠️ Privacy Reminder:
Only share with trusted contacts.
Never connect to exchanges.

[Read Privacy Guide]
```

**QR Code View:**

```
[Large QR Code]

Scan this with another device 
to add you as a contact.

[Copy Address] [Done]
```

---

## Contact Verification Interface

### Verify Contact Screen

**Access:** Contact Profile → Verify

**Options:**

**Option 1: Request Endorsement**

```
Verify Alice

Ask a mutual contact to endorse Alice:

Available Endorsers:
☐ Charlie (mutual friend)
☐ David (community leader)

[Request Endorsements]
```

**Option 2: In-Person Verification**

```
Verify in Person

1. Meet Alice face-to-face
2. Scan her QR code or compare addresses
3. Confirm identity
4. Mark as verified

[Scan QR Code] [Compare Manually]
```

**Manual Verification:**

```
Compare Wallet Addresses

Your screen shows:
0x742d...bEbF

Alice's screen should show:
0x8f3e...4a2c

Do they match?

[Yes, Verified] [No, Don't Match]
```

---

## Security Warnings

### Critical Warnings

**Unverified Contact Warning:**

```
⚠️ Unverified Contact

You're about to send to Alice (unverified).

Messages are encrypted, but you haven't 
confirmed this is really Alice.

[Verify First] [Send Anyway]
```

**Wallet Privacy Violation:**

```
❌ Privacy Risk Detected

You're about to connect this wallet 
to [Exchange Name].

This will link your mesh identity to 
your real name. Are you sure?

[Cancel] [I Understand the Risk]
```

**Low Storage for Queue:**

```
⚠️ Queue Storage Low

Only 15 MB available for queued messages.

Some messages may fail to queue.

[Free Up Space] [Manage Queue]
```

---

## Security Audit Log

### Access and Display

**Access:** Settings → Security → Security Audit Log

**Log Entries:**

```
SECURITY AUDIT LOG

Oct 16, 2:45 PM
✓ Message sent (encrypted)
  To: Alice
  Hops: 3

Oct 16, 2:30 PM
✓ Video uploaded to IPFS
  Hash: Qmx7g...
  Chunks: 32/32

Oct 16, 1:15 PM  
⚠️ Unverified contact message
  From: Unknown (0x8f3e...)
  Action: Flagged for review

Oct 16, 12:00 PM
✓ Wallet backup verified
  Method: Seed phrase quiz

Oct 15, 11:45 PM
✓ Panic mode test successful
  Duration: 2.3 seconds

[Export Log] [Clear Old Entries]
```

**Log Retention:**

- 30 days default
- Stored locally only
- Export before panic mode

---

## Backup and Recovery

### Backup Recovery Phrase

**Access:** Settings → Security → Backup Recovery Phrase

**Verification Required:**

```
Re-verify Recovery Phrase

Select word #7:
[quality] [rabbit] [race] [rack]

Select word #3:
[able] [about] [above] [absent]

[Continue]
```

**Display Options:**

```
Recovery Phrase Backup

[Show Phrase Again]

⚠️ Warning: Anyone with these words 
can access your account.

Last backed up: 7 days ago

[Mark as Backed Up] [Test Recovery]
```

---

## First-Vote Disclosure

### Governance Transparency

**Before First Vote:**

```
⚠️ Public Vote Disclosure

Your votes are PUBLIC on the blockchain.

This is by design:
• Prevents vote manipulation
• Creates accountability
• Enables community verification

Your wallet address is visible, 
but NOT your real name.

☐ I understand votes are public

[Learn More] [Continue to Vote]
```

---

## Privacy Education

### Wallet Hygiene Guide

**Access:** Settings → Privacy → Wallet Hygiene Guide

**Content:**

```
WALLET PRIVACY GUIDE

Rule #1: Single Purpose
✓ Use this wallet ONLY for mesh network
✗ Never use for other apps or websites

Rule #2: No KYC
✗ Never connect to exchanges (Coinbase, etc.)
✗ Never link to services requiring ID
✓ Keep separate from other wallets

Rule #3: Pseudonymity
✓ Your address is public (like email)
✗ Don't tell anyone it's yours
✓ Maintain separation from real identity

Rule #4: Social Media
✗ Never post your wallet address
✗ Never connect to Web3 social networks
✓ Keep mesh wallet completely separate

Why this matters:
Blockchain is transparent. If you link 
this wallet to your real name anywhere, 
your activities can be traced.

[I Understand] [Quiz Me]
```

---

## Security Testing

### Test Panic Mode (Safe)

**Access:** Settings → Security → Test Panic Mode

**Test Process:**

```
Test Panic Mode (Safe)

This will:
1. Simulate panic mode activation
2. Show you what happens
3. Restore everything after (safe test)

Your data will NOT be deleted.

[Start Test]
```

**Test Experience:**

```
[Screen goes black]
[2-second wait]

Panic Mode Test Complete

In real panic mode:
✓ Screen goes black immediately
✓ All keys destroyed
✓ App wipes completely
✓ Cannot be recovered

Test took 2.1 seconds

[Test Again] [Done]
```

---

## Success Criteria

**Visibility:**

- 100% of users can locate encryption indicator
- > 95% understand green lock meaning
    
- > 90% can activate panic mode under stress
    

**Comprehension:**

- > 85% correctly explain wallet privacy rules
    
- > 80% understand contact verification purpose
    
- > 90% aware votes are public before first vote
    

**Usage:**

- > 70% verify at least one contact
    
- > 50% test panic mode during onboarding
    
- <10% accidentally trigger real panic mode

---

## Status

**Current State:** Interface design complete  
**Next Steps:** UI mockups and user testing  
**Blockers:** None

---

## Related Documents

- [[09-ux-principles]]: Design philosophy
- [[09A-ux-onboarding]]: Security education in onboarding
- [[09B - UX - Core Flows]]: Daily usage patterns
- [[08 - Security & Encryption]]: Technical security implementation
- [[04A-identity-system]]: Wallet and key management