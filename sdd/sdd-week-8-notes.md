**WOC7014: Framework-Based Software Design & Development**

**Week 8: Middleware and Authentication in Django**

*   **Focus:** This week covers two critical aspects of web application development in Django: **Middleware**, which provides a powerful mechanism for hooking into Django's request/response cycle, and Django's robust built-in **Authentication and Authorization System** for managing users, permissions, and access control.

**Part 1: Middleware in Django**

*   **Definition and Role:**
    *   Middleware in Django is a framework of hooks into Django's request/response processing. It's a light, low-level "plugin" system for globally altering Django's input or output.
    *   Think of it as a series of processing layers that a request passes through on its way to the view, and the response passes through on its way out to the client.
    *   It acts as an important **mediator**, "glue," or "lightweight processor" that can perform simple yet crucial tasks for every request/response cycle (or a subset based on its logic).
    *   **Key Focus:** Hooking into the client/server request/response lifecycle to add functionality or modify behavior without altering individual view functions.

*   **How Middleware Works (Request/Response Cycle):**
    1.  **Request Inbound:**
        *   When a request comes in, Django passes it through each middleware class listed in `settings.PY`'s `MIDDLEWARE` setting, in order from top to bottom.
        *   Each middleware can process the request or even short-circuit it by returning an `HttpResponse` directly (e.g., for authentication checks that deny access).
    2.  **View Processing:**
        *   If the request makes it through all request-phase middleware, it reaches the appropriate view function.
        *   The view processes the request and returns an `HttpResponse`.
    3.  **Response Outbound:**
        *   The response then travels back through the middleware classes, this time in reverse order (bottom to top).
        *   Each middleware can process or modify the response before it's sent to the client.

*   **Structure of Middleware (New Style - Django 1.10+):**
    *   Middleware is typically implemented as a Python class.
    *   It needs an `__init__` method that takes a `get_response` callable. This `get_response` callable could be the next middleware in the chain or the actual view.
    *   It must have a `__call__(self, request)` method:
        *   This method is called once per request.
        *   It can execute code *before* calling `self.get_response(request)` to get the response from the next layer.
        *   It can execute code *after* receiving the response from `self.get_response(request)` to modify it.
    ```python
    # myapp/middleware.py
    class MyCustomMiddleware:
        def __init__(self, get_response):
            self.get_response = get_response
            # One-time configuration and initialization (called once when the server starts).
            print("MyCustomMiddleware Initialized")

        def __call__(self, request):
            # Code to be executed for each request before
            # the view (and later middleware) are called.
            print(f"MyCustomMiddleware: Processing request to {request.path}")
            # request.my_custom_attribute = "Hello from middleware!" # Example: Modifying request

            response = self.get_response(request) # This calls the next middleware or the view

            # Code to be executed for each request/response after
            # the view is called.
            print(f"MyCustomMiddleware: Processing response with status {response.status_code}")
            # response['X-My-Custom-Header'] = 'Middleware was here' # Example: Modifying response

            return response
    ```
    *   **Older Style Middleware (Pre-Django 1.10):** Used methods like `process_request`, `process_view`, `process_template_response`, `process_exception`, and `process_response`. While still supported for backward compatibility, new style is preferred.

*   **Types of Middleware in Django:**
    *   **Built-in Middleware:** Provided by Django itself for essential functionalities. These are commonly found in the default `MIDDLEWARE` setting in `settings.py`.
    *   **Custom Middleware:** Created by developers to address specific application needs (like the example above).
    *   **Third-Party Middleware:** Provided by Django packages to add specialized features.

