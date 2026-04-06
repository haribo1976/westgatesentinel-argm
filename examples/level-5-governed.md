# Example: Level 5 — Governed: Full Framework Structure

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

This stub illustrates the unified governance framework required at ARGM Level 5. At this level all seven directives (D0-D6) are active, integrated, and enforced by technical controls rather than model compliance alone.

---

## Framework Document Set

A Level 5 organisation maintains one of the following structures:

**Option A — Single unified document:**
- `CLAUDE.md` or `AGENTS.md` encoding all D0-D6 directives, two-tier architecture, autonomous operation controls, and third-party isolation rules

**Option B — Modular document set:**
- `governance/directives.md` — D0-D6 definitions, two-tier architecture, and conflict resolution order
- `governance/autonomous-ops.md` — turn limits, exit conditions, overnight rules, logging requirements
- `governance/isolation.md` — third-party data isolation, placeholder syntax, prohibited patterns

## Two-Tier Directive Summary

### Tier 1 — Safety (unconditional)

| Directive | Name | Enforcement |
|-----------|------|-------------|
| D0 | Data Protection | Pre-commit scan, log sanitisation, template system |
| D1 | Security Controls | CI pipeline, branch protection, rate limiting |
| D2 | Autonomous Operation | Turn limits, dry-run default, exit conditions |

### Tier 2 — Business (configurable order)

| Directive | Name | Enforcement |
|-----------|------|-------------|
| D3 | Value Alignment | Task classification gates, scope boundaries |
| D4 | Infrastructure Governance | Cost controls, model selection policy |
| D5 | Operational Efficiency | Performance monitoring, resource budgets |
| D6 | Delivery Standards | Quality gates, review requirements |

## D0 — Third-party Isolation

No client names, tenant IDs, PII, or commercial pricing in:
- Repository files (enforced by pre-commit scan)
- Agent logs or stdout (enforced by log sanitisation)
- Agent output documents (enforced by template system)

Placeholder syntax: `{{CLIENT_NAME}}`, `{{TENANT_ID}}`, `{{CONTACT_EMAIL}}`, `{{PRICE}}`

## Governance Review Cadence

- Quarterly scheduled review (minimum)
- Review documented: date, changes made, rationale, approver
- Review record maintained in `CHANGELOG.md` or equivalent

## Cross-agent Application

This framework applies to all agents in the environment. New agents are not deployed until governance review confirms the framework applies to their scope and access level.

## Break-Glass Exception Mechanism (Tier 2 Only)

When an urgent operational need requires temporary deviation from a Tier 2 directive:

1. **Named individual:** [Full name of accountable person]
2. **Directive overridden:** [e.g., D6 Delivery Standards — raw output permitted for emergency client response]
3. **Justification:** [Written before activation, not retrospective]
4. **Time bound:** [Start datetime] to [End datetime, max 72 hours]
5. **Log entry:** Immutable record in governance log
6. **Post-incident review:** Scheduled within 5 business days of expiry

**Tier 1 directives (D0, D1, D2) cannot be overridden by break-glass.** Any request to override Tier 1 is a governance failure requiring escalation, not an exception.

---

*This stub provides structure. Populate with your organisation's actual controls and review records.*
