---
title: Development - Detailed Phase Breakdown
version: 2.0
last_updated: 2025-10-23
status: Production-Ready
parent: 11-development
related:
  - 11-00-development-overview
  - 11A-development-team-budget
  - 11B-development-testing
tags: [development, phases, deliverables, milestones]
---

## Phase 1: MVP - Text Messaging (Months 1-3)

### Goal
Prove mesh networking works with encrypted text messaging.

### Deliverables
- Android app (Kotlin, Jetpack Compose)
- Wallet creation/import (Web3j)
- Matrix E2E encryption (Olm)
- WiFi Direct + BLE discovery
- Babel routing on relay nodes (babeld)
- Works with 10-20 devices, 3+ hops

### Success Criteria
- Message delivered through mesh without internet
- Encryption verified (can't decrypt without keys)
- Babel routes around failed nodes
- User can backup/restore wallet

### Team
2-4 developers for 3 months

---

## Phase 2: Media & IPFS (Months 4-5)

### Goal
Add documentation capability with permanent storage.

### Deliverables
- Photo capture/sharing
- Video compression (H.265, 480p)
- Chunked transfer (256KB chunks)
- Bridge IPFS gateway (lightweight HTTP client)
- Pinata/Web3.Storage API integration
- Pin monitoring dashboard
- Media gallery, progress indicators

### Key Decisions
- ❌ NOT: Full go-ipfs daemon on bridge
- ✅ YES: Lightweight HTTP gateway service
- ✅ Pinata API client (primary pinning)
- ✅ Web3.Storage API client (backup pinning)
- ✅ Local cache (100GB, 30-day retention)

### Success Criteria
- 2-min video compressed to <10MB in <60s
- Video uploaded and pinned to 2+ external services
- Hash returned to mesh after first pin
- Progressive playback (watch while downloading)
- Text messages maintain priority during video upload
- Pin status visible to user ("Pinned to 2 services")

### Team
Full team (4-6 developers) for 2 months

---

## Phase 3: UX & Security (Months 6-7)

### Goal
Production-ready interface and security hardening.

### Deliverables
- Polished UI/UX (professional design)
- Onboarding flow (seed phrase backup quiz)
- Duress PIN setup
- Wallet privacy education screens
- Contact verification (QR code, emoji comparison)
- Panic mode testing (safe mode)
- Auto-wipe after failed attempts
- Device compatibility warnings
- Accessibility (TalkBack, high contrast)
- Multi-language support (priority languages)

### Success Criteria
- 80% users complete onboarding without help
- 90% send first message within 5 minutes
- 100% can trigger BOTH panic modes after tutorial:
  - Duress PIN test (safe mode)
  - Physical button combo test
- Auto-wipe after failed attempts works reliably
- Passes WCAG 2.1 AA standards
- Users understand wallet privacy limitations
- First vote disclosure shown and acknowledged

### Team
Full team with UX focus for 2 months

---

## Phase 4: Governance & Bridge (Months 8-9)

### Goal
Complete feature set with community governance.

### Deliverables
- Smart contracts (Polygon/Base L2)
- DAO voting interface
- Moderator vetting system
- First vote disclosure workflow
- Bridge node software complete
- Starlink integration + VPN
- Software update distribution
- Network monitoring dashboard

### Success Criteria
- Users can vote on moderation decisions
- Users acknowledge public vote warning before first vote
- Bridge uploads to IPFS reliably
- Updates distributed through mesh
- Monitoring shows network health

### Team
Full team + smart contract specialist for 2 months

---

## Phase 5: Polish & Scale (Months 9-10)

### Goal
Field-deployable system ready for production.

### Deliverables
- Performance optimization
- Battery life improvements
- Message reordering buffer implementation
- Buffer status indicators in UI
- Error handling polished
- Training materials (operator manual, user guides)
- Operator training: wallet privacy education
- Deployment scripts (automated node setup)
- Field testing (100+ devices, 50+ nodes)
- Bug fixes, stability improvements

### Success Criteria
- <1% crash rate
- Works on devices from 2019+
- 95% relay node uptime
- Operators can deploy independently
- Message buffer handles 30-message queue reliably
- <3% message reordering failures

### Team
Full team for 2 months

---

## Phase Dependencies

### Critical Path
1. Phase 1 must complete before Phase 2 (core mesh required)
2. Phase 2 must complete before Phase 3 (media needs testing)
3. Phase 3 can partially overlap Phase 4 (UX independent)
4. Phase 4 must complete before Phase 5 (governance needed)
5. Phase 5 requires all previous phases complete

### Parallel Work Opportunities
- Smart contract development can start in Phase 2
- Bridge node software can start in Phase 3
- Documentation can be written throughout
- Training materials can be drafted early

---

## Risk Management

### Per-Phase Risks

**Phase 1:**
- Mesh networking harder than expected
- WiFi Direct compatibility issues
- Matrix SDK integration challenges

**Phase 2:**
- IPFS pinning service reliability
- Video compression performance
- Chunked transfer complexity

**Phase 3:**
- User comprehension of security model
- Panic mode reliability across devices
- Accessibility compliance

**Phase 4:**
- Smart contract security vulnerabilities
- Bridge node complexity
- Governance adoption

**Phase 5:**
- Field testing reveals critical issues
- Performance optimization takes longer
- Operator training effectiveness

### Mitigation Strategy
- Build prototype early to test assumptions
- Plan buffer time in each phase
- Continuous user testing throughout
- Security audits at multiple checkpoints
- Phase gates strictly enforced

---

## Metrics & Tracking

### Development Velocity
- Story points per sprint
- Bug discovery rate
- Technical debt accumulation
- Code review turnaround

### Quality Metrics
- Test coverage percentage
- Bug density (per 1000 lines)
- Crash rate in testing
- User testing success rates

### Budget Tracking
- Monthly burn rate
- Variance from plan
- Contingency fund status
- Per-phase cost actuals

---

## Related Documents

- **11-00:** Development overview and principles
- **11A:** Team composition and budget
- **11B:** Testing strategy
- **10-00:** Deployment procedures
