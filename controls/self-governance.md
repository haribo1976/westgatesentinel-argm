# Control — Self-Governance

## Purpose

Define how the Agent Runtime Framework itself is amended, reviewed, and versioned. The framework must not be a static document; it must evolve as the organisation's needs change. But it must not be amended casually or without accountability.

---

## Reasoning

A governance framework that cannot be updated becomes irrelevant. A governance framework that can be updated without process becomes a liability. Self-governance balances these pressures by requiring all changes to follow a documented process, be reviewed by appropriate roles, and be recorded in the changelog.

---

## Amendment Process

### Who May Propose Amendments

Any contributor may propose an amendment by opening an issue or a pull request against the framework repository. The proposal must describe:

1. Which pillar or control is being amended
2. What the current text says
3. What the proposed text says
4. Why the change is needed
5. Any risks introduced by the change

### Review Requirements

Amendments must be reviewed and approved by at least one person in each of the following roles before merging:

- A person with operational authority over the agent's deployment (e.g. the operator or team lead)
- A person with security responsibility (e.g. a security lead or equivalent)

If the organisation does not have distinct people in these roles, the same person may fulfil both, but this must be documented in the review record.

### Prohibited Amendments

The following changes are not permitted via the standard amendment process:

- Removing or weakening universal hard boundaries (Pillar 02)
- Disabling security injection defence (Pillar 07)
- Removing the requirement for dry-run defaults in autonomous operation

These changes require an extraordinary review process defined by the organisation's governance authority.

### Changelog Requirements

Every merged amendment must produce a changelog entry in `CHANGELOG.md` that includes:

- The version number (following semantic versioning)
- The date of the amendment
- A description of what changed and why

---

## Review Cadence

The framework must be reviewed in full at least once per year. The review must assess:

- Whether pillar configurations reflect current organisational needs
- Whether new threat patterns require updates to Pillar 07
- Whether the hard boundaries list remains complete
- Whether the controls remain appropriate for the scale of autonomous operation

Review outcomes must be documented in the changelog, even if no changes are made.

---

## Configurable Elements

```yaml
# self-governance configuration
# Replace all [PLACEHOLDER] values before deployment.

# Roles required to approve amendments.
amendment_approvers:
  - role: "[OPERATIONAL_APPROVER_ROLE]"
    description: "[OPERATIONAL_APPROVER_DESCRIPTION]"
  - role: "[SECURITY_APPROVER_ROLE]"
    description: "[SECURITY_APPROVER_DESCRIPTION]"

# Minimum review frequency (ISO 8601 duration).
review_cadence: "P1Y"

# Whether amendments to universal hard boundaries require extraordinary review.
extraordinary_review_required_for_universal_boundaries: true
```
