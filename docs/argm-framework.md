# ARGM: Agentic Runtime Governance Model — Framework

**Version:** 2.0
**Date:** 2026-04-06
**Licence:** CC-BY-SA 4.0

---

## 1. Purpose

ARGM is a domain-specific maturity profile, built on CMMI's structural conventions, for governing AI agents at runtime. It provides seven maturity levels (0–6) and a two-tier directive architecture (D0–D6) for assessing and improving how organisations control agents that write files, execute shell commands, invoke APIs, and make irreversible system state changes.

ARGM complements ISO 42001 and NIST AI RMF. It does not replace them. ISO 42001 governs the AI management system lifecycle. NIST AI RMF governs risk management processes. Neither answers the question: what rules govern this agent's behaviour while it is running? ARGM answers that question.

ARGM is not a threat model — defer to AISM and MITRE ATLAS for threat enumeration and attack surface mapping. It is not a lifecycle framework — defer to ISO 42001 for management system certification. It is not an adoption model — defer to Microsoft's Agentic AI Adoption Maturity Model or Salesforce's Agentic Maturity Model for organisational readiness.

The directive architecture divides into two tiers. Tier 1 (D0–D2: Safety) contains directives that are unconditional — violations cause irreversible harm and no exception mechanism applies. Tier 2 (D3–D6: Business) contains directives whose recommended order can be reconfigured by sector with documented rationale. Tier 2 never overrides Tier 1.

ARGM makes three genuine contributions to the governance landscape:

1. **Runtime self-monitoring as a maturity requirement.** Governance documents enforced solely by prompt-based instruction are soft constraints. ARGM treats automated governance drift detection, lint-based enforcement, and continuous compliance reporting as the defining characteristic of its highest maturity level.
2. **Business value alignment as a governance dimension.** No surveyed framework treats the mapping of agent effort to organisational priorities as a formal governance concern. ARGM encodes this as a directive (D3) with observable evidence requirements.
3. **Cost governance as a maturity requirement.** Token budgets, compute spend tracking, and model selection governance are treated as first-class maturity dimensions, not operational afterthoughts.

---

## 2. Research Foundation

### Structural Conventions Drawn From

ARGM adopts CMMI's staged maturity progression, evidence-based assessment, and cumulative level achievement as its structural foundation. The seven ARGM levels map directly to CMMI's architectural pattern: Level 0 (Incomplete/absence), progressing through increasingly capable stages to Level 6 (self-optimising governance). This is a deliberate derivation, not a coincidence.

- **CMMI (v2.0/v3.0, ISACA):** Staged maturity levels where each builds on the previous. Evidence-based assessment via SCAMPI methodology. Level 0 (Incomplete) through Level 5 (Optimizing). Five factors per key process area: goals, commitment, ability, measurement, verification.
- **NIST CSF 2.0:** Four implementation tiers (Partial, Risk Informed, Repeatable, Adaptive) describing governance rigour. Six core functions (Govern, Identify, Protect, Detect, Respond, Recover).
- **NIST AI RMF 1.0 and AI RMF Playbook (Feb 2025):** Four functions (Govern, Map, Measure, Manage). Voluntary, non-prescriptive. No formal maturity tiers but supports maturity-style assessment. The AI RMF Playbook provides implementation guidance. SP 800-53 AI control overlays (Aug 2025) extend security and privacy controls to cover single-agent and multi-agent AI systems.
- **ISO 42001:2023:** Annex SL clause structure (context, leadership, planning, support, operation, performance evaluation, improvement). PDCA cycle. 38 AI-specific controls. Third-party certifiable.
- **UK DSIT Five Principles:** Safety/security/robustness, transparency/explainability, fairness, accountability/governance, contestability/redress. Principles-based, non-statutory, regulator-interpreted.
- **FinOps Foundation:** Established framework for cloud financial management. Defines cost governance practices (allocation, budgeting, forecasting, anomaly detection) that ARGM draws on for its agentic cost governance dimension. ARGM's contribution is applying cost governance as a maturity requirement for agentic operations specifically, not inventing cost governance as a discipline.

