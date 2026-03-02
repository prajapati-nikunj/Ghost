# Testing Standards

## Unit Testing
- Test logic in isolation.
- Mock all dependencies (Repositories, Services).
- Follow the Given-When-Then pattern.

## Integration Testing
- Test the interaction between two or more components (e.g., Use Case + Repository).
- Ensure data flows correctly through the system.

## E2E Testing
- Test critical user paths from the UI.
- Validate the system as a whole.

## Tooling
- Use standard testing frameworks (e.g., XCTest, Swift Testing, Vitest).
- Generate coverage reports for every PR.
