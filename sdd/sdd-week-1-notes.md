**WOC7014: Framework-Based Software Design & Development - Expanded Study Notes**

**Week 1: Introduction to Framework Based Development**

*   **Focus:** This week introduces the concept of frameworks, their purpose, and how they differ from libraries and software architecture.

**Key Concepts**

*   **Software Framework Definition:**
    *   Large codebase or collection of code meant to provide reusable behavior for targeted projects
    *   Most programming languages have at least one major framework that is actively developed and maintained
    *   Main purpose: Lessen the work of programmers dealing with standard low-level details of the working system

*   **Types of Software Frameworks:**
    *   **Frontend Frameworks:** Focus on user interface and client-side functionality (e.g., React, Angular, Vue.js)
    *   **Backend Frameworks:** Handle server-side logic and data processing (e.g., Django, ASP.Net Core, Express.js)
    *   **Mobile Application Frameworks:** Facilitate mobile app development (e.g., Flutter, React Native, Ionic)

*   **Advantages of Using Frameworks:**
    *   Removal of tedious and repetitive tasks
    *   Time savings through pre-built components and structures
    *   Enhanced security and maintainability

*   **Disadvantages of Using Frameworks:**
    *   Contain interdependent systems requiring comprehensive understanding
    *   Learning curve to fully understand how the framework works

**Web Application Frameworks**

*   **Definition:** Software frameworks used to streamline web app and website development, web services, and web resources
*   **Purpose:**
    *   Provide a standard way to build and deploy web applications
    *   Offer core functionality common to most web applications
    *   Handle user session management and authentication
    *   Manage security, caching, data persistence, administrative interfaces
    *   Implement templating systems

*   **MVC Architecture in Web Frameworks:**
    *   **Model:** Controls data organization and storage, may define data-specific behavior
    *   **View:** Controls how data is displayed and generates output for the user
    *   **Controller:** Acts as the glue (middleman) between the Model and View (and the User)

*   **Benefits of MVC Pattern:**
    *   Separates application characteristics into three layers
    *   Provides loose coupling between layers
    *   Enables parallel development (different developers can work on different layers simultaneously)
    *   Facilitates code reuse and maintenance

**Framework vs. Library Comparison:**
*   **Inversion of Control:**
    - Frameworks: Dictate program flow (Hollywood Principle: "Don't call us, we'll call you")
    - Libraries: Developer controls flow through direct calls
*   **Extensibility:**
    - Frameworks: Designed for extension through inheritance and composition
    - Libraries: Typically used as-is with configuration
*   **Completeness:**
    - Frameworks: Provide complete application skeleton
    - Libraries: Solve specific problems within larger systems

**Historical Context:**
*   **MVC Origins:** Developed at Xerox PARC in late 1970s for Smalltalk-80
*   **Web Framework Evolution:** From CGI scripts (1990s) to modern full-stack frameworks
*   **Mobile Framework Trends:** Cross-platform solutions vs. native development debates

**Framework Selection Criteria:**
1. Community Support (StackOverflow questions, GitHub stars)
2. Learning Curve vs. Long-term Maintainability
3. Security Track Record (OWASP compliance)
4. Documentation Quality
5. Enterprise Adoption Rates