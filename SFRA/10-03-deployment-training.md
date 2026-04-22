---
title: Deployment Training
section: 10
subsection: 3
parent: 10-00-deployment-overview
related:
  - 10-02-deployment-installation
  - 10-04-deployment-operations
  - 08-00-security-overview
  - 09A-ux-onboarding
description: 2-week intensive operator training and 2-hour user training covering technical operations, security model explanation, and OpSec
tags: [deployment, training, operators, users, security-education]
version: 2.0
last_updated: 2025-10-17
word_count: 780
---

# Deployment Training

## Operator Training (2 weeks intensive)

### Training Schedule

**Week 1: Technical Foundation**
- Days 1-3: Network Basics
- Days 4-7: Hands-On Maintenance

**Week 2: Security and Support**
- Days 8-10: OpSec Protocols
- Days 11-14: User Support

### Days 1-3: Network Basics

**Day 1: How Mesh Works (Non-Technical)**
- Physical demonstration with 5 devices
- Message hop visualization
- Node types and roles (relay, hub, bridge)
- Coverage and limitations
- When to escalate to home base

**Day 2: Hardware Components**
- Raspberry Pi overview (components, ports)
- WiFi amplification systems
- Solar panels and battery management
- Starlink operation and limitations
- Troubleshooting power issues

**Day 3: Software Systems**
- Babel routing explained (metric-based, not hop-based)
- Matrix protocol role (messaging layer)
- IPFS gateway function (not full daemon)
- Monitoring dashboard walkthrough
- Log interpretation basics

### Days 4-7: Hands-On Maintenance

**Day 4: Physical Inspections**
- Solar panel cleaning and positioning
- Cable integrity checks
- Weatherproofing verification
- Antenna alignment
- Documentation: inspection checklist

**Day 5: Basic Troubleshooting**
- Node offline: power, network, software
- Connectivity issues: antenna, interference, positioning
- Performance degradation: bandwidth, routing
- Using diagnostic tools: ping, traceroute, babeld status
- When to replace vs repair

**Day 6: Component Replacement**
- Raspberry Pi swap procedure
- microSD card replacement (flashing OS)
- WiFi adapter replacement
- Battery replacement
- Solar panel replacement
- Spare parts inventory management

**Day 7: Monitoring Tools**
- Dashboard interpretation (uptime, bandwidth, errors)
- Alert response procedures
- Performance benchmarks (what's normal vs concerning)
- Log review (finding patterns)
- Documentation: incident reports

### Days 8-10: OpSec Protocols

**Day 8: What to Say (and Not Say)**
- Public story: "community tech project"
- Avoiding specific details (node counts, locations)
- Compartmentalized knowledge (need-to-know basis)
- Social media blackout (no mentions)
- Handling questions from outsiders

**Day 9: Physical Security**
- Concealment best practices
- Recognizing tampering
- Surveillance detection basics
- Emergency shutdown procedures
- Hardware kill switch operation
- Safe communication channels

**Day 10: Threat Recognition**
- Government surveillance indicators
- Social engineering attempts
- Unusual network patterns (attacks)
- Operator compromise scenarios
- Escalation procedures
- Incident response practice

### Days 11-14: User Support

**Day 11: Security Model Explanation**

**Critical:** Operators must explain security to non-technical users.

**E2E Encryption:**
- "Your messages are locked with a special key"
- "Only you and recipient can unlock them"
- "Even we (operators) cannot read your messages"
- Use lock and key metaphor (not technical jargon)

**Panic Mode:**
- "Destroys encryption keys, not data"
- Two methods: Duress PIN + Physical button (Power + Volume Down 3s)
- "Keys gone = messages unreadable forever"
- When to use: "If forced to unlock your phone"

**Auto-Wipe:**
- Configurable: 3, 5, or 10 failed unlock attempts
- "Protects you if phone is seized"
- "Remember your normal PIN!"

**Wallet Privacy:**
- "Your wallet is your identity, but pseudonymous"
- "NEVER connect to cryptocurrency exchanges"
- "Use separate wallet for crypto activities"

**Training Validation:**
- Role-play: User asks about wallet privacy
- Demonstrate panic mode explanation
- Practice: Explain encryption to 10-year-old
- Identify: When to escalate vs handle locally

**Day 12: Common User Issues**
- App won't connect (BLE permissions, relay distance)
- Messages stuck in queue (expected behavior)
- Video upload slow (bandwidth, compression settings)
- Wallet recovery (seed phrase process)
- Contact verification (QR scanning, endorsements)

**Day 13: User Training Delivery**
- Teaching techniques for low-literacy users
- Using visual aids and demonstrations
- Handling questions and confusion
- Cultural sensitivity considerations
- Managing group dynamics (10-20 people)

**Day 14: Final Assessment**
- Written quiz (80% pass required)
- Hands-on: Replace failed relay node
- Role-play: Explain panic mode to skeptical user
- Emergency: Respond to bridge node compromise
- Certification upon passing

## User Training (2-hour sessions, groups of 10-20)

### Session Structure

**Minutes 0-15: Welcome and Overview**
- What is mesh network (simple explanation)
- Why it works offline
- What makes it secure
- What we'll learn today

**Minutes 15-45: Hands-On Setup**
- Install app (APK file or F-Droid)
- Create wallet (emphasize: write down seed phrase)
- Backup seed phrase (quiz verification)
- Set up duress PIN
- Test panic mode (safe mode)

**Minutes 45-75: Core Features**
- Send first message to test bot
- Understand message status (queued → sent → delivered)
- Record and share 10-second video
- Add contact via QR code
- Verify a contact (endorsement request)

**Minutes 75-105: Security Education**
- Wallet privacy rules (no KYC exchanges)
- Panic mode demonstration (both methods)
- Auto-wipe setup (failed attempts)
- Understanding "queued" ≠ "failed"
- Message reordering behavior

**Minutes 105-120: Q&A and Practice**
- Answer user questions
- Address concerns
- Practice scenarios
- Distribute support contact info
- Schedule follow-up (7 days later)

### Training Materials

**Provided to each user:**
- Quick reference card (laminated, pictographic)
- Seed phrase backup template
- QR code for operator support contact
- Emergency procedures (one-page)

### Follow-Up Sessions

**7 Days Later:** Check-in session (1 hour)
- Address usage issues
- Reinforce security practices
- Advanced features introduction
- Community Q&A

**30 Days Later:** Refresher (1 hour)
- Review core concepts
- Update on network status
- Governance introduction
- Collect feedback

## Training Validation

### Operator Certification Criteria
- [ ] Pass written quiz (80%+)
- [ ] Successfully replace failed node
- [ ] Explain security model clearly to non-technical person
- [ ] Handle simulated emergency correctly
- [ ] Complete all 14 days

### User Training Success Metrics
- [ ] 80%+ complete setup without help
- [ ] 90%+ can send first message within 5 minutes
- [ ] 100%+ can trigger both panic modes after tutorial
- [ ] 85%+ understand wallet privacy limitations
- [ ] 90%+ correctly explain "queued" status

## Related Documentation

- **Installation:** [10-02-deployment-installation](10-02-deployment-installation.md)
- **Operations:** [10-04-deployment-operations](10-04-deployment-operations.md)
- **Security Overview:** [08-00-security-overview](08-00-security-overview.md)
- **UX Onboarding:** [09A-ux-onboarding](09A-ux-onboarding.md)
