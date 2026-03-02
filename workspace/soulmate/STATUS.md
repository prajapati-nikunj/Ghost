# Project Workspace Status: SoulMate

## Identification
- **Project Name**: SoulMate
- **Goal**: AI-Native Requirement Analysis Engine (MVP)
- **State**: `ANALYZED` (from [CLAUDE.md](../../.claude/CLAUDE.md))
- **Team**: Requirement Analyzer, Architect, Code Generator, QA Engine

## Stack (from [ADRs](../../docs/architecture/adr/))
- **Frontend**: Next.js + Tailwind (Atomic Design)
- **Backend**: Node.js + Express (Clean Architecture)
- **Mobile (iOS)**: SwiftUI (MVVM)
- **Mobile (Android)**: Kotlin + Jetpack Compose (MVVM)
- **Database**: PostgreSQL (Prisma)
- **Infrastructure**: AWS (EKS / RDS)

## Requirement Matrix (from [RAD](../../docs/epics/soulmate_rad.md))
- [x] Functional: User Auth, RAD Generation, Project Scoring.
- [x] Non-Functional: < 5s Analysis Time, EARS Compliance.
- [ ] Technical: Monorepo Setup (@soulmate/api, @soulmate/web).

## Current Blockers
- [ ] Finalizing the OpenAPI 3.1 specification for cross-platform sync.
- [ ] Provisioning the AWS EKS staging environment (Terraform).

## Next Sprint
1. `/generate-arch`: Define the shared domain layer for the monorepo.
2. `/build-mvp`: Scaffold the backend and web frontend base structures.
