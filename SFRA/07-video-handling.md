---
title: 07 - Video Handling
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 7/10
tags: [infrastructure, video, media, compression, technical]
---

## Overview

Video documentation is critical for recording persecution evidence, but video files are large (50-150MB raw) while mesh networks are constrained (1-10 Mbps shared bandwidth). This component defines requirements for making video practical in a delay-tolerant mesh: aggressive compression to 3-5MB per minute, chunked transfer for reliability, and asynchronous delivery with progress tracking.

**What Success Looks Like:** A user records 2 minutes of video (720p), the app compresses it to 8MB, chunks it into 32 pieces, and delivers it to IPFS through the mesh within 10-30 minutes depending on network conditions.

---

## Requirements

### Video Compression
- Reduce 1-minute smartphone video from 100MB to 3-5MB
- Maintain sufficient quality to identify faces and events
- Process compression on-device within 30 seconds
- Work with standard Android video formats (MP4, H.264/H.265)

**Target Specifications:**
- Resolution: 480p (854×480)
- Codec: H.265/HEVC
- Bitrate: 500-700 kbps
- Frame rate: 24 fps
- Audio: AAC 64 kbps mono

**Constraints:** Must use Android MediaCodec API, compression happens before transmission, no user-adjustable settings, all on-device processing.

### Chunked Transfer
- Split compressed video into 256KB chunks
- Each chunk tagged with video ID, sequence number, total chunks
- Chunks sent as standard messages through Matrix protocol
- Enable resume if transfer interrupted
- Allow parallel chunk delivery through multiple routes

### Asynchronous Delivery
- User can send video and continue using app (background transfer)
- Clear progress indication: "Uploading video: 12/32 chunks (37%)"
- Graceful handling of delays (minutes to hours)
- Automatic retry on failed chunks
- Video chunks use lower priority than text messages

### Bandwidth Management
**Priority Queue:**
1. High Priority: Text messages, alerts, critical updates
2. Medium Priority: Photos (smaller, faster)
3. Low Priority: Video chunks (large, delay-tolerant)

Relay nodes must track bandwidth usage, implement priority queuing, and automatically throttle video when network congested.

### Media Library Management
- Gallery view of all videos (sent/received)
- Status indicators: "Uploading (23%)", "Complete", "Failed"
- Retry failed uploads
- View IPFS link when upload complete
- Automatic cleanup of old temporary files

### Progressive Playback
- User can start watching video before all chunks arrive
- Play first N chunks while remaining download
- Show loading indicator when waiting for next chunk
- Standard video players support progressive MP4

---

## Implementation Notes

**Android MediaCodec API:** Use hardware encoding when available for faster compression. Compression must happen before transmission to avoid real-time encoding complexity.

**Chunk Boundaries:** Must align with video keyframes for seamless playback. This ensures smooth viewing experience when chunks arrive out of order.

**Throttling Logic:** Monitor available bandwidth from recent transfer rates. Limit video to 50% of available bandwidth. Pause video transfer if text messages waiting.

---

## Success Criteria

**Performance:**
- 2-minute 720p video compresses to <10MB in <60 seconds
- 32 chunks transfer through 3-hop mesh in <20 minutes (good conditions)
- Text messages maintain <5 second delivery during video upload
- Failed transfers resume from last successful chunk

**User Experience:**
- Recording and compression intuitive (one-button)
- Progress tracking clear and accurate
- No unexplained failures or hangs
- Successful IPFS upload confirmed with shareable link

---

## Status

**Well-Defined:**
- Compression targets and codec strategy
- Chunking approach and chunk size
- Asynchronous delivery model
- Bandwidth priority system
- User experience flow

**Needs Work:**
- Android MediaCodec implementation details
- Chunk reassembly algorithm (handling corrupt chunks)
- Adaptive bitrate logic (if network too slow)
- Testing with various video lengths and network conditions
- Fallback strategies when IPFS bridge unavailable

**To Reach 9/10:** Field validation with real users, performance testing under poor network conditions, refinement of compression settings based on actual documentation needs.

---

## Dependencies

- **05 Mesh Networking:** Relies on priority queuing and store-and-forward
- **06 IPFS Integration:** Video chunks ultimately stored on IPFS
- **08 Security & Encryption:** Video chunks must be encrypted in transit
- **09 UX:** Gallery, progress indicators, playback interface