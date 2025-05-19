**WOC7014: Framework-Based Software Design & Development**

**Week 4: Models and Database Integration**

*   **Focus:** This week explores fundamental database principles, how Django models are used to define data structures, and the powerful Object-Relational Mapping (ORM) system that Django provides to interact with databases using Python code instead of raw SQL.

**Basic Database Principles**

*   **Purpose of Databases in Applications:**
    *   **Persistent Storage:** To store application data in an organized and durable manner, so it persists beyond the lifecycle of a single application run or user session.
    *   **Structured Data Management:** Typically store data in a structured format (e.g., tables with rows and columns in relational databases) allowing for efficient organization.
    *   **Efficient Data Retrieval & Manipulation:** Provide mechanisms (like query languages, e.g., SQL) to easily search, retrieve, filter, sort, update, and delete data.
    *   **Data Integrity & Consistency:** Enforce rules and constraints (e.g., data types, uniqueness, relationships) to ensure data accuracy and reliability.
    *   **Concurrency Control:** Manage simultaneous access to data from multiple users or processes, preventing data corruption and ensuring consistency (e.g., through locking mechanisms, transactions).
    *   **Data Relationships:** Allow defining and managing relationships between different pieces of data (e.g., a user has many orders, an order contains many products).
    *   **Scalability & Performance:** Modern databases are designed to handle large volumes of data and high transaction rates.

*   **Types of Databases (Brief Overview):**
    *   **Relational Databases (RDBMS):**
        *   **Concept:** Store data in tables (relations) consisting of rows (tuples/records) and columns (attributes). Relationships between tables are defined using primary and foreign keys. SQL (Structured Query Language) is the standard language for interacting with RDBMS.
        *   **Strengths:** Strong consistency (ACID properties - Atomicity, Consistency, Isolation, Durability), well-defined schemas, mature technology, suitable for structured data with clear relationships.
        *   **Examples:** MySQL, PostgreSQL, Microsoft SQL Server, Oracle Database, SQLite (file-based).
    *   **Object-Oriented Databases (OODBMS):**
        *   **Concept:** Store data as objects, similar to objects used in object-oriented programming languages. Allows for direct storage of complex data structures and inheritance.
        *   **Strengths:** Can simplify mapping between application objects and stored data, good for complex, interconnected data.
        *   **Considerations:** Less widespread than RDBMS or NoSQL, ecosystem might be smaller.
        *   **Examples:** Versant Object Database, ObjectDB, GemStone/S.
    *   **NoSQL Databases ("Not Only SQL"):**
        *   **Concept:** A broad category of databases that do not adhere to the traditional relational model. Designed for scalability, flexibility, and performance, often sacrificing some of the strict consistency of RDBMS for availability and partition tolerance (BASE properties - Basically Available, Soft state, Eventual consistency).
        *   **Types & Strengths:**
            *   **Document Databases (e.g., MongoDB, CouchDB):** Store data in flexible, semi-structured documents (often JSON or BSON). Good for evolving schemas and hierarchical data.
            *   **Key-Value Stores (e.g., Redis, Amazon DynamoDB Key-Value):** Store data as simple key-value pairs. Extremely fast for lookups, often used for caching and session management.
            *   **Column-Family Stores (e.g., Apache Cassandra, HBase):** Store data in columns rather than rows. Optimized for high write throughput and querying large datasets by column.
            *   **Graph Databases (e.g., Neo4j, Amazon Neptune):** Store data as nodes and edges, optimized for representing and querying complex relationships. Excellent for social networks, recommendation engines.
        *   **Considerations:** Data modeling can be different, consistency models vary, choose based on specific use case needs.