### Existing Agentic AI Governance Models Surveyed

- **AISM (AI Sovereignty Maturity Model, Cyber Strategy Institute, 2025-2026):** Five levels (Chaos, Visibility, Governance, Control, Sovereignty). Five pillars (Shield, Ledger, Circuit Breaker, Command Center, Learning Engine). 128 controls in a Sovereignty Matrix. Dual-licensed MIT + CC-BY-SA. Closest existing model to ARGM in scope. Strong on threat modelling and non-human identity governance. Current AI SAFE² scope covers shell-access agent governance, alignment drift detection, sub-agent policy enforcement, and cross-agent trust boundaries. No business value alignment, cost governance, or delivery standards.
- **Microsoft Agentic AI Adoption Maturity Model (2026):** Five levels (100-500: Initial, Repeatable, Defined, Capable, Efficient). Enterprise adoption focus across strategy, governance, technology, and organisational dimensions. Adoption readiness model, not runtime governance model.
- **McKinsey AI Trust Maturity Model (2026):** Five dimensions (strategy, risk management, data/technology, governance, agentic AI governance). Four maturity levels. Survey of ~500 organisations. Found average RAI maturity at 2.3/4, with only ~30% at level 3+ for agentic AI governance. Benchmarking tool, not prescriptive governance framework.
- **Salesforce Agentic Maturity Model (2025):** Four stages (single agent, multi-agent coordination, autonomous orchestration, enterprise AI ecosystem). Adoption-focused. No runtime governance specificity.
- **Arsanjani Agentic AI Maturity Model (2025-2026):** Six levels mapped to NeurIPS 2025 findings. Level 5 treats governance as executable code. Level 4 introduces sandboxed constitutional agency. Thought leadership, not a formal assessment framework.
- **AIGN Agentic AI Governance Framework 1.0 (2025):** Five maturity levels with agentic trust scans. Published by AI Governance Network. Includes cultural maturity benchmarks. Independent adoption evidence not confirmed.
- **Pandey, R. Agentic AI Governance Framework (SSRN, October 2025):** Six governance principles with Agentic Log Retention Index (ALRI) and Runtime Governance Architecture. Academic paper with implementation mappings for LangChain, Power Platform, UiPath.
- **Governance Architecture for Autonomous Agent Systems (arXiv, 2026):** Academic paper covering prompt injection, RAG poisoning, multi-agent security. Proposes Layered Governance Architecture (LGA). References OpenClaw as a case study.

### Gaps Identified in Existing Models

After surveying the landscape, ARGM identifies three areas where no existing model provides adequate coverage:

1. **Runtime self-monitoring and governance drift detection** — automated verification that governance documents have not been weakened, with continuous compliance reporting rather than periodic manual audit.
2. **Business value alignment as a governance dimension** — formal governance over which work agents prioritise, defer, or reject, mapped to organisational priorities with observable evidence requirements.
3. **Cost governance as a first-class maturity requirement** — token budgets, compute cost tracking, and model selection governance treated as governance dimensions rather than operational concerns.

Other models, particularly AISM, address autonomy controls (Circuit Breaker pillar) and multi-agent scope bounding (swarm governance) at comparable or greater depth. ARGM does not claim unique coverage of these areas.

---

## 3. Design Decisions

### Why Seven Levels (0–6)?

ARGM v1.1 used six levels (0–5). Level 3 activated five directives simultaneously — autonomous operation controls, value alignment, infrastructure governance, operational efficiency, and delivery standards — making it the most overloaded level in the framework. v2.0 splits this into Level 3 (Controlled: autonomous operation) and Level 4 (Aligned: business directives), distributing the governance work across two levels. The remaining levels shift accordingly: v1.1 Level 4 becomes Level 5, v1.1 Level 5 becomes Level 6.

Level 0 is retained. CMMI v2.0 and the Secure Controls Framework C|P-CMM both include a Level 0 representing absence. Most organisations using AI coding tools today have zero explicit runtime governance. Starting at Level 1 would imply basic governance is the worst case. It is not.

### Why a Domain-Specific CMMI Profile?

