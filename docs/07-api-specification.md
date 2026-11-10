# 07 - API SPECIFICATION

## 1. API Design

Base path:

/api/v1

Content type:

application/json

Transport:

HTTPS only.

## 2. Proposed Endpoints

POST /api/v1/payments
GET /api/v1/payments/{payment_id}
POST /api/v1/payments/{payment_id}/cancel
POST /api/v1/payments/{payment_id}/reversal
GET /api/v1/accounts/{account_id}/balance
GET /api/v1/transactions/{transaction_id}
GET /api/v1/health
GET /api/v1/readiness

Administrative and balance-changing endpoints require additional authorization.

## 3. Payment Request Example

```json
{
  "source_account_id": "acct_test_001",
  "destination_account_id": "acct_test_002",
  "amount": "150000.00",
  "currency": "IDR",
  "description": "Internal test payment",
  "reference": "TEST-2026-0001"
}
```

This is a synthetic test request.

## 4. HTTP Headers

Authorization: Bearer <access_token>

Idempotency-Key: <unique-request-key>

Content-Type: application/json

X-Correlation-ID: <request-correlation-id>

## 5. Successful Response Example

```json
{
  "payment_id": "pay_test_001",
  "status": "PENDING_AUTHORIZATION",
  "amount": "150000.00",
  "currency": "IDR",
  "created_at": "2026-11-11T00:00:00Z"
}
```

The response means the instruction was accepted into the workflow, not that funds have settled.

## 6. Error Format

```json
{
  "error": {
    "code": "INSUFFICIENT_FUNDS",
    "message": "The requested transaction cannot be authorized.",
    "correlation_id": "corr_test_001"
  }
}
```

## 7. API Security

- OAuth 2.0 or equivalent approved authentication.
- Short-lived access tokens.
- Scope-based authorization.
- Rate limiting.
- Input validation.
- Request size limits.
- Idempotency.
- Audit logging.
- Secure error handling.
- API versioning.

Never return secrets, access tokens or internal stack traces.
