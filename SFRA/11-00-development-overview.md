---
title: Development Overview
version: 2.0
last_updated: 2025-10-23
status: Production-Ready
parent: 11-development
related:
  - 11-01-development-phases
  - 11A-development-team-budget
  - 11B-development-testing
  - 10-00-deployment-overview
tags: [development, roadmap, timeline, overview]
---

## Purpose

Outlines the 5-phase, 10-month development timeline with clear deliverables, success criteria, and phase gates. Professional team of 4-6 developers required.

## Timeline Summary

**Phase 1 (Months 1-3):** MVP text messaging  
**Phase 2 (Months 4-5):** Media & IPFS  
**Phase 3 (Months 6-7):** UX & security hardening  
**Phase 4 (Months 8-9):** Governance & bridge nodes  
**Phase 5 (Months 9-10):** Polish & field testing

## Budget Range

- **Bootstrap:** $150k (lean team, longer timeline)
- **Professional:** $400k (full team, 10 months)
- **Recommended:** $300-350k (balanced approach)

## Technology Stack

### Mobile App
- Kotlin, Jetpack Compose
- WiFi Direct: android.net.wifi.p2p
- BLE: android.bluetooth.le
- Matrix SDK (Java/Kotlin)
- Web3j (Ethereum wallet)
- MediaCodec (video compression)
- IPFS HTTP client (not full daemon)

### Relay Nodes
- Raspberry Pi 4 (4GB RAM)
- Babel routing (babeld)
- Matrix Synapse (lightweight)
- IPFS gateway service (Go)
- SQLite or PostgreSQL
- Monitoring: Prometheus/Grafana

### Bridge Nodes
- Mini PC or Raspberry Pi 5
- Starlink + VPN (WireGuard)
- IPFS gateway
- Pinata/Web3.Storage APIs
- Pin monitoring service
- Linux (Ubuntu Server)

### Smart Contracts
- Solidity
- OpenZeppelin libraries
- Polygon or Base L2
- Hardhat (dev/testing)

## Phase Gates

**Critical principle:** Each phase must meet ALL success criteria before proceeding.

**Gate requirements:**
1. Security review completed
2. All P0/P1 bugs resolved
3. User testing validates functionality
4. Performance benchmarks met
5. Documentation current
6. Technical debt addressed (not deferred)

**If gate fails:**
- Extend phase timeline (don't skip fixes)
- Address root causes
- Re-test before proceeding
- Update timeline and budget projections

## Production Readiness

### Before Launch
- All critical bugs resolved (P0/P1)
- Security audit completed, no critical findings
- Performance benchmarks met
- Documentation complete (user + operator manuals)
- Deployment tested in staging
- 100% critical content pinned to 2+ services
- Panic mode tested and reliable
- Message buffer handling 30+ messages
- Wallet privacy education proven effective (>90% comprehension)

### Post-Launch (First 3 Months)
- 90% user retention
- <1% crash rate
- 95% relay node uptime
- Zero content loss (pin monitoring works)
- <1% panic mode false triggers
- <3% message reordering failures
- No wallet privacy breaches from user error

## Development Principles

### Quality Over Speed
- Phase gates strictly enforced
- No advancing with known critical issues
- Technical debt addressed, not deferred
- User safety paramount

### Testing Throughout
- Continuous testing in all phases
- User testing validates each phase
- Security audits at multiple points
- Field testing before launch

### Iterative Development
- Build core functionality first
- Add features incrementally
- Validate assumptions early
- Adjust based on testing feedback

## Current Status

**State:** Comprehensive 5-phase roadmap defined  
**Next steps:** Funding acquisition and team recruitment  
**Blockers:** Funding commitments needed

## Related Documents

- **11-01:** Detailed phase breakdown and deliverables
- **11A:** Team composition and budget details
- **11B:** Testing strategy and quality assurance
- **10-00:** Post-development deployment procedures
