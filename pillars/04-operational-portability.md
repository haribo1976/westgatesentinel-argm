# Pillar 04 — Operational Portability

**Governs infrastructure, authentication, and resource footprint.**

---

## Purpose

Defines where agent-driven work runs, what authentication patterns are permitted, and the resource ceiling for infrastructure. Targets minimal footprint, least-privilege authentication, and portable delivery patterns. No external dependencies without explicit justification.

---

## Why This Pillar Exists

Infrastructure choices made during autonomous operation have cost, security, and operational implications. Embedding constraints at the runtime level means resources are evaluated at task planning time rather than discovered after execution.

Portability does not mean the agent must be cloud-agnostic or stateless by default. It means that every infrastructure assumption is declared explicitly and is configurable, so a new operator can stand up an equivalent environment by reading this file.

---

## Rules

1. The agent must not connect to external services that are not declared in the approved integration list.
2. The agent must use the configured authentication pattern. It must not store credentials in tracked files (see Pillar 01).
3. The agent must not provision infrastructure that would incur costs above the configured resource ceiling without explicit human approval.
4. All tooling must be executable in the configured target environment. The agent must not introduce dependencies incompatible with the target.
5. If a task requires an external dependency not on the approved list, the agent must halt and request explicit justification before proceeding.
6. Portability requires that every infrastructure choice be reproducible from configuration alone — no undocumented manual steps.

---

## Configurable Elements

```yaml
# operational-portability configuration
# Replace all [PLACEHOLDER] values before deployment.

# Primary infrastructure target.
# Example: "azure", "aws", "gcp", "on-premises", "hybrid"
infrastructure_target: "[INFRASTRUCTURE_TARGET]"

# Target region for all provisioned resources.
target_region: "[TARGET_REGION]"

# Permitted authentication patterns. The agent must use one of these.
# Example: "managed-identity", "service-principal", "oidc", "api-key-via-vault"
permitted_auth_patterns:
  - "[AUTH_PATTERN_1]"

# Resource ceiling: maximum spend the agent may incur in a single session without human approval.
# Format: decimal value in the organisation's billing currency.
resource_ceiling_per_session: "[RESOURCE_CEILING]"

# Approved external integrations. The agent must not connect to services not on this list.
approved_integrations:
  - name: "[INTEGRATION_NAME]"
    purpose: "[INTEGRATION_PURPOSE]"
    auth_pattern: "[AUTH_PATTERN]"

# Whether the agent may provision new infrastructure autonomously.
autonomous_provisioning_enabled: false

# Portability requirements: constraints that ensure reproducibility.
portability_requirements:
  - "[PORTABILITY_REQUIREMENT_1]"  # e.g. "All configuration stored in version control"
  - "[PORTABILITY_REQUIREMENT_2]"  # e.g. "No manual provisioning steps outside IaC"
```

---

## Deployment Example

```yaml
infrastructure_target: "azure"
target_region: "uksouth"
permitted_auth_patterns:
  - "managed-identity"
resource_ceiling_per_session: "10.00"
approved_integrations:
  - name: "Azure OpenAI"
    purpose: "Language model inference"
    auth_pattern: "managed-identity"
  - name: "Azure Blob Storage"
    purpose: "Output artefact storage"
    auth_pattern: "managed-identity"
  - name: "GitHub"
    purpose: "Source control and CI/CD"
    auth_pattern: "oidc"
autonomous_provisioning_enabled: false
portability_requirements:
  - "All configuration stored in version control"
  - "No manual provisioning steps outside IaC templates"
  - "Environment reproducible from configuration alone within 30 minutes"
```
