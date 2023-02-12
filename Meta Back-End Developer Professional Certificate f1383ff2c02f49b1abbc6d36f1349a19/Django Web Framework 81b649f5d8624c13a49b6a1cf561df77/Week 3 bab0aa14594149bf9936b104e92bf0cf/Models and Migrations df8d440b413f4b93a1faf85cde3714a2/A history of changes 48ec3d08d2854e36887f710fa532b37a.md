# A history of changes

# ****What are Migrations in Django?****

- Migrations are a way for Django to keep track of changes made to the database schema.
- They allow developers to apply changes to the database without writing SQL commands.
- Migrations are tied to models and stored as migration files in a Migrations folder inside each app.
- They provide a history of changes to the codebase and are useful for version control.
- Migrations help to avoid repetition and ensure schema changes are applied to multiple databases.

# ****How Migrations Work in Django****

- To make a change to a model, the developer must create the change directly in the model then apply the migration using migration scripts.
- Migration files are stored in a migration folder and are automatically updated after a migration has run.
- The **`show migrations`** command can be used to explore the details of migrations and the **`migrate`** command is used to apply migrations.
- Django creates a new table called Django migrations to keep track of all changes made to the database.
- Each migration file contains two important sequences: dependencies and operations.