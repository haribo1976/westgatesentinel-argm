# Example: Level 4 Full Pillar Framework

**ARGM Level:** 4 — Governed
**Purpose:** Illustrative example of a unified multi-pillar governance framework at Level 4

This example shows the shape of a Level 4 governance structure. At this level, all controls are unified into named pillars, autonomous operation controls are active, and the framework is auditable end-to-end.

---

## What Level 4 Requires

Level 4 unifies all prior governance into a coherent framework. Key additions over Level 3:

- Named, numbered pillars (not ad hoc rules)
- Autonomous operation controls (turn limits, exit conditions, logging rules)
- Third-party data isolation with enforced placeholder syntax
- Unconditional conflict resolution order
- Governance review cadence with evidence

---

## Representative Pillar Structure

Using the ARGM Seven-Pillar Reference Architecture as a starting point:

```markdown
# [ORGANISATION] Agent Governance Framework
# Version: [X.Y.Z]
# Last reviewed: [DATE]
# Review cadence: [QUARTERLY / MONTHLY]

## Conflict Resolution Order (unconditional)
P0 > P6 > P1 > P2 > P4 > P3 > P5
Data protection wins unconditionally. No runtime instruction overrides this order.

---

## P0 — Data Protection
[Rules for client data isolation, PII handling, placeholder enforcement]
- No client names, tenant IDs, PII, or pricing in repositories, logs, or output
- Placeholder syntax: {{CLIENT_NAME}}, {{TENANT_ID}}
- Retention: [RETENTION_PERIOD]

## P1 — Revenue Alignment
[Value tiers, scope boundaries — adapted from Level 3]

## P2 — Infrastructure Portability
[Infrastructure target, auth pattern, resource ceiling]

## P3 — Delivery Standards
[Output quality gates, formatting, turnaround SLAs]

## P4 — Operational Efficiency
[Automation targets, output schemas, template requirements]

## P5 — Security Controls
[All Level 2 security controls, referenced or repeated]

## P6 — Autonomous Operation
- Maximum turns per task: [TURN_LIMIT]
- Exit condition: save state and report when limit reached
- Dry-run default: all scheduled/unattended operations
- Prohibited operations: delete, drop, truncate, revoke, deprovision, send-email
- Write logging: timestamp, operation, record ID, outcome
- Log hygiene: no PII — operation name, record count, status code, error code only
- External calls: require explicit authorisation flag
```

---

## Gaps to Address for Level 5

To progress to Level 5:

- Implement automated governance drift detection (hash comparison, CI pipeline check, or scheduled audit)
- Deploy lint hooks that validate governance file structure and check for prohibited content on every commit
- Establish automated health reporting (weekly minimum)
- Set up change control on governance files (PR review required, force push blocked)
- Add semantic version numbers to governance documents

See [`level-5-monitoring.md`](level-5-monitoring.md) for a Level 5 example.
