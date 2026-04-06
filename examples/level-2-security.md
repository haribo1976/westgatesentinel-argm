# Example: Level 2 Security Controls Configuration

**ARGM Level:** 2 — Secured
**Purpose:** Illustrative example of the security controls that must be in place at Level 2

This example shows the shape of Level 2 security configuration across the key control areas. It is representative, not prescriptive. Adapt to your stack and environment.

---

## What Level 2 Requires

Level 2 adds a security layer on top of Level 1 instructional governance. Controls must exist as enforced technical mechanisms, not solely as instructions in a governance document.

Key control areas:

1. Secrets management
2. Pre-commit scanning
3. CORS policy
4. Rate limiting
5. Injection defence
6. Branch protection
7. Least privilege
8. Credential rotation

---

## Representative Configuration Shapes

### Secrets Management

```bash
# .gitignore — minimum entries
.env
.env.*
.dev.vars
secrets.*
credentials.*
*.pem
*.key
```

```bash
# Correct pattern: secrets from environment
SECRET_VALUE = os.environ.get("SECRET_VALUE")
# or
const value = process.env.SECRET_VALUE

# Incorrect pattern: never do this
SECRET_VALUE = "sk_live_abc123"  # hardcoded — Level 0 behaviour
```

### Pre-Commit Scanning

```yaml
# .pre-commit-config.yaml shape
repos:
  - repo: [SECRET_SCANNER_REPO]
    hooks:
      - id: [SCANNER_HOOK_ID]
        # Patterns to detect: sk_, pk_, eyJ, API_KEY=, SECRET=,
        # Bearer, client_secret=, PRIVATE_KEY, Authorization:
```

### CORS Policy Shape

```javascript
// Correct: specific origins
cors({ origin: ['https://[TRUSTED_ORIGIN_1]', 'https://[TRUSTED_ORIGIN_2]'] })

// Incorrect: wildcard — never in production
cors({ origin: '*' })
```

### Rate Limiting Shape

```javascript
// Authentication endpoints: 5 attempts per minute per IP (default)
rateLimit({
  windowMs: 60 * 1000,
  max: 5,
  // log and alert on breach
})
```

---

## Gaps to Address for Level 3

To progress to Level 3, the security foundation must be supplemented with:

- Value alignment tiers and scope boundaries
- Cost governance (token budgets, threshold alerts)
- Delivery standards and output quality gates
- Conflict resolution order

See [`level-3-directives.md`](level-3-directives.md) for a Level 3 example.
