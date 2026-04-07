---
title: "ARGM: Gap Analysis vs Existing Models"
tags: [argm, gap-analysis, governance]
date: 2026-04-06
---

# ARGM: Gap Analysis vs Existing Models

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

---

## Where ARGM Goes Further

ARGM makes three genuine contributions to the agentic governance landscape. These are areas where no surveyed framework addresses the specific concern as a formal maturity requirement.

| Gap | Detail |
|-----|--------|
| **Runtime governance self-monitoring and drift detection** | Level 6 requires automated detection of governance document weakening — lint hooks, continuous compliance reporting, and alerting when directive constraints are modified or removed. Existing models monitor for threats (AISM) or system performance (NIST); ARGM monitors for governance erosion specifically. This treats governance documents as attack surfaces and requires tooling that detects when safety controls are degraded over time. |
| **Business value alignment as a governance dimension** | Level 4 introduces value tiers, scope boundaries, and classification mechanisms as formal governance controls with observable evidence requirements. Other models treat value alignment as strategy (Microsoft Agentic AI Adoption Maturity Model) or adoption readiness (Salesforce Agentic Maturity Model), not as a runtime governance control that constrains what agents are permitted to work on. ARGM encodes this as directive D3 with mandatory evidence requirements. |
| **Cost governance as a first-class maturity requirement** | Level 4 requires model selection policy, budget allocation, cost attribution, and escalation thresholds as maturity evidence. No surveyed framework treats agentic cost governance as a maturity dimension. The FinOps Foundation covers cloud cost governance broadly; ARGM's contribution is applying cost governance as a formal requirement for agentic operations specifically, with observable evidence at a defined maturity level. |

---

## Where Existing Models Go Further Than ARGM

| Gap | Model | Detail |
|-----|-------|--------|
| **Non-human identity governance** | AISM | Agent identity verification, cryptographic identity at Sovereignty level. ARGM governs behaviour and permissions but does not define an identity framework for agents. |
| **Swarm governance and inter-agent trust** | AISM | Multi-agent swarm coordination, agent-to-agent trust, distributed governance, and trust chain management. ARGM requires cross-agent consistency (Level 5) but does not govern inter-agent communication protocols or trust chains between agents. |
| **Autonomy controls depth** | AISM | The Circuit Breaker pillar covers kill switches, rate limiting, and automated shutdown with comparable depth to ARGM's D2 Safety Controls. ARGM adds dry-run defaults and turn limits as governance controls; AISM covers the broader agent safety surface including failure modes and recovery. |
| **Threat model specificity** | AISM, MITRE ATLAS | Agent Threat and Control Matrix with 10 threat categories, MITRE ATLAS cross-references, OWASP LLM mappings. ARGM defers to existing threat frameworks and does not define its own threat taxonomy. |
| **Runtime agent controls (NIST)** | NIST SP 800-53 | SP 800-53 AI control overlays (Aug 2025) now address single-agent and multi-agent deployment controls. ARGM's claim that NIST does not address runtime behaviour requires qualification — the Aug 2025 overlays extend security and privacy controls explicitly to AI systems including agentic deployments. |
| **Immutable audit trails** | AISM | Sovereignty level requires immutable ledgers and cryptographic logging. ARGM requires logging but does not specify immutability mechanisms or cryptographic verification. |
| **Compliance crosswalk granularity** | AISM | Control-level mapping to NIST AI RMF, ISO 42001. ARGM provides level-to-framework mapping, not control-level crosswalk. |
| **Fairness and bias** | NIST AI RMF, ISO 42001 | ARGM governs what agents do and how they do it, not the equity of their outputs. Fairness and bias belong in lifecycle governance and model evaluation, not runtime governance. |
| **Certification pathway** | ISO 42001 | Third-party certification available. ARGM is self-assessment only; no external certification body exists. |

---

## What ARGM Does Not Cover

ARGM is a runtime governance maturity model. The following areas are explicitly out of scope. Practitioners should use the referenced frameworks for these concerns.

| Out-of-scope area | Recommended framework |
|-------------------|----------------------|
| **Threat modelling** | AISM Agent Threat and Control Matrix, MITRE ATLAS |
| **Non-human identity governance** | AISM Sovereignty pillar |
| **Fairness and bias** | NIST AI RMF, ISO 42001 |
| **Certification pathway** | ISO 42001 (third-party certifiable) |
| **Incident response** | NIST CSF Respond function |
| **Non-coding agents** (customer support, HR, purchasing) | Acknowledged gap. ARGM's current scope covers agents that write files, execute shell commands, invoke APIs, and make irreversible system state changes. Conversational and transactional agents are not addressed. Future work. |
| **Multi-tenancy and context leakage** | Acknowledged gap. ARGM does not address governance of context leakage between client sessions in shared agentic deployments. Future work. |

---

## Consolidated: What ARGM Addresses That No Single Existing Model Does

1. Runtime self-monitoring as a maturity requirement — governance drift detection, not just threat detection
2. Business value alignment as a runtime governance dimension with observable evidence requirements
3. Cost governance for agentic operations as a formal maturity level criterion
