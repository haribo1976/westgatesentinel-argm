# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.2.0] — 2026-04-06

### Changed

- Restructured as ARGM maturity model. Six levels (0 Ungoverned through 5 Autonomous), cross-framework mappings, assessment tooling.
- New file structure: docs/, assessment/, examples/
- Licence changed from MIT to CC-BY-SA 4.0

### Added

- docs/argm-framework.md — full model (sections 1–5)
- docs/argm-mapping.md — cross-framework mapping to NIST CSF, CMMI, NIST AI RMF, ISO 42001, AISM, Microsoft
- docs/argm-gap-analysis.md — gap analysis vs existing models
- docs/argm-naming.md — naming rationale
- docs/argm-references.md — references (verified and partially verified)
- assessment/assessment-template.md — blank assessment template, all questions levels 0–5
- assessment/evidence-checklist.md — observable evidence checklist per level
- assessment/scoring-guide.md — scoring methodology
- examples/ — illustrative governance configurations at levels 1–5

---

## [0.1.0] — 2026-04-06

### Added

- Initial framework release
- Seven governance pillars covering data sovereignty, hard boundaries, value alignment, operational portability, output efficiency, output quality, and security injection defence
- Three operational controls: autonomous operation, self-governance, and conflict resolution
- Deployment configuration checklist
- Deployment example stubs for five verticals
- MIT licence
- Contributing guidelines and GitHub issue templates
