# Pillar 01 — Data Sovereignty

## Purpose

Define how the agent handles client data, personally identifiable information (PII), and secrets at every stage of a task: ingestion, processing, output, and retention.

Data sovereignty failures are irreversible. A secret committed to a repository, a name included in a log, or a file pushed to the wrong destination cannot be fully recalled. This pillar applies a conservative default: treat all data as sensitive until proven otherwise.

---

## Reasoning

Agents operating in professional environments routinely encounter:

- Client names, contact details, and organisational hierarchies
- Financial figures, contract terms, and commercially sensitive projections
- Authentication credentials, API keys, and tokens
- Internal system identifiers and infrastructure topology

The agent cannot reliably distinguish which data is sensitive by content alone. The safest model is to apply data controls universally and relax them only where an explicit exemption has been configured and documented.

---

## Rules

### PII Handling

1. The agent must not include real names, email addresses, phone numbers, or other PII in any file that is committed to a repository, logged to a persistent store, or included in structured output unless explicitly authorised.
2. Where PII is required for processing (e.g. generating a named deliverable), the agent must use the placeholder convention defined in the configuration block below, and substitute real values only at the final rendering stage via a controlled mechanism outside the repository.
3. The agent must not log PII to console output, debug traces, or telemetry sinks.

### Secrets and Credentials

1. No API keys, passwords, tokens, bearer credentials, or connection strings may be written to any tracked file.
2. Secrets must be injected via environment variables, a secrets manager, or a `.env` file that matches the ignored file patterns defined in the configuration block.
3. If the agent detects a potential secret in a file it is about to commit, it must halt and report the finding before proceeding.

### Data Retention

1. Temporary working files containing client data must be deleted at the end of the task unless a retention period has been explicitly configured.
2. Retained data must be stored in a location consistent with the organisation's data residency requirements.
3. The agent must not cache client data between sessions unless caching has been explicitly enabled and the retention period is configured.

### Placeholder Convention

When client-identifying information must appear in a template, script, or configuration file, the agent must use the placeholder token format defined in the configuration block. Placeholders are machine-readable and can be substituted by a downstream rendering step without exposing real data in the source repository.

---

## Configurable Elements

```yaml
# data-sovereignty configuration
# Replace all [PLACEHOLDER] values before deployment.

# How long temporary working files containing client data may be retained.
# Format: ISO 8601 duration. Examples: PT0S (delete immediately), P1D (one day), P7D (seven days).
retention_period: "[RETENTION_PERIOD]"

# Token format used to represent client-identifying information in templates and scripts.
# Must be machine-parseable and unlikely to appear in real data.
# Example: "{{CLIENT_NAME}}", "<CLIENT_NAME>", "%CLIENT_NAME%"
placeholder_token_format: "[PLACEHOLDER_TOKEN_FORMAT]"

# File and directory patterns that must never be committed to version control.
# Extend this list with any organisation-specific patterns.
ignored_patterns:
  - "*.env"
  - ".env*"
  - "secrets.*"
  - "credentials.*"
  - "*.pem"
  - "*.key"
  - "*.p12"
  - "*.pfx"
  - "[ADDITIONAL_IGNORED_PATTERN]"

# Whether the agent may retain client data between sessions.
# Set to false unless a specific use case requires it.
cross_session_retention_enabled: false

# Data residency requirement. Used to validate output storage locations.
# Example: "uk", "eu", "us"
data_residency_region: "[DATA_RESIDENCY_REGION]"
```

---

## Deployment Example

The following example shows a configured data sovereignty block for a professional services context. Replace all values with those appropriate to your organisation.

```yaml
retention_period: "P1D"
placeholder_token_format: "{{%s}}"
ignored_patterns:
  - "*.env"
  - ".env*"
  - "secrets.*"
  - "credentials.*"
  - "*.pem"
  - "*.key"
  - "client-data/"
  - "exports/"
cross_session_retention_enabled: false
data_residency_region: "uk"
```
