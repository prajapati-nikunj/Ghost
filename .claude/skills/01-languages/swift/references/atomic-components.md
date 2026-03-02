# Atomic SwiftUI Components

## Atoms (Smallest units)
```swift
struct PrimaryButton: View {
    let title: String
    let action: () -> Void
    
    var body: some View {
        Button(action: action) {
            Text(title)
                .font(.headline)
                .foregroundStyle(.white)
                .padding()
                .frame(maxWidth: .infinity)
                .background(.blue.gradient)
                .clipShape(RoundedRectangle(cornerRadius: 12))
        }
    }
}
```

## Molecules (Groups of Atoms)
```swift
struct TodoRow: View {
    let todo: TodoItem
    let onToggle: () -> Void
    
    var body: some View {
        HStack {
            Image(systemName: todo.isCompleted ? "checkmark.circle.fill" : "circle")
            Text(todo.title)
                .strikethrough(todo.isCompleted)
            Spacer()
        }
        .contentShape(Rectangle())
        .onTapGesture(perform: onToggle)
    }
}
```

## Organisms (Complex sections)
```swift
struct TodoListView: View {
    let todos: [TodoItem]
    let onToggle: (UUID) -> Void
    let onDelete: (UUID) -> Void
    
    var body: some View {
        List {
            ForEach(todos) { todo in
                TodoRow(todo: todo, onToggle: { onToggle(todo.id) })
            }
            .onDelete { indexSet in
                indexSet.forEach { onDelete(todos[$0].id) }
            }
        }
    }
}
```
