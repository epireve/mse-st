**WOC7014: Framework-Based Software Design & Development - Expanded Study Notes**

**Week 6: The Form and The Controller**

*   **Focus:** This week covers HTML forms in Django and the controller aspect of the MVC architecture.

**Part 1: HTML Forms**

*   **HTML Forms - Definition:**
    *   Represented by `<form>...</form>` tags
    *   Contain UI widgets/elements that interact with users to gather information
    *   Allow users to enter text, select options, manipulate objects or controls
    *   Send collected information to other pages, back to server, or store in database

*   **HTML Forms - UI Types:**
    *   **Built-in HTML components:**
        *   Text input: `<input type="text">`
        *   Checkboxes: `<input type="checkbox">`
    *   **More complex components:**
        *   Date pickers, color sliders
        *   Typically use JavaScript and CSS with built-in HTML components

*   **HTML `<input>` Tag:**
    *   Specifies an input field where users can enter data
    *   Various types: button, checkbox, color, date, email, file, password, radio, etc.
    *   Includes attributes for customization: min, max, name, pattern, required, width, etc.
    *   Supported by most internet browsers

*   **HTML Form Requirements:**
    *   Must specify **where**: the URL to return data to (action attribute)
    *   Must specify **how**: the HTTP method to use (method attribute)

*   **Example - Django Login Form:**
    *   Contains three visible `<input>` elements:
        *   `<input type="text">` for username
        *   `<input type="password">` for password
        *   `<input type="submit">` for the "Log in" button
    *   Form data sent to URL specified in action attribute (e.g., /admin/)
    *   Uses HTTP method specified in method attribute (e.g., post)

**Part 2: GET and POST Methods**

*   **GET Method:**
    *   Appends form data to the URL as query parameters
    *   Visible in the browser address bar
    *   Limited amount of data can be sent (URL length restrictions)
    *   Suitable for non-sensitive data and search forms
    *   Bookmarkable and can be shared

*   **POST Method:**
    *   Sends form data in the HTTP request body
    *   Not visible in the URL
    *   Can send large amounts of data
    *   More secure for sensitive information
    *   Not bookmarkable or shareable via URL
    *   Requires CSRF protection in Django

**Part 3: The Controller**

*   **Re-interpretation of Django MTV:**
    *   **View in Django:** Determines *which* data is presented (Python callback function for a URL)
    *   **Template:** Defines *how* the data looks (delegated from View)
    *   **Controller:** The framework itself, machinery that routes requests to appropriate Views
    *   **Model:** Defines how data is stored
    *   The functionality matters more than the naming convention

*   **Django Design Philosophies:**
    *   **Loose coupling and tight cohesion:**
        *   Coupling: relationship between modules
        *   Cohesion: relationship within modules
        *   Layers should not know about each other unless necessary
    *   **Less code:** Minimize boilerplate and standardization text
    *   **Quick development:** Rapid application development
    *   **Don't Repeat Yourself (DRY):** Avoid redundancy, promote normalization
    *   **Explicit is better than implicit:** Less magic, less confusion
    *   **Consistency:** At all levels, from code to user experience

*   **Controller Implementation in Django:**
    *   Django's URL dispatcher acts as the controller
    *   Maps URL patterns to view functions
    *   Handles request processing and response generation
    *   Manages middleware execution