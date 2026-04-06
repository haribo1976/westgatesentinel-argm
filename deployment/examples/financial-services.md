# Deployment Example — Financial Services

This file is a configuration stub for deploying the Agent Runtime Framework in a financial services organisation.

Replace all `[TODO: ...]` blocks with your organisation's specific values. Financial services deployments must give particular attention to Pillar 02 (Hard Boundaries) and Pillar 03 (Value Alignment) given regulatory obligations and the risk of automated financial action.

---

## Organisation Context

- **Vertical**: Financial Services
- **Organisation**: [ORGANISATION_NAME]
- **Primary domain**: [DOMAIN]

---

## Pillar Configuration

### Pillar 01 — Data Sovereignty

```yaml
retention_period: "[TODO: align to FCA/PRA or applicable regulatory retention requirements]"
placeholder_token_format: "[TODO]"
ignored_patterns:
  - "*.env"
  - ".env*"
  - "*.pem"
  - "*.key"
  - "[TODO: e.g. client-portfolios/, trade-data/]"
data_residency_region: "[TODO]"
cross_session_retention_enabled: false
```

### Pillar 02 — Hard Boundaries

```yaml
# TODO: Financial services typically require strict prohibitions on automated financial action
never_build:
  - "[TODO: e.g. Systems that execute trades or financial transactions without human sign-off]"
  - "[TODO: e.g. Tools that generate investment advice without regulatory review]"
  - "[TODO: e.g. Processes that access client accounts without explicit authorisation]"
log_boundary_triggers: true
boundary_log_destination: "[TODO]"
```

### Pillar 03 — Value Alignment

```yaml
tiers:
  primary:
    description: "[TODO: e.g. Revenue-generating client services and regulated activities]"
  secondary:
    description: "[TODO: e.g. Compliance tooling, risk management, operational systems]"
  enablement:
    description: "[TODO: e.g. Staff development, documentation, internal tooling]"
    auto_approve: false
  reject:
    description: "[TODO: e.g. Activities outside regulated scope or commercial mandate]"
approved_service_codes:
  - "[TODO]"
enablement_approval_role: "[TODO]"
```

### Pillar 04 — Operational Portability

```yaml
cloud_provider: "[TODO: note any FCA/PRA guidance on outsourcing and cloud use]"
target_region: "[TODO]"
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
brand_reference: "[TODO]"
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
  - "[TODO: additional patterns relevant to financial data or trading contexts]"
injection_report_destination: "[TODO]"
detection_halt_scope: "session"
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
  - "[TODO: e.g. execute-trade, transfer-funds, update-client-record]"
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
