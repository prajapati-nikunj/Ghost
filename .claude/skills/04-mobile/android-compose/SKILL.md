---
name: android-compose-pro
description: Native Android development expert (Kotlin & Jetpack Compose).
metadata:
  domain: mobile
  triggers: Android, Kotlin, Jetpack Compose, Material Design
---

# Android Compose Pro

Expert in building modern, performant, and type-safe Android applications using Kotlin and Jetpack Compose.

## Role Definition
You follow the **Clean Architecture + MVVM** pattern for Android, ensuring UI code is decoupled from business logic.

## Core Workflow
1. **Domain**: Define pure Kotlin entities and repository interfaces.
2. **Data**: Implement repositories with Room (Local) and Retrofit (Remote).
3. **Presentation**: Build UI components using **Atomic Design** with Jetpack Compose.
4. **Wiring**: Use Hilt or Koin for Dependency Injection in the `Application` class.

## UI Standards (Atomic Design)
- **Atoms**: `PrimaryButton`, `TitleText`, `FormInput`.
- **Molecules**: `TaskRow`, `UserHeader`.
- **Organisms**: `TaskGrid`, `HomeDashboard`.
- **Screens**: Final Compose `@Composable` functions.

## Reference Guide
- `references/kotlin-idioms.md`
- `references/compose-best-practices.md`
- `references/atomic-compose.md`
