# Atomic React Components

## Atoms
```tsx
// components/atoms/PrimaryButton.tsx
export const PrimaryButton = ({ label, onClick, disabled }: Props) => (
  <button className="btn-primary" onClick={onClick} disabled={disabled}>{label}</button>
);

// components/atoms/TextInput.tsx
export const TextInput = ({ value, onChange, placeholder }: Props) => (
  <input className="input-text" value={value} onChange={e => onChange(e.target.value)} placeholder={placeholder} />
);
```

## Molecules
```tsx
// components/molecules/AddTodoForm.tsx
export const AddTodoForm = ({ onAdd }: Props) => {
  const [title, setTitle] = useState("");
  return (
    <form onSubmit={e => { e.preventDefault(); onAdd(title); setTitle(""); }}>
      <TextInput value={title} onChange={setTitle} placeholder="What needs done?" />
      <PrimaryButton label="Add" onClick={() => {}} />
    </form>
  );
};
```

## Organisms
```tsx
// components/organisms/TodoDashboard.tsx
export const TodoDashboard = ({ todos, onAdd, onToggle, onDelete }: Props) => (
  <section>
    <AddTodoForm onAdd={onAdd} />
    <TodoList todos={todos} onToggle={onToggle} onDelete={onDelete} />
    <TodoStats total={todos.length} completed={todos.filter(t => t.completed).length} />
  </section>
);
```

## Directory Structure
```
src/components/
├── atoms/       # PrimaryButton, TextInput, Badge, Icon
├── molecules/   # AddTodoForm, TodoRow, FilterBar
├── organisms/   # TodoDashboard, Header, Sidebar
├── templates/   # MainLayout, AuthLayout
└── pages/       # HomePage, SettingsPage
```
