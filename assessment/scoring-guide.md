# ARGM Scoring Guide

**Version:** 2.0
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

### Critical Failures

Certain questions are marked **[CRITICAL]**. A score of 0 on a critical question fails the level regardless of the total score.

Critical questions by level:

| Level | Critical Requirement |
|-------|----------------------|
| 1+ | D0 data protection acknowledgment present and unconditional |
| 2+ | Pre-commit scanning operational |
| 3+ | Turn limits configured and enforced |
| 5+ | Break-glass logging mechanism operational |
| 6 | Drift detection baseline established |

A critical failure is recorded in the assessment report alongside the standard score. The level is not achieved even if the total score would otherwise meet the threshold.

### Level Achievement Threshold

A level is achieved when:

- All questions score **≥1** (no zero scores)
- At least three questions score **2**
- No critical question scores **0**

Minimum achievable score per level: **7/10**

**Threshold justification:** The 7/10 threshold requires demonstrated competence across all assessment areas (no zeros) with majority full evidence (three 2s). A threshold of 6/10 would permit too many partial implementations in non-critical areas. A threshold of 8/10 would exclude organisations with legitimate partial progress. The critical-failure mechanism addresses the weakness that the threshold alone does not distinguish between critical and non-critical gaps.

### Levels are Cumulative

Levels 0–6 are cumulative. Level 3 cannot be awarded unless Levels 1 and 2 are also achieved. Assessment proceeds from Level 1 upward; stop when a level is not achieved.

### Level 0 — Baseline Only

Level 0 is not a target level. It describes the absence of governance. Document Level 0 evidence to establish baseline, then proceed to Level 1 assessment.

---

## Determining Current Level

Assess from Level 1 upward. Stop when a level is not achieved. The current ARGM level is the highest level where all threshold conditions are met, no critical failures exist, and all preceding levels are also achieved.

**Example:** Organisation achieves Level 1 (8/10) and Level 2 (7/10) but scores 5/10 on Level 3. Current ARGM level: **2 — Secured**.

**Example with critical failure:** Organisation scores 9/10 on Level 2 but pre-commit scanning is not operational (critical failure). Current ARGM level: **1 — Instructed**, regardless of the total score.

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

### Genuineness of Evidence

Assessors should verify that evidence is genuine and operationally applied, not staged for assessment. A pre-commit hook configured but never triggered does not constitute full evidence of pre-commit scanning. A cost governance dashboard that has never influenced a decision does not constitute full evidence of cost governance.

---

## Inter-Rater Reliability

For assessments with consequential outcomes — compliance reporting, client-facing maturity claims, procurement qualification — the following process applies:

1. Two assessors independently score the same organisation.
2. Compare results per question and document any divergence.
3. If divergence exceeds 1 point on any single question, reconcile with evidence discussion before finalising.
4. If divergence exceeds 2 points on any level total, involve a third assessor or governance owner.
5. Document reconciliation rationale in the assessment report.

For internal self-assessment, inter-rater reliability is recommended but not required.

---

## Calibration Exercise

Organisations conducting their first ARGM assessment should calibrate by scoring the Level 1 example (`examples/level-1-claude-md.md`) against the Level 1 assessment questions before assessing their own environment. This establishes shared understanding of the 0-1-2 scale and reduces assessor drift on subsequent questions.

---

## Common Scoring Notes

**Level 1 — Instructed**
- Governance document exists but has not been reviewed in >6 months: score Q1 as 1, not 2
- Governance document exists but D0 (Data Protection) is not explicitly unconditional: score Q3 as 1
- D0 acknowledgment absent entirely: critical failure — level not achieved

**Level 2 — Secured**
- Pre-commit scanning configured but never triggered in >90 days: score Q1 as 1
- Pre-commit scanning not operational: critical failure — level not achieved
- Controls exist for primary agent only: cap all questions at 1

**Level 3 — Controlled**
- Turn limits configured but never tested in unattended operation: score Q2 as 1
- Turn limits not configured or not enforced: critical failure — level not achieved
- Conflict resolution order documented but exceptions permitted at runtime: score Q4 as 1, not 2

**Level 4 — Aligned**
- Cost governance tracked but no model selection policy: score Q2 as 1
- Cost governance tracked but no evidence of a cost-influenced decision: score Q2 as 1

**Level 5 — Governed**
- Break-glass mechanism exists but never tested or exercised: score Q4 as 1
- Break-glass logging mechanism absent entirely: critical failure — level not achieved
- Health reports exist but require manual trigger: score Q3 as 1, not 2

**Level 6 — Autonomous**
- Drift detection configured but baseline never updated since initial setup: score Q1 as 1
- Drift detection baseline not established: critical failure — level not achieved

---

## Reporting

Assessment reports should include:

1. **Assessment date and assessor identity** (including both assessors if inter-rater process was followed)
2. **Per-level score table** (scores for all questions per level, Levels 0–6)
3. **Critical failures** — listed separately with the specific question and level affected
4. **Current ARGM level** with rationale
5. **Key gaps** — specific evidence items missing for the next level
6. **Recommended actions** — ordered by priority (critical failures first, then highest impact gaps)
7. **Inter-rater reconciliation notes** (if applicable)
8. **Next assessment date** — recommended within 90 days when progressing levels
