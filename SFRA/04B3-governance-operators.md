---
title: 04B3 - Governance - Operators
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 9/10
tags: [communication, governance, operators, infrastructure]
---

---

## Overview

Network operators maintain the physical infrastructure of the mesh network. They are separate from content moderators and focus exclusively on technical operations. This document covers operator selection, responsibilities, accountability, and removal processes.

---

## Operator Role Definition

### Core Responsibilities

**Infrastructure Maintenance:**

- Deploy and configure bridge nodes
- Monitor network health 24/7
- Respond to outages (2-hour SLA for critical issues)
- Perform hardware upgrades and replacements

**Network Operations:**

- Optimize routing and bandwidth usage
- Coordinate with relay node volunteers
- Troubleshoot connectivity issues
- Document operational procedures

**Budget Management:**

- Track infrastructure costs
- Propose equipment purchases
- Manage operational budget allocations
- Report spending monthly

**Security Operations:**

- Monitor for attacks or anomalies
- Apply security patches promptly
- Respond to infrastructure emergencies
- Maintain OpSec protocols

---

## What Operators CANNOT Do

**Clear Boundaries:**

**CANNOT Moderate Content:**

- Operators handle infrastructure only
- Content decisions belong to moderators
- Separation prevents conflicts of interest

**CANNOT Access User Data:**

- End-to-end encryption prevents this
- Operators see only metadata (routing info)
- Cannot read messages or view media

**CANNOT Make Governance Decisions Unilaterally:**

- Major decisions require DAO approval
- Emergency actions documented and reviewed
- Accountable to operator council and community

**CANNOT Censor Users:**

- Cannot block specific users or content
- Can only respond to technical issues
- Network-level filtering prohibited

---

## Operator Selection

### Initial Operators (Bootstrap Phase)

**First 3-5 Operators:**

- Selected by founding team
- Technical expertise required
- Trusted community members
- Serve 12-month initial term

### Ongoing Selection Process

**Skill-Based Selection:**

```
1. Existing operators identify need (e.g., new region coverage)
2. Post requirements (skills, location, availability)
3. Candidates apply (resume + technical interview)
4. Operator council evaluates (majority approval)
5. Community veto period (7 days, requires 66% to block)
6. If no veto → Onboarding begins
```

**Required Skills:**

- Linux system administration
- Network engineering (routing protocols)
- Hardware deployment experience
- On-call availability
- Documentation skills

**Preferred Skills:**

- Mesh networking experience
- Security operations background
- Multi-language capability
- Local community connections

---

## Operator Accountability

### Service Level Agreements (SLAs)

**Response Times:**

- **Critical** (network down): 2 hours
- **High** (degraded performance): 8 hours
- **Medium** (minor issues): 24 hours
- **Low** (routine maintenance): 7 days

**Uptime Targets:**

- Bridge nodes: 99.5% uptime
- Response to critical alerts: <2 hours
- Documentation updates: Within 48 hours of changes

### Performance Metrics

**Tracked On-Chain:**

- Response time to incidents
- Bridge node uptime percentage
- Infrastructure cost efficiency
- Community satisfaction ratings

**Quarterly Reviews:**

- Operator council evaluates performance
- Community feedback collected
- Areas for improvement identified
- Compensation adjusted if needed

### Compensation Model

**Base Payment:**

- $2,000-4,000/month (depends on region, workload)
- Paid in stablecoins (USDC) monthly
- Governance tokens bonus for excellent performance

**Performance Bonuses:**

- +10% for exceeding SLAs
- +15% for exceptional incident response
- +20% for major infrastructure improvements

**Penalties:**

- -25% for missing SLA targets
- -50% for repeated failures
- Removal for serious negligence

---

## Operator Council

### Structure

**Size:** 3-7 active operators (scales with network size)

**Leadership:**

- Rotating coordinator (3-month terms)
- No permanent leader (prevents power concentration)
- Coordinator schedules meetings, not decision-maker

### Meetings

**Weekly Operations Call:**

- Review current status
- Coordinate maintenance windows
- Discuss ongoing issues
- Plan upgrades

**Monthly Strategy Session:**

- Long-term infrastructure planning
- Budget proposals
- Policy improvements
- Community feedback review

**Decision-Making:**

- Consensus preferred
- Simple majority vote if needed
- Escalate to DAO for major policy/budget changes

---

## Dispute Resolution

### Operator-to-Operator Conflicts

**Process:**

```
1. Direct resolution attempt (within 48 hours)
2. If unresolved → Mediation by coordinator
3. If still unresolved → Full operator council vote
4. If contentious → DAO vote (rare)
```

### User Complaints About Operators

**Process:**

```
1. User files complaint (via governance dashboard)
2. Operator responds within 48 hours
3. Operator council reviews (within 7 days)
4. Decision: Dismiss, warning, or penalty
5. User can appeal to DAO if unsatisfied
```

