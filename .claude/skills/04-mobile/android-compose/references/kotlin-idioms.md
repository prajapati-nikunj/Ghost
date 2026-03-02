# Kotlin Idioms for Android

## Data Classes
```kotlin
data class TodoItem(
    val id: String = UUID.randomUUID().toString(),
    val title: String,
    val completed: Boolean = false,
    val createdAt: Instant = Clock.System.now()
)
```

## Sealed Classes for State
```kotlin
sealed class UiState<out T> {
    data object Loading : UiState<Nothing>()
    data class Success<T>(val data: T) : UiState<T>()
    data class Error(val message: String) : UiState<Nothing>()
}
```

## Extension Functions
```kotlin
fun List<TodoItem>.completedCount(): Int = count { it.completed }
fun List<TodoItem>.pendingCount(): Int = count { !it.completed }
```

## Coroutine Patterns
```kotlin
viewModelScope.launch {
    _uiState.value = UiState.Loading
    runCatching { repository.fetchTodos() }
        .onSuccess { _uiState.value = UiState.Success(it) }
        .onFailure { _uiState.value = UiState.Error(it.message ?: "Unknown error") }
}
```
