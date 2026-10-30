# Enterprise Project Tracking System

A Spring Boot–based enterprise project tracking application designed to manage employees, managers, projects, assignments, commits, departments, locations, and user credentials through a structured backend architecture.

The application provides RESTful CRUD operations, role-based security, relational database persistence, API documentation, monitoring endpoints, and integrations for email/SMS-based communication.

## Features

- Employee management
- Manager management
- Administrator management
- Project management
- Project assignment management
- Employee commit tracking
- Department management
- Location management
- Credential management
- RESTful CRUD APIs
- Spring Security authentication and authorization
- Spring Data JPA / Hibernate persistence
- MySQL database support
- H2 database support
- Flyway database version control
- Swagger / OpenAPI API documentation
- Spring Boot Actuator monitoring
- Docker support
- Email integration
- Twilio SMS integration
- Server-side HTML templates
- Unit and integration test support
- Maven-based build and dependency management

## Technology Stack

| Technology | Purpose |
|---|---|
| Java 11 | Application development |
| Spring Boot | Backend application framework |
| Spring Security | Authentication and authorization |
| Spring Data JPA | Data access layer |
| Hibernate | ORM |
| MySQL | Relational database |
| H2 | Development/testing database |
| Flyway | Database migration and version control |
| Maven | Build and dependency management |
| Swagger / OpenAPI | REST API documentation |
| Spring Boot Actuator | Application monitoring |
| Docker | Containerization |
| Twilio API | SMS communication |
| HTML / JavaScript / jQuery | Web interface |
| Bootstrap | UI styling |
| Git | Version control |
| Postman | API testing |

## Architecture

The application follows a layered Spring Boot architecture:

```text
Client
   |
   v
Controllers
   |
   v
Services
   |
   v
Repositories
   |
   v
MySQL / H2 Database
```

### Main Layers

```text
src/main/java
└── com.pfa.app
    ├── controllers
    ├── services
    ├── repositories
    ├── models
    ├── security
    ├── configs
    ├── exceptions
    ├── converters
    ├── enums
    └── utils
```

### Resources

```text
src/main/resources
├── static
│   ├── css
│   ├── js
│   └── images
├── templates
└── application.properties
```

## Core Domain

The system manages the following major business areas:

```text
Administrator
    |
    +-- Employees
    |
    +-- Departments
    |
    +-- Locations

Manager
    |
    +-- Projects
    |
    +-- Assignments
    |
    +-- Commit Tracking

Employee
    |
    +-- Assigned Projects
    |
    +-- Team
    |
    +-- Commit Tracking
    |
    +-- Credentials
```

## Prerequisites

Install the following before running the application:

- JDK 11
- Maven or Maven Wrapper
- MySQL
- Git

Optional:

- Docker
- Postman
- IntelliJ IDEA / Eclipse / VS Code

Verify Java:

```powershell
java -version
```

Verify Maven:

```powershell
mvn -version
```

## Clone the Repository

```powershell
git clone https://github.com/Mohamednabil292638/enterprise-project-tracking-system.git
```

Move into the project:

```powershell
cd enterprise-project-tracking-system
```

## Database Setup

Create a MySQL database and configure the application's database connection through environment variables or your local Spring configuration.

The repository contains:

```text
pfa_db.sql
```

This SQL file can be used to initialize the database schema and data.

For MySQL:

```sql
source ./pfa_db.sql;
```

## Environment Configuration

Sensitive credentials should **not** be committed to GitHub.

Configure the following environment variables before starting the application:

```text
MAIL_USERNAME
MAIL_PASSWORD

TWILIO_ACCOUNT_SID
TWILIO_AUTH_TOKEN
TWILIO_TRIAL_NUMBER
```

### Windows PowerShell Example

```powershell
$env:MAIL_USERNAME="your-email@example.com"
$env:MAIL_PASSWORD="your-mail-password"

$env:TWILIO_ACCOUNT_SID="your-account-sid"
$env:TWILIO_AUTH_TOKEN="your-auth-token"
$env:TWILIO_TRIAL_NUMBER="your-twilio-number"
```

Use your own valid credentials.

Do not commit real passwords, API keys, authentication tokens, or other secrets to GitHub.

## Build the Application

Using the Maven Wrapper:

### Windows

```powershell
.\mvnw.cmd clean install
```

### Linux / macOS

```bash
./mvnw clean install
```

Or with Maven:

```bash
mvn clean install
```

## Run the Application

Using the Maven Wrapper:

```powershell
.\mvnw.cmd spring-boot:run
```

Or:

```powershell
mvn spring-boot:run
```

The application runs on:

```text
http://localhost:8080
```

## Run Using the JAR

After building the project:

```powershell
java -jar target/project-tracking-sys.jar
```

For a development profile:

```powershell
java -Dspring.profiles.active=dev -jar target/project-tracking-sys.jar
```

For the test profile:

