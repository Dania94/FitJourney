# Architecture Decision Record (ADR-001)


# Context

FitJourney is an all-in-one health and fitness platform that allows users to:

* track nutrition and calories,
* manage meal plans,
* track workouts,
* monitor weight and body measurements,
* track women's health information,
* receive personalized recommendations.

The product is currently in the MVP stage and is being developed by a very small team (one developer). Therefore, the architecture should prioritize:

* simplicity,
* maintainability,
* development speed,
* ease of deployment,
* low operational overhead,
* future scalability.

Several architectural approaches were considered:

1. Traditional Monolith
2. Modular Monolith
3. Microservices

---

# Decision

We have decided to implement FitTrack as a **Modular Monolith**.

The application will be deployed as a single application but internally organized into independent modules with clear boundaries and responsibilities.

---

# Rationale

## 1. Small Team Size

The project is currently developed by a single developer. Microservices introduce significant operational complexity that is not justified for a small team.

---

## 2. Faster Development

A modular monolith allows faster implementation because:

* there is only one codebase,
* there is only one deployment,
* local development is simpler,
* debugging is easier.

The team can focus on delivering business features instead of managing infrastructure.

---

## 3. Lower Operational Complexity

Microservices would require additional infrastructure, including:

* service discovery,
* API gateway,
* distributed tracing,
* inter-service communication,
* service monitoring,
* container orchestration,
* independent deployment pipelines.

These requirements would significantly increase the complexity of the project.

---

## 4. Highly Connected Business Domains

The domains of the application are highly related.

Examples:

* weight changes influence calorie recommendations,
* user goals influence workout recommendations,
* food tracking influences progress calculations.

Keeping these domains in a single application simplifies communication and transactions.

---

## 5. Easier Maintenance and Debugging

Because everything runs inside a single application:

* debugging is simpler,
* testing is easier,
* refactoring is safer,
* development productivity is higher.

---

## 6. Future Evolution

The modular monolith architecture provides a migration path to microservices if the application grows significantly.

Modules can later be extracted into independent services if there is a business or technical need.

Possible future extraction candidates include:

* Recommendation Service
* Notification Service
* Analytics Service

---

# Architectural Principles

The application should follow these principles:

## Clear Module Boundaries

Each module should have its own responsibilities and avoid direct access to another module's internals.

## High Cohesion

Code that belongs together should remain together.

## Low Coupling

Modules should communicate through well-defined interfaces or events.

## Independent Domain Ownership

Each module owns its own business logic and data.

## Separation of Concerns

Business logic, infrastructure, and presentation layers should remain separated.

---

# Initial Module Candidates

* User Module
* Nutrition Module
* Workout Module
* Progress Module
* Recommendation Module
* Women's Health Module
* Notification Module

---

# Positive Consequences

* Faster development.
* Easier deployment.
* Easier debugging.
* Easier testing.
* Lower operational overhead.
* Better maintainability.
* Future migration path to microservices.

---

# Negative Consequences

* The entire application is deployed together.
* Individual modules cannot be scaled independently.
* Strong discipline is required to maintain module boundaries.
* Poor module design can eventually lead to a "Big Ball of Mud".

---

# Decision Summary

For the current size, team structure, and business requirements of FitTrack, a **Modular Monolith** provides the best balance between simplicity, maintainability, and future scalability.
