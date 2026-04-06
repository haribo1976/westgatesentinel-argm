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

### Level 0 — Ungoverned

**Definition:** No runtime governance exists. Agents operate on default model behaviour with whatever permissions the human operator has. No explicit rules, no scope control, no security controls, no awareness of what agents are even running.

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
- Credential sprawl — agents accumulate permissions over time, never revoked
- Shadow agents — team members adopt AI coding tools individually with no organisational awareness, creating an ungoverned fleet
- Irreversible damage from defaults — agents execute destructive operations because nothing told them not to

**Assessment Questions:**
1. Show me a complete inventory of AI agents in your environment, including which systems each agent accesses. [CRITICAL]
2. Where are the documented rules governing what your AI agents are permitted and prohibited from doing?
3. Show me the last five commits made by or with an AI agent. Can you trace what instructions governed each commit?
4. How are credentials managed for AI agent access? Show me where API keys are stored. [CRITICAL]
5. If an agent made an irreversible change to a production system right now, what mechanism would prevent or detect it?

**Failure Scenario:** A 12-person development team adopted three different AI coding assistants over a four-month period. No central register existed. When the security team ran a credential audit, they discovered that one assistant had been configured with a personal access token granting write access to the production Kubernetes cluster. The token had been active for 11 weeks. No one could confirm whether the agent had ever issued commands against production, because no logging existed. The token was revoked, but the team spent two weeks auditing production state to confirm nothing had been modified.

---

### Level 1 — Instructed

**Definition:** Governance documents exist and define coding standards, validation gates, context management rules, and behavioural expectations. Agent behaviour is guided by explicit instructions, but enforcement depends entirely on model compliance — there are no technical controls verifying adherence. D0 (Data Protection) is acknowledged as a principle in the governance document. It is not yet enforced by technical controls.

**Observable Evidence:**
- CLAUDE.md, AGENTS.md, or equivalent governance file exists in each repository where agents operate
- Coding conventions documented: file naming, commit format, linting rules, output schemas
- Validation gates defined: what must be true before an agent commits code or creates files
- Context management rules present: how agents handle long conversations, what to include in prompts
- Basic file structure discipline: agents know where to write and where not to
- "Do not" list: prohibited actions or files the agent must not modify
- D0 (Data Protection) documented as a governing principle — the governance file states that client data, PII, and confidential information must be protected
- No technical enforcement of D0 (no automated scanning, no placeholder syntax enforcement, no isolation controls)
- No security-specific controls (no injection defence, no credential hygiene, no CORS policy)
- No business priority alignment
- No cost tracking or token budget constraints

**Progression Criteria (to reach Level 2):**
1. Implement credential hygiene: all secrets in environment variables, .env in .gitignore, pre-commit scanning for leaked secrets
2. Define and enforce a CORS policy for any agent-accessible web endpoints
3. Implement rate limiting on all authentication endpoints
4. Establish injection defence measures (input validation, output sanitisation)
5. Enforce D0 (Data Protection) with technical controls: automated scanning for client names, PII patterns, and confidential data in repositories and agent output

**Common Failure Modes:**
- Instruction drift — governance documents written once, never updated as agent capabilities change
- Compliance theatre — agents instructed to follow rules but no mechanism verifies they do
- Overloaded system prompts — governance documents grow past context window limits, causing the model to de-prioritise critical rules buried at the bottom
- False confidence — the presence of a CLAUDE.md creates an assumption of governance that does not exist in practice

**Assessment Questions:**
1. Show me the governance documents that instruct your AI agents. When were they last reviewed and by whom? [CRITICAL]
2. How do you verify that agents actually follow instructions? Show me evidence of a recent violation and how it was detected.
3. Where does your governance document acknowledge D0 (Data Protection)? What specific protections does it require? How would you know if an agent violated them today?
4. How do you manage governance document size as they grow? What is your context window strategy?
5. Demonstrate an agent completing a task end-to-end and trace which governance rules applied at each decision point.

