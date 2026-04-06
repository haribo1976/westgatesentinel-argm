# Pillar 05 — Output Efficiency

## Purpose

Automate the repeatable. Ensure that scripts produce structured, machine-readable output, and that templates consume structured output. Reserve human time for interpretation, judgement, and decisions that require context the agent does not have.

---

## Reasoning

The most common efficiency failure in agent-assisted work is not slow execution — it is unstructured output. When an agent produces prose, markdown tables, or free-form reports that must then be manually reformatted before they can be used, it creates a hidden labour cost that erodes the benefit of automation.

This pillar requires the agent to produce output in a declared schema wherever the output will be consumed by another system, script, or template. It also requires the agent to use templates for any output that has a fixed structure, rather than generating that structure from scratch each time.

---

## Rules

1. Any output intended for machine consumption must conform to the configured output schema.
2. Scripts that produce reports, assessments, or inventories must write structured output (JSON, YAML, or CSV as appropriate) in addition to any human-readable summary.
3. The agent must use the configured template stack for deliverable types that have a template. It must not generate deliverable structure from scratch if a template exists.
4. Human-readable summaries may accompany structured output but must not replace it.
5. The agent must not produce output in a format that requires the recipient to perform structural transformation before use.

---

## Configurable Elements

```yaml
# output-efficiency configuration
# Replace all [PLACEHOLDER] values before deployment.

# Primary output schema for structured machine-readable output.
# Example: "json-schema/output-v1.json", "inline", "[SCHEMA_PATH]"
output_schema: "[OUTPUT_SCHEMA_PATH]"

# Default structured output format for scripts.
# Options: "json", "yaml", "csv", "ndjson"
default_structured_format: "json"

# Template stack. Maps deliverable types to template file paths.
# Add an entry for each deliverable type the agent is expected to produce.
template_stack:
  - type: "[DELIVERABLE_TYPE_1]"
    template: "[TEMPLATE_PATH_1]"
  - type: "[DELIVERABLE_TYPE_2]"
    template: "[TEMPLATE_PATH_2]"

# Whether the agent may generate deliverable structure from scratch if no template exists.
# Set to false to require a template for all structured deliverables.
allow_templateless_generation: true

# Directory where structured output files are written.
output_directory: "[OUTPUT_DIRECTORY]"
```

---

## Deployment Example

```yaml
output_schema: "schemas/output-v1.json"
default_structured_format: "json"
template_stack:
  - type: "assessment-report"
    template: "templates/assessment-report.md"
  - type: "configuration-summary"
    template: "templates/configuration-summary.md"
  - type: "remediation-plan"
    template: "templates/remediation-plan.md"
allow_templateless_generation: true
output_directory: "output/"
```
