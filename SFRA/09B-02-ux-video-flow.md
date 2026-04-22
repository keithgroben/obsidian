---
title: Video Recording Workflow
section: 9
subsection: B.2
parent: 09B-00-ux-core-flows
related:
  - 09B-03-ux-queue-management
  - 07-video-handling
  - 06-ipfs-integration
description: Workflow for recording, compressing, and uploading video documentation with progress tracking and IPFS storage
tags: [ux, video, recording, ipfs, compression, workflows]
version: 2.0
last_updated: 2025-10-17
word_count: 580
---

# Video Recording Workflow

## Record Video Flow

### Starting Point
Conversation screen with message history and compose bar.

### Recording Process

**Step 1: Open Camera**
- Tap camera icon in bottom toolbar
- Camera interface opens full-screen
- Viewfinder shows preview
- Red record button centered at bottom

**Step 2: Start Recording**
- Tap red record button to begin
- Button pulses to indicate recording
- Timer appears showing elapsed time
- Maximum duration: 5:00 (5 minutes)
- Countdown appears at 4:30 (30 seconds remaining warning)

**Step 3: Stop Recording**
- Tap stop button (red square)
- Recording ends immediately
- Preview screen appears

### Preview and Options

**Review Screen Shows:**
- Video thumbnail with play button
- Duration display
- Estimated file size after compression
- Three action buttons

**Actions:**
```
[Discard]  [Re-record]  [Send]
```

**Discard:** Deletes video, returns to conversation  
**Re-record:** Retakes video, discards current  
**Send:** Compresses and queues for upload

### Compression and Upload

**Step 4: Automatic Processing**
When user taps [Send]:

1. Compression begins (on-device)
   - "Compressing video..." with spinner
   - 720p → 480p, H.265 codec
   - Target: 3-5MB per minute
   - Takes 10-30 seconds

2. Chunking (behind the scenes)
   - Split into 256KB chunks
   - 32 chunks for typical 2-minute video
   - Each chunk numbered and tagged

3. Queue for upload
   - Chunks enter upload queue
   - Progress indicator appears in chat

**Step 5: Upload Progress**
Message bubble in conversation shows:
```
Uploading video...
█████████░░░ 67% (21/32 chunks)

[View Progress] [Cancel]
```

**Step 6: Upload Complete**
Final message state:
```
Video uploaded successfully
ipfs://QmT5Nv...yCxX

📹 [Tap to view]
Pinned to 2 services ✓
```

## Storage Warnings

### Low Storage Alert
When available space < 500MB:

```
⚠️ Low Storage

Only 430 MB available. 
Video quality may be reduced.

[Free Up Space] [Record Anyway]
```

**Record Anyway:** Continues with lower quality  
**Free Up Space:** Opens storage management

### Critical Storage Alert
When available space < 100MB:

```
❌ Storage Full

Cannot record video.
Free up space to continue.

[Open Settings]
```

**Blocks recording** until space available.

## Error Scenarios

### Video Too Large
If recording exceeds 5 minutes:

```
⚠️ Video Too Large

Maximum: 5 minutes per video
Your video: 7 minutes 32 seconds

Try recording shorter clips.

[Re-record] [Cancel]
```

### Compression Failed
If on-device compression errors:

```
❌ Compression Failed

Unable to compress video.
Try again or record shorter clip.

[Retry] [Discard]
```

### Upload Interrupted
If network lost during upload:

```
⚠️ Upload Paused

Network connection lost.
Upload will resume automatically 
when connection restored.

Progress saved: 21/32 chunks

[View Queue] [Cancel Upload]
```

## Camera Interface Elements

### On-Screen Controls
- Red record/stop button (center bottom)
- Timer (top center)
- Flash toggle (top right)
- Camera flip (front/back, top left)
- Cancel (X icon, top left corner)

### Recording Indicators
- Pulsing red button during recording
- Elapsed time counter
- Storage space remaining (if <1GB)
- 30-second warning before 5-minute limit

## Quality Settings

### Default (Automatic)
- Resolution: 480p (854×480)
- Codec: H.265/HEVC
- Bitrate: 500-700 kbps
- Frame rate: 24 fps
- Audio: AAC 64 kbps mono

**Result:** ~3-5MB per minute

### Advanced (Settings Menu)
Users can adjust in Settings > Video:
- Quality: Low (240p), Standard (480p), High (720p)
- Frame rate: 15, 24, or 30 fps
- Audio: On/Off

**Note:** Higher quality = larger files = longer upload times

## Upload Queue Integration

Videos automatically use **Low Priority** queue:
- Text messages sent first
- Videos throttled to 50% bandwidth
- Can be promoted to High Priority if critical

See [09B-03-ux-queue-management](09B-03-ux-queue-management.md) for queue details.

## Related Documentation

- **Queue Management:** [09B-03-ux-queue-management](09B-03-ux-queue-management.md)
- **Video Technical Details:** [07-video-handling](07-video-handling.md)
- **IPFS Storage:** [06-ipfs-integration](06-ipfs-integration.md)
