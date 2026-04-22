---
title: Security - Panic Mode & Data Protection
version: 2.0
last_updated: 2025-10-23
status: Production-Ready
parent: 08-security-encryption
related:
  - 08-00-security-overview
  - 08-01-security-encryption-keys
  - 09A-ux-onboarding
tags: [security, panic-mode, data-protection, duress]
---

## Purpose

Panic mode enables instant, unrecoverable deletion of sensitive data when users face imminent device seizure or duress. Must work reliably under stress with clear physical triggers.

## Trigger Methods

### Method 1: Physical Button

**Activation:**
- Long-press Power + Volume Down (3 seconds)
- No confirmation dialog (speed critical)
- Tactile feedback on trigger
- Works from lock screen

**Data Wiped:**
- All encryption keys (Matrix + wallet)
- All stored messages and conversations
- All cached media files
- App settings revealing network participation
- Message queue and drafts
- Contact list and group information

**Timing:**
- Complete wipe in <5 seconds
- Irreversible (unrecoverable even with forensics)
- Device remains functional (not bricked)
- App appears freshly installed after wipe

### Method 2: Duress PIN

**Purpose:**
- Appear to unlock normally while wiping data
- Protects against coerced unlock attempts
- Buys time with plausible deniability

**Behavior:**
- User enters duress PIN
- App opens to fake/decoy content
- Real data wiped silently in background
- Looks normal to adversary observing
- Complete background wipe in <10 seconds

**Setup:**
- Primary PIN: Normal unlock
- Duress PIN: Different from primary, triggers wipe
- User sets both during onboarding
- No visual indication of which PIN used

## Auto-Wipe Features

### Failed Unlock Attempts

**Configuration:**
- User chooses threshold: 3, 5, or 10 failed attempts
- Counter resets on successful unlock
- Warning at threshold - 1 ("2 attempts remaining")
- Immediate wipe at threshold

**Implementation:**
- Counter stored in Android Keystore
- Survives app restart
- Cannot be bypassed via side-loading
- Logs attempt timestamps

### Inactivity Timer

**Optional Feature:**
- Auto-wipe if device not unlocked for X days
- User configurable: 7, 14, 30, 60 days
- Default: Disabled
- Use case: Abandoned device or detention

**Warnings:**
- Notification at 80% of timeout
- Final notification at 95% of timeout
- User can extend timer via unlock

### SIM Card Removal

**Optional Feature:**
- Auto-wipe on SIM card removal
- Default: Disabled
- Use case: Forced SIM swap or device cloning
- Immediate trigger (no delay)

**Consideration:**
- Can cause accidental wipes
- User must understand implications
- Recommended only in high-threat scenarios

## What Gets Wiped

### Critical Data (Always Wiped)
- Matrix encryption keys (Olm/Megolm session keys)
- Web3 wallet private keys
- Message database (all conversations)
- Media cache (photos, videos)
- Contact list and group memberships
- Message queue (pending sends)

### App Settings (Configurable)
- Network participation evidence
- Relay node bookmarks
- Operator relationships
- App preferences and customizations

### What Remains
- Android OS (device functional)
- Other apps (unaffected)
- App binary (reinstall not needed)
- Public IPFS hashes (content already encrypted)

## Security Requirements

### Unrecoverability

**Secure Deletion:**
- Keys overwritten with random data (7 passes)
- Database files securely wiped
- Media files securely deleted
- Verify deletion completeness

**Android Keystore:**
- Keys deleted via Keystore API
- Hardware-backed deletion when available
- No key recovery possible
- Forensic tools cannot retrieve

### Testing & Validation

**Safe Mode:**
- Testing mode that simulates wipe without destroying data
- Verifies trigger mechanisms work
- Measures wipe completion time
- Used in user training

**Forensic Validation:**
- Professional forensic tools used to verify wipe
- No data recoverable after panic mode
- Keys irretrievable from device
- Messages unreadable

**Device State Testing:**
- Test while app active
- Test while app backgrounded
- Test while device locked
- Test during low battery
- Test during incoming call

## User Training

### Onboarding Requirements

**Panic Mode Tutorial:**
- Physical button demonstration
- Duress PIN setup explanation
- Practice trigger in safe mode
- Understand irreversibility

**Scenarios:**
- Checkpoint encounter
- Home raid
- Device confiscation
- Coerced unlock

### Best Practices

**Physical Security:**
- Regular backups to secure location
- Seed phrase stored separately
- Practice panic mode activation
- Plan for device loss scenarios

**Operational Security:**
- Don't rely solely on panic mode
- Minimize sensitive data retention
- Regular data cleanup
- Use auto-wipe features appropriately

## Implementation Notes

**Android APIs:**
- KeyguardManager for lock screen detection
- KeyStore for secure key deletion
- File.delete() with secure overwrite
- Room database secure clearing

**Performance:**
- Wipe operations prioritized (THREAD_PRIORITY_URGENT_AUDIO)
- Progress tracked internally
- Device remains responsive
- No user-visible delay

**Edge Cases:**
- Power loss during wipe (keys deleted first)
- Crash during wipe (resume on restart)
- Multiple simultaneous triggers (idempotent)
- Developer mode enabled (still works)

## Related Documents

- **08-00:** Security architecture overview
- **08-01:** Encryption and key management
- **09A:** Onboarding and user training
