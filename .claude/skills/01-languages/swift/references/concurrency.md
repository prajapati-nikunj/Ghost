# Swift Concurrency (async/await)

## Basic async Functions
```swift
func fetchTodos() async throws -> [TodoItem] {
    let (data, _) = try await URLSession.shared.data(from: url)
    return try JSONDecoder().decode([TodoItem].self, from: data)
}
```

## @MainActor for UI Updates
```swift
@MainActor
@Observable
final class TodoViewModel {
    var todos: [TodoItem] = []
    
    func loadTodos() async {
        do {
            todos = try await fetchTodosUseCase.execute()
        } catch {
            errorMessage = error.localizedDescription
        }
    }
}
```

## TaskGroup for Parallel Work
```swift
func fetchAll() async throws -> ([TodoItem], [Category]) {
    async let todos = todoRepo.fetchAll()
    async let categories = categoryRepo.fetchAll()
    return try await (todos, categories)
}
```

## Sendable Protocol
```swift
struct TodoItem: Sendable, Codable {
    let id: UUID
    let title: String
    let isCompleted: Bool
}
```
