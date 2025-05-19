**WOC7014: Framework-Based Software Design & Development**

**Week 2: Django Installation and Basic Python for Django**

*   **Focus:** This week covers the critical setup of a robust Django development environment, with a strong emphasis on virtual environments. We will also touch upon the foundational Python concepts directly relevant to understanding and working with Django.

**Virtual Environments**

*   **Purpose and Importance:**
    *   A virtual environment is an isolated Python environment that allows projects to have their own specific set_of dependencies (libraries and their versions) and Python interpreter version, separate from other projects and the global Python installation.
    *   **Core Problem Solved: Dependency Conflicts.** Different projects may require different versions of the same library. For example, Project A might need `requests==2.20.0` while Project B needs `requests==2.25.0`. Without isolation, installing one would break the other. Virtual environments prevent these version clashes.
    *   **Reproducibility:** Ensures that an application developed in one environment will behave identically in another (e.g., when deploying to production or when another developer works on it) by precisely defining its dependencies (often via a `requirements.txt` file).

*   **Benefits:**
    *   **Project-specific Python versions and packages:** While tools like `pyenv` manage Python versions, virtual environments (like `venv` or `virtualenv`) manage package versions within a specific Python interpreter environment.
    *   **Clean development environment:** Keeps your global Python installation tidy and free from project-specific packages.
    *   **Easier dependency management:** Tools often integrate with `pip` to install, uninstall, and list packages specific to the active environment.
    *   **Simplified Collaboration:** Developers can easily replicate the exact environment needed for a project by sharing a dependency file.
    *   **Deployment Consistency:** Production environments can be configured to match the development environment precisely, reducing "it works on my machine" issues.

*   **Common Tools for Virtual Environments:**
    *   **`venv`:** (Recommended for Python 3.3+) A module included in the Python standard library. Created using `python -m venv myenv_name`.
    *   **`virtualenv`:** A third-party tool that predates `venv` and offers some additional features, also supporting older Python 2 versions. Often used if more advanced features or broader Python version support is needed. Installed via `pip install virtualenv`.
    *   **`pyenv`:** While not strictly a virtual environment manager in the same vein, `pyenv` is used to manage multiple Python versions on a single machine. It can be used in conjunction with `venv` or `virtualenv` (e.g., `pyenv-virtualenv` plugin).
    *   **`conda`:** An open-source package management system and environment management system that is popular in the data science community. It can manage Python versions and packages, as well as non-Python libraries.

*   **Basic `venv` Workflow:**
    1.  **Creation:** `python -m venv venv` (conventionally names the environment folder `venv` or `.venv`)
    2.  **Activation:**
        *   Windows: `.\venv\Scripts\activate`
        *   macOS/Linux: `source venv/bin/activate`
        *   (The command prompt usually changes to indicate the active environment)
    3.  **Install packages:** `pip install django psycopg2-binary ...`
    4.  **Freeze dependencies:** `pip freeze > requirements.txt` (captures exact versions)
    5.  **Deactivation:** `deactivate` (when done working on the project)
    6.  **Replicating environment:** `pip install -r requirements.txt` (in a new, activated virtual environment)

**Django Project Structure**

*   **Creating a New Django Project:**
    *   Once your virtual environment is activated and Django is installed (`pip install django`), you create a project using:
        ```bash
        django-admin startproject MyDjangoProject .
        ```
        *   `django-admin`: Django's command-line utility for administrative tasks.
        *   `startproject`: The command to create a new project.
        *   `MyDjangoProject`: The name of your project. This will be the name of the configuration directory.
        *   `.` (optional, but common): Creates the project in the current directory. Without it, it creates an extra parent directory.

