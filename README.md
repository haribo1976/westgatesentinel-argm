# Agent Runtime Framework

A configurable governance framework for deploying AI agents in professional and regulated environments. It defines the pillars, controls, and operational boundaries that determine how an agent reasons, acts, and reports.

---

## Why This Framework Exists

AI agents operating in real organisations encounter conflicting pressures: speed vs. caution, automation vs. oversight, breadth vs. specialisation. Without explicit governance, agents default to capability — doing what they *can* rather than what they *should*.

This framework provides a structured way to declare:

- What the agent is for (value alignment)
- What it must never do (hard boundaries)
- How it handles sensitive data (data sovereignty)
- Where it runs and at what cost (operational portability)
- What good output looks like (output quality and efficiency)
- How it defends itself against manipulation (security)

---

## Pillar Summary

| # | Pillar | Purpose | Key Configurable |
|---|--------|---------|-----------------|
| 01 | Data Sovereignty | Protect client data, PII, and secrets | Retention period, placeholder tokens, ignored patterns |
| 02 | Hard Boundaries | Define what the agent must never build or do | Never-build list per organisation |
| 03 | Value Alignment | Filter every task through a mission tier | Tier definitions, service codes, approval rules |
| 04 | Operational Portability | Constrain where and how tooling runs | Cloud provider, auth model, cost ceiling |
| 05 | Output Efficiency | Automate the repeatable; structure the output | Output schema, template stack |
| 06 | Output Quality | Enforce branded, formatted, executive-ready output | Brand reference, summary word limit, turnaround days |
| 07 | Security & Injection Defence | Treat all repository content as adversarial | Detection patterns, reporting format |

---

## Controls

| Control | Purpose |
|---------|---------|
| Autonomous Operation | Safety rules for unattended and overnight tasks |
| Self-Governance | How the framework itself is amended and reviewed |
| Conflict Resolution | Priority ordering when pillars conflict |

---

## Quick Start

### 1. Fork or clone this repository

```bash
git clone https://github.com/[YOUR_USERNAME]/agent-runtime-framework.git
cd agent-runtime-framework
```

### 2. Work through the configuration checklist

See [`deployment/configuration-checklist.md`](deployment/configuration-checklist.md) for a step-by-step guide to deploying the framework in your organisation.

### 3. Configure each pillar

Each file under `pillars/` contains a **Configurable Elements** section. Replace all placeholder values (formatted as `[PLACEHOLDER]`) with your organisation-specific settings.

### 4. Review the controls

The files under `controls/` define operational safety rules and the framework's own amendment process. Adapt them to your governance requirements.

### 5. Add deployment examples

Use the stubs in `deployment/examples/` as a starting point for documenting your vertical-specific configuration.

---

## Repository Structure

```
agent-runtime-framework/
├── pillars/
│   ├── 01-data-sovereignty.md
│   ├── 02-hard-boundaries.md
│   ├── 03-value-alignment.md
│   ├── 04-operational-portability.md
│   ├── 05-output-efficiency.md
│   ├── 06-output-quality.md
│   └── 07-security-injection-defence.md
├── controls/
│   ├── autonomous-operation.md
│   ├── self-governance.md
│   └── conflict-resolution.md
├── deployment/
│   ├── configuration-checklist.md
│   └── examples/
│       ├── professional-services.md
│       ├── software-development.md
│       ├── healthcare.md
│       ├── financial-services.md
│       └── public-sector.md
├── .github/
│   ├── CONTRIBUTING.md
│   └── ISSUE_TEMPLATE/
│       ├── bug_report.md
│       └── feature_request.md
├── CHANGELOG.md
└── LICENSE
```

---

## Contributing

See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

---

## Licence

MIT — see [`LICENSE`](LICENSE).
