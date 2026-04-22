---
title: C - Glossary
version: 1.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 10/10
tags: [reference, glossary, terminology, definitions]
---

---

## Overview

**⚠️ IMPORTANT: This is a Phase 6 future feature, NOT part of the initial deployment (Phases 1-5).**

The core mesh network (Phases 1-5) operates on a volunteer/community model with no financial incentives. This document outlines potential economic mechanisms that could be added in Phase 6 (12+ months post-launch) if communities request compensation for operators, mutual aid features, or incentive systems.

---

## Current Design (Phases 1-5)

**No Payment System:**

- Volunteer-operated relay nodes
- Community-funded bridge nodes
- Equipment provided, not cash
- Governance uses non-financial tokens
- Focus: Security and functionality first

**Why Defer Payments:**

- Adds regulatory complexity
- Creates financial attack surface
- Requires wallet separation protocols
- Not essential for core mission
- Can be added later if needed

---

## Potential Phase 6 Features

### Use Cases

**If communities request these features:**

**1. Operator Compensation**

- Monthly stipends for relay/bridge node operators
- Performance-based bonuses
- Equipment reimbursement

**2. Mutual Aid**

- Emergency funds for community members
- P2P transfers for basic needs
- Solidarity payments during crises

**3. Bounty System**

- Reward documentation collection
- Incentivize evidence preservation
- Compensate citizen journalists

**4. Node Incentives**

- Small payments for hosting relay nodes
- Bandwidth sharing compensation
- Uptime rewards

---

## Technical Architecture (If Implemented)

### Stablecoin Payments

**Recommended: USDC on Ethereum Layer 2**

**Why Stablecoins:**

- Value stability (not volatile like Bitcoin)
- Fast transactions (<3 seconds)
- Low fees ($0.01-0.05)
- Widely accepted
- Can cash out to local currency

**Why Ethereum L2 (Polygon or Base):**

- Same blockchain as identity system
- Single wallet for both identity and payments
- Mature ecosystem
- Mobile wallet support

---

### DEX-Only Strategy

**CRITICAL: No Centralized Exchanges (CEXs)**

**Why DEX-Only:**

- Centralized exchanges require KYC (Know Your Customer)
- KYC links wallet to real identity
- Destroys pseudonymity
- Creates tracking risk

**Decentralized Exchanges (DEXs):**

- Uniswap, PancakeSwap, Curve
- No ID required
- Direct wallet-to-wallet trading
- USDC → Local currency tokens

---

### Wallet Separation Protocol

**MANDATORY: Separate Wallets for Identity vs Payments**

**Identity Wallet (Existing):**

- Used for authentication
- Governance voting
- Contact verification
- NEVER receives payments
- NEVER connects to exchanges

**Payment Wallet (New, Optional):**

- Created separately
- Used ONLY for payments
- Can connect to DEX
- NEVER used for governance
- Kept completely separate

**Why Separation Critical:**

- Identity wallet must remain pseudonymous
- Payment activity can be analyzed
- Separate wallets = separate identities
- One compromised doesn't expose the other

---

### P2P Cash-Out Strategies

**Local Exchange Network:**

**Trusted Local Exchangers:**

- Community members who buy/sell crypto
- Meet in person, exchange cash for USDC
- Similar to informal money changers
- Build reputation over time

**Process:**

```
1. Operator earns USDC in payment wallet
2. Finds local exchanger in community
3. Meets in person
4. Transfers USDC to exchanger's wallet
5. Receives local cash
6. No bank, no KYC, no trace
```

**Safety Protocols:**

- Only use trusted community exchangers
- Public meeting places
- Small amounts initially
- Verify transaction before handing cash
- Build trust gradually

---

## Smart Contract Design (Conceptual)

### Operator Compensation Contract

**Automated Monthly Payments:**

```
Function: distributeMonthlyStipends()
- Reads operator list from governance contract
- Checks uptime metrics
- Calculates payment amount
- Transfers USDC to payment wallets
- Logs transaction for transparency
```

**Performance Bonuses:**

- 99%+ uptime: +20%
- 95-99% uptime: Base pay
- <95% uptime: -25%

### Mutual Aid Pool

**Community Emergency Fund:**

```
Function: requestEmergencyAid(amount, reason)
- User submits request
- Moderators verify need
- Community votes (if >$100)
- Funds released to user's payment wallet
- Repayment optional (solidarity model)
```

**Pool Funding:**

- Voluntary contributions
- Percentage of operator compensation
- External donations
- Grant funding

---

## Security Considerations

### Financial Risks

**Money Makes Targets:**

- Adding payments increases threat level
- Operators become targets for robbery
- Wallet theft becomes profitable
- Requires enhanced OpSec

**Regulatory Risk:**

- Some countries ban cryptocurrency
- Payment features could be illegal
- May attract government attention
- Must assess per region

**Wallet Compromise:**

- If payment wallet stolen, funds lost
- No recovery mechanism (decentralized)
- Users must secure seed phrases carefully
- Hardware wallets recommended for large amounts

---

## Implementation Requirements

### Prerequisites (Must Be Met Before Phase 6)

**Technical:**

- [ ] Phases 1-5 complete and stable
- [ ] Identity system proven secure
- [ ] Governance functioning well
- [ ] Community size >500 users
- [ ] Legal review completed

**Community:**

- [ ] Clear demand for payment features
- [ ] Local exchangers identified
- [ ] OpSec training completed
- [ ] Risk assessment done

**Development:**

- [ ] Smart contract audit ($25k)
- [ ] Payment wallet UI
- [ ] P2P exchange matching system
- [ ] Training materials

**Estimated Cost:** $50-75k development + audit  
**Estimated Timeline:** 3-4 months

---

## Regional Risk Assessment

**High Risk (Defer Indefinitely):**

- Countries with crypto bans
- Regions with high robbery rates
- Areas with strict financial surveillance
- Unstable legal environments

**Medium Risk (Proceed with Caution):**

- Legal gray areas
- Moderate security concerns
- Limited enforcement capacity
- Assess case-by-case

**Low Risk (Can Implement):**

- Crypto-friendly regulations
- Secure operational environment
- Strong community trust
- Legal clarity

---

## Alternatives to Blockchain Payments

**If blockchain payments too risky:**

**Option A: In-Kind Compensation**

- Provide equipment, not cash
- Food, supplies, services
- No financial trail
- Simpler, safer

**Option B: Traditional Banking**

- Use existing money transfer services
- Mobile money (M-Pesa style)
- Lower tech, higher traceability
- May be acceptable in some regions

**Option C: Hybrid**

- Essential operators: In-kind
- Voluntary contributions: Blockchain
- Flexibility per region

---

## Decision Framework

**Should Community Add Phase 6 Payments?**

**Consider:**

1. Is compensation necessary for sustainability?
2. Are security risks acceptable?
3. Is legal environment permissive?
4. Do local exchangers exist?
5. Can users handle wallet separation?

**If ANY answer is "no" → Defer Phase 6**

**Payment features are optional enhancements, not requirements.**

---

## Status

**Current State:** Conceptual design only  
**Implementation:** Not before Phase 5 complete (Month 10+)  
**Decision:** Defer until community requests  
**Blockers:** Phases 1-5 must succeed first

---

## Related Documents

- [[04A-identity-system]]: Wallet architecture and privacy
- [[04B - Governance - Overview]]: Community decision-making
- [[11 - Development - Overview]]: Phase 1-5 prioritization
- [[08 - Security & Encryption]]: OpSec considerations for payments