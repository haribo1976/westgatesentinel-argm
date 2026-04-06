# Deployment Example — Public Sector

This file is a configuration stub for deploying the Agent Runtime Framework in a public sector organisation.

Replace all `[TODO: ...]` blocks with your organisation's specific values. Public sector deployments must give particular attention to data sovereignty, procurement compliance, and transparency obligations.

---

## Organisation Context

- **Vertical**: Public Sector
- **Organisation**: [ORGANISATION_NAME]
- **Primary domain**: [DOMAIN]

---

## Pillar Configuration

### Pillar 01 — Data Sovereignty

```yaml
# TODO: Align to applicable legislation (e.g. UK GDPR, DPA 2018, FOIA)
retention_period: "[TODO: align to records management policy]"
placeholder_token_format: "[TODO]"
ignored_patterns:
  - "*.env"
  - ".env*"
  - "*.pem"
  - "*.key"
  - "[TODO: e.g. citizen-data/, restricted/]"
# Public sector data must typically remain in-country
data_residency_region: "[TODO: e.g. uk]"
cross_session_retention_enabled: false
```

### Pillar 02 — Hard Boundaries

```yaml
# TODO: Public sector prohibitions often relate to decision-making on behalf of citizens
never_build:
  - "[TODO: e.g. Automated decision-making systems affecting citizen rights without human review]"
  - "[TODO: e.g. Systems that process OFFICIAL-SENSITIVE or above data without accreditation]"
log_boundary_triggers: true
boundary_log_destination: "[TODO]"
```

### Pillar 03 — Value Alignment

```yaml
tiers:
  primary:
    description: "[TODO: e.g. Statutory services and citizen-facing delivery]"
  secondary:
    description: "[TODO: e.g. Back-office operations, case management, compliance]"
  enablement:
    description: "[TODO: e.g. Staff capability, digital transformation, knowledge management]"
    auto_approve: false
  reject:
    description: "[TODO: e.g. Activities outside the organisation's statutory remit]"
approved_service_codes:
  - "[TODO]"
enablement_approval_role: "[TODO]"
```

### Pillar 04 — Operational Portability

```yaml
# TODO: Note any Crown Commercial Service, G-Cloud, or procurement constraints
cloud_provider: "[TODO]"
target_region: "[TODO: public sector often requires uk or gov.uk-approved regions]"
auth_model: "[TODO]"
cost_ceiling_per_session: "[TODO]"
approved_integrations:
  - name: "[TODO]"
    purpose: "[TODO]"
autonomous_provisioning_enabled: false
```

### Pillar 05 — Output Efficiency

```yaml
output_schema: "[TODO]"
default_structured_format: "json"
template_stack:
  - type: "[TODO]"
    template: "[TODO]"
output_directory: "[TODO]"
```

### Pillar 06 — Output Quality

```yaml
brand_reference: "[TODO: e.g. GOV.UK Design System or departmental brand guide]"
executive_summary_word_limit: "[TODO]"
turnaround_target: "[TODO]"
allow_raw_output: false
formatted_output_types:
  - "[TODO]"
```

### Pillar 07 — Security & Injection Defence

```yaml
detection_patterns:
  - "ignore previous instructions"
  - "[TODO: additional patterns relevant to public sector or citizen data contexts]"
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
  - "send-email"
  - "[TODO: e.g. update-citizen-record, publish-to-gov-uk]"
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
