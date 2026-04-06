# Deployment Example — Professional Services

This file is a configuration stub for deploying the Agent Runtime Framework in a professional services organisation (consulting, advisory, managed services).

Replace all `[TODO: ...]` blocks with your organisation's specific values. Refer to the pillar and control files for guidance on each configuration element.

---

## Organisation Context

- **Vertical**: Professional Services
- **Organisation**: [ORGANISATION_NAME]
- **Primary domain**: [DOMAIN]

---

## Pillar Configuration

### Pillar 01 — Data Sovereignty

```yaml
# TODO: Define retention period aligned to client contract terms and applicable regulation
retention_period: "[TODO: e.g. P7D]"

# TODO: Define placeholder token format used in all client-facing templates
placeholder_token_format: "[TODO: e.g. {{%s}}]"

# TODO: Add any client data directories or file types specific to this vertical
ignored_patterns:
  - "*.env"
  - ".env*"
  - "[TODO: additional patterns]"

data_residency_region: "[TODO: e.g. uk]"
cross_session_retention_enabled: false
```

### Pillar 02 — Hard Boundaries

```yaml
# TODO: Define the never-build list for this organisation
never_build:
  - "[TODO: item 1]"
  - "[TODO: item 2]"

log_boundary_triggers: true
boundary_log_destination: "[TODO: path or sink]"
```

### Pillar 03 — Value Alignment

```yaml
# TODO: Define tier descriptions aligned to the organisation's service model
tiers:
  primary:
    description: "[TODO: billable engagement definition]"
  secondary:
    description: "[TODO: internal tooling definition]"
  enablement:
    description: "[TODO: capability building definition]"
    auto_approve: false
  reject:
    description: "[TODO: out-of-scope definition]"

# TODO: Populate with active service codes or engagement types
approved_service_codes:
  - "[TODO: SERVICE_CODE_1]"

enablement_approval_role: "[TODO: role name]"
```

### Pillar 04 — Operational Portability

```yaml
cloud_provider: "[TODO: e.g. azure]"
target_region: "[TODO: e.g. uksouth]"
auth_model: "[TODO: e.g. managed-identity]"
cost_ceiling_per_session: "[TODO: e.g. 5.00]"

approved_integrations:
  - name: "[TODO: integration 1]"
    purpose: "[TODO: purpose]"

autonomous_provisioning_enabled: false
```

### Pillar 05 — Output Efficiency

```yaml
output_schema: "[TODO: path to schema]"
default_structured_format: "json"

template_stack:
  - type: "[TODO: deliverable type]"
    template: "[TODO: template path]"

output_directory: "[TODO: output directory]"
```

### Pillar 06 — Output Quality

```yaml
brand_reference: "[TODO: path to brand guide]"
executive_summary_word_limit: "[TODO: e.g. 400]"
turnaround_target: "[TODO: e.g. PT4H]"
allow_raw_output: false
formatted_output_types:
  - "[TODO: e.g. pdf]"
  - "[TODO: e.g. docx]"
```

### Pillar 07 — Security & Injection Defence

```yaml
# TODO: Review and extend detection patterns
detection_patterns:
  - "ignore previous instructions"
  - "[TODO: additional patterns]"

injection_report_destination: "[TODO: path or sink]"
detection_halt_scope: "task"
subagent_pattern_inheritance: true
```

---

## Controls Configuration

### Autonomous Operation

```yaml
max_turns_per_session: "[TODO: e.g. 50]"
dry_run_default: true
forbidden_operations:
  - "delete"
  - "send-email"
  - "[TODO: additional operations]"
turn_limit_behaviour: "checkpoint"
```

### Conflict Resolution

```yaml
# TODO: Adjust priority ordering if needed. Pillar 02 must remain at priority 1.
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