*   **Key Concepts in Relational Databases (Most relevant for typical Django usage):**
    *   **Schema:** The logical structure of the database, including tables, columns, data types, relationships, and constraints.
    *   **Table:** A collection of related data entries organized in rows and columns. (e.g., `Users` table, `Products` table).
    *   **Record/Row (Tuple):** A single entry in a table, representing a specific instance of an entity (e.g., one specific user, one specific product).
    *   **Field/Column (Attribute):** A specific piece of information within a record (e.g., `username` column in the `Users` table, `price` column in the `Products` table). Each column has a defined data type (e.g., `VARCHAR`, `INTEGER`, `DATE`).
    *   **Primary Key (PK):**
        *   A column (or set of columns) whose value uniquely identifies each row in a table.
        *   **Properties:** Must be unique, cannot be NULL (empty).
        *   **Purpose:** Essential for linking tables and ensuring data integrity. Django automatically creates an `id` primary key for models unless specified otherwise.
    *   **Foreign Key (FK):**
        *   A column (or set of columns) in one table that references the primary key of another table.
        *   **Purpose:** Establishes and enforces a link (relationship) between the data in two tables. (e.g., an `order_id` in an `OrderItems` table referencing the `id` in an `Orders` table).
    *   **Constraints:**
        *   Rules applied to columns to ensure data integrity and accuracy.
        *   **Examples:**
            *   `NOT NULL`: Ensures a column cannot have a NULL value.
            *   `UNIQUE`: Ensures all values in a column (or set of columns) are unique.
            *   `CHECK`: Ensures values meet a specific condition (e.g., `price > 0`).
            *   `DEFAULT`: Specifies a default value for a column if no value is provided.
    *   **Indexes:**
        *   Special lookup tables that the database search engine can use to speed up data retrieval operations (queries).
        *   Created on columns that are frequently used in `WHERE` clauses or `JOIN` conditions.
        *   **Trade-off:** Improve query speed but can slow down data insertion, update, and deletion operations as indexes also need to be updated.
    *   **Transactions (ACID properties):**
        *   A sequence of one or more database operations (e.g., reads, writes, updates) that are treated as a single, atomic unit of work.
        *   **Atomicity:** All operations in a transaction either complete successfully, or if any operation fails, the entire transaction is rolled back, leaving the database in its original state.
        *   **Consistency:** A transaction brings the database from one valid state to another.
        *   **Isolation:** Concurrent transactions produce the same result as if they were executed serially (one after another).
        *   **Durability:** Once a transaction is committed, its changes are permanent and survive system failures.
        *   Django's ORM supports database transactions.

**Django Models (`models.py`)**

*   **Purpose:**
    *   A Django model is the single, definitive source of information about your data. It contains the essential fields and behaviors of the data you’re storing.
    *   Each model maps to a single database table (by default).
    *   Provides an object-oriented way to define your database schema in Python code.
    *   Enables CRUD (Create, Read, Update, Delete) operations on database records using Python objects and methods.

*   **Defining a Model:**
    *   Models are defined as Python classes that inherit from `django.db.models.Model`.
    *   Each attribute of the model class represents a database field (column).
    *   Django uses these model definitions to generate the database schema (e.g., `CREATE TABLE` statements) via migrations.

*   **Example Django Model:**
    ```python
    from django.db import models
    from django.utils import timezone # For default values or auto_now_add

    class Genre(models.Model):
        name = models.CharField(max_length=50, unique=True)

        def __str__(self): # Important for human-readable representation
            return self.name

    class Game(models.Model):
        title = models.CharField(max_length=100, db_index=True) # db_index=True creates a database index on this field
        # genre is a ForeignKey, establishing a one-to-many relationship
        # One Genre can have many Games.
        # on_delete=models.CASCADE means if a Genre is deleted, all Games associated with it are also deleted.
        genre = models.ForeignKey(Genre, on_delete=models.CASCADE, related_name='games')
        release_date = models.DateField(null=True, blank=True) # null=True allows NULL in DB, blank=True allows empty in forms
        platform = models.CharField(max_length=50, choices=[('PC', 'PC'), ('PS5', 'PlayStation 5'), ('XBOX', 'Xbox Series X/S')])
        description = models.TextField(blank=True) # For longer text, blank=True means it's not required in forms
        created_at = models.DateTimeField(auto_now_add=True) # Automatically set to now when object is first created
        updated_at = models.DateTimeField(auto_now=True)     # Automatically set to now every time the object is saved

        class Meta: # Inner class for model metadata
            ordering = ['-release_date', 'title'] # Default ordering for querysets
            verbose_name = "Video Game"
            verbose_name_plural = "Video Games"
            # unique_together = (('title', 'platform'),) # Example: Ensures no two games have the same title on the same platform

        def __str__(self):
            return f"{self.title} ({self.platform})"

        def was_released_recently(self):
            now = timezone.now().date()
            return now - timezone.timedelta(days=30) <= self.release_date <= now
    ```

