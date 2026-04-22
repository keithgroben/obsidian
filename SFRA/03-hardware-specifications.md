---
title: 03 - Hardware Specifications
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 9/10
tags: [core, hardware, technical, budget]
---

---

## Overview

Consumer-grade equipment, affordable, covert procurement, solar-capable. All nodes use off-the-shelf hardware maintained with basic tools.

---

## Relay Node (Standard Backbone)

**Raspberry Pi 4 (4GB) - $75**

**Specs:**

- Dual-band WiFi (2.4/5GHz), Bluetooth 5.0
- 64GB microSD for OS, babeld, message queue
- 15W power (grid or solar)
- Fanless/passive cooling
- 3-5 year lifespan

**WiFi Amplification (REQUIRED):**

- **Budget:** Alfa AWUS036ACH USB adapter ($40) + 9dBi antenna ($15) = $55
- **Premium:** Ubiquiti Bullet M2 ($80) or MikroTik BaseBox ($65)
- Range: 300-600ft (budget) or 500-1000ft (premium)
- Power: +3-5W for USB adapter, +5-10W for external AP

**Solar Setup:**

- 25W panel + 25Ah battery = $65
- 48hr autonomy (3 cloudy days)
- Battery replacement every 2-3 years ($20)

**Software:**

- Raspberry Pi OS (Debian)
- babeld (apt repository)
- systemd auto-start

**Total Cost:** $195-220 per node (with WiFi amplification)

---

## Hub Node (High-Performance Video)

**Mini PC with WiFi 6 - $200**

**When needed:** 3-5 nodes at high-traffic locations (church, market, school)

**Specs:**

- WiFi 6 (802.11ax) for 2-3x throughput
- 128GB storage for video chunk buffering
- 30-50W power
- Fanless required
- Examples: Intel NUC, Beelink mini PC

**Software:** Same as relay node (Debian, babeld)

---

## Bridge Node (Internet Gateway)

**Raspberry Pi 4 + Starlink - $600-750**

**Components:**

- Raspberry Pi 4: $75
- Starlink kit: $500 (one-time) + $120/month
- WiFi amplification: $55-80
- Solar backup: $100 (critical for uptime)
- Lockable weatherproof enclosure: $50

**Alternatives to Starlink:**

1. 4G/5G cellular ($50-150 hardware, $30-80/month)
2. Fixed wireless (if available)

**Storage:** 128GB microSD (IPFS cache + logs)

**Software:**

- Everything from relay node (Debian, babeld)
- IPFS gateway service (lightweight HTTP client)
- WireGuard VPN
- Firewall (allow Babel, Matrix, IPFS only)

**Power:** 50-100W (includes satellite modem)

**Physical Security:**

- Hardware kill switch (emergency shutdown)
- Tamper detection
- Hidden location with clear sky view

**IPFS Implementation (UPDATED):**

- NOT full go-ipfs daemon
- Lightweight HTTP gateway (50-100MB RAM vs 300MB)
- Forwards to Pinata/Web3.Storage API
- Local cache: 100GB, 30-day retention

---

## User Devices (De-Googled Phones)

**REQUIRED: De-Googled Android**

**Why:**

- Google telemetry exposes: location, contacts, network activity
- Pings home even behind VPNs
- Adversary with Google access tracks users

**Recommended ROMs:**

- **GrapheneOS** (Pixel only) - Highest security
- **CalyxOS** (Pixel, Fairphone) - Good balance
- **LineageOS** (widest support) - Minimal, maintained
- **/e/OS** (Murena) - Pre-installed option

**Minimum Requirements:**

- Android 10+ (de-googled ROM)
- 3GB RAM, 64GB storage
- WiFi Direct hardware support
- microG or no Google Services

**Certified Devices (Tested):**

- Google Pixel 4a/5/6/7 + GrapheneOS ⭐ (recommended)
- Fairphone 4/5 + CalyxOS
- OnePlus 7/8 + LineageOS
- Motorola G series + LineageOS (budget)

