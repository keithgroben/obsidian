---
title: 09A - UX - Onboarding
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 8/10
tags: [user-facing, ux, onboarding, tutorial]
---

---

## Overview

First-time users must complete a secure onboarding process that creates their identity, backs up recovery information, and teaches core security concepts - all within 10 minutes. This document defines the 7-step onboarding flow that balances security requirements with usability.

---

## Onboarding Goals

**Must Achieve:**

- Generate wallet identity securely
- Back up seed phrase (with verification)
- Configure emergency protection (duress PIN)
- Understand queue/offline behavior
- Join mesh network
- Understand core security model
- Feel confident using the app

**Time Budget:** <10 minutes for tech-savvy users, <15 minutes for non-technical users

---

## 7-Step Onboarding Flow

### Step 1: Welcome Screen

**Purpose:** Set expectations and build trust

**Screen Content:**

```
[App Logo]

Secure Communication Without Internet

✓ Messages work offline
✓ Videos preserved forever
✓ Your identity is private
✓ No phone number required

[Continue Button]

Takes about 10 minutes to set up
```

**User Actions:**

- Tap "Continue" to proceed
- Optional: "Learn More" link to FAQ

**Education:**

- App works offline (mesh network)
- No central server to shut down
- Privacy-focused design

---

### Step 2: Identity Creation

**Purpose:** Generate wallet and explain what it means

**Screen Content:**

```
Creating Your Identity

Your identity is being created...
[Progress animation]

What's happening:
• Generating your unique ID
• This is your permanent identity
• No one can delete or block you
• You control your own account

[Automatically proceeds when complete]
```

**Technical Background Process:**

- Generate Ethereum wallet (BIP-39)
- Create 12-word seed phrase
- Derive public/private key pair
- Initialize local encrypted storage

**User Experience:**

- Animation suggests secure process
- Progress shown (builds confidence)
- Auto-proceeds when done (no action needed)
- Takes 3-5 seconds

---

### Step 3: Backup Phrase

**Purpose:** Save recovery phrase and verify comprehension

**Screen 3A: Explanation**

```
Save Your Recovery Phrase

These 12 words are the ONLY way to recover your account.

⚠️ IMPORTANT:
• Write them down on paper
• Keep them somewhere safe
• NEVER share them with anyone
• If you lose them, you lose access forever

[Show My Phrase]
```

**Screen 3B: Display Phrase**

```
Write These Words Down

1. abandon    7. quality
2. ability    8. rabbit
3. able       9. race
4. about     10. rack
5. above     11. radar
6. absent    12. radio

☐ I have written these down safely

[Continue]
```

**Screen 3C: Verification Quiz**

```
Verify You Saved It

Select word #4:
[about] [able] [above] [absent]

Select word #9:
[quality] [race] [radar] [rabbit]

Select word #12:
[rack] [radio] [radar] [race]
```

**Design Rationale:**

