# MusicApp

A contemporary music discovery platform engineered with cutting-edge Android technologies. This sophisticated application empowers users to explore musical compositions, access comprehensive track information, and curate personalized collections of preferred audio content through intuitive local storage management

## Features

*   **Reactive Real-Time Search:** Discover music instantly with a search interface that provides immediate feedback and results as you type.
*   **Comprehensive Track Analytics:** Access detailed information about any track, featuring an enhanced album artwork viewer, precise duration metrics, and release chronology.
*   **Favorites:** Effortlessly build and maintain a bespoke library of preferred tracks with seamless add/remove functionality.
*   **Localized Data Persistence:** All curated selections are securely stored locally via a Room database architecture, guaranteeing persistent availability across application sessions.
*   **Declarative Interface Architecture:** An entirely Jetpack Compose-based user experience delivering fluid responsiveness with distinct visual states for loading processes, error conditions, and content presentation.

## Architecture

The application is architected using Clean Architecture principles to establish a robust, scalable, and maintainable codebase. This is achieved through a clear separation of concerns into three independent, modular layers:

*   **Presentation (UI Layer):**
    *   Developed exclusively with **Jetpack Compose**, embracing a modern, declarative UI paradigm. 
    *   Adheres to the **Model-View-ViewModel (MVVM)** pattern for structured state management.
    *   **ViewModel** components surface the UI state via observable StateFlow streams, establishing a unidirectional and reactive data pipeline from the business logic to the user interface.
    *   Manages user input, orchestrates navigation, and subscribes to the data streams provided by the domain layer.

*   **Domain Layer (Business Logic Core):**
    *   Houses the essential business rules and application logic, independent of external frameworks.
    *   Operational logic is compartmentalized into single-responsibility **Use Cases** (Interactors), such as `SearchTracksUseCase` and `AddTrackToFavoritesUseCase`.
    *   Defines the application's core **Domain Entities** (e.g., `Track`, `Album`, `Artist`)—pure data models that are agnostic to any specific data source implementation, ensuring business logic remains decoupled and testable.
    *   Declares abstract `Repository` interfaces here, adhering to the Dependency Inversion Principle, to dictate the contract for data operations without binding to concrete implementations.

*   **Data Layer:**
    *   Provides concrete implementations for the `Repository` interfaces defined in the domain layer.
    *   Acts as a gateway that abstracts and consolidates all data sources, whether local or remote.
    *   Leverages **Retrofit** for performing structured HTTP network calls to external APIs.
    *   Employs **Room** to furnish a robust, SQLite-based local persistence layer for storing user favorites.
    *   Incorporates **Mapper** components responsible for transforming data transfer objects (DTOs) from the network and persistence entities from the database into the clean domain models used by the application's core logic.

## Key Technologies & Libraries

*   **UI:**
    *   [Jetpack Compose](https://developer.android.com/jetpack/compose): For building a modern, declarative UI.
    *   [Navigation for Compose](https://developer.android.com/jetpack/compose/navigation): For handling navigation between screens.
    *   [Coil](https://coil-kt.github.io/coil/): For efficient image loading.

*   **Architecture & Async:**
    *   [Kotlin Coroutines & Flow](https://kotlinlang.org/docs/coroutines-guide.html): For managing asynchronous operations and creating reactive data streams.
    *   [Koin](https://insert-koin.io/): For dependency injection, used to provide dependencies across all layers.

*   **Data:**
    *   [Retrofit](https://square.github.io/retrofit/): For type-safe HTTP requests to the Deezer API.
    *   [Room](https://developer.android.com/training/data-storage/room): For robust, local database persistence.
    *   [Kotlinx.serialization](https://github.com/Kotlin/kotlinx.serialization): For parsing JSON data from the API.

## System Requirements

*   **Minimum Android Version:** Android 5.0 (Lollipop), API 21
