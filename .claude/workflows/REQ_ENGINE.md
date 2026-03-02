---
name: REQ_ENGINE
description: Raw input → structured specs + architecture + estimates + backlog
---

# ReqEngine Workflow

**Trigger**: `/req-engine` or Conductor when state=`DRAFT`
**States**: `DRAFT → ANALYZING → ANALYZED → DESIGNING → ARCHITECTURE_GENERATED → ESTIMATING → ESTIMATED`

## Execution Plan

```
Step 1 [sequential]
  requirement-analyzer
  IN:  raw user input
  OUT: docs/artifacts/rad.md
  → state: ANALYZED

Step 2 [PARALLEL — fire simultaneously]
  architect                    effort-estimator
  IN:  rad.md                  IN:  rad.md
  OUT: docs/artifacts/sad.md   OUT: docs/artifacts/effort-estimate.md
  → state: ARCHITECTURE_GENERATED + ESTIMATED

Step 3 [sequential, after Step 2]
  product-manager
  IN:  rad.md + sad.md + effort-estimate.md
  OUT: docs/artifacts/product-backlog.md

Step 4 [conductor applies The Fool skill]
  IN:  sad.md + effort-estimate.md
  OUT: risks appended to sad.md § Risk Review
```

## Exit Criteria
All 4 artifacts exist and are non-empty. Conductor updates `project-state.json`.

## Completion Output
```
REQ ENGINE COMPLETE
✅ RAD: N requirements | N user stories
✅ SAD: [stack] | N ADRs
✅ Estimate: N/100 risk | N sprints
✅ Backlog: N stories | N epics
Next: /mvp-builder
```
