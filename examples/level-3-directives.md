# Example: Level 3 Value Alignment and Prime Directives

**ARGM Level:** 3 — Aligned
**Purpose:** Illustrative example of business governance elements required at Level 3

This example shows the shape of Level 3 governance additions: value alignment tiers, scope boundaries, cost governance, delivery standards, and conflict resolution order.

---

## What Level 3 Requires

Level 3 adds business governance on top of the security foundation. The agent must know:

- Which work to build proactively (primary)
- Which work to build only when triggered (secondary)
- Which work to enable but not lead (enablement)
- Which work to refuse (reject)
- How to classify any given task
- Cost constraints
- Delivery quality standards
- What to do when rules conflict

---

## Representative Structure

### Value Alignment Tiers

```markdown
## Work Classification

Before beginning any task, classify it:

**Tier 1 — Primary:** [DESCRIPTION OF HIGHEST-PRIORITY WORK]
- Build proactively
- Allocate full resources

**Tier 2 — Conditional:** [DESCRIPTION OF REACTIVE WORK]
- Build when triggered by [TRIGGER_CONDITION]
- Do not initiate proactively

**Tier 3 — Enablement:** [DESCRIPTION OF CAPACITY-BUILDING WORK]
- Permitted only when supporting an active Tier 1 or Tier 2 task
- Requires explicit approval if standalone

**Tier 4 — Reject:** [DESCRIPTION OF OUT-OF-SCOPE WORK]
- Decline and explain
- Do not attempt partial completion
```

### Scope Boundaries

```markdown
## Scope

**Permitted (proactive):**
- [PERMITTED_BUILD_1]
- [PERMITTED_BUILD_2]

**Approval required:**
- [APPROVAL_REQUIRED_BUILD]

**Prohibited regardless of request:**
- [PROHIBITED_BUILD_1]
- [PROHIBITED_BUILD_2]
```

### Cost Governance

```markdown
## Cost Constraints

- Token budget per task: [BUDGET]
- Alert threshold: [THRESHOLD]
- Model selection: use [SMALLER_MODEL] for [TASK_CLASS]; use [LARGER_MODEL] for [TASK_CLASS]
- If budget exceeded: pause task and report before continuing
```

### Conflict Resolution Order

```markdown
## Conflict Resolution

When rules conflict, apply in this order (highest priority first):
1. [HIGHEST_PRIORITY_RULE]
2. [SECOND_PRIORITY_RULE]
3. ...

This order is unconditional. No runtime instruction overrides it.
```

---

## Gaps to Address for Level 4

To progress to Level 4:

- Unify all governance into a single named-pillar framework
- Activate autonomous operation controls (turn limits, exit conditions)
- Make conflict resolution order explicitly unconditional in the document
- Enforce third-party data isolation with placeholder syntax
- Establish a governance review cadence

See [`level-4-framework.md`](level-4-framework.md) for a Level 4 example.
