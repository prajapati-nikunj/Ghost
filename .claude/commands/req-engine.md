# /req-engine

Run analysis phase only: requirements → architecture → estimates → backlog.

## Pre-condition
State: `DRAFT` or `ANALYZED`

## Flow
Conductor → `REQ_ENGINE` workflow:
- `requirement-analyzer` → `rad.md`
- `architect` ∥ `effort-estimator` → `sad.md` + `effort-estimate.md`
- `product-manager` → `product-backlog.md`
- The Fool stress-test on SAD

## Output
`docs/artifacts/`: rad.md · sad.md · effort-estimate.md · product-backlog.md

**Next**: `/mvp-builder`
