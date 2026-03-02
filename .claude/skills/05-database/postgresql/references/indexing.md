# PostgreSQL Indexing

## Index Types
| Type | Use Case |
|---|---|
| B-tree (default) | Equality, range, sorting |
| Hash | Equality only |
| GIN | Full-text search, JSONB, arrays |
| GiST | Geometric, range types |
| BRIN | Very large tables, sequential data |

## Common Indexes for a Todo App
```sql
CREATE INDEX idx_todos_user_id ON todos(user_id);
CREATE INDEX idx_todos_user_status ON todos(user_id, completed);
CREATE INDEX idx_todos_created_at ON todos(created_at DESC);
CREATE UNIQUE INDEX idx_todos_user_title ON todos(user_id, title) WHERE deleted_at IS NULL;
```

## Rules
- Always index foreign keys.
- Use composite indexes for frequent multi-column queries.
- Use partial indexes (`WHERE condition`) to reduce index size.
- Monitor with `pg_stat_user_indexes` for unused indexes.
