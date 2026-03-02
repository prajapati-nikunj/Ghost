# Next.js SSR Patterns

## Server Components (default in App Router)
```tsx
// app/todos/page.tsx — runs on server
export default async function TodosPage() {
  const todos = await db.todo.findMany();
  return <TodoList todos={todos} />;
}
```

## Client Components
```tsx
"use client";
// Only use when you need useState, useEffect, event handlers
export function AddTodoButton() {
  const [open, setOpen] = useState(false);
  return <button onClick={() => setOpen(true)}>Add Todo</button>;
}
```

## Server Actions
```tsx
"use server";
export async function createTodo(formData: FormData) {
  const title = formData.get("title") as string;
  await db.todo.create({ data: { title } });
  revalidatePath("/todos");
}
```
