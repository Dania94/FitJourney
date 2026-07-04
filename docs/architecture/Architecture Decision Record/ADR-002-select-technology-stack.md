# Architecture Decision Record (ADR-002)


FitJourney is an all-in-one health and fitness platform that is currently being developed by a small team and aims to:

* provide a production-like learning experience,
* follow enterprise development practices,
* maximize maintainability,
* improve developer employability in the Java ecosystem.

The technology stack should:

* be widely adopted in the industry,
* support long-term maintainability,
* have a strong ecosystem,
* support future scalability,
* provide valuable learning opportunities.

---

# Decision

The following technology stack has been selected.

---

# Backend

## Programming Language

**Java 21 (LTS)**

### Rationale

* Long-Term Support (LTS) release.
* Widely adopted by enterprise companies.
* Stable ecosystem and library support.
* Excellent balance between modern features and industry adoption.

---

## Framework

**Spring Boot 3**

### Rationale

* Industry standard for Java backend development.
* Excellent ecosystem.
* Rapid application development.
* Strong integration with security, data, testing, and cloud technologies.

---

## Build Tool

**Maven**

### Rationale

* Industry standard in many enterprise Java projects.
* Simple and predictable project structure.
* Extensive plugin ecosystem.
* Easier for developers new to build tooling.

---

# Database

## Relational Database

**PostgreSQL**

### Rationale

* Mature and highly reliable.
* Excellent support in Spring Boot.
* Powerful SQL capabilities.
* Supports future advanced features such as JSON columns and full-text search.
* Developer already has experience with SQL and PostgreSQL.

---

## Database Migrations

**Flyway**

### Rationale

* Version-controlled database changes.
* Repeatable migrations.
* Industry standard approach for schema management.

---

# Frontend

## Framework

**Angular**

### Rationale

* Widely used in enterprise environments, especially in Germany.
* Opinionated framework with clear architecture.
* Built-in dependency injection and routing.
* Uses TypeScript by default.
* Excellent for learning enterprise frontend development practices.

---

## Programming Language

**TypeScript**

### Rationale

* Strong typing.
* Better maintainability.
* Improved developer productivity.
* Industry standard for Angular applications.

---

# Authentication

## Authentication Mechanism

**JWT (JSON Web Token)**

### Rationale

* Stateless authentication.
* Simple implementation.
* Suitable for single-page applications.
* Widely used in modern web applications.

---

## Future Enhancement

**OAuth2 Social Login**

Potential providers:

* Google
* Apple
* Facebook

This functionality is not required for the MVP.

---

# Containerization

## Container Platform

**Docker**

### Rationale

* Consistent development environment.
* Simplified deployment.
* Industry standard for application packaging.

---

## Local Development Environment

**Docker Compose**

### Rationale

* Easy local setup.
* Simple orchestration of services.
* Reproducible development environments.

---

# API Documentation

## Tool

**OpenAPI / Swagger**

### Rationale

* Automatic API documentation.
* Easy API testing.
* Improved developer experience.

---

# Testing

## Unit Testing

* JUnit 5
* Mockito

## Integration Testing

* Spring Boot Test
* Testcontainers

### Rationale

* Production-like testing environment.
* Better confidence during refactoring.
* Valuable experience for enterprise development.

---

# Future Technologies

## Cloud Platform

**AWS**

Potential services:

* ECS
* RDS
* S3
* CloudWatch
* IAM

---

## CI/CD

**GitHub Actions**

---

# Final Technology Stack

| Category            | Technology        |
| ------------------- | ----------------- |
| Language            | Java 21           |
| Backend             | Spring Boot 3     |
| Build Tool          | Maven             |
| Database            | PostgreSQL        |
| Database Migration  | Flyway            |
| Frontend            | Angular           |
| Frontend Language   | TypeScript        |
| Authentication      | JWT               |
| Containerization    | Docker            |
| Local Orchestration | Docker Compose    |
| API Documentation   | OpenAPI / Swagger |
| Unit Testing        | JUnit 5           |
| Mocking             | Mockito           |
| Integration Testing | Testcontainers    |
| Cloud (Future)      | AWS               |
| CI/CD (Future)      | GitHub Actions    |

---

# Consequences

## Positive

* Strong alignment with enterprise development practices.
* Excellent learning opportunities.
* High employability in the Java ecosystem.
* Maintainable and scalable architecture.

## Negative

* Angular has a steeper learning curve.
* More technologies to learn initially.
* Slightly slower initial development compared to simpler stacks.

---

# Decision Summary

The selected technology stack prioritizes:

* enterprise readiness,
* maintainability,
* long-term scalability,
* and developer growth and employability.
