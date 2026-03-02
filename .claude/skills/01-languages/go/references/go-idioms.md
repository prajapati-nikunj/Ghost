# Go Idioms

## Error Handling
```go
func FindTodo(id string) (*Todo, error) {
    todo, err := repo.FindByID(id)
    if err != nil {
        return nil, fmt.Errorf("finding todo %s: %w", id, err)
    }
    return todo, nil
}
```

## Interfaces (Implicit)
```go
type TodoRepository interface {
    FindByID(id string) (*Todo, error)
    Save(todo *Todo) error
    Delete(id string) error
}
```

## Struct Embedding
```go
type BaseTodo struct { ID string; Title string }
type PriorityTodo struct {
    BaseTodo
    Priority int
}
```

## Table-Driven Tests
```go
func TestValidate(t *testing.T) {
    tests := []struct{name, input string; wantErr bool}{
        {"empty", "", true},
        {"valid", "Buy milk", false},
    }
    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            err := Validate(tt.input)
            if (err != nil) != tt.wantErr { t.Errorf("got %v", err) }
        })
    }
}
```
