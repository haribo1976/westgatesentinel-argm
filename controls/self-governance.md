# Control — Self-Governance

**The framework monitors itself.**

---

## Purpose

Define how the Agent Runtime Framework is amended, reviewed, and versioned — and how it monitors its own health over time. The framework must evolve as the organisation's needs change, but must not be amended casually or without accountability. Governance frameworks that are never audited drift.

---

## Change Hook

A change hook fires on every modification to a governance file. It checks for:

- Pillar duplication (the same rule appearing in more than one pillar)
- Inline rule insertion outside the defined pillar structure
- Size thresholds that indicate governance drift (a pillar growing beyond its intended scope)

Change hook triggers must be resolved before the modification is committed. If the hook cannot run automatically in the deployment environment, it must be run manually as part of the review process.

---

## Scheduled Audit

A scheduled audit runs at the configured cadence, producing a per-file health status across all governance files:

| Status | Meaning |
|--------|---------|
| Healthy | File conforms to structure, no drift indicators, last reviewed within cadence |
| Needs attention | Minor drift detected or review overdue |
| Unhealthy | Structural violation, duplication, or significant drift |

Owned governance content and third-party tooling configuration are reported separately to preserve signal value. When a violation fires, it is always actionable — never a false positive from a dependency the organisation does not control.

---

## Amendment Process

### Who May Propose Amendments

Any contributor may propose an amendment by opening an issue or pull request. The proposal must describe:

1. Which pillar or control is being amended
2. What the current text says
3. What the proposed text says
4. Why the change is needed
5. Any risks introduced by the change

### Review Requirements

Amendments require review and approval by at least one person in each of:

- A person with operational authority over the agent's deployment
- A person with security responsibility

If the organisation does not have distinct people in these roles, the same person may fulfil both, documented in the review record.

### Prohibited Amendments

The following cannot be changed via the standard process:

- Removing or weakening the unconditional status of Pillar 01 (Data Sovereignty)
- Removing items from the universal hard boundaries (Pillar 02)
- Disabling the security injection defence (Pillar 07)
- Removing the safe-run default from autonomous operation controls

These require an extraordinary review process defined by the organisation's governance authority.

### Changelog Requirements

Every merged amendment must produce a changelog entry with:

- Version number (semantic versioning)
- Date
- Description of what changed and why

---

## Configurable Elements

```yaml
# self-governance configuration
# Replace all [PLACEHOLDER] values before deployment.

# Roles required to approve amendments.
amendment_approvers:
  - role: "[OPERATIONAL_APPROVER_ROLE]"
  - role: "[SECURITY_APPROVER_ROLE]"

# Scheduled audit cadence.
# Format: ISO 8601 duration. Example: P1M (monthly), P3M (quarterly), P1Y (annually)
audit_cadence: "[AUDIT_CADENCE]"

# Change hook: whether it runs automatically or manually.
# Options: "automatic", "manual"
change_hook_mode: "[CHANGE_HOOK_MODE]"

# Size thresholds for drift detection (approximate line counts).
drift_thresholds:
  pillar_max_lines: "[MAX_LINES_PER_PILLAR]"
  control_max_lines: "[MAX_LINES_PER_CONTROL]"
```
