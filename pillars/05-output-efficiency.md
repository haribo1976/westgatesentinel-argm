# Pillar 05 — Output Efficiency

**Maximises the ratio of value produced to resources spent.**

---

## Purpose

Mandates automation of repeatable tasks, structured output from all processes, template-driven production, and formatted wrappers on all output. Human time is reserved for interpretation, decisions, and exceptions — the agent handles production.

---

## Why This Pillar Exists

The value proposition of autonomous agents depends on producing usable output without manual post-processing. An agent that generates raw, unformatted output requiring human intervention to use eliminates much of the efficiency gain. Structured output means downstream systems and humans consume agent output directly.

---

## Rules

1. Any output intended for machine consumption must conform to the configured output schema.
2. Scripts that produce reports, assessments, or inventories must write structured output (JSON, YAML, or CSV as appropriate) in addition to any human-readable summary.
3. The agent must use the configured template stack for deliverable types that have a template. It must not generate deliverable structure from scratch if a template exists.
4. Human-readable summaries may accompany structured output but must not replace it.
5. The agent must not produce output that requires the recipient to perform structural transformation before use.
6. Repeatable tasks must be automated. If a task has been performed manually more than once, the agent should flag it as an automation candidate.

---

## Configurable Elements

```yaml
# output-efficiency configuration
# Replace all [PLACEHOLDER] values before deployment.

# Output formats your downstream systems and humans consume.
# Determines what the agent produces by default.
downstream_formats:
  - "[FORMAT_1]"  # e.g. "json", "csv", "markdown", "html"
  - "[FORMAT_2]"

# Primary output schema for structured machine-readable output.
output_schema: "[OUTPUT_SCHEMA_PATH]"

# Default structured format for script output.
# Options: "json", "yaml", "csv", "ndjson"
default_structured_format: "json"

# Template stack. Maps deliverable types to template file paths.
template_stack:
  - type: "[DELIVERABLE_TYPE_1]"
    template: "[TEMPLATE_PATH_1]"
  - type: "[DELIVERABLE_TYPE_2]"
    template: "[TEMPLATE_PATH_2]"

# Whether the agent may generate deliverable structure without a template.
allow_templateless_generation: true

# Directory where structured output files are written.
output_directory: "[OUTPUT_DIRECTORY]"

# Automation targets: task classes that should always be automated, never manual.
automation_targets:
  - "[AUTOMATION_TARGET_1]"  # e.g. "inventory generation"
  - "[AUTOMATION_TARGET_2]"  # e.g. "report compilation"
```

---

## Deployment Example

```yaml
downstream_formats:
  - "json"
  - "markdown"
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
automation_targets:
  - "Inventory generation from live systems"
  - "Report compilation from structured data"
  - "Configuration export and diff"
```
