# 10 - DATABASE DESIGN

## 1. Recommended Database

PostgreSQL.

## 2. Core Entities

customers
- id
- legal_name
- status
- created_at

accounts
- id
- customer_id
- currency
- account_type
- status

payments
- id
- client_id
- source_account_id
- destination_reference
- amount
- currency
- status
- provider_reference
- created_at
- updated_at

idempotency_records
- id
- client_id
- idempotency_key
- request_hash
- payment_id
- response_status
- created_at

journal_entries
- id
- payment_id
- status
- created_at
- posted_at

journal_lines
- id
- journal_entry_id
- account_id
- debit_amount
- credit_amount
- currency

provider_events
- id
- provider_id
- provider_reference
- event_type
- event_timestamp
- payload_hash
- processing_status

audit_events
- id
- actor_id
- action
- resource_type
- resource_id
- correlation_id
- created_at

reconciliation_records
- id
- payment_id
- provider_reference
- internal_status
- provider_status
- reconciliation_status
- created_at

## 3. Data Integrity

- Primary keys
- Foreign keys
- Unique constraints
- Check constraints
- Appropriate indexes
- Transaction isolation
- Database backups

## 4. Monetary Values

Use fixed-precision decimal or integer minor units.

Never use binary floating-point for financial amounts.

Currency precision must follow currency-specific rules.

## 5. Database Security

- Separate database users.
- Least-privilege permissions.
- Encrypted connections.
- Protected backups.
- Audited migrations.
- Restricted production access.
- Tested restoration procedures.

## 6. Data Retention

Define retention based on applicable law, contracts and business requirements.

Protect personal and financial data through access controls and minimization.