**App Distribution:**

- F-Droid repository (primary)
- Direct APK download
- Mesh network distribution (USB/WiFi sideload)
- NO Google Play Store

**Procurement:**

- Buy pre-installed (Murena, Shift)
- OR buy Pixel + flash GrapheneOS/CalyxOS
- Split bulk orders across vendors
- Mix models for OpSec

**Device Subsidy:**

- Project provides where users can't afford
- $10-20k fund (50-100 devices @ $100-200 each)
- Donation/swap program for upgrades
- Compatibility test for user-provided devices

---

## Lifecycle Management

**Relay Nodes:**

- Lifespan: 5-7 years
- SD cards: Replace every 2 years ($15)
- Upgrade cycle: Every 5 years to current Pi
- Spare parts: 10% inventory (5 spare for 50-node network)

**User Phones:**

- Supported: 2019+ devices (Android 10+)
- Warning: 2017-2019 devices (compatibility issues)
- Unsupported: Pre-2017 (blocked)
- App warns users <3 years support remaining

**Obsolescence Strategy:**

- Community device drive (collect compatible phones)
- Trade-in program (old device credit)
- Quarterly "Supported Devices" update

---

## Constraints

**Procurement:**

- Consumer channels only
- Split bulk purchases
- Plausible alternative uses
- No enterprise gear

**Power:**

- Grid unreliable (solar viable)
- Extreme temps affect batteries
- Battery replacement every 2-3 years

**Maintenance:**

- Component replacement only (no field repair)
- Spare parts stockpiled
- Common tools only

**Environmental:**

- 0-50°C operational
- Sealed enclosures (tropical humidity)
- Passive cooling (no fans)
- Concealment > hardening

---

## Success Criteria

**Reliability:**

- ✅ Relay nodes: >95% uptime over 90 days
- ✅ Bridge nodes: >99% uptime
- ✅ Hub nodes: >98% uptime
- ✅ Hardware failure: <10% annually

**Performance:**

- ✅ Relay nodes: 50+ messages/minute
- ✅ Hub nodes: 5-10 concurrent video transfers
- ✅ Bridge nodes: 100MB+ IPFS uploads/hour
- ✅ babeld RAM: <50MB on relay nodes
- ✅ IPFS gateway RAM: <100MB (vs 300MB full daemon)

**Deployment:**

- ✅ Fits in luggage/backpacks
- ✅ Setup: <30 minutes per relay
- ✅ No specialized tools
- ✅ Procurement raises no flags

---

## Cost Analysis (50-node network)

**Initial Hardware:**

- Relay nodes (47): 47 × $195 = $9,165
- Hub nodes (3): 3 × $200 = $600
- Bridge nodes (3): 3 × $750 = $2,250
- Installation materials: $500
- Spare parts: $1,500
- **Total: ~$14,015**

**Annual Operating:**

- Starlink (3 bridges): 3 × $120/mo × 12 = $4,320
- Hardware replacement: $1,500
- External IPFS pinning: $250-500 ⬆️ (NEW)
- **Total: ~$6,070-6,320/year**

---

## What Changed

**Updates:**

1. ✅ De-googled phones now mandatory (OpSec)
2. ✅ WiFi amplification added to all relay nodes
3. ✅ Bridge IPFS: Lightweight gateway (not full daemon)
4. ✅ Updated RAM: 50-100MB vs 300MB (bridge IPFS)
5. ✅ Updated costs: Relay $195-220 (was $75)
6. ✅ Added: External pinning costs ($250-500/year)

**Why:**

- Security: Google telemetry unacceptable
- Coverage: WiFi amplification required for 200-500ft range
- Reliability: Lightweight gateway more stable
- Budget: Realistic costs with all requirements

---

## Dependencies

- **Component 1:** Network architecture (node roles)
- **Component 4:** WiFi range requirements
- **Component 5:** IPFS gateway implementation
- **Component 9:** Budget and maintenance