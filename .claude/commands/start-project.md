# /start-project

Primary entry point. Runs the full Ghost factory pipeline end-to-end.

## Usage
```
/start-project [name] — [brief description]
```

## What Happens
Conductor takes control and runs all 3 workflows autonomously:
1. **ReqEngine** → RAD + SAD + estimate + backlog
2. **MVPBuilder** → code + review + QA + security + docs
3. **[HUMAN GATE]** → type `APPROVE` to continue
4. **DeployOps** → Docker + IaC + Kubernetes + monitoring → live

## Resume Behavior
If `docs/artifacts/project-state.json` exists with non-DRAFT status, Conductor resumes from last known state.

## Agents Involved
`conductor` → `req-analyzer` → `architect`∥`effort-estimator` → `product-manager` → `code-gen`×2 → `code-reviewer` → `qa-engine`∥`security-auditor` → `tech-writer` → `devops-automator`
