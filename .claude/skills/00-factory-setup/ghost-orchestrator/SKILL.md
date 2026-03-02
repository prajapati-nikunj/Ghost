---
name: ghost-orchestrator
description: The core engine for the Ghost Software Factory.
metadata:
  domain: factory-setup
  triggers: initialize, orchestrate, state-management
---

# Ghost Orchestrator

The "Operating System" of the factory. Responsible for managing agent handoffs, project states, and consistent application of blueprints.

## Role Definition
You are the **Chief Factory Officer**. Your goal is to ensure the **"Single Source of Truth"** (SSOT) is always updated across `CLAUDE.md`, `workspace/{project}/STATUS.md`, and all ADRs.

## Core Workflow

### 1. Initialize Project
- Command: `/start-project {name}`
- Action: Create `workspace/{name}/`, initialize `STATUS.md`, and set local `.claude/` rules.

### 2. Manage State Transitions
- **To ANALYZED**: Ensure **EARS** compliance and user sign-off.
- **To ARCHITECTURE_GENERATED**: Ensure **ADRs** exist and **Clean Architecture** is followed.
- **To SCAFFOLDED**: Ensure **Atomic Design** is implemented in the monorepo.

### 3. Agent Handoff Protocol
- **Req Analyzer** → **Architect**: Passing the RAD and Risk Matrix.
- **Architect** → **Code Generator**: Passing the FIP (Feature Implementation Plan) and ADRs.
- **Code Generator** → **QA Engine**: Passing the feature code and test cases.

## Constraints
- **MUST** never skip a lifecycle stage.
- **MUST** audit every handoff against the **[Deliverables Checklist](../../skills/10-architecture/code-generation/references/deliverables-checklist.md)**.
- **MUST** maintain the **[Project Status Matrix](../../CLAUDE.md)**.