*   **Examples of Key Built-in Middleware (Order in `settings.MIDDLEWARE` is important!):**
    *   `django.middleware.security.SecurityMiddleware`:
        *   Implements various security enhancements: HSTS (HTTP Strict Transport Security), X-Content-Type-Options, X-XSS-Protection, SSL redirect, etc.
        *   Should generally be near the top of the list.
    *   `django.contrib.sessions.middleware.SessionMiddleware`:
        *   Enables session management. Allows Django to store and retrieve arbitrary data on a per-site-visitor basis.
        *   Essential for authentication (to know if a user is logged in across requests).
        *   Must come *after* `SecurityMiddleware` and *before* `AuthenticationMiddleware`.
    *   `django.middleware.common.CommonMiddleware`:
        *   Provides various conveniences:
            *   Forbids access to user agents in `DISALLOWED_USER_AGENTS` setting.
            *   Performs URL rewriting (appending slashes and/or `WWW` based on `APPEND_SLASH` and `PREPEND_WWW` settings).
            *   Handles `ETag` generation if `USE_ETAGS` is `True`.
    *   `django.middleware.csrf.CsrfViewMiddleware`:
        *   Adds protection against Cross-Site Request Forgeries (CSRF) by adding a hidden token to POST forms and verifying it on submission.
        *   Crucial for securing any site that uses forms.
    *   `django.contrib.auth.middleware.AuthenticationMiddleware`:
        *   Associates users with requests using sessions.
        *   Adds the `user` object (an instance of `User` or `AnonymousUser`) to every incoming `HttpRequest` object (`request.user`).
        *   Relies on `SessionMiddleware` and must come after it.
    *   `django.contrib.messages.middleware.MessageMiddleware`:
        *   Enables the cookie- and session-based messaging framework (for displaying one-time notification messages to users, e.g., "Profile updated successfully").
    *   `django.middleware.clickjacking.XFrameOptionsMiddleware`:
        *   Provides clickjacking protection via the `X-Frame-Options` header, preventing your site from being embedded in an `<iframe>` or `<object>` on other sites.

*   **Middleware Configuration in `settings.py`:**
    *   The `MIDDLEWARE` setting is a list of strings, where each string is the Python path to a middleware class.
    *   **Order is critical:** Middleware is processed sequentially during the request phase (top-down) and in reverse order during the response phase (bottom-up). Dependencies between middleware (e.g., `AuthenticationMiddleware` needs `SessionMiddleware`) dictate their correct ordering.
    ```python
    # settings.py
    MIDDLEWARE = [
        'django.middleware.security.SecurityMiddleware',
        'django.contrib.sessions.middleware.SessionMiddleware', # Sessions needed for auth
        'django.middleware.common.CommonMiddleware',
        'django.middleware.csrf.CsrfViewMiddleware',         # CSRF protection
        'django.contrib.auth.middleware.AuthenticationMiddleware', # Adds request.user
        'django.contrib.messages.middleware.MessageMiddleware', # For flash messages
        'django.middleware.clickjacking.XFrameOptionsMiddleware',
        # 'myapp.middleware.MyCustomMiddleware', # Example of custom middleware
    ]
    ```

*   **Use Cases for Custom Middleware:**
    *   Logging requests/responses.
    *   Adding custom HTTP headers.
    *   Handling specific exceptions globally.
    *   Modifying request/response objects (e.g., adding attributes to `request`).
    *   IP-based blocking or rate limiting.
    *   Setting timezone or language based on request information.

**Part 2: Authentication and Authorization in Django**

Django comes with a powerful and flexible authentication and authorization system (`django.contrib.auth`).

*   **Core Concepts:**
    *   **Authentication ("Who are you?"):**
        *   The process of verifying the identity of a user. It answers the question: "Is this user who they claim to be?"
        *   Typically involves a username and password, but can also use tokens, OAuth, etc.
        *   Django's `AuthenticationMiddleware` populates `request.user` with either an instance of the `User` model (if authenticated) or an `AnonymousUser` object.
    *   **Authorization ("What are you allowed to do?"):**
        *   The process of determining whether an authenticated user has the necessary permissions to perform a specific action or access a particular resource.
        *   Django's system includes:
            *   **Permissions:** Flags designating whether a user can perform a specific task (e.g., `can_edit_post`, `can_delete_user`). Permissions are often automatically created for models (add, change, delete, view).
            *   **Groups:** A way to categorize users and assign permissions to the group. A user in a group inherits all permissions of that group.
            *   **User flags:**
                *   `is_active`: Designates whether the user account is considered active. Inactive users cannot log in.
                *   `is_staff`: Designates whether the user can access the Django admin site.
                *   `is_superuser`: Designates that this user has all permissions without them being explicitly assigned.

*   **Key Features of Django's Authentication System (`django.contrib.auth`):**
    *   **User Model (`django.contrib.auth.models.User`):**
        *   A built-in model with fields like `username`, `password` (stored hashed), `email`, `first_name`, `last_name`, and the flags (`is_active`, `is_staff`, `is_superuser`).
        *   **Custom User Model:** For more complex needs, Django allows you to substitute the default `User` model with a custom one (e.g., if you want to use email as the username or add fields like `date_of_birth`). This should be done at the beginning of a project.
    *   **Password Management:**
        *   Securely hashes passwords (using algorithms like PBKDF2 by default, configurable). Raw passwords are never stored.
        *   Provides utilities for setting and checking passwords.
    *   **Forms:**
        *   `AuthenticationForm`: For handling user login.
        *   `UserCreationForm`: For user registration.
        *   `PasswordChangeForm`, `PasswordResetForm`, `SetPasswordForm`.
    *   **Views:**
        *   Django provides built-in views for common auth actions (login, logout, password change, password reset) in `django.contrib.auth.views`. These are class-based views.
    *   **Decorators & Mixins for Access Control:**
        *   `@login_required` (decorator for function-based views): Redirects unauthenticated users to the login page.
        *   `LoginRequiredMixin` (for class-based views): Similar functionality.
        *   `@permission_required('app_label.codename')` (decorator): Checks if the user has a specific permission.
        *   `PermissionRequiredMixin` (for class-based views).
        *   `UserPassesTestMixin` / `@user_passes_test`: For more complex custom authorization checks.
    *   **Session Management:** Integrates with `django.contrib.sessions` to maintain login state across requests.

