# Atomic Design Pattern

## Overview
The User Interface must be structured using the Atomic Design methodology for maximum reusability, consistency, and scalability across the Ghost factory's output.

## Layers

### 1. Atoms
Indivisible, smallest elements. Logic-lite and dumb.
- **Goal**: Receive data, provide callbacks.
- **Examples**: `Button`, `Label`, `Icon`, `Input`.

### 2. Molecules
Groups of Atoms bonded together. Functions as a single unit.
- **Goal**: Small reusable components.
- **Examples**: `SearchField` (Label + Input + Button), `UserAvatar` (Image + Name).

### 3. Organisms
Complex sections of the UI, combining Atoms and Molecules.
- **Goal**: Form a distinct part of the interface. Tied to a specific ViewModel property.
- **Examples**: `Header`, `ProductGrid`, `CommentSection`.

### 4. Templates
Page-level layout structures.
- **Goal**: Define content arrangement; where organisms and molecules are placed.
- **Examples**: `TwoColumnLayout`, `AuthTemplate`.

### 5. Pages
Instances of Templates populated with real data.
- **Goal**: The final view the user sees. Maps data from the Repository/ViewModel to the Template.
- **Examples**: `LoginView`, `DashboardHome`.

## Rule
All UI components created by the **Code Generator** must be categorized into one of these layers and stored in corresponding directory structures (e.g., `src/presentation/components/atoms/`).
