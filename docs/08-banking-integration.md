# 08 - BANKING INTEGRATION

## 1. Integration Principle

The platform must communicate with financial institutions only through officially authorized channels.

Possible integration types:

- Bank-provided REST API
- Corporate banking API
- Host-to-host connectivity
- Approved file-based integration
- Payment service provider API
- Approved financial messaging infrastructure

## 2. Adapter Architecture

Core payment service must not depend directly on a specific bank implementation.

Suggested interface:

```python
from typing import Protocol

class BankingAdapter(Protocol):

    async def submit_payment(self, request):
        ...

    async def get_payment_status(self, reference):
        ...

    async def get_account_statement(self, parameters):
        ...

    async def health_check(self):
        ...
```

Actual methods must be implemented according to the provider's official API contract.

## 3. Provider Configuration

Each adapter requires:

- Provider identifier
- Approved endpoint
- Authentication mechanism
- Certificate requirements
- Request schema
- Response schema
- Timeout policy
- Retry policy
- Inquiry procedure
- Error mapping
- Sandbox credentials

Credentials must never be committed to Git.

## 4. Host-to-Host Requirements

Depending on the provider:

- Network allowlisting
- Mutual TLS
- Client certificates
- IPsec or VPN
- Message authentication
- File encryption
- File integrity checks
- Acknowledgement processing
- Sequence management
- Duplicate detection

## 5. Financial Messaging

For ISO 20022 or SWIFT integrations:

- Follow the official message specifications.
- Use the exact provider-supported version.
- Validate message schemas.
- Preserve original references.
- Validate acknowledgements.
- Record transport and business status separately.

An MT199 or other financial message alone does not prove that funds have been credited or settled.

## 6. Sandbox Strategy

Phase 1:
Mock banking adapter.

Phase 2:
Provider sandbox.

Phase 3:
Formal integration testing.

Phase 4:
Authorized pilot.

Phase 5:
Controlled production rollout.

## 7. Evidence Model

Store:
- Internal payment ID
- Provider reference
- Submission timestamp
- Provider response
- Inquiry response
- Settlement evidence
- Reconciliation result

Do not manufacture provider confirmations or bank statements.
