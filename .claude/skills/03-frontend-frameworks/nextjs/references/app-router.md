# Next.js App Router

## File-Based Routing
```
app/
├── layout.tsx        # Root layout
├── page.tsx          # Home (/)
├── todos/
│   ├── page.tsx      # /todos
│   ├── [id]/
│   │   └── page.tsx  # /todos/:id
│   └── loading.tsx   # Loading UI
└── api/
    └── todos/
        └── route.ts  # API Route Handler
```

## Route Handlers
```tsx
// app/api/todos/route.ts
export async function GET() {
  const todos = await db.todo.findMany();
  return Response.json(todos);
}

export async function POST(request: Request) {
  const body = await request.json();
  const todo = await db.todo.create({ data: body });
  return Response.json(todo, { status: 201 });
}
```

## Middleware
```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  if (!request.cookies.get("session")) {
    return NextResponse.redirect(new URL("/login", request.url));
  }
}
export const config = { matcher: ["/todos/:path*"] };
```
