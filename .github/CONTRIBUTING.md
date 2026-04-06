# Contributing to Agent Runtime Framework

Thank you for your interest in contributing. This document explains how to propose changes to the framework.

---

## Before You Open a Pull Request

1. **Open an issue first.** Describe the change you are proposing, why it is needed, and which pillar or control it affects. This allows discussion before implementation effort is invested.
2. **Check existing issues.** Your proposal may already be under discussion.
3. **Read the self-governance control.** [`controls/self-governance.md`](../controls/self-governance.md) defines the amendment process, review requirements, and prohibited amendments.

---

## Scope of Contributions

The following contributions are welcome:

- **Bug fixes**: Corrections to factual errors, broken links, or internal inconsistencies
- **Pillar improvements**: Clarifications, additional reasoning, or improved configurable element descriptions
- **New deployment examples**: Configuration stubs for verticals not yet covered — keep these as stubs with `[TODO: ...]` placeholders; do not include real organisation data
- **Control improvements**: Amendments to the autonomous operation, self-governance, or conflict resolution controls
- **Tooling**: Scripts or templates that help operators deploy the framework

---

## One Pillar Per Pull Request

Keep pull requests focused. Each PR should touch at most one pillar or control. This makes review faster and reduces the risk of unintended interactions.

---

## Configuration Examples Are Welcome

If you have deployed the framework in a new vertical and want to share a sanitised configuration stub, open a PR adding a new file under `deployment/examples/`. The file must:

- Contain only `[TODO: ...]` placeholders — no real organisation names, domains, costs, or configuration values
- Follow the structure of the existing example files
- Include a brief Organisation Context section with the vertical name

---

## Commit Message Convention

This repository uses [Conventional Commits](https://www.conventionalcommits.org/):

| Prefix | Use for |
|--------|---------|
| `feat:` | New pillars, controls, or examples |
| `fix:` | Corrections and bug fixes |
| `docs:` | Documentation improvements |
| `chore:` | Maintenance, tooling, changelog updates |
| `refactor:` | Restructuring without behavioural change |

---

## Pull Request Checklist

Before submitting a pull request, confirm:

- [ ] An issue exists for this change and is referenced in the PR description
- [ ] The PR touches at most one pillar or control
- [ ] No real organisation names, credentials, or configuration values are included
- [ ] The `CHANGELOG.md` has been updated with a new version entry
- [ ] The PR description explains what changed and why

---

## Review Process

All pull requests require at least one review from a repository maintainer. Pull requests that amend the universal hard boundaries (Pillar 02) or disable the security injection defence (Pillar 07) require an extraordinary review as defined in `controls/self-governance.md`.

---

## Licence

By contributing to this repository, you agree that your contributions will be licensed under the MIT Licence.
