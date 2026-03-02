# Spec Mining Template

## Code Exploration Process
1. **Inventory**: List all files, modules, and their responsibilities.
2. **Entry Points**: Identify main routes, handlers, event listeners.
3. **Data Flow**: Trace how data moves from input → processing → output.
4. **Hidden Rules**: Document implicit business rules found in code.

## Output Format
### Module: [Name]
- **Purpose**: [What this module does]
- **Inputs**: [What data it receives]
- **Outputs**: [What data it produces]
- **Side Effects**: [DB writes, API calls, file I/O]
- **Dependencies**: [Other modules it relies on]
- **Business Rules**:
  - Rule 1: [Description + file:line reference]
  - Rule 2: [Description + file:line reference]

## Discovery Checklist
- [ ] All API endpoints documented
- [ ] Database schema reverse-engineered
- [ ] Authentication/authorization flow mapped
- [ ] Error handling patterns identified
- [ ] Configuration and environment variables listed
- [ ] Third-party integrations catalogued
