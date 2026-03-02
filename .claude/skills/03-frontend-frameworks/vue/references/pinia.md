# Pinia State Management

## Define Store
```typescript
// stores/todo.store.ts
import { defineStore } from 'pinia'

export const useTodoStore = defineStore('todos', () => {
  const todos = ref<TodoItem[]>([])
  const loading = ref(false)

  const completed = computed(() => todos.value.filter(t => t.completed))
  const pending = computed(() => todos.value.filter(t => !t.completed))

  async function fetchAll() {
    loading.value = true
    todos.value = await api.getTodos()
    loading.value = false
  }

  function toggle(id: string) {
    const todo = todos.value.find(t => t.id === id)
    if (todo) todo.completed = !todo.completed
  }

  return { todos, loading, completed, pending, fetchAll, toggle }
})
```

## Usage in Component
```vue
<script setup>
const store = useTodoStore()
onMounted(() => store.fetchAll())
</script>
```
