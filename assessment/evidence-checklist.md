# ARGM Observable Evidence Checklist

Use this checklist to verify observable evidence for each level. To achieve a level, ALL evidence items for that level must be demonstrable. Evidence from lower levels must also be intact.

---

## Level 0 — Ungoverned (conditions to exit)

*These are indicators that an organisation is at Level 0. Check these to confirm whether Level 0 conditions exist.*

- [ ] No CLAUDE.md, AGENTS.md, system prompt files, or equivalent governance documents in any repository
- [ ] No .gitignore entries for secrets or environment files (or .env files committed to version control)
- [ ] No branch protection on repositories where agents operate
- [ ] API keys, tokens, or credentials hardcoded in scripts or configuration files
- [ ] No audit trail of agent actions beyond default provider logs
- [ ] No documented scope boundaries for agent permissions
- [ ] Agents have same access as the human operator with no least-privilege separation

*If any item above is checked, the organisation is at Level 0.*

---

## Level 1 — Instructed

*All items must be demonstrable to claim Level 1.*

- [ ] CLAUDE.md, AGENTS.md, or equivalent governance file exists in each repository where agents operate
- [ ] Coding conventions documented: file naming, commit format, linting rules, output schemas
- [ ] Validation gates defined: what must be true before an agent commits code or creates files
- [ ] Context management rules present: how agents handle long conversations, what to include in prompts
- [ ] Basic file structure discipline: agents know where to write and where not to
- [ ] "Do not" list present: prohibited actions or files the agent must not modify

*Note: Level 1 explicitly does NOT require security controls, business alignment, or cost tracking. Their absence is expected at this level.*

---

## Level 2 — Secured

*All items must be demonstrable to claim Level 2. Level 1 evidence must also be intact.*

- [ ] **Secrets management:** All API keys, tokens, credentials in environment variables or secret managers. .env and .dev.vars in .gitignore. Scripts read secrets from env vars, not parameters.
- [ ] **Pre-commit scanning:** Git hooks or CI stages scan for: `sk_`, `pk_`, `eyJ`, `API_KEY=`, `SECRET=`, `Bearer`, `client_secret=`, `PRIVATE_KEY`, `Authorization:`
- [ ] **CORS policy:** No `Access-Control-Allow-Origin: *` in production. Specific trusted origins whitelisted. Credentials paired with origin restrictions.
- [ ] **Rate limiting:** All authentication endpoints rate-limited (default: 5 attempts/minute/IP). Breach logging and alerting configured.
- [ ] **Injection defence:** Input validation on all agent-facing interfaces. Output sanitisation for agent-generated content rendered in web contexts.
- [ ] **Branch protection:** Main/production branches require pull request review. Agents cannot push directly to protected branches.
- [ ] **Least privilege:** Agent service accounts have minimum required permissions. No shared admin credentials.
- [ ] **Rotation policy:** Documented credential rotation process. Evidence of at least one rotation in the past 90 days.

---

## Level 3 — Aligned

*All items must be demonstrable to claim Level 3. Levels 1–2 evidence must also be intact.*

- [ ] **Value alignment tiers:** Documented hierarchy of work priorities (primary, secondary, enablement, reject) governing proactive vs reactive build decisions
- [ ] **Scope boundaries:** Explicit list of permitted builds, approval-required builds, and prohibited builds regardless of request
- [ ] **Cost governance:** Token usage tracked per agent, per task, per period. Budget thresholds with alerts. Evidence of at least one cost-related decision (pausing a task, choosing a smaller model, deferring non-priority work)
- [ ] **Delivery standards:** Output quality gates: branded templates, executive summary length limits, turnaround SLAs, no raw script output without formatted wrapper
- [ ] **Conflict resolution order:** Documented, unconditional priority order for when governance rules conflict
- [ ] **Agent task classification:** Each agent task tagged by value tier before execution begins
- [ ] **Dry-run defaults:** Write operations default to dry-run mode unless explicitly scheduled for live execution
- [ ] **Destructive operation prohibition:** Agents cannot delete records, objects, or infrastructure without explicit human authorisation and logging

---

## Level 4 — Governed

*All items must be demonstrable to claim Level 4. Levels 1–3 evidence must also be intact.*

- [ ] **Unified governance framework:** Single document or document set defining all pillars
- [ ] **Pillar architecture:** Governance organised into named, numbered pillars (not ad hoc rules)
- [ ] **Turn limits:** Maximum agent turn limits per task configured and enforced
- [ ] **Clean exit conditions:** Defined conditions under which an autonomous session terminates
- [ ] **Dry-run default for unattended operations:** All scheduled/unattended operations default to dry-run
- [ ] **No destructive operations without human scheduling:** Explicit authorisation required
- [ ] **No unauthorised external calls:** External API calls and email sends require explicit authorisation flag
- [ ] **Full write logging:** Every write operation logged with timestamp, operation, record ID, outcome
- [ ] **No PII in logs:** Logs contain only operation name, record count, status code, error code
- [ ] **Third-party isolation:** No client names, tenant IDs, PII, or commercial pricing in repositories, logs, or agent output. Placeholder syntax enforced.
- [ ] **Unconditional conflict resolution order:** Data protection wins without exception. Documented and enforced.
- [ ] **Governance review cadence:** Evidence of scheduled reviews (quarterly minimum) with documented changes, rationale, and approval
- [ ] **Cross-agent consistency:** Same governance framework applied to all agents in the environment

---

## Level 5 — Autonomous

*All items must be demonstrable to claim Level 5. Levels 1–4 evidence must also be intact.*

- [ ] **Governance drift detection:** Automated mechanism compares current governance documents against known-good baseline. Deviation triggers alert.
- [ ] **Lint hooks — structure validation:** Pre-commit or CI hooks validate governance document structure (required sections present)
- [ ] **Lint hooks — prohibited content:** Hooks check for hardcoded secrets, client names, tenant IDs
- [ ] **Lint hooks — conflict resolution integrity:** Hooks verify conflict resolution order is intact and unconditional
- [ ] **Lint hooks — security non-negotiable integrity:** Hooks flag weakening of security controls
- [ ] **Automated health reporting:** Machine-generated compliance reports at defined intervals (weekly minimum)
- [ ] **Health report — document currency:** Covers governance document currency (last review date, days since last change)
- [ ] **Health report — security compliance:** Covers security control compliance (scan results, rotation status, CORS)
- [ ] **Health report — business alignment:** Covers task classification distribution, cost against budget
- [ ] **Health report — autonomous operation:** Covers turn limit adherence, dry-run default status
- [ ] **Third-party isolation verification:** Automated scanning of agent outputs, logs, and repository for client-identifying data patterns
- [ ] **Change control on governance files:** Modifications require pull request review. Force pushes blocked.
- [ ] **Governance versioning:** Governance documents carry semantic version numbers. Changes tracked in changelog.
