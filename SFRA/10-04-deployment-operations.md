---
title: Deployment Operations
section: 10
subsection: 4
parent: 10-00-deployment-overview
related:
  - 10-03-deployment-training
  - 11A-development-team-budget
  - 04B3-governance-operators
description: Ongoing network operations including team structure, maintenance schedules, budget management, and sustainability planning
tags: [deployment, operations, maintenance, budget, sustainability]
version: 2.0
last_updated: 2025-10-17
word_count: 700
---

# Deployment Operations

## Operational Structure

### Field Operators (6-9 local, paid)

**Roles and Responsibilities:**

**Daily Tasks:**
- Check monitoring dashboard (10 minutes)
- Review alerts and anomalies
- Respond to user support requests
- Document issues in shared log

**Weekly Tasks:**
- Physical node inspections (select 10-15 nodes rotating)
- Battery level checks (solar-powered nodes)
- Performance benchmark review
- User community check-in

**Monthly Tasks:**
- Solar panel cleaning and repositioning
- Comprehensive node health review
- Hardware replacement as needed
- Budget reporting to home base
- Community feedback collection

**As Needed:**
- User support and troubleshooting
- Hardware replacement (failed components)
- Emergency response (node compromise, outages)
- Training new users (ongoing)

**Compensation:** $200-500/month (regional wages)

**On-Call Rotation:**
- 2 operators on-call each week
- Response SLA: 2 hours for critical issues
- 24/7 coverage through rotation

### Home Base Team (Remote support)

**2-3 Developers:**
- Bug fixes and patches
- Feature enhancements
- Security updates
- Software maintenance

**1-2 DevOps Engineers:**
- Network monitoring (24/7)
- Performance analysis
- Deployment automation
- Infrastructure optimization

**1 Training Specialist:**
- Materials creation and updates
- Operator mentorship
- User training curriculum
- Documentation maintenance

**1 Security Analyst:**
- Threat monitoring
- Vulnerability assessment
- Incident response coordination
- Security patches

**24/7 Technical Support:**
- Slack channel for field operators
- Emergency hotline for critical issues
- Knowledge base maintenance
- Escalation procedures

## Maintenance Schedules

### Daily Monitoring

**Automated Dashboard Checks:**
- Relay node uptime (target: >95%)
- Bridge node uptime (target: >99%)
- Message delivery rates
- IPFS pin success rates
- Bandwidth utilization
- Error rates and patterns

**Alert Thresholds:**
- Node offline >1 hour → Alert operator
- Message delivery <90% → Investigate
- Bridge offline >15 minutes → Emergency
- IPFS pin failures >5% → Critical

### Weekly Inspections

**Physical Node Checks (rotating 10-15 nodes):**
- Visual inspection (tampering, damage)
- Cable integrity
- Antenna positioning
- Weatherproofing
- Power stability

**Solar Node Specific:**
- Panel cleanliness
- Battery voltage (>12V)
- Charge controller status
- Sun exposure optimization

### Monthly Maintenance

**All Relay Nodes:**
- Software updates (if available)
- Log rotation and cleanup
- Storage usage review
- Configuration backup

**Bridge Nodes:**
- Starlink dish cleaning
- VPN tunnel health
- IPFS cache management
- Pin verification (100% critical content)

**Hub Nodes:**
- Performance benchmarks
- High-traffic optimization
- Storage expansion if needed

### Quarterly Reviews

**Network Health:**
- Coverage reassessment
- Dead zone identification
- Performance trends analysis
- Capacity planning

**Hardware:**
- Replacement schedule planning
- Spare parts inventory
- End-of-life device identification
- Upgrade opportunities

**Team:**
- Operator performance review
- Training refreshers
- Compensation adjustments
- Succession planning

## Budget Management

### Annual Operating Budget

**Infrastructure ($8,070-8,320/year):**
- Starlink (3 bridges): 3 × $120/mo × 12 = $4,320
- Hardware replacement: $1,500
- IPFS pinning: $250-500
- Contingency: $2,000

**Personnel ($104,000-155,000/year):**
- Field operators: 6-9 × $200-500/mo × 12 = $14,400-54,000
- Home base team: $80,000-120,000
  - 2-3 developers: $60k-90k
  - 1-2 DevOps: $12k-18k
  - 1 training specialist: $6k-9k
  - 1 security analyst: $6k-9k
- Training materials: $5,000

**Total Annual: $112,070-163,320**

### Funding Model

**Years 1-2: Grant-Dependent**
- 100% external funding
- Alliance of businesses and ministries
- Multi-year commitment secured
- Operator salaries guaranteed

**Years 3-5: Hybrid Model**
- 50% external grants
- 50% community contributions ($5-10/user/year optional)
- 200 users × $10 = $2k/year community funding
- Shortfall covered by grants

**Years 5+: Community-Owned (Goal)**
- Community covers 100% operating costs
- Modest user donations OR local sponsors
- Grants for major upgrades only
- Operator compensation from community budget

### Contingency Plans

**Funding drops 50%:**
- Reduce to 3 bridges, 30 relays
- Maintain core coverage
- Defer upgrades
- Reduce home base team to 2-3 people

**Funding drops 75%:**
- Minimum viable: 1 bridge, 15 relays
- Core population areas only
- Emergency-only support
- Community self-support model

**Funding ends:**
- Archive code, publish documentation
- Transfer ownership to community
- Community forks and maintains independently
- Graceful shutdown with 3-month notice

## Sustainability Metrics

### Success Indicators (Ongoing)

**Technical Health:**
- 95%+ relay node uptime
- 99%+ bridge node uptime
- <5 second message delivery (3-hop avg)
- 100% critical content pinned to 2+ services
- Zero content loss over 90 days

**Community Health:**
- 90%+ user retention
- 200+ active users
- Growing user base (organic)
- Low support request rate (<10/week)
- High satisfaction scores (>4/5)

**Operational Health:**
- Operators handle 80%+ issues independently
- <20% operator turnover annually
- Budget variance <10%
- Zero critical security compromises
- Monthly budget reports on time

## Related Documentation

- **Training:** [10-03-deployment-training](10-03-deployment-training.md)
- **Budget Details:** [11A-development-team-budget](11A-development-team-budget.md)
- **Operator Governance:** [04B3-governance-operators](04B3-governance-operators.md)