**Failure Scenario:** An engineering team deployed agents with CLAUDE.md files across 14 repositories, each containing a clear rule: "No client names in commits or code comments." Six months later, an internal audit sampled 200 agent-assisted commits and found 47 containing client identifiers — company names in variable strings, project codenames in comments, one commit message referencing a specific acquisition target by name. The governance document had been correct the entire time. No mechanism had ever checked whether the agent was following it.

---

### Level 2 — Secured

**Definition:** D0 (Data Protection) and D1 (Security Controls) enforced by technical controls, not solely by prompt-based instruction. Credential hygiene, injection defence, CORS policy, rate limiting, pre-commit scanning, and data protection isolation are implemented as automated, verifiable controls. The agent operates securely but without business context, autonomous operation controls, or a directive hierarchy beyond D0 and D1.

**Observable Evidence:**
- **D0 — Data Protection enforcement:**
  - Automated scanning of repositories, logs, and agent output for client names, PII patterns, tenant IDs, and confidential pricing
  - Placeholder syntax enforced for client-identifying data (`{{CLIENT_NAME}}`, `{{TENANT_ID}}`)
  - Pre-commit hooks or CI stages that reject commits containing data protection violations
  - Evidence of at least one D0 violation caught and blocked by automated controls
- **D1 — Secrets management:** All API keys, tokens, credentials in environment variables or secret managers. .env and .dev.vars in .gitignore. Scripts read secrets from env vars, not parameters.
- **D1 — Pre-commit scanning:** Git hooks or CI stages scan for: `sk_`, `pk_`, `eyJ`, `API_KEY=`, `SECRET=`, `Bearer`, `client_secret=`, `PRIVATE_KEY`, `Authorization:`
- **D1 — CORS policy:** No `Access-Control-Allow-Origin: *` in production. Specific trusted origins whitelisted.
- **D1 — Rate limiting:** All authentication endpoints rate-limited (default: 5 attempts/minute/IP). Breach logging and alerting configured.
- **D1 — Injection defence:** Input validation on all agent-facing interfaces. Output sanitisation for agent-generated content rendered in web contexts.
- **D1 — Branch protection:** Main/production branches require pull request review. Agents cannot push directly to protected branches.
- **D1 — Least privilege:** Agent service accounts have minimum required permissions. No shared admin credentials.
- **D1 — Rotation policy:** Documented credential rotation process. Evidence of at least one rotation in the past 90 days.

**Progression Criteria (to reach Level 3):**
1. Implement turn limits for agent sessions — define maximum turns per task with clean exit conditions
2. Establish dry-run defaults for all write operations in unattended or scheduled contexts
3. Prohibit destructive operations (delete, drop, force-push) without explicit human authorisation
4. Implement write logging: every file write, API call, and state change logged with timestamp and outcome
5. Ensure no PII appears in logs — log operation name, record count, status code, error code only

**Common Failure Modes:**
- Security as ceiling — treating security as the end goal rather than a foundation for further governance
- Tool-specific silos — controls applied to one agent but not others in the same environment
- Alert fatigue — false positives from pre-commit scans train developers to bypass or ignore them
- D0 without teeth — data protection documented but scanning only covers obvious patterns, missing encoded or abbreviated client references

**Assessment Questions:**
1. Show me your pre-commit scanning configuration. When was it last triggered, and what was the outcome? [CRITICAL]
2. Walk me through how an agent accesses a production system. What credentials, where stored, when last rotated?
3. If I submitted a prompt containing a SQL injection payload, what would happen? Show me the defence.
4. Show me evidence that D0 (Data Protection) is enforced by technical controls, not just documented. When was the last violation caught automatically? [CRITICAL]
5. What was the last security incident or near-miss involving an AI agent? How was it detected and resolved?

