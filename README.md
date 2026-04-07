# ARGM: Agentic Runtime Governance Model

**Version:** 2.0 | **Licence:** CC-BY-SA 4.0 | **Date:** 2026-04-06

ARGM provides a seven-level maturity framework (0–6) for assessing how organisations govern AI agents at runtime. It is a domain-specific maturity profile, built on CMMI's structural conventions, that addresses the operational gap between existing AI governance frameworks and the reality of agents that write files, execute shell commands, invoke APIs, and make irreversible system state changes.

ARGM complements ISO 42001 (AI management system), NIST AI RMF (risk management), and AISM (agent security). It does not replace them.

---

## Seven-Level Maturity Summary

| Level | Name | Definition |
|-------|------|-----------|
| 0 | Ungoverned | No runtime governance. Agent operates on default model behaviour. |
| 1 | Instructed | Prompt-level governance. Coding standards, validation gates, behavioural expectations. |
| 2 | Secured | D0 (Data Protection) and D1 (Security Controls) enforced by technical controls. |
| 3 | Controlled | D2 (Autonomous Operation) enforced. Turn limits, dry-run defaults, destructive operation prohibition. |
| 4 | Aligned | D3–D6 (Business Directives) active. Value alignment, cost governance, delivery standards. Sector-configurable ordering. |
| 5 | Governed | All directives integrated. Break-glass exception mechanism. Cross-agent consistency. Auditable end-to-end. |
| 6 | Autonomous | Framework governs itself. Drift detection, automated health reporting, three-layer assurance. |

---

## Two-Tier Directive Architecture

Governance directives are split into two tiers with different conflict resolution rules and different escalation paths.

**Tier 1 — Safety (unconditional):**

| Directive | Name | Scope |
|-----------|------|-------|
| D0 | Data Protection | Client data isolation, PII handling, retention limits |
| D1 | Security Controls | Secrets management, CORS, rate limiting, injection defence |
| D2 | Autonomous Operation | Turn limits, dry-run defaults, destructive operation prohibition |

Conflict resolution: D0 > D1 > D2. No exceptions. No break-glass.

**Tier 2 — Business (sector-configurable):**

| Directive | Name | Scope |
|-----------|------|-------|
| D3 | Value Alignment | Value tiers, scope boundaries, build decisions |
| D4 | Infrastructure Governance | Tenant strategy, cost targets, auth architecture |
| D5 | Operational Efficiency | Automation targets, output schemas |
| D6 | Delivery Standards | Output quality, formatting, turnaround expectations |

Default order: D3 > D4 > D5 > D6. Organisations may reorder with documented rationale. Tier 2 never overrides Tier 1. Break-glass is available at Level 5 and above for Tier 2 directives only.

---

## Quick Start

### 1. Establish your current level

Read the [assessment template](assessment/assessment-template.md) and answer all questions for each level with evidence. Use the [scoring guide](assessment/scoring-guide.md) to determine your current ARGM level.

### 2. Identify gaps

Use the [evidence checklist](assessment/evidence-checklist.md) to identify which specific controls are missing for the next level.

### 3. Implement

Use the [examples](examples/) as stubs for each level. Adapt to your tools and context.

### 4. Verify

A level is achieved when all assessment questions score ≥1 and at least three score 2. Evidence must be artefact-based — claims without artefacts do not count.

---

## Repository Structure

```
argm/
├── README.md
├── LICENCE
├── CHANGELOG.md
├── docs/
│   ├── argm-framework.md          # Full framework — Sections 1–5
│   ├── argm-mapping.md            # Cross-framework mapping + generic agent guide
│   ├── argm-gap-analysis.md       # Gap analysis vs existing models
│   ├── argm-naming.md             # Naming rationale and structural heritage
│   └── argm-references.md         # References
├── assessment/
│   ├── assessment-template.md     # All assessment questions, Levels 0–6
│   ├── evidence-checklist.md      # All observable evidence items
│   └── scoring-guide.md           # Scoring methodology
├── examples/
│   ├── level-1-claude-md.md
│   ├── level-2-security.md
│   ├── level-3-directives.md      # Autonomous operation controls
│   ├── level-4-aligned.md         # Business directives + cost governance
│   ├── level-5-governed.md        # Full framework + break-glass
│   ├── level-6-autonomous.md      # Self-monitoring + regress solution
│   └── wsc-reference-implementation.md  # WSC-specific agent mapping
└── .github/
    ├── CONTRIBUTING.md
    └── ISSUE_TEMPLATE/
```

---

## Design Rationale

ARGM addresses three gaps not covered by existing models in combination:

1. **Runtime governance self-monitoring** — automated detection of governance document weakening
2. **Business value alignment as governance** — agent effort mapped to organisational priorities as a governance control
3. **Cost governance** — token budgets, model selection, and cost attribution as maturity requirements

ARGM is built on CMMI's maturity structure by design. Full rationale, research foundation, and cross-framework mappings in [docs/argm-framework.md](docs/argm-framework.md).

---

## Positioning

ARGM is:
- A domain-specific CMMI profile for AI agent runtime governance
- Self-assessment only (no certification pathway)
- Complementary to ISO 42001, NIST AI RMF, and AISM

ARGM is not:
- A threat model (see AISM Agent Threat and Control Matrix)
- A lifecycle governance framework (see ISO 42001)
- An adoption maturity model (see Microsoft Agentic AI Adoption Model)
- An incident response framework (see NIST CSF Respond)

---

## Contributing

See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

---

## Licence

CC-BY-SA 4.0 — see [LICENCE](LICENCE).
