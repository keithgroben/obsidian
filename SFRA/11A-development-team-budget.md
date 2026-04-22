---
title: 11A - Development - Team & Budget
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 9/10
tags: [operations, development, budget, team, resources]
---

---

## Overview

This document outlines team composition requirements and budget estimates for a 10-month development cycle. Options range from a bootstrap approach ($150k) to a full professional team ($400k), with trade-offs clearly defined.

---

## Team Requirements

### Core Team (Recommended - Professional Approach)

**Senior Android Developer (Full-Time, 10 months)**

**Required Skills:**

- Kotlin and Jetpack Compose expertise
- WiFi Direct and BLE networking
- Cryptography implementation (Olm/Megolm)
- Mobile security best practices
- Performance optimization

**Responsibilities:**

- Android app development (Phases 1-5)
- Wallet integration (Web3j)
- UI/UX implementation
- Device compatibility testing
- App store deployment

**Compensation:** $120k-160k (10 months)

---

**Backend/Network Engineer (Full-Time, 10 months)**

**Required Skills:**

- Babel routing protocol
- IPFS gateway implementation
- Go or Python
- Linux system administration
- Network security

**Responsibilities:**

- Relay node software (Babel configuration)
- Bridge node development
- IPFS gateway and pinning integration
- Network monitoring tools
- Performance optimization

**Compensation:** $110k-150k (10 months)

---

**Smart Contract Developer (Part-Time, Months 7-9)**

**Required Skills:**

- Solidity programming
- Ethereum Layer 2 (Polygon/Base)
- OpenZeppelin contracts
- Security audit experience
- Web3 development

**Responsibilities:**

- Governance smart contracts
- DAO voting system
- Moderator election contracts
- Testing and deployment
- Security documentation

**Compensation:** $30k-50k (3 months, ~60% time)

---

**DevOps Engineer (Part-Time, Months 4-10)**

**Required Skills:**

- Linux server administration
- Raspberry Pi deployment
- Automation scripting (Ansible/Bash)
- Network configuration
- Monitoring tools (Prometheus/Grafana)

**Responsibilities:**

- Deployment automation scripts
- Node setup and configuration
- Monitoring dashboard
- Backup and recovery procedures
- Documentation

**Compensation:** $35k-50k (7 months, ~50% time)

---

**UI/UX Designer (Part-Time, Months 1-3, 9-10)**

**Required Skills:**

- Mobile app design (Android)
- Accessibility standards (WCAG 2.1)
- User research and testing
- Figma or Sketch
- Low-literacy design experience

**Responsibilities:**

- App design mockups
- User flow optimization
- Accessibility review
- Icon and visual asset creation
- Onboarding experience design

**Compensation:** $25k-40k (5 months, ~50% time)

---

### Bootstrap Team (Minimum Viable)

**2 Full-Stack Developers (10 months each)**

**Requirements:**

- One Android-focused, one backend-focused
- Both capable of multiple roles
- Willing to learn as needed
- Mission-aligned (lower compensation acceptable)

**Responsibilities:**

- Split all development work
- Manage DevOps (basic scripts)
- DIY UI/UX (functional, not polished)
- Contract out smart contracts only

**Compensation:** $100k-120k each (10 months)

**Trade-offs:**

- Longer timeline (12-14 months likely)
- Less polished UX
- Higher technical debt
- More iteration required
- Greater bus factor risk

---

## Budget Estimates

### Bootstrap Option: $150k Total

**Personnel:**

- 2 full-stack developers × 10 months × $6k = $120k
- Part-time smart contract dev × 2 months × $5k = $10k
- Part-time UI/UX × 3 months × $3k = $9k

**Infrastructure & Services:**

- Dev hardware (phones, PIs, laptops): $5k
- Pinata/Web3.Storage (year 1): $500
- Smart contract audits: $5k
- Testing devices: $1k

**Contingency:** $500

**Timeline:** 12-14 months (realistic with lean team)

---

### Professional Option: $400k Total

**Personnel:**

- Senior Android dev × 10 months × $15k = $150k
- Senior backend/network engineer × 10 months × $15k = $150k
- Smart contract specialist × 3 months × $12k = $36k
- DevOps engineer × 6 months × $10k = $60k
- UI/UX designer × 4 months × $8k = $32k

**Infrastructure:**

- Dev hardware: $10k
- Testing infrastructure: $5k
- Pinata/Web3.Storage: $1k
- Smart contract audits (professional): $15k

**Contingency:** $41k

**Timeline:** 10 months (as planned)

---

## Compensation Market Rates

### Developer Salary Ranges

**High End (Senior, US-based):**

- Android: $160k/year → $133k/10 months
- Backend: $150k/year → $125k/10 months

**Mid-Range (Global Talent):**

- Android: $120k/year → $100k/10 months
- Backend: $110k/year → $92k/10 months

**Contract Specialists:**

- Smart Contracts: $150-250/hour
- UI/UX: $100-150/hour
- DevOps: $100-150/hour

### Equity Alternative

**For Mission-Aligned Developers:**

- Lower cash compensation
- Future token allocation (if Phase 6 payment system deployed)
- Governance role in network
- Residual income from node operations

**Structure:**

- 60% cash, 40% future tokens
- Vesting over 2 years
- Only if funding constrained

---

## Contingency Planning

### If Budget Cuts Needed

**Priority 1 (Essential):**

- Android developer
- Backend developer
- Minimal security audit

**Priority 2 (Important):**

- Smart contract developer
- DevOps automation
- Professional UI/UX

**Priority 3 (Nice to Have):**

- Comprehensive audit
- Full-time DevOps
- Extensive testing hardware

### Timeline Flexibility

**If Development Slower:**

- Extend to 12-14 months
- Adjust funding accordingly
- Maintain phase gates (don't compromise quality)

---

## Success Metrics

**Team Performance:**

- Sprint velocity consistent
- Code review turnaround <24 hours
- Bug density <10 per 1000 lines
- Test coverage >80%

**Budget Performance:**

- Monthly burn rate tracked
- Variance <10% of plan
- Contingency fund intact at Phase 3
- No surprise costs

---

## Status

**Current State:** Budget and team structure defined  
**Next Steps:** Funding acquisition and recruitment  
**Blockers:** Funding commitments

---

## Related Documents

- [[11 - Development - Overview]]: Five-phase timeline and deliverables
- [[11B-development-testing]]: Testing strategy and quality assurance
- [[10 - Deployment]]: Operational costs after development