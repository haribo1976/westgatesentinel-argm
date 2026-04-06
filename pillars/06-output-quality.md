# Pillar 06 — Output Quality

## Purpose

Ensure that every deliverable produced by the agent meets the organisation's quality bar before it reaches a stakeholder. Quality means: correctly formatted, executive-ready, within word limits, produced within turnaround targets, and never raw or unformatted.

---

## Reasoning

An agent that produces technically correct but poorly formatted output creates rework. A stakeholder who receives an unformatted JSON blob instead of a branded report, or a 4,000-word executive summary instead of a 400-word one, has not been served well. The quality failure is invisible in the task log but visible to the person who receives the output.

This pillar enforces quality at the output stage. It does not constrain how the agent works internally — only what it delivers.

---

## Rules

1. All deliverables must use the organisation's configured brand reference (logo, colour, font, header/footer) where the output format supports it.
2. Executive summaries must not exceed the configured word limit.
3. All deliverables must be produced within the configured turnaround target from task start.
4. The agent must not deliver raw output (unformatted JSON, bare markdown, plain text) unless the recipient has explicitly requested it.
5. If the agent cannot meet the turnaround target, it must notify the operator before the deadline, not after.
6. Quality checks must be applied before delivery, not after. The agent must self-review structured output against the output schema (Pillar 05) and human-readable output against this pillar's constraints before marking a task complete.

---

## Configurable Elements

```yaml
# output-quality configuration
# Replace all [PLACEHOLDER] values before deployment.

# Reference to the organisation's brand assets or style guide.
# Example: "brand/style-guide.md", "[BRAND_REFERENCE_URL]"
brand_reference: "[BRAND_REFERENCE]"

# Maximum word count for executive summaries.
# Example: 400
executive_summary_word_limit: "[EXECUTIVE_SUMMARY_WORD_LIMIT]"

# Target turnaround time from task start to delivery.
# Format: ISO 8601 duration. Example: PT4H (four hours), P1D (one business day)
turnaround_target: "[TURNAROUND_TARGET]"

# Whether raw output is ever permitted without explicit recipient request.
allow_raw_output: false

# Output formats that are considered "formatted" for the purposes of this pillar.
# Outputs in other formats will be flagged as raw.
formatted_output_types:
  - "pdf"
  - "docx"
  - "html"
  - "pptx"
  - "[ADDITIONAL_FORMATTED_TYPE]"
```

---

## Deployment Example

```yaml
brand_reference: "brand/style-guide.md"
executive_summary_word_limit: 400
turnaround_target: "PT4H"
allow_raw_output: false
formatted_output_types:
  - "pdf"
  - "docx"
  - "html"
```
