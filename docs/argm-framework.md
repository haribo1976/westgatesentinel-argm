# ARGM: Agentic Runtime Governance Model — Full Framework

**Version:** 1.0 DRAFT
**Date:** 2026-04-06
**Author:** [AUTHOR]
**Licence:** CC-BY-SA 4.0

---

## 1. Purpose

ARGM provides a six-level maturity framework (0-5) for assessing how organisations govern AI agents at runtime. It addresses the operational gap between existing AI governance frameworks (NIST AI RMF, ISO 42001, CMMI) and the reality of agents that write files, execute shell commands, invoke APIs, and make irreversible system state changes.

Existing frameworks govern the AI lifecycle, organisational readiness, and risk management processes. None of them answer the question: what rules govern this agent's behaviour while it is running?

ARGM answers that question with progressive maturity levels, observable evidence requirements, assessment questions, and a seven-pillar reference architecture for full governance.

---

## 2. Research Foundation

### Structural Conventions Drawn From

- **CMMI (v2.0/v3.0, ISACA):** Staged maturity levels where each builds on the previous. Evidence-based assessment via SCAMPI methodology. Level 0 (Incomplete) through Level 5 (Optimizing). Five factors per key process area: goals, commitment, ability, measurement, verification.
- **NIST CSF 2.0:** Four implementation tiers (Partial, Risk Informed, Repeatable, Adaptive) describing governance rigour. Six core functions (Govern, Identify, Protect, Detect, Respond, Recover).
- **NIST AI RMF 1.0:** Four functions (Govern, Map, Measure, Manage). Voluntary, non-prescriptive. No formal maturity tiers but supports maturity-style assessment.
- **ISO 42001:2023:** Annex SL clause structure (context, leadership, planning, support, operation, performance evaluation, improvement). PDCA cycle. 38 AI-specific controls. Third-party certifiable.
- **UK DSIT Five Principles:** Safety/security/robustness, transparency/explainability, fairness, accountability/governance, contestability/redress. Principles-based, non-statutory, regulator-interpreted.

### Existing Agentic AI Governance Models Surveyed

- **AISM (AI Sovereignty Maturity Model, Cyber Strategy Institute, 2025-2026):** Five levels (Chaos, Visibility, Governance, Control, Sovereignty). Five pillars (Shield, Ledger, Circuit Breaker, Command Center, Learning Engine). 128 controls in a Sovereignty Matrix. Dual-licensed MIT + CC-BY-SA. Closest existing model to ARGM in scope. Strong on threat modelling and non-human identity governance. No business value alignment, cost governance, or delivery standards.
- **Microsoft Agentic AI Adoption Maturity Model (2026):** Five levels (100-500: Initial, Repeatable, Defined, Capable, Efficient). Enterprise adoption focus across strategy, governance, technology, and organisational dimensions. Adoption readiness model, not runtime governance model.
- **McKinsey AI Trust Maturity Model (2026):** Five dimensions (strategy, risk management, data/technology, governance, agentic AI governance). Four maturity levels. Survey of ~500 organisations. Found average RAI maturity at 2.3/4, with only ~30% at level 3+ for agentic AI governance. Benchmarking tool, not prescriptive governance framework.
- **Salesforce Agentic Maturity Model (2025):** Four stages (single agent, multi-agent coordination, autonomous orchestration, enterprise AI ecosystem). Adoption-focused. No runtime governance specificity.
- **Arsanjani Agentic AI Maturity Model (2025-2026):** Six levels mapped to NeurIPS 2025 findings. Level 5 treats governance as executable code. Level 4 introduces sandboxed constitutional agency. Thought leadership, not a formal assessment framework.
- **AIGN Agentic AI Governance Framework 1.0 (2025):** Five maturity levels with agentic trust scans. Published by AI Governance Network. Includes cultural maturity benchmarks. Independent adoption evidence not confirmed.
- **Pandey, R. Agentic AI Governance Framework (SSRN, October 2025):** Six governance principles with Agentic Log Retention Index (ALRI) and Runtime Governance Architecture. Academic paper with implementation mappings for LangChain, Power Platform, UiPath.
- **Governance Architecture for Autonomous Agent Systems (arXiv, 2026):** Academic paper covering prompt injection, RAG poisoning, multi-agent security. Proposes Layered Governance Architecture (LGA). References OpenClaw as a case study.

### Gaps Identified in Existing Models

No existing model addresses all of the following simultaneously:

