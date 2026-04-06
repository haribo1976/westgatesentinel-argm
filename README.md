# Agent Runtime Framework

A governance framework for autonomous AI agents operating in any commercial context. It defines how agents behave, what they build, what they refuse, and how they report — across security, business, cost, and delivery dimensions.

The framework is organised into seven pillars. Each pillar addresses a distinct class of failure mode. Pillars are ordered by priority — higher pillars override lower ones unconditionally when conflicts arise.

It is designed to be configured, not customised. The pillar architecture is universal. The values inside each pillar reflect the organisation deploying it.

---

## The Seven Pillars

| # | Pillar | Purpose | Priority |
|---|--------|---------|----------|
| 1 | [Data Sovereignty](pillars/01-data-sovereignty.md) | Unconditional constraint on what the agent may expose, log, or embed | Highest |
| 2 | [Hard Boundaries](pillars/02-hard-boundaries.md) | Explicit rejection list — what the agent will never build or execute | 2 |
| 3 | [Value Alignment](pillars/03-value-alignment.md) | Connects agent effort to organisational outcomes via a tier system | 3 |
| 4 | [Operational Portability](pillars/04-operational-portability.md) | Governs infrastructure, authentication, and resource footprint | 4 |
| 5 | [Output Efficiency](pillars/05-output-efficiency.md) | Maximises the ratio of value produced to resources spent | 5 |
| 6 | [Output Quality](pillars/06-output-quality.md) | Defines what acceptable output looks like | 6 |
| 7 | [Security & Injection Defence](pillars/07-security-injection-defence.md) | Governs agent behaviour in adversarial environments | Lowest |

When pillars conflict, higher-numbered pillars yield to lower-numbered ones. Pillar 1 wins every conflict unconditionally.

---

## Autonomous Operation Controls

Separate from the pillars, a set of controls governs unattended execution. See [`controls/autonomous-operation.md`](controls/autonomous-operation.md).

---

## Self-Governance

The framework monitors itself. See [`controls/self-governance.md`](controls/self-governance.md).

---

## Conflict Resolution

See [`controls/conflict-resolution.md`](controls/conflict-resolution.md).

---

## Quick Start

### 1. Fork or clone this repository

```bash
git clone https://github.com/[YOUR_USERNAME]/agent-runtime-framework.git
cd agent-runtime-framework
```

### 2. Work through the deployment checklist

See [`deployment/configuration-checklist.md`](deployment/configuration-checklist.md).

### 3. Configure each pillar

Each file under `pillars/` contains a **Configurable Elements** section. Replace all `[PLACEHOLDER]` values with your organisation-specific settings.

### 4. Review the controls

The files under `controls/` define operational safety rules and the framework's own amendment process.

### 5. Add deployment examples

Use the stubs in `deployment/examples/` as a starting point for your vertical-specific configuration.

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

## Design Principles

**Structural over advisory.** Rules that matter are enforced structurally, not stated as preferences. Advisory rules belong in documentation, not in the runtime governance layer.

**Configured, not customised.** The pillar architecture is universal. The values inside each pillar reflect the organisation deploying it.

**Portability.** The framework contains no vendor-specific dependencies in its governance layer. It applies to any agent runtime, any model provider, any infrastructure target, any vertical.

**Third-party isolation.** External tooling configuration is excluded from governance thresholds and health reporting. When a violation fires, it is always actionable.

---

## Contributing

See [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

---

## Licence

MIT — see [`LICENSE`](LICENSE).
