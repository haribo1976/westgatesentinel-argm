# Example: Level 5 Governance Drift Detection Configuration

**ARGM Level:** 5 — Autonomous
**Purpose:** Illustrative example of the self-monitoring mechanisms required at Level 5

This example shows the shape of Level 5 governance infrastructure: drift detection, lint hooks, automated health reporting, and change control on governance files.

---

## What Level 5 Requires

Level 5 adds automated self-monitoring on top of the Level 4 framework. The governance framework monitors itself. An assessor can verify compliance at any point without triggering a manual audit.

Key mechanisms:

1. Governance drift detection (automated baseline comparison)
2. Lint hooks on governance files (structure, prohibited content, integrity)
3. Automated health reporting (weekly minimum)
4. Third-party isolation verification (automated scanning)
5. Change control on governance files (PR review required, force push blocked)
6. Governance versioning (semantic version, changelog)

---

## Representative Implementation Shapes

### Drift Detection Options

**Option A — Git-based hash comparison**
```bash
# Store baseline hash at a known-good state
git rev-parse HEAD:path/to/governance-file > .governance-baseline

# Check script: compare current hash to baseline
CURRENT=$(git rev-parse HEAD:path/to/governance-file)
BASELINE=$(cat .governance-baseline)
if [ "$CURRENT" != "$BASELINE" ]; then
  echo "GOVERNANCE DRIFT DETECTED"
  # trigger alert
fi
```

**Option B — CI/CD pipeline validation stage**
```yaml
# Governance validation job shape
governance-check:
  runs-on: [RUNNER]
  steps:
    - name: Validate governance file structure
      run: [GOVERNANCE_LINT_COMMAND]
    - name: Check for prohibited content
      run: [PROHIBITED_CONTENT_SCAN_COMMAND]
    - name: Verify conflict resolution order intact
      run: [CONFLICT_ORDER_CHECK_COMMAND]
```

**Option C — Scheduled audit**
```yaml
# Scheduled governance audit shape
schedule:
  - cron: '[CRON_EXPRESSION]'
jobs:
  governance-audit:
    steps:
      - name: Compare against baseline
      - name: Generate health report
      - name: Alert if deviation detected
```

### Lint Hook Shape

```bash
# Pre-commit hook shape for governance files
# Checks to include:
# 1. Required sections present in governance document
# 2. No hardcoded secrets (sk_, pk_, eyJ patterns)
# 3. No client names or tenant IDs
# 4. Conflict resolution order present and unconditional
# 5. Security non-negotiables not removed
```

### Automated Health Report Shape

```markdown
# Governance Health Report — [DATE]
Generated: [TIMESTAMP] | Next: [NEXT_SCHEDULED]

## Document Currency
- [FILE]: last changed [DATE], [N] days ago | Status: [HEALTHY/NEEDS ATTENTION]
- Review due: [DATE]

## Security Control Compliance
- Pre-commit scan: last triggered [DATE] | Result: [PASS/FAIL]
- Credential rotation: last rotated [DATE] | Status: [CURRENT/OVERDUE]
- CORS configuration: [COMPLIANT/NON-COMPLIANT]

## Business Alignment
- Tasks classified this period: [N] | Tier 1: [N] | Tier 2: [N] | Tier 3: [N] | Rejected: [N]
- Cost vs budget: [AMOUNT] / [BUDGET] ([PERCENTAGE]%)

## Autonomous Operation
- Turn limit adherence: [COMPLIANT/BREACH DETECTED]
- Dry-run default: [ACTIVE/INACTIVE]
- Write operations logged: [N]
```

### Change Control Configuration Shape

```yaml
# Branch protection shape for governance files
branch_protection:
  pattern: "main"
  require_pull_request_reviews: true
  dismiss_stale_reviews: true
  require_review_from: "[GOVERNANCE_OWNER_ROLE]"
  restrict_push_to_protected_branches: true
  block_force_pushes: true
  # Apply to governance file paths specifically via CODEOWNERS
```

```
# CODEOWNERS shape
[GOVERNANCE_FILE_PATH] @[GOVERNANCE_OWNER]
```