```powershell
java -Dspring.profiles.active=test -jar target/project-tracking-sys.jar
```

For the production profile:

```powershell
java -Dspring.profiles.active=prod -jar target/project-tracking-sys.jar
```

## API Documentation

Swagger UI is available when the application is running:

```text
http://localhost:8080/swagger-ui.html
```

Use Swagger to inspect and test the available REST endpoints.

## Actuator Endpoints

Spring Boot Actuator provides application monitoring endpoints.

| Endpoint | Method |
|---|---|
| `/actuator/` | GET |
| `/actuator/health` | GET |
| `/actuator/info` | GET |
| `/actuator/prometheus` | GET |
| `/actuator/httptrace` | GET |

Example:

```text
http://localhost:8080/actuator/health
```

## Application Endpoints

The application includes role-based web functionality for:

### Employees

```text
/app/employees
/app/employees/employee-index
/app/employees/employee-show-my-commits
/app/employees/employee-add-commit
/app/employees/employee-show-all-commits
/app/employees/employee-team
```

### Managers

```text
/app/managers
/app/managers/manager-index
/app/managers/manager-add-project
/app/managers/manager-show-commits
/app/managers/manager-describe-commit
/app/managers/manager-assign
/app/managers/manager-edit-project
/app/managers/manager-delete-project
/app/managers/manager-info
/app/managers/manager-team
/app/managers/manager-assigned-projects
```

### Administrators

```text
/app/admins
/app/admins/admin-index
/app/admins/employees/admin-employees-list
/app/admins/employees/admin-employees-add
/app/admins/employees/admin-employees-edit
/app/admins/employees/admin-employee-credentials
/app/admins/employees/admin-employees-isactive
/app/admins/employees/admin-employees-delete
/app/admins/departments/admin-departments-list
/app/admins/departments/admin-departments-edit
/app/admins/departments/admin-departments-delete
/app/admins/locations/admin-locations-list
/app/admins/locations/admin-locations-edit
/app/admins/locations/admin-locations-delete
```

## Testing

The project contains test sources under:

```text
src/test/java
```

Run the test suite with:

```powershell
.\mvnw.cmd test
```

Or:

```powershell
mvn test
```

## Docker

The project includes Docker configuration files:

```text
Dockerfile
docker-compose.yaml
```

Build the Docker image:

```powershell
docker build -t enterprise-project-tracking-system .
```

Run the container:

```powershell
docker run -p 8080:8080 enterprise-project-tracking-system
```

For Docker Compose:

```powershell
docker compose up --build
```

## Database

The application uses relational database persistence through Spring Data JPA and Hibernate.

Supported databases include:

- MySQL
- H2

Database initialization and migration support is provided through Flyway.

Database-related project files include:

```text
pfa_db.sql
```

## Project Structure

```text
enterprise-project-tracking-system/
│
├── .github/
├── .mvn/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/pfa/app/
│   │   │       ├── configs/
│   │   │       ├── controllers/
│   │   │       ├── converters/
│   │   │       ├── enums/
│   │   │       ├── exceptions/
│   │   │       ├── models/
│   │   │       ├── repositories/
│   │   │       ├── security/
│   │   │       ├── services/
│   │   │       └── utils/
│   │   │
│   │   └── resources/
│   │       ├── static/
│   │       ├── templates/
│   │       └── application.properties
│   │
│   └── test/
│       └── java/
│
├── Dockerfile
├── docker-compose.yaml
├── mvnw
├── mvnw.cmd
├── pom.xml
├── pfa_db.sql
├── pfa_ERD.png
├── Procfile
├── system.properties
└── README.md
```

## Development Workflow

Recommended development workflow:

```text
Clone Repository
      |
      v
Configure Environment Variables
      |
      v
Configure MySQL
      |
      v
Build with Maven
      |
      v
Run Tests
      |
      v
Start Spring Boot Application
      |
      v
Test APIs with Swagger / Postman
      |
      v
Commit Changes
      |
      v
Push to GitHub
```

## API Testing

Postman can be used to test the REST APIs.

Recommended testing flow:

```text
Authentication
      ↓
Employee APIs
      ↓
Manager APIs
      ↓
Project APIs
      ↓
Assignment APIs
      ↓
Commit APIs
      ↓
Department APIs
      ↓
Location APIs
```

Swagger provides interactive API documentation and testing capabilities.

## Security

The application uses Spring Security for authentication and authorization.

Sensitive configuration values are provided through environment variables rather than being stored directly in the repository.

Never commit:

```text
Passwords
API Keys
Authentication Tokens
Database Credentials
Private Keys
Production Secrets
```

## Version Control

Git is used for source-code version control.

Basic workflow:

```powershell
git status
git add .
git commit -m "Your commit message"
git push
```

## License

This repository contains the Project Tracking System application and its associated source code and configuration.

Refer to the repository history and project files for applicable licensing and attribution information.
