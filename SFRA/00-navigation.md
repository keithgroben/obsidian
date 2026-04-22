---
filename: "00-navigation.md"
title: Navigation
section: 0
subsection: nav
parent: root
description: Hierarchical navigation structure for all project documentation
tags: [navigation, index, structure, toc]
related: [ref-a-status-assessment, ref-b-documentation-principles-standards]
version: 2.0
updated: 2025-10-17
status: Production-Ready
completeness: 10
word_count: 350
---

## Navigation

### 00-03 System Core

* [[00-navigation]]
* [[01-system-overview]]
* [[02-architecture]]
* [[03-hardware-specifications]]

---

### 04-Identity, Governance, and Communication

* [[04A-identity-system]]
* **[[04B-Governance]]**
    * [[04B-00-governance-overview]]
    * [[04B1-governance-moderators]]
    * [[04B2-governance-smart-contracts]]
    * [[04B3-governance-operators]]
    * [[04B4-governance-conflicts]]
    * [[04B5-governance-voting]]
* [[04-communication-protocol-overview]]

---

### 05-07 System Infrastructure

* [[05-mesh-networking]]
* [[06-ipfs-integration]]
* [[07-video-handling]]

---

### 08-Security

* [[08-00-security-overview]]
* [[08-01-security-encryption-keys]]
* [[08-02-security-panic-mode]]
* [[08-03-security-ipfs-threat-model]]

---

### 09-User Experience (UX)

* [[09A-ux-onboarding]]
* **[[09B-Core UX Flows]]**
    * [[09B-00-ux-core-flows]]
    * [[09B-01-ux-messaging-flow]]
    * [[09B-02-ux-video-flow]]
    * [[09B-03-ux-queue-management]]
    * [[09B-04-ux-content-viewing]]
* [[09C-ux-security-interface]]
* [[09-ux-principles]]

---

### 10-Deployment

* [[10-00-deployment-overview]]
* [[10-01-deployment-pre-planning]]
* [[10-02-deployment-installation]]
* [[10-03-deployment-training]]
* [[10-04-deployment-operations]]

---

### 11-Development

* [[11-00-development-overview]]
* [[11-01-development-phases]]
* [[11-02-development-stack]]
* [[11A-development-team-budget]]
* [[11B-development-testing]]

---

### Reference (ref)

* [[ref-a-status-assessment]]
* [[ref-b-documentation-principles-standards]]
* [[ref-c-glossary]]
* [[ref-d-payment-systems-phase-6]]
* [[ref-e-project-name]]

---
# Quick Stats
stats:
  total_files: 41
  production_ready: 23
  approved: 15
  needs_work: 3
  overall_score: 8.2
  phase_1_ready: true

# Key Relationships
relationships:
  governance_system: [04B-00, 04B1, 04B2, 04B3, 04B4, 04B5]
  ux_flows: [09B-00, 09B-01, 09B-02, 09B-03, 09B-04]
  security_layer: [08-00, 08-01, 08-02, 08-03]
  deployment_process: [10-00, 10-01, 10-02, 10-03, 10-04]
  development_plan: [11-00, 11-01, 11-02, 11A, 11B]