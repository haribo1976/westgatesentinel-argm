# Pillar 04 — Operational Portability

## Purpose

Define where the agent runs, what infrastructure it depends on, how it authenticates, and what it costs. Portability means the agent can be moved, reproduced, or audited without hidden dependencies.

---

## Reasoning

Agents that accumulate undocumented infrastructure dependencies become brittle. They break when environments change, cannot be reproduced for testing, and are difficult to audit. Portability disciplines the agent to declare its dependencies explicitly and to operate within cost and infrastructure constraints set by the organisation.

Portability does not mean the agent must be cloud-agnostic or stateless by default. It means that every infrastructure assumption is documented and configurable, so that a new operator can stand up an equivalent environment by reading this file.

---

## Rules

1. The agent must not connect to external services that are not declared in the approved integration list.
2. The agent must use the configured authentication model. It must not store credentials in tracked files (see Pillar 01).
3. The agent must not provision infrastructure that would incur costs above the configured cost ceiling without explicit human approval.
4. All tooling must be executable in the configured target environment. The agent must not introduce dependencies that are incompatible with the target platform.
5. If the agent is relocated to a different environment, the operator must update this configuration block and re-validate the integration list.

---

## Configurable Elements

```yaml
# operational-portability configuration
# Replace all [PLACEHOLDER] values before deployment.

# Primary cloud provider or runtime environment.
# Example: "azure", "aws", "gcp", "on-premises", "hybrid"
cloud_provider: "[CLOUD_PROVIDER]"

# Target region for all provisioned resources.
# Example: "uksouth", "us-east-1", "europe-west1"
target_region: "[TARGET_REGION]"

# Authentication model used by the agent to access cloud and third-party services.
# Example: "managed-identity", "service-principal", "oidc", "api-key-vault"
auth_model: "[AUTH_MODEL]"

# Maximum cost the agent may incur in a single session without human approval.
# Format: decimal value in the organisation's billing currency.
cost_ceiling_per_session: "[COST_CEILING]"

# Approved external integrations. The agent must not connect to services not on this list.
approved_integrations:
  - name: "[INTEGRATION_NAME_1]"
    purpose: "[INTEGRATION_PURPOSE_1]"
  - name: "[INTEGRATION_NAME_2]"
    purpose: "[INTEGRATION_PURPOSE_2]"

# Whether the agent may provision new infrastructure autonomously.
# Set to false to require human approval for all provisioning.
autonomous_provisioning_enabled: false
```

---

## Deployment Example

```yaml
cloud_provider: "azure"
target_region: "uksouth"
auth_model: "managed-identity"
cost_ceiling_per_session: "10.00"
approved_integrations:
  - name: "Azure OpenAI"
    purpose: "Language model inference"
  - name: "Azure Blob Storage"
    purpose: "Output artefact storage"
  - name: "GitHub"
    purpose: "Source control and CI/CD"
autonomous_provisioning_enabled: false
```
