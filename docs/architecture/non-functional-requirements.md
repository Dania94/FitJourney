# Non-Functional Requirements

## Status
Accepted

## Date
2026-07-04

---

# Purpose

This document defines the non-functional requirements (NFRs) for FitJourney.

These requirements describe how the system should behave and the quality attributes it should provide.

---

# Performance

## API Response Time

- 95% of API requests should complete within 500ms.
- Heavy calculations should complete within 2 seconds.

---

## Database Performance

- Database queries should be optimized.
- Avoid N+1 query problems.
- Proper indexes should be created.

---

# Availability

## Target Availability

- MVP target:
  - 99.0%

- Future target:
  - 99.9%

---

# Reliability

The system should:

- recover gracefully from failures,
- provide meaningful error messages,
- avoid data corruption.

---

# Scalability

The system should support:

- increasing number of users,
- increasing amount of tracked data,
- future extraction of modules into microservices.

The architecture should prioritize:

- modularity,
- horizontal scalability,
- stateless APIs.

---

# Security

## Authentication

- JWT authentication.
- Password hashing using BCrypt.
- Password complexity requirements.
- Brute force protection.
- Account lockout after repeated failed login attempts.

---

## Authorization

- Users may only access their own data.
- Shared resources must respect permissions.

---

## API Security

- Input validation.
- Protection against SQL Injection.
- Protection against XSS.
- Protection against CSRF where applicable.
- Rate limiting (future).

---

## Secret Management

Secrets must never be stored in source code.

---

# Privacy

FitJourney processes personal and health-related information.

The application should:

- collect only necessary information,
- protect user data,
- allow users to delete their accounts,
- allow users to export their data.

---

# GDPR Requirements

The application should support:

- account deletion,
- consent management,
- privacy policy,
- terms of service,
- user data export,
- user data correction.

---

# Data Retention

Deleted accounts should be anonymized where possible.

---

# Maintainability

The system should:

- follow clean architecture principles,
- use modular boundaries,
- provide automated tests,
- use code reviews,
- maintain technical documentation.

---

# Testability

The application should provide:

- unit tests,
- integration tests,
- end-to-end tests (future).

Target:

- minimum 70% test coverage.

---

# Observability

The application should provide:

- structured logging,
- application metrics,
- health endpoints,
- error tracking.

---

# Logging

The application should:

- log important business events,
- avoid logging sensitive information,
- provide sufficient information for debugging.

---

# Monitoring (Future)

- Application metrics
- Database metrics
- Error tracking
- Performance monitoring

---

# Backup and Recovery

The system should support:

- regular database backups,
- restoration procedures,
- disaster recovery documentation.

---

# Accessibility

The application should:

- support mobile devices,
- support different screen sizes,
- follow accessibility guidelines where possible.

---

# Internationalization (Future)

The application should support:

- multiple languages,
- multiple units of measurement,
- multiple time zones.

---

# Compatibility

The application should support:

- Android devices,
- iOS devices,
- modern web browsers.

---

# Sharing Requirements

Users should be able to:

- share meal plans,
- share workout plans.

Permissions:

- OWNER
- EDITOR
- VIEWER

External users may access shared content through read-only links.

---

# Auditability

The system should maintain:

- created timestamps,
- updated timestamps,
- audit information,
- activity history where appropriate.

---

# Decision Summary

FitJourney is designed to become a real public application and therefore prioritizes:

- security,
- privacy,
- maintainability,
- scalability,
- observability,
- and regulatory compliance.