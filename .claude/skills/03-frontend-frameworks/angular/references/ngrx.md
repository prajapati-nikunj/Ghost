# NgRx State Management

## Store Setup
```typescript
// State
export interface TodoState { todos: TodoItem[]; loading: boolean; error: string | null; }

// Actions
export const loadTodos = createAction('[Todo] Load');
export const loadTodosSuccess = createAction('[Todo] Load Success', props<{ todos: TodoItem[] }>());
export const loadTodosFailure = createAction('[Todo] Load Failure', props<{ error: string }>());

// Reducer
export const todoReducer = createReducer(
  initialState,
  on(loadTodos, state => ({ ...state, loading: true })),
  on(loadTodosSuccess, (state, { todos }) => ({ ...state, todos, loading: false })),
  on(loadTodosFailure, (state, { error }) => ({ ...state, error, loading: false })),
);

// Selectors
export const selectTodos = createSelector(selectTodoState, state => state.todos);
export const selectLoading = createSelector(selectTodoState, state => state.loading);

// Effects
loadTodos$ = createEffect(() => this.actions$.pipe(
  ofType(loadTodos),
  switchMap(() => this.todoService.getAll().pipe(
    map(todos => loadTodosSuccess({ todos })),
    catchError(error => of(loadTodosFailure({ error: error.message })))
  ))
));
```