1. **Agentic autonomy controls** (turn limits, dry-run defaults, destructive operation prohibition, overnight safety rules)
2. **Multi-agent routing and scope bounding** (what each agent is permitted to build, proactive vs reactive)
3. **Runtime self-monitoring and governance drift detection** (automated verification that governance documents have not been weakened)
4. **Business value alignment as a governance dimension** (agent effort maps to organisational revenue priorities)
5. **Cost governance as a governance dimension** (token budgets, compute cost tracking, model selection governance)

ARGM addresses all five.

---

## 3. Design Decisions

### Why Six Levels (0-5) Rather Than Five (1-5)?

CMMI v2.0 and the Secure Controls Framework C|P-CMM both include a Level 0 representing absence. Most organisations using AI coding tools today have zero explicit runtime governance. Starting at Level 1 would imply basic governance is the worst case. It is not.

### Why Runtime Focus Rather Than Lifecycle?

ISO 42001 and NIST AI RMF cover AI management system and risk management lifecycle comprehensively. Neither addresses runtime agent behaviour: what happens when agents execute code, modify files, and invoke APIs. ARGM complements lifecycle governance. It does not replace it.

### Why Business Alignment Before Full Governance?

McKinsey's 2026 survey confirmed that governance lags behind technical capability. Organisations that skip business alignment and jump to comprehensive governance frameworks build frameworks disconnected from operational reality. Aligning agent effort to business value (Level 3) before formalising the full pillar architecture (Level 4) ensures the framework serves the organisation.

### Why Cost Governance?

No surveyed framework treats cost governance as a first-class maturity dimension. Token costs, compute spend, and model selection directly affect whether agentic AI operations are sustainable. An organisation running agents without cost visibility is not governed, regardless of its security posture.

### Why Self-Monitoring at Level 5?

Governance documents enforced solely by prompt-based instruction are soft constraints. Models can ignore, de-prioritise, or misinterpret them. Level 5 moves governance enforcement from semantic interpretation to automated verification: lint hooks, drift detection, health reporting. The framework governs itself.

---

## 4. Level Definitions

### Level 0 — Ungoverned

**Definition:** No runtime governance. Agent operates on default model behaviour. No explicit rules, no scope control, no security controls.

**Observable Evidence:**
- No CLAUDE.md, AGENTS.md, system prompt files, or equivalent governance documents in any repository
- No .gitignore entries for secrets or environment files (or .env files committed to version control)
- No branch protection on repositories where agents operate
- API keys, tokens, or credentials hardcoded in scripts or configuration files
- No audit trail of agent actions beyond default provider logs
- No documented scope boundaries for agent permissions
- Agents have same access as the human operator with no least-privilege separation

**Progression Criteria (to reach Level 1):**
1. Acknowledge that AI agents require explicit behavioural instructions
2. Create at least one governance document (CLAUDE.md, AGENTS.md, or equivalent) containing coding standards and validation rules
3. Establish a repository or location where agent instructions are maintained
4. Document what agents are in use and what systems they access

**Common Failure Modes:**
- "It's fine, I'm watching it" — reliance on human supervision as sole control
- Credential sprawl — agents accumulate permissions, never revoked
- Shadow agents — team members adopt tools with no organisational awareness
- Irreversible damage from defaults — agents execute destructive operations because nothing told them not to

**Assessment Questions:**
1. Show me a complete inventory of AI agents in your environment, including which systems each agent accesses.
2. Where are the documented rules governing what your AI agents are permitted and prohibited from doing?
3. Show me the last five commits made by or with an AI agent. Can you trace what instructions governed each commit?
4. How are credentials managed for AI agent access? Show me where API keys are stored.
5. If an agent made an irreversible change to a production system right now, what mechanism would prevent or detect it?

---

### Level 1 — Instructed

**Definition:** Basic prompt-level instructions in place. Governance documents define coding standards, validation gates, context management rules, and behavioural expectations. Agent behaviour is guided but enforcement depends entirely on model compliance. No security layer, no business alignment, no cost controls.

**Observable Evidence:**
- CLAUDE.md, AGENTS.md, or equivalent governance file exists in each repository where agents operate
- Coding conventions documented: file naming, commit format, linting rules, output schemas
- Validation gates defined: what must be true before an agent commits code or creates files
- Context management rules present: how agents handle long conversations, what to include in prompts
- Basic file structure discipline: agents know where to write and where not to
- "Do not" list: prohibited actions or files the agent must not modify
- No security-specific controls (no injection defence, no credential hygiene, no CORS policy)
- No business priority alignment
- No cost tracking or token budget constraints

