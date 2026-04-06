# Example: Level 4 — Aligned: Business Directives and Cost Governance

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

This stub illustrates the business directive activation and cost governance controls required at ARGM Level 4.

---

## Two-Tier Directive Architecture

### Tier 1 — Safety (unconditional, from Level 2)

| Directive | Status |
|-----------|--------|
| D0 Data Protection | Active — unconditional |
| D1 Security Controls | Active — unconditional |
| D2 Autonomous Operation | Active — unconditional |

### Tier 2 — Business (configurable, activated at Level 4)

| Directive | Status | Order Position |
|-----------|--------|---------------|
| D3 Value Alignment | Active | 1st (default) |
| D4 Infrastructure Governance | Active | 2nd (default) |
| D5 Operational Efficiency | Active | 3rd (default) |
| D6 Delivery Standards | Active | 4th (default) |

**This organisation's Tier 2 order:** D3 > D4 > D5 > D6
**Rationale:** Professional services consultancy — client-facing revenue work takes precedence.

## D3 — Value Alignment: Classification Mechanism

### Decision Flowchart

1. Is this task within the defined service scope? → No → **Reject** (unless approval obtained)
2. Does it directly serve a client deliverable or revenue outcome? → Yes → **Primary**
3. Does it support primary work (internal tooling, documentation, team enablement)? → Yes → **Secondary**
4. Does it maintain governance, security, or infrastructure? → Yes → **Enablement**
5. None of the above → **Requires approval** before starting

### Sector-Specific Terminology

| Sector | "Primary" means | "Revenue outcome" replaced by |
|--------|----------------|-------------------------------|
| Consultancy | Client deliverable | Billable outcome |
| Healthcare | Patient-facing system | Patient safety outcome |
| Public sector | Citizen service | Mission outcome |
| Open-source | Community benefit | Adoption/contribution outcome |

## Cost Governance Controls

### Model Selection Policy

| Task Type | Recommended Model Tier | Rationale |
|-----------|----------------------|-----------|
| Quick lookup, formatting, simple generation | Small/fast (e.g., Haiku-class) | Low cost, sufficient capability |
| Standard implementation, analysis, review | Mid-tier (e.g., Sonnet-class) | Balance of capability and cost |
| Architecture, deep analysis, security review | Large/capable (e.g., Opus-class) | Justifies cost for complex reasoning |

### Budget Allocation

- **Per-agent:** Monthly token budget per agent instance
- **Per-project:** Budget allocated to each active project
- **Escalation thresholds:** Alert at 50%, warning at 80%, hard stop at 100% unless override approved

### Cost Attribution

Each agent task tagged with:
- Value tier (Primary / Secondary / Enablement)
- Project code
- Model used
- Token count (input + output)

Monthly cost review: trend analysis, cost-per-deliverable, budget vs actual.

## Scope Boundaries

**Permitted without approval:** Tasks classified Primary or Secondary within defined service scope.

**Requires approval:** Tasks not previously categorised, estimated at >4 hours agent time, or outside defined service scope.

**Prohibited:** Tasks classified Reject. Destructive operations without authorisation. Work outside organisational mandate.

---

*Adapt value tiers, model selection policy, and budget thresholds to your organisation's context.*
