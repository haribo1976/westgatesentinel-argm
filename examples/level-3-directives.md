# Example: Level 3 — Controlled: Autonomous Operation Configuration

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

This stub illustrates the autonomous operation controls required at ARGM Level 3. At this level D2 (Autonomous Operation) is enforced alongside the existing D0 and D1 controls from Level 2.

---

## D2 — Autonomous Operation Controls

### Turn Limits

- **Attended operation:** No hard limit, but agent should summarise progress every 20 turns
- **Unattended/overnight:** Maximum 15 turns per task. Agent writes summary and halts at limit.
- **Scheduled batch:** Maximum 50 turns with checkpoint every 10 turns

### Dry-Run Default

All write operations default to dry-run mode. To execute live:
- Attended: explicit user confirmation per operation or `--live` flag
- Unattended: task must be explicitly scheduled with live execution flag in the task definition

Dry-run output must be reviewed before any live execution of the same operation.

### Destructive Operation Controls

The following operations are **prohibited** without explicit human authorisation:
- File or record deletion
- Infrastructure teardown (resource groups, clusters, databases)
- Permission or role removal
- External API calls that modify state
- Email, notification, or message sends

Each authorised destructive operation must be logged: timestamp, operation, target, authorising individual, outcome.

### Exit Conditions

When any limit is reached, the agent must:
1. Stop executing new operations immediately
2. Write a summary of completed work and remaining tasks
3. Save state sufficient to resume (if applicable)
4. Exit cleanly with status code 0

The agent must not attempt to "finish one more thing" or exceed the limit by even one operation.

### Write Logging

Every write operation logged with:
- Timestamp (ISO 8601)
- Operation type (create, update, delete, execute)
- Target identifier (file path, record ID, resource name)
- Outcome (success, failure, dry-run)
- Status code or error code (if applicable)

**No PII in logs.** Log operation name and record count, not record content.

---

*This stub provides structure. Adapt turn limits and exit conditions to your operational context.*