*   **Basic Project Structure (after `startproject MyDjangoProject .`):**
    ```
    MyDjangoProject/
    ├── manage.py
    └── MyDjangoProject/  # This is the Python package for your project.
        ├── __init__.py
        ├── settings.py
        ├── urls.py
        ├── wsgi.py
        └── asgi.py
    ```
    *   **Outer `MyDjangoProject/` (Root Directory):** This is just a container for your project. Its name doesn’t matter to Django; you can rename it to anything.
    *   **`manage.py`:**
        *   A command-line utility that lets you interact with this Django project. It's a thin wrapper around `django-admin`.
        *   **Key Uses:**
            *   `python manage.py runserver`: Starts the development server.
            *   `python manage.py startapp app_name`: Creates a new Django app within the project.
            *   `python manage.py makemigrations`: Creates new migration files based on changes detected to your models.
            *   `python manage.py migrate`: Applies migrations to the database.
            *   `python manage.py createsuperuser`: Creates an admin user.
            *   `python manage.py shell`: Opens an interactive Python shell with your project's settings loaded.
            *   `python manage.py test`: Runs tests.
            *   `python manage.py collectstatic`: Collects static files into a single location for deployment.
    *   **Inner `MyDjangoProject/` (Project Configuration Directory):**
        *   The actual Python package for your project. Its name is the Python package name you’ll need to use to import anything inside it (e.g., `from MyDjangoProject.settings import DEBUG`).
        *   **`__init__.py`:** An empty file that tells Python that this directory should be considered a Python package. This allows you to import modules from this directory.
        *   **`settings.py`:**
            *   Contains all the configuration for your Django project.
            *   **Key Settings:** `DEBUG`, `ALLOWED_HOSTS`, `INSTALLED_APPS` (to register your apps and third-party apps), `MIDDLEWARE`, `ROOT_URLCONF`, `TEMPLATES`, `DATABASES`, `STATIC_URL`, `MEDIA_ROOT`, `SECRET_KEY`, etc.
            *   This file is pure Python, allowing for dynamic configuration.
        *   **`urls.py`:**
            *   The URL declarations for this Django project; a "table of contents" of your Django-powered site.
            *   Contains a `urlpatterns` list that routes URLs to views.
            *   This is the primary (root) URL configuration. Each app can also have its own `urls.py`.
        *   **`wsgi.py` (Web Server Gateway Interface):**
            *   An entry-point for WSGI-compatible web servers to serve your project. WSGI is the Python standard for web servers and applications.
            *   It defines how a web server communicates with your Django application for synchronous requests.
            *   Used by servers like Gunicorn, uWSGI during deployment.
        *   **`asgi.py` (Asynchronous Server Gateway Interface):**
            *   An entry-point for ASGI-compatible web servers. ASGI is the successor to WSGI, designed to handle both synchronous and asynchronous applications (e.g., WebSockets, long-polling HTTP).
            *   Allows Django to leverage asynchronous features.
            *   Used by servers like Daphne, Uvicorn.

*   **Key Concepts: Projects vs. Apps:**
    *   **Project:** The entire web application or website. It encompasses all configurations and apps. A project contains one or more apps.
    *   **App:** A self-contained module within a project that handles a specific piece of functionality (e.g., a blog app, a polling app, a user authentication app).
        *   Apps are designed to be reusable. A good app can potentially be plugged into other Django projects.
        *   To create an app: `python manage.py startapp myappname`
        *   This creates a directory `myappname/` with its own `models.py`, `views.py`, `admin.py`, `apps.py`, `tests.py`, and a `migrations/` directory.
    *   **Project Settings (`settings.py`):** Control the overall behavior, database connections, installed apps, middleware, etc., for the entire project.
    *   **URL Routing (`urls.py`):** The project's main `urls.py` directs requests to the appropriate app's `urls.py` (if defined) or directly to views.

**Advanced Virtual Environment Concepts & Best Practices**

*   **Dependency Isolation Strategies & Tools:**
    *   **`pip freeze > requirements.txt`:** The most basic method. Captures all packages in the current environment, including transitive dependencies (dependencies of your dependencies).
        *   **Pros:** Simple, universally understood.
        *   **Cons:** Doesn't distinguish between direct dependencies (those you explicitly installed) and transitive ones. Can lead to "version pinning" issues if not managed carefully.
    *   **`pip-tools` (with `pip-compile`):**
        *   You maintain a `requirements.in` file listing only your direct dependencies (optionally with loose version specifiers like `django>=3.2,<4.0`).
        *   `pip-compile requirements.in` generates a fully pinned `requirements.txt` file, resolving all transitive dependencies.
        *   **Pros:** Clear separation of direct vs. transitive dependencies, repeatable builds, helps manage updates more systematically.
    *   **Poetry:** A modern Python dependency management and packaging tool.
        *   Uses a `pyproject.toml` file to declare dependencies and project metadata.
        *   Manages its own virtual environments automatically (or can use existing ones).
        *   Has a lock file (`poetry.lock`) for reproducible builds.
        *   Provides build and packaging features.
        *   **Pros:** All-in-one tool, robust dependency resolution, good for library development as well as applications.
    *   **Pipenv:** Another tool aiming to bring "the best of all packaging worlds" to Python.
        *   Uses `Pipfile` (for direct dependencies) and `Pipfile.lock` (for pinned versions of all dependencies).
        *   Also manages virtual environments automatically.
        *   **Pros:** Aims to simplify workflow, integrates `virtualenv` and `pip`.
    *   **Conda:** As mentioned, more than just Python virtual environments; it's a full package and environment manager, especially for scientific computing. Can manage Python and non-Python dependencies. Environments are managed with `conda create`, `conda activate`, etc.
    *   **PEP 582 (`__pypackages__` directory):** A proposal for a local package directory that Python would automatically recognize, potentially simplifying some aspects of environment management by avoiding explicit activation/deactivation. Not yet widely adopted or part of standard Python behavior.
    *   **PEP 665 (Overhauling BPython packaging specification formats):** This was a proposal related to standardizing package distribution. It has evolved, and current efforts focus on interoperability and standards like `pyproject.toml`.