- Force written backup (can't screenshot)
- Verification proves they saved it
- Random word selection prevents memorization patterns
- 3 words tested = sufficient validation

**Failure Handling:**

- If wrong: "Please check your written phrase and try again"
- Show correct words after 2 failures
- Must get all 3 correct to proceed

---

### Step 4: Duress PIN Setup

**Purpose:** Configure panic mode protection

**Screen 4A: Explanation**

```
Emergency Protection

Set up two PINs:
• Normal PIN (6 digits) - Regular access
• Duress PIN (6 digits) - Emergency wipe

If forced to unlock:
Use duress PIN → App wipes all keys instantly
Looks normal, but destroys all data

[Set Up PINs]
```

**Screen 4B: Normal PIN**

```
Create Your Normal PIN

Enter 6-digit PIN for daily use:
[●●●●●●]

Confirm PIN:
[●●●●●●]

[Continue]
```

**Screen 4C: Duress PIN**

```
Create Your Emergency PIN

Different 6-digit PIN that wipes everything:
[●●●●●●]

⚠️ This must be DIFFERENT from your normal PIN

Confirm emergency PIN:
[●●●●●●]

[Continue]
```

**Validation:**

- Both PINs must be exactly 6 digits
- Duress PIN must differ from normal PIN
- No sequential numbers (123456, 111111)
- Confirmation must match

**Skip Option:**

- "Skip for now" button
- Warning: "You can set this up later in Settings"
- Persistent nag until configured

---

### Step 5: Network Connection

**Purpose:** Find and connect to mesh network

**Screen Content:**

```
Finding Network

Searching for nearby devices...
[Animated radar-style search]

What's happening:
• Looking for relay nodes
• Connecting to mesh network
• No internet required

Found:
✓ 2 relay nodes nearby
✓ 15 users connected

[Connected! Continue]
```

**Technical Process:**

- Babel routing discovery
- Connect to nearest relay nodes
- Fetch network state
- Subscribe to Matrix rooms

**Offline Handling:**

- If no nodes found after 30 seconds:
    
    ```
    No Network FoundYou can still:• Create messages (they'll queue)• Record videos• Add contactsMessages will send when network available[Continue Offline]
    ```
    

---

### Step 6: Wallet Privacy Education

**Purpose:** Critical security education

**Screen Content:**

```
Protecting Your Privacy

Your wallet address is public (like an email address)

✓ DO:
• Use only for this app
• Keep it separate from other wallets
• Never tell anyone it's yours

✗ DON'T:
• Connect to exchanges (Coinbase, etc.)
• Use for cryptocurrency trading
• Link to your real name anywhere

Why this matters:
Blockchain is public. If you connect this wallet to 
services requiring ID, your identity can be traced.

☐ I understand - keep this wallet private

[Continue]
```

**Education Goals:**

- Explain pseudonymity vs anonymity
- Warn about KYC exchange danger
- Emphasize single-purpose wallet
- Make consequences clear

**Confirmation Required:**

- Must check box to proceed
- Cannot skip this screen
- Review available in Settings later

---

### Step 7: Interactive Tutorial

**Purpose:** Learn by doing

**Tutorial Sequence:**

**7A: Test Panic Mode**

```
Try Panic Mode

Press and hold:
Power + Volume Down (3 seconds)

[Finger pressing buttons illustration]

Don't worry - we'll restore everything after!

[Try It Now]
```

- User activates panic mode
- Screen goes black
- Restoration happens automatically
- "Great! You know how to activate emergency wipe"

**7B: Send First Message**

```
Send Your First Message

This is a practice message. Try it:

To: Test Bot

Type: "Hello"
[Message box]

[Send]
```

- Shows message queue status
- Explains "Queued → Sent → Delivered" flow
- Success: "Great! You sent your first message"

**7C: Queue Behavior Explanation**

```
Understanding Queued Messages

"Queued" = Normal, not broken!

When you're offline:
• Messages wait in queue
• Send automatically when connected
• You can see queue status anytime

This is how mesh networks work.
It's a feature, not a bug!

[Got It]
```

**7D: Record Test Video**

```
Try Recording Video

Tap camera button → Record → Stop

[Camera Icon]

Videos are saved locally and uploaded 
to permanent storage when ready.

[Try It Now]
```

- Quick 5-second recording
- Shows upload progress
- Explains IPFS storage concept simply

---

## Post-Onboarding Experience

### First Launch After Onboarding

**Home Screen Welcome:**

```
[Dismiss Welcome Card]

You're All Set!

✓ Identity created
✓ Recovery phrase saved
✓ Emergency protection active
✓ Connected to mesh network

Start by:
• Adding contacts
• Sending messages
• Recording videos

[Get Started]
```

### Ongoing Reminders

**If Seed Phrase Not Backed Up:**

- Persistent banner: "Backup your recovery phrase"
- Dismissible but returns daily
- Goes away only after backup verified

**If Duress PIN Not Set:**

- Weekly reminder
- Lower priority than seed phrase
- Can be permanently dismissed

---

## Onboarding Analytics

**Track Success Metrics:**

- % completing each step
- Average time per step
- Drop-off points
- Common errors/confusion
- Support requests by step

**Target Metrics:**

- Completion rate >90%
- Average time <12 minutes
- Step 3 (seed phrase) <5% failure rate
- Step 7 (tutorial) engagement >85%

---

## Alternative Flows

### Advanced User Option

```
[Skip Tutorial] button on Step 7

Warning:
"Are you familiar with mesh networks and 
blockchain wallets? Skipping is not recommended."

[Yes, Skip]  [No, Continue Tutorial]
```

### Returning User (Wallet Recovery)

```
Welcome Back

To restore your account:

1. Enter your 12-word recovery phrase
2. Set new PINs
3. Reconnect to network

[Restore Account]
[Create New Account Instead]
```

---

## Accessibility Accommodations

**Visual Impairments:**

- Screen reader announces each step
- High contrast mode available
- Font size adjustable during onboarding

**Motor Impairments:**

- Large touch targets on all buttons
- No time-limited interactions
- Voice input alternative for seed phrase entry

**Literacy Challenges:**

- Video tutorials alternative to text
- Icon-based navigation
- Translation available before starting

---

## Error Prevention

**Common Mistakes:**

**Mistake 1: Screenshot Seed Phrase**

- Detect screenshot attempt
- Warning: "Don't screenshot! Write on paper only"
- Explain digital copies can be stolen

**Mistake 2: Skip Backup**

- Cannot skip Step 3 entirely
- Can dismiss temporarily but persistent reminder
- Final warning before exiting onboarding

**Mistake 3: Same PIN for Normal/Duress**

- Real-time validation prevents this
- Clear error: "PINs must be different"
- Explain why duress needs to be different

---

## Success Criteria

**Completion:**

- > 90% of users complete onboarding
    
- <10 minutes for 75% of users
- <3% abandon during process

**Comprehension:**

- > 80% correctly explain wallet privacy
    
- > 90% successfully activate panic mode in test
    
- > 85% understand message queuing
    

**Retention:**

- > 70% return within 24 hours
    
- > 50% send 5+ messages in first week
    
- <20% request support during onboarding

---

## Status

**Current State:** Flow designed, ready for implementation  
**Next Steps:** Create UI mockups, user testing  
**Blockers:** None

---

## Related Documents

- [[09-ux-principles]]: Design philosophy and standards
- [[09B - UX - Core Flows]]: Post-onboarding user actions
- [[09C-ux-security-interface]]: Security indicators and settings
- [[04A-identity-system]]: Technical wallet implementation
- [[08 - Security & Encryption]]: Panic mode and duress PIN technical details