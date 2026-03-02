# FastAPI Reference

## Project Structure (Clean Architecture)
```
src/
├── main.py                  # App factory
├── core/
│   ├── entities/            # Domain models (Pydantic)
│   │   └── todo.py
│   └── errors.py            # Domain exceptions
├── use_cases/
│   ├── create_todo.py       # Business logic
│   └── ports/
│       └── todo_repository.py  # Repository interface (ABC)
├── adapters/
│   ├── controllers/
│   │   └── todo_router.py   # FastAPI Router
│   └── repositories/
│       └── postgres_todo_repo.py
└── infrastructure/
    ├── database.py           # SQLAlchemy engine
    └── dependencies.py       # Dependency injection
```

## Router Pattern
```python
from fastapi import APIRouter, Depends, HTTPException

router = APIRouter(prefix="/api/v1/todos", tags=["Todos"])

@router.get("/", response_model=list[TodoResponse])
async def list_todos(
    repo: TodoRepository = Depends(get_todo_repository),
    current_user: User = Depends(get_current_user),
):
    return await repo.find_by_user(current_user.id)

@router.post("/", status_code=201, response_model=TodoResponse)
async def create_todo(
    request: CreateTodoRequest,
    use_case: CreateTodoUseCase = Depends(get_create_todo_use_case),
):
    return await use_case.execute(request)
```

## Dependency Injection
```python
from functools import lru_cache

@lru_cache
def get_settings() -> Settings:
    return Settings()

async def get_db_session() -> AsyncGenerator[AsyncSession, None]:
    async with async_session_factory() as session:
        yield session

def get_todo_repository(session: AsyncSession = Depends(get_db_session)):
    return PostgresTodoRepository(session)
```

## Pydantic Models
```python
from pydantic import BaseModel, Field
from datetime import datetime

class CreateTodoRequest(BaseModel):
    title: str = Field(..., min_length=1, max_length=255)

class TodoResponse(BaseModel):
    id: str
    title: str
    completed: bool
    created_at: datetime
    model_config = ConfigDict(from_attributes=True)
```
