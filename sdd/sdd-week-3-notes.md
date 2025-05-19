**WOC7014: Framework-Based Software Design & Development - Expanded Study Notes**

**Week 3: Framework Designing**

*   **Focus:** This week explores framework design principles, with emphasis on the MVC architecture and its implementation.

**MVC Framework Components**

*   **Model-View-Controller (MVC) Architecture:**
    *   A software architectural pattern traditionally used for implementing user interfaces on computers
    *   Implementation in different languages might have slight variations, but conceptually remains the same

*   **Components:**
    *   **Model:** Controls data organization and storage, defines data-specific behavior
    *   **View:** Controls how data is displayed, generates output for the user
    *   **Controller:** Acts as the glue between Model and View, handles user input logic

*   **Real-World Example:**
    *   Login system:
        *   Model = user database
        *   View = login page
        *   Controller = handles authentication

**Benefits of MVC Architecture**

*   **Separation of Concerns:**
    *   Three-layered architecture separates application characteristics
    *   First layer: user input logic
    *   Second layer: business logic
    *   Third layer: user interface logic

*   **Loose Coupling:**
    *   Provides very loose coupling among the three layers
    *   Specifies the location of each logic in the application

*   **Parallel Development:**
    *   Enables multiple developers to work on a single application simultaneously
    *   One developer can work on user input logic (controller)
    *   Another can work on user interface logic (view)
    *   A third can work on business logic (model)

**MVC Architecture Diagram**

*   **Flow:**
    *   User sends a request to the Controller
    *   Controller manipulates the Model
    *   Model updates the View
    *   View returns the request to the Controller
    *   Controller presents the final output to the User

**Project Structure Example**

*   **Typical Django Project Structure:**
    *   Multiple apps organized by functionality
    *   Each app contains models, views, templates, and tests
    *   Central project configuration manages the overall application

**MVC Variations Across Frameworks:**
| Framework   | Model Layer              | View Layer           | Controller Layer      |
|-------------|--------------------------|----------------------|-----------------------|
| Django      | ORM Models               | Templates            | View Functions        |
| Ruby on Rails | Active Record         | ERB/HAML Templates   | ActionController      |
| ASP.NET MVC | Entity Framework        | Razor Pages          | Controller Classes    |

**Design Patterns in MVC:**
1. Observer Pattern (Model-View communication)
2. Strategy Pattern (Controller behavior variation)
3. Composite Pattern (Complex view hierarchies)
4. Decorator Pattern (Middleware implementation)

**Performance Considerations:**
*   N+1 Query Problem in ORM
*   View Caching Strategies
*   Lazy Loading vs. Eager Loading
*   Connection Pooling Configuration