**Failure Scenario:** A consultancy implemented robust D1 security controls — pre-commit scanning, credential rotation, branch protection — but treated D0 as a Level 1 concern: documented but not enforced. Their CLAUDE.md said "never include client names." Their pre-commit hooks scanned for secrets but not for client identifiers. Over three months, agents committed 23 files containing client company names in code comments and test fixtures. The exposure was discovered when a client's legal team reviewed a public repository fork and found their company name in a mock data file.

---

### Level 3 — Controlled

**Definition:** D2 (Autonomous Operation) enforced. Agents operate within defined boundaries for unsupervised execution: turn limits cap runaway sessions, dry-run mode is the default for write operations, destructive actions are prohibited without human authorisation, and all write operations are logged. This level exists because autonomous operation safety is a distinct concern from business alignment — an organisation can and should demonstrate that agents operate safely before layering on business directives.

This level was previously bundled into old Level 3 (v1.1) alongside business directives D3–D6. Separating it recognises that controlling *how* an agent operates is a prerequisite to controlling *what* it works on.

**Observable Evidence:**
- **Turn limits:** Maximum agent turns per task defined and enforced (e.g., 15 turns for standard tasks, 30 for complex). Agent exits cleanly when limit reached, preserving work state.
- **Dry-run defaults:** All write operations in scheduled or unattended contexts default to dry-run mode. Live execution requires explicit flag or human scheduling.
- **Destructive operation prohibition:** Agents cannot delete records, drop tables, force-push branches, or destroy infrastructure without explicit human authorisation. The prohibition is enforced by tooling (hook, wrapper, or permission boundary), not solely by prompt instruction.
- **Clean exit conditions:** When an agent reaches a turn limit, encounters an unrecoverable error, or detects it is outside scope, it exits with a structured status report — not a silent failure or an abandoned partial state.
- **Write logging:** Every file write, API call, database mutation, and infrastructure change logged with: timestamp, operation type, target identifier, outcome (success/failure), and error code if applicable.
- **No PII in logs:** Logs contain operation name, record count, status code, and error code. No client names, email addresses, tenant IDs, or other personally identifiable information.
- **Overnight/unattended safety:** Scheduled agent runs have additional constraints: reduced turn limits, no external API calls without pre-authorisation, mandatory dry-run for first execution of any new task type.

**Progression Criteria (to reach Level 4):**
1. Define a business value classification mechanism: how the organisation categorises work as primary, secondary, enablement, or requiring approval
2. Implement cost governance: token budgets, model selection policy, cost attribution, escalation thresholds
3. Activate D3–D6 (Value Alignment, Infrastructure Governance, Operational Efficiency, Delivery Standards) with documented scope for each
4. Document the full conflict resolution order: Tier 1 (D0 > D1 > D2, unconditional) and Tier 2 (configurable, default D3 > D4 > D5 > D6)
5. Establish scope boundaries: what agents build proactively, what requires approval, what is prohibited

**Common Failure Modes:**
- Turn limits without exit handling — agent hits the limit and drops state silently, requiring manual recovery
- Dry-run theatre — dry-run mode exists but is routinely overridden because "we know this one is safe"
- Log volume without log review — terabytes of write logs that no one reads or alerts on
- Overnight drift — scheduled agents run within limits but accumulate small deviations over weeks that only surface when a human reviews the output
- Prohibition gaps — destructive operations blocked in the primary tool but available through a secondary agent or direct CLI access
- PII leakage in error messages — logs are clean but unhandled exceptions dump full payloads including client data

**Assessment Questions:**
1. Show me your turn limit configuration. What happens when an agent reaches the limit? Walk me through the exit state. [CRITICAL]
2. Demonstrate a dry-run execution. How does an agent distinguish dry-run from live mode? Who authorises the transition?
3. Show me your write logs for the past 48 hours. Confirm no PII is present. [CRITICAL]
4. What destructive operations can an agent perform? Show me the enforcement mechanism that prevents unauthorised destruction.
5. Describe your overnight agent safety rules. What additional constraints apply to unattended execution?

