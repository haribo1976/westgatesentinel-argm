---
title: ARGM Assessment Template
version: "2.0"
tags: [argm, assessment, governance]
date: 2026-04-06
---

# ARGM Assessment Template

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

Use this template to assess an organisation's ARGM maturity level. For each level, answer all five questions with evidence. Score each answer 0–2 (0 = no evidence, 1 = partial, 2 = full). A level is achieved when all five questions score ≥1 and at least three score 2.

Questions marked **[CRITICAL]** must score 2 for the level to be achieved, regardless of the overall score.

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

3. Is D0 (Data Protection) explicitly stated as the highest-priority principle in your governance document, even if technical enforcement is not yet in place?

   *Evidence:*

4. How do you manage governance document size as they grow? What is your context window strategy?

   *Evidence:*

5. Demonstrate an agent completing a task end-to-end and trace which governance rules applied at each decision point.

   *Evidence:*

**Level 1 Score:** ___/10

---

## Level 2 — Secured

**Assessment Questions:**

1. **[CRITICAL]** Show me your pre-commit scanning configuration. When was it last triggered, and what was the outcome?

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

## Level 3 — Controlled

**Assessment Questions:**

1. **[CRITICAL]** Show me your turn limit configuration for unattended agent tasks. When was it last enforced, and what happened when the limit was reached?

   *Evidence:*

2. Demonstrate a dry-run execution. How does an agent distinguish between dry-run and live mode? Show the mechanism.

   *Evidence:*

3. What happens if an agent attempts a destructive operation (file deletion, record deletion, infrastructure teardown)? Show the prohibition and logging.

   *Evidence:*

4. Walk me through an overnight or scheduled agent task end-to-end. What are the exit conditions, and how is the outcome reported?

   *Evidence:*

5. Show me write operation logs from the last 7 days. Do they include timestamp, operation type, record ID, and outcome? Is PII excluded?

   *Evidence:*

**Level 3 Score:** ___/10

---

## Level 4 — Aligned

**Assessment Questions:**

1. Show me your value alignment framework. How does an agent classify a task as primary, secondary, enablement, or reject? Show the decision mechanism (flowchart, rules, or classification prompt).

   *Evidence:*

2. **[CRITICAL]** Walk me through your cost governance controls. Show model selection policy, budget allocation, and evidence of at least one cost-influenced decision in the past 90 days.

   *Evidence:*

3. What is your Tier 2 directive ordering, and why? Show the documented rationale for your organisation's chosen order of D3–D6.

   *Evidence:*

4. Describe the full conflict resolution order. Give a scenario where a Tier 1 directive conflicts with a Tier 2 directive and show resolution.

   *Evidence:*

5. Show me delivery standards for agent output. Demonstrate a recent deliverable and which quality gates it passed.

   *Evidence:*

**Level 4 Score:** ___/10

---

## Level 5 — Governed

**Assessment Questions:**

1. Show me your complete governance framework. Identify each directive (D0–D6), state its tier and scope, and demonstrate conflict resolution in practice.

   *Evidence:*

2. Demonstrate the break-glass exception mechanism. Show a recent use or a documented test exercise. Who was the named individual, what was overridden, what was the time bound?

   *Evidence:*

3. How do you enforce third-party data isolation? Show a recent agent output and confirm no client-identifying data in version control or logs.

   *Evidence:*

4. **[CRITICAL]** Is this framework applied consistently across all AI agents? Show evidence for at least two different agents.

   *Evidence:*

5. When was the last governance review? Show what changed, why, and who approved.

   *Evidence:*

**Level 5 Score:** ___/10

---

## Level 6 — Autonomous

**Assessment Questions:**

1. **[CRITICAL]** Show me your governance drift detection mechanism. When was it last triggered, and what was the finding?

   *Evidence:*

2. Demonstrate someone modifying a governance document. What automated checks fire, what alerts generate, who is notified?

   *Evidence:*

3. Show me your most recent automated governance health report. Walk through each metric and explain what failure looks like.

   *Evidence:*

4. How do you prevent the self-monitoring layer from being weakened or bypassed? Describe your three-layer assurance (technical, organisational, external).

   *Evidence:*

5. When was the last external review of your governance framework? Who conducted it, and what did they find?

   *Evidence:*

**Level 6 Score:** ___/10

---

## Summary

| Level | Score | Critical Questions Met? | Achieved? |
|-------|-------|------------------------|-----------|
| 0 — Ungoverned | /10 | N/A | |
| 1 — Instructed | /10 | N/A | |
| 2 — Secured | /10 | Q1 | |
| 3 — Controlled | /10 | Q1 | |
| 4 — Aligned | /10 | Q2 | |
| 5 — Governed | /10 | Q4 | |
| 6 — Autonomous | /10 | Q1 | |

**Current ARGM Level:** ___

**Assessor:** _______________

**Date:** _______________

**Next Review:** _______________
