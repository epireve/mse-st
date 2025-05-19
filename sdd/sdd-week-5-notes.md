**WOC7014: Framework-Based Software Design & Development**

**Week 5: The Views - Presentation Layer: Django Templates & Static Files**

*   **Focus:** This week explores the presentation layer in Django, specifically **Django Templates** for dynamically generating HTML, and the management of **Static Files** (CSS, JavaScript, Images) which are essential for rendering the complete user interface. This corresponds to the 'T' (Template) in Django's MVT architecture, which handles the traditional 'View' role of MVC.

**Django Templates**

*   **Definition & Purpose:**
    *   Django templates are text files (typically HTML, but can be XML, CSV, etc.) that serve as a blueprint or **scaffolding for building dynamic web pages.**
    *   They form the backbone of the visual presentation layer of a web application.
    *   **Key Idea: Separation of Presentation from Logic.** Templates allow developers to separate the HTML structure and display logic from the Python code (business logic in Django Views). This makes the codebase cleaner, easier to maintain, and allows frontend designers and backend developers to work more independently.
    *   Templates contain:
        *   **Static Elements:** Parts of the document that remain constant across requests (e.g., standard HTML markup, site branding, headers, footers).
        *   **Dynamic Content Placeholders & Logic:** Special tags and variable placeholders (using Django Template Language - DTL) that are replaced with actual data or processed at runtime by the template engine.

*   **Static Elements Examples in Templates:**
    *   Consistent site-wide headers (e.g., logo, navigation menu) and footers (e.g., copyright notices, contact links).
    *   Standard page layouts (e.g., a two-column layout with a sidebar).
    *   Boilerplate HTML structure (`<html>`, `<head>`, `<body>`).

*   **Core Purpose of Templates in Django:**
    *   **Separate Presentation from Application Logic:** As mentioned, this is a cornerstone of good web development practice and aligns with the MVT pattern. Views (Python code) prepare the data, and templates decide how to display it.
    *   **Promote Reusability & Consistency:**
        *   **Template Inheritance:** A powerful feature allowing you to define a base template (e.g., `base.html`) with common structural elements, and then have other templates "extend" this base and override specific blocks. This drastically reduces redundancy.
        *   **Includes:** Allows you to include one template within another (e.g., `{% include 'partials/navbar.html' %}`), useful for reusable components like navigation bars or sidebars.
    *   **Facilitate Collaboration:** Designers can work on HTML and CSS in templates with minimal Python knowledge, while developers focus on the backend logic.

**Template Configuration in Django**

*   **Template Loaders & `TEMPLATES` Setting:**
    *   Django needs to know where to find your template files. This is configured in the `TEMPLATES` setting in your project's `settings.py`.
    *   The default configuration usually includes `django.template.backends.django.DjangoTemplates` as the backend.
    *   **`APP_DIRS': True`:** This tells Django to look for a `templates` subdirectory inside each installed application (e.g., `my_app/templates/my_app/template.html`). This is good for app-specific templates.
    *   **`DIRS': [os.path.join(BASE_DIR, 'templates')]`:** This tells Django to look for templates in a project-level `templates` directory located at the root of your project. This is useful for templates that are shared across multiple apps or for overriding app templates.

*   **Template Discovery Order:**
    *   Django searches for templates in the directories specified in `DIRS` first.
    *   If `APP_DIRS` is `True`, it then looks in the `templates` subdirectory of each app in `INSTALLED_APPS`.
    *   It uses the first template it finds that matches the requested name. This allows project-level templates in `DIRS` to override app-specific templates if they have the same relative path.
    *   **Best Practice for App Templates:** To avoid naming collisions between apps, create a subdirectory within your app's `templates` folder that has the same name as the app itself (e.g., `my_app/templates/my_app/example.html`). Then, refer to it as `my_app/example.html` in your views.

