# PostgreSQL Transactions

## Basic Transaction
```sql
BEGIN;
INSERT INTO todos (id, title, user_id) VALUES ('uuid1', 'Buy milk', 'user1');
UPDATE users SET todo_count = todo_count + 1 WHERE id = 'user1';
COMMIT;
```

## Isolation Levels
| Level | Dirty Read | Non-Repeatable | Phantom |
|---|---|---|---|
| Read Uncommitted | ✅ | ✅ | ✅ |
| Read Committed (default) | ❌ | ✅ | ✅ |
| Repeatable Read | ❌ | ❌ | ✅ |
| Serializable | ❌ | ❌ | ❌ |

## Python/SQLAlchemy
```python
async with async_session() as session:
    async with session.begin():
        session.add(new_todo)
        # auto-commits on exit, auto-rollbacks on exception
```

## Rules
- Keep transactions short.
- Always handle `ROLLBACK` on failure.
- Use `SELECT ... FOR UPDATE` for row-level locking.
