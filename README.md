# Employee Directory Spring Boot REST API

A simple Employee Directory REST API built with Spring Boot, Spring Data JPA, Spring Data REST, PostgreSQL, and Swagger/OpenAPI. The project exposes CRUD operations for managing employee records through repository-backed REST endpoints.

## Features

* Employee CRUD API
* Spring Boot REST backend
* Spring Data JPA persistence
* Spring Data REST repository endpoints
* PostgreSQL database integration
* Swagger/OpenAPI UI for API exploration
* Java 21 support
* Maven-based build workflow

## Tech Stack

* Java 21
* Spring Boot 3.5
* Spring Web
* Spring Data JPA
* Spring Data REST
* PostgreSQL
* Springdoc OpenAPI
* Maven

## Project Structure

```text
EmployeeDirectorySpringBootRestAPI/
├── src/
│   ├── main/
│   │   ├── java/com/joeljebitto/employeeCRUD/
│   │   │   ├── EmployeeCrudApplication.java
│   │   │   ├── dao/
│   │   │   │   └── EmployeeRepository.java
│   │   │   └── entity/
│   │   │       └── Employee.java
│   │   └── resources/
│   │       └── application.properties
├── pom.xml
└── README.md
```

## Employee Model

The API manages employee records with the following fields:

```text
id          integer, auto-generated primary key
firstName   employee first name
lastName    employee last name
email       employee email address
```

The entity is mapped to the database table:

```text
employee
```

## API Overview

Spring Data REST exposes repository-backed endpoints under:

```text
/api
```

Typical employee endpoints:

| Method   | Endpoint              | Description               |
| -------- | --------------------- | ------------------------- |
| `GET`    | `/api/employees`      | List employees            |
| `GET`    | `/api/employees/{id}` | Get employee by ID        |
| `POST`   | `/api/employees`      | Create employee           |
| `PUT`    | `/api/employees/{id}` | Replace employee          |
| `PATCH`  | `/api/employees/{id}` | Partially update employee |
| `DELETE` | `/api/employees/{id}` | Delete employee           |

Example request body:

```json
{
  "firstName": "Joel",
  "lastName": "Jebitto",
  "email": "joel@example.com"
}
```

## Swagger UI

Swagger/OpenAPI UI is configured at:

```text
http://localhost:8080/
```

Use it to inspect and test the available API endpoints.

## Prerequisites

* Java 21
* Maven
* PostgreSQL

## Database Setup

Create a PostgreSQL database:

```sql
CREATE DATABASE employee_directory;
```

Update the database credentials in:

```text
src/main/resources/application.properties
```

Example local configuration:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/employee_directory
spring.datasource.username=postgres
spring.datasource.password=your_password

spring.data.rest.base-path=/api
spring.data.rest.default-page-size=20

springdoc.swagger-ui.path=/
```

## Running the Application

Clone the repository:

```bash
git clone https://github.com/joeljebitto-dev/EmployeeDirectorySpringBootRestAPI.git
cd EmployeeDirectorySpringBootRestAPI
```

Run the app with Maven:

```bash
./mvnw spring-boot:run
```

On Windows:

```bash
mvnw.cmd spring-boot:run
```

If Maven is installed globally:

```bash
mvn spring-boot:run
```

The API will be available at:

```text
http://localhost:8080/api
```

Swagger UI will be available at:

```text
http://localhost:8080/
```

## Build

Create a packaged JAR:

```bash
./mvnw clean package
```

Run the generated JAR:

```bash
java -jar target/*.jar
```

## Example cURL Commands

Create an employee:

```bash
curl -X POST http://localhost:8080/api/employees \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Joel",
    "lastName": "Jebitto",
    "email": "joel@example.com"
  }'
```

List employees:

```bash
curl http://localhost:8080/api/employees
```

Get one employee:

```bash
curl http://localhost:8080/api/employees/1
```

Update an employee:

```bash
curl -X PUT http://localhost:8080/api/employees/1 \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Joel",
    "lastName": "Jebitto",
    "email": "updated@example.com"
  }'
```

Delete an employee:

```bash
curl -X DELETE http://localhost:8080/api/employees/1
```

## Notes

* This is a backend-only REST API project.
* PostgreSQL must be running before starting the application.
* The project uses Spring Data REST, so CRUD endpoints are generated from the JPA repository.
* The default API base path is `/api`.
* Swagger UI is configured at the root path `/`.

## Future Improvements

* Add custom service and controller layers
* Add request validation
* Add exception handling with consistent error responses
* Add DTOs instead of exposing entities directly
* Add pagination and filtering examples
* Add Docker Compose for PostgreSQL
* Add integration tests with Testcontainers
* Add authentication and authorization with Spring Security
* Add Flyway or Liquibase database migrations
* Add CI workflow for build and tests

## Author

Built by [Joel Jebitto](https://github.com/joeljebitto-dev).
