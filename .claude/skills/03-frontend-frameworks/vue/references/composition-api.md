# Vue Composition API

## Basic Component
```vue
<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'

interface TodoItem { id: string; title: string; completed: boolean }

const todos = ref<TodoItem[]>([])
const newTitle = ref('')
const completedCount = computed(() => todos.value.filter(t => t.completed).length)

onMounted(async () => { todos.value = await fetchTodos() })

function addTodo() {
  todos.value.push({ id: crypto.randomUUID(), title: newTitle.value, completed: false })
  newTitle.value = ''
}
</script>

<template>
  <input v-model="newTitle" @keyup.enter="addTodo" />
  <p>{{ completedCount }} / {{ todos.length }} done</p>
</template>
```

## Composables (Custom Hooks)
```typescript
// composables/useTodos.ts
export function useTodos() {
  const todos = ref<TodoItem[]>([])
  const loading = ref(true)
  onMounted(async () => { todos.value = await api.getTodos(); loading.value = false })
  return { todos, loading }
}
```
