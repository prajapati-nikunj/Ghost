# React Hooks Patterns

## Custom Hook Pattern
```tsx
function useTodos() {
  const [todos, setTodos] = useState<TodoItem[]>([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    fetchTodos().then(setTodos).catch(e => setError(e.message)).finally(() => setLoading(false));
  }, []);

  const addTodo = useCallback(async (title: string) => {
    const newTodo = await createTodo(title);
    setTodos(prev => [...prev, newTodo]);
  }, []);

  return { todos, loading, error, addTodo };
}
```

## useReducer for Complex State
```tsx
type Action = { type: "ADD"; todo: TodoItem } | { type: "TOGGLE"; id: string } | { type: "DELETE"; id: string };

function todoReducer(state: TodoItem[], action: Action): TodoItem[] {
  switch (action.type) {
    case "ADD": return [...state, action.todo];
    case "TOGGLE": return state.map(t => t.id === action.id ? { ...t, completed: !t.completed } : t);
    case "DELETE": return state.filter(t => t.id !== action.id);
  }
}
```

## Rules
- Hooks must start with `use`.
- Never call hooks inside conditionals or loops.
- Extract shared logic into custom hooks.
