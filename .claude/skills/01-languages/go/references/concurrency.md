# Go Concurrency

## Goroutines & Channels
```go
ch := make(chan TodoItem, 10)
go func() { ch <- fetchTodo(); close(ch) }()
todo := <-ch
```

## sync.WaitGroup
```go
var wg sync.WaitGroup
for _, id := range ids {
    wg.Add(1)
    go func(id string) {
        defer wg.Done()
        process(id)
    }(id)
}
wg.Wait()
```

## Context for Cancellation
```go
ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
defer cancel()
result, err := repo.FindByID(ctx, id)
```
