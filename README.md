# Sekwate Backend

## Migrations

Migrations are managed using liquibase. Follow the steps for migrating any database changes.

### Prerequisites

- `liquibase.properties` filled up
- `secret.properties` filled up

1. Create/update your entities via hibernate
2. Run `mvn clean compile` to generate the classes to the target folder.
3. Run `mvn liquibase:diff` to generate the changelog in `resources/db/changelog/migrations`.
4. Rename the generated changelog file to something meaningful. Set naming convention should be `{number}_{your_migration_file_name}.yaml` (e.g. `01_initial_migration.yaml`).
5. Run `mvn clean compile` to generate the migration files to the target folder.
6. Run `mvn liquibase:update` to run the migration.

Running the Spring Boot app will never migrate the database changes automatically!
