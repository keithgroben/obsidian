---
title: Deployment Pre-Planning
section: 10
subsection: 1
parent: 10-00-deployment-overview
related:
  - 10-02-deployment-installation
  - 03-hardware-specifications
  - 02-architecture
description: Community engagement, coverage mapping, security assessment, and covert procurement for hostile environment deployment
tags: [deployment, planning, community, opsec, procurement]
version: 2.0
last_updated: 2025-10-17
word_count: 650
---

# Deployment Pre-Planning

## Community Engagement (4-8 weeks minimum)

### Establish Trust
**Critical foundation before any hardware deployment:**
- Meet with local leadership (religious, civic, community organizers)
- Explain threat model honestly: capabilities and limitations
- Demonstrate prototype if possible
- Answer questions transparently
- Listen to community concerns and needs

### Key Questions to Address
**With community leaders:**
- Who are the trusted members who should operate the network?
- What are the specific threats we're facing?
- Where are safe locations for hidden nodes?
- What communication needs are most critical?
- How can we maintain this without outside experts?

### Operator Selection
**Through community nomination (not outside choice):**
- Community leaders suggest 12-15 candidates
- Interview for: technical aptitude, trustworthiness, availability
- Select 6-9 operators (3x redundancy per role)
- Each operator mentors 1-2 apprentices (succession planning)
- Operators paid $200-500/month (regional wages)

### Security Risk Assessment
**Evaluate deployment environment:**
- Active surveillance presence?
- Historical government response to similar projects?
- Physical security threats (robbery, seizure)?
- Legal risks for operators and users?
- Community's risk tolerance?

**Decision criteria:**
- High risk + low community trust = Defer deployment
- Medium risk + strong community support = Proceed with enhanced OpSec
- Low risk = Standard deployment

## Coverage Mapping

### Target Area Analysis
**Map coverage requirements:**
- Identify population centers (homes, gathering places)
- Mark high-traffic locations (markets, churches, schools)
- Note geographic barriers (hills, buildings, rivers)
- Assess power availability (grid, solar)
- Identify secure relay locations

### Node Placement Strategy
**Strategic placement priorities:**

**Relay Nodes (47 units):**
1. High points (rooftops, hills) - maximum range
2. Central locations - connect population clusters
3. Trusted homes - security and maintenance access
4. Geographic coverage - eliminate dead zones
5. Power-accessible - grid or solar viable

**Hub Nodes (3 units):**
- High-traffic locations: church, market, school
- Grid power required (30-50W)
- High throughput needs (video sharing hotspots)

**Bridge Nodes (3 units):**
- Hidden locations with clear sky view (Starlink)
- Maximum physical security
- Backup power critical
- Accessible for emergency shutdown

### Coverage Verification
**Create coverage map:**
- Plot node locations on map
- Calculate coverage circles (200-500 ft radius with amplification)
- Verify 7-hop paths reach target areas
- Identify gaps requiring additional nodes or directional antennas
- Accept <5% dead zones if not population centers

## Procurement

### Hardware Acquisition
**Covert procurement to avoid flags:**

**Strategy:**
- Split orders across 5-10 vendors
- Use different shipping addresses
- Mix timing (spread over 2-4 weeks)
- Plausible alternative uses (home automation, education project)
- No enterprise bulk orders

**Equipment List:**
- 50 Raspberry Pi 4 (4GB) - $75 each
- 50 WiFi amplification kits - $55-80 each
- 3 Mini PCs (hub nodes) - $200 each
- 3 Starlink kits - $500 each
- 25 solar panel kits - $65 each
- Spare parts (10% extra)

**Total: ~$14,000**

### Testing Before Shipment
**Verify all hardware:**
- Test each Raspberry Pi (boot, connectivity)
- Flash OS and configure babeld on 2-3 units (test routing)
- Test WiFi amplification range
- Verify Starlink connectivity
- Check solar panel output

**Reject/replace defective units before shipping**

## Documentation Preparation

### Encrypted Records
**Document for operators (encrypted):**
- Node location map (with addresses/GPS)
- Operator assignments per node
- Emergency contact procedures
- Hardware serial numbers
- Configuration details

**Storage:**
- Encrypted USB drives (2 copies)
- One with lead operator, one with home base
- Never stored in cloud or unencrypted

### Physical Security Plans
**Per node type:**

**Relay Nodes:**
- Concealment strategy (behind furniture, attics, false walls)
- Weatherproof enclosures blend with environment
- Antenna placement (hidden but effective)
- Access plan for maintenance

**Bridge Nodes:**
- Hidden with plausible cover (amateur radio, educational)
- Hardware kill switch installation plan
- Emergency shutdown procedure
- Physical security (locks, tamper detection)

### Incident Response Protocols
**Prepare procedures for:**
- Node compromised (what to do, who to contact)
- Operator compromised (access revocation, backup activation)
- Mass seizure event (network continuation plan)
- Bridge raid (queue uploads, mesh-only mode)

## Pre-Deployment Checklist

**Before proceeding to installation:**
- [ ] Community leadership supports deployment
- [ ] 6-9 operators selected and committed
- [ ] Coverage map complete with node locations
- [ ] All hardware procured and tested
- [ ] Secure locations identified for all nodes
- [ ] Physical security plans documented
- [ ] Incident response procedures written
- [ ] Operator training curriculum prepared
- [ ] User training materials ready
- [ ] Funding secured for 12+ months operations
- [ ] Home base support team in place

**If ANY item unchecked → Address before proceeding**

## Related Documentation

- **Installation Phase:** [10-02-deployment-installation](10-02-deployment-installation.md)
- **Hardware Specs:** [03-hardware-specifications](03-hardware-specifications.md)
- **Network Architecture:** [02-architecture](02-architecture.md)
