# Testing

When building Android apps, we want to make sure they're not just functional, but also enjoyable to use. That's where
two key types of testing come in. First, we have **manual testing**, which is like having real people try out the app,
clicking buttons, navigating menus, and seeing if everything feels natural and works as expected. This helps us catch
things like confusing layouts or awkward flows. Then, we have **unit testing**, which is all about checking the app's "
building blocks" – the individual pieces of code – to make sure they're doing their jobs correctly. Think of it as
double-checking that each part of the engine is running smoothly. By combining these two approaches, we can create
Android apps that are both reliable and a pleasure to use.

### Manual Testing

When it comes to manually testing your Android app, you'll want to use a variety of devices to ensure it works well for
everyone. Here's a breakdown of the two main options:

* **Emulators (Virtual Devices):**
    * Think of emulators as virtual Android phones running on your computer. They're incredibly useful for early-stage
      testing and quickly checking how your app behaves on different Android versions.
    * **Android API Range:** To cover a good range of users, we'll focus on testing with Android API levels ranging from
      API 24 (Android 7.0 Nougat) up to the current latest API. This ensures compatibility with a wide spectrum of
      devices.
    * **Benefits:** Emulators are convenient for developers as they are easily accessible and configurable. They also
      allow for quick testing of different screen sizes and Android versions.
    * **Considerations:** Emulators can sometimes be slower than real devices and may not perfectly replicate real-world
      device behavior, especially with hardware-specific features.

####

* **Real Devices (Physical Devices):**
    * Testing on real Android phones and tablets is crucial for getting a true sense of how your app will perform in the
      hands of users.
    * **Wireless Debugging (API 31+):** For devices running Android 12 (API 31) and later, wireless debugging offers a
      convenient way to connect your device to your development environment without the need for a USB cable. This
      simplifies the testing process and allows for more flexible testing scenarios.
    * **USB Debugging (All API Levels):** For broader device compatibility, especially for devices running older Android
      versions, USB debugging remains a reliable method. You'll connect your device to your computer via a USB cable,
      enabling you to install and debug your app.
    * **Benefits:** Real devices provide the most accurate representation of how your app will perform, including
      hardware performance, sensor behavior, and user experience.
    * **Considerations:** Testing on a variety of real devices can be time-consuming and requires access to a range of
      hardware.

### Unit Testing

Unit testing is a fundamental practice in Android development that focuses on verifying the functionality of individual components of your code in isolation. It helps ensure that each piece of your application works as intended, leading to a more stable and reliable app.

**Key Concepts:**

* **Isolation:** Unit tests focus on testing small, independent units of code, such as functions, classes, or methods. This isolation is crucial for pinpointing the source of bugs and ensuring that changes in one part of the code don't unintentionally affect other parts.
* **Automation:** Unit tests are automated, meaning they can be run repeatedly and consistently. This allows for rapid feedback on code changes and helps prevent regressions.
* **Frameworks:** Android development utilizes frameworks like JUnit for writing and running unit tests, and Mockito for creating mock objects to isolate dependencies.

**Types of Unit Tests:**

* **Local Unit Tests:**
    * These tests run on your development machine's Java Virtual Machine (JVM).
    * They are ideal for testing business logic, algorithms, and other components that don't directly interact with the Android framework.
    * These tests are fast and efficient, making them suitable for frequent execution.
    * **Libraries and Usage:**
        * **JUnit (4/5):** Used for structuring and running tests. You can use annotations like `@Test`, `@Before`, `@After` to define test cases and setup/teardown methods.
        * **Mockito:** Used for creating mock objects to replace dependencies. For example, mocking network requests or database interactions to isolate the unit under test. Use `Mockito.mock()`, `Mockito.when()`, and `Mockito.verify()` for mocking and verifying interactions.
        * **Truth:** Used for writing fluent and readable assertions. For example, `assertThat(result).isEqualTo(expected)` or `assertThat(list).contains(item)`.

####

* **Instrumented Unit Tests:**
    * These tests run on an Android emulator or a physical device.
    * They are used for testing components that interact with the Android framework, such as Activities, Fragments, and other Android-specific classes.
    * Instrumented tests allow you to verify the behavior of your code in a real Android environment.
    * **Libraries and Usage:**
        * **JUnit (4/5):** Used for structuring and running tests, similar to local unit tests.
        * **Mockito:** Can also be used in instrumented tests for mocking dependencies.
        * **Espresso:** Used for UI testing, simulating user interactions with the app's UI. Use `onView()`, `perform()`, and `check()` to interact with UI elements and verify their state. For example, `onView(withId(R.id.button)).perform(click())`.

**Libraries Description:**

* **JUnit (4/5):** A widely used Java testing framework for writing and running unit tests.
* **Mockito:** A mocking framework that allows you to create mock objects for dependencies, making it easier to isolate the code being tested.
* **Truth:** An assertion library that provides more readable and expressive assertions.
* **Espresso:** A UI testing framework that allows you to write automated UI tests for Android applications, ensuring that user interactions behave as expected.


## Additional Notes for Android Testing

Beyond the core unit and manual testing, several critical considerations ensure your Android application's quality and longevity.

* **Android 35+ Full Edge Behavior:**
    * Android API 35 (and beyond) introduces new behaviors related to full-edge display handling. It's crucial to meticulously test how your application's UI adapts to these changes.
    * Pay close attention to how content is displayed in the rounded corners and cutouts of modern devices.
    * Verify that interactive elements remain accessible and that no critical information is obscured by the device's physical edges.
    * Test with the latest emulators and real devices running Android 35+ to ensure compatibility.
####
* **Lower API Device Full Edge Behavior:**
    * While newer APIs introduce specific full-edge handling, it's equally important to test how your application behaves on devices running older Android versions.
    * Devices with rounded corners and cutouts existed before API 35.
    * Ensure that your layout handles these various screen types on lower API versions.
    * Test on a variety of older devices to identify and address any layout or usability issues.
####
* **Permission Checking Across API Levels:**
    * Android's permission model has evolved significantly across different API levels.
    * Thoroughly test permission requests and handling on both older and newer Android versions.
    * Verify that your application gracefully handles permission denials and provides clear explanations to users.
    * Ensure that permission requests are only made when necessary and that the user experience is consistent across API levels.
####
* **Public Library Management:**
    * When using public libraries, it's essential to assess their reliability and trustworthiness.
    * Verify that the libraries are actively maintained and have a strong community following.
    * Consider the risk of library expiration or discontinuation.
    * For critical or sensitive libraries, it's often best practice to copy the library's source code into your project. This provides greater control and mitigates the risk of external dependencies breaking your application.
####
* **Staying Up-to-Date with Android API Releases:**
    * Android's API is constantly evolving, with new features, improvements, and changes introduced with each release.
    * It's crucial to stay informed about the latest Android API releases and their implications for your application.
    * Regularly review the Android developer documentation and attend relevant conferences or webinars.
    * Proactively adapt your application to new API changes to ensure compatibility and leverage the latest features.


