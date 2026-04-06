# ARGM Assessment Template

**Version:** 1.1
**Licence:** CC-BY-SA 4.0

Use this template to assess an organisation's ARGM maturity level. For each level, answer all five questions with evidence. Score each answer 0–2 (0 = no evidence, 1 = partial, 2 = full). A level is achieved when all five questions score ≥1 and at least three score 2.

---

## Level 0 — Ungoverned

**Assessment Questions:**

1. Show me a complete inventory of AI agents in your environment, including which systems each agent accesses.

   *Evidence:*

2. Where are the documented rules governing what your AI agents are permitted and prohibited from doing?

   *Evidence:*

3. Show me the last five commits made by or with an AI agent. Can you trace what instructions governed each commit?

   *Evidence:*

4. How are credentials managed for AI agent access? Show me where API keys are stored.

   *Evidence:*

5. If an agent made an irreversible change to a production system right now, what mechanism would prevent or detect it?

   *Evidence:*

**Level 0 Score:** ___/10

---

## Level 1 — Instructed

**Assessment Questions:**

1. Show me the governance documents that instruct your AI agents. When were they last reviewed and by whom?

   *Evidence:*

2. How do you verify that agents actually follow instructions? Show me evidence of a recent violation and how it was detected.

   *Evidence:*

3. What happens when an agent encounters conflicting instructions? Is there a documented conflict resolution order? Even at Level 1, D0 (Data Protection) must be unconditional — is this explicit in the governance document?

   *Evidence:*

4. How do you manage governance document size as they grow? What is your context window strategy?

   *Evidence:*

5. Demonstrate an agent completing a task end-to-end and trace which governance rules applied at each decision point.

   *Evidence:*

**Level 1 Score:** ___/10

---

## Level 2 — Secured

**Assessment Questions:**

1. Show me your pre-commit scanning configuration. When was it last triggered, and what was the outcome?

   *Evidence:*

2. Walk me through how an agent accesses a production system. What credentials, where stored, when last rotated?

   *Evidence:*

3. If I submitted a prompt containing a SQL injection payload, what would happen? Show me the defence.

   *Evidence:*

4. How do you ensure security controls are consistent across all AI agents, not the primary one only?

   *Evidence:*

5. What was the last security incident or near-miss involving an AI agent? How was it detected and resolved?

   *Evidence:*

**Level 2 Score:** ___/10

---

## Level 3 — Aligned

**Assessment Questions:**

1. Show me your value alignment framework. How does an agent determine whether a task is primary, secondary, enablement, or reject?

   *Evidence:*

2. Walk me through a recent example where cost governance influenced a decision.

   *Evidence:*

3. What are your delivery standards for agent output? Show me a recent deliverable and explain which quality gates it passed.

   *Evidence:*

4. Describe your conflict resolution order. Give me a scenario where two rules conflict and show me resolution.

   *Evidence:*

5. Show me an example of work that fell outside scope and how it was handled.

   *Evidence:*

**Level 3 Score:** ___/10

---

## Level 4 — Governed

**Assessment Questions:**

1. Show me your complete governance framework. Identify each prime directive (D0–D6), state its scope, and demonstrate how directive conflicts resolve in practice.

   *Evidence:*

2. Demonstrate an overnight or unattended agent task. Show turn limits, exit conditions, dry-run defaults, and logging in operation.

   *Evidence:*

3. How do you enforce third-party data isolation? Show a recent agent output and confirm no client-identifying data in version control or logs.

   *Evidence:*

4. Is this framework applied consistently across all AI agents? Show evidence for at least two different agents.

   *Evidence:*

5. When was the last governance review? Show what changed, why, and who approved.

   *Evidence:*

**Level 4 Score:** ___/10

---

## Level 5 — Autonomous

**Assessment Questions:**

1. Show me your governance drift detection mechanism. When was it last triggered, and what was the finding?

   *Evidence:*

2. Demonstrate someone modifying a governance document. What automated checks fire, what alerts generate, who is notified?

   *Evidence:*

3. Show me your most recent automated governance health report. Walk through each metric and explain what failure looks like.

   *Evidence:*

4. How do you prevent the self-monitoring layer from being weakened or bypassed? What governs the governor?

   *Evidence:*

5. Show me version history of your governance framework. For the most recent change, explain trigger, change, and validation.

   *Evidence:*

**Level 5 Score:** ___/10

---

## Summary

| Level | Score | Achieved? |
|-------|-------|-----------|
| 0 — Ungoverned | /10 | |
| 1 — Instructed | /10 | |
| 2 — Secured | /10 | |
| 3 — Aligned | /10 | |
| 4 — Governed | /10 | |
| 5 — Autonomous | /10 | |

**Current ARGM Level:** ___

**Assessor:** _______________

**Date:** _______________

**Next Review:** _______________
