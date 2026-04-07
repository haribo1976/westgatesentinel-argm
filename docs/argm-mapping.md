# ARGM: Cross-Framework Mapping

**Version:** 2.0
**Licence:** CC-BY-SA 4.0

> ARGM adopts CMMI's staged maturity structure. The parallel numbering is by design, not coincidence. Cross-framework mappings below show where ARGM levels correspond to established governance tiers — they are alignment aids, not equivalence claims.

---

## ARGM to NIST CSF 2.0 Implementation Tiers

| ARGM Level | NIST CSF Tier | Rationale |
|-----------|---------------|-----------|
| 0 - Ungoverned | Precedes Tier 1 | Tier 1 (Partial) assumes some risk awareness. Level 0 assumes none. NIST CSF does not define a tier below Tier 1; this mapping acknowledges the gap. |
| 1 - Instructed | Tier 1 - Partial | Ad hoc, reactive, inconsistent. |
| 2 - Secured | Tier 2 - Risk Informed | Security controls informed by risk awareness. |
| 3 - Controlled | Tier 2 - Risk Informed | Autonomous operation controls extend risk-informed practice to agent behaviour. |
| 4 - Aligned | Tier 3 - Repeatable | Business-integrated governance with consistent processes. |
| 5 - Governed | Tier 3 - Repeatable | Formalised, auditable, cross-agent. |
| 6 - Autonomous | Tier 4 - Adaptive | Self-monitoring, continuous assurance. |

## ARGM to CMMI Maturity Levels

ARGM adopts CMMI's staged maturity structure. This mapping is not coincidental — it is by design.

| ARGM Level | CMMI Level | Rationale |
|-----------|------------|-----------|
| 0 - Ungoverned | 0 Incomplete | No documented processes. |
| 1 - Instructed | 1 Initial | Documented but inconsistently followed. |
| 2 - Secured | 2 Managed | Planned, performed, measured security. |
| 3 - Controlled | 2 Managed (upper) | Autonomous operation managed and controlled. |
| 4 - Aligned | 3 Defined | Organisational standard processes with business context. |
| 5 - Governed | 4 Quantitatively Managed | Quantitative targets, cost budgets, compliance metrics. |
| 6 - Autonomous | 5 Optimizing | Continuous improvement through automated monitoring. |

## ARGM to NIST AI RMF Functions

| ARGM Level | GOVERN | MAP | MEASURE | MANAGE |
|-----------|--------|-----|---------|--------|
| 0 - Ungoverned | No governance structures exist | No risk context identified | No measurement capability | No risk management |
| 1 - Instructed | Instructions exist but are informally applied | Agent capabilities and limitations partially documented | No systematic measurement | Incident response is ad hoc |
| 2 - Secured | Security policies govern agent access and secrets | Attack surface and input vectors mapped | Security scans and secret detection in place | Security incidents have defined response procedures |
| 3 - Controlled | Autonomous operation policies define scope and limits | Agent operational boundaries mapped with turn limits and dry-run defaults | Runtime metrics (turns, timeouts, write counts) tracked | Destructive operations blocked; escalation paths defined |
| 4 - Aligned | Business-integrated governance with value alignment directives | Agent capabilities mapped to business value tiers and revenue priorities | Cost, quality, and delivery metrics measured per engagement | Scope drift and priority conflicts actively managed |
| 5 - Governed | Unified governance across all agents with drift detection | All agent capabilities, gaps, and compensating controls documented | Quantitative compliance metrics with thresholds and alerting | Cross-agent conflict resolution and audit trail maintained |
| 6 - Autonomous | Self-governing with automated policy adaptation | Continuously updated capability and risk maps | Automated measurement with anomaly detection | Automated risk response with human override capability |

## ARGM to ISO 42001 Clauses

> **Note:** ISO 42001 clauses are concurrent requirements within a management system, not sequential maturity stages. This mapping shows where ARGM assessment evidence may support ISO 42001 compliance, not a maturity equivalence.

