# ARGM: Agentic Runtime Governance Model

**Version:** 1.1 | **Licence:** CC-BY-SA 4.0 | **Date:** 2026-04-06

ARGM provides a six-level maturity framework for assessing how organisations govern AI agents at runtime. It addresses the operational gap between existing AI governance frameworks (NIST AI RMF, ISO 42001, CMMI) and the reality of agents that write files, execute shell commands, invoke APIs, and make irreversible system state changes.

---

## Six-Level Maturity Summary

| Level | Name | Definition |
|-------|------|-----------|
| 0 | Ungoverned | No runtime governance. Agent operates on default model behaviour. |
| 1 | Instructed | Basic prompt-level governance. Coding standards, validation gates, behavioural expectations. Enforcement relies on model compliance. |
| 2 | Secured | D1 (Security Controls) enforced. Credential hygiene, injection defence, CORS, rate limiting, pre-commit scanning enforced as technical controls. |
| 3 | Aligned | All seven directives active. Value alignment tiers, scope boundaries, cost governance, delivery standards. Full D0–D6 conflict resolution order declared unconditional. |
| 4 | Governed | All directives integrated. Autonomous operation controls (turn limits, dry-run defaults, overnight safety). Conflict resolution unconditional. Framework auditable end-to-end. |
| 5 | Autonomous | Framework governs itself. Automated drift detection, lint hooks, health reporting. Continuous assurance without manual audit. |

---

## Prime Directive Architecture (D0–D6)

At Level 4 and above, governance is organised as seven numbered prime directives. The number encodes conflict resolution priority: **D0 wins unconditionally. D6 has lowest priority.**

| Directive | Name | Scope |
|-----------|------|-------|
| D0 | Data Protection | Client data isolation, PII handling, retention limits, placeholder enforcement |
| D1 | Security Controls | Secrets management, CORS, rate limiting, injection defence, pre-commit scanning |
| D2 | Autonomous Operation | Turn limits, dry-run defaults, destructive operation prohibition, overnight safety, logging |
| D3 | Revenue Alignment | Value tiers, scope boundaries, proactive vs reactive build decisions |
| D4 | Infrastructure Portability | Tenant strategy, SKU selection, cost targets, auth architecture |
| D5 | Operational Efficiency | Automation targets, JSON output schemas, template consumption patterns |
| D6 | Delivery Standards | Output quality, branding, turnaround SLAs, formatted wrapper requirements |

**Conflict Resolution Order:** D0 > D1 > D2 > D3 > D4 > D5 > D6 — unconditional, no runtime exceptions.

---

## Quick Start

### 1. Establish your current level

Read the [assessment template](assessment/assessment-template.md) and answer all five questions for each level with evidence. Use the [scoring guide](assessment/scoring-guide.md) to determine your current ARGM level.

### 2. Identify gaps

Use the [evidence checklist](assessment/evidence-checklist.md) to identify which specific controls are missing for the next level.

### 3. Implement

Use the [examples](examples/) as stubs for each level. Adapt to your tools and context.

### 4. Verify

A level is achieved when all five assessment questions score ≥1 and at least three score 2. Evidence must be artefact-based — claims without artefacts do not count.

---

## Repository Structure

```
argm/
├── README.md                      # This file
├── LICENCE                        # CC-BY-SA 4.0
├── CHANGELOG.md                   # Version history
├── docs/
│   ├── argm-framework.md          # Full framework — Sections 1–5
│   ├── argm-mapping.md            # Cross-framework mapping
│   ├── argm-gap-analysis.md       # Gap analysis vs existing models
│   ├── argm-naming.md             # Naming rationale
│   └── argm-references.md         # References
├── assessment/
│   ├── assessment-template.md     # All assessment questions, Levels 0–5
│   ├── evidence-checklist.md      # All observable evidence items
│   └── scoring-guide.md           # Scoring methodology
├── examples/
│   ├── level-1-claude-md.md       # Level 1: example governance document
│   ├── level-2-security.md        # Level 2: security controls configuration
│   ├── level-3-directives.md      # Level 3: prime directives and value alignment
│   ├── level-4-framework.md       # Level 4: full governed framework structure
│   └── level-5-monitoring.md      # Level 5: governance self-monitoring
└── .github/
    ├── CONTRIBUTING.md
    └── ISSUE_TEMPLATE/
```

---

## Design Rationale

ARGM addresses five gaps identified across surveyed models:

1. **Agentic autonomy controls** — turn limits, dry-run defaults, destructive operation prohibition, overnight safety rules
2. **Multi-agent scope bounding** — what each agent is permitted to build, proactive vs reactive
3. **Runtime self-monitoring** — automated verification that governance documents have not been weakened
4. **Business value alignment** — agent effort maps to organisational priorities, treated as a governance dimension
5. **Cost governance** — token budgets and compute cost tracking as first-class maturity requirements

Full rationale, research foundation, and cross-framework mappings are in [docs/argm-framework.md](docs/argm-framework.md).

---

## Contributing

See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

---

## Licence

CC-BY-SA 4.0 — see [LICENCE](LICENCE).
