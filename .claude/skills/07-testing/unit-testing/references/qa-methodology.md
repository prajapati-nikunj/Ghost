# QA Methodology

## Testing Pyramid
```
         ╱╲
        ╱ E2E ╲        (Few — slow, expensive, high confidence)
       ╱────────╲
      ╱Integration╲    (Some — medium speed, database/API)
     ╱──────────────╲
    ╱  Unit Tests     ╲  (Many — fast, isolated, cheap)
   ╱────────────────────╲
```

## Test Types
| Type | Scope | Speed | Dependencies |
|---|---|---|---|
| Unit | Single function/class | < 10ms | None (mocked) |
| Integration | Multiple modules + DB | < 1s | Database, cache |
| E2E | Full user flow | < 30s | Everything |
| Performance | Load/stress | Minutes | Full environment |

## Shift-Left Testing
Test early, test often:
- Write tests during development (not after).
- Run tests in CI on every PR.
- Security scanning in CI pipeline.

## Quality Gates
- [ ] All tests pass.
- [ ] Code coverage ≥ 80%.
- [ ] No critical/high severity bugs.
- [ ] No new security vulnerabilities.
- [ ] Performance baselines met.
