---
title: Queue Management Workflow
section: 9
subsection: B.3
parent: 09B-00-ux-core-flows
related:
  - 09B-01-ux-messaging-flow
  - 09B-02-ux-video-flow
  - 05-mesh-networking
description: Workflow for viewing and managing queued messages and videos waiting to be sent through the mesh network
tags: [ux, queue, offline, delay-tolerant, workflows, priority]
version: 2.0
last_updated: 2025-10-17
word_count: 620
---

# Queue Management Workflow

## View Queue Status

### Access Queue
**From any screen:** Tap status bar indicator showing queue count
```
[Network Icon] 3 queued

Tap to view details
```

### Queue Management Screen

**Display shows all queued items:**

```
Queued Messages (3)

Message to Alice
"Are you safe?" • Queued 2h 15m
Priority: Urgent
[View] [Cancel]

Video to Human Rights Org
"Evidence.mp4" • Uploading 45%
Priority: High
[View Progress] [Cancel]

Message to Bob
"Meeting at 7pm" • Queued 15m
Priority: Normal
[View] [Cancel]

[Queue Settings]
```

### Status Bar Indicator States

**Connected (No Queue)**
```
[Network: ● 3 hops] 
Green dot, no badge
```

**Queue Pending**
```
[Network: ● 3 hops] [3]
Green dot, badge showing count
```

**Offline with Queue**
```
[Network: Offline] [5]
Gray indicator, badge showing count
```

**Searching**
```
[Network: ○○○] [2]
Animated dots, badge showing count
```

## Queue Actions

### Cancel Queued Message

**Step 1:** Tap [Cancel] on queued item

**Step 2:** Confirmation dialog appears
```
Cancel this message?
It has not been sent yet.

[No, Keep It] [Yes, Cancel]
```

**Step 3:** If confirmed
- Message removed from queue
- Notification: "Message cancelled"
- Queue count updates

### Change Priority

**Step 1:** Long-press queued message

**Step 2:** Context menu appears
```
Move to:
• Urgent (Critical messages)
• High Priority (Important)
• Normal Priority (Standard)
• Low Priority (Can wait)

[Cancel]
```

**Step 3:** Tap selection
- Priority updated immediately
- Queue re-orders automatically
- Higher priority items sent first

### View Progress

**For video uploads in progress:**

Tap [View Progress] to see detailed status:
```
Video Upload Progress

Chunks: 24/32 completed (75%)
Estimated: 2 minutes remaining

Speed: 256 KB/s
Quality: Standard (480p)

[Pause Upload] [Cancel]
```

## Queue Settings

### Access Settings
From Queue Management Screen → [Queue Settings]

### Auto-Send Priority
```
☑ Retry urgent messages more frequently
☑ Send high priority before normal
☑ Drop low priority after 24 hours
```

### Storage Management
```
Queue Storage Limit:
○ 50 MB (recommended)
○ 100 MB
● 200 MB
○ Custom: [___] MB

Currently used: 47 MB / 200 MB
```

### Notifications
```
☑ Notify when message sent
☑ Notify when message delivered
☐ Notify for each queue status change
☑ Daily queue summary (evening)
```

### Cleanup
```
Auto-delete after:
○ 24 hours
● 7 days
○ 30 days
○ Never

[Clear All Sent] [Clear All Failed]
```

## Queue Behavior

### Automatic Processing

**Priority Order:**
1. **Urgent** - Sent immediately when network available
2. **High** - Sent before normal, parallel processing
3. **Normal** - Standard queue order (FIFO)
4. **Low** - Sent when bandwidth available

**Retry Logic:**
- Failed items retry automatically
- Exponential backoff: 1min → 5min → 15min → 1hr
- Maximum 10 attempts over 24 hours
- User notified after final failure

**TTL (Time To Live):**
- Text messages: 6 hours
- Photos: 24 hours
- Videos: 72 hours
- Urgent items: 12 hours (never auto-deleted)

### Adaptive Scanning

When queue contains items:

**Phase 1 (0-5 min):** Scan every 10s (aggressive)  
**Phase 2 (5-30 min):** Scan every 30s (moderate)  
**Phase 3 (30+ min):** Scan every 2 min (conservative)  
**Phase 4 (no queue):** Scan every 5 min (background)

**Battery Impact:** ~1% per 16 hours

### Queue Warnings

**80% Full**
```
⚠️ Queue Nearly Full

Queue: 160 MB / 200 MB used
Consider clearing sent items or 
increasing storage limit.

[Free Up Space] [Settings]
```

**100% Full**
```
❌ Queue Full

Cannot queue new messages.
Clear space to continue.

[View Queue] [Clear Sent Items]
```

## Understanding Queue States

### "Queued" ≠ "Failed"

**User Education:**
```
ℹ️ What does "Queued" mean?

Your message is safely stored and 
will send automatically when:
• You're near a relay node
• Network becomes available
• Connection is restored

This is how mesh networks work.
It's a feature, not a bug!

[Got It]
```

### Expected Delays

**Urban Area:** 1-10 minutes typical  
**Rural Area:** 10-60 minutes typical  
**Network Outage:** Hours to days acceptable  
**Critical Content:** Use "Urgent" priority

## Related Documentation

- **Messaging Flow:** [09B-01-ux-messaging-flow](09B-01-ux-messaging-flow.md)
- **Video Flow:** [09B-02-ux-video-flow](09B-02-ux-video-flow.md)
- **Mesh Networking:** [05-mesh-networking](05-mesh-networking.md)
