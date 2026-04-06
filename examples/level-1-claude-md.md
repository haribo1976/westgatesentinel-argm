# Example: Level 1 CLAUDE.md

**ARGM Level:** 1 — Instructed
**Purpose:** Illustrative example of a governance document that meets Level 1 observable evidence requirements

This is a representative example showing the shape of a Level 1 governance document. It demonstrates the categories of content required. It is not a complete or production-ready configuration.

---

## What Level 1 Requires

At Level 1, the governance file must contain:

- Coding conventions (file naming, commit format, linting, output schemas)
- Validation gates (what must be true before committing or creating files)
- Context management rules
- File structure discipline (where to write, where not to)
- A "do not" list

Level 1 does **not** require security controls, business alignment, or cost tracking.

---

## Representative Structure

```markdown
# [REPOSITORY_NAME] — Agent Governance

## Coding Conventions

- File names: lowercase, hyphen-separated (e.g. `my-component.ts`)
- Commit format: Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`)
- Output files: write to `output/` directory only
- Linting: run `[LINTER_COMMAND]` before committing

## Validation Gates

Before creating or committing any file, verify:
- [ ] File is in the correct directory per the structure below
- [ ] No hardcoded values that should be parameterised
- [ ] Follows naming convention

## Context Management

- For conversations exceeding [N] turns, summarise progress at the start of each new context
- Include the task reference in every prompt: `[TASK_REF]`
- Do not carry state from previous sessions without explicit re-confirmation

## File Structure

Write to:
- `src/` — source code
- `tests/` — test files
- `output/` — generated artefacts
- `docs/` — documentation

Do not write to:
- Root directory (except configuration files)
- `node_modules/`, `.next/`, `dist/` (generated directories)

## Do Not List

- Do not modify `[PROTECTED_FILE_OR_DIRECTORY]`
- Do not commit directly to `main` or `production`
- Do not delete files without explicit instruction
```

---

## Gaps to Address for Level 2

To progress to Level 2, this file needs to be supplemented with:

- Credential hygiene rules (secrets in env vars, .env in .gitignore)
- CORS policy for any web-facing endpoints
- Rate limiting requirements
- Injection defence instructions
- Pre-commit scanning configuration

See [`level-2-security.md`](level-2-security.md) for a Level 2 example.
