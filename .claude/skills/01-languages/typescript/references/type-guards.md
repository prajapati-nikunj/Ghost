# TypeScript Type Guards

## typeof Guard
```typescript
function process(value: string | number): string {
  if (typeof value === "string") return value.toUpperCase();
  return value.toFixed(2);
}
```

## Custom Type Guard
```typescript
interface TodoItem { id: string; title: string; }
interface ErrorResponse { error: string; code: number; }

function isTodoItem(obj: unknown): obj is TodoItem {
  return typeof obj === "object" && obj !== null && "title" in obj;
}
```

## Assertion Functions
```typescript
function assertDefined<T>(val: T | undefined, name: string): asserts val is T {
  if (val === undefined) throw new Error(`${name} is undefined`);
}
```
