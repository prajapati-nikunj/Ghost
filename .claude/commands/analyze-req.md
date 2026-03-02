# /analyze-req

Run requirement analysis only. For full pipeline use `/start-project`.

## Usage
```
/analyze-req [raw requirements or idea]
```

## Pre-condition
State: `DRAFT` or `ANALYZING`

## Flow
Conductor → `requirement-analyzer`:
- Extract: FUNCTIONAL, NON_FUNCTIONAL, TECHNICAL, BUSINESS, SECURITY requirements
- Define user stories with Given/When/Then AC
- Flag ambiguities in Ambiguity Register
- Generate Mermaid user flow diagrams
- Write `docs/artifacts/rad.md`
- State → `ANALYZED`

**Next**: `/generate-arch`