**Failure Scenario:** A platform team configured agents for overnight infrastructure maintenance with a generous 200-turn limit — "enough headroom for complex tasks." No one reviewed what constituted a reasonable turn count for their workloads. On the third night, an agent processing a backlog of infrastructure tickets consumed all 200 turns on a single misconfigured task, making 214 API calls to a cloud provider. The calls were non-destructive (read-only queries in a retry loop against a rate-limited endpoint), but the API bill for that single night exceeded the team's monthly agent budget. The agent exited cleanly at turn 200 with a status report indicating the task was incomplete. The underlying issue was a malformed resource identifier that would have been caught on turn 3 with basic input validation.

---

### Level 4 — Aligned

**Definition:** D3 (Value Alignment), D4 (Infrastructure Governance), D5 (Operational Efficiency), and D6 (Delivery Standards) active alongside Tier 1 directives. Business context enters the governance framework. Agents know not just how to operate safely, but what work matters, how to allocate resources, and what quality standards apply. The full two-tier conflict resolution order is documented: Tier 1 (D0 > D1 > D2) unconditional, Tier 2 (default D3 > D4 > D5 > D6) configurable with documented rationale.

This level was split from v1.1 Level 3, which attempted to activate autonomous operation controls and business directives simultaneously. The split recognises that operational safety (Level 3) and business alignment (Level 4) are distinct governance concerns that benefit from separate maturity stages.

**Observable Evidence:**

- **Business value classification mechanism:** A documented, repeatable process for classifying agent work:
  - Is this task within the defined scope? If no → requires approval or reject.
  - Is it revenue-critical or mission-critical? If yes → **Primary**.
  - Does it directly support primary work? If yes → **Secondary**.
  - Does it maintain governance, infrastructure, or operational capability? If yes → **Enablement**.
  - None of the above? → **Requires approval or reject**.
  - The terminology is sector-configurable: "revenue-critical" for consultancy, "mission outcome" for public sector, "patient safety" for healthcare, "community benefit" for open-source.

- **Cost governance control set:**
  - *Model selection policy:* Documented criteria for when to use which model tier (e.g., haiku for lookups, sonnet for standard work, opus for architecture decisions). Policy reviewed when new models are released.
  - *Budget allocation:* Token and compute budgets defined per-agent, per-project, or per-period — whichever granularity matches the organisation's cost structure.
  - *Cost attribution:* Agent costs mapped to value tiers. Primary work may consume more; enablement work should be efficient. The mapping exists so cost conversations reference business value, not raw token counts.
  - *Escalation thresholds:* Alerts configured at 50%, 80%, and 100% of budget. The 50% alert is informational. The 80% alert requires acknowledgement. The 100% alert pauses non-primary work or requires explicit override.
  - *Monthly cost review:* Trend analysis comparing actual spend against budget, with variance explanation. Not a rubber stamp — evidence of at least one decision influenced by cost data.

- **Tier 2 directive ordering:** The organisation's chosen order for D3–D6 is documented with rationale. The default order (D3 > D4 > D5 > D6) may be reordered — a hospital might place D4 (Infrastructure Governance) above D3 (Value Alignment) because system reliability is a patient safety concern. The rationale must be explicit and approved.

- **Full conflict resolution order:** Tier 1 (D0 > D1 > D2) unconditional, no break-glass, no exceptions. Tier 2 (configurable, documented) applies to business directive conflicts. Tier 2 never overrides Tier 1.

- **Scope boundaries:** Explicit list of what agents build proactively, what requires human approval, and what is prohibited regardless of request.

- **Delivery standards:** Output quality gates defined and enforced: branded templates, executive summary requirements, turnaround expectations, formatted output wrappers. Raw script output without context is not a deliverable.

- **Agent task classification:** Each agent task tagged by value tier before execution begins. Classification is auditable.

