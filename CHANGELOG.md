# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.2.0] — 2026-04-06

### Changed

- Restructured as ARGM v1.1 prime directive model
- Replaced pillar architecture with seven numbered prime directives (D0–D6) with explicit conflict resolution order
- Replaced `pillars/`, `controls/`, and `deployment/` directories with `docs/`, `assessment/`, and `examples/`
- `docs/argm-framework.md`: full framework (Sections 1–5 from source), including six level definitions with observable evidence, assessment questions, progression criteria, and common failure modes
- `docs/argm-mapping.md`: cross-framework mapping to NIST CSF 2.0, CMMI, NIST AI RMF, ISO 42001, AISM, and Microsoft Agentic AI Adoption Maturity Model
- `docs/argm-gap-analysis.md`: gap analysis against surveyed models, including where ARGM goes further and where existing models go further
- `docs/argm-naming.md`: naming rationale and alternatives considered
- `docs/argm-references.md`: verified and partially verified references
- `assessment/assessment-template.md`: all assessment questions for Levels 0–5
- `assessment/evidence-checklist.md`: all observable evidence items for Levels 0–5
- `assessment/scoring-guide.md`: scoring methodology, evidence standards, and common scoring notes
- `examples/level-1-claude-md.md` through `examples/level-5-monitoring.md`: implementation stubs
- Licence changed from MIT to CC-BY-SA 4.0
- D0 compliance: no client names, PII, or internal commercial data in any repository content

---

## [0.1.0] — 2026-04-06

### Added

- Initial framework release
- Seven governance pillars covering data sovereignty, hard boundaries, value alignment, operational portability, output efficiency, output quality, and security injection defence
- Three operational controls: autonomous operation, self-governance, and conflict resolution
- Deployment configuration checklist
- Deployment example stubs for five verticals: professional services, software development, healthcare, financial services, and public sector
- MIT licence
- Contributing guidelines and GitHub issue templates
