---
name: MVP_BUILDER
description: Architecture → reviewed, tested, secured, documented code
---

# MVPBuilder Workflow

**Trigger**: `/mvp-builder` or Conductor when state=`ARCHITECTURE_GENERATED`
**States**: `ARCHITECTURE_GENERATED → SCAFFOLDED → REVIEWED → QA_PASSED → SECURED → DOCUMENTED`

## Execution Plan

```
Step 1 [PARALLEL]
  code-generator (backend)        code-generator (frontend)
  Skills: Fullstack Guardian      Skills: Atomic Design rules
  IN:  sad.md + rad.md            IN:  sad.md + rad.md
  OUT: src/core/ use-cases/       OUT: src/presentation/
       interface/ infrastructure/      atoms→molecules→organisms→pages
  → SCAFFOLDED (lint must pass)

Step 2 [sequential]
  code-reviewer
  Skills: Architecture Designer + Security Checklist
  IN:  src/ + sad.md
  OUT: docs/artifacts/review-report.md
  0 blockers → REVIEWED | blockers > 0 → back to Step 1 (max 3×)

Step 3 [PARALLEL — both after REVIEWED]
  qa-engine                        security-auditor (was: AUDIT_PRO)
  Skills: Test Master              Skills: Security Specialist + The Fool
  IN:  src/ + sad.md               IN:  src/ + package manifest
  OUT: qa-report.md                OUT: security-report.md
  Pass: coverage≥80%, 0 failures   Pass: 0 CRITICAL, 0 HIGH
  fail → back to Step 1 (max 3×)   fail → back to Step 1 (max 2×)
  both pass → SECURED

Step 4 [sequential]
  tech-writer
  IN:  src/ + sad.md + qa-report.md
  OUT: README.md, docs/api/, docs/architecture/ADL.md, CHANGELOG.md
  → DOCUMENTED
```

## Completion Output
```
MVP BUILDER COMPLETE
✅ Code: N files | ✅ Review: 0 blockers | ✅ QA: N% | ✅ Security: 0 critical | ✅ Docs
Next: /deploy-ops
```
