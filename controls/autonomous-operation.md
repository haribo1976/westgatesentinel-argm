# Control — Autonomous Operation

## Purpose

Define the safety rules that apply when the agent operates without continuous human supervision — including overnight tasks, scheduled runs, and background workflows.

---

## Reasoning

Autonomous operation amplifies both capability and risk. A supervised agent that makes a mistake can be corrected immediately. An unsupervised agent that makes a mistake may complete many subsequent steps before the error is noticed, compounding the impact.

This control applies a conservative safety posture to autonomous operation. It does not prevent automation; it constrains what automation may do without human sign-off.

---

## Rules

### Dry-Run Default

1. Autonomous tasks must default to dry-run mode unless the operator has explicitly enabled live execution for that task.
2. Dry-run output must clearly indicate what would have been changed, created, or deleted.
3. The agent must not interpret absence of operator feedback as approval to proceed from dry-run to live execution.

### Destructive Operations

1. The agent must not perform any destructive operation autonomously. Destructive operations include but are not limited to:
   - Deleting files, records, or resources
   - Overwriting data without backup
   - Revoking access or permissions
   - Deprovisioning infrastructure
   - Sending external communications that cannot be recalled
2. If a workflow requires a destructive operation, the agent must pause, report the pending operation, and wait for explicit human approval before proceeding.

### Turn Limits

1. Autonomous sessions must not exceed the configured maximum turn limit without a human checkpoint.
2. If the turn limit is reached, the agent must save its state, report progress and any blockers, and suspend until resumed by a human operator.

### PII in Logs

1. Autonomous task logs must not contain PII (see Pillar 01).
2. Log entries must be sufficient for audit purposes without including personal data.

---

## Configurable Elements

```yaml
# autonomous-operation configuration
# Replace all [PLACEHOLDER] values before deployment.

# Maximum number of turns (agent-to-tool or agent-to-agent exchanges) in a single autonomous session.
# Example: 50
max_turns_per_session: "[MAX_TURNS]"

# Whether dry-run mode is the default for autonomous tasks.
# Strongly recommended: true
dry_run_default: true

# Operations that are unconditionally forbidden in autonomous mode.
# Extend this list with organisation-specific operations.
forbidden_operations:
  - "delete"
  - "drop"
  - "truncate"
  - "revoke"
  - "deprovision"
  - "send-email"
  - "send-message"
  - "[ADDITIONAL_FORBIDDEN_OPERATION]"

# Whether the agent must checkpoint progress at the turn limit or may continue.
# Options: "checkpoint" (pause and report), "abort" (terminate session)
turn_limit_behaviour: "checkpoint"
```

---

## Deployment Example

```yaml
max_turns_per_session: 50
dry_run_default: true
forbidden_operations:
  - "delete"
  - "drop"
  - "truncate"
  - "revoke"
  - "deprovision"
  - "send-email"
  - "send-message"
turn_limit_behaviour: "checkpoint"
```
