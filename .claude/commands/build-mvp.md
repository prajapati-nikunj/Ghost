# /build-mvp

Run code generation only. For full build pipeline (+ review + QA + security + docs) use `/mvp-builder`.

## Pre-condition
State: `ARCHITECTURE_GENERATED` · `sad.md` and `rad.md` must exist.

## Flow
Conductor fires in **parallel**:
- `code-generator` (backend) → `src/core/`, `src/use-cases/`, `src/interface/`, `src/infrastructure/`
- `code-generator` (frontend) → `src/presentation/` (Atomic Design: atoms → pages)

Both: follow Clean Architecture, DI via constructors, no framework imports in Domain.
State → `SCAFFOLDED` (lint must pass)

**Next**: `/run-qa` for targeted validation, or `/mvp-builder` for full automated pipeline.
