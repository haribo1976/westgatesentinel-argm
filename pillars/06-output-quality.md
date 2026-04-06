# Pillar 06 — Output Quality

**Defines what acceptable output looks like.**

---

## Purpose

Sets standards for length, format, accuracy, branding, and delivery timeline. All output destined for external consumption meets defined quality thresholds. No raw process output reaches an end recipient without a formatted wrapper.

---

## Why This Pillar Exists

Output quality signals organisational credibility regardless of vertical. Inconsistent, unformatted, or off-brand output undermines trust in the system producing it. Embedding quality standards in the runtime ensures consistency without manual review at the production stage.

---

## Rules

1. All deliverables destined for external recipients must use the organisation's configured brand reference where the output format supports it.
2. Executive summaries must not exceed the configured word limit.
3. All deliverables must be produced within the configured turnaround target from task start.
4. The agent must not deliver raw output — unformatted JSON, bare markdown, plain text — unless the recipient has explicitly requested it.
5. If the agent cannot meet the turnaround target, it must notify the operator before the deadline, not after.
6. The agent must self-review output against this pillar's constraints before marking a task complete. Quality checks apply before delivery.
7. No raw process output — logs, intermediate data, debug traces — may reach an end recipient directly.

---

## Configurable Elements

```yaml
# output-quality configuration
# Replace all [PLACEHOLDER] values before deployment.

# Reference to brand assets or style guide.
# Example: "brand/style-guide.md", "[BRAND_REFERENCE_URL]"
brand_reference: "[BRAND_REFERENCE]"

# Maximum word count for executive summaries.
executive_summary_word_limit: "[WORD_LIMIT]"

# Target turnaround time from task start to delivery.
# Format: ISO 8601 duration. Example: PT4H (four hours), P1D (one day)
turnaround_target: "[TURNAROUND_TARGET]"

# Whether raw output is permitted without explicit recipient request.
allow_raw_output: false

# Quality gate: criteria that output must meet before delivery.
quality_gate:
  - "[QUALITY_CRITERION_1]"  # e.g. "Conforms to output schema (Pillar 05)"
  - "[QUALITY_CRITERION_2]"  # e.g. "Executive summary within word limit"
  - "[QUALITY_CRITERION_3]"  # e.g. "Brand reference applied"
  - "[QUALITY_CRITERION_4]"  # e.g. "No raw process output included"

# Output formats considered acceptable for delivery (not raw).
acceptable_delivery_formats:
  - "[FORMAT_1]"  # e.g. "pdf", "docx", "html", "pptx"
  - "[FORMAT_2]"
```

---

## Deployment Example

```yaml
brand_reference: "brand/style-guide.md"
executive_summary_word_limit: 400
turnaround_target: "PT4H"
allow_raw_output: false
quality_gate:
  - "Conforms to output schema defined in Pillar 05"
  - "Executive summary within 400-word limit"
  - "Brand reference applied to all external deliverables"
  - "No raw process output, logs, or debug traces included"
  - "Delivery timeline met or operator notified before deadline"
acceptable_delivery_formats:
  - "pdf"
  - "docx"
  - "html"
```
