# TDD Iron Laws

## The Three Laws of TDD
1. **You may not write production code** until you have written a failing unit test.
2. **You may not write more of a unit test** than is sufficient to fail (compilation failures count).
3. **You may not write more production code** than is sufficient to make the currently failing test pass.

## Red-Green-Refactor Cycle
1. **🔴 Red**: Write a failing test.
2. **🟢 Green**: Write the minimum code to pass.
3. **🔵 Refactor**: Clean up without changing behavior.

## Test Structure (Arrange-Act-Assert / Given-When-Then)
```python
def test_create_todo_success():
    # Given
    request = CreateTodoRequest(title="Buy milk", user_id="user1")
    repo = FakeTodoRepository()
    use_case = CreateTodoUseCase(repo)
    
    # When
    result = use_case.execute(request)
    
    # Then
    assert result.title == "Buy milk"
    assert result.completed is False
    assert repo.find_by_id(result.id) is not None
```

## What to Test
- ✅ Business logic (Use Cases, Entities)
- ✅ Edge cases and error paths
- ✅ Boundary values
- ❌ Framework internals
- ❌ Third-party libraries
- ❌ Private methods directly
