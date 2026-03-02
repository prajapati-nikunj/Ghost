# /mvp-builder

Run build phase: code → review → QA + security (parallel) → docs.

## Pre-condition
State: `ARCHITECTURE_GENERATED` · `sad.md` and `rad.md` must exist.

## Flow
Conductor → `MVP_BUILDER` workflow:
- `code-gen`×2 (backend ∥ frontend) → `src/`
- `code-reviewer` → `review-report.md` (auto-retry on blockers, max 3×)
- `qa-engine` ∥ `security-auditor` → `qa-report.md` + `security-report.md`
- `tech-writer` → README + API docs + CHANGELOG

## Output
`src/` + `docs/artifacts/`: review-report.md · qa-report.md · security-report.md · tech-docs.md

**Next**: `/deploy-ops`
