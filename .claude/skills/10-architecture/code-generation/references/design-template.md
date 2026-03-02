# Design Template (Three-Perspective)

## Feature: [Name]

### Frontend Perspective
- **Components**: [Atoms, Molecules, Organisms needed]
- **State**: [Local vs Global state management]
- **Routes**: [New pages/routes required]
- **Accessibility**: [ARIA labels, keyboard navigation]

### Backend Perspective
- **Endpoints**: [HTTP Method + URI + Request/Response schema]
- **Business Logic**: [Use Cases to implement]
- **Data Model**: [New entities or migrations]
- **Validation**: [Input rules, Zod/Pydantic schemas]

### Security Perspective
- **Authentication**: [Who can access?]
- **Authorization**: [What permissions are required?]
- **Input Validation**: [Server-side checks]
- **Data Protection**: [Sensitive fields, encryption]

## Implementation Order
1. Database migration and entity
2. Repository implementation
3. Use Case / Service
4. Controller / API endpoint
5. Frontend component
6. Tests (unit → integration → E2E)
