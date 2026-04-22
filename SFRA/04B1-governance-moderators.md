---
title: 04B1 - Governance - Moderators
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 9/10
tags: [communication, governance, moderators, community]
---

---

## Overview

Community moderators handle content disputes and user conflicts in a decentralized mesh network. This system ensures accountability while preventing any single moderator from having unilateral power. All moderation actions are transparent, blockchain-auditable, and subject to community oversight.

---

## Moderator Powers (What They CAN Do)

### Content Review

**Flag Content for Review:**

- Mark content as "pending review" within 48 hours of report
- Content remains visible but marked with warning
- Cannot hide or remove content themselves

**Recommend Takedown to DAO:**

- Submit formal proposal for content removal
- Provide evidence and reasoning
- Community votes (66% required to remove)

**Mediate Disputes:**

- Facilitate communication between conflicting users
- Recommend resolutions
- Document outcomes for transparency

**Propose Governance Changes:**

- Submit proposals to improve moderation system
- Participate in governance discussions
- Vote on DAO proposals (same power as any user)

---

## Moderator Limitations (What They CANNOT Do)

### Hard Technical Constraints

**CANNOT Delete Content:**

- IPFS makes content immutable once published
- Only DAO vote can remove content from promoted feed
- Content remains accessible via direct IPFS hash

**CANNOT Unilaterally Ban Users:**

- Can recommend ban to DAO
- Requires 66% community vote
- Even then, user can continue using network (just not promoted)

**CANNOT Access Encrypted Messages:**

- End-to-end encryption prevents moderator access
- Can only review publicly shared content
- Cannot read private conversations

**CANNOT Override Community Votes:**

- All major decisions require DAO approval
- Moderators cannot veto community decisions
- Appeals go directly to community, not moderators

---

## Moderator Selection

### Initial Bootstrap (First 6 Months)

**Founding Moderators:**

- 5-7 trusted individuals from founding team
- Serve initial 6-month term
- Establish moderation precedents
- Train next cohort

### Regular Elections (Every 6 Months)

**Nomination Phase (2 weeks):**

- Any user can nominate themselves
- Requires 3 endorsements from existing users (>90 days old)
- Must complete moderator training course
- Submit statement of values and approach

**Campaign Phase (2 weeks):**

- Nominees present qualifications
- Community asks questions
- Track record reviewed (if existing moderator)

**Voting Phase (2 weeks):**

- One wallet = one vote
- Top 5-7 nominees elected
- Results publicly auditable on blockchain

**Term:** 6 months with optional renewal (max 3 consecutive terms)

---

## Moderator Requirements

### Baseline Qualifications

**Technical:**

- Active user for ≥90 days
- Demonstrated understanding of system (pass quiz)
- Available ≥10 hours/week for moderation duties
- Responsive within 24 hours (average)

**Character:**

- No previous governance violations
- Endorsed by ≥3 trusted community members
- Commitment to transparency and fairness
- Understanding of free speech vs safety balance

### Diversity Goals

**Geographic:** At least 3 different regions represented  
**Demographic:** Diverse perspectives and experiences  
**Timezone:** Coverage across 24-hour cycle  
**Language:** Multilingual capability preferred

---

## Moderator Accountability

### Performance Metrics (Tracked On-Chain)

**Response Time:**

- Average time to review flagged content: <48 hours
- Critical issues: <8 hours

**Decision Quality:**

- Appeal rate: <20% of decisions appealed
- Appeal success rate: Indicates fairness (target: 10-30%)

**Community Trust:**

- Quarterly satisfaction surveys
- Transparency in decision-making
- Public explanation of all major decisions

**Activity Level:**

- Minimum 10 moderation actions per month
- Active participation in moderator discussions
- Attendance at weekly moderator meetings

### Three-Strike System

**Strike 1 (Warning):**

- Issued for: Slow response, minor judgment error
- Consequence: Public warning, additional training
- Expires: After 90 days of good performance

**Strike 2 (Suspension):**

- Issued for: Repeated issues, bias in decisions
- Consequence: 30-day suspension, intensive review
- Requires: Improvement plan and re-training

**Strike 3 (Removal):**

- Issued for: Serious abuse, corruption, repeated failures
- Consequence: Immediate removal from moderator role
- Permanent: Cannot run for moderator again

