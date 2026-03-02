# /generate-arch

Run architecture + effort estimation (parallel). Requires `rad.md`.

## Pre-condition
State: `ANALYZED` · `docs/artifacts/rad.md` must exist.

## Flow
Conductor fires in **parallel**:
- `architect` → `docs/artifacts/sad.md` (Clean Architecture + ADRs + API contracts + Mermaid diagrams)
- `effort-estimator` → `docs/artifacts/effort-estimate.md` (6-dim risk score + PERT + sprint plan)

Then Conductor applies The Fool stress-test on SAD.
State → `ARCHITECTURE_GENERATED`

**Next**: `/build-mvp` or `/mvp-builder`
