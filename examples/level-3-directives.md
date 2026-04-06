# Example: Level 3 — Prime Directives and Value Alignment

**Version:** 1.1
**Licence:** CC-BY-SA 4.0

This stub illustrates the directive architecture and value alignment framework required at ARGM Level 3. Replace with your organisation's actual directives.

---

## Conflict Resolution Order (Unconditional)

**D0 > D1 > D2 > D3 > D4 > D5 > D6**

When any two directives conflict, the lower number wins without exception. No runtime override is permitted.

## Directive Summary

| Directive | Name | Status at Level 3 |
|-----------|------|-------------------|
| D0 | Data Protection | Active — unconditional |
| D1 | Security Controls | Active |
| D2 | Autonomous Operation | Active (dry-run, no destructive ops) |
| D3 | Revenue Alignment | Active |
| D4 | Infrastructure Portability | Active |
| D5 | Operational Efficiency | Active |
| D6 | Delivery Standards | Active |

## D3 — Revenue Alignment: Value Tiers

| Tier | Description | Examples |
|------|-------------|---------|
| Primary | Direct revenue impact | Client deliverables, billable automation, production deployments |
| Secondary | Indirect revenue support | Internal tooling, team productivity, documentation |
| Enablement | Infrastructure and governance | Security controls, monitoring, CI/CD |
| Reject | Outside mandate | Speculative builds without client mandate, non-billable scope creep |

## Scope Boundaries

**Permitted without approval:**
- Tasks classified as Primary or Secondary
- Enablement work within established governance

**Requires approval before starting:**
- Tasks not previously categorised
- Any build estimated at >4 hours of agent time

**Always prohibited:**
- Builds classified as Reject
- Destructive operations without explicit instruction and logging

## D2 — Autonomous Operation: Dry-Run Default

All write operations default to dry-run mode. To execute live, the task must be explicitly scheduled with the `--live` flag or equivalent mechanism. Dry-run output must be reviewed before live execution.

---

*This stub provides structure. Populate with your organisation's actual values and boundaries.*
