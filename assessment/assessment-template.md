# ARGM Assessment Template

Use this template to assess the current ARGM maturity level of an organisation. Work through each level's questions. Record responses and evidence references.

**Organisation:** _______________
**Assessor:** _______________
**Date:** _______________
**Assessed Level (outcome):** _______________

---

## Level 0 — Ungoverned

*Answer these questions to determine whether Level 0 conditions exist. If any of these describe the current state, the organisation is at Level 0.*

1. Show me a complete inventory of AI agents in your environment, including which systems each agent accesses.

   **Response:** _______________
   **Evidence reference:** _______________

2. Where are the documented rules governing what your AI agents are permitted and prohibited from doing?

   **Response:** _______________
   **Evidence reference:** _______________

3. Show me the last five commits made by or with an AI agent. Can you trace what instructions governed each commit?

   **Response:** _______________
   **Evidence reference:** _______________

4. How are credentials managed for AI agent access? Show me where API keys are stored.

   **Response:** _______________
   **Evidence reference:** _______________

5. If an agent made an irreversible change to a production system right now, what mechanism would prevent or detect it?

   **Response:** _______________
   **Evidence reference:** _______________

---

## Level 1 — Instructed

*Answer these questions if the organisation has passed Level 0. These probe whether Level 1 is met or whether it is the current ceiling.*

1. Show me the governance documents that instruct your AI agents. When were they last reviewed and by whom?

   **Response:** _______________
   **Evidence reference:** _______________

2. How do you verify that agents actually follow instructions? Show me evidence of a recent violation and how it was detected.

   **Response:** _______________
   **Evidence reference:** _______________

3. What happens when an agent encounters conflicting instructions? Is there a documented conflict resolution order?

   **Response:** _______________
   **Evidence reference:** _______________

4. How do you manage governance document size as they grow? What is your context window strategy?

   **Response:** _______________
   **Evidence reference:** _______________

5. Demonstrate an agent completing a task end-to-end and trace which governance rules applied at each decision point.

   **Response:** _______________
   **Evidence reference:** _______________

---

## Level 2 — Secured

1. Show me your pre-commit scanning configuration. When was it last triggered, and what was the outcome?

   **Response:** _______________
   **Evidence reference:** _______________

2. Walk me through how an agent accesses a production system. What credentials, where stored, when last rotated?

   **Response:** _______________
   **Evidence reference:** _______________

3. If I submitted a prompt containing a SQL injection payload, what would happen? Show me the defence.

   **Response:** _______________
   **Evidence reference:** _______________

4. How do you ensure security controls are consistent across all AI agents, not the primary one only?

   **Response:** _______________
   **Evidence reference:** _______________

5. What was the last security incident or near-miss involving an AI agent? How was it detected and resolved?

   **Response:** _______________
   **Evidence reference:** _______________

---

## Level 3 — Aligned

1. Show me your value alignment framework. How does an agent determine whether a task is primary, secondary, enablement, or reject?

   **Response:** _______________
   **Evidence reference:** _______________

2. Walk me through a recent example where cost governance influenced a decision.

   **Response:** _______________
   **Evidence reference:** _______________

3. What are your delivery standards for agent output? Show me a recent deliverable and explain which quality gates it passed.

   **Response:** _______________
   **Evidence reference:** _______________

4. Describe your conflict resolution order. Give me a scenario where two rules conflict and show me resolution.

   **Response:** _______________
   **Evidence reference:** _______________

5. Show me an example of work that fell outside scope and how it was handled.

   **Response:** _______________
   **Evidence reference:** _______________

---

## Level 4 — Governed

1. Show me your complete governance framework. How many pillars, and how are inter-pillar conflicts resolved?

   **Response:** _______________
   **Evidence reference:** _______________

2. Demonstrate an overnight or unattended agent task. Show turn limits, exit conditions, dry-run defaults, and logging in operation.

   **Response:** _______________
   **Evidence reference:** _______________

3. How do you enforce third-party data isolation? Show a recent agent output and confirm no client-identifying data in version control or logs.

   **Response:** _______________
   **Evidence reference:** _______________

4. Is this framework applied consistently across all AI agents? Show evidence for at least two different agents.

   **Response:** _______________
   **Evidence reference:** _______________

5. When was the last governance review? Show what changed, why, and who approved.

   **Response:** _______________
   **Evidence reference:** _______________

---

## Level 5 — Autonomous

1. Show me your governance drift detection mechanism. When was it last triggered, and what was the finding?

   **Response:** _______________
   **Evidence reference:** _______________

2. Demonstrate someone modifying a governance document. What automated checks fire, what alerts generate, who is notified?

   **Response:** _______________
   **Evidence reference:** _______________

3. Show me your most recent automated governance health report. Walk through each metric and explain what failure looks like.

   **Response:** _______________
   **Evidence reference:** _______________

4. How do you prevent the self-monitoring layer from being weakened or bypassed? What governs the governor?

   **Response:** _______________
   **Evidence reference:** _______________

5. Show me version history of your governance framework. For the most recent change, explain trigger, change, and validation.

   **Response:** _______________
   **Evidence reference:** _______________

---

## Assessment Summary

| Level | Questions answered satisfactorily | Observable evidence demonstrated | Level met? |
|-------|----------------------------------|----------------------------------|------------|
| 0 | / 5 | | ☐ Conditions present (still at L0) |
| 1 | / 5 | | ☐ |
| 2 | / 5 | | ☐ |
| 3 | / 5 | | ☐ |
| 4 | / 5 | | ☐ |
| 5 | / 5 | | ☐ |

**Assessed level:** _______________
**Key gaps for next level:** _______________
**Recommended actions:** _______________
