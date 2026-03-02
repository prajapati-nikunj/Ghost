# RxJS Patterns for Angular

## Observable Patterns
```typescript
// Declarative data fetching
todos$ = this.http.get<TodoItem[]>('/api/todos').pipe(
  retry(3),
  catchError(() => of([])),
  shareReplay(1)
);
```

## Subject Types
| Type | Behavior |
|---|---|
| Subject | No initial value, multicast |
| BehaviorSubject | Has initial value, emits last value to new subscribers |
| ReplaySubject | Replays N previous values |
| AsyncSubject | Emits only last value on complete |

## Common Operators
```typescript
// Search with debounce
searchResults$ = this.searchControl.valueChanges.pipe(
  debounceTime(300),
  distinctUntilChanged(),
  switchMap(term => this.todoService.search(term))
);
```

## Unsubscribe Pattern
```typescript
private destroy$ = new Subject<void>();

ngOnInit() {
  this.data$.pipe(takeUntil(this.destroy$)).subscribe(data => this.items = data);
}
ngOnDestroy() { this.destroy$.next(); this.destroy$.complete(); }
```
