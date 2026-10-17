# Spring Boot MongoDB NoSQL CRUD

Spring Boot MongoDB NoSQL CRUD is a small REST API project that demonstrates how to build CRUD (Create, Read, Update, Delete) operations using Spring Boot and Spring Data MongoDB. The project provides endpoints to manage Employees and Projects stored in a MongoDB database, includes a sequence generator for document IDs, and is integrated with Swagger for API documentation.

## Features
- Spring Boot application (Java 11)
- Spring Data MongoDB repositories
- REST controllers for Employees and Projects
- Sequence generator service for unique IDs
- Swagger (Springfox) configuration for API docs

## Quick start
Prerequisites:
- Java 11+
- Gradle (optional — the repo contains the Gradle wrapper)
- MongoDB running locally or accessible remotely

1. Clone the repository:

   git clone https://github.com/ravichan18/springboot-mongodb-nosql-crud.git
   cd springboot-mongodb-nosql-crud

2. Configure MongoDB connection (recommended: use environment variables or external config):

   Edit `src/main/resources/application.properties` or set environment variables for the following properties:

   - spring.data.mongodb.host (default: localhost)
   - spring.data.mongodb.port (default: 27017)
   - spring.data.mongodb.database (example: crud2employee)
   - spring.data.mongodb.username
   - spring.data.mongodb.password

   Note: The repository currently contains sample credentials in application.properties. Remove or replace them before publishing or deploying.

3. Build and run the application:

   Unix/macOS: `./gradlew clean bootRun`
   Windows: `gradlew.bat clean bootRun`

4. API docs (Swagger):

   Once running, Swagger UI is available (default) at:
   `http://localhost:8080/swagger-ui.html` (depending on your Spring Boot config)

## Project structure
- src/main/java/com/urunov/mongodb
  - controller — REST controllers (EmployeeController, ProjectController)
  - model — domain models (Employees, Projects, DatabaseSequence)
  - repository — Spring Data MongoDB repositories (MongoDB, ProjectsDB)
  - service — SequenceGeneratorService
  - configSwag — Swagger configuration
- src/main/resources — application.properties, schema.script

## Notes & recommendations
- Security: Do not keep plaintext credentials in repository. Use environment variables, Spring Cloud Config, or GitHub Secrets for CI.
- ProjectsDB repository: the repository code imports the MongoDB client directly and declares the repository generics; review and adjust the repository generic type if needed (it typically should be `MongoRepository<Projects, String>`).
- The Gradle wrapper binary was excluded from the initial import; if you need it, add it back or use Gradle installed on your machine.

## License
This repository doesn't include a license file by default. Add a LICENSE if you plan to share or change the license terms.

## Reference
- CRUD tutorial: https://www.javaguides.net/2019/12/spring-boot-mongodb-crud-example-tutorial.html
