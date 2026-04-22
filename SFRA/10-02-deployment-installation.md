---
title: Deployment Installation
section: 10
subsection: 2
parent: 10-00-deployment-overview
related:
  - 10-01-deployment-pre-planning
  - 10-03-deployment-training
  - 03-hardware-specifications
description: Physical installation procedures for relay, hub, and bridge nodes with verification testing
tags: [deployment, installation, hardware, nodes, testing]
version: 2.0
last_updated: 2025-10-17
word_count: 680
---

# Deployment Installation

## Installation Timeline: Weeks 5-6

### Relay Nodes (47 units - Week 5)

**Installation Steps per Node:**

1. **Mount WiFi antenna**
   - Highest point available (rooftop, attic, high window)
   - Clear line-of-sight preferred
   - Weatherproof enclosure if outdoor
   - Document GPS coordinates

2. **Conceal Raspberry Pi device**
   - Behind furniture, in attic, false wall
   - Ventilated location (fanless cooling)
   - Access to power outlet
   - Protected from weather/tampering

3. **Power connection**
   - Wall power preferred (grid)
   - Solar + battery if no grid (25W panel, 25Ah battery)
   - Test power stability (48-hour burn-in)

4. **Configure babeld routing**
   - Connect to Pi via SSH
   - Verify babeld daemon running
   - Check routing table populating
   - Document node ID and address

5. **Test connectivity**
   - Ping neighboring relay nodes
   - Verify routes discovered (3-5 neighbors minimum)
   - Check WiFi range (walk test with phone)
   - Document actual coverage area

6. **Document installation**
   - Location, power source, antenna direction
   - Node ID, IP address, neighbors
   - Access instructions for maintenance
   - Add to encrypted master map

**Installation Rate:** 6-8 nodes per day (2 operators) = 6-7 days for 47 nodes

**Placement Priorities:**
1. Population centers first (homes, gathering places)
2. High points second (range extension)
3. Fill gaps third (dead zone elimination)
4. Verify 7-hop paths working

### Hub Nodes (3 units - Day 8)

**High-Traffic Location Installation:**

**Day 8 Morning - Church:**
- Install Mini PC with WiFi 6
- Higher power requirement (30-50W grid)
- Verify video throughput (5-10 concurrent transfers)
- Test bandwidth to nearby relay nodes

**Day 8 Afternoon - Market:**
- Similar installation to church
- Public area requires extra concealment
- Higher traffic volume expected

**Day 9 Morning - School:**
- Coordinate with trusted staff
- Installation during off-hours
- Extra OpSec (government oversight risk)

**Verification:**
- Each hub routes to 5+ relay nodes
- Video transfer test (2-minute clip <5 min delivery)
- Performance benchmarks documented

### Bridge Nodes (3 units - Days 9-10)

**Critical Gateway Setup:**

**Bridge Node Components:**
- Raspberry Pi 4 or Mini PC
- Starlink dish + router
- WiFi amplification (mesh connectivity)
- Solar backup battery (48-hour autonomy)
- Weatherproof lockable enclosure
- Hardware kill switch

**Installation Steps:**

1. **Site selection** (completed in pre-planning)
   - Hidden location with sky view
   - Physical security (locks, tamper detection)
   - Trusted operator home or secure building

2. **Starlink installation**
   - Clear sky view (no obstructions)
   - Dish mounting (roof, pole, or ground)
   - Router connection to Pi/Mini PC
   - Test internet connectivity

3. **Configure bridge software**
   - IPFS gateway service (lightweight HTTP)
   - Pinata API keys configured
   - Web3.Storage API keys configured
   - WireGuard VPN tunnel established
   - Firewall: allow Babel, Matrix, IPFS only

4. **Connect to mesh network**
   - babeld daemon running (participates in routing)
   - Verify mesh connectivity (relay nodes see bridge)
   - Test message routing through bridge

5. **Test IPFS upload**
   - Upload test file from mesh to IPFS
   - Verify pins to Pinata (primary)
   - Verify pins to Web3.Storage (backup)
   - Confirm hash returned to mesh

6. **Physical security**
   - Install hardware kill switch (emergency shutdown)
   - Tamper detection configured
   - Access restricted to 2-3 operators
   - Document emergency procedures

**Installation Rate:** 1 bridge per day (requires careful testing) = 2-3 days

### Verification Testing (Day 11-12)

**End-to-End Testing:**

**Test 1: Message Delivery**
- Send text message from user phone
- Route through 7 hops (maximum)
- Verify delivery at destination
- Measure: <10 seconds delivery time

**Test 2: Video Upload**
- Record 2-minute video on user phone
- Upload through mesh to bridge
- Verify chunks transmitted
- Confirm IPFS pin to 2+ services
- Verify hash distributed through mesh
- Measure: <10 minutes completion

**Test 3: Coverage Validation**
- Walk target area with phone
- Test connectivity at key locations
- Identify dead zones
- Document: >90% population coverage

**Test 4: Node Failure Resilience**
- Shut down 3 random relay nodes
- Verify Babel routes around failures
- Confirm messages still delivered
- Measure: <60 seconds re-convergence

**Test 5: Bridge Failover**
- Shut down Bridge 1
- Verify Bridge 2 takes over IPFS uploads
- Confirm no message loss
- Measure: <1 minute failover

### Performance Benchmarks

**Document baseline metrics:**
- Message delivery time: avg, 50th, 95th percentile
- Video upload time: avg for 2-min clip
- Relay node uptime: first 48 hours
- Coverage: % area, % population
- Bridge upload capacity: chunks/hour

### Installation Documentation

**Create encrypted installation report:**
- All node locations (GPS coordinates)
- Node configurations (IDs, addresses, neighbors)
- Performance benchmarks
- Issues encountered and resolved
- Maintenance access procedures
- Emergency shutdown procedures

**2 copies: Lead operator + Home base**

## OpSec During Installation

**Minimize visibility:**
- Install during off-hours (evening/night)
- Small teams (2 operators max)
- No obvious patterns (vary timing, routes)
- Plausible cover story (home automation project)
- No photos of installations
- Compartmentalized knowledge (operators know only their nodes)

## Related Documentation

- **Pre-Planning:** [10-01-deployment-pre-planning](10-01-deployment-pre-planning.md)
- **Training Phase:** [10-03-deployment-training](10-03-deployment-training.md)
- **Hardware Specs:** [03-hardware-specifications](03-hardware-specifications.md)
