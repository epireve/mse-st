**WOC7014: Framework-Based Software Design & Development - Expanded Study Notes**

**Week 4: Models and Database**

*   **Focus:** This week covers database principles, Django models, and the Object-Relational Mapping (ORM) system.

**Basic Database Principles**

*   **Purpose of Databases:**
    *   Store structured data (rows and columns)
    *   Enable easy retrieval and updates
    *   Support relationships between data

*   **Types of Databases:**
    *   **Relational:** MySQL, PostgreSQL, Microsoft SQL Server
    *   **Object-Oriented:** Versant Object Database, ObjectDB
    *   **NoSQL:** MongoDB, Redis, Neo4j

*   **Key Concepts in Databases:**
    *   **Primary Key:** Unique identifier for each record
    *   **Foreign Key:** Links between tables, establishes relationships
    *   **Constraints:** Rules that enforce data integrity (e.g., Not Null, Unique)

**Django Models**

*   **Purpose:**
    *   Define data structure in Python
    *   Map to database tables
    *   Support CRUD operations (Create, Read, Update, Delete)

*   **Example Django Model:**
    ```python
    class Game(models.Model):
        title = models.CharField(max_length=100)
        genre = models.CharField(max_length=50)
        release_date = models.DateField()
    ```

*   **Field Types:**
    *   CharField: For text with a maximum length
    *   TextField: For unlimited text
    *   IntegerField: For integers
    *   DateField: For dates
    *   Many others for specific data types

**Relationships in Models**

*   **Types of Relationships:**
    *   **One-to-One:** One record in table A relates to exactly one record in table B
    *   **One-to-Many:** One record in table A relates to multiple records in table B
    *   **Many-to-Many:** Multiple records in table A relate to multiple records in table B

*   **Implementing Relationships:**
    *   OneToOneField: For one-to-one relationships
    *   ForeignKey: For one-to-many relationships
    *   ManyToManyField: For many-to-many relationships

**Django ORM (Object-Relational Mapping)**

*   **Purpose:**
    *   Abstract database operations
    *   Allow database interactions using Python code instead of SQL
    *   Provide a consistent API regardless of the underlying database

*   **Benefits:**
    *   Database-agnostic code
    *   Automatic SQL generation
    *   Protection against SQL injection
    *   Simplified data manipulation

**Advanced ORM Techniques:**
```python
# Complex Query Example
from django.db.models import Q, F, Window
from django.db.models.functions import Rank

queryset = Game.objects.annotate(
    rank=Window(
        expression=Rank(),
        order_by=F('release_date').asc()
    )
).filter(
    Q(genre='RPG') | Q(genre='Strategy'),
    release_date__year__gte=2020
)