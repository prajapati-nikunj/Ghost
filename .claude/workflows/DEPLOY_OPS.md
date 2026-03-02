---
name: DEPLOY_OPS
description: Documented code → live deployed, monitored production system
---

# DeployOps Workflow

**Trigger**: `/deploy-ops` + human APPROVE. Conductor when state=`DOCUMENTED`.
**States**: `DOCUMENTED → [HUMAN GATE] → DEPLOYING → COMPLETED`

## Pre-flight (Conductor validates before gate)
- qa-report.md: PASSED · security-report.md: PASSED · tech-docs.md: COMPLETE

## Human Gate
```
GHOST DEPLOY GATE
✅ Review: 0 blockers | ✅ QA: N% | ✅ Security: 0 critical | ✅ Docs complete
Target: [env] | Risk: N/100
Type APPROVE to proceed or REJECT [reason].
```

## Execution Plan

```
Step 1 [sequential]  devops-automator — Docker
  Skills: Docker Expert
  OUT: Dockerfile (multi-stage), docker-compose.yml
  Gate: image builds, 0 CRITICAL CVEs in image scan

Step 2+3 [PARALLEL]
  devops-automator — Terraform IaC    devops-automator — CI/CD
  Skills: Terraform Engineer          Skills: CI/CD Pipeline
  OUT: infra/terraform/               OUT: .github/workflows/
  VPC, DB, cache, queues              lint→test→build→scan→deploy stages

Step 4+5 [PARALLEL after Steps 2+3]
  devops-automator — Kubernetes       devops-automator — Monitoring
  Skills: Kubernetes Specialist       Skills: Monitoring
  OUT: infra/k8s/                     OUT: infra/monitoring/ + docs/runbook.md
  Deployment/Service/Ingress/HPA      Prometheus alerts, structured logging

Step 6 [sequential — final]
  devops-automator — Deploy + Verify
  Actions: terraform apply → deploy → smoke tests → health checks
  → COMPLETED
```

## Rollback Protocol
Failure at any step → halt → auto-rollback → surface:
`DEPLOYMENT FAILED: [step] | Error: [x] | Rollback: EXECUTED | Fix: [action]`

## Completion Output
```
GHOST FACTORY COMPLETE
✅ Live URL: [url] | ✅ Monitoring: [url] | ✅ Runbook: docs/runbook.md
Pipeline: Requirements → Architecture → Code → QA → Security → Docs → Deploy
```
