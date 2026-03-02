# Node.js Error Handling

## Custom Error Classes
```typescript
export class AppError extends Error {
  constructor(
    public statusCode: number,
    public type: string,
    message: string,
    public detail?: string
  ) {
    super(message);
    this.name = "AppError";
  }
}

export class NotFoundError extends AppError {
  constructor(resource: string, id: string) {
    super(404, "not-found", `${resource} not found`, `${resource} with ID '${id}' does not exist`);
  }
}

export class ValidationError extends AppError {
  constructor(detail: string) {
    super(422, "validation-error", "Validation Error", detail);
  }
}
```

## Async Error Wrapper
```typescript
function asyncHandler(fn: (req: Request, res: Response, next: NextFunction) => Promise<void>) {
  return (req: Request, res: Response, next: NextFunction) => {
    fn(req, res, next).catch(next);
  };
}

// Usage
app.get("/todos/:id", asyncHandler(async (req, res) => {
  const todo = await todoRepo.findById(req.params.id);
  if (!todo) throw new NotFoundError("Todo", req.params.id);
  res.json(todo);
}));
```

## Global Error Handler
```typescript
app.use((err: Error, req: Request, res: Response, next: NextFunction) => {
  if (err instanceof AppError) {
    return res.status(err.statusCode).json({
      type: `https://api.example.com/errors/${err.type}`,
      title: err.message,
      status: err.statusCode,
      detail: err.detail,
      instance: req.originalUrl,
    });
  }
  console.error("Unhandled error:", err);
  res.status(500).json({ type: "internal-error", title: "Internal Server Error", status: 500 });
});
```
