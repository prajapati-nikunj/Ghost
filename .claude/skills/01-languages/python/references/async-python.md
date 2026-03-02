# Async Python

## async/await Basics
```python
import asyncio

async def fetch_todos() -> list[dict]:
    await asyncio.sleep(0.1)  # simulating I/O
    return [{"id": "1", "title": "Buy milk"}]
```

## Concurrent Tasks
```python
async def process_all():
    results = await asyncio.gather(
        fetch_todos(),
        fetch_users(),
        fetch_tags(),
    )
    return results
```

## FastAPI Integration
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/todos")
async def get_todos(repo: TodoRepository = Depends(get_repo)):
    return await repo.find_all()
```

## Async Context Managers
```python
from contextlib import asynccontextmanager

@asynccontextmanager
async def get_db_session():
    session = await create_session()
    try:
        yield session
    finally:
        await session.close()
```