*   **Common Field Types (subset):**
    *   `CharField(max_length, ...)`: For short to medium length strings (e.g., names, titles). `max_length` is required.
    *   `TextField(...)`: For large blocks of text (e.g., descriptions, articles). No `max_length` (though database may have practical limits).
    *   `IntegerField(...)`: For integers.
    *   `FloatField(...)`: For floating-point numbers.
    *   `DecimalField(max_digits, decimal_places, ...)`: For fixed-precision decimal numbers (e.g., currency).
    *   `DateField(auto_now=False, auto_now_add=False, ...)`: For dates.
        *   `auto_now`: Automatically set the field to now every time the object is saved. Useful for "last-modified" timestamps.
        *   `auto_now_add`: Automatically set the field to now when the object is first created. Useful for "created" timestamps.
    *   `DateTimeField(...)`: For dates and times.
    *   `BooleanField(...)`: For true/false values. Defaults to `None` unless `default` is specified. Use `NullBooleanField` if you need to store `NULL` explicitly.
    *   `EmailField(...)`: A `CharField` that checks if the value is a valid email address using `EmailValidator`.
    *   `URLField(...)`: A `CharField` that checks for a valid URL using `URLValidator`.
    *   `FileField(upload_to='', ...)`: For file uploads.
    *   `ImageField(upload_to='', height_field=None, width_field=None, ...)`: Inherits from `FileField` with validation for image content.
    *   `UUIDField(...)`: For universally unique identifiers.
    *   **Relationship Fields:** `ForeignKey`, `ManyToManyField`, `OneToOneField`.

*   **Field Options (Common):**
    *   `null` (boolean): If `True`, Django will store empty values as `NULL` in the database. Default is `False`.
    *   `blank` (boolean): If `True`, the field is allowed to be blank in forms. Default is `False`. This is a validation-related option, distinct from `null` (database storage).
    *   `choices` (iterable): An iterable (e.g., list of tuples) to provide choices for this field. Django admin and some form widgets will use these.
    *   `default` (value): The default value for the field. Can be a value or a callable object.
    *   `unique` (boolean): If `True`, this field must be unique throughout the table.
    *   `db_index` (boolean): If `True`, a database index will be created for this field.
    *   `primary_key` (boolean): If `True`, sets this field as the primary key for the model. Django automatically adds an `id` AutoField as PK if not specified.
    *   `editable` (boolean): If `False`, the field will not be displayed in the admin or any other `ModelForm`.
    *   `help_text` (string): Extra "help" text to be displayed with the form widget.
    *   `verbose_name` (string): A human-readable name for the field.

*   **Model `Meta` Options (Inner class):**
    *   Provides metadata for the model.
    *   `ordering`: Default ordering for querysets for this model.
    *   `verbose_name`, `verbose_name_plural`: Human-readable names for the model in singular and plural forms (used in Django admin).
    *   `db_table`: Specifies the exact database table name to use (default is `appname_modelname`).
    *   `unique_together`: A tuple of tuples of field names that must be unique together.
    *   `indexes`: A list of `models.Index` instances for creating database indexes (more flexible than `db_index` on fields).
    *   `permissions`, `default_permissions`: For custom model permissions.
    *   `abstract`: If `True`, this model will be an abstract base class (no DB table created, used for common fields in other models).
    *   `managed`: If `False`, Django will not create/delete DB table for this model during migrations (e.g., for mapping to existing tables).

