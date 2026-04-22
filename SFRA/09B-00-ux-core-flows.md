---
title: UX Core Flows - Overview
section: 9
subsection: B.0
parent: 09-00-ux-principles
related:
  - 09B-01-ux-messaging-flow
  - 09B-02-ux-video-flow
  - 09B-03-ux-queue-management
  - 09B-04-ux-content-viewing
  - 09C-ux-security-interface
description: Overview of core user workflows for everyday app usage - messaging, video recording, queue management, and content viewing
tags: [ux, workflows, overview, user-flows]
version: 2.0
last_updated: 2025-10-17
word_count: 320
---

# UX Core Flows - Overview

This document provides an overview of the core user workflows that define everyday interaction with the mesh network app. These flows must be intuitive enough for stressed users to complete without instructions.

## Core Workflows

### Primary Actions
**Messaging** - Send and receive text messages through the mesh network, with clear delivery status indicators showing the message journey from queued to delivered.

**Video Recording** - Capture and share video documentation, with automatic compression, chunking, and upload to IPFS for permanent storage.

**Queue Management** - View and manage messages waiting to be sent, with the ability to adjust priorities, cancel items, or check status.

**Content Viewing** - Access received messages and videos, with options to download IPFS content at different quality levels.

### Supporting Actions
**Contact Management** - Add contacts via wallet address, QR code, or invitation code, with optional identity verification through endorsements.

**Settings Access** - Configure account, privacy, network, notifications, and security preferences through organized settings menu.

## Design Principles Applied

**Stress-Resilient** - Large touch targets, high contrast, and instant access to critical features like panic mode.

**Offline-First** - All features work without internet, with clear status indicators for network state and queued items.

**Error Prevention** - Automatic behaviors (encryption always on, auto-save drafts) and confirmations for destructive actions.

**Progressive Disclosure** - Core features on home screen, advanced features in settings, with complexity revealed only when needed.

## Status Indicators

**Network State** - Connection status always visible in header (Connected, Searching, Offline).

**Message Status** - Clear progression through states: Queued → Searching → Sending → Sent → Delivered.

**Queue Status** - Badge count showing queued items, tappable to view queue management screen.

**Security Status** - Encryption indicator and contact verification badges always visible.

## Related Documentation

For detailed workflows, see:
- **Messaging:** [09B-01-ux-messaging-flow](09B-01-ux-messaging-flow.md)
- **Video:** [09B-02-ux-video-flow](09B-02-ux-video-flow.md)
- **Queue:** [09B-03-ux-queue-management](09B-03-ux-queue-management.md)
- **Viewing:** [09B-04-ux-content-viewing](09B-04-ux-content-viewing.md)