| ISO 42001 Clause | ARGM Levels Contributing Evidence | Notes |
|------------------|----------------------------------|-------|
| 4. Context of the organisation | 1, 3, 4 | Level 1 establishes agent context; Level 3 defines operational boundaries; Level 4 integrates business context |
| 5. Leadership | 1, 4, 5 | Level 1 sets direction via instructions; Level 4 aligns to business strategy; Level 5 formalises cross-agent leadership |
| 6. Planning | 2, 3, 4 | Level 2 plans security controls; Level 3 plans autonomous operation; Level 4 plans business alignment |
| 7. Support | 1, 2, 5 | Level 1 provides governance files; Level 2 provides security tooling; Level 5 provides audit infrastructure |
| 8. Operation | 2, 3, 4, 5 | Level 2 operates security controls; Level 3 operates turn limits and dry-run; Level 4 operates value-aligned workflows; Level 5 operates unified governance |
| 9. Performance evaluation | 3, 5, 6 | Level 3 tracks runtime metrics; Level 5 measures compliance quantitatively; Level 6 automates evaluation |
| 10. Improvement | 5, 6 | Level 5 identifies improvement via audit; Level 6 implements continuous automated improvement |

## ARGM to AISM (Cyber Strategy Institute)

| ARGM Level | AISM Level | Overlap | Divergence |
|-----------|-----------|---------|------------|
| 0 - Ungoverned | Chaos | Both describe ungoverned state | AISM includes NHI sprawl; ARGM focuses on runtime behaviour |
| 1 - Instructed | Chaos/Visibility boundary | ARGM addresses instruction quality; AISM addresses asset visibility | AISM's Ledger pillar starts earlier |
| 2 - Secured | Visibility/Governance boundary | Both include input sanitisation, circuit breakers | AISM's five pillars cover security more broadly |
| 3 - Controlled | Governance (lower) | Both establish operational controls | AISM does not address autonomous operation limits (turn caps, dry-run defaults) |
| 4 - Aligned | Governance (upper) | Both establish organisational governance | AISM does not include business value alignment or cost governance |
| 5 - Governed | Control | Both describe comprehensive frameworks | AISM has 128 controls; ARGM has prime directives with drift detection |
| 6 - Autonomous | Sovereignty | Both describe self-governing capability | AISM includes cryptographic identity; ARGM focuses on automated assurance |

## ARGM to Microsoft Agentic AI Adoption Maturity Model

| ARGM Level | Microsoft Level | Key Difference |
|-----------|----------------|----------------|
| 0 - Ungoverned | Below 100 | Microsoft assumes experimentation; ARGM assumes nothing |
| 1 - Instructed | 100 - Initial | Microsoft is adoption; ARGM is governance |
| 2 - Secured | 200 - Repeatable | Microsoft does not prescribe specific security controls |
| 3 - Controlled | 200 - Repeatable (upper) | ARGM prescribes autonomous operation controls; Microsoft does not distinguish |
| 4 - Aligned | 300 - Defined | ARGM prescribes cost governance and value tiers |
| 5 - Governed | 400 - Capable | ARGM prescribes autonomous operation controls and cross-agent audit |
| 6 - Autonomous | 500 - Efficient | ARGM requires self-monitoring; Microsoft requires agent-first culture |

---

## Generic Agent Mapping Guide

How to map D0-D6 directives to any coding agent, regardless of vendor.

### 1. Governance file

Identify where the agent reads instructions on startup (system prompt, config file, `CLAUDE.md`, `AGENTS.md`, or equivalent). Place D0-D6 directive blocks there. If the agent supports multiple instruction files, use one file per directive for maintainability.

### 2. Hook integration

Identify the pre-commit or pre-action hook mechanism available in the development environment. Use for D1 enforcement (secret scanning, prohibited pattern detection). The hook is environment-level, not agent-level — a single `.git/hooks/pre-commit` serves all agents operating in the same repository.

### 3. Turn limit mechanism

Check for a native `--max-turns` equivalent or timeout flag. If absent, implement an external process wrapper that counts agent iterations and terminates at the configured limit. This is required for D2 compliance in any unattended execution.

### 4. Dry-run pattern

Check for a native dry-run or sandbox mode. If absent, implement at the task runner level: intercept write operations and require an explicit `--live` flag for execution. Default to dry-run for all unattended runs.

### 5. Permission scoping

Identify the tool or permission restriction mechanism (allowlists, deny rules, sandbox flags). Use for D2 enforcement: restrict which tools, files, and external APIs the agent may access during autonomous operation.

### 6. Log integration

Identify where the agent logs actions (stdout, log files, structured output). Configure for D2 write logging requirements: every write operation must record timestamp, operation type, target, and outcome. Ensure no PII appears in logs.
