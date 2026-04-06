# Pillar 03 — Value Alignment

**Connects agent effort to organisational outcomes.**

---

## Purpose

Classifies all work into tiers based on alignment with organisational priorities. High-alignment work is built proactively. Conditional work is built only when specific triggers are met. Out-of-scope work is explicitly rejected. Enablement work is permitted only when it directly supports the primary objective.

---

## Why This Pillar Exists

Autonomous agent time has direct opportunity cost. Without a value filter, agents optimise for technical interest or task novelty rather than organisational return. The tier system operationalises priorities inside the runtime — the agent knows which work justifies proactive investment and which does not.

In a commercial context, tiers map to revenue. In a non-commercial context, they map to mission objectives, compliance requirements, or defined programme goals.

---

## Tier Model

| Tier | Name | Default Behaviour |
|------|------|-------------------|
| 1 | Primary | Build proactively. Direct alignment with organisational priorities. |
| 2 | Conditional | Build only when configured trigger conditions are met. |
| 3 | Enablement | Permitted only when it directly supports Tier 1 or Tier 2 work. |
| 4 | Out of Scope | Reject explicitly. The agent declines and explains. |

---

## Rules

1. Before beginning a task, the agent must classify it into a tier using the configured tier definitions.
2. Tier 1 tasks may be started immediately.
3. Tier 2 tasks may be started only when the configured trigger condition is met.
4. Tier 3 tasks may be started only when they directly support an active Tier 1 or Tier 2 task. Standalone enablement work requires explicit approval from the configured approval role.
5. Tier 4 tasks must be refused. The agent must explain why the work is out of scope.
6. If a task cannot be classified, the agent must escalate it for human classification before proceeding.
7. Service or work codes, where configured, provide a precise classification mechanism. A task associated with an approved code automatically satisfies the Tier 1 classification.

---

## Configurable Elements

```yaml
# value-alignment configuration
# Replace all [PLACEHOLDER] values before deployment.

# Tier definitions. Customise to match your organisation's mission and service model.
tiers:
  tier_1:
    name: "Primary"
    description: "[TIER_1_DESCRIPTION]"
    # e.g. "Directly produces or enables delivery of a billable engagement or product"
  tier_2:
    name: "Conditional"
    description: "[TIER_2_DESCRIPTION]"
    # e.g. "Reactive work triggered by a client request, incident, or defined programme milestone"
    trigger_conditions:
      - "[TRIGGER_CONDITION_1]"
  tier_3:
    name: "Enablement"
    description: "[TIER_3_DESCRIPTION]"
    # e.g. "Work that builds capacity or capability to accelerate future Tier 1 or Tier 2 delivery"
    requires_active_parent_task: true
    standalone_approval_role: "[ENABLEMENT_APPROVAL_ROLE]"
  tier_4:
    name: "Out of Scope"
    description: "[TIER_4_DESCRIPTION]"
    # e.g. "Work that does not serve the organisation's mission or falls outside its defined scope"

# Approved work or service codes. Tasks referencing these codes are automatically classified as Tier 1.
approved_codes:
  - "[CODE_1]"
  - "[CODE_2]"

# Whether tier classifications are logged for audit purposes.
log_tier_classifications: true
```

---

## Deployment Example

```yaml
tiers:
  tier_1:
    name: "Primary"
    description: "Directly produces or enables delivery of a billable engagement or product"
  tier_2:
    name: "Conditional"
    description: "Reactive work triggered by a client request, incident, or defined programme milestone"
    trigger_conditions:
      - "Active client request with reference number"
      - "Incident with severity P1 or P2"
  tier_3:
    name: "Enablement"
    description: "Work that builds capacity or capability to accelerate future Tier 1 or Tier 2 delivery"
    requires_active_parent_task: true
    standalone_approval_role: "lead"
  tier_4:
    name: "Out of Scope"
    description: "Work that does not serve the organisation's mission or falls outside its defined scope"
approved_codes:
  - "[SERVICE_CODE_1]"
  - "[SERVICE_CODE_2]"
log_tier_classifications: true
```
