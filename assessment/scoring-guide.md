# ARGM Scoring Guide

**Version:** 1.1
**Licence:** CC-BY-SA 4.0

---

## Scoring Methodology

ARGM uses evidence-based assessment. Maturity levels are assigned based on observable evidence, not self-reported capability.

### Per-Question Scoring

Each assessment question is scored 0–2:

| Score | Meaning |
|-------|---------|
| 0 | No evidence. Practice does not exist or assessor cannot verify existence. |
| 1 | Partial evidence. Practice exists but is incomplete, inconsistently applied, or applies to only one agent. |
| 2 | Full evidence. Practice exists, is consistently applied, and assessor can verify with artefacts. |

### Level Achievement Threshold

A level is achieved when:
- All five questions score **≥1** (no zero scores)
- At least three questions score **2**

Minimum achievable score per level: **7/10**

Levels are cumulative. Level 3 cannot be awarded unless Levels 1 and 2 are also achieved.

### Level 0 — Baseline Only

Level 0 is not a target level. It describes the absence of governance. Document Level 0 evidence to establish baseline, then proceed to Level 1 assessment.

---

## Determining Current Level

Assess from Level 1 upward. Stop when a level is not achieved. The current ARGM level is the highest level where all threshold conditions are met and all preceding levels are also achieved.

**Example:** Organisation achieves Level 1 (8/10) and Level 2 (7/10) but scores 5/10 on Level 3. Current ARGM level: **2 — Secured**.

---

## Evidence Standards

### What Counts as Evidence

- Artefacts assessor can view: governance files, CI/CD configurations, scan logs, cost reports, health dashboards
- Demonstrated behaviours: assessor observes agent completing a task under governance controls
- Auditable records: git history, access logs, credential rotation records, review sign-offs

### What Does Not Count as Evidence

- Claims without artefacts ("we do this, we just haven't documented it")
- Documentation that exists but is not operationally applied
- Controls applied to the primary agent but not verified across all agents

---

## Common Scoring Notes

**Level 1 — Instructed**
- Governance document exists but has not been reviewed in >6 months: score Q1 as 1, not 2
- Governance document exists but D0 (Data Protection) is not explicitly unconditional: score Q3 as 1

**Level 2 — Secured**
- Pre-commit scanning configured but never triggered in >90 days: score Q1 as 1
- Controls exist for primary agent only: cap all questions at 1

**Level 3 — Aligned**
- Conflict resolution order documented but exceptions permitted at runtime: score Q4 as 1, not 2
- Cost governance tracked but no evidence of a cost-influenced decision: score Q2 as 1

**Level 4 — Governed**
- Governance framework documented but review cadence not evidenced: score Q5 as 0 or 1
- Third-party isolation enforced in repositories but not in logs: score Q3 as 1

**Level 5 — Autonomous**
- Drift detection configured but never triggered and no baseline established: score Q1 as 1
- Health reports exist but require manual trigger: score Q3 as 1, not 2

---

## Reporting

Assessment reports should include:

1. **Assessment date and assessor identity**
2. **Per-level score table** (scores for all five questions per level)
3. **Current ARGM level** with rationale
4. **Key gaps** — specific evidence items missing for the next level
5. **Recommended actions** — ordered by priority (highest impact gaps first)
6. **Next assessment date** — recommended within 90 days when progressing levels
