**WOC7014: Framework-Based Software Design & Development - Expanded Study Notes**

**Week 2: Django Installation and Basic Python**

*   **Focus:** This week covers the setup of Django development environment and introduces basic Python concepts relevant to Django development.

**Virtual Environments**

*   **Purpose:**
    *   Ensure each project has its own configuration settings, versioning, packages, etc.
    *   Isolate dependencies to avoid conflicts between projects
    *   Many options available: venv, pyenv, virtualenv (used in this course)

*   **Benefits:**
    *   Project-specific Python versions and packages
    *   Clean development environment for each project
    *   Easier dependency management

**Django Project Structure**

*   **Creating a New Django Project:**
    ```bash
    django-admin startproject MyDjangoProject
    ```

*   **Basic Project Structure:**
    *   **manage.py:** Command-line utility for debugging, deploying, and running web applications
    *   **__init__.py:** Blank Python script indicating to the Python interpreter that the directory is a Python package
    *   **settings.py:** Stores all Django project's main settings, used to add applications and middleware
    *   **urls.py:** Stores URL patterns for the project, addresses resources like images, webpages, websites
    *   **wsgi.py:** Web Server Gateway Interface - describes how servers interact with applications, helps run development server and deploy to production
    *   **asgi.py:** Asynchronous Server Gateway Interface - similar to wsgi but with additional functionalities

*   **Key Concepts:**
    *   Django projects contain multiple apps
    *   Each app should focus on a specific functionality
    *   The project settings control the overall configuration
    *   URL routing determines how requests are handled

**Advanced Virtual Environment Concepts:**
*   **Dependency Isolation Strategies:**
    - PEP 582 (__pypackages__ directory)
    - PEP 665 (Standardized package format)
    - Poetry vs. pipenv vs. conda comparisons
*   **Virtual Environment Best Practices:**
    - .gitignore recommendations for Python projects
    - pip freeze vs. pip-compile workflows
    - Multi-stage Docker builds with venv

**Django Project Structure Deep Dive:**
```python
# settings.py Advanced Configuration
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.redis.RedisCache',
        'LOCATION': 'redis://127.0.0.1:6379',
    }
}
# Custom Middleware Example
class CustomSecurityHeadersMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response
        
    def __call__(self, request):
        response = self.get_response(request)
        response['X-Content-Type-Options'] = 'nosniff'
        return response