*   **Configuration Example in `settings.py`:**
    ```python
    import os # Typically at the top of settings.py

    # BASE_DIR is usually defined at the top of settings.py
    # BASE_DIR = Path(__file__).resolve().parent.parent (for newer Django versions)
    # BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__))) (for older versions)

    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
            # DIRS specifies a list of directories where Django should look for templates
            # outside of individual apps.
            'DIRS': [os.path.join(BASE_DIR, 'templates')],
            # APP_DIRS tells Django to look for a 'templates' subdirectory in each
            # installed application.
            'APP_DIRS': True,
            'OPTIONS': {
                # Context processors add variables to the context of all templates.
                'context_processors': [
                    'django.template.context_processors.debug', # Adds debug-related variables like sql_queries.
                    'django.template.context_processors.request', # Adds the current HttpRequest object (request) to the context.
                    'django.contrib.auth.context_processors.auth', # Adds the current user and permissions.
                    'django.contrib.messages.context_processors.messages', # Adds messages from the messages framework.
                ],
                # 'builtins': ['myapp.templatetags.custom_tags'], # Example of loading custom template tags globally
            },
        },
    ]
    ```
    *   **`os.path.join(BASE_DIR, 'templates')`:**
        *   `BASE_DIR`: An absolute path to your Django project's root directory.
        *   `os.path.join()`: A Python function that intelligently joins path components using the correct separator for the current operating system (e.g., `/` on Linux/macOS, `\` on Windows). This ensures cross-platform compatibility.

**Django Template Language (DTL)**

*   **Characteristics:**
    *   DTL is designed to feel comfortable for those used to HTML. It's not a full programming language, intentionally limiting logic to keep presentation separate from business logic.
    *   It includes:
        *   Static HTML structure.
        *   **Variables:** `{{ variable_name }}` - Replaced with the value of the variable passed from the view's context.
            *   Supports dot lookup for accessing attributes of objects or dictionary keys: `{{ user.username }}`, `{{ my_dict.key }}`.
            *   Can also call methods (with no arguments): `{{ user.get_full_name }}`.
        *   **Tags:** `{% tag_name %}` - Provide control flow, inclusion of other templates, loading external resources, etc.
            *   Common tags: `{% if %}`, `{% else %}`, `{% endif %}`, `{% for %}`, `{% endfor %}`, `{% block %}`, `{% endblock %}`, `{% extends %}`, `{% include %}`, `{% url %}`, `{% csrf_token %}`, `{% load %}`.
        *   **Filters:** `{{ variable|filter_name:"argument" }}` - Modify variables for display.
            *   Common filters: `date`, `length`, `lower`, `upper`, `truncatewords`, `default`, `filesizeformat`, `safe` (use with caution, disables auto-escaping).
        *   **Comments:** `{# This is a single-line comment #}` or `{% comment %} This is a multi-line comment {% endcomment %}`.
    *   **Automatic HTML Escaping:** By default, DTL escapes characters like `<`, `>`, `&`, `'`, `"` to prevent Cross-Site Scripting (XSS) attacks when rendering variables. Use the `|safe` filter only if you trust the content and need to render raw HTML.

**Rendering Templates with Context**

*   **The Context:**
    *   A Python dictionary passed from a Django View to the template engine.
    *   Keys in the dictionary become variable names available in the template.
    *   Values are the data to be displayed or used by template tags/filters.
*   **The Rendering Process:**
    1.  **View Prepares Data:** The Django View function (or class-based view method) gathers or computes the necessary data.
    2.  **Context Creation:** This data is packaged into a dictionary (the context).
    3.  **Template Loading:** The view specifies which template file to use. Django's template loaders find this file.
    4.  **Template Engine Processing:** The Django template engine parses the template file.
        *   It replaces `{{ variable }}` placeholders with corresponding values from the context.
        *   It executes `{% tag %}` logic (loops, conditionals, inheritance, etc.).
        *   It applies `|filter` modifications.
    5.  **HTML Generation:** The result is a fully rendered HTML string (or other document type).
    6.  **HTTP Response:** This HTML string is then wrapped in an `HttpResponse` object and sent back to the client's browser.

*   **`render()` Shortcut:** Django provides a convenient shortcut `django.shortcuts.render()` for loading a template, filling a context, and returning an `HttpResponse` object.
    ```python
    from django.shortcuts import render
    from .models import Article # Assuming an Article model

    # views.py
    def article_list_view(request):
        articles = Article.objects.filter(published=True).order_by('-publication_date')
        # The context is a dictionary where keys are variable names in the template.
        context = {
            'page_title': 'Latest Articles',
            'article_list': articles,
            'user_is_authenticated': request.user.is_authenticated,
        }
        # 'myapp/article_list.html' is the path to the template file
        # relative to a templates directory.
        return render(request, 'myapp/article_list.html', context)
    ```

*   **Example Template (`myapp/article_list.html`):**
    ```html
    {% extends "base.html" %} {# Assuming a base.html for common layout #}

    {% block title %}{{ page_title }}{% endblock %}

    {% block content %}
        <h1>{{ page_title }}</h1>

        {% if user_is_authenticated %}
            <p>Welcome back, {{ request.user.username }}!</p>
        {% endif %}

        {% if article_list %}
            <ul>
                {% for article in article_list %}
                    <li>
                        <h2><a href="{% url 'article_detail' article.slug %}">{{ article.headline|upper }}</a></h2>
                        <p>Published on: {{ article.publication_date|date:"F j, Y" }}</p>
                        <p>{{ article.summary|truncatewords:30 }}</p>
                    </li>
                {% endfor %}
            </ul>
        {% else %}
            <p>No articles found.</p>
        {% endif %}

        <p><a href="{% url 'homepage' %}">Back to Home</a></p>
    {% endblock %}
    ```

**Static Files Management (CSS, JavaScript, Images)**

*   **Definition:**
    *   Static files are assets required by your web application's presentation layer that are not dynamically generated by the server for each request.
    *   Examples: CSS stylesheets, JavaScript files, images (logos, icons), web fonts.
*   **Purpose in Django:**
    *   Django provides a mechanism (`django.contrib.staticfiles`) to manage and serve these files during development and to collect them for deployment in production.
    *   It helps decouple static assets from your Python/template code.

*   **Configuration (`settings.py`):**
    *   **`STATIC_URL`:**
        *   The URL prefix for static files when served by the Django development server or when referenced in templates.
        *   Example: `STATIC_URL = '/static/'`
        *   In templates, you'd use `{% static 'myapp/css/style.css' %}` which would render as `/static/myapp/css/style.css`.
    *   **`STATICFILES_DIRS`:**
        *   A list of directories where Django's `staticfiles` app will look for static files *in addition* to the `static` subdirectory of each installed app.
        *   Useful for project-wide static assets that don't belong to a specific app (e.g., a global CSS file, project logo).
        *   Example: `STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static_project_assets')]`
    *   **`STATIC_ROOT`:**
        *   **For Production Only.** The absolute path to the directory where `python manage.py collectstatic` will gather *all* static files from `STATICFILES_DIRS` and from the `static` subdirectories of all installed apps into a single location.
        *   Your production web server (e.g., Nginx, Apache) should be configured to serve files from `STATIC_ROOT`.
        *   **Do not** put your project's static files directly into `STATIC_ROOT` during development. `collectstatic` populates it.
        *   Example: `STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles_production')`
    *   **`STATICFILES_FINDERS`:**
        *   Specifies how Django discovers static files. The defaults are usually sufficient:
            *   `django.contrib.staticfiles.finders.FileSystemFinder`: Finds files in `STATICFILES_DIRS`.
            *   `django.contrib.staticfiles.finders.AppDirectoriesFinder`: Finds files in the `static` subdirectory of each app in `INSTALLED_APPS`.

*   **Serving Static Files:**
    *   **During Development (`DEBUG = True`):**
        *   If `django.contrib.staticfiles` is in `INSTALLED_APPS`, Django's development server (`runserver`) will automatically serve static files found by the finders at the `STATIC_URL`.
    *   **In Production (`DEBUG = False`):**
        *   Django's `runserver` is **not suitable** for serving static files in production due to inefficiency and security risks.
        *   You must run `python manage.py collectstatic`. This copies all static files into the `STATIC_ROOT` directory.
        *   Configure your production web server (e.g., Nginx, Apache, or a CDN) to serve files directly from the `STATIC_ROOT` directory at the `STATIC_URL` path.

*   **Using the `{% static %}` Template Tag:**
    *   To make your static file URLs robust and configurable (respecting `STATIC_URL`), always use the `{% static %}` template tag.
    *   First, load it at the top of your template: `{% load static %}`
    *   Then use it:
        ```html
        {% load static %}
        <link rel="stylesheet" href="{% static 'myapp/css/main.css' %}">
        <img src="{% static 'myapp/images/logo.png' %}" alt="My Logo">
        <script src="{% static 'myapp/js/script.js' %}"></script>
        ```
    *   This ensures that if you change `STATIC_URL` (e.g., for a CDN), your template links will update automatically.

*   **Organizing Static Files:**
    *   **App-specific:** Place them in `my_app/static/my_app/` (e.g., `my_app/static/my_app/css/style.css`). This namespacing prevents conflicts if another app has a `style.css`.
    *   **Project-wide:** Place them in a directory defined in `STATICFILES_DIRS` (e.g., `static_project_assets/css/global.css`).

This covers the core aspects of how Django handles the presentation layer through templates and static files.