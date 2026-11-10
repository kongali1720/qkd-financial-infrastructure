# 06 - DOUBLE-ENTRY LEDGER

## 1. Purpose

The ledger is the authoritative internal accounting record.

Payment status and accounting balance are related but separate concepts.

## 2. Double-Entry Principle

Every posted journal must balance:

Total Debits = Total Credits

## 3. Example

Illustrative internal transfer of IDR 100,000:

Debit:
Customer A Liability: IDR 100,000

Credit:
Customer B Liability: IDR 100,000

This is an accounting illustration, not proof of an external bank transfer.

## 4. Suggested Tables

accounts:
- id
- account_code
- account_type
- currency
- status

journal_entries:
- id
- transaction_id
- entry_type
- status
- created_at
- posted_at

journal_lines:
- id
- journal_entry_id
- account_id
- debit_amount
- credit_amount
- currency

## 5. Ledger Rules

1. Posted journal entries are immutable.
2. Each journal entry must balance per currency.
3. Unposted entries must not affect posted balances.
4. Reversals use compensating entries.
5. Posting must be atomic.
6. Every posting must have a business reference.
7. Balance calculation must be deterministic.

## 6. Atomic Posting

Use a single database transaction.

Pseudocode:

BEGIN;

Lock required account rows.

Validate account status.

Validate funding or approved credit.

Insert journal header.

Insert debit line.

Insert credit line.

Verify balance.

Mark journal as POSTED.

COMMIT;

On any failure:

ROLLBACK;

## 7. Important Distinction

Do not equate:
- Payment initiated
- Payment accepted
- Payment processed
- Funds debited
- Funds settled
- Funds available

Each event has a different operational meaning.

## 8. Reconciliation

Compare:
- Internal transaction ID
- Provider transaction ID
- Amount
- Currency
- Value date
- Settlement status

Unmatched entries must enter an exception queue.
