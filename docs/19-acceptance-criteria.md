# 19 - ACCEPTANCE CRITERIA

## 1. Software Foundation

- Application builds reproducibly.
- Automated CI passes.
- Configuration is environment-specific.
- Secrets are not stored in source control.

## 2. Payment Processing

- Valid requests are accepted.
- Invalid requests are rejected.
- Idempotency prevents duplicate execution.
- Unknown provider outcomes are handled safely.
- Reversal is auditable.

## 3. Accounting

- Posted entries always balance.
- Posted entries cannot be silently modified.
- Reversal creates compensating entries.
- Reconciliation exceptions are visible.

## 4. Banking

- Only approved provider channels are used.
- Provider references are persisted.
- Submission and settlement states are distinct.
- Sandbox results are never represented as production funds.

## 5. Security

- Authentication and authorization work.
- Administrative access is protected.
- Sensitive information is not logged.
- Security tests pass.
- Cryptographic inventory exists.

## 6. QKD/PQC

- PQC algorithms use supported implementations.
- QKD simulation is identified as simulation.
- Hardware deployment is separately validated.
- Key lifecycle and access controls are documented.

## 7. Operations

- Monitoring is active.
- Alerts are tested.
- Backups are restorable.
- Recovery procedures are exercised.
- Incident ownership is assigned.

## 8. Production Approval

Production requires formal approval from:
- Engineering
- Security
- Operations
- Banking provider
- Legal and compliance
- Authorized business management

No production release is approved solely by successful software compilation.