**Progression Criteria (to reach Level 2):**
1. Implement credential hygiene: all secrets in environment variables, .env in .gitignore, pre-commit scanning for leaked secrets
2. Define and enforce a CORS policy for any agent-accessible web endpoints
3. Implement rate limiting on all authentication endpoints
4. Establish injection defence measures (input validation, output sanitisation)
5. Document security non-negotiables in the governance file and verify compliance

**Common Failure Modes:**
- Instruction drift — governance documents written once, never updated
- Compliance theatre — agents instructed to follow rules but no verification they do
- Overloaded system prompts — governance documents grow past context window limits, causing de-prioritisation of critical rules
- False confidence — presence of a CLAUDE.md creates assumption of governance that does not exist in practice
- No enforcement mechanism — all rules are soft constraints interpreted by model language understanding

**Assessment Questions:**
1. Show me the governance documents that instruct your AI agents. When were they last reviewed and by whom?
2. How do you verify that agents actually follow instructions? Show me evidence of a recent violation and how it was detected.
3. What happens when an agent encounters conflicting instructions? Is there a documented conflict resolution order?
4. How do you manage governance document size as they grow? What is your context window strategy?
5. Demonstrate an agent completing a task end-to-end and trace which governance rules applied at each decision point.

---

### Level 2 — Secured

**Definition:** Security layer added on top of instructional foundation. Credential hygiene, injection defence, CORS policy, rate limiting, and pre-commit scanning enforced as non-negotiable requirements. Security controls exist as both documented requirements and enforced technical controls, not solely prompt-based. Agent operates securely but without business context.

**Observable Evidence:**
- **Secrets management:** All API keys, tokens, credentials in environment variables or secret managers. .env and .dev.vars in .gitignore. Scripts read secrets from env vars, not parameters.
- **Pre-commit scanning:** Git hooks or CI stages scan for: `sk_`, `pk_`, `eyJ`, `API_KEY=`, `SECRET=`, `Bearer`, `client_secret=`, `PRIVATE_KEY`, `Authorization:`
- **CORS policy:** No `Access-Control-Allow-Origin: *` in production. Specific trusted origins whitelisted. Credentials paired with origin restrictions.
- **Rate limiting:** All authentication endpoints rate-limited (default: 5 attempts/minute/IP). Breach logging and alerting configured.
- **Injection defence:** Input validation on all agent-facing interfaces. Output sanitisation for agent-generated content rendered in web contexts.
- **Branch protection:** Main/production branches require pull request review. Agents cannot push directly to protected branches.
- **Least privilege:** Agent service accounts have minimum required permissions. No shared admin credentials.
- **Rotation policy:** Documented credential rotation process. Evidence of at least one rotation in the past 90 days.

**Progression Criteria (to reach Level 3):**
1. Define a value alignment framework: which work the agent should prioritise, defer, or reject
2. Establish scope boundaries: what the agent builds proactively vs reactively
3. Implement cost governance: token budgets, compute cost tracking, threshold alerts
4. Define delivery standards: output quality gates, formatting requirements, turnaround expectations
5. Document a conflict resolution order for when business rules conflict

**Common Failure Modes:**
- Security as ceiling — treating security as the end goal rather than a foundation
- Tool-specific silos — controls applied to one agent but not others
- Alert fatigue — false positives train developers to ignore pre-commit scans
- Static security posture — controls not adapted as agent capabilities expand
- Missing the business question — a perfectly secure agent building the wrong things

**Assessment Questions:**
1. Show me your pre-commit scanning configuration. When was it last triggered, and what was the outcome?
2. Walk me through how an agent accesses a production system. What credentials, where stored, when last rotated?
3. If I submitted a prompt containing a SQL injection payload, what would happen? Show me the defence.
4. How do you ensure security controls are consistent across all AI agents, not the primary one only?
5. What was the last security incident or near-miss involving an AI agent? How was it detected and resolved?

---

### Level 3 — Aligned

**Definition:** Business governance added on top of security foundation. Value alignment tiers map agent effort to organisational priorities. Scope boundaries prevent agents building outside their mandate. Cost constraints cap token spend and compute usage. Delivery standards enforce output quality. The agent operates securely and its work maps to what the organisation values most.