*   **Virtual Environment Best Practices:**
    *   **Always use a virtual environment for every Python project.** No exceptions.
    *   **Add your virtual environment directory to `.gitignore`:** (e.g., `venv/`, `.venv/`, `__pypackages__/`, `.direnv/`) to prevent committing it to version control. Only commit dependency definition files (`requirements.txt`, `Pipfile`, `pyproject.toml`, and their lock files).
    *   **Regularly update your dependencies:** Use tools like `pip list --outdated` or specific commands from Poetry/Pipenv to check for updates and apply them cautiously, testing thoroughly.
    *   **Pin your dependencies:** Always use a lock file or a fully pinned `requirements.txt` for reproducible builds, especially for production deployments.
    *   **Multi-stage Docker builds with venv:** When containerizing Django apps with Docker, use multi-stage builds. One stage can install dependencies into a virtual environment, and then only this environment (or the necessary parts) is copied to the final, smaller production image, reducing image size and attack surface.
        ```dockerfile
        # Stage 1: Build stage
        FROM python:3.9-slim as builder
        WORKDIR /app
        RUN python -m venv /opt/venv # Create venv
        ENV PATH="/opt/venv/bin:$PATH" # Activate venv
        COPY requirements.txt .
        RUN pip install --no-cache-dir -r requirements.txt

        # Stage 2: Final stage
        FROM python:3.9-slim
        WORKDIR /app
        COPY --from=builder /opt/venv /opt/venv # Copy venv
        ENV PATH="/opt/venv/bin:$PATH" # Activate venv
        COPY . .
        # Add CMD to run your application (e.g., gunicorn)
        ```

**Django Project Structure Deep Dive: `settings.py` Examples**

*   **`settings.py` Advanced Configuration (Conceptual Examples):**
    *   **`CACHES`:** Django supports various caching backends (in-memory, database, Memcached, Redis). Configuring a robust cache is crucial for performance.
        ```python
        # settings.py
        CACHES = {
            'default': {
                'BACKEND': 'django_redis.cache.RedisCache', # Using django-redis
                'LOCATION': 'redis://127.0.0.1:6379/1', # Redis server address and DB number
                'OPTIONS': {
                    'CLIENT_CLASS': 'django_redis.client.DefaultClient',
                }
            },
            'another_cache': { # Example of multiple cache configurations
                'BACKEND': 'django.core.cache.backends.memcached.PyMemcacheCache',
                'LOCATION': '127.0.0.1:11211',
            }
        }
        ```
    *   **Custom Middleware:** Middleware components are processed for every request/response. You can write your own to add custom behavior.
        *   Middleware is a class with specific methods like `__init__` and `__call__`, or older style function-based middleware hook methods (`process_request`, `process_view`, `process_template_response`, `process_exception`, `process_response`).
        *   The example `CustomSecurityHeadersMiddleware` adds a security header.
        ```python
        # myapp/middleware.py (example custom middleware file)
        class CustomSecurityHeadersMiddleware:
            def __init__(self, get_response):
                self.get_response = get_response
                # One-time configuration and initialization.

            def __call__(self, request):
                # Code to be executed for each request before
                # the view (and later middleware) are called.

                response = self.get_response(request)

                # Code to be executed for each request/response after
                # the view is called.
                response['X-Content-Type-Options'] = 'nosniff'
                response['X-Frame-Options'] = 'DENY'
                # Add other headers like Content-Security-Policy etc.

                return response

        # settings.py - Registering the custom middleware
        MIDDLEWARE = [
            'django.middleware.security.SecurityMiddleware',
            # ... other default middleware ...
            'myapp.middleware.CustomSecurityHeadersMiddleware', # Add your custom middleware
            # ...
        ]
        ```
    *   **`STATIC_ROOT` vs. `STATICFILES_DIRS` vs. `STATIC_URL`:**
        *   `STATIC_URL`: The URL prefix for static files when served (e.g., `/static/`). Used in templates.
        *   `STATICFILES_DIRS`: A list of directories where Django will look for additional static files besides the `static/` subdirectory of each app (e.g., for project-wide static assets).
        *   `STATIC_ROOT`: The absolute path to the directory where `collectstatic` will gather all static files for deployment. This directory is typically served by a dedicated web server like Nginx in production. **Do not put files here directly; `collectstatic` populates it.**
    *   **Database Routers:** For more complex setups with multiple databases, you can define database routers to control which database is used for specific models or operations.

This provides a more thorough foundation for understanding the Django environment setup.