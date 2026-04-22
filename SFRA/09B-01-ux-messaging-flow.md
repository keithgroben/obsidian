---
title: Messaging Workflow
section: 9
subsection: B.1
parent: 09B-00-ux-core-flows
related:
  - 09B-03-ux-queue-management
  - 09C-ux-security-interface
  - 09A-ux-onboarding
description: Detailed workflow for sending text messages through the mesh network with delivery status tracking and contact management
tags: [ux, messaging, contacts, delivery-status, workflows]
version: 2.0
last_updated: 2025-10-17
word_count: 520
---

# Messaging Workflow

## Send Message Flow

### Starting Point
Home screen showing conversation list with existing contacts and recent messages.

### Standard Message Send

**Step 1: Select Conversation**
- Tap contact from conversation list
- Opens chat interface with message history
- Encryption indicator visible in header (🔒 green lock)

**Step 2: Compose Message**
- Type message in input field at bottom
- Draft automatically saved as you type
- Character counter shows remaining space (if applicable)

**Step 3: Send Message**
- Tap send button (paper plane icon)
- Message immediately enters queue
- Status icon appears next to message

### Message Status Progression

**Queued State**
- Gray background bubble
- Clock icon (⏱️)
- Text: "Queued • Waiting for network"
- Meaning: Message stored locally, waiting for relay connection

**Searching State**
- Gray background bubble
- Animated dots (•••)
- Text: "Searching for network..."
- Meaning: BLE scanning for nearby relay nodes

**Sending State**
- Light blue background bubble
- Spinner animation
- Text: "Sending through mesh..."
- Meaning: Message hopping through relay nodes

**Sent State**
- Blue background bubble
- Single checkmark (✓)
- Text: "Sent" + timestamp
- Meaning: Message reached recipient's relay node

**Delivered State**
- Blue background bubble
- Double checkmark (✓✓)
- Text: "Delivered" + timestamp
- Meaning: Recipient's device received and decrypted message

**Failed State**
- Red background bubble
- X icon
- Text: "Failed after 24 hours"
- Action button: [Retry]
- Meaning: Message expired before delivery (rare)

## Add Contact Flow

### Manual Contact Addition

**Starting Point:** Contacts screen

**Step 1: Initiate Addition**
- Tap "Add Contact" button (+)
- Opens contact entry form

**Step 2: Enter Details**
```
Name: [Text input]
Wallet Address: [0x... or QR scan icon]
```

**Step 3: Optional Verification**
- Tap [Request Endorsement] to verify identity through mutual contacts
- Select endorsers from list of mutual connections

**Step 4: Confirm**
- Tap "Add" button
- Contact appears in conversation list
- Ready to send first message

### QR Code Scanning

**Alternative entry method:**

1. Tap QR icon next to wallet address field
2. Camera opens with viewfinder
3. Point at contact's displayed QR code
4. Address auto-fills when detected
5. Enter name and tap "Add"

**Benefits:** Faster, no typing errors, works in-person

### Invitation Code Entry

**Third option for adding contacts:**

1. Tap "Add via Invitation Code"
2. Enter 8-character alphanumeric code
3. System looks up wallet address on network
4. Name auto-populated (or edit)
5. Confirm and add

**Use case:** Remote contact addition, shared via other channels

## Visual Feedback

### Instant Feedback (<100ms)
- Button press animations
- Keyboard input response
- Scroll smoothness
- Haptic feedback on send

### Quick Feedback (<1 second)
- Message sent confirmation
- Contact added success message
- Draft saved indicator

### Progress Indicators (>1 second)
- Message status updates
- Contact verification progress
- Network searching animation

## Error Handling

### Common Scenarios

**Network Not Found**
```
⚠️ No Network Connection

Your message is queued and will 
send when you're near a relay node.

[View Queue] [Retry Search]
```

**Invalid Wallet Address**
```
⚠️ Invalid Address

Please check the wallet address.
It should start with "0x" and be 
42 characters long.

[Edit] [Scan QR Instead]
```

**Contact Already Exists**
```
⚠️ Contact Already Added

This wallet address is already 
in your contacts as "Alice".

[View Contact] [Cancel]
```

## Related Documentation

- **Queue Management:** [09B-03-ux-queue-management](09B-03-ux-queue-management.md)
- **Security Interface:** [09C-ux-security-interface](09C-ux-security-interface.md)
- **Onboarding:** [09A-ux-onboarding](09A-ux-onboarding.md)
