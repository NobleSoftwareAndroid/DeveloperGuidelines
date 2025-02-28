# Best Practices

Follow these foundational practices to ensure clean, maintainable, and scalable Android codebases aligned with **MVVM**, **Clean Architecture**, and **SOLID principles**.

---

## **1. Structure**
- ### **Layer Separation**
  - **Presentation Layer**:
      - Use Jetpack ViewModel + StateFlow/LiveData for UI state management.
      - Keep Activities/Fragments lean (only UI rendering and input handling).
  - **Domain Layer**:
      - Business logic in Use Cases (Interactors).
      - Define repository interfaces here.
  - **Data Layer**:
      - Implement repository interfaces using remote (Retrofit) and local (Room) sources.
      - Use DTOs for API/database models; map them to domain entities.  

- ### **Package Structure**
  ```plaintext
  com.visiprima.app
  ├──feature
  │    ├── :auth_data
  │    │   ├── src/
  │    │   │   ├── main/          # Data (for feature)
  │    │   │   └── test/          # Feature-specific tests
  │    │   └── build.gradle.kts   # Declares dependencies (e.g., domain, core, shared)
  │    │
  │    ├── :auth_domain
  │    │   ├── src/
  │    │   │   ├── main/          # Domain (for feature)
  │    │   │   └── test/          # Feature-specific tests
  │    │   └── build.gradle.kts   # Declares dependencies (e.g., core, shared)
  │    │
  │    ├── :auth_presentation
  │    │   ├── src/
  │    │   │   ├── main/          # Prsentation (Screen, View Model, State, Event)
  │    │   │   └── test/          # Feature-specific tests
  │    │   └── build.gradle.kts   # Declares dependencies (e.g., domain, core, shared)
  │
  ├── core/
  │   ├── network/           # Retrofit, API clients
  │   ├── database/          # Room DAOs, Entities
  │   └── di/                # Hilt Modules 
   ```

## 2. Code Quality
Consistent code style improves readability and maintainability. Follow these guidelines:

**Advantage of Implementation of Coding Standards**
* Offers uniformity to the code created by different engineers.
* Enables the creation of reusable code.
* Makes it easier to detect errors.
* Make code simpler, more readable, and easier to maintain.
* Boost programmer efficiency and generate faster results.
---
**Coding standards** are a set of rules, guidelines, and best practices that developers follow when writing code. They ensure consistency, readability, maintainability, and collaboration within a development team.

**Key Components of Android Coding Standards**
Here's a breakdown of essential elements for your Android coding standards:

**Naming Conventions**
* **Package Names**: Use reverse domain names (e.g., `com.example.app`).
* **Class Names**: Use UpperCamelCase (e.g., `MainActivity`).
* **Interface Names**: Use UpperCamelCase starting with "I" (e.g., `IOnClickListener`).
* **Method Names**: Use lowerCamelCase (e.g., `onCreate`).
* **Variable Names**: Use lowerCamelCase, descriptive names (e.g., `userName`).
* **Constants**: Use UPPERCASE_WITH_UNDERSCORES (e.g., `MAX_VALUE`).
* **Resources**: Prefix for clarity (e.g., `img_imagename`, `ic_iconname`).

## 3. Code Formatting
   Indentation: Use 4 spaces for indentation.
   Line Length: Keep lines to a maximum of 80-100 characters.
   Braces: Use consistent brace placement (e.g., K&R style, Allman style).
   Whitespace: Use consistent spacing around operators and keywords.

## 4. Code Comments
   Purpose: Explain the purpose of code sections, especially complex logic.
   Style: Use clear and concise language.
   Updating: Keep comments up-to-date with code changes.

## 5. Code Structure
   Package Organization: Use logical package structures based on functionality.
   Class Design: Follow SOLID principles (Single Responsibility, Open-Closed, Liskov Substitution, Interface Segregation, Dependency Inversion).
   Method Length: Keep methods concise and focused on a single task.
   Error Handling: Use try-catch blocks appropriately and provide informative error messages.

## 6. Code Optimization
   Performance: Consider performance implications when writing code.
   Memory Management: Avoid memory leaks and optimize memory usage.
   Battery Usage: Be mindful of battery consumption, especially for background tasks.


## 7. Security

Android apps must protect user data and prevent vulnerabilities.

* Use encrypted storage for sensitive data.
* Use HTTPS for all network communication and validate server certificates.
* Sanitize user inputs to prevent injection attacks.
* Request only necessary permissions and explain their purpose.
* Handle permission denials gracefully.
* Use code obfuscation techniques.
* Keep dependencies updated and use dependency scanning tools.
* Validate all user-provided input.
* Avoid hardcoding sensitive information.

## 8. Performance & Optimization
* Background Threading: Use coroutines (`Dispatchers.IO`) for network/database operations.
* Memory Management:
  * Avoid leaking contexts (use `viewModelScope` in `ViewModels`).
  * Profile with Android Studio’s Profiler (CPU, Memory, Energy).
* RecyclerView Optimization:
  * Use `DiffUtil` for efficient updates.
  * Implement view caching (`RecyclerView.setItemViewCacheSize()`).


---