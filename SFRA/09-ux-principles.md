---
title: 09 - UX - Principles
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 8/10
tags: [user-facing, ux, design, principles]
---
---

## Overview

The mesh network app must be usable by non-technical people under high stress, often with limited literacy or smartphone experience. Users face real danger and need confidence that the system is secure and working. These design principles ensure the app is accessible, trustworthy, and resilient to user error.

**Success Vision:** A first-time user with basic literacy can install the app, create their identity, send a message, and record video documentation within 10 minutes, without external help.

---

## Core Design Principles

### Offline-First Mindset

**Default Assumption: No Internet Connectivity**

The app treats offline operation as the normal state, not an error:

- Every feature available offline (except IPFS sync)
- Clear status indicators for network state
- Never show "error" messages for normal offline conditions
- Use positive language: "Searching for mesh..." not "Connection failed"
- "Queued" is normal behavior, not a failure

**Why This Matters:**

- Users won't panic when offline
- Reduces perceived system failures
- Builds confidence in system reliability
- Matches real-world mesh network behavior

### Security-Visible

**Trust Through Transparency**

Users must always know their security status:

**Always Visible:**

- Encryption status (green lock icon in header)
- Contact verification status (checkmark badges)
- Network connection state
- Backup reminder until seed phrase saved

**Easily Accessible:**

- Panic mode via physical button combo (Power + Volume Down)
- Security settings one tap from home screen
- Duress PIN option prominently featured
- Wallet privacy warnings in onboarding

**Why This Matters:**

- Users can verify messages are encrypted
- No hidden security states
- Emergency features readily available
- Builds trust through visibility

### Simplicity Over Features

**Focus on Core Path**

Most users need three things:

1. Send text messages
2. Record and share video evidence
3. View received content

**Implementation:**

- Core features on home screen
- Advanced features hidden in settings
- No technical jargon
- Single-purpose screens when possible
- Progressive disclosure (show advanced features only when needed)

**Examples of Simplification:**

- "Send Message" not "Initiate Encrypted Communication"
- "Video" not "IPFS Media Upload"
- "Contacts" not "Wallet Address Book"
- "Settings" not "Configuration Parameters"

### Stress-Resilient

**Design for High-Pressure Situations**

Users may operate the app while:

- Under immediate threat
- Highly stressed or emotional
- Low lighting conditions
- Moving or hiding
- One-handed operation

**Design Requirements:**

- Large touch targets (48dp minimum per Android guidelines)
- High contrast text and icons (WCAG AAA compliance)
- Panic mode accessible instantly
- Undo available for destructive actions
- Confirmation dialogs for irreversible operations

**Color Coding:**

- Green = Secure/Good
- Yellow = Warning/Attention
- Red = Danger/Error
- Gray = Neutral/Inactive

### Error Prevention

**Fail-Safe Defaults**

The system should make it hard to make mistakes:

**Automatic Behaviors:**

- Encryption always on (no option to disable)
- Seed phrase must be backed up before full access
- Duress PIN configured during onboarding
- Messages auto-save as drafts
- Video auto-saves before upload

**Confirmations Required For:**

- Deleting conversations
- Removing contacts
- Sharing IPFS links outside app
- Disabling security features
- Activating panic mode

**Clear Warnings For:**

- Wallet privacy violations (connecting to exchanges)
- Sending to unverified contacts
- Low storage space affecting queue
- Network connection loss during video upload

---

## Language and Accessibility

### Plain Language Requirements

**Avoid:**

- Technical jargon (blockchain, IPFS, encryption keys)
- Academic terminology
- Acronyms without explanation
- Passive voice
- Conditional language ("might", "could", "may")

**Use:**

- Active voice
- Short sentences (<15 words average)
- Common words
- Direct instructions
- Concrete examples

**Examples:**

- ❌ "Your cryptographic key pair has been generated"
    
- ✅ "Your secure identity is ready"
    
- ❌ "Message queued pending relay node availability"
    
- ✅ "Message waiting for network connection"
    

### Multilingual Support

**Phase 1 Languages (MVP):**

- English
- Arabic
- Burmese (Myanmar)

**Phase 2 Languages:**

- Spanish
- French
- Tigrinya (Eritrea)
- Oromo (Ethiopia)

**Design Considerations:**