*   **Model Methods:**
    *   You can define custom methods on your model classes to add business logic or utility functions related to the model's data (e.g., `was_released_recently()` in the example).
    *   The `__str__()` method is particularly important: it should return a human-readable string representation of the object, used in Django admin and when an object is displayed.

**Relationships in Models**

Django provides fields to define the three main types of database relationships:

*   **`ForeignKey` (One-to-Many / Many-to-One):**
    *   **Concept:** Links one record in the "many" side table to exactly one record in the "one" side table. (e.g., A `Game` has one `Genre`, but a `Genre` can have many `Games`).
    *   **Definition:** Defined on the "many" side (e.g., on `Game` model pointing to `Genre`).
    *   **Key Arguments:**
        *   `to`: The model class the relationship is with.
        *   `on_delete`: Specifies what happens when the referenced object is deleted. Crucial for data integrity.
            *   `models.CASCADE`: Deletes the object containing the ForeignKey (e.g., delete the `Game` if its `Genre` is deleted).
            *   `models.PROTECT`: Prevents deletion of the referenced object if there are still objects pointing to it.
            *   `models.SET_NULL` (requires `null=True` on the field): Sets the ForeignKey to `NULL`.
            *   `models.SET_DEFAULT` (requires `default` to be set): Sets the ForeignKey to its default value.
            *   `models.SET()`: Sets to a given value or result of a callable.
            *   `models.DO_NOTHING`: Potentially dangerous, can lead to database integrity errors if not handled carefully.
        *   `related_name`: The name to use for the reverse relation from the "one" side back to the "many" side (e.g., `genre_instance.games.all()`). If not specified, Django creates `_set` (e.g., `genre_instance.game_set.all()`).
        *   `limit_choices_to`: Limits choices for this field when rendered in forms or admin.
*   **`ManyToManyField` (Many-to-Many):**
    *   **Concept:** Links multiple records in one table to multiple records in another table. (e.g., An `Article` can have many `Tags`, and a `Tag` can be applied to many `Articles`).
    *   **Implementation:** Django automatically creates an intermediary "join" table in the database to manage this relationship.
    *   **Definition:** Can be defined on either side of the relationship.
    *   **Key Arguments:**
        *   `to`: The model class the relationship is with.
        *   `related_name`: For reverse access.
        *   `through`: Specifies a custom intermediate model if you need to store extra data on the relationship itself (e.g., the date a tag was added to an article).
        *   `symmetrical`: Only relevant for `ManyToManyField`s that point to `self`. If `True` (default), the relationship is considered symmetrical (if A is related to B, B is related to A). If `False`, it's not.
    ```python
    # Example ManyToManyField
    class Tag(models.Model):
        name = models.CharField(max_length=50, unique=True)
        def __str__(self): return self.name

    class Article(models.Model):
        headline = models.CharField(max_length=200)
        tags = models.ManyToManyField(Tag, related_name='articles', blank=True)
        # Access: article.tags.all(), tag.articles.all()
        def __str__(self): return self.headline
    ```
*   **`OneToOneField` (One-to-One):**
    *   **Concept:** Links one record in a table to exactly one record in another table. It's like a `ForeignKey` with a `unique=True` constraint, but also implies a primary key-like relationship. (e.g., A `UserProfile` might have a one-to-one relationship with Django's built-in `User` model, extending it with extra profile information).
    *   **Definition:** Can be defined on either side, but typically on the "extension" model.
    *   **Key Arguments:**
        *   `to`: The model class the relationship is with.
        *   `on_delete`: Same as `ForeignKey`.
        *   `parent_link`: If `True` and this model inherits from another non-abstract model, this field becomes the link to the parent class (effectively making it a form of inheritance).
    ```python
    # Example OneToOneField
    from django.contrib.auth.models import User

    class UserProfile(models.Model):
        user = models.OneToOneField(User, on_delete=models.CASCADE, primary_key=True, related_name='profile')
        bio = models.TextField(blank=True)
        profile_picture_url = models.URLField(blank=True)
        # Access: user.profile, userprofile.user
        def __str__(self): return self.user.username
    ```

