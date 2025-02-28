# Things to Avoid in Android Development (Especially with Clean Architecture)

When developing Android applications, particularly with Clean Architecture, there are several common pitfalls to avoid.
Here's a breakdown of things to avoid, focusing on software development practices within a Clean Architecture context:

## General Android Development Pitfalls

* **Memory Leaks:**
    * Avoid holding references to Activities or other long-lived objects in static variables or non-static inner
      classes.
    * Properly unregister listeners and dispose of resources.
* **Performance Issues:**
    * Avoid performing long-running operations on the main UI thread.
    * Optimize resource usage (e.g., image loading, network requests).
    * Avoid excessive object creation.
* **Battery Drain:**
    * Minimize background processing and network requests.
    * Use efficient data structures and algorithms.
* **Hardcoded Values:**
    * Avoid hardcoding strings, dimensions, or other values directly in code.
    * Use resources for better maintainability and localization.
* **Ignoring Android Lifecycle:**
    * Failure to properly handle the Activity and Fragment lifecycle can lead to crashes and unexpected behavior.
    * Always use lifecycle aware components.
* **Overly Complex UI:**
    * Keep UI layouts simple and efficient to avoid performance issues.
    * Avoid deeply nested layouts.
* **Permission Issues:**
    * Improperly requesting or handling runtime permissions can lead to a bad user experience.
* **Not targeting recent API levels:**
    * This leads to security vulnerabilities, and a bad user experience.

## Clean Architecture Specific Pitfalls

* **Violating Dependency Rules:**
    * Avoid dependencies from outer layers (e.g., UI) to inner layers (e.g., domain).
    * Ensure that dependencies flow inwards.
* **Overly Complex Use Cases/Interactors:**
    * Keep use cases focused on single responsibilities.
    * Avoid putting too much logic in use cases.
* **Data Layer Leaks:**
    * Avoid exposing data layer implementation details to other layers.
    * Use data transfer objects (DTOs) or domain models to decouple layers.
* **Presentation Layer Bloat:**
    * Avoid putting business logic in the presentation layer (ViewModels, Presenters).
    * The presentation layer should focus on UI logic and data presentation.
* **Ignoring Domain Layer:**
    * The domain layer should be the core of the application, containing business logic and entities.
    * Avoid making the domain layer an anemic model.
* **Unnecessary Layering:**
    * While Clean Architecture promotes layering, avoid adding layers that don't add value.
    * Keep the architecture as simple as possible.
* **Incorrect use of Repositories:**
    * Repositories should abstract data sources, not just be direct database access.
    * Repositories should be interface based.
* **Not writing Unit tests:**
    * Clean architecture is designed to be very testable, so not writing unit tests, especially for the domain layer,
      defeats the purpose.

## Key Takeaways

* Prioritize clean code, testability, and maintainability.
* Follow the principles of SOLID and Clean Architecture.
* Pay close attention to Android lifecycle and performance optimization.
* Always keep security in mind.