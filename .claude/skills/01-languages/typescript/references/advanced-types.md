# TypeScript Advanced Types

## Branded Types
```typescript
type UserId = string & { readonly __brand: "UserId" };
type TodoId = string & { readonly __brand: "TodoId" };

function createUserId(id: string): UserId { return id as UserId; }
```

## Discriminated Unions
```typescript
type Result<T> = 
  | { success: true; data: T }
  | { success: false; error: AppError };
```

## Template Literal Types
```typescript
type HttpMethod = "GET" | "POST" | "PUT" | "DELETE";
type ApiRoute = `/api/v1/${string}`;
```

## Mapped Types
```typescript
type ReadonlyEntity<T> = { readonly [K in keyof T]: T[K] };
type Optional<T> = { [K in keyof T]?: T[K] };
```
