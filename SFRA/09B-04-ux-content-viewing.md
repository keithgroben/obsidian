---
title: Content Viewing Workflow
section: 9
subsection: B.4
parent: 09B-00-ux-core-flows
related:
  - 09B-01-ux-messaging-flow
  - 09B-02-ux-video-flow
  - 06-ipfs-integration
description: Workflow for viewing received messages and videos, including IPFS content download with quality options
tags: [ux, viewing, ipfs, playback, messages, workflows]
version: 2.0
last_updated: 2025-10-17
word_count: 480
---

# Content Viewing Workflow

## View Received Messages

### New Message Notification

**Lock screen or notification tray:**
```
Alice
"Are you safe?"
Just now

[Tap to view]
```

**In-app notification:**
- Badge count on conversation list
- Preview in conversation item
- Unread indicator (bold text)

### Conversation View

**Message Display:**
- Most recent messages at bottom
- Sender name + timestamp on each message
- Encryption indicator always visible (🔒)
- Read/Unread status
- Delivery receipts (✓ or ✓✓)

**Message Bubbles:**
- Sent messages: Blue background, right-aligned
- Received messages: Gray background, left-aligned
- System messages: Center-aligned, italic

## View Received Video

### IPFS Video Link Display

**In conversation:**
```
Alice sent a video
ipfs://QmX7g...

[Loading preview...]
⬇ Download to watch (2.3 MB)

📹 Tap to download
```

### Download Options

**Tap on video message shows:**
```
Download Video

Quality:
● Auto (recommended)
○ High Quality (5 MB)
○ Medium Quality (2 MB)
○ Low Quality (500 KB)

[Download and Play]
```

**Quality Details:**
- **Auto:** Adapts to available bandwidth
- **High:** Original 480p upload quality
- **Medium:** Compressed for faster download
- **Low:** Maximum compression, lowest quality

### Download Progress

**While downloading:**
```
Downloading video...
██████████░░ 60% (1.8 MB / 3 MB)

Estimated: 30 seconds

Speed: 100 KB/s

[Cancel Download]
```

**Progress indicators:**
- Percentage complete
- Data downloaded / total size
- Time remaining estimate
- Current download speed

### Video Playback

**Player controls:**
- Full-screen video player
- Play/Pause button
- Seek bar (scrub through video)
- Volume control
- Fullscreen toggle
- Close button (X)

**Additional options:**
- Save locally (download to device storage)
- Share IPFS link (copy link to clipboard)
- Report content (flag for moderator review)

### Playback Issues

**Slow Download:**
```
⚠️ Slow Connection

Download may take several minutes.
Try lower quality or wait for 
better network conditions.

[Switch to Low Quality] [Wait]
```

**Download Failed:**
```
❌ Download Failed

Unable to retrieve video from IPFS.
Try again later.

[Retry] [Cancel]
```

**Corrupted Video:**
```
❌ Cannot Play Video

Video file appears corrupted.
Ask sender to re-upload.

[Delete] [Report Issue]
```

## Contact Verification Status

### Unverified Contact

**Warning displayed:**
```
Alice (Unverified)
⚠️ Not yet verified

Messages are encrypted, but you 
haven't confirmed this is really Alice.

[Verify Identity] [Learn More]
```

### Verified Contact

**Checkmark badge shown:**
```
Alice ✓
Endorsed by 2 contacts

Messages are encrypted and 
identity verified.

[View Endorsements]
```

## Media Gallery

### Access Gallery
Settings → Media or Long-press on video message

### Gallery View
```
Sent Videos (3)
• Evidence.mp4 - Oct 15 (Pinned ✓)
• Protest.mp4 - Oct 14 (Uploading 67%)
• Interview.mp4 - Oct 12 (Pinned ✓)

Received Videos (5)
• Alice/Video1.mp4 - Oct 16
• Bob/Evidence.mp4 - Oct 15
[...]

[Manage Storage]
```

**Actions per video:**
- Play/Download
- View IPFS link
- Share link
- Delete local copy
- Re-upload (if pin failed)

## Storage Management

**View storage usage:**
```
Media Storage

Videos: 124 MB
Photos: 45 MB
Queue: 12 MB
Total: 181 MB / 3 GB

[Clear Cache] [Delete Old Media]
```

**Automatic cleanup:**
- Downloaded videos: Keep 30 days
- Cached thumbnails: Keep 7 days
- Failed uploads: Keep until retried

## Related Documentation

- **Messaging Flow:** [09B-01-ux-messaging-flow](09B-01-ux-messaging-flow.md)
- **Video Recording:** [09B-02-ux-video-flow](09B-02-ux-video-flow.md)
- **IPFS Integration:** [06-ipfs-integration](06-ipfs-integration.md)
