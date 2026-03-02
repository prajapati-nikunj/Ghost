# Clean TypeScript Patterns

## Domain Entity Pattern
```typescript
// core/entities/todo.entity.ts
export interface TodoEntity {
  readonly id: string;
  readonly title: string;
  readonly completed: boolean;
  readonly createdAt: Date;
  readonly userId: string;
}
```

## Use Case Pattern
```typescript
// use-cases/create-todo.use-case.ts
export interface CreateTodoRequest { title: string; userId: string; }

export interface CreateTodoUseCase {
  execute(request: CreateTodoRequest): Promise<TodoEntity>;
}
```

## Repository Interface Pattern
```typescript
// use-cases/ports/todo.repository.ts
export interface TodoRepository {
  findById(id: string): Promise<TodoEntity | null>;
  findAll(userId: string): Promise<TodoEntity[]>;
  save(todo: TodoEntity): Promise<TodoEntity>;
  delete(id: string): Promise<void>;
}
```

## Path Aliases (tsconfig.json)
```json
{
  "compilerOptions": {
    "paths": {
      "@core/*": ["src/core/*"],
      "@use-cases/*": ["src/use-cases/*"],
      "@adapters/*": ["src/adapters/*"],
      "@infra/*": ["src/infrastructure/*"]
    }
  }
}
```
