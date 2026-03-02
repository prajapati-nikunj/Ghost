# Ghost: AI-Native Software Factory

Ghost is a **fully AI-driven software factory** that takes a raw idea and autonomously produces a deployed, tested, documented, and monitored production system — with minimal human intervention.

## How It Works

```
You:    /start-project "E-commerce platform" — multi-vendor marketplace with payments

Ghost:  ┌─ ReqEngine (autonomous) ──────────────────────────────────────────┐
        │  requirement-analyzer → RAD (requirements + user stories)         │
        │  architect ∥ effort-estimator → SAD + risk/effort estimates        │
        │  product-manager → sprint backlog                                  │
        └───────────────────────────────────────────────────────────────────┘
        ┌─ MVPBuilder (autonomous) ─────────────────────────────────────────┐
        │  code-generator ×2 (backend ∥ frontend) → production code        │
        │  code-reviewer → review with auto-fix loops                       │
        │  qa-engine ∥ security-auditor → tests + OWASP audit (parallel)   │
        │  tech-writer → README + API docs + CHANGELOG                      │
        └───────────────────────────────────────────────────────────────────┘
        ⚡ HUMAN GATE: Review quality report → type APPROVE
        ┌─ DeployOps (autonomous) ──────────────────────────────────────────┐
        │  Docker + Terraform ∥ CI/CD + Kubernetes ∥ Monitoring (parallel) │
        │  Smoke tests → health checks → live deployment                    │
        └───────────────────────────────────────────────────────────────────┘

You:    Live URL + monitoring dashboard
```

## Quick Start

```bash
# Full pipeline — idea to deployed product
/start-project [name] — [description]

# Or step by step:
/req-engine     # Analysis: requirements + architecture + estimates + backlog
/mvp-builder    # Build: code + review + QA + security + docs
/deploy-ops     # Deploy: Docker + IaC + Kubernetes + monitoring
```

## Agent Roster

| Agent | Role | Phase |
|---|---|---|
| **Conductor** | Master orchestrator, drives the whole pipeline | All |
| **Requirement Analyzer** | RAD, user stories, EARS requirements | ReqEngine |
| **Architect** | SAD, Clean Architecture, ADRs, API contracts | ReqEngine |
| **Effort Estimator** | Risk scores, PERT estimates, sprint plan | ReqEngine |
| **Product Manager** | MoSCoW backlog, sprint mapping | ReqEngine |
| **Code Generator** | Full-stack implementation (×2 parallel) | MVPBuilder |
| **Code Reviewer** | Architecture + SOLID + security review | MVPBuilder |
| **QA Engine** | Unit + integration + E2E tests | MVPBuilder |
| **Security Auditor** | OWASP Top 10, CVE scan, attack simulation | MVPBuilder |
| **Tech Writer** | README, API docs, ADL, CHANGELOG | MVPBuilder |
| **DevOps Automator** | Docker, Terraform, Kubernetes, CI/CD, monitoring | DeployOps |

## Lifecycle States

```
DRAFT → ANALYZING → ANALYZED → DESIGNING → ARCHITECTURE_GENERATED
→ ESTIMATING → ESTIMATED → SCAFFOLDING → SCAFFOLDED
→ REVIEWING → REVIEWED → QA_RUNNING → QA_PASSED
→ SECURITY_AUDIT → SECURED → DOCUMENTING → DOCUMENTED
→ [HUMAN GATE] → DEPLOYING → COMPLETED
```

## Architecture & Standards

Ghost enforces strict quality standards on all generated code:

- **Clean Architecture** — Dependency rule strictly enforced across all 4 layers
- **Atomic Design** — UI: atoms → molecules → organisms → templates → pages
- **SOLID Principles** — Every class and module validated by Code Reviewer
- **OWASP Top 10** — Security Auditor audits every build
- **Test Coverage** — Minimum 80%, TDD where applicable
- **Performance** — Async I/O, indexed queries, caching strategies

## Project Structure

```
Ghost/
├── .claude/
│   ├── agents/              # 11 specialist AI agents
│   │   ├── conductor.md     # Master orchestrator
│   │   ├── requirement-analyzer.md
│   │   ├── architect.md
│   │   ├── effort-estimator.md
│   │   ├── product-manager.md
│   │   ├── code-generator.md
│   │   ├── code-reviewer.md
│   │   ├── qa-engine.md
│   │   ├── security-auditor.md
│   │   ├── tech-writer.md
│   │   └── devops-automator.md
│   ├── workflows/           # Multi-agent orchestration flows
│   │   ├── req-engine.md
│   │   ├── mvp-builder.md
│   │   └── deploy-ops.md
│   ├── commands/            # Slash command entry points
│   │   ├── start-project.md ← primary entry point
│   │   ├── req-engine.md
│   │   ├── mvp-builder.md
│   │   ├── deploy-ops.md
│   │   ├── analyze-req.md
│   │   ├── generate-arch.md
│   │   ├── build-mvp.md
│   │   └── run-qa.md
│   ├── skills/              # 66+ domain skill modules
│   └── rules/               # Coding standards and principles
├── docs/
│   ├── artifacts/           # Inter-agent communication contracts
│   │   ├── project-state.json  ← single source of truth
│   │   ├── rad-template.md
│   │   └── sad-template.md
│   ├── api/                 # Generated API documentation
│   └── architecture/        # ADRs and architecture logs
└── src/                     # Generated application code
```

## Granular Commands

For targeted control without the full pipeline:

| Command | What It Does |
|---|---|
| `/analyze-req [input]` | Requirements analysis only → RAD |
| `/generate-arch` | Architecture + effort estimation (parallel) → SAD + estimate |
| `/build-mvp` | Code generation only → src/ |
| `/run-qa` | QA + security audit (parallel) → reports |

## Integration

- **Atlassian**: Jira story creation, Confluence documentation sync
- **GitHub**: Actions CI/CD pipeline generation
- **Cloud**: AWS, GCP, Azure deployment via Terraform
- **Monitoring**: Prometheus, CloudWatch, or equivalent

---

*Ghost v2.0 — Built with the Conductor orchestration engine.*