- Right-to-left (RTL) layout support for Arabic
- Unicode font support for all scripts
- Cultural sensitivity in icons and colors
- Local date/time formats
- Voice input support where possible

### Accessibility Features

**Visual:**

- Screen reader compatible (TalkBack/VoiceOver)
- Font size adjustable (120%-200%)
- High contrast mode
- Dark mode (reduces screen visibility)

**Motor:**

- Minimum touch target: 48dp
- Gesture alternatives for all actions
- Long-press alternatives for complex gestures
- One-handed operation where possible

**Literacy:**

- Icons with text labels
- Voice messages as alternative to text
- Video tutorials (no reading required)
- Pictographic instructions

---

## Information Hierarchy

### What Users Need to Know, When

**First 30 Seconds:**

- Is my message secure? (Yes - green lock icon)
- Did my message send? (Status indicator)
- Do I have new messages? (Badge count)

**First 5 Minutes:**

- How do I send a message?
- How do I record video?
- How do I add a contact?

**First Hour:**

- Why is my message "queued"?
- How do I verify a contact?
- What is panic mode?

**First Week:**

- How does wallet privacy work?
- What are governance votes?
- How do I back up my data?

### Progressive Disclosure

**Hide Complexity Until Needed:**

- Show basic message controls first
- Reveal queue management only when messages are queued
- Show governance features after 7 days of use
- Advanced settings behind two-level menu
- Emergency features always accessible but not prominent

---

## Feedback and Affordances

### Visual Feedback for Every Action

**Instant Feedback (<100ms):**

- Button press animations
- Checkboxes toggle visually
- Scroll response
- Touch feedback (vibration)

**Quick Feedback (<1 second):**

- Message sent confirmation
- Contact added success
- Settings saved

**Progress Indicators (>1 second):**

- Video upload progress bar
- IPFS chunk upload count
- Seed phrase verification steps
- Network searching animation

### Affordances (Design Hints)

**Buttons Look Clickable:**

- Rounded corners
- Shadow or border
- Color contrast from background
- Label inside button

**Input Fields Look Editable:**

- Border visible
- Cursor appears on focus
- Placeholder text hints at content
- Label above field

**Swipeable Elements Show Hint:**

- Partial visibility of next item
- Gesture indicator on first use
- Tutorial highlights swipe actions

---

## Error Messages and Failures

### What NOT to Say

**Never Use:**

- "Error 404"
- "Connection timed out"
- "System failure"
- "Null reference exception"
- "Operation failed"

**Always Explain:**

- What happened
- Why it happened
- What the user can do
- How to prevent it next time

**Examples:**

- ❌ "Upload failed"
    
- ✅ "Video too large. Try recording shorter clips (under 5 minutes)"
    
- ❌ "Network error"
    
- ✅ "No nearby relay nodes found. Move to different location or try again later"
    

### Failure Recovery

**Automatic Recovery When Possible:**

- Retry message send (up to 3 times)
- Auto-resume interrupted uploads
- Restore drafts after app crash
- Re-establish connections automatically

**User Actions When Needed:**

- Clear instructions ("Tap here to retry")
- Explanation of the issue
- Alternative approaches if available
- Support contact if all else fails

---

## Success Criteria

**Usability Metrics:**

- > 90% of test users complete onboarding without help
    
- Average time to send first message: <2 minutes
- Average time to record and share video: <5 minutes
- <5% of users require support after onboarding

**Comprehension:**

- Users correctly explain encryption status (>80%)
- Users understand "queued" means waiting, not error (>90%)
- Users can activate panic mode under stress simulation (>95%)

**Satisfaction:**

- System Usability Scale (SUS) score >70
- User-reported confidence in security >4/5
- Willingness to recommend to others >80%

---

## Status

**Current State:** Design principles defined, ready for mockups  
**Next Steps:** Create detailed screen designs ([[09A-ux-onboarding]], [[09B - UX - Core Flows]])  
**Blockers:** None

---

## Related Documents

- [[09A-ux-onboarding]]: 7-step onboarding flow implementation
- [[09B - UX - Core Flows]]: Send message, record video, queue management
- [[09C-ux-security-interface]]: Security indicators and panic mode
- [[08 - Security & Encryption]]: Technical security implementation
- [[04A-identity-system]]: Wallet creation and recovery