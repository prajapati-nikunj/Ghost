# Blueprint: Clean Architecture (Node/React/Monorepo)

## Purpose
Standardizes the structure for full-stack monorepos produced by the Ghost factory.

## Directory Structure
```
workspace/{{project_name}}/
├── apps/
│   ├── web/ (Next.js + Tailwind + Atomic Design)
│   ├── mobile-ios/ (SwiftUI + MVVM)
│   ├── mobile-android/ (Kotlin + Jetpack Compose + MVVM)
│   └── api/ (Node.js + Express + Clean Architecture)
├── packages/
│   ├── core/ (Domain Entities + Types)
│   ├── shared-ui/ (Atomic Design Components)
│   └── database/ (Prisma Schema + Migrations)
├── docs/ (RAD, FIP, ADRs)
└── .claude/ (Local project rules)
```

## Layer-by-Layer Standards

### 1. Domain (@{{project_name}}/core)
Pure TS entities and domain errors. Zero imports.
- `src/entities/{{entity_name}}.ts`
- `src/errors/{{error_name}}.ts`

### 2. Use Cases (@{{project_name}}/api)
Business logic orchestration.
- `src/use-cases/{{feature}}/{{interactor_name}}.ts`

### 3. Interface (@{{project_name}}/api)
- `src/controllers/{{controller_name}}.ts`
- `src/repositories/{{repo_interface}}.ts`

### 4. Infrastructure (@{{project_name}}/api & @{{project_name}}/database)
- `src/infrastructure/db/{{repo_impl}}.ts`
- `src/infrastructure/auth/{{auth_impl}}.ts`

## UI Standard (Atomic Design)
All UI must be stored in `@{{project_name}}/shared-ui` or `apps/web/components/atoms`.
```
src/components/
├── atoms/
├── molecules/
├── organisms/
├── templates/
└── pages/
```
