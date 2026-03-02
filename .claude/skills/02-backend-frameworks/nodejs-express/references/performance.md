# Node.js Performance

## Connection Pooling
```typescript
import { Pool } from "pg";
const pool = new Pool({ max: 20, idleTimeoutMillis: 30000, connectionTimeoutMillis: 5000 });
```

## Caching Strategy
```typescript
import Redis from "ioredis";
const redis = new Redis();

async function getCachedTodos(userId: string): Promise<TodoItem[]> {
  const cached = await redis.get(`todos:${userId}`);
  if (cached) return JSON.parse(cached);
  const todos = await db.query("SELECT * FROM todos WHERE user_id = $1", [userId]);
  await redis.setex(`todos:${userId}`, 300, JSON.stringify(todos)); // 5 min TTL
  return todos;
}
```

## Compression & Rate Limiting
```typescript
import compression from "compression";
import rateLimit from "express-rate-limit";

app.use(compression());
app.use(rateLimit({ windowMs: 15 * 60 * 1000, max: 100:  }));
```

## Clustering
```typescript
import cluster from "node:cluster";
import os from "node:os";

if (cluster.isPrimary) {
  for (let i = 0; i < os.cpus().length; i++) cluster.fork();
} else {
  startServer();
}
```
