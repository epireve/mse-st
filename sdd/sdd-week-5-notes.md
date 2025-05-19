**WOC7014: Framework-Based Software Design & Development - Expanded Study Notes**

**Week 5: The Views**

*   **Focus:** This week explores Django templates and static files, essential components for rendering the user interface.

**Django Templates**

*   **Definition:**
    *   Templates serve as scaffolding for building HTML webpages
    *   They form the backbone of the visual presentation
    *   Contain static elements (that never change) and special tags for dynamic content

*   **Static Elements Examples:**
    *   Headers (banners) and footers (footnotes or copyright notices)
    *   Consistent page layouts

*   **Purpose:**
    *   Separate presentation (look and feel) from application logic (code and business logic)
    *   Promote consistency across the application

**Template Configuration**

*   **Storage Options:**
    *   Create a template folder in each Django app (useful when apps have their own templates)
    *   Create a "templates" subfolder under the project folder for consistent look and feel across apps
    *   Optionally create subfolders within templates for each app

*   **Configuration in settings.py:**
    ```python
    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
            'DIRS': [os.path.join(BASE_DIR, 'templates')],  # Tell Django where templates are stored
            'APP_DIRS': True,
            'OPTIONS': {
                'context_processors': [
                    'django.template.context_processors.debug',
                    'django.template.context_processors.request',
                    'django.contrib.auth.context_processors.auth',
                    'django.contrib.messages.context_processors.messages',
                ],
            },
        },
    ]
    ```

*   **Path Configuration:**
    *   Define the path after BASE_DIR
    *   BASE_DIR stores the absolute path from the drive to the base project directory
    *   Use os.path.join() to ensure path safety across different operating systems

**Django Template Language**

*   **Characteristics:**
    *   HTML file enhanced with Django's templating language
    *   Includes static HTML structure
    *   Uses dynamic placeholders with {{ variable }} syntax
    *   Promotes separation of concerns between UI and business logic

**Rendering with Context**

*   **Process:**
    *   Views prepare data in a dictionary (context)
    *   Template engine replaces variables with actual values
    *   Resulting HTML is sent to the client

*   **Example:**
    ```python
    # views.py
    def example_view(request):
        context = {
            'title': 'My Page',
            'items': ['Item 1', 'Item 2', 'Item 3']
        }
        return render(request, 'example.html', context)
    ```

    ```html
    <!-- example.html -->
    <h1>{{ title }}</h1>
    <ul>
        {% for item in items %}
            <li>{{ item }}</li>
        {% endfor %}
    </ul>
    ```