**Django ORM (Object-Relational Mapping)**

*   **Purpose:**
    *   An ORM is a programming technique that provides an abstraction layer between object-oriented code (Python, in Django's case) and a relational database.
    *   **Goal:** Allows developers to interact with the database using familiar Python objects and methods instead of writing raw SQL queries.
    *   Django's ORM translates these Python operations into SQL queries behind the scenes.

*   **Benefits:**
    *   **Increased Productivity:** Write database interaction code faster using Python, rather than context-switching to SQL.
    *   **Database Agnosticism (to a degree):** Django's ORM supports multiple database backends (PostgreSQL, MySQL, SQLite, Oracle). You can often switch databases with minimal code changes (though complex queries or database-specific features might need adjustments).
    *   **Automatic SQL Generation:** The ORM handles the creation of SQL queries, reducing the likelihood of syntax errors and boilerplate.
    *   **Security:** Helps protect against SQL injection vulnerabilities because queries are constructed programmatically, and parameters are typically escaped correctly.
    *   **Simplified Data Manipulation:** CRUD operations become intuitive method calls on Python objects.
    *   **Abstraction of Database Complexities:** Hides many of the low-level details of database interaction.
    *   **Integration with Migrations:** Model definitions drive the database migration system.

*   **How it Works (Conceptual):**
    1.  **Define Models:** You create Django model classes.
    2.  **Migrations:** `makemigrations` inspects your models and creates migration files (Python code describing schema changes). `migrate` applies these changes to the database, creating/altering tables.
    3.  **Querying:** You use the model's manager (e.g., `Game.objects`) to construct queries using Python methods (`filter()`, `get()`, `exclude()`, `annotate()`, etc.).
    4.  **SQL Generation:** The ORM translates these Python query constructions into SQL statements.
    5.  **Execution:** The SQL is executed against the configured database.
    6.  **Results to Objects:** The database results (rows) are converted back into instances of your Django model classes (Python objects).

*   **Basic ORM Operations (QuerySet API):**
    *   **Managers:** Each Django model has at least one `Manager` (by default, named `objects`). It's the main source of `QuerySet`s.
        *   `Game.objects.all()`: Retrieves all `Game` objects.
    *   **Creating Objects:**
        ```python
        new_genre = Genre.objects.create(name='Adventure')
        new_game = Game(title='Uncharted', genre=new_genre, release_date='2007-11-19', platform='PS5')
        new_game.save()
        ```
    *   **Retrieving Objects:**
        *   `Game.objects.all()`: Returns a `QuerySet` of all games.
        *   `Game.objects.get(id=1)` or `Game.objects.get(title__exact="Uncharted")`: Retrieves a single object. Raises `DoesNotExist` if no object found or `MultipleObjectsReturned` if more than one found.
        *   `Game.objects.filter(platform='PC')`: Returns a `QuerySet` of PC games.
        *   `Game.objects.filter(release_date__year=2020)`: Games released in 2020.
        *   `Game.objects.exclude(genre__name='Sports')`: All games not in the 'Sports' genre.
    *   **Field Lookups (for `filter`, `exclude`, `get`):**
        *   `exact`, `iexact` (case-insensitive)
        *   `contains`, `icontains`
        *   `startswith`, `istartswith`, `endswith`, `iendswith`
        *   `in`: `Game.objects.filter(id__in=[1, 2, 3])`
        *   `gt`, `gte`, `lt`, `lte` (greater/less than or equal to)
        *   `year`, `month`, `day` (for DateFields/DateTimeFields)
        *   `isnull`
    *   **Updating Objects:**
        ```python
        game = Game.objects.get(id=1)
        game.title = 'Updated Title'
        game.save()
        # Bulk update
        Game.objects.filter(platform='PC').update(description='Now available on PC!')
        ```
    *   **Deleting Objects:**
        ```python
        game = Game.objects.get(id=1)
        game.delete()
        # Bulk delete
        Game.objects.filter(release_date__year__lt=2000).delete()
        ```
    *   **QuerySets are Lazy:**
        *   Creating a `QuerySet` (e.g., `Game.objects.filter(platform='PC')`) doesn't hit the database immediately.
        *   The database is queried only when the `QuerySet` is *evaluated* (e.g., by iterating over it, slicing it, calling `len()`, `list()`, or `get()`). This allows for chaining filters efficiently.
    *   **Chaining Filters:** `Game.objects.filter(platform='PC').filter(release_date__year__gt=2020)`
    *   **Ordering:** `Game.objects.order_by('title')` or `Game.objects.order_by('-release_date')` (descending).
    *   **Slicing:** `Game.objects.all()[:5]` (gets first 5 games, translates to `LIMIT` in SQL).

**Advanced ORM Techniques (Brief Mention - from your original notes)**

*   **`Q` Objects:** For complex queries involving `OR` conditions.
    ```python
    from django.db.models import Q
    # Games that are RPG OR Strategy
    Game.objects.filter(Q(genre__name='RPG') | Q(genre__name='Strategy'))
    # Games that are RPG AND released after 2019
    Game.objects.filter(Q(genre__name='RPG') & Q(release_date__year__gt=2019))
    ```
*   **`F` Expressions:** To refer to model field values directly in database operations, avoiding pulling data into Python memory. Useful for atomic updates or comparisons between fields.
    ```python
    from django.db.models import F
    # Example: Increase price of all games by 10 (hypothetical 'price' field)
    # Game.objects.all().update(price=F('price') * 1.1)
    # Example: Find games where number_of_players > required_players (hypothetical fields)
    # Game.objects.filter(number_of_players__gt=F('required_players'))
    ```
*   **Annotations (`annotate`) and Aggregations (`aggregate`):**
    *   `annotate()`: To add calculated fields to each object in a `QuerySet` (e.g., count of related objects).
    *   `aggregate()`: To calculate summary values over an entire `QuerySet` (e.g., average price, total count).
    ```python
    from django.db.models import Count, Avg
    # Annotate each genre with the number of games
    genres_with_counts = Genre.objects.annotate(num_games=Count('games'))
    # for genre in genres_with_counts: print(genre.name, genre.num_games)

    # Aggregate: Get the average release year (hypothetical, needs careful thought on DateField aggregation)
    # average_year = Game.objects.aggregate(avg_year=Avg('release_date__year'))
    ```
*   **Window Functions (`Window`):** (More advanced, for calculations over a "window" or partition of rows related to the current row).
    *   The `Rank` function in your example is a window function. It assigns a rank to each game based on its release date.
    ```python
    from django.db.models import Window, F
    from django.db.models.functions import Rank

    queryset = Game.objects.annotate(
        rank_by_release=Window(
            expression=Rank(),
            order_by=F('release_date').asc() # Rank oldest first
        )
    ).filter(
        Q(genre__name='RPG') | Q(genre__name='Strategy'),
        release_date__year__gte=2020
    )
    # for game in queryset: print(game.title, game.release_date, game.rank_by_release)
    ```
*   **Subqueries (`Subquery`, `Exists`):** For embedding SQL subqueries within an ORM query.
*   **Transactions (`django.db.transaction.atomic`):** To ensure a block of database operations either all succeed or all fail together.
    ```python
    from django.db import transaction

    try:
        with transaction.atomic():
            # ... multiple database operations ...
            # game1.save()
            # order.update_status()
            pass # If all successful, transaction is committed
    except IntegrityError:
        # Handle error, transaction is rolled back
        pass
    ```

This gives a more solid understanding of how Django models interact with databases via the ORM.