**Observable Evidence:**
- **Value alignment tiers:** Documented hierarchy of work priorities (primary, secondary, enablement, reject) governing proactive vs reactive build decisions
- **Scope boundaries:** Explicit list of permitted builds, approval-required builds, and prohibited builds regardless of request
- **Cost governance:** Token usage tracked per agent, per task, per period. Budget thresholds with alerts. Evidence of at least one cost-related decision (pausing a task, choosing a smaller model, deferring non-priority work)
- **Delivery standards:** Output quality gates: branded templates, executive summary length limits, turnaround SLAs, no raw script output without formatted wrapper
- **Conflict resolution order:** Documented, unconditional priority order for when governance rules conflict
- **Agent task classification:** Each agent task tagged by value tier before execution begins
- **Dry-run defaults:** Write operations default to dry-run mode unless explicitly scheduled for live execution
- **Destructive operation prohibition:** Agents cannot delete records, objects, or infrastructure without explicit human authorisation and logging

**Progression Criteria (to reach Level 4):**
1. Unify all governance pillars (instruction, security, business alignment) into a single operating framework with named pillars
2. Activate autonomous operation controls: turn limits, exit conditions, overnight safety rules
3. Formalise conflict resolution order as unconditional (no exceptions, no runtime overrides)
4. Implement third-party isolation: agent-generated content does not leak client data, pricing, or internal strategy
5. Establish governance review cadence: scheduled review and update cycle for all governance documents

**Common Failure Modes:**
- Over-engineering priorities — more time classifying work than doing it
- Value alignment as veto — rejecting all non-primary work, missing legitimate enablement tasks
- Cost governance as rationing — token budgets so low that output quality degrades
- Delivery standards without substance — professional formatting over shallow content
- Misaligned incentives — optimising for stated values rather than operational needs

**Assessment Questions:**
1. Show me your value alignment framework. How does an agent determine whether a task is primary, secondary, enablement, or reject?
2. Walk me through a recent example where cost governance influenced a decision.
3. What are your delivery standards for agent output? Show me a recent deliverable and explain which quality gates it passed.
4. Describe your conflict resolution order. Give me a scenario where two rules conflict and show me resolution.
5. Show me an example of work that fell outside scope and how it was handled.

---

### Level 4 — Governed

**Definition:** Full multi-pillar operating framework active. All security, business, and delivery controls operate as an integrated system. Autonomous operation controls active: turn limits, exit conditions, overnight safety rules. Conflict resolution order unconditional and documented. Third-party data isolation enforced. The framework constitutes a complete governance system auditable end-to-end.

**Observable Evidence:**
- **Unified governance framework:** Single document or document set defining all pillars: instruction standards, security non-negotiables, business alignment, delivery standards, autonomous operation controls, data protection, conflict resolution order
- **Pillar architecture:** Governance organised into named, numbered pillars (not ad hoc rules scattered across files)
- **Autonomous operation controls:**
  - Maximum agent turn limits per task (e.g., 15 turns for overnight tasks)
  - Clean exit conditions when limits reached
  - Dry-run default for all scheduled/unattended operations
  - No destructive operations without explicit human scheduling
  - No external API calls or email sends without explicit authorisation flag
  - Full logging of every write operation: timestamp, operation, record ID, outcome
  - No PII in logs or stdout: log only operation name, record count, status code, error code
- **Third-party isolation:** No client names, tenant IDs, PII, or commercial pricing in repositories, logs, or agent output. Placeholder syntax enforced (`{{CLIENT_NAME}}`, `{{TENANT_ID}}`)
- **Conflict resolution order:** Documented priority sequence for all pillars, declared unconditional. Data protection wins without exception.
- **Governance review cadence:** Evidence of scheduled reviews (quarterly minimum) with documented changes, rationale, and approval
- **Cross-agent consistency:** Same governance framework applied to all agents in the environment, not the primary agent only

**Progression Criteria (to reach Level 5):**
1. Implement automated governance health monitoring that detects when governance documents are modified, moved, or weakened
2. Deploy lint hooks or CI/CD checks validating governance file integrity on every commit
3. Establish automated health reporting: regular machine-generated compliance reports without manual intervention
4. Implement governance drift detection: comparison of current state against known-good baseline
5. Achieve continuous assurance: governance monitors and reports on itself without manual audit triggers

**Common Failure Modes:**
- Framework as shelfware — comprehensive document that exists but is not operationally enforced
- Rigidity paralysis — so prescriptive that legitimate work is blocked, causing workarounds
- Single-agent assumption — governs the primary agent but not secondary agents, local models, or new tools
- Review theatre — quarterly reviews occur but produce no meaningful changes
- Governance document bloat — framework exceeds context window capacity, fragmenting enforcement

