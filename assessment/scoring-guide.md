# ARGM Scoring Guide

How to determine an organisation's ARGM maturity level.

---

## The Core Rule

**To achieve Level N, an organisation must:**

1. Demonstrate ALL observable evidence items for Level N
2. Have demonstrated all observable evidence for every level below N (cumulative)
3. Meet all progression criteria from Level N-1 (the criteria that enabled the move from N-1 to N)

There is no partial credit. A level is either met or not met. The assessed level is the highest level for which all evidence is demonstrable.

---

## Why Cumulative?

Each level builds on the previous. An organisation that has Level 3 value alignment but has lost its Level 2 security controls is not at Level 3 — it has a security regression that must be resolved before the Level 3 claim is valid.

This is consistent with CMMI's treatment of maturity levels: you cannot skip levels, and you cannot claim a higher level while lower-level practices have eroded.

---

## Scoring Process

### Step 1 — Start at Level 0

Check for Level 0 conditions (the observable evidence checklist). If any Level 0 conditions are present, the organisation is at Level 0. Stop here and record findings.

### Step 2 — Work upward level by level

For each level from 1 to 5:

1. Review the observable evidence checklist for that level
2. For each evidence item, ask for a demonstration — not a description
3. Mark each item as: **Demonstrated** / **Partial** / **Not present**
4. If all items are **Demonstrated**: the level is met; proceed to the next level
5. If any item is **Partial** or **Not present**: this is the ceiling; record gaps

### Step 3 — Record the assessed level

The assessed level is the highest level where all evidence items are **Demonstrated** and all lower levels are intact.

### Step 4 — Document gaps for the next level

Identify which evidence items are missing or partial for the next level. These become the improvement roadmap.

---

## Evidence Standards

**Demonstrated** means: shown, not told. The assessor has seen the artefact, the configuration, the log, the report, the hook in action.

**Partial** means: exists but incomplete. For example, pre-commit scanning is configured but only covers some repositories, or branch protection is in place but not on all protected branches.

**Not present** means: no evidence exists.

---

## Common Scoring Pitfalls

### The Documentation Trap
A governance document exists does not mean governance is active. The evidence standard is demonstrated behaviour, not document presence. Ask: "Show me the last time this rule was enforced."

### The Primary Agent Trap
Controls applied to the primary agent but not to secondary agents, local models, or newer tools do not meet the cross-agent consistency requirement. Level 4 explicitly requires consistency across all agents in the environment.

### The Regression Trap
An organisation at Level 3 that has allowed Level 2 security controls to erode (e.g., secrets in version control after a migration) is not at Level 3. Re-assess lower levels before confirming the claimed level.

### The Context Window Trap (Level 1)
Governance documents that exist but exceed agent context window limits are functionally absent during long tasks. Evidence of context window strategy and document size management is required at Level 1.

---

## Level Progression Criteria Reference

These are the criteria an organisation must meet to progress from each level to the next. They are derived from the source framework (Section 4) and are listed here for reference during assessment.

### To reach Level 1 (from Level 0):
1. Acknowledge that AI agents require explicit behavioural instructions
2. Create at least one governance document (CLAUDE.md, AGENTS.md, or equivalent) containing coding standards and validation rules
3. Establish a repository or location where agent instructions are maintained
4. Document what agents are in use and what systems they access

### To reach Level 2 (from Level 1):
1. Implement credential hygiene: all secrets in environment variables, .env in .gitignore, pre-commit scanning for leaked secrets
2. Define and enforce a CORS policy for any agent-accessible web endpoints
3. Implement rate limiting on all authentication endpoints
4. Establish injection defence measures (input validation, output sanitisation)
5. Document security non-negotiables in the governance file and verify compliance

### To reach Level 3 (from Level 2):
1. Define a value alignment framework: which work the agent should prioritise, defer, or reject
2. Establish scope boundaries: what the agent builds proactively vs reactively
3. Implement cost governance: token budgets, compute cost tracking, threshold alerts
4. Define delivery standards: output quality gates, formatting requirements, turnaround expectations
5. Document a conflict resolution order for when business rules conflict

### To reach Level 4 (from Level 3):
1. Unify all governance pillars into a single operating framework with named pillars
2. Activate autonomous operation controls: turn limits, exit conditions, overnight safety rules
3. Formalise conflict resolution order as unconditional (no exceptions, no runtime overrides)
4. Implement third-party isolation: agent-generated content does not leak client data, pricing, or internal strategy
5. Establish governance review cadence: scheduled review and update cycle for all governance documents

### To reach Level 5 (from Level 4):
1. Implement automated governance health monitoring that detects when governance documents are modified, moved, or weakened
2. Deploy lint hooks or CI/CD checks validating governance file integrity on every commit
3. Establish automated health reporting: regular machine-generated compliance reports without manual intervention
4. Implement governance drift detection: comparison of current state against known-good baseline
5. Achieve continuous assurance: governance monitors and reports on itself without manual audit triggers
