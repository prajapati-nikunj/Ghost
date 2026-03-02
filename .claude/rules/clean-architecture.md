# Clean Architecture Standards

## Core Principles
1. **Dependency Rule**: Dependencies point inward. Inner layers (Domain) know nothing about outer layers (Data, UI).
2. **Separation of Concerns**: Each layer has a distinct responsibility.
3. **Independence**: The UI, Database, and Frameworks should be swap-able without affecting the business logic.

## Layer Definitions

### 1. Core (Domain)
Contains **Entities** and **Domain Errors**. Pure business logic with **ZERO external dependencies**.
- **Entities**: Business rules and objects with state.
- **Errors**: Domain-specific errors carrying HTTP status codes.

### 2. Use Cases (Application)
Orchestrates entities and external services. This is where the core functionality lives.
- **Interactors**: Executes specific business operations.
- **Interfaces**: Protocols for external needs (Repositories, AI services).

### 3. Interface (Adapters)
Converts data from external sources into the format used by the use cases.
- **Controllers**: Express/Rest handlers.
- **Middlewares**: Auth, Validation, Logging.
- **Presenters**: UI adapters (ViewModels).

### 4. Infrastructure (Frameworks)
Details and external concerns.
- **Database**: Prisma, SQL, Document stores.
- **Cache**: Redis, In-memory.
- **External**: Third-party APIs (OpenAI, AWS).

## The Dependency Rule
Dependencies must ALWAYS point inward. Outer layers (Infrastructure, Interface) know about inner layers (Use Case, Core), but inner layers MUST NOT import from outer ones. Use **Dependency Injection** via constructors.
