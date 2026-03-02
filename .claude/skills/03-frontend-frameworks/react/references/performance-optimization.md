# React Performance Optimization

## React.memo
```tsx
const TodoRow = React.memo(({ todo, onToggle }: Props) => (
  <li onClick={() => onToggle(todo.id)}>{todo.title}</li>
));
```

## useMemo & useCallback
```tsx
const filtered = useMemo(() => todos.filter(t => t.completed === showDone), [todos, showDone]);
const handleToggle = useCallback((id: string) => dispatch({ type: "TOGGLE", id }), []);
```

## Lazy Loading
```tsx
const Settings = React.lazy(() => import("./pages/Settings"));
// Wrap in <Suspense fallback={<Spinner />}>
```

## Virtualized Lists
Use `react-window` or `@tanstack/virtual` for lists > 100 items.

## Key Rules
- Use stable, unique `id` for `key` prop (never array index).
- Avoid inline object/function creation in JSX when passed as props.
- Profile with React DevTools Profiler before optimizing.
