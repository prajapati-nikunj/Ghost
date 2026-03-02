# /deploy-ops

Run deploy phase: Docker → IaC + CI/CD → K8s + monitoring → live.

## Usage
```
/deploy-ops [staging|production]
```

## Pre-condition
State: `DOCUMENTED` · qa-report: PASSED · security-report: PASSED

## Flow
Conductor validates pre-flight → presents human gate → on `APPROVE`:
- `devops-automator`: Dockerfile + docker-compose
- `devops-automator`: Terraform ∥ GitHub Actions CI/CD
- `devops-automator`: Kubernetes manifests ∥ Monitoring + runbook
- Deploy → smoke tests → health checks → COMPLETED

## Rollback
Any failure → auto-rollback + incident report surfaced to user.

**Output**: live URL + monitoring dashboard + `docs/runbook.md`
