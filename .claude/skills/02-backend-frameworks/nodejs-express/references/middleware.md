# Node.js Express Middleware

## Error Handling Middleware
```typescript
function errorHandler(err: AppError, req: Request, res: Response, next: NextFunction) {
  const status = err.statusCode || 500;
  res.status(status).json({
    type: `https://api.example.com/errors/${err.type}`,
    title: err.message,
    status,
    detail: err.detail,
    instance: req.originalUrl,
  });
}
app.use(errorHandler);
```

## Auth Middleware
```typescript
function authenticate(req: Request, res: Response, next: NextFunction) {
  const token = req.headers.authorization?.split(" ")[1];
  if (!token) return res.status(401).json({ error: "Missing token" });
  try {
    req.user = jwt.verify(token, process.env.JWT_SECRET!);
    next();
  } catch { res.status(401).json({ error: "Invalid token" }); }
}
```

## Validation Middleware (Zod)
```typescript
import { z } from "zod";
const createTodoSchema = z.object({ title: z.string().min(1).max(255) });

function validate(schema: z.ZodSchema) {
  return (req: Request, res: Response, next: NextFunction) => {
    const result = schema.safeParse(req.body);
    if (!result.success) return res.status(422).json({ errors: result.error.issues });
    req.body = result.data;
    next();
  };
}
```
