# ARGM Evidence Checklist

**Version:** 1.1
**Licence:** CC-BY-SA 4.0

Use this checklist during assessment. Tick each item where evidence has been observed. A level is achieved when all items are ticked for that level and all preceding levels.

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
- [ ] D0 (Data Protection) acknowledged as unconditional even if full hierarchy not yet defined

---

## Level 2 — Secured

**Secrets Management**
- [ ] All API keys, tokens, credentials in environment variables or secret managers
- [ ] .env and .dev.vars in .gitignore
- [ ] Scripts read secrets from env vars, not parameters

**Pre-commit Scanning**
- [ ] Git hooks or CI stages scan for: `sk_`, `pk_`, `eyJ`, `API_KEY=`, `SECRET=`, `Bearer`, `client_secret=`, `PRIVATE_KEY`, `Authorization:`

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

## Level 3 — Aligned

**Value Alignment**
- [ ] Documented hierarchy of work priorities (primary, secondary, enablement, reject)
- [ ] Scope boundaries: explicit list of permitted builds, approval-required builds, and prohibited builds

**Cost Governance**
- [ ] Token usage tracked per agent, per task, per period
- [ ] Budget thresholds with alerts configured
- [ ] Evidence of at least one cost-related decision

**Delivery Standards**
- [ ] Output quality gates defined: branded templates, executive summary length limits, turnaround SLAs
- [ ] No raw script output without formatted wrapper

**Conflict Resolution**
- [ ] D0 > D1 > D2 > D3 > D4 > D5 > D6 — documented, declared unconditional
- [ ] Agent task classification in use: each task tagged by value tier before execution

**Autonomous Operation (initial)**
- [ ] Dry-run defaults: write operations default to dry-run unless explicitly scheduled
- [ ] Destructive operation prohibition: no deletions without explicit human authorisation and logging

---

## Level 4 — Governed

**Unified Framework**
- [ ] Single document or document set encoding all prime directives D0–D6
- [ ] Governance organised as named, numbered directives with explicit conflict resolution order

**Autonomous Operation Controls**
- [ ] Maximum agent turn limits per task defined and enforced
- [ ] Clean exit conditions when limits reached
- [ ] Dry-run default for all scheduled/unattended operations
- [ ] No destructive operations without explicit human scheduling
- [ ] No external API calls or email sends without explicit authorisation flag
- [ ] Full logging of every write operation: timestamp, operation, record ID, outcome
- [ ] No PII in logs or stdout

**Third-party Isolation**
- [ ] No client names, tenant IDs, PII, or commercial pricing in repositories, logs, or agent output
- [ ] Placeholder syntax enforced (`{{CLIENT_NAME}}`, `{{TENANT_ID}}`)

**Governance Review**
- [ ] Evidence of scheduled reviews (quarterly minimum)
- [ ] Documented changes, rationale, and approval

**Cross-agent Consistency**
- [ ] Same governance framework applied to all agents in the environment

---

## Level 5 — Autonomous

**Governance Drift Detection**
- [ ] Automated mechanism compares current governance documents against known-good baseline
- [ ] Deviation triggers alert

**Lint Hooks on Governance Files**
- [ ] Validate governance document structure (required sections present)
- [ ] Check for prohibited content (hardcoded secrets, client names, tenant IDs)
- [ ] Verify directive numbering (D0–D6) and conflict resolution order are intact
- [ ] Flag weakening of security non-negotiables

**Automated Health Reporting**
- [ ] Machine-generated compliance reports at defined intervals (weekly minimum)
- [ ] Reports cover: governance document currency, security control compliance, business alignment adherence, autonomous operation compliance

**Third-party Isolation Verification**
- [ ] Automated scanning of all agent outputs, logs, and repository contents for client-identifying data patterns

**Change Control on Governance**
- [ ] Modifications require pull request review from designated governance owner
- [ ] Force pushes to governance files blocked

**Governance Versioning**
- [ ] Governance documents carry semantic version numbers
- [ ] Changes tracked in changelog with rationale