CMMI's maturity structure is proven, well-understood, and widely adopted across industries. Building on it rather than inventing a new maturity architecture gives ARGM immediate structural credibility and reduces adoption friction for organisations already familiar with capability maturity assessment.

The mapping is explicit and intentional. ARGM Level 0 corresponds to CMMI Level 0 (Incomplete). The progression through increasingly capable stages follows CMMI's cumulative achievement model — each level builds on the previous. ARGM is a domain-specific application of CMMI's architecture to agentic runtime governance, not a novel maturity model.

### Why Runtime Focus Rather Than Lifecycle?

ISO 42001 and NIST AI RMF cover AI management system and risk management lifecycle comprehensively. Neither addresses runtime agent behaviour: what happens when agents execute code, modify files, and invoke APIs. ARGM complements lifecycle governance. It does not replace it.

### Why Two-Tier Directive Architecture?

D0–D2 (Safety) are unconditional because violations cause irreversible harm. A data protection failure exposes client information that cannot be unexposed. A security breach compromises credentials that must be assumed compromised forever. An unsupervised destructive operation deletes data that may not be recoverable. No sector, no business context, and no organisational priority justifies relaxing these directives.

D3–D6 (Business) have a recommended order, but organisations in different sectors legitimately prioritise differently. A hospital deploying agentic AI may prioritise infrastructure governance (D4) over value alignment (D3) because system reliability is a patient safety concern. A government agency may prioritise operational efficiency (D5) over value alignment because public sector accountability demands cost justification before strategic alignment. Making Tier 2 configurable with documented rationale is honest governance, not weak governance.

### Why Break-Glass for Tier 2?

Real enterprise governance requires exception handling. A framework with no exception mechanism does not prevent exceptions — it drives them off-book, unlogged, and unaccountable.

The break-glass mechanism for Tier 2 directives at Level 5 and above is time-bounded (72 hours maximum), requires named individual accountability, mandates immutable logging of the exception and its justification, and triggers a mandatory post-incident review. It cannot override Tier 1 directives under any circumstances. The mechanism exists because governance that accounts for operational reality is stronger than governance that pretends exceptions never happen.

### Why Business Alignment Before Full Governance?

McKinsey's 2026 survey confirmed that governance lags behind technical capability. Organisations that skip business alignment and jump to comprehensive governance frameworks build frameworks disconnected from operational reality. The observation that alignment tends to precede effective governance is now encoded structurally in v2.0: Level 4 (Aligned) establishes business directives as a distinct maturity stage before Level 5 (Governed) integrates the full directive architecture.

### Why Cost Governance?

The FinOps Foundation established cloud financial management as a governance discipline. ARGM builds on this foundation by treating cost governance as a maturity requirement for agentic operations specifically. Token costs, compute spend, and model selection directly affect whether agentic AI operations are sustainable. An organisation running agents without cost visibility is not governed, regardless of its security posture. ARGM's contribution is not inventing cost governance — it is recognising that agentic operations introduce cost dynamics (per-token billing, model routing decisions, autonomous compute consumption) that require governance tailored to the agentic context.

### Why Self-Monitoring at Level 6?

Governance documents enforced solely by prompt-based instruction are soft constraints. Models can ignore, de-prioritise, or misinterpret them. Level 6 moves governance enforcement from semantic interpretation to automated verification: lint hooks, drift detection, health reporting. The framework governs itself.

### Why Directives Rather Than Pillars?

The governance dimensions in ARGM are not pillars of equal weight to be balanced. They are directives with a conflict resolution order. When D0 (Data Protection) conflicts with D3 (Value Alignment), D0 wins without exception. No judgement call, no context exception, no runtime override.

The directive framing borrows from embedded systems governance and military doctrine: rules that must be inviolable to be functional. A pillar can be deprioritised. A directive cannot. Organisations that treat governance as a set of balanced pillars produce frameworks that erode under pressure. Organisations that treat governance as an ordered set of directives produce frameworks that hold.

