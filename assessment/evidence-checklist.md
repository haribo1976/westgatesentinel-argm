# ARGM Evidence Checklist

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

Use this checklist during assessment. Tick each item where evidence has been observed. A level is achieved when all items are ticked for that level and all preceding levels.

Items marked `[CRITICAL]` are non-negotiable. A level cannot be awarded if any critical item is unticked.

---

## Level 0 — Ungoverned (Baseline)

These items represent the absence of governance. Confirm which apply before assessing Level 1.

- [ ] No CLAUDE.md, AGENTS.md, system prompt files, or equivalent governance documents in any repository
- [ ] No .gitignore entries for secrets or environment files (or .env files committed to version control)
- [ ] No branch protection on repositories where agents operate
- [ ] API keys, tokens, or credentials hardcoded in scripts or configuration files
- [ ] No audit trail of agent actions beyond default provider logs
- [ ] No documented scope boundaries for agent permissions
- [ ] Agents have same access as the human operator with no least-privilege separation

---

## Level 1 — Instructed

- [ ] CLAUDE.md, AGENTS.md, or equivalent governance file exists in each repository where agents operate
- [ ] Coding conventions documented: file naming, commit format, linting rules, output schemas
- [ ] Validation gates defined: what must be true before an agent commits code or creates files
- [ ] Context management rules present: how agents handle long conversations, what to include in prompts
- [ ] Basic file structure discipline: agents know where to write and where not to
- [ ] "Do not" list: prohibited actions or files the agent must not modify
- [ ] D0 (Data Protection) acknowledged as highest-priority principle in governance document

---

## Level 2 — Secured

**Secrets Management**
- [ ] All API keys, tokens, credentials in environment variables or secret managers
- [ ] .env and .dev.vars in .gitignore
- [ ] Scripts read secrets from env vars, not parameters

**Pre-commit Scanning**
- [ ] `[CRITICAL]` Git hooks or CI stages scan for: `sk_`, `pk_`, `eyJ`, `API_KEY=`, `SECRET=`, `Bearer`, `client_secret=`, `PRIVATE_KEY`, `Authorization:`
- [ ] `[CRITICAL]` D0 (Data Protection) enforced by technical controls: pre-commit scan for client names/PII, .gitignore for sensitive files

**CORS Policy**
- [ ] No `Access-Control-Allow-Origin: *` in production
- [ ] Specific trusted origins whitelisted
- [ ] Credentials paired with origin restrictions

**Rate Limiting**
- [ ] All authentication endpoints rate-limited (default: 5 attempts/minute/IP)
- [ ] Breach logging and alerting configured

**Injection Defence**
- [ ] Input validation on all agent-facing interfaces
- [ ] Output sanitisation for agent-generated content rendered in web contexts

**Branch Protection**
- [ ] Main/production branches require pull request review
- [ ] Agents cannot push directly to protected branches

**Least Privilege**
- [ ] Agent service accounts have minimum required permissions
- [ ] No shared admin credentials

**Rotation Policy**
- [ ] Documented credential rotation process
- [ ] Evidence of at least one rotation in the past 90 days

---

## Level 3 — Controlled

**Autonomous Operation Controls**
- [ ] `[CRITICAL]` Maximum agent turn limits per task defined and enforced
- [ ] Clean exit conditions when limits reached
- [ ] Dry-run default for all scheduled/unattended operations
- [ ] No destructive operations without explicit human authorisation and logging
- [ ] No external API calls or email sends without explicit authorisation flag
- [ ] Full logging of every write operation: timestamp, operation type, record ID, outcome
- [ ] No PII in logs or stdout
- [ ] Overnight/scheduled task safety rules documented

---

## Level 4 — Aligned

**Value Alignment**
- [ ] Documented hierarchy of work priorities with sector-appropriate terminology
- [ ] Scope boundaries: explicit list of permitted, approval-required, and prohibited builds
- [ ] Decision mechanism for task classification (flowchart, rules, or prompt-based)

**Cost Governance**
- [ ] `[CRITICAL]` Model selection policy documented (when to use which model tier)
- [ ] Budget allocation: per-agent, per-project, or per-period budgets defined
- [ ] Cost attribution: costs mapped to value tiers
- [ ] Escalation thresholds configured (alerts at defined budget percentages)
- [ ] Evidence of at least one cost-influenced decision in the past 90 days
- [ ] Monthly cost review with trend analysis

**Delivery Standards**
- [ ] Output quality gates defined
- [ ] No raw unformatted output without wrapper

**Conflict Resolution**
- [ ] Tier 1 (D0 > D1 > D2) documented as unconditional
- [ ] Tier 2 ordering documented with sector-specific rationale
- [ ] Agent task classification in use: each task tagged by value tier before execution

---

## Level 5 — Governed

**Unified Framework**
- [ ] Single document or document set encoding all directives D0–D6 with tier assignments
- [ ] Governance organised as named, numbered directives with explicit conflict resolution order

**Break-Glass Mechanism**
- [ ] `[CRITICAL]` Break-glass procedure documented for Tier 2 exceptions
- [ ] Named accountable individual required (not role, not team)
- [ ] Time-bounded (72h maximum, non-renewable without fresh approval)
- [ ] Immutable log entry for each break-glass activation
- [ ] Post-incident review within 5 business days
- [ ] Tier 1 (D0–D2) explicitly excluded from break-glass

**Third-party Isolation**
- [ ] No client names, tenant IDs, PII, or commercial pricing in repositories, logs, or output
- [ ] Placeholder syntax enforced

**Governance Review**
- [ ] Evidence of scheduled reviews (quarterly minimum)
- [ ] Documented changes, rationale, and approval

**Cross-agent Consistency**
- [ ] Same governance framework applied to all agents in the environment

---

## Level 6 — Autonomous

**Governance Drift Detection**
- [ ] `[CRITICAL]` Automated mechanism compares governance documents against known-good baseline
- [ ] Baseline updated on each approved governance change
- [ ] Deviation triggers alert

**Lint Hooks on Governance Files**
- [ ] Validate governance document structure (required sections present)
- [ ] Check for prohibited content (secrets, client names, tenant IDs)
- [ ] Verify directive numbering (D0–D6) and tier assignments intact
- [ ] Flag weakening of Tier 1 requirements

**Automated Health Reporting**
- [ ] Machine-generated compliance reports at defined intervals (weekly minimum)
- [ ] Reports cover: governance document currency, security control compliance, cost governance adherence, autonomous operation compliance

**Three-Layer Regress Assurance**
- [ ] Technical layer: integrity checks operational
- [ ] Organisational layer: designated governance owner documented with change control authority
- [ ] `[CRITICAL]` External layer: periodic review (quarterly minimum) by someone outside the governance-building team

**Change Control on Governance**
- [ ] Modifications require pull request review from governance owner
- [ ] Force pushes to governance files blocked

**Governance Versioning**
- [ ] Governance documents carry semantic version numbers
- [ ] Changes tracked in changelog with rationale
