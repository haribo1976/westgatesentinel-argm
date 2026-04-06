# Example: Level 4 — Full Governed Framework Structure

**Version:** 1.1
**Licence:** CC-BY-SA 4.0

This stub illustrates the unified governance framework required at ARGM Level 4. At this level all seven prime directives are active, integrated, and enforced by technical controls rather than model compliance alone.

---

## Framework Document Set

A Level 4 organisation maintains one of the following structures:

**Option A — Single unified document:**
- `CLAUDE.md` or `AGENTS.md` encoding all D0–D6 directives, conflict resolution order, autonomous operation controls, and third-party isolation rules

**Option B — Modular document set:**
- `governance/directives.md` — D0–D6 definitions and conflict resolution order
- `governance/autonomous-ops.md` — turn limits, exit conditions, overnight rules, logging requirements
- `governance/isolation.md` — third-party data isolation, placeholder syntax, prohibited patterns

## D2 — Autonomous Operation Controls

- **Turn limit:** Maximum 15 turns per task for overnight/unattended operation
- **Exit condition:** If turn limit reached, agent writes summary and halts without further action
- **Dry-run default:** All scheduled operations default to dry-run. Live execution requires explicit flag
- **Destructive operations:** Prohibited without human scheduling and explicit logging
- **External calls:** No API calls or notifications without explicit authorisation flag
- **Logging:** Every write operation logged: timestamp, operation type, record ID, outcome, status code

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

---

*This stub provides structure. Populate with your organisation's actual controls and review records.*
