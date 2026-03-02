# Swift Idioms

## Value Types & Immutability
```swift
struct TodoItem: Identifiable, Hashable {
    let id: UUID
    var title: String
    var isCompleted: Bool = false
}
```

## Guard Statements
```swift
func validate(title: String?) throws -> String {
    guard let title, !title.isEmpty else {
        throw ValidationError.emptyTitle
    }
    return title
}
```

## Result Type
```swift
enum AppError: Error { case networkError, notFound }

func fetchTodo(id: UUID) async -> Result<TodoItem, AppError> {
    // ...
}
```

## Protocol-Oriented Design
```swift
protocol TodoRepositoryProtocol {
    func fetchAll() async throws -> [TodoItem]
    func save(_ item: TodoItem) async throws -> TodoItem
    func delete(id: UUID) async throws
}
```

## Property Wrappers
```swift
@Observable
final class TodoViewModel {
    var todos: [TodoItem] = []
    var isLoading: Bool = false
    var errorMessage: String?
}
```
