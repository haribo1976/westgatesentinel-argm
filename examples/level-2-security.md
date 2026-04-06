# Example: Level 2 — Secured Controls Configuration

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

This stub illustrates the technical controls required at ARGM Level 2. Replace with your actual configuration artefacts.

---

## Pre-commit Scanning Hook

Example `.pre-commit-config.yaml` using gitleaks or equivalent secret scanning tool.

Patterns to detect: `sk_`, `pk_`, `eyJ`, `API_KEY=`, `SECRET=`, `Bearer`, `client_secret=`, `PRIVATE_KEY`, `Authorization:`

## Secrets Management

- All API keys and tokens in environment variables or a secret manager (Azure Key Vault, AWS Secrets Manager, etc.)
- `.env` and `.dev.vars` listed in `.gitignore`
- No secrets passed as command-line parameters

## CORS Policy

Production endpoints must specify explicit allowed origins. Wildcard `*` is prohibited in production. Credentials must be paired with specific origin restrictions.

## Rate Limiting

- Authentication endpoints: 5 attempts per minute per IP
- Breach events logged with timestamp, IP, endpoint, and outcome
- Alert triggered at 3 consecutive failures

## Injection Defence

- Input validated against allowlist before passing to agent context
- Agent-generated HTML output sanitised before rendering
- No user-supplied content concatenated into shell commands or dynamic queries

## Branch Protection

- `main` requires pull request with at least one reviewer approval
- Agents operate on feature branches, never push directly to `main`

## Credential Rotation

- Rotation schedule: every 90 days minimum
- Rotation log maintained with date, credential type, and approver

---

*This stub provides structure. Populate with your actual tooling and configuration.*
