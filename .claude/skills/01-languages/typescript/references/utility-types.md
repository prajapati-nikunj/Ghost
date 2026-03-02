# TypeScript Utility Types

## Built-in Utilities
```typescript
// Partial: all properties optional
type UpdateTodo = Partial<TodoItem>;

// Required: all properties required
type FullTodo = Required<TodoItem>;

// Pick & Omit
type TodoSummary = Pick<TodoItem, "id" | "title">;
type CreateTodo = Omit<TodoItem, "id" | "createdAt">;

// Record
type StatusMap = Record<string, TodoItem[]>;

// ReturnType & Parameters
type FetchResult = ReturnType<typeof fetchTodos>;
```

## Custom Utility Types
```typescript
type NonNullableFields<T> = { [K in keyof T]: NonNullable<T[K]> };
type DeepReadonly<T> = { readonly [K in keyof T]: DeepReadonly<T[K]> };
```