**Who Decides:** Other moderators (majority vote) or DAO (if controversial)

---

## Moderator Compensation

### Token-Based Rewards

**Base:** 100 governance tokens/month (for active moderators)  
**Performance Bonus:** +20% for excellent metrics  
**Penalty:** -50% for poor performance or strikes

**Why Tokens, Not Cash:**

- Aligns incentives with network health
- Creates long-term commitment
- Tradeable on DEX (future Phase 6)

### Non-Monetary Benefits

- Early access to new features
- Recognition badge in UI
- Invitation to governance working groups
- Influence over network direction

---

## Moderator Council Structure

### Weekly Meetings

**Format:**

- 1-hour video call
- Review contentious cases
- Discuss policy improvements
- Coordinate on emerging issues

**Decision-Making:**

- Consensus preferred
- Simple majority vote if needed
- Escalate to DAO for major policy changes

### Internal Communication

**Platform:** Dedicated Matrix room (end-to-end encrypted)  
**Purpose:** Coordinate reviews, discuss edge cases, share best practices  
**Transparency:** Meeting notes published (sensitive details redacted)

---

## Moderation Workflow

### Standard Content Review Process

```
1. User flags content → Enters review queue
2. Moderator reviews within 48 hours
3. Decision:
   a) No action (false flag) → Close ticket
   b) Warning to poster → Log decision
   c) Recommend DAO removal → Submit proposal
4. If DAO vote initiated → 14-day voting period
5. If 66% approve → Content removed from promoted feed
6. User can appeal → Independent review
```

### Conflict Resolution Process

```
1. User A files complaint against User B
2. Moderator contacts both parties (within 24 hours)
3. Mediation session scheduled (within 7 days)
4. Moderator facilitates discussion, proposes resolution
5. Both parties agree → Case closed
6. No agreement → Escalate to full moderator council
7. Still unresolved → DAO vote (rare)
```

---

## Moderator Training

### Initial Training (Required)

**Curriculum (8 hours):**

- System architecture and constraints
- Moderation philosophy and values
- Decision-making frameworks
- Edge case scenarios and precedents
- Communication skills and de-escalation

**Certification:**

- Pass knowledge test (80% required)
- Shadow experienced moderator for 2 weeks
- Handle 10 cases under supervision

### Ongoing Education

**Monthly:**

- Review of contentious decisions
- New precedent discussions
- External expert presentations

**Quarterly:**

- Policy updates and training refreshers
- Community feedback integration

---

## Appeals Process

Users can appeal any moderator decision:

**How to Appeal:**

1. Submit appeal within 14 days of decision
2. Provide reasoning and evidence
3. Appeals reviewed by different moderator
4. If still disputed → DAO vote

**Appeal Outcomes:**

- Decision upheld (no change)
- Decision modified (partial reversal)
- Decision overturned (full reversal)
- Moderator strike (if error was egregious)

**Transparency:**

- All appeals and outcomes publicly logged
- Used to improve moderation guidelines

---

## Moderator Removal

### Voluntary Resignation

- Give 30-day notice (if possible)
- Train replacement
- Complete handover documentation

### Community-Initiated Removal

**Process:**

- Petition requires 100 signatures
- DAO vote scheduled (66% required)
- Moderator can defend themselves
- If removed: Immediate loss of powers

**Grounds for Removal:**

- Abuse of power
- Corruption or bias
- Incompetence or inactivity
- Violations of governance policies

---

## Success Metrics

**Moderator Team Health:**

- Retention rate >80% annually
- Average tenure: 12-18 months
- Diversity goals met
- No burnout indicators

**Community Trust:**

- Satisfaction survey >4/5
- Low appeal rate (<20%)
- Fair appeal success rate (10-30%)
- Active community participation in elections

---

## Status

**Current State:** Production-ready specification  
**Next Steps:** Recruit founding moderators (Phase 2)  
**Blockers:** None

---

## Related Documents

- [[04B - Governance - Overview]]: Four-tier governance structure
- [[04B2-governance-smart-contracts]]: Technical governance layer
- [[04B3-governance-operators]]: Infrastructure operators (separate role)
- [[04B4-governance-conflicts]]: Escalation procedures and emergencies