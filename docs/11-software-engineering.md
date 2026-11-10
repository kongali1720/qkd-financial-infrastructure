# 11 - SOFTWARE ENGINEERING

## 1. Recommended Stack

Backend:
Python 3.12+ and FastAPI.

Database:
PostgreSQL.

ORM:
SQLAlchemy.

Migrations:
Alembic.

Validation:
Pydantic.

Testing:
pytest and HTTPX.

Quality:
Ruff and static type checking.

Infrastructure:
Docker and Docker Compose.

API:
OpenAPI.

Frontend:
Optional React or Next.js administration interface.

## 2. Backend Project Structure

```text
backend/
├── app/
│   ├── main.py
│   ├── core/
│   │   ├── config.py
│   │   ├── security.py
│   │   └── logging.py
│   ├── api/
│   │   └── v1/
│   │       ├── payments.py
│   │       ├── accounts.py
│   │       └── health.py
│   ├── models/
│   ├── schemas/
│   ├── repositories/
│   ├── services/
│   │   ├── payment_service.py
│   │   ├── ledger_service.py
│   │   ├── risk_service.py
│   │   └── reconciliation_service.py
│   ├── adapters/
│   │   ├── banking/
│   │   └── cryptography/
│   └── workers/
├── migrations/
├── tests/
├── Dockerfile
├── requirements.txt
└── .env.example
```

## 3. Software Development Lifecycle

1. Requirements.
2. Architecture.
3. Database modeling.
4. API contract.
5. Implementation.
6. Unit tests.
7. Integration tests.
8. Security tests.
9. Staging deployment.
10. Acceptance review.
11. Controlled production release.

## 4. Coding Standards

- Use typed interfaces.
- Separate controllers and business logic.
- Use dependency injection.
- Validate all external input.
- Handle exceptions explicitly.
- Use structured logs.
- Never hardcode credentials.
- Avoid business logic inside API controllers.
- Write automated tests.
- Review all financial code changes.

## 5. Domain Boundaries

Payment Service:
Payment lifecycle.

Ledger Service:
Accounting records.

Banking Adapter:
External provider communication.

Risk Service:
Policy evaluation.

KMS Integration:
Cryptographic operations.

Audit Service:
Security and financial event records.

## 6. Event-Driven Processing

Use an outbox pattern when publishing events from a database transaction.

The outbox ensures that database state and event publication intent are committed together.

Consumers must be idempotent.

## 7. Code Review Requirements

Every change involving:
- Payment state
- Balance calculation
- Ledger posting
- Authorization
- Cryptographic functions
- Provider integration

requires focused review and automated test coverage.
