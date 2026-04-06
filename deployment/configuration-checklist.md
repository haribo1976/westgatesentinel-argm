# Deployment Configuration Checklist

This checklist guides an operator through the steps required to deploy the Agent Runtime Framework in a new organisation. Work through each section in order. Check each item when complete.

---

## Phase 1 — Identity and Repository Setup

- [ ] Fork or clone the framework repository to a private repository under the organisation's version control system
- [ ] Assign a named owner to the framework repository — this person is responsible for amendments and reviews
- [ ] Add the framework repository to the organisation's access control system with appropriate permissions (read for all contributors; write for designated framework owners only)
- [ ] Configure branch protection on the main branch: require pull request reviews, disallow direct pushes
- [ ] Create a `.gitignore` file that includes all patterns from the Pillar 01 `ignored_patterns` configuration
- [ ] Verify that no secrets, credentials, or PII are present in the repository's initial state

---

## Phase 2 — Pillar Configuration

Work through each pillar file and replace all `[PLACEHOLDER]` values with organisation-specific settings.

### Pillar 01 — Data Sovereignty

- [ ] Set `retention_period` to match the organisation's data retention policy
- [ ] Define `placeholder_token_format` and document it in the team wiki or equivalent
- [ ] Extend `ignored_patterns` with any organisation-specific file patterns
- [ ] Set `data_residency_region` to the appropriate jurisdiction
- [ ] Confirm `cross_session_retention_enabled` is set correctly for your use case

### Pillar 02 — Hard Boundaries

- [ ] Review the universal hard boundaries — no action required unless you are documenting an exception (which requires extraordinary review)
- [ ] Define the `never_build` list for your organisation
- [ ] Set `boundary_log_destination` to an appropriate audit sink
- [ ] Verify that the audit sink is write-accessible by the agent and read-accessible by the security team

### Pillar 03 — Value Alignment

- [ ] Write clear `description` values for all four tiers that reflect the organisation's mission
- [ ] Populate `approved_service_codes` with all current service lines or product codes
- [ ] Set `enablement_approval_role` to the appropriate role
- [ ] Confirm `log_tier_classifications` is enabled

### Pillar 04 — Operational Portability

- [ ] Set `cloud_provider` and `target_region`
- [ ] Configure `auth_model` and verify that the agent's identity has been provisioned in the target environment
- [ ] Set `cost_ceiling_per_session` — start conservatively and increase after baseline data is available
- [ ] Populate `approved_integrations` with all external services the agent is expected to use
- [ ] Set `autonomous_provisioning_enabled` to false unless there is a specific, reviewed use case for autonomous provisioning

### Pillar 05 — Output Efficiency

- [ ] Define or reference the `output_schema` for structured output
- [ ] Set `default_structured_format`
- [ ] Populate `template_stack` with all deliverable types and their template paths
- [ ] Confirm templates exist at the specified paths
- [ ] Set `output_directory`

### Pillar 06 — Output Quality

- [ ] Reference or create `brand_reference` assets
- [ ] Set `executive_summary_word_limit`
- [ ] Set `turnaround_target` to a realistic value based on task complexity
- [ ] Confirm `allow_raw_output` is set correctly
- [ ] Define `formatted_output_types` for the output formats your organisation uses

### Pillar 07 — Security & Injection Defence

- [ ] Review and extend `detection_patterns` with any organisation-specific patterns
- [ ] Set `injection_report_destination` to an appropriate audit sink
- [ ] Set `detection_halt_scope` based on your risk appetite
- [ ] Confirm `subagent_pattern_inheritance` is enabled

---

## Phase 3 — Controls Configuration

### Autonomous Operation

- [ ] Set `max_turns_per_session` to a conservative limit for initial deployment
- [ ] Confirm `dry_run_default` is true
- [ ] Review `forbidden_operations` and extend with any organisation-specific operations
- [ ] Set `turn_limit_behaviour`

### Self-Governance

- [ ] Assign named individuals to the `amendment_approvers` roles
- [ ] Confirm `review_cadence` is set and a calendar reminder has been created for the first review
- [ ] Ensure all team members understand the amendment process

### Conflict Resolution

- [ ] Review the default pillar priority ordering
- [ ] Adjust the ordering if required (Pillar 02 must remain at priority 1)
- [ ] Confirm `log_conflicts` is enabled

---

## Phase 4 — Conventions

### File Naming

- [ ] Agree on a file naming convention for agent-produced artefacts and document it
- [ ] Ensure the convention is reflected in the `output_directory` configuration

### Commit Conventions

- [ ] Adopt a commit message convention. Recommended: Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`)
- [ ] Document the convention in the repository's CONTRIBUTING file

### Code Conventions by Stack

Specify conventions for each language or framework used in the organisation's codebase. At minimum, document:

- [ ] Linting tool and configuration file location
- [ ] Formatter and configuration
- [ ] Required pre-commit hooks
- [ ] Test framework and coverage target

### Output Schema

- [ ] Define or reference the output schema file specified in Pillar 05
- [ ] Validate that existing scripts produce output conforming to the schema

---

## Phase 5 — Security Scanning

- [ ] Enable secret scanning on the framework repository (GitHub Advanced Security or equivalent)
- [ ] Configure a pre-commit hook to run secret detection before any commit
- [ ] Run a baseline scan of the repository on initial deployment
- [ ] Schedule regular dependency vulnerability scans
- [ ] Document the process for responding to scan findings

---

## Phase 6 — Go-Live

- [ ] All pillar and control placeholder values have been replaced
- [ ] All audit sinks are operational and accessible
- [ ] A test task has been run in dry-run mode and the output has been reviewed
- [ ] The framework owner has reviewed and signed off the configuration
- [ ] The initial configuration has been committed with a `chore: initial configuration` commit message
- [ ] The `CHANGELOG.md` has been updated with the configuration date and operator name
