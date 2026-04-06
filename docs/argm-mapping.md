# ARGM — Cross-Framework Mapping

**Source:** ARGM v1.0 DRAFT, Section 6

---

## 6. Cross-Framework Mapping

### ARGM to NIST CSF 2.0 Implementation Tiers

| ARGM Level | NIST CSF Tier | Rationale |
|-----------|---------------|-----------|
| 0 - Ungoverned | Below Tier 1 | Tier 1 (Partial) assumes some risk awareness. Level 0 assumes none. |
| 1 - Instructed | Tier 1 - Partial | Ad hoc, informal, inconsistent. |
| 2 - Secured | Tier 2 - Risk Informed | Security controls with risk awareness. Not yet enterprise-wide. |
| 3 - Aligned | Tier 2/3 boundary | Business-aware governance bridging risk-informed and repeatable. |
| 4 - Governed | Tier 3 - Repeatable | Formalised, consistent, cross-agent. |
| 5 - Autonomous | Tier 4 - Adaptive | Self-monitoring, continuous improvement, automated adaptation. |

### ARGM to CMMI Maturity Levels

| ARGM Level | CMMI Level | Rationale |
|-----------|------------|-----------|
| 0 - Ungoverned | 0 Incomplete / 1 Initial | No documented processes. Individual heroics. |
| 1 - Instructed | 1 Initial (upper bound) | Documented but inconsistently followed. |
| 2 - Secured | 2 Managed | Planned, performed, measured, controlled security. |
| 3 - Aligned | 3 Defined | Organisational standard processes established. |
| 4 - Governed | 4 Quantitatively Managed | Quantitative targets (cost budgets, turn limits, compliance metrics). |
| 5 - Autonomous | 5 Optimizing | Continuous improvement through automated monitoring. |

### ARGM to NIST AI RMF Functions

| ARGM Level | GOVERN | MAP | MEASURE | MANAGE |
|-----------|--------|-----|---------|--------|
| 0 | None | None | None | None |
| 1 | Partial | Partial | None | None |
| 2 | Active (security) | Active (attack surface) | Partial (scans) | Partial (incidents) |
| 3 | Active (business) | Active (value mapping) | Active (cost, quality) | Active (scope) |
| 4 | Full (unified) | Full (all dimensions) | Full (quantitative) | Full (conflict resolution) |
| 5 | Self-governing | Continuously updated | Automated | Automated |

### ARGM to ISO 42001 Clauses

| ISO 42001 Clause | First Addressed | Full Implementation |
|------------------|----------------|---------------------|
| 4. Context | Level 1 | Level 3 |
| 5. Leadership | Level 1 | Level 4 |
| 6. Planning | Level 2 | Level 3 |
| 7. Support | Level 1 | Level 4 |
| 8. Operation | Level 2 | Level 4 |
| 9. Performance evaluation | Level 3 | Level 5 |
| 10. Improvement | Level 4 | Level 5 |

### ARGM to AISM (Cyber Strategy Institute)

| ARGM Level | AISM Level | Overlap | Divergence |
|-----------|-----------|---------|------------|
| 0 - Ungoverned | Chaos | Both describe ungoverned state | AISM includes NHI sprawl; ARGM focuses on runtime behaviour |
| 1 - Instructed | Chaos/Visibility boundary | ARGM addresses instruction quality; AISM addresses asset visibility | AISM's Ledger pillar starts earlier |
| 2 - Secured | Visibility/Governance boundary | Both include input sanitisation, circuit breakers | AISM's five pillars cover security more broadly |
| 3 - Aligned | Governance | Both establish governance | AISM does not include business value alignment or cost governance |
| 4 - Governed | Control | Both describe comprehensive frameworks | AISM has 128 controls; ARGM has seven pillars |
| 5 - Autonomous | Sovereignty | Both describe self-governing capability | AISM includes cryptographic identity; ARGM focuses on drift detection |

### ARGM to Microsoft Agentic AI Adoption Maturity Model

| ARGM Level | Microsoft Level | Key Difference |
|-----------|----------------|----------------|
| 0 | Below 100 | Microsoft assumes experimentation; ARGM assumes nothing |
| 1 | 100 - Initial | Microsoft is adoption; ARGM is governance |
| 2 | 200 - Repeatable | Microsoft does not prescribe specific security controls |
| 3 | 300 - Defined | ARGM prescribes cost governance and value tiers |
| 4 | 400 - Capable | ARGM prescribes autonomous operation controls |
| 5 | 500 - Efficient | ARGM requires self-monitoring; Microsoft requires agent-first culture |
