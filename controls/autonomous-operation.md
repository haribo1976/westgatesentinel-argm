# Control — Autonomous Operation

**Safety rules for unattended and scheduled execution.**

---

## Purpose

Define the safety constraints that apply whenever the agent operates without real-time human oversight — including overnight tasks, scheduled runs, and background workflows.

---

## Why These Controls Exist

Autonomous operation amplifies both capability and risk. A supervised agent that makes a mistake can be corrected immediately. An unsupervised agent that makes a mistake may complete many subsequent steps before the error is noticed, compounding the impact.

These controls apply a conservative safety posture. They do not prevent automation — they constrain what automation may do without human sign-off, and they make the blast radius of a misconfigured run recoverable.

---

## Controls

### Turn Limit

Every autonomous run has a maximum turn count. The agent exits cleanly when the limit is reached rather than continuing indefinitely. On exit, the agent saves its state and produces a progress report.

### Safe-Run Default

All scheduled and unattended runs operate in a non-destructive mode unless explicitly promoted to live execution. A misconfigured safe run produces a report, not irreversible changes. The promotion from safe-run to live must be an explicit, auditable operator action — not an assumption or a default.

### Destructive Operation Prohibition

No record deletion, no irreversible modifications, no destructive operations during unattended runs without explicit authorisation at run time. If a workflow reaches a step that requires a destructive operation, it must pause, report the pending operation, and wait for explicit human approval before proceeding.

Destructive operations include but are not limited to:
- Deleting files, records, or resources
- Overwriting data without a backup
- Revoking access or permissions
- Deprovisioning infrastructure
- Sending external communications that cannot be recalled

### Write Logging

Every write operation during an autonomous run is logged with: timestamp, operation type, record identifier, and outcome. Write logs are retained for the configured period and are excluded from sensitive data handling (they contain only operational metadata, not the data being written).

### Sensitive Data Exclusion from Logs

Operational logs contain only metadata. No sensitive or personally identifiable information appears in process output or log files. See Pillar 01 for the full data sovereignty rules that apply to log content.

### External Call Gating

Calls to external systems during unattended runs require an explicit flag. Silent outbound calls during overnight or scheduled execution are prohibited by default. If a workflow needs to make external calls, this must be declared at run configuration time.

---

## Configurable Elements

```yaml
# autonomous-operation configuration
# Replace all [PLACEHOLDER] values before deployment.

# Maximum number of turns in a single autonomous session.
max_turns_per_session: "[MAX_TURNS]"

# Behaviour when turn limit is reached.
# Options: "checkpoint" (save state and pause), "abort" (terminate session)
turn_limit_behaviour: "checkpoint"

# Whether safe-run mode is the default for autonomous tasks.
# Strongly recommended: true
safe_run_default: true

# Operations that are unconditionally prohibited in autonomous mode.
# Extend with organisation-specific operations.
prohibited_operations:
  - "delete"
  - "drop"
  - "truncate"
  - "revoke"
  - "deprovision"
  - "send-email"
  - "send-message"
  - "[ADDITIONAL_PROHIBITED_OPERATION]"

# How long write logs are retained.
# Format: ISO 8601 duration.
write_log_retention: "[WRITE_LOG_RETENTION_PERIOD]"

# Whether external calls require an explicit flag.
external_call_gating_enabled: true
```

---

## Deployment Example

```yaml
max_turns_per_session: 50
turn_limit_behaviour: "checkpoint"
safe_run_default: true
prohibited_operations:
  - "delete"
  - "drop"
  - "truncate"
  - "revoke"
  - "deprovision"
  - "send-email"
  - "send-message"
write_log_retention: "P30D"
external_call_gating_enabled: true
```
