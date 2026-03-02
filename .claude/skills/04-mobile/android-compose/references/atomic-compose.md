# Atomic Compose Components

## Atoms
```kotlin
@Composable
fun PrimaryButton(text: String, onClick: () -> Unit, modifier: Modifier = Modifier) {
    Button(onClick = onClick, modifier = modifier.fillMaxWidth()) {
        Text(text, style = MaterialTheme.typography.labelLarge)
    }
}
```

## Molecules
```kotlin
@Composable
fun TodoRow(todo: TodoItem, onToggle: (String) -> Unit) {
    Row(modifier = Modifier.fillMaxWidth().clickable { onToggle(todo.id) }.padding(16.dp)) {
        Checkbox(checked = todo.completed, onCheckedChange = { onToggle(todo.id) })
        Text(todo.title, modifier = Modifier.weight(1f), textDecoration = if (todo.completed) TextDecoration.LineThrough else null)
    }
}
```

## Organisms
```kotlin
@Composable
fun TodoListSection(todos: List<TodoItem>, onToggle: (String) -> Unit, onDelete: (String) -> Unit) {
    LazyColumn {
        items(todos, key = { it.id }) { todo ->
            TodoRow(todo = todo, onToggle = onToggle)
        }
    }
}
```
