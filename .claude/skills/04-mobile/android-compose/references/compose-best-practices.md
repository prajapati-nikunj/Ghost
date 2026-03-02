# Jetpack Compose Best Practices

## State Hoisting
```kotlin
@Composable
fun TodoScreen(viewModel: TodoViewModel = hiltViewModel()) {
    val uiState by viewModel.uiState.collectAsStateWithLifecycle()
    TodoContent(state = uiState, onToggle = viewModel::toggleTodo, onAdd = viewModel::addTodo)
}

@Composable
fun TodoContent(state: UiState<List<TodoItem>>, onToggle: (String) -> Unit, onAdd: (String) -> Unit) {
    when (state) {
        is UiState.Loading -> CircularProgressIndicator()
        is UiState.Success -> TodoList(todos = state.data, onToggle = onToggle)
        is UiState.Error -> Text(state.message, color = MaterialTheme.colorScheme.error)
    }
}
```

## Previews
```kotlin
@Preview(showBackground = true)
@Composable
fun TodoRowPreview() {
    TodoRow(todo = TodoItem(title = "Preview Task"), onToggle = {})
}
```

## Performance
- Use `key` in `LazyColumn` items.
- Avoid recomposition by using `remember` and stable types.
- Use `derivedStateOf` for computed properties.
