---
title: Documentation Checklist - RAG Optimized
section: ref
description: Streamlined documentation index for efficient RAG retrieval
tags: [reference, index, rag-optimized]
version: 2.0
updated: 2025-10-23
---

# Core System (00-03)
files:

id: "00"
file: 00-navigation.md
title: Navigation
tags: [navigation, index]
status: 10/10

id: "01"
file: 01-system-overview.md
title: System Overview
section: 1
tags: [overview, architecture]
related: [02, 03]
status: 8/10

id: "02"
file: 02-architecture.md
title: Architecture
section: 2
tags: [architecture, design, layers]
related: [01, 03, 05]
status: 8/10

id: "03"
file: 03-hardware-specifications.md
title: Hardware
section: 3
tags: [hardware, raspberry-pi, solar]
related: [02, 10-02]
status: 9/10

# Communication (04-Series)
id: "04"
file: 04-communication-protocol-overview.md
title: Communication Protocol
section: 4.0
tags: [protocol, matrix, web3]
related: [04A, 04B-00, 05]
status: 8/10

id: "04A"
file: 04A-identity-system.md
title: Identity
section: 4.A
tags: [identity, wallet, privacy]
related: [04, 04B-00, 08-01]
status: 8/10

id: "04B-00"
file: 04B-00-governance-overview.md
title: Governance Overview
section: 4.B.0
tags: [governance, dao]
related: [04B1, 04B2, 04B3, 04B4, 04B5]
status: 9/10

id: "04B1"
file: 04B1-governance-moderators.md
title: Moderators
section: 4.B.1
tags: [governance, moderators]
parent: 04B-00
status: 9/10

id: "04B2"
file: 04B2-governance-smart-contracts.md
title: Smart Contracts
section: 4.B.2
tags: [governance, contracts, upgrades]
parent: 04B-00
status: 9/10

id: "04B3"
file: 04B3-governance-operators.md
title: Operators
section: 4.B.3
tags: [governance, operators, sla]
parent: 04B-00
status: 9/10

id: "04B4"
file: 04B4-governance-conflicts.md
title: Conflicts
section: 4.B.4
tags: [governance, disputes]
parent: 04B-00
status: 9/10

id: "04B5"
file: 04B-05-governance-voting.md
title: Voting
section: 4.B.5
tags: [governance, voting]
parent: 04B-00
status: 9/10

# Infrastructure (05-07)
id: "05"
file: 05-mesh-networking.md
title: Mesh Networking
section: 5
tags: [mesh, babel, queue]
related: [02, 06, 07, 09B-03]
status: 8/10

id: "06"
file: 06-ipfs-integration.md
title: IPFS
section: 6
tags: [ipfs, storage, gateway]
related: [05, 07, 08-03]
status: 7/10

id: "07"
file: 07-video-handling.md
title: Video
section: 7
tags: [video, compression]
related: [05, 06, 09B-02]
status: 7/10

# Security (08-Series)
id: "08-00"
file: 08-00-security-overview.md
title: Security Overview
section: 8.0
tags: [security, threat-model]
related: [08-01, 08-02, 08-03]
status: 8/10

id: "08-01"
file: 08-01-security-encryption-keys.md
title: Encryption
section: 8.1
tags: [security, encryption, keys]
parent: 08-00
status: 8/10

id: "08-02"
file: 08-02-security-panic-mode.md
title: Panic Mode
section: 8.2
tags: [security, panic, duress]
parent: 08-00
status: 8/10

id: "08-03"
file: 08-03-security-ipfs-threat-model.md
title: IPFS Threats
section: 8.3
tags: [security, ipfs, privacy]
parent: 08-00
status: 8/10

# UX (09-Series)
id: "09"
file: 09-ux-principles.md
title: UX Principles
section: 9.0
tags: [ux, design]
related: [09A, 09B-00, 09C]
status: 8/10

id: "09A"
file: 09A-ux-onboarding.md
title: Onboarding
section: 9.A
tags: [ux, onboarding]
parent: 09
status: 8/10

id: "09B-00"
file: 09B-00-ux-core-flows.md
title: Core Flows
section: 9.B.0
tags: [ux, flows]
related: [09B-01, 09B-02, 09B-03, 09B-04]
status: 8/10

id: "09B-01"
file: 09B-01-ux-messaging-flow.md
title: Messaging
section: 9.B.1
tags: [ux, messaging]
parent: 09B-00
status: 8/10

id: "09B-02"
file: 09B-02-ux-video-flow.md
title: Video Flow
section: 9.B.2
tags: [ux, video]
parent: 09B-00
status: 8/10

id: "09B-03"
file: 09B-03-ux-queue-management.md
title: Queue UI
section: 9.B.3
tags: [ux, queue]
parent: 09B-00
status: 8/10

id: "09B-04"
file: 09B-04-ux-content-viewing.md
title: Content Viewing
section: 9.B.4
tags: [ux, gallery]
parent: 09B-00
status: 8/10

id: "09C"
file: 09C-ux-security-interface.md
title: Security UI
section: 9.C
tags: [ux, security]
parent: 09
status: 8/10

# Deployment (10-Series)
id: "10-00"
file: 10-00-deployment-overview.md
title: Deployment Overview
section: 10.0
tags: [deployment]
related: [10-01, 10-02, 10-03, 10-04]
status: 8/10

id: "10-01"
file: 10-01-deployment-pre-planning.md
title: Pre-Planning
section: 10.1
tags: [deployment, planning]
parent: 10-00
status: 8/10

id: "10-02"
file: 10-02-deployment-installation.md
title: Installation
section: 10.2
tags: [deployment, installation]
parent: 10-00
status: 8/10

id: "10-03"
file: 10-03-deployment-training.md
title: Training
section: 10.3
tags: [deployment, training]
parent: 10-00
status: 8/10

id: "10-04"
file: 10-04-deployment-operations.md
title: Operations
section: 10.4
tags: [deployment, operations]
parent: 10-00
status: 8/10

# Development (11-Series)
id: "11-00"
file: 11-00-development-overview.md
title: Development Overview
section: 11.0
tags: [development, roadmap]
related: [11-01, 11-02, 11A, 11B]
status: 9/10

id: "11-01"
file: 11-01-development-phases.md
title: Phases
section: 11.1
tags: [development, phases]
parent: 11-00
status: 9/10

id: "11-02"
file: 11-02-development-stack.md
title: Tech Stack
section: 11.2
tags: [development, stack]
parent: 11-00
status: 9/10

id: "11A"
file: 11A-development-team-budget.md
title: Team & Budget
section: 11.A
tags: [development, budget]
parent: 11-00
status: 9/10

id: "11B"
file: 11B-development-testing.md
title: Testing
section: 11.B
tags: [development, testing]
parent: 11-00
status: 9/10

# Reference (ref)
id: "ref-a"
file: ref-a-status-assessment.md
title: Status Assessment
tags: [reference, status]
status: 9/10

id: "ref-b"
file: ref-b-documentation-principles-standards.md
title: Doc Standards
tags: [reference, standards]
status: 10/10

id: "ref-c"
file: ref-c-glossary.md
title: Glossary
tags: [reference, glossary]
status: 10/10

id: "ref-d"
file: ref-d-payment-systems-phase-6.md
title: Payment Systems
tags: [reference, future, phase-6]
status: 5/10

id: "ref-e"
file: ref-e-project-name.md
title: Project Name
tags: [reference, naming]
status: 4/10
