# /run-qa

Run QA + security audit in parallel. Standalone or called by MVPBuilder.

## Pre-condition
State: `SCAFFOLDED` or `REVIEWED` · `src/` must exist.

## Flow
Conductor fires in **parallel**:

**qa-engine**
- Generate + run: unit tests (use cases + entities), integration tests (API), E2E (critical flows)
- Produce coverage report
- OUT: `docs/artifacts/qa-report.md`
- Pass: coverage ≥ 80%, 0 failures

**security-auditor**
- OWASP Top 10 audit + attack simulation + CVE dependency scan
- OUT: `docs/artifacts/security-report.md`
- Pass: 0 CRITICAL, 0 HIGH

Both pass → state `SECURED`. Either fails → surface report with fix guidance.
