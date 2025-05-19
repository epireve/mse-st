**WOC7014: Framework-Based Software Design & Development - Expanded Study Notes**

**Week 8: Authentication**

*   **Focus:** This week covers middleware in Django and the authentication system.

**Middleware**

*   **Definition:**
    *   An important mediator or "glue" or "lightweight processor"
    *   Helps communicate or perform simple yet crucial tasks between components
    *   Focuses on "hooking" between request/response cycle (client/server cycle)
    *   A light, low-level plugin that globally alters Django's input/output

*   **Types of Middleware in Django:**
    *   **Built-in middleware:** Provided by Django for specific functions
    *   **Custom middleware:** Created by developers for specific needs

*   **Examples of Built-in Middleware:**
    *   **CommonMiddleware:** Enables URL consistencies (append WWW or "/")
    *   **SecurityMiddleware:** Provides security enhancement during request/response cycle
    *   **CsrfViewMiddleware:** Protects against Cross Site Request Forgeries
    *   **SessionMiddleware:** Manages sessions across requests
    *   **AuthenticationMiddleware:** Associates users with requests using sessions

*   **Middleware Configuration:**
    *   Defined in settings.py
    *   Must follow certain sequences for proper operation
    ```python
    MIDDLEWARE = [
        'django.middleware.security.SecurityMiddleware',
        'django.contrib.sessions.middleware.SessionMiddleware',
        'django.middleware.common.CommonMiddleware',
        'django.middleware.csrf.CsrfViewMiddleware',
        'django.contrib.auth.middleware.AuthenticationMiddleware',
        'django.contrib.messages.middleware.MessageMiddleware',
        'django.middleware.clickjacking.XFrameOptionsMiddleware',
    ]
    ```

**Authentication and Authorization**

*   **Authentication:**
    *   Answers "Who are you?"
    *   Validates that a system is being accessed by the right person
    *   Verifies user identity

*   **Authorization:**
    *   Answers "What are you allowed to do?"
    *   Determines user permissions after authentication
    *   Controls access to resources and actions

**Django Authentication System**

*   **Features:**
    *   User accounts and groups
    *   Permissions and authorization
    *   Form validation
    *   User authentication (login/logout)
    *   Session management

*   **Implementation Components:**
    *   **User Registration Form:** Collects user information for account creation
    *   **Login Function:** Authenticates users and creates sessions
    *   **Logout Function:** Terminates user sessions
    *   **LoginRequired Mixin:** Restricts access to authenticated users only

*   **Security Considerations:**
    *   Password hashing and storage
    *   Protection against brute force attacks
    *   Session security
    *   CSRF protection