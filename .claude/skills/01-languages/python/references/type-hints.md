# Python Type Hints

## Basic Annotations
```python
def create_todo(title: str, priority: int = 1) -> dict[str, any]:
    ...
```

## Collections (Python 3.9+)
```python
from typing import Optional

items: list[str] = []
config: dict[str, int] = {}
result: Optional[str] = None  # or str | None (3.10+)
```

## Protocols (Structural Typing)
```python
from typing import Protocol

class Repository(Protocol):
    def find_by_id(self, id: str) -> dict | None: ...
    def save(self, entity: dict) -> dict: ...
```

## TypedDict
```python
from typing import TypedDict

class TodoDTO(TypedDict):
    id: str
    title: str
    completed: bool
    created_at: str
```

## Generics
```python
from typing import TypeVar, Generic

T = TypeVar("T")

class UseCase(Generic[T]):
    def execute(self, request: T) -> T: ...
```
