# Deployment Example — Software Development

This file is a configuration stub for deploying the Agent Runtime Framework in a software development organisation or team.

Replace all `[TODO: ...]` blocks with your organisation's specific values.

---

## Organisation Context

- **Vertical**: Software Development
- **Organisation**: [ORGANISATION_NAME]
- **Primary domain**: [DOMAIN]

---

## Pillar Configuration

### Pillar 01 — Data Sovereignty

```yaml
retention_period: "[TODO: e.g. PT0S for ephemeral, P1D for short-lived]"
placeholder_token_format: "[TODO: e.g. {{%s}}]"
ignored_patterns:
  - "*.env"
  - ".env*"
  - "*.pem"
  - "*.key"
  - "[TODO: additional patterns e.g. local config files]"
data_residency_region: "[TODO]"
cross_session_retention_enabled: false
```

### Pillar 02 — Hard Boundaries

```yaml
never_build:
  - "[TODO: e.g. Tools designed to bypass licence checks]"
  - "[TODO: e.g. Code that intentionally obscures telemetry or audit trails]"
log_boundary_triggers: true
boundary_log_destination: "[TODO]"
```

### Pillar 03 — Value Alignment

```yaml
tiers:
  primary:
    description: "[TODO: e.g. Features and fixes that ship to production]"
  secondary:
    description: "[TODO: e.g. Developer tooling, CI/CD, test infrastructure]"
  enablement:
    description: "[TODO: e.g. Documentation, knowledge base, onboarding]"
    auto_approve: false
  reject:
    description: "[TODO: e.g. Work unrelated to the product roadmap]"
approved_service_codes:
  - "[TODO]"
enablement_approval_role: "[TODO: e.g. tech-lead]"
```

### Pillar 04 — Operational Portability

```yaml
cloud_provider: "[TODO]"
target_region: "[TODO]"
auth_model: "[TODO: e.g. oidc]"
cost_ceiling_per_session: "[TODO]"
approved_integrations:
  - name: "[TODO: e.g. GitHub]"
    purpose: "[TODO: e.g. Source control and CI/CD]"
autonomous_provisioning_enabled: false
```

### Pillar 05 — Output Efficiency

```yaml
output_schema: "[TODO]"
default_structured_format: "json"
template_stack:
  - type: "[TODO: e.g. pull-request-description]"
    template: "[TODO]"
  - type: "[TODO: e.g. release-notes]"
    template: "[TODO]"
output_directory: "[TODO: e.g. .agent/output/]"
```

### Pillar 06 — Output Quality

```yaml
brand_reference: "[TODO]"
executive_summary_word_limit: "[TODO]"
turnaround_target: "[TODO]"
allow_raw_output: false
formatted_output_types:
  - "markdown"
  - "html"
  - "[TODO]"
```

### Pillar 07 — Security & Injection Defence

```yaml
detection_patterns:
  - "ignore previous instructions"
  - "[TODO: additional patterns relevant to code review or CI contexts]"
injection_report_destination: "[TODO]"
detection_halt_scope: "task"
subagent_pattern_inheritance: true
```

---

## Controls Configuration

### Autonomous Operation

```yaml
max_turns_per_session: "[TODO]"
dry_run_default: true
forbidden_operations:
  - "delete"
  - "drop"
  - "[TODO: e.g. force-push]"
turn_limit_behaviour: "checkpoint"
```

### Conflict Resolution

```yaml
pillar_priority_order:
  - pillar: "02-hard-boundaries"
    priority: 1
  - pillar: "07-security-injection-defence"
    priority: 2
  - pillar: "01-data-sovereignty"
    priority: 3
  - pillar: "03-value-alignment"
    priority: 4
  - pillar: "04-operational-portability"
    priority: 5
  - pillar: "05-output-efficiency"
    priority: 6
  - pillar: "06-output-quality"
    priority: 7
```
