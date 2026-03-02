# Ghost Orchestration Workflows

This directory defines the high-level orchestration flows that chain multiple agents and skills together to achieve complex project objectives.

## Core Workflows

### 1. [Requirement Engine (ReqEngine)](./REQ_ENGINE.md)
**Objective**: Convert raw ideas into refined, stress-tested functional specifications.
**Chain**: `Requirement Analyzer` (Feature Forge) → `The Fool` (Stress-testing) → `Architect` (ADR Creation).

### 2. [MVP Builder (MVPBuilder)](./MVP_BUILDER.md)
**Objective**: Transform specifications into production-ready, verified code.
**Chain**: `Architect` (System Design) → `Code Generator` (Implementation) → `QA Engine` (Verification).

### 3. [Deployment Pipeline (DeployOps)](./DEPLOY_OPS.md)
**Objective**: Move verified code from repository to production infrastructure.
**Chain**: `QA Engine` (Final Audit) → `DevOps Automator` (IaC & CI/CD) → `Platform Specialist` (Cloud Provisioning).
