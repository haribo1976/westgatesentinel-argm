# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.0.0] — 2026-04-06

### Breaking Changes

- **Seven levels (0-6)** replacing six (0-5). Old Level 3 (Aligned) split into Level 3 (Controlled: autonomous operation) and Level 4 (Aligned: business directives + cost governance). Old Levels 4-5 renumbered to 5-6.
- **Two-tier directive architecture.** Tier 1 (D0-D2: Safety) is unconditional. Tier 2 (D3-D6: Business) is sector-configurable with documented rationale. Tier 2 never overrides Tier 1.
- **D3 renamed** from "Revenue Alignment" to "Value Alignment" (sector-neutral).
- **D4 renamed** from "Infrastructure Portability" to "Infrastructure Governance" (broader scope).
- **Per-agent mapping moved** from `docs/argm-mapping.md` to `examples/wsc-reference-implementation.md` and labelled as WSC-specific reference, not framework content.
- **Example files renamed:** `level-4-framework.md` → `level-5-governed.md`, `level-5-monitoring.md` → `level-6-autonomous.md`.

### Added

- **Level 3 — Controlled:** Dedicated level for D2 (Autonomous Operation) controls — turn limits, dry-run defaults, destructive operation prohibition, exit conditions, write logging.
- **Break-glass exception mechanism** (Level 5+): Time-bounded (72h), named individual, immutable logging, post-incident review. Tier 2 only — cannot override Tier 1.
- **Cost governance control set** (Level 4): Model selection policy, budget allocation, cost attribution, escalation thresholds, monthly cost review. Expanded from three bullet points to a full control set.
- **Business value classification mechanism** (Level 4): Decision flowchart with sector-configurable terminology (consultancy, healthcare, public sector, open-source).
- **Sector configuration examples** for Tier 2 directive ordering: professional services, healthcare, public sector, open-source/research.
- **Directive evolution mechanism:** How to add, deprecate, reorder, or move directives between tiers.
- **Three-layer regress solution** (Level 6): Technical (drift detection), organisational (governance owner), external (quarterly review). Answers "what governs the governor?"
- **Critical-failure concept** in scoring: A score of 0 on a critical question fails the level regardless of total score.
- **Inter-rater reliability** in scoring: Two-assessor process, divergence thresholds, reconciliation.
- **Calibration exercise** in scoring: Score the Level 1 example before assessing your own environment.
- **Generic Agent Mapping Guide** in `docs/argm-mapping.md`: Agent-agnostic guidance for mapping D0-D6 to any agent ecosystem.
- **Real-world failure scenarios** in every level definition (anonymised).
- **"What ARGM Does Not Cover"** section in gap analysis: explicit out-of-scope areas with recommended frameworks.
- **Positioning section** in README: what ARGM is and is not.

### Changed

- **Novelty claims reduced** from five gaps to three genuine contributions: runtime governance self-monitoring, business value alignment as governance, cost governance.
- **CMMI derivation acknowledged** explicitly in framework doc, naming rationale, and cross-framework mapping.
- **NIST references updated:** SP 800-53 AI control overlays (Aug 2025), AI RMF Playbook (Feb 2025).
- **AISM references updated:** Current AI SAFE² scope includes shell-access governance, alignment drift, sub-agent policy.
- **FinOps Foundation** acknowledged as prior art for cost governance.
- **D0 activation language fixed:** Level 1 acknowledges D0 as principle; Level 2 enforces it technically. Removed contradiction.
- **Cross-framework mappings fixed:** NIST CSF commits to specific tiers (no "Tier 2/3 boundary" hedge). ISO 42001 reframed as evidence contribution (clauses are concurrent, not sequential). CMMI derivation acknowledged in mapping.
- **Scoring threshold justified** with sensitivity analysis note.
- **Evidence standards tightened:** "Genuine and operationally applied, not staged for assessment."

### Removed

- `--dangerously-skip-permissions` from all documentation and examples.
- Universal "no runtime exceptions" language — replaced with Tier 1 unconditional + Tier 2 break-glass.
- Claim that "no existing model addresses all five gaps."
- Per-agent mapping from framework docs (moved to examples/).

### Security

- Removed `--dangerously-skip-permissions` flag from D2 reference implementation. Replaced with `--allowedTools` permission scoping.

---

## [0.3.0] — 2026-04-06

### Added

- `docs/argm-mapping.md`: new section "ARGM Prime Directive Enforcement by Agent" covering all eight agents (Claude Code, Cursor, Codex CLI, Amp, Gemini CLI, Droid CLI, OpenCode, Ollama)
- Summary mapping table: D0–D6 enforcement mechanism per agent with coverage ratings (Full / Partial / Minimal)
- Per-agent configuration guidance: D0–D6 implementation for each agent including governance files, hook configurations, turn limit enforcement, and compensating controls
- Governance consistency controls: shared governance repository, unified pre-commit hook, turn limit wrapper pattern, drift detection, and agent capability register

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