**Progression Criteria (to reach Level 5):**
1. Unify all active directives (D0–D6) into a single governance document or integrated document set
2. Implement cross-agent consistency: same governance framework applied to all agents, not just the primary one
3. Establish governance review cadence (quarterly minimum) with documented changes, rationale, and approval
4. Implement third-party data isolation verification as an automated control
5. Achieve end-to-end auditability: an assessor can trace any agent action back to the directive that governed it

**Common Failure Modes:**
- Cost governance as checkbox — budgets defined but never reviewed, thresholds set but alerts routed to an unmonitored channel
- Value classification paralysis — agents spend more effort classifying work than performing it
- Scope rigidity — scope boundaries so narrow that legitimate secondary work is rejected, forcing humans to do what agents could
- Tier 2 ordering without rationale — the organisation picks a directive order but cannot explain why D4 outranks D5 in their context
- Delivery standards as formatting — quality gates that check template compliance but not content accuracy or completeness
- Model selection policy as cost minimisation — always routing to the cheapest model regardless of task complexity, producing low-quality output that requires rework

**Assessment Questions:**
1. Show me your business value classification mechanism. Walk me through how a new task gets classified. Who reviews edge cases? [CRITICAL]
2. Show me your cost governance controls. What is your current month's spend against budget? When was the last cost-influenced decision?
3. What is your Tier 2 directive ordering and why? Give me a scenario where two Tier 2 directives conflict and show me how it resolves.
4. Show me your model selection policy. How do you decide which model tier to use for a given task?
5. Walk me through a recent deliverable. Which quality gates did it pass? Show me evidence, not policy. [CRITICAL]

**Failure Scenario:** A mid-size consultancy reached Level 4 by defining cost governance controls that looked thorough on paper: per-project budgets, escalation thresholds at 50/80/100%, monthly review meetings. In practice, the 50% and 80% alerts were sent to a shared Slack channel that averaged 400 messages per day. No one noticed them. The 100% alert paused agent work as designed, but the team had configured an auto-override ("resume with manager approval") that a team lead rubber-stamped without reviewing the underlying spend. After six months, the quarterly business review revealed that agent compute costs had grown 340% while the volume of primary-tier work had grown only 15%. Most of the spend was on secondary and enablement tasks that could have been deferred. The cost governance framework existed. The governance behaviour did not.

---

### Level 5 — Governed

**Definition:** All directives (D0–D6) integrated into a unified governance system, enforced consistently across every agent in the environment. The framework is no longer a collection of controls bolted onto individual tools — it is an organisational capability. Cross-agent consistency is verified. A governance review cadence ensures the framework evolves with the organisation. A break-glass exception mechanism for Tier 2 directives provides controlled flexibility without undermining governance integrity.

**Observable Evidence:**

- **Unified governance framework:** Single document or integrated document set encoding all directives D0–D6 with scope definitions, enforcement mechanisms, and conflict resolution order. Not scattered rules across repositories — a coherent system.

- **Cross-agent consistency:** Evidence that every agent in the environment (primary coding assistant, secondary tools, local models, CI/CD agents) operates under the same governance framework. Consistency verified by periodic audit, not assumed.

- **Governance review cadence:** Quarterly minimum. Each review produces documented evidence: what was reviewed, what changed, what was ratified without change, who approved. Reviews that produce no changes document why — "reviewed, no changes required" with rationale is valid; an empty review log is not.

- **Break-glass exception mechanism (Tier 2 only):**
  - A named, accountable individual authorises the exception. Not a role — a person, by name, in the log.
  - Time-bounded: 72 hours maximum. The exception expires automatically. Renewal requires a new authorisation.
  - Immutable log entry: the exception, its justification, the authorising individual, the start time, and the expiry time are recorded in a log that cannot be retroactively modified.
  - Post-incident review within 5 business days: what happened, whether the exception was justified, whether the governance framework should be updated to prevent recurrence.
  - **Cannot override Tier 1 (D0–D2) under any circumstances.** There is no break-glass for safety directives. If someone claims to need a D0/D1/D2 exception, the answer is: fix the underlying problem. The framework does not bend here.

