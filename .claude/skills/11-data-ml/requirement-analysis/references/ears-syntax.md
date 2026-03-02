# EARS (Easy Approach to Requirements Syntax)

## Overview
Functional requirements should follow the EARS syntax to ensure they are clear, concise, and testable.

## Patterns

### 1. Ubiquitous Requirements
*Keyword: none*
- **Pattern**: The [system name] shall [system response].
- **Example**: The system shall encrypt all user data at rest.

### 2. Event-Driven Requirements
*Keyword: When*
- **Pattern**: When [event], the [system name] shall [system response].
- **Example**: When the user clicks "Delete", the system shall display a confirmation dialog.

### 3. State-Driven Requirements
*Keyword: While*
- **Pattern**: While [in a state], the [system name] shall [system response].
- **Example**: While in emergency mode, the system shall disable non-essential services.

### 4. Unwanted Behavior Requirements
*Keyword: If*
- **Pattern**: If [trigger], then the [system name] shall [system response].
- **Example**: If the login fails three times, the system shall lock the account for 10 minutes.

### 5. Optional Feature Requirements
*Keyword: Where*
- **Pattern**: Where [feature is included], the [system name] shall [system response].
- **Example**: Where a camera is detected, the system shall allow video capture.
