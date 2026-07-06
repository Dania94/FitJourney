# Module Responsibilities and Boundaries

## Status
Accepted

## Date
2026-07-04

---

# Purpose

This document defines the responsibilities, ownership, boundaries, and communication rules between modules in the FitJourney Modular Monolith.

The goal is to maintain a clean architecture, avoid tight coupling, and enable future extraction of modules into microservices if necessary.

---

# Architecture Principles

## High Cohesion

Each module should contain closely related business functionality.

---

## Low Coupling

Modules should depend on abstractions and avoid direct dependencies on internal implementations of other modules.

---

## Single Ownership

Each module owns its business logic and data.

---

## Separation of Concerns

Business logic, infrastructure, and presentation concerns should remain separated.

---

## Explicit Communication

Modules communicate only through:

- Public interfaces
- Domain events

---

# Communication Rules

## Allowed

### Synchronous Communication

Through public APIs/interfaces.

Example:

```java
UserProfile profile =
        userProfileQueryService.getProfile(userId);
```

---

### Asynchronous Communication

Through domain events.

Examples:

- MealLoggedEvent
- WeightUpdatedEvent
- WorkoutCompletedEvent
- CalorieTargetExceededEvent

---

# Not Allowed

❌ Accessing another module's repositories.

❌ Accessing another module's entities directly.

❌ Calling internal services of another module.

❌ Sharing mutable state between modules.

---

# Module Overview

## User Module

### Responsibilities

- Registration
- Authentication
- Authorization
- User profile management
- User goals
- Activity level
- Dietary preferences
- Cuisine preferences

### Owns

- Users
- UserPreferences
- UserGoals
- UserSettings

### Dependencies

None.

---

## Nutrition Module

### Responsibilities

- Food catalog
- Custom foods
- Meal planning
- Food diary
- Calories tracking
- Macro tracking

### Owns

- Foods
- CustomFoods
- MealPlans
- FoodLogs

### Dependencies

- User Module

Needs:

- goals
- dietary preferences
- cuisine preferences

---

## Workout Module

### Responsibilities

- Exercise catalog
- Custom exercises
- Workout plans
- Workout sessions

### Owns

- Exercises
- WorkoutPlans
- WorkoutSessions

### Dependencies

- User Module

Needs:

- goals
- fitness level

---

## Progress Module

### Responsibilities

- Weight tracking
- Body measurements
- Progress history
- Progress statistics

### Owns

- WeightEntries
- MeasurementEntries

### Dependencies

- User Module

---

## Recommendation Module

### Responsibilities

- Meal recommendations
- Workout recommendations
- Personalized suggestions
- Goal calculations
- Adaptive recommendations

### Owns

- RecommendationRules
- RecommendationHistory

### Dependencies

- User Module
- Nutrition Module
- Workout Module
- Progress Module
- Women's Health Module

---

## Women's Health Module

### Responsibilities

- Menstrual cycle tracking
- Symptoms tracking
- Pregnancy tracking (Version 2)

### Owns

- Cycles
- Symptoms
- PregnancyData

### Dependencies

- User Module

---

## Notification Module

### Responsibilities

- In-app notifications
- Email notifications
- Push notifications
- Scheduled reminders

### Owns

- Notifications
- ReminderSchedules
- NotificationPreferences

### Dependencies

- User Module
- Recommendation Module
- Women's Health Module

---

## Shared Module

### Responsibilities

Contains only technical shared components.

### Allowed Content

- Exceptions
- Utilities
- Common enums
- Base classes
- Shared DTOs

### Restrictions

No business logic may be placed inside this module.

---

# Dependency Diagram

```text
User
├── Nutrition
├── Workout
├── Progress
├── Women's Health

Nutrition ───────┐
Workout ─────────┤
Progress ────────┤
Women's Health ──┤
                 ↓
          Recommendation
                 ↓
            Notification
```

---

# Package Structure

```text
com.fitjourney

├── user
│   ├── api
│   ├── application
│   ├── domain
│   ├── infrastructure
│   └── web

├── nutrition
├── workout
├── progress
├── recommendation
├── womenshealth
├── notification
└── shared
```

---

# Layer Responsibilities

## web

REST Controllers.

---

## application

Use cases and application services.

Examples:

- LogMealUseCase
- CreateWorkoutPlanUseCase
- RegisterUserUseCase

---

## domain

Business rules and entities.

---

## infrastructure

Repositories and external integrations.

---

## api

Public contracts exposed to other modules.

Example:

```java
public interface UserProfileQueryService {
    UserProfile getProfile(Long userId);
}
```

---

# Domain Events

The following events are expected in the system:

- UserRegisteredEvent
- MealLoggedEvent
- WeightUpdatedEvent
- WorkoutCompletedEvent
- CalorieTargetExceededEvent
- CycleStartedEvent

---

# Future Microservice Candidates

The following modules may eventually be extracted into independent services:

1. Recommendation Module
2. Notification Module
3. Analytics Module

---

# Decision Summary

FitJourney follows a Modular Monolith architecture with:

- clear module ownership,
- explicit communication,
- low coupling,
- high cohesion,
- and future microservice readiness.