- **Third-party data isolation:** Automated verification that no client names, tenant IDs, PII, or confidential pricing appear in repositories, logs, or agent output. Placeholder syntax enforced and scanned.

- **End-to-end auditability:** An assessor can select any agent action from the past quarter and trace it back to: the task classification, the governing directives, the conflict resolution order applied, and the quality gates passed.

**Progression Criteria (to reach Level 6):**
1. Implement automated governance drift detection: hash-based or structural comparison against a known-good baseline
2. Deploy lint hooks or CI/CD checks validating governance file integrity on every commit
3. Establish automated health reporting: machine-generated compliance reports without manual intervention
4. Designate a governance owner with authority to modify monitoring rules, subject to change control
5. Arrange external review capability: someone outside the team that built the framework can assess governance effectiveness

**Common Failure Modes:**
- Framework as shelfware — a comprehensive governance document that exists, was approved, and is operationally ignored
- Break-glass abuse — exceptions become routine, with the same justification used repeatedly without triggering a framework update
- Cross-agent blind spots — the primary agent is fully governed but a team member's local model or a CI/CD bot operates outside the framework
- Review theatre — quarterly reviews occur on schedule, produce minutes, and change nothing meaningful for years

**Assessment Questions:**
1. Show me your complete governance framework. Identify each directive (D0–D6), state its scope, and demonstrate how conflicts resolve in practice. [CRITICAL]
2. Show me evidence of cross-agent consistency. Pick two different agents in your environment and demonstrate they operate under the same governance.
3. Walk me through your most recent governance review. What changed? If nothing changed, why not?
4. Show me a break-glass exception from the past year. Who authorised it, what was the justification, and what did the post-incident review conclude? If no exceptions have occurred, how do you know the mechanism works?
5. Select a random agent action from last month. Trace it end-to-end: task classification, governing directive, conflict resolution, quality gate. [CRITICAL]

**Failure Scenario:** A financial services firm built a governance framework that scored well on every assessment dimension. Directives were documented. Conflict resolution was defined. Reviews were quarterly. The framework was also 47 pages long and lived in a Confluence space that agents could not read. The operational reality was a 900-token CLAUDE.md that contained a subset of the rules, paraphrased by a developer who had skimmed the full document. Over 18 months, the CLAUDE.md drifted from the canonical framework. Three directives were absent entirely. The conflict resolution order had been simplified to "security first, then use your judgment." The quarterly reviews reviewed the Confluence document, not the CLAUDE.md. The governance framework was comprehensive, approved, and entirely disconnected from the agents it was supposed to govern.

---

### Level 6 — Autonomous

**Definition:** The governance framework governs itself. Automated monitoring detects governance drift, reports compliance health, and enforces document integrity without manual intervention. The regress problem — "what governs the governor?" — is addressed through a three-layer assurance model that prevents any single layer from being the sole guarantor of governance integrity.

Level 6 is not a destination. It is a sustained capability. Organisations do not achieve Level 6 and stop. They maintain it, or they regress.

**Observable Evidence:**

- **Governance drift detection:** Automated comparison of current governance documents against a known-good baseline. Deviation triggers alert. Implementation options include:
  - Git-based hash comparison against a pinned baseline commit
  - CI/CD pipeline stage validating governance file structure and required content on every push
  - Scheduled audit comparing governance state against baseline at defined intervals

- **Lint hooks on governance files:** Pre-commit or CI hooks that validate governance document structure (required sections present), check for prohibited content (hardcoded secrets, client names, tenant IDs), verify directive numbering and conflict resolution order are intact, and flag weakening of non-negotiable controls.

- **Automated health reporting:** Machine-generated compliance reports at defined intervals (weekly minimum) covering governance document currency, security control compliance, business alignment adherence, autonomous operation compliance, and cost governance status. Reports are generated without human initiation.