**Assessment Questions:**
1. Show me your complete governance framework. How many pillars, and how are inter-pillar conflicts resolved?
2. Demonstrate an overnight or unattended agent task. Show turn limits, exit conditions, dry-run defaults, and logging in operation.
3. How do you enforce third-party data isolation? Show a recent agent output and confirm no client-identifying data in version control or logs.
4. Is this framework applied consistently across all AI agents? Show evidence for at least two different agents.
5. When was the last governance review? Show what changed, why, and who approved.

---

### Level 5 — Autonomous

**Definition:** The governance framework governs itself. Self-monitoring layer detects governance drift, reports on compliance health, and enforces governance document integrity without manual intervention. Lint hooks validate governance files on every commit. Automated health reports generated on a defined schedule. Changes to governance documents trigger alerts and require review. Continuous assurance achieved: an assessor can verify compliance at any point without triggering a manual audit.

**Observable Evidence:**
- **Governance drift detection:** Automated mechanism compares current governance documents against known-good baseline. Deviation triggers alert. Implementation options:
  - Git-based: hash comparison against pinned baseline commit
  - CI/CD: pipeline stage validating governance file structure and content on every push
  - Scheduled: cron or equivalent auditing governance state at defined intervals
- **Lint hooks on governance files:** Pre-commit or CI hooks that:
  - Validate governance document structure (required sections present)
  - Check for prohibited content (hardcoded secrets, client names, tenant IDs)
  - Verify conflict resolution order is intact and unconditional
  - Flag weakening of security non-negotiables (e.g., removal of rate limiting requirements)
- **Automated health reporting:** Machine-generated compliance reports at defined intervals (weekly minimum) covering:
  - Governance document currency (last review date, days since last change)
  - Security control compliance (scan results, rotation status, CORS configuration)
  - Business alignment adherence (task classification distribution, cost against budget)
  - Autonomous operation compliance (turn limit adherence, dry-run default status)
- **Third-party isolation verification:** Automated scanning of all agent outputs, logs, and repository contents for client-identifying data patterns
- **Change control on governance:** Modifications require pull request review from designated governance owner. Force pushes to governance files blocked.
- **Governance versioning:** Governance documents carry semantic version numbers. Changes tracked in changelog with rationale.

**Common Failure Modes:**
- Monitoring the monitor — self-monitoring layer itself becomes single point of failure with no oversight
- False assurance — automated reports show green but checks are too shallow to catch meaningful erosion
- Alert overload — drift detection too sensitive, generating noise that causes alerts to be ignored
- Ossification — self-monitoring enforces current state so rigidly that legitimate evolution becomes difficult
- Toolchain dependency — monitoring built on specific CI/CD platform that becomes unavailable

**Assessment Questions:**
1. Show me your governance drift detection mechanism. When was it last triggered, and what was the finding?
2. Demonstrate someone modifying a governance document. What automated checks fire, what alerts generate, who is notified?
3. Show me your most recent automated governance health report. Walk through each metric and explain what failure looks like.
4. How do you prevent the self-monitoring layer from being weakened or bypassed? What governs the governor?
5. Show me version history of your governance framework. For the most recent change, explain trigger, change, and validation.

---

## 5. Seven-Pillar Reference Architecture (Level 4+)

At Level 4 and above, governance should be organised into defined pillars. This seven-pillar architecture is a reference model. Organisations adapt pillar count and scope to their context.

| Pillar | Name | Scope |
|--------|------|-------|
| P0 | Data Protection | Client data isolation, PII handling, retention limits, placeholder enforcement |
| P1 | Revenue Alignment | Value tiers, scope boundaries, proactive vs reactive build decisions |
| P2 | Infrastructure Portability | Tenant strategy, SKU selection, cost targets, auth architecture |
| P3 | Delivery Standards | Output quality, branding, turnaround SLAs, formatted wrapper requirements |
| P4 | Operational Efficiency | Automation targets, JSON output schemas, template consumption patterns |
| P5 | Security Controls | Secrets management, CORS, rate limiting, injection defence, pre-commit scanning |
| P6 | Autonomous Operation | Turn limits, dry-run defaults, destructive operation prohibition, overnight safety, logging |

**Conflict Resolution Order:** P0 > P6 > P1 > P2 > P4 > P3 > P5

Data protection wins unconditionally. Autonomous operation safety overrides business priorities. Revenue alignment overrides infrastructure and efficiency concerns. Security controls (P5) rank lower than business pillars because security is non-negotiable at all levels from Level 2 upward and does not require priority arbitration in the same way business rules do. Security requirements are baseline; they do not compete with other pillars.
