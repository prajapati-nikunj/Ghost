---
name: AUDIT_PRO
description: Code Review and Security Audit Orchestration Flow
---

# AUDIT_PRO: Advanced Code Audit

**Chain**: `Architect` (Review) → `QA Engine` (Security/Perf) → `The Fool` (Stress test)

## Sequence

### Step 1: Architectural Integrity Review
- **Agent**: `Architect`
- **Skill**: [Architecture Designer]
- **Task**: Verify adherence to **Clean Architecture** patterns.
- **Output**: Structural audit report.

### Step 2: Automated Analysis
- **Agent**: `QA Engine`
- **Skill**: [Debugging Wizard]
- **Task**: Run linters and static analysis.
- **Output**: Static code quality metrics.

### Step 3: Security & Performance Deep Dive
- **Agent**: `QA Engine`
- **Skill**: [Security Specialist](file:///.claude/skills/09-security/authentication/SKILL.md)
- **Task**: Audit against the **[Security Checklist](file:///.claude/skills/10-architecture/code-generation/references/security-checklist.md)**.
- **Output**: Vulnerability and performance report.

### Step 4: Red-Teaming (The Fool)
- **Agent**: `The Fool`
- **Skill**: [The Fool]
- **Task**: Select a reasoning mode (e.g., Attack This) to find logical exploits.
- **Output**: Critical logic flaws or perverse incentives identified.