- **Change control on governance:** Modifications to governance documents require pull request review from the designated governance owner. Force pushes to governance files are blocked.

- **Governance versioning:** Documents carry semantic version numbers. Changes tracked in changelog with rationale, reviewer, and approval date.

- **Three-layer assurance model (the regress solution):**

  The question "what governs the governor?" has no perfect theoretical answer — it is turtles all the way down. ARGM's practical answer is three independent layers, each compensating for the blind spots of the others.

  1. **Technical layer:** Hash-based drift detection, lint hooks, CI validation, automated health reporting. This layer catches mechanical drift — files changed, sections removed, structure broken. It cannot assess whether the governance framework is *effective*, only whether it is *intact*.

  2. **Organisational layer:** A designated governance owner — a named individual, not a committee — with authority to modify monitoring rules, subject to change control. The governance owner is not the monitoring system. They can override a false positive, update detection rules when the framework legitimately evolves, and make judgment calls that automated checks cannot. The governance owner is subject to the same change control as everyone else: their modifications are logged, reviewed, and auditable.

  3. **External layer:** Periodic review (quarterly minimum) by someone outside the team that built the framework. This can be an internal team from a different department, an external auditor, a consultant, or a peer organisation. The external reviewer's mandate is specific: assess whether the monitoring is actually catching real drift, not just confirming green dashboards. Are the lint rules testing meaningful properties? Has the baseline drifted so far from the original intent that hash comparisons are validating the wrong thing? Would a genuine governance failure be detected, or would it pass every automated check?

  No single layer is sufficient. The technical layer catches drift but cannot judge effectiveness. The organisational layer provides judgment but is a single point of human failure. The external layer provides independence but is periodic, not continuous. Together, they provide assurance that is stronger than any individual mechanism.

**Common Failure Modes:**
- Dashboard green, governance red — automated checks pass because they test structure, not substance. The directive numbering is intact but the directive content has been hollowed out.
- Governance owner as bottleneck — a single individual whose availability gates all governance changes, creating pressure to bypass the process
- External review as compliance exercise — the quarterly external review becomes a checkbox. The reviewer asks the same questions, gets the same answers, signs the same attestation. Actual governance effectiveness is never tested.
- Baseline drift — the "known-good baseline" is updated so frequently that it tracks current state rather than intended state. Drift detection compares today against yesterday, not against the governance design.
- Monitoring tool monoculture — all three layers rely on the same CI/CD platform. When that platform has an outage or misconfiguration, all layers fail simultaneously.

**Assessment Questions:**
1. Show me your governance drift detection. Trigger a deliberate change to a governance file and demonstrate the detection mechanism firing. [CRITICAL]
2. Who is your designated governance owner? Show me their most recent governance modification, including the change control log.
3. Show me your most recent external governance review. What did the reviewer assess? What was their finding? Did anything change as a result?
4. Demonstrate that your three assurance layers are genuinely independent. If the CI/CD platform went down, what would still be monitoring governance?
5. Show me an automated health report from last week. For each metric, explain what a failure would look like and how it would be escalated. [CRITICAL]

**Failure Scenario:** A technology company implemented Level 6 governance with visible commitment: drift detection via CI, a governance owner in the platform team, and quarterly reviews by an external consultant. After 18 months, an internal incident revealed that the drift detection had been validating governance file checksums against a baseline that was updated automatically on every merge to main. The system was comparing current governance against last week's governance, not against the approved governance design. A gradual weakening of D2 controls — turn limits relaxed from 15 to 50 to "no limit for trusted tasks" — passed every automated check because each incremental change became the new baseline before the next check ran. The governance owner had approved each change individually without tracking the cumulative effect. The external consultant reviewed the drift detection dashboard, confirmed it showed no alerts, and signed off. Three layers of assurance, none of which caught a directional change that would have been obvious to anyone reading the D2 section from 12 months prior alongside the current version.

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