### Operator Performance Issues

**Three-Strike System:**

**Strike 1 (Warning):**

- Trigger: Missed SLA, slow response, minor error
- Action: Documented warning, improvement plan
- Review: 30-day performance monitoring
- Expires: After 90 days of good performance

**Strike 2 (Probation):**

- Trigger: Repeated issues, second SLA miss
- Action: 30-day probation, reduced responsibilities
- Compensation: Reduced by 25%
- Review: Intensive weekly check-ins

**Strike 3 (Removal):**

- Trigger: Third major failure, negligence, misconduct
- Action: Immediate removal from operator role
- Compensation: Final payment for work completed
- Handover: 2-week transition period (if possible)

---

## Operator Removal

### Voluntary Departure

**Process:**

- Give 30-day notice (if possible)
- Document all systems and procedures
- Train replacement operator
- Complete handover checklist

### Community-Initiated Removal

**Grounds:**

- Repeated SLA failures
- Security negligence
- Fraud or misuse of funds
- Prolonged inactivity

**Process:**

```
1. Petition requires 50 community signatures
2. Operator council investigates (7 days)
3. Council recommendation to DAO
4. DAO vote (66% required to remove)
5. If removed → Immediate access revocation
6. Emergency replacement identified
```

### Emergency Removal

**Immediate Threats Only:**

- Compromised operator account
- Malicious actions detected
- Severe security breach caused by operator

**Authority:**

- Operator council multi-sig (3 of 5)
- Must be followed by DAO vote within 7 days
- If DAO rejects → Operator reinstated with apology

---

## Operational Budget

### Budget Allocation

**Monthly Operating Costs:**

- Operator compensation: $6,000-20,000 (3-5 operators)
- Hardware purchases: $2,000-5,000
- Bandwidth/hosting: $500-1,500
- Emergency reserve: $5,000
- **Total:** ~$15,000-30,000/month

### Budget Approval Process

**Routine Expenses (<$1,000):**

- Operator council approval (majority)
- Document and report monthly

**Major Expenses ($1,000-10,000):**

- Operator council proposes
- Community discussion (7 days)
- DAO vote (simple majority)

**Large Expenses (>$10,000):**

- Detailed proposal required
- Extended discussion (14 days)
- DAO vote (66% supermajority)

### Financial Transparency

**Monthly Reports:**

- All expenses itemized
- Performance metrics included
- Budget variance explained
- Published on governance dashboard

**Quarterly Audits:**

- Independent financial review
- Community Q&A session
- Recommendations for efficiency

---

## Emergency Procedures

### Infrastructure Emergency Response

**SCENARIO: All Bridge Nodes Down**

```
1. Automated alert to on-call operator
2. Operator investigates (within 30 minutes)
3. Status update broadcast to community
4. Emergency response initiated:
   - If fixable quickly → Restore service
   - If prolonged → Deploy temporary cloud backup
5. Moderators approve emergency spending (multi-sig)
6. Service restored, detailed post-mortem within 7 days
```

### Security Incident Response

**SCENARIO: Bridge Node Compromised**

```
1. Operator detects unusual activity
2. Immediately isolate affected node
3. Alert security team and moderators
4. Forensic investigation begins
5. If confirmed compromise:
   - Rebuild node from clean image
   - Rotate all credentials
   - Review logs for data exposure
6. Post-mortem and preventive measures
```

---

## Operator Training

### Initial Onboarding (2 weeks)

**Week 1:**

- System architecture overview
- Access credentials and tools
- Documentation review
- Shadow experienced operator

**Week 2:**

- Hands-on deployment
- Incident response simulation
- Emergency procedure drills
- First on-call shift (supervised)

### Ongoing Education

**Monthly:**

- New technology briefings
- Security update training
- Incident retrospectives

**Quarterly:**

- Advanced skills workshops
- External expert presentations
- Disaster recovery drills

---

## Success Criteria

**Operational Excellence:**

- Bridge node uptime >99.5%
- Critical incident response <2 hours
- Monthly budget variance <10%
- Zero security breaches due to operator negligence

**Team Health:**

- Operator retention >80% annually
- Low conflict/dispute rate
- Effective coordination
- Adequate coverage across timezones

**Community Trust:**

- Satisfaction ratings >4/5
- Transparent operations
- Responsive to feedback
- Regular communication

---

## Status

**Current State:** Production-ready specification  
**Next Steps:** Recruit initial operators (Phase 2)  
**Blockers:** Budget allocation pending

---

## Related Documents

- [[04B - Governance - Overview]]: Overall governance framework
- [[04B1-governance-moderators]]: Content moderation (separate role)
- [[04B2-governance-smart-contracts]]: Emergency controls and budget
- [[04B4-governance-conflicts]]: Escalation procedures
- [[10 - Deployment]]: Infrastructure deployment details