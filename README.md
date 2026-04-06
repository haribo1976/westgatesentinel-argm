# ARGM: Agentic Runtime Governance Model

**Version:** 1.0 DRAFT
**Licence:** CC-BY-SA 4.0

ARGM provides a six-level maturity framework (0–5) for assessing how organisations govern AI agents at runtime. It addresses the operational gap between existing AI governance frameworks (NIST AI RMF, ISO 42001, CMMI) and the reality of agents that write files, execute shell commands, invoke APIs, and make irreversible system state changes.

Existing frameworks govern the AI lifecycle, organisational readiness, and risk management processes. None of them answer the question: *what rules govern this agent's behaviour while it is running?*

ARGM answers that question with progressive maturity levels, observable evidence requirements, assessment questions, and a seven-pillar reference architecture for full governance.

---

## Six-Level Summary

| Level | Name | Definition |
|-------|------|------------|
| 0 | Ungoverned | No runtime governance. Agent operates on default model behaviour. No explicit rules, no scope control, no security controls. |
| 1 | Instructed | Basic prompt-level instructions in place. Governance documents define coding standards, validation gates, and behavioural expectations. Enforcement depends entirely on model compliance. |
| 2 | Secured | Security layer added. Credential hygiene, injection defence, CORS policy, rate limiting, and pre-commit scanning enforced as technical controls, not solely prompt-based. |
| 3 | Aligned | Business governance added. Value alignment tiers map agent effort to organisational priorities. Scope boundaries, cost constraints, and delivery standards active. |
| 4 | Governed | Full multi-pillar operating framework active. Autonomous operation controls, conflict resolution order, third-party data isolation, and governance review cadence all enforced. |
| 5 | Autonomous | The governance framework governs itself. Self-monitoring detects drift, reports on compliance health, and enforces governance document integrity without manual intervention. |

---

## Seven-Pillar Reference Architecture (Level 4+)

At Level 4 and above, governance should be organised into defined pillars. This seven-pillar architecture is a reference model. Organisations adapt pillar count and scope to their context.

| Pillar | Name | Scope |
|--------|------|-------|
| P0 | Data Protection | Client data isolation, PII handling, retention limits, placeholder enforcement |
| P1 | Revenue Alignment | Value tiers, scope boundaries, proactive vs reactive build decisions |
| P2 | Infrastructure Portability | Tenant strategy, SKU selection, cost targets, auth architecture |
| P3 | Delivery Standards | Output quality, branding, turnaround SLAs, formatted wrapper requirements |
| P4 | Operational Efficiency | Automation targets, JSON output schemas, template consumption patterns |
| P5 | Security Controls | Secrets management, CORS, rate limiting, injection defence, pre-commit scanning |
| P6 | Autonomous Operation | Turn limits, dry-run defaults, destructive operation prohibition, overnight safety, logging |

**Conflict Resolution Order:** P0 > P6 > P1 > P2 > P4 > P3 > P5

Data protection wins unconditionally. Autonomous operation safety overrides business priorities. Security controls (P5) rank lower than business pillars because security is non-negotiable from Level 2 upward and does not require priority arbitration in the same way business rules do.

---

## Quick Start

1. **Assess your current level** — work through [`assessment/assessment-template.md`](assessment/assessment-template.md) using the questions for each level
2. **Check observable evidence** — use [`assessment/evidence-checklist.md`](assessment/evidence-checklist.md) to verify what you can demonstrate today
3. **Understand scoring** — read [`assessment/scoring-guide.md`](assessment/scoring-guide.md) for how levels are determined
4. **Read the full framework** — [`docs/argm-framework.md`](docs/argm-framework.md) contains sections 1–5 (purpose, research foundation, design decisions, level definitions, seven-pillar architecture)
5. **See cross-framework mappings** — [`docs/argm-mapping.md`](docs/argm-mapping.md) maps ARGM to NIST CSF, CMMI, NIST AI RMF, ISO 42001, AISM, and Microsoft's model
6. **Review examples** — the [`examples/`](examples/) directory contains illustrative governance configurations at each level

---

## Repository Structure

```
argm/
├── docs/
│   ├── argm-framework.md        # Sections 1–5: full model
│   ├── argm-mapping.md          # Section 6: cross-framework mapping
│   ├── argm-gap-analysis.md     # Section 7: gap analysis
│   ├── argm-naming.md           # Section 8: naming rationale
│   └── argm-references.md       # Section 10: references
├── assessment/
│   ├── assessment-template.md   # All assessment questions, grouped by level
│   ├── scoring-guide.md         # How to determine level
│   └── evidence-checklist.md    # Observable evidence per level
├── examples/
│   ├── level-1-claude-md.md     # Example CLAUDE.md at Level 1
│   ├── level-2-security.md      # Example security controls configuration
│   ├── level-3-directives.md    # Example value alignment / prime directives
│   ├── level-4-framework.md     # Example full pillar framework
│   └── level-5-monitoring.md    # Example governance drift detection config
├── .github/
│   ├── CONTRIBUTING.md
│   └── ISSUE_TEMPLATE/
│       ├── bug_report.md
│       └── feature_request.md
├── README.md
├── LICENCE
└── CHANGELOG.md
```

---

## Contributing

See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

---

## Licence

CC-BY-SA 4.0 — see [`LICENCE`](LICENCE).
