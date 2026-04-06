# Deployment Example — Healthcare

This file is a configuration stub for deploying the Agent Runtime Framework in a healthcare organisation.

Replace all `[TODO: ...]` blocks with your organisation's specific values. Healthcare deployments must give particular attention to Pillar 01 (Data Sovereignty) given the sensitivity of patient data and applicable regulation (e.g. GDPR, NHS Data Security Standards, HIPAA).

---

## Organisation Context

- **Vertical**: Healthcare
- **Organisation**: [ORGANISATION_NAME]
- **Primary domain**: [DOMAIN]

---

## Pillar Configuration

### Pillar 01 — Data Sovereignty

```yaml
# TODO: Align to applicable health data regulation (e.g. GDPR Article 9, NHS DSP Toolkit)
retention_period: "[TODO: typically short, e.g. PT0S or P1D]"
placeholder_token_format: "[TODO]"
ignored_patterns:
  - "*.env"
  - ".env*"
  - "*.pem"
  - "*.key"
  - "[TODO: e.g. patient-data/, exports/, hl7/]"
data_residency_region: "[TODO: critical for health data — e.g. uk]"
cross_session_retention_enabled: false
```

### Pillar 02 — Hard Boundaries

```yaml
# TODO: Healthcare-specific prohibitions
never_build:
  - "[TODO: e.g. Systems that make clinical decisions without clinician sign-off]"
  - "[TODO: e.g. Tools that transmit patient identifiable data to unapproved destinations]"
log_boundary_triggers: true
boundary_log_destination: "[TODO]"
```

### Pillar 03 — Value Alignment

```yaml
tiers:
  primary:
    description: "[TODO: e.g. Patient-facing or clinician-facing services]"
  secondary:
    description: "[TODO: e.g. Clinical informatics, integration, operational tooling]"
  enablement:
    description: "[TODO: e.g. Staff training, documentation, capacity building]"
    auto_approve: false
  reject:
    description: "[TODO: e.g. Work unrelated to patient care or organisational mission]"
approved_service_codes:
  - "[TODO]"
enablement_approval_role: "[TODO]"
```

### Pillar 04 — Operational Portability

```yaml
cloud_provider: "[TODO: note any NHS or regulatory constraints on cloud provider choice]"
target_region: "[TODO: must align to data residency requirement above]"
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
  - "[TODO: additional patterns relevant to clinical data contexts]"
injection_report_destination: "[TODO]"
detection_halt_scope: "task"
subagent_pattern_inheritance: true
```

---

## Controls Configuration

### Autonomous Operation

```yaml
# TODO: Healthcare contexts may require more conservative turn limits
max_turns_per_session: "[TODO: e.g. 25]"
dry_run_default: true
forbidden_operations:
  - "delete"
  - "drop"
  - "send-email"
  - "[TODO: e.g. write-to-ehr, update-patient-record]"
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