The directives are numbered D0–D6 so the number directly encodes conflict resolution priority. D0 has highest priority. D6 has lowest. Within Tier 1, the order is unconditional. Within Tier 2, the recommended order is D3 > D4 > D5 > D6, but organisations may reorder with documented rationale. Tier 2 never overrides Tier 1.

---

## 4. Level Definitions

### Level 0 - Ungoverned

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

### Level 1 - Instructed

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
- Conflict resolution order not yet defined — Level 1 acknowledges that D0 (Data Protection) takes unconditional precedence; full directive hierarchy established at Level 3

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
3. What happens when an agent encounters conflicting instructions? Is there a documented conflict resolution order? Even at Level 1, D0 (Data Protection) must be unconditional — is this explicit in the governance document?
4. How do you manage governance document size as they grow? What is your context window strategy?
5. Demonstrate an agent completing a task end-to-end and trace which governance rules applied at each decision point.

---

### Level 2 - Secured

**Definition:** D1 (Security Controls) enforced on top of instructional foundation. Credential hygiene, injection defence, CORS policy, rate limiting, and pre-commit scanning enforced as non-negotiable requirements. Security controls exist as both documented requirements and enforced technical controls, not solely prompt-based. D0 (Data Protection) active from this level. Agent operates securely but without business context or directive hierarchy beyond D0 and D1.

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
5. Document the full directive conflict resolution order (D0 > D1 > D2 > D3 > D4 > D5 > D6) and declare it unconditional with no runtime exceptions

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

### Level 3 - Aligned

**Definition:** D2 (Autonomous Operation), D3 (Revenue Alignment), D4 (Infrastructure Portability), D5 (Operational Efficiency), and D6 (Delivery Standards) activated. Value alignment tiers map agent effort to organisational priorities. Scope boundaries prevent agents building outside their mandate. Cost constraints cap token spend. Delivery standards enforce output quality. The full directive conflict resolution order (D0 > D1 > D2 > D3 > D4 > D5 > D6) is documented and declared unconditional at this level.

**Observable Evidence:**
- **Value alignment tiers:** Documented hierarchy of work priorities (primary, secondary, enablement, reject) governing proactive vs reactive build decisions
- **Scope boundaries:** Explicit list of permitted builds, approval-required builds, and prohibited builds regardless of request
- **Cost governance:** Token usage tracked per agent, per task, per period. Budget thresholds with alerts. Evidence of at least one cost-related decision (pausing a task, choosing a smaller model, deferring non-priority work)
- **Delivery standards:** Output quality gates: branded templates, executive summary length limits, turnaround SLAs, no raw script output without formatted wrapper
- **Conflict resolution order:** D0 > D1 > D2 > D3 > D4 > D5 > D6 — documented, declared unconditional, applied to all directive conflicts. D0 (Data Protection) wins without exception.
- **Agent task classification:** Each agent task tagged by value tier before execution begins
- **Dry-run defaults:** Write operations default to dry-run mode unless explicitly scheduled for live execution
- **Destructive operation prohibition:** Agents cannot delete records, objects, or infrastructure without explicit human authorisation and logging

**Progression Criteria (to reach Level 4):**
1. Unify all active directives (D0, D1, D2, D3, D4, D5, D6) into a single governance document encoding each directive's scope, requirements, and conflict resolution position
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

### Level 4 - Governed

**Definition:** All seven prime directives (D0–D6) active and integrated. Security, business, delivery, and autonomous operation controls operate as a single directive-governed system. D2 (Autonomous Operation) fully active: turn limits, exit conditions, overnight safety rules. Conflict resolution order unconditional and enforced at the framework level, not reliant on model compliance. D0 (Data Protection) enforced by automated controls. The framework constitutes a complete governance system auditable end-to-end.

**Observable Evidence:**
- **Unified governance framework:** Single document or document set encoding all prime directives D0–D6: data protection, security controls, autonomous operation, revenue alignment, infrastructure portability, operational efficiency, delivery standards, and conflict resolution order
- **Directive architecture:** Governance organised as named, numbered directives D0–D6 with explicit conflict resolution order — not ad hoc rules scattered across files
- **Autonomous operation controls:**
  - Maximum agent turn limits per task (e.g., 15 turns for overnight tasks)
  - Clean exit conditions when limits reached
  - Dry-run default for all scheduled/unattended operations
  - No destructive operations without explicit human scheduling
  - No external API calls or email sends without explicit authorisation flag
  - Full logging of every write operation: timestamp, operation, record ID, outcome
  - No PII in logs or stdout: log only operation name, record count, status code, error code
