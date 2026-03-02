# Ghost Factor Execution Guide - TODO Example

This file provides a structured example of how to execute project phases within the **Ghost AI-Native Software Factory**. It serves as a living document to track progress and guide the AI agents through the autonomous pipeline.

## 🚀 Current Execution State: `INITIALIZING`
- **Project**: [Example Project Name]
- **Target Status**: `ANALYZED`
- **Last Command**: `/start-project`

---

## 📋 Execution Checklist

### Phase 1: ReqEngine (Requirement Analysis & Architecture)
**Objective**: Build the RAD (Requirement Analysis Document) and SAD (System Architecture Design).

- [ ] **Collect Requirements** (`/analyze-req`)
  - [ ] Persona identification and user value mapping.
  - [ ] EARS-syntax functional requirement drafting.
  - [ ] Non-functional performance/security constraints.
- [ ] **Architecture Design** (`/generate-arch`)
  - [ ] Define Monorepo structure (Apps/Packages).
  - [ ] Map Domain Entities and Use Cases.
  - [ ] Select Tech Stack components (Next.js, Node, PostgreSQL).
- [ ] **Effort Estimation**
  - [ ] Risk scoring (Complexity, Scale, Security).
  - [ ] PERT-based timeline estimation.
  - [ ] Product backlog (MoSCoW) creation.

### Phase 2: MVPBuilder (Generation & Verification)
**Objective**: Produce production-ready code with full test coverage.

- [ ] **Code Generation** (`/build-mvp`)
  - [ ] Scaffold base architecture (Clean Architecture layers).
  - [ ] Implement UI Components (Atomic Design standard).
  - [ ] Core business logic and API implementation.
- [ ] **Quality Control** (`/run-qa`)
  - [ ] Automated Code Review (0 BLOCKERs policy).
  - [ ] Performance and Security Audit (OWASP Top 10).
  - [ ] Unit & Integration testing (Target: 80% Coverage).
- [ ] **Documentation**
  - [ ] API Documentation (OpenAPI/Swagger).
  - [ ] README and CHANGELOG updates.

### Phase 3: DeployOps (Infrastructure & Launch)
**Objective**: Deploy to production with monitoring.

- [ ] **Infrastructure Provisioning**
  - [ ] Dockerization of all services.
  - [ ] Terraform/IaC scripts generation.
- [ ] **Deployment Execution**
  - [ ] CI/CD pipeline triggering (GitHub Actions).
  - [ ] Kubernetes/Cloud deployment.
- [ ] **Post-Launch Verification**
  - [ ] Smoke tests and health checks.
  - [ ] Monitoring dashboard setup (Prometheus/CloudWatch).

---

## 🛠 How to Execute
To proceed with this project, run the relevant slash command in the chat:

1. **Start Full Pipeline**:
   ```bash
   /start-project "Project Name" — "Detailed description including goals and stack."
   ```

2. **Run Individual Phase**:
   - `/req-engine`: Triggers the analysis and architecture suite.
   - `/mvp-builder`: Starts the code generation and QA process.
   - `/deploy-ops`: Initiates infrastructure and deployment.

3. **Verify Quality**:
   ```bash
   /run-qa
   ```

---

## 📝 Example TODO Update (During Execution)
*When an agent completes a task, it updates the state here:*

- [x] **Requirement Analysis** (RAD saved to `docs/artifacts/rad.md`)
- [x] **Architecture Blueprint** (SAD saved to `docs/artifacts/sad.md`)
- [/] **Code Generation** (In Progress: `apps/api/src/use-cases/`)
- [ ] **QA Audit** (Pending)

---
> [!TIP]
> Always verify the `docs/artifacts/project-state.json` file for the programmatic single source of truth.
