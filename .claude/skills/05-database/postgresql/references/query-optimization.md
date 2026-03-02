# PostgreSQL Query Optimization

## EXPLAIN ANALYZE
```sql
EXPLAIN ANALYZE SELECT * FROM todos WHERE user_id = 'abc' AND completed = false ORDER BY created_at DESC;
```

## Common Optimizations
1. **Use indexes for WHERE, JOIN, ORDER BY columns**.
2. **Avoid SELECT ***: Specify only needed columns.
3. **Use LIMIT**: Always paginate large result sets.
4. **Batch inserts**: Use `INSERT INTO ... VALUES (...), (...), (...)`.
5. **Connection Pooling**: Use PgBouncer or built-in pool (Prisma, SQLAlchemy).

## Anti-Patterns
- N+1 queries (use JOINs or batch loading).
- Missing indexes on foreign keys.
- Using `LIKE '%term%'` without full-text search index.
- Not using `RETURNING` on INSERT/UPDATE.
