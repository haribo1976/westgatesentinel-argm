# Contributing to ARGM

Thank you for your interest in contributing to the Agentic Runtime Governance Model.

---

## Before You Open a Pull Request

1. **Open an issue first.** Describe the change, which section or level it affects, and why it is needed.
2. **Check existing issues.** Your proposal may already be under discussion.
3. **Read the self-assessment framework.** Changes to level definitions, observable evidence, or assessment questions affect the validity of assessments already conducted against the model.

---

## What We Welcome

- **Corrections to level definitions or evidence requirements** — if evidence items are ambiguous, incorrect, or missing
- **New or improved assessment questions** — questions that better probe a level's requirements
- **Cross-framework mapping corrections** — if a mapping to NIST, CMMI, ISO 42001, or other frameworks is incorrect or outdated
- **New cross-framework mappings** — mappings to frameworks not yet covered in Section 6
- **Deployment examples** — illustrative examples at each level for new contexts or stacks (keep these as representative shapes, not fabricated configurations)
- **Gap analysis updates** — as new agentic AI governance models are published

---

## One Level or Section Per Pull Request

Keep pull requests focused. Each PR should address at most one level or one section of the framework. This preserves reviewability and makes change history traceable.

---

## Content Standards

- Keep content generic — no organisation-specific names, internal references, or pricing
- Use `[PLACEHOLDER]` format for values that must be filled in by the deploying organisation
- Preserve verbatim wording from the source framework where possible — wording precision matters for assessment validity
- Section numbers from the source document should be preserved in `docs/` files

---

## Commit Convention

Use [Conventional Commits](https://www.conventionalcommits.org/):

| Prefix | Use for |
|--------|---------|
| `feat:` | New levels, pillars, or framework additions |
| `fix:` | Corrections to evidence, questions, or mappings |
| `docs:` | Documentation and example improvements |
| `chore:` | Maintenance, changelog, tooling |

---

## Pull Request Checklist

- [ ] Issue exists and is referenced in the PR description
- [ ] PR touches at most one level or section
- [ ] No organisation-specific names, credentials, or internal references
- [ ] CHANGELOG.md updated with version entry
- [ ] PR description explains what changed and why

---

## Licence

By contributing, you agree that your contributions are licensed under CC-BY-SA 4.0.
