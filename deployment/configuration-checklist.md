# Deployment Configuration Checklist

Use this checklist to deploy the Agent Runtime Framework in a new organisation. Work through each section in order.

---

## Phase 1 — Identity and Repository Setup

- [ ] Fork or clone the framework repository to a private repository under the organisation's version control system
- [ ] Assign a named owner to the framework repository — this person is responsible for amendments, reviews, and audit responses
- [ ] Add the repository to the organisation's access control system: read for all contributors, write for designated framework owners only
- [ ] Configure branch protection on the main branch: require pull request reviews, disallow direct pushes
- [ ] Create a `.gitignore` that includes all patterns from the Pillar 01 `ignored_patterns` configuration
- [ ] Verify that no secrets, credentials, or sensitive data are present in the repository's initial state

---

## Phase 2 — Pillar Configuration

Work through each pillar file and replace all `[PLACEHOLDER]` values.

### Pillar 01 — Data Sovereignty

- [ ] Define `sensitive_data_classes` for your context — be specific
- [ ] Define `placeholder_token_format` and document it in the team wiki
- [ ] Set `retention_period` to match your data retention policy
- [ ] Define `purge_procedure`
- [ ] Extend `ignored_patterns` with any organisation-specific file patterns
- [ ] Set `violation_notification_channel`
- [ ] Set `data_residency_region`
- [ ] Confirm `cross_session_retention_enabled` is set correctly

### Pillar 02 — Hard Boundaries

- [ ] Review the universal hard boundaries — no action required unless documenting an exemption (extraordinary review required)
- [ ] Define the `rejection_list` for your organisation
- [ ] Define `readiness_thresholds` for any conditionally permitted work classes
- [ ] Document the `exemption_process`
- [ ] Set `boundary_log_destination`
- [ ] Verify the audit sink is write-accessible by the agent and read-accessible by the security team

### Pillar 03 — Value Alignment

- [ ] Write clear `description` values for all four tiers reflecting the organisation's mission
- [ ] Define `trigger_conditions` for Tier 2 work
- [ ] Set `standalone_approval_role` for Tier 3 work
- [ ] Populate `approved_codes`
- [ ] Confirm `log_tier_classifications` is enabled

### Pillar 04 — Operational Portability

- [ ] Set `infrastructure_target` and `target_region`
- [ ] Configure `permitted_auth_patterns` and verify the agent's identity has been provisioned
- [ ] Set `resource_ceiling_per_session` — start conservatively
- [ ] Populate `approved_integrations`
- [ ] Set `autonomous_provisioning_enabled` to false unless there is a specific, reviewed use case
- [ ] Define `portability_requirements` for your environment

### Pillar 05 — Output Efficiency

- [ ] Define `downstream_formats` — what your systems and humans consume
- [ ] Define or reference the `output_schema`
- [ ] Set `default_structured_format`
- [ ] Populate `template_stack` and confirm templates exist at the specified paths
- [ ] Set `output_directory`
- [ ] Define `automation_targets`

### Pillar 06 — Output Quality

- [ ] Reference or create `brand_reference` assets
- [ ] Set `executive_summary_word_limit`
- [ ] Set `turnaround_target` to a realistic value
- [ ] Define `quality_gate` criteria
- [ ] Define `acceptable_delivery_formats`

### Pillar 07 — Security and Injection Defence

- [ ] Review and extend `scan_patterns` with organisation-specific patterns
- [ ] Configure `alert_format` and set `destination`
- [ ] Define `trusted_sources`
- [ ] Set `detection_halt_scope`
- [ ] Configure `rate_limits` for sensitive endpoints
- [ ] Define `subagent_max_permissions`

---

## Phase 3 — Controls Configuration

### Autonomous Operation

- [ ] Set `max_turns_per_session` — start conservatively
- [ ] Confirm `safe_run_default` is true
- [ ] Review and extend `prohibited_operations`
- [ ] Set `turn_limit_behaviour`
- [ ] Set `write_log_retention`
- [ ] Confirm `external_call_gating_enabled` is true

### Self-Governance

- [ ] Assign named individuals to `amendment_approvers` roles
- [ ] Set `audit_cadence` and create a calendar reminder for the first audit
- [ ] Set `change_hook_mode` and verify the hook is operational
- [ ] Set `drift_thresholds`
- [ ] Ensure all contributors understand the amendment process

### Conflict Resolution

- [ ] Review the default pillar priority order
- [ ] Adjust the ordering if required (Pillar 01 must remain at priority 1)
- [ ] Set `conflict_log_destination`
- [ ] Confirm `log_conflicts` is enabled

---

## Phase 4 — Conventions

### File Naming

- [ ] Agree on a naming convention for agent-produced artefacts and document it
- [ ] Ensure the convention is reflected in the `output_directory` configuration

### Commit Conventions

- [ ] Adopt a commit message convention — recommended: Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`)
- [ ] Document the convention in CONTRIBUTING

### Code Conventions by Stack

For each language or framework in the organisation's codebase, document:

- [ ] Linting tool and configuration file location
- [ ] Formatter and configuration
- [ ] Required pre-commit hooks
- [ ] Test framework and coverage target

### Output Schema

- [ ] Define or reference the output schema specified in Pillar 05
- [ ] Validate that existing scripts produce conforming output

---

## Phase 5 — Security Scanning

- [ ] Enable secret scanning on the framework repository
- [ ] Configure a pre-commit hook for secret detection
- [ ] Run a baseline scan on initial deployment
- [ ] Schedule regular dependency vulnerability scans
- [ ] Document the process for responding to scan findings

---

## Phase 6 — Go-Live

- [ ] All pillar and control placeholder values have been replaced
- [ ] All audit sinks are operational and accessible
- [ ] A test task has been run in safe-run mode and the output has been reviewed
- [ ] The framework owner has reviewed and signed off the configuration
- [ ] The initial configuration has been committed with a `chore: initial configuration` commit message
- [ ] `CHANGELOG.md` has been updated with the configuration date and operator
