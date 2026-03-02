# Python Idioms

## List Comprehensions
```python
# ✅ Pythonic
squares = [x**2 for x in range(10) if x % 2 == 0]

# ❌ Non-Pythonic
squares = []
for x in range(10):
    if x % 2 == 0:
        squares.append(x**2)
```

## Context Managers
```python
# ✅ Always use `with` for resource management
with open("file.txt", "r") as f:
    data = f.read()
```

## Unpacking & Walrus Operator
```python
first, *rest = [1, 2, 3, 4]  # first=1, rest=[2,3,4]

if (n := len(items)) > 10:
    print(f"Too many items: {n}")
```

## Dataclasses (Python 3.10+)
```python
from dataclasses import dataclass

@dataclass(frozen=True)
class TodoItem:
    id: str
    title: str
    completed: bool = False
```

## Pattern Matching (Python 3.10+)
```python
match status:
    case "DRAFT":
        handle_draft()
    case "ANALYZED":
        handle_analyzed()
    case _:
        raise ValueError(f"Unknown status: {status}")
```
