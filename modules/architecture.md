# Architecture

### Android Architecture Guide: MVVM, Clean Architecture & SOLID Principles

This document outlines a scalable Android app architecture combining **MVVM**, **Clean Architecture**, and **SOLID principles**, tailored for modularity, testability, and maintainability.

- [Modularization Strategy](#Modularization Strategy for Android Architecture)
- [Architecture Overview](#Architecture Overview)

---

## Modularization Strategy for Android Architecture

This document outlines a modularization approach that complements the **MVVM + Clean Architecture** setup, focusing on scalability, team collaboration, and build efficiency.

### **Module Types & Structure**
![Modular Diagram](..%2Fassets%2Fmodularization_strategy.png)
*Aligns with existing `PortalCore` and feature-based architecture.*

### **1. App Module**
- **Role**: Entry point of the application.
- **Responsibilities**:
    - Initializes DI (Hilt), navigation, and global configurations.
    - Contains no business logic.
    - Depends on `feature` modules and `core` libraries.

### **2. Feature Modules**
- **Naming**: `:feature:<name>` (e.g., `:feature:auth`, `:feature:profile`).
- **Structure**:
  ```plaintext
  feature
    ├── :auth_data
    │   ├── src/
    │   │   ├── main/          # Data (for feature)
    │   │   └── test/          # Feature-specific tests
    │   └── build.gradle.kts   # Declares dependencies (e.g., domain, core, shared)
    │
    ├── :auth_domain
    │   ├── src/
    │   │   ├── main/          # Domain (for feature)
    │   │   └── test/          # Feature-specific tests
    │   └── build.gradle.kts   # Declares dependencies (e.g., core, shared)
    │
    ├── :auth_presentation
    │   ├── src/
    │   │   ├── main/          # Prsentation (Screen, View Model, State, Event)
    │   │   └── test/          # Feature-specific tests
    │   └── build.gradle.kts   # Declares dependencies (e.g., domain, core, shared)
    │

### **3. Core Modules (:core)**
- **Role:** Reusable infrastructure and utilities.

- **Packages:**
  * `:core.network`: Retrofit, API interfaces, interceptors.
  * `:core.database`: Room DAOs, migrations.
  * `:core.di`: Hilt modules for dependency injection.
  * `:core.util`: Extensions, constants, logging.
---

## **Architecture Overview**
![Architecture Diagram](..%2Fassets%2Farchitecture.png)
*The company's existing structure with enhancements for modern practices.*

### **Key Layers**
1. **Presentation Layer (MVVM)**
2. **Domain Layer (Clean Architecture)**
3. **Data Layer (Clean Architecture)**

---

## **1. Presentation Layer (MVVM)**
Handles UI logic, user interactions, and observes data changes using Android Jetpack components.

### **Components**
- **View**: Activities, Fragments, Composables (observes ViewModel state).
- **ViewModel**: Manages UI-related data, exposes `StateFlow`/`LiveData` to the View.
- **State**: Immutable data classes representing UI state (e.g., `Loading`, `Success`, `Error`).

### **SOLID Compliance**
- **Single Responsibility**: ViewModel only handles UI logic.
- **Dependency Inversion**: ViewModel depends on UseCase abstractions, not concrete implementations.

## **2. Domain Layer (Clean Architecture)**
Pure Kotlin module containing business logic, **independent of Android frameworks**.

### **Components**
- **Use Cases (Interactors)**: Execute single business actions (e.g., `GetUserUseCase`).
- **Entities**:  Business models (e.g., `User`).
- **Repository Interfaces:**: Define data operations (e.g., `UserRepository`).

### **SOLID Compliance**
- **Open/Closed Principle**: Extend behavior via new Use Cases, not modifying existing ones.
- **Interface Segregation**: Split repositories into focused interfaces (e.g., `UserRepository`, `SettingsRepository`).

## **3. Data Layer (Clean Architecture)**
Implements repository interfaces and handles data sources (network, database, cache).

### **Components**
- **Repository Implementations**: Fetch data from remote/local sources.
- **Data Sources**:
  - **Remote**: Retrofit, Firebase.
  - **Local**: Room, DataStore.
- **DTOs**: Data Transfer Objects (e.g., API/database models).

### **SOLID Compliance**
- **Data Source**: Data sources interfaces (e.g., `UserRemoteDataSource`).
- **Dependency Inversion**: Data layer depends on domain-layer abstractions.

---