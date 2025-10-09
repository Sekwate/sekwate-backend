# Sekwate Backend

A Java Spring REST backend for an ecommerce app.

## Requirements

- Java 17
- Postgresql 18

## Environment Variables

All variables are set in two properties file at `src/main/resources`. There are `sample` properties file in the folder that you can rename without the `sample.` (e.g. `sample.liquibase.properties` to `liquibase.properties`).

There will be comments in the file what values to replace. Make sure to fill in/replace the values before attempting to run the application or a command.

## Folder Structure

This project will use per module hierarchy of folders. Each module will have:

- `controllers` - For the controller classes
- `dto` - For the Data transfer objects
- `entities` - For the entity/model classes
- `repositories` - For the repository interface/classes
- `services` - For the service classes
- `utilities` - For the module level utilities

There will be a special module called `common` where the above folders will be optional and can have additional folders to house more classes that can be used to each module or for the whole application.

```
.
└── com/sekwate/backend/
    ├── common/
    │   └── config
    ├── module1/
    │   ├── controllers
    │   ├── dto
    │   ├── entities
    │   ├── repositories
    │   ├── services
    │   └── utilities
    ├── module2
    └── BackendApplication.java
```

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
