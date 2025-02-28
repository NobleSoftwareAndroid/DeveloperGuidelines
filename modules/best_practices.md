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

* Use descriptive naming conventions for variables, functions, and classes.
* Apply Android-specific style guidelines.
* Follow camelCase for variables and functions, and PascalCase for classes and interfaces.
* Prefix boolean variables with `is` or `has`.
* Use consistent indentation and limit line length.
* Add clear and concise comments.
* Utilize lint and code analysis tools, and integrate them into CI/CD pipelines.


Naming Conventions
* **Classes**: Suffix with purpose (e.g., `LoginFragment`, `UserRepositoryImpl`).
* **Variables**: Use descriptive names (e.g., `isUserLoggedIn` instead of flag).
* **Resources**: Prefix for clarity (e.g., `img_imagename`, `ic_iconname`).

Code Style
* Follow Kotlin Style Guide.
* Use `ktlint` or `Detekt` for automated linting.
* Format code with Android Studio’s built-in formatter.

Documentation
* Document public APIs with KDoc.
* Use `// TODO` or `// FIXME` sparingly and resolve them promptly.
* Avoid redundant comments; write self-explanatory code.


## 3. Security

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

## 4. Performance & Optimization
* Background Threading: Use coroutines (`Dispatchers.IO`) for network/database operations.
* Memory Management:
  * Avoid leaking contexts (use `viewModelScope` in `ViewModels`).
  * Profile with Android Studio’s Profiler (CPU, Memory, Energy).
* RecyclerView Optimization:
  * Use `DiffUtil` for efficient updates.
  * Implement view caching (`RecyclerView.setItemViewCacheSize()`).


---