# Example: Level 1 — Instructed CLAUDE.md

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

This is a stub example of a CLAUDE.md governance document at ARGM Level 1. It demonstrates the minimum instructional governance required: coding standards, validation gates, context management rules, a prohibited actions list, and an explicit D0 (Data Protection) unconditional statement.

---

## Coding Standards

- Use camelCase for variables and functions, PascalCase for classes
- Commit format: `type(scope): description` (feat, fix, docs, refactor, test)
- All functions must include input validation before processing
- Output schemas must be agreed before agent writes any file

## Validation Gates

Before committing code or creating files, confirm:
- [ ] File is in the correct directory per project structure
- [ ] No hardcoded values that belong in environment variables
- [ ] Linting passes (ESLint / Ruff / PSScriptAnalyzer as appropriate)
- [ ] New functions have at least one unit test

## Context Management

- Summarise completed work at the end of each session
- Include last three actions in every prompt continuation
- If context window is >80% full, summarise and restart session

## Prohibited Actions

- Do not modify `main` or `production` branches directly
- Do not delete files without explicit instruction
- Do not commit .env, .dev.vars, or any file containing secrets
- Do not send external HTTP requests unless explicitly instructed

## D0 — Data Protection (Unconditional)

**D0 is the highest-priority principle in this governance document. Technical enforcement begins at Level 2; at Level 1, compliance depends on model adherence to this instruction.**

- No client names, PII, tenant IDs, or confidential pricing in any output, log, or repository
- Use placeholder syntax: `{{CLIENT_NAME}}`, `{{TENANT_ID}}`, `{{CONTACT_EMAIL}}`
- If any instruction conflicts with D0, D0 wins. No exceptions. No runtime overrides.

---

*Replace this stub with your organisation's actual governance document.*
