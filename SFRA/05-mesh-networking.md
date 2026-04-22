---
title: 06 - IPFS Integration
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 7/10
tags: [infrastructure, ipfs, storage, technical]
---

## Overview

The mesh networking layer enables device-to-device communication through multi-hop routing without relying on cellular or internet infrastructure. User phones connect to relay nodes (Raspberry Pi devices) which form a self-organizing, self-healing network using Babel routing protocol. This component defines routing strategy, node discovery, bandwidth management, and offline message queuing for delay-tolerant networking.

**What Success Looks Like:** Messages route through 5+ relay hops reliably. Network adapts when nodes fail. Users can send messages while "offline" from relays, which are queued locally and transmitted automatically when network detected.

---

## Requirements

### Routing Strategy

**Two-Tier Architecture:**
- **Relay Nodes** (Raspberry Pi): Always-on backbone, run Babel routing
- **User Phones**: Leaf nodes only, do NOT relay for others

**Rationale:** User phones moving/powering off makes poor relay infrastructure. Battery life preserved by leaf-only design.

**Routing Protocol: Babel**
- Proven, stable, distance-vector protocol
- Self-organizing, no configuration needed
- Handles link failures gracefully
- Scales to 100+ nodes
- Uses metric-based path selection (prefers stable, fast links)

**Network Parameters:**
- Maximum hops: 7 (covers ~1-1.5 miles)
- Route cache timeout: 10 minutes
- WiFi Direct range: 200-500 feet per hop
- BLE discovery range: 30-100 feet

### Node Discovery

**Hybrid Approach:**
- **BLE Discovery:** Low-power scanning for nearby relay nodes
- **WiFi Direct:** High-bandwidth data connection once discovered

**Connection Process:**
1. BLE discovery (background scan)
2. WiFi Direct handshake
3. IP address assigned
4. Ready to send/receive

**Battery Optimization:**
- User phones don't run routing protocol
- Adaptive BLE scanning (aggressive when queue exists)
- WiFi Direct only activated for actual transfers

### Bandwidth Management

**Priority Queue System:**

**Priority 1 - High (Critical):**
- Emergency broadcasts
- Panic mode triggers
- Network control messages
- Routing protocol packets

**Priority 2 - Medium (Standard):**
- Text messages
- Small photos (<500KB)
- Message acknowledgments

**Priority 3 - Low (Bulk):**
- Video chunks
- Large photos
- Media downloads

**Queue Processing:**
- FIFO within each priority level
- High priority messages preempt lower priorities
- Video throttled to 50% available bandwidth
- Text messages always get through even during video upload

### Offline Message Queuing

**Local Queue (User Phone):**

Users can send messages while not connected to any relay node. Messages stored locally in encrypted queue and auto-transmitted when relay detected.

**Queue Storage:**
- Database: SQLite (Android Room)
- Encryption: Android Keystore
- Capacity: 1000 messages OR 100MB
- Persistence: Survives app restart, reboot

**Queue Behavior:**
- Messages created even when offline
- TTL timer only starts when handed to relay (not while in local queue)
- Auto-transmit when relay detected
- Retry logic: 10 attempts over 24 hours

**Adaptive BLE Scanning:**
- Phase 1 (0-5 min): Scan every 10s (aggressive)
- Phase 2 (5-30 min): Scan every 30s (moderate)
- Phase 3 (30+ min): Scan every 2 min (conservative)
- Phase 4 (no queue): Scan every 5 min (background)

**Battery Impact:** ~1% per 16 hours background scanning

**Queue Management:**
- At 80% full: Warning notification
- At 100% full: Block new sends
- User actions: Delete, retry manually, mark urgent

### Store-and-Forward (Relay Nodes)

**When Recipient Offline:**

Relay nodes temporarily store messages for offline recipients until they reconnect.

**Storage Strategy:**
- Each relay node: 32GB microSD (28GB available after OS)
- Per-message storage: ~1KB text, ~300KB photo, ~3MB video chunk
- Capacity: Millions of text messages, thousands of photos
- TTL enforcement: Delete after expiration

**Message TTL by Type:**
- Text messages: 6 hours
- Photos: 24 hours
- Video chunks: 72 hours
- Emergency broadcasts: 12 hours

**Priority-Based Storage:**
- Priority 1 never deleted (until delivered or 12 hours)
- Priority 2 deleted only if disk >90% full
- Priority 3 deleted when disk >80% full

### Gap Handling

**Primary Strategy: Store-Carry-Forward (Sneakernet)**
- Users moving between areas act as mobile bridges
- Phone downloads messages from Area A
- User walks to Area B
- Phone uploads messages to Area B relays
- Delay: 15-30 minutes typical
- Cost: $0 (uses natural movement)

**Secondary: Directional Antennas**
- For fixed gaps with line-of-sight
- $20-40 WiFi directional antenna
- Range: 1-2 miles between relay nodes

**Tertiary: Additional Relay Nodes**
- Fill critical gaps strategically
- Lampposts, trees, friendly businesses

---

## Implementation Notes

**Technology Stack:**
- libp2p for networking foundation
- Babel routing protocol
- Android WiFi Direct APIs
- Android BLE APIs for discovery

**Connection State Machine:**
```
OFFLINE (no relay detected)
  ↓ BLE detects relay
CONNECTING (WiFi Direct handshake)
  ↓ Connection successful
ONLINE (transmitting queue)
  ↓ Queue empty OR out of range
OFFLINE
```

**Reliability Features:**
- Acknowledgment system confirms delivery
- Automatic retry with exponential backoff
- Self-healing (routes around failed nodes)
- Heartbeat/keepalive every 30 seconds

---

## Success Criteria

**Routing Performance:**
- 95%+ delivery success rate (5-hop max)
- <30 second average delivery time
- <5% packet loss rate
- Routes adapt to failures <60 seconds

**Queue Performance:**
- Messages persist across reboots
- Auto-transmission within 5 min of relay detection
- <1% message loss from queue
- Users understand "queued" ≠ "failed"

**Battery Life:**
- Adaptive scanning uses <2% battery per day
- Users get 12-24 hours normal use
- Background service doesn't drain excessively

**Reliability:**
- Store-and-forward holds messages 7+ days
- Relay node uptime >95%
- Failed relays don't black-hole messages

---

## Status

**Well-Defined:**
- Routing protocol selected (Babel)
- Two-tier architecture clear
- User phone queue management complete
- Relay store-and-forward specified
- Priority system defined
- Battery optimization strategy

**Needs Work:**
- Field testing with 50+ nodes
- Performance tuning under actual load
- libp2p integration validation
- Queue parameter tuning from real data

**To Reach 10/10:** Field deployment validation, performance metrics from 100+ node network, queue timeout optimization based on real latency.

---

## Dependencies

- **03 Hardware Specifications:** Raspberry Pi relay node specs
- **04 Communication Protocol:** Matrix message format
- **08 Security & Encryption:** Messages encrypted before queuing
- **09 UX Series:** Queue status indicators, network status display