*   **Implementation Components & Common Workflow:**
    *   **1. User Registration:**
        *   Create a form (often subclassing `UserCreationForm` or a custom form).
        *   Create a view to display the form and handle its submission.
        *   On valid submission, create a new `User` object and save it. Often, you'd log the user in immediately after registration.
    *   **2. User Login (`django.contrib.auth.views.LoginView` or custom):**
        *   Presents a login form (`AuthenticationForm`).
        *   On submission, the form validates credentials.
        *   If valid, the `login()` function (`from django.contrib.auth import login`) is called. This function creates a session for the user, effectively logging them in. `AuthenticationMiddleware` then attaches this user to subsequent requests.
    *   **3. User Logout (`django.contrib.auth.views.LogoutView` or custom):**
        *   Calls the `logout()` function (`from django.contrib.auth import logout`). This function clears the user's session data.
    *   **4. Access Control in Views:**
        ```python
        from django.contrib.auth.decorators import login_required, permission_required
        from django.contrib.auth.mixins import LoginRequiredMixin, PermissionRequiredMixin
        from django.views.generic import ListView
        from .models import Article

        @login_required # Redirects to LOGIN_URL if not logged in
        def my_protected_view(request):
            # ... view logic for logged-in users ...
            return HttpResponse("This is a protected view.")

        @permission_required('myapp.view_article', raise_exception=True) # Or login_url='/custom/login/'
        def article_detail_view(request, slug):
            # ... view logic for users with 'view_article' permission ...
            article = Article.objects.get(slug=slug)
            return render(request, 'myapp/article_detail.html', {'article': article})

        class ProtectedListView(LoginRequiredMixin, ListView):
            model = Article
            template_name = 'myapp/article_list.html'
            # login_url = '/custom_login_url/' # Optional: override default login URL
            # redirect_field_name = 'my_next_parameter' # Optional: override 'next'

        class ArticleCreateView(PermissionRequiredMixin, CreateView):
            model = Article
            fields = ['title', 'content']
            permission_required = 'myapp.add_article'
            # Or permission_required = ('myapp.add_article', 'myapp.change_article')
        ```
    *   **5. Checking Permissions in Templates:**
        *   The `perms` variable (from `django.contrib.auth.context_processors.auth`) allows checking permissions directly in templates:
        ```html
        {% if user.is_authenticated %}
            <p>Welcome, {{ user.username }}!</p>
            {% if perms.myapp.add_article %}
                <a href="{% url 'article_create' %}">Add New Article</a>
            {% endif %}
            {% if perms.myapp.change_secretdata %}
                <p>You can change secret data.</p>
            {% endif %}
        {% endif %}
        ```

*   **Security Considerations for Authentication:**
    *   **Password Policies:** Enforce strong password policies (length, complexity). Django doesn't do this by default but provides validators and third-party packages can help.
    *   **HTTPS:** Always use HTTPS for login forms and any page handling sensitive data to protect credentials in transit. `SecurityMiddleware` can help enforce this.
    *   **Protection Against Brute Force Attacks:** Implement measures like rate limiting login attempts, CAPTCHAs, or account lockout after too many failed attempts (often via third-party packages or custom logic).
    *   **Session Security:**
        *   Use secure session cookies (`SESSION_COOKIE_SECURE = True`).
        *   Set `SESSION_COOKIE_HTTPONLY = True` to prevent client-side JavaScript access to session cookies.
        *   Consider session expiry (`SESSION_COOKIE_AGE`).
    *   **CSRF Protection:** Already handled by `CsrfViewMiddleware` for POST requests, crucial for preventing unauthorized actions.
    *   **Regularly Update Django:** To get the latest security patches.

By understanding middleware and the authentication system, you can build secure and robust Django applications that manage user access effectively.