- **Third-party isolation:** No client names, tenant IDs, PII, or commercial pricing in repositories, logs, or agent output. Placeholder syntax enforced (`{{CLIENT_NAME}}`, `{{TENANT_ID}}`)
- **Conflict resolution order:** D0 > D1 > D2 > D3 > D4 > D5 > D6 — documented as unconditional. D0 (Data Protection) wins without exception. No runtime override permitted.
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
1. Show me your complete governance framework. Identify each prime directive (D0–D6), state its scope, and demonstrate how directive conflicts resolve in practice.
2. Demonstrate an overnight or unattended agent task. Show turn limits, exit conditions, dry-run defaults, and logging in operation.
3. How do you enforce third-party data isolation? Show a recent agent output and confirm no client-identifying data in version control or logs.
4. Is this framework applied consistently across all AI agents? Show evidence for at least two different agents.
5. When was the last governance review? Show what changed, why, and who approved.

---

### Level 5 - Autonomous

**Definition:** The governance framework governs itself. Self-monitoring layer detects governance drift, reports on compliance health, and enforces governance document integrity without manual intervention. Lint hooks validate governance files on every commit. Automated health reports generated on a defined schedule. Changes to governance documents trigger alerts and require review. Continuous assurance achieved: an assessor can verify compliance at any point without triggering a manual audit.

**Observable Evidence:**
- **Governance drift detection:** Automated mechanism compares current governance documents against known-good baseline. Deviation triggers alert. Implementation options:
  - Git-based: hash comparison against pinned baseline commit
  - CI/CD: pipeline stage validating governance file structure and content on every push
  - Scheduled: cron or equivalent auditing governance state at defined intervals
- **Lint hooks on governance files:** Pre-commit or CI hooks that:
  - Validate governance document structure (required sections present)
  - Check for prohibited content (hardcoded secrets, client names, tenant IDs)
  - Verify directive numbering (D0–D6) and conflict resolution order (D0 > D1 > D2 > D3 > D4 > D5 > D6) are intact and unconditional
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

## 5. Prime Directive Architecture (D0–D6)

At Level 4 and above, governance is organised as seven numbered prime directives. Each directive has defined scope and a fixed conflict resolution position. This is the reference architecture. Organisations adapt directive scope to their context but must preserve the conflict resolution order — it is the architecture's operating principle.

| Directive | Name | Scope |
|-----------|------|-------|
| D0 | Data Protection | Client data isolation, PII handling, retention limits, placeholder enforcement |
| D1 | Security Controls | Secrets management, CORS, rate limiting, injection defence, pre-commit scanning |
| D2 | Autonomous Operation | Turn limits, dry-run defaults, destructive operation prohibition, overnight safety, logging |
| D3 | Revenue Alignment | Value tiers, scope boundaries, proactive vs reactive build decisions |
| D4 | Infrastructure Portability | Tenant strategy, SKU selection, cost targets, auth architecture |
| D5 | Operational Efficiency | Automation targets, JSON output schemas, template consumption patterns |
| D6 | Delivery Standards | Output quality, branding, turnaround SLAs, formatted wrapper requirements |

**Conflict Resolution Order:** D0 > D1 > D2 > D3 > D4 > D5 > D6

D0 wins unconditionally — no client data, PII, or confidential pricing leaves the boundary in any scenario. D1 (Security Controls) ranks second because a security failure causes irreversible harm and is non-negotiable from Level 2 onward; it does not compete with business directives, it precedes them. D2 (Autonomous Operation) wins over all business directives — an agent operating without supervision must not take destructive or irreversible actions regardless of business priority. D3 overrides D4, D5, and D6 — revenue-generating work takes precedence over infrastructure choices, efficiency optimisation, and delivery formatting.
