# OpenAPI 3.1 Reference

## Minimal Spec
```yaml
openapi: "3.1.0"
info:
  title: Todo API
  version: "1.0.0"
servers:
  - url: http://localhost:8000/api/v1
paths:
  /todos:
    get:
      summary: List all todos
      operationId: listTodos
      parameters:
        - name: status
          in: query
          schema: { type: string, enum: [pending, completed] }
        - name: limit
          in: query
          schema: { type: integer, default: 20, maximum: 100 }
      responses:
        "200":
          description: List of todos
          content:
            application/json:
              schema:
                type: object
                properties:
                  data:
                    type: array
                    items: { $ref: "#/components/schemas/TodoItem" }
    post:
      summary: Create a todo
      operationId: createTodo
      requestBody:
        required: true
        content:
          application/json:
            schema: { $ref: "#/components/schemas/CreateTodoRequest" }
      responses:
        "201":
          description: Created
components:
  schemas:
    TodoItem:
      type: object
      required: [id, title, completed]
      properties:
        id: { type: string, format: uuid }
        title: { type: string, minLength: 1, maxLength: 255 }
        completed: { type: boolean, default: false }
        createdAt: { type: string, format: date-time }
    CreateTodoRequest:
      type: object
      required: [title]
      properties:
        title: { type: string, minLength: 1, maxLength: 255 }
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
```
