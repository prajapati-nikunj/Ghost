# GHOST: AI-Native Software Factory

## Single Command Entry
```
/start-project [name] — [description]
```
Conductor runs the full pipeline autonomously. Human input at kickoff + one pre-deploy APPROVE gate.

## Pipeline
```
/req-engine ──────────────────────────────────────────────────────────
  requirement-analyzer → architect ∥ effort-estimator → product-manager
  OUT: rad.md · sad.md · effort-estimate.md · product-backlog.md

/mvp-builder ─────────────────────────────────────────────────────────
  code-gen×2(parallel) → code-reviewer → qa-engine ∥ security-auditor → tech-writer
  OUT: src/ · review-report · qa-report · security-report · docs

[HUMAN GATE: APPROVE]

/deploy-ops ──────────────────────────────────────────────────────────
  Docker → Terraform ∥ CI/CD → K8s ∥ Monitoring → live deployment
  OUT: infra/ · .github/workflows/ · runbook.md · live URL
```

## Commands
| Command | Scope |
|---|---|
| `/start-project` | Full pipeline |
| `/req-engine` | Analysis phase |
| `/mvp-builder` | Build phase |
| `/deploy-ops` | Deploy phase |
| `/analyze-req` | Requirements only |
| `/generate-arch` | Architecture + estimates (parallel) |
| `/build-mvp` | Code generation only |
| `/run-qa` | QA + security (parallel) |

## Agents
| Agent | Phase | Output |
|---|---|---|
| conductor | All | project-state.json |
| requirement-analyzer | ReqEngine | rad.md |
| architect | ReqEngine | sad.md |
| effort-estimator | ReqEngine | effort-estimate.md |
| product-manager | ReqEngine | product-backlog.md |
| code-generator | MVPBuilder | src/ |
| code-reviewer | MVPBuilder | review-report.md |
| qa-engine | MVPBuilder | qa-report.md |
| security-auditor | MVPBuilder | security-report.md |
| tech-writer | MVPBuilder | README + API docs + CHANGELOG |
| devops-automator | DeployOps | Dockerfile + IaC + K8s + CI/CD |

## Lifecycle States
`DRAFT → ANALYZING → ANALYZED → DESIGNING → ARCHITECTURE_GENERATED → ESTIMATING → ESTIMATED → SCAFFOLDING → SCAFFOLDED → REVIEWING → REVIEWED → QA_RUNNING → QA_PASSED → SECURITY_AUDIT → SECURED → DOCUMENTING → DOCUMENTED → DEPLOYING → COMPLETED`

## Quality Gates (enforced by Conductor)
- Review: 0 BLOCKERs · QA: ≥80% coverage, 0 failures · Security: 0 CRITICAL, 0 HIGH
- Max retries per agent: 3

## Rules Applied to All Generated Code
- **Clean Architecture**: dependency rule — inward only, no exceptions
- **Atomic Design**: UI atoms → molecules → organisms → templates → pages
- **SOLID**: enforced by code-reviewer
- **OWASP Top 10**: enforced by security-auditor
- **Testing**: ≥80% coverage, Given/When/Then pattern

## Requirement Types
FUNCTIONAL · NON_FUNCTIONAL · TECHNICAL · BUSINESS · SECURITY

## Risk Dimensions (1-100)
COMPLEXITY · TIMELINE · SCALABILITY · SECURITY · DEPENDENCY · AMBIGUITY
