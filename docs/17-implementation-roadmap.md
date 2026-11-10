# 17 - IMPLEMENTATION ROADMAP

## Overview

The roadmap prioritizes a working financial software foundation before introducing physical QKD equipment.

Estimated durations are planning assumptions. Actual delivery depends on team capacity, provider access, budget, licensing and testing results.

## PHASE 0 - Requirements and Governance

Duration: Weeks 1-2

Deliverables:
- Project charter.
- Requirements.
- Threat model.
- Initial architecture.
- Technology decisions.
- Compliance applicability review.
- Project backlog.

Exit criteria:
Architecture and scope approved.

## PHASE 1 - Development Foundation

Duration: Weeks 3-4

Deliverables:
- Git repository.
- Backend skeleton.
- Docker Compose.
- PostgreSQL.
- Configuration management.
- CI pipeline.
- Health endpoints.

Exit criteria:
Application starts reproducibly and passes CI.

## PHASE 2 - Transaction Engine

Duration: Weeks 5-8

Deliverables:
- Payment API.
- Transaction state machine.
- Idempotency.
- Authorization rules.
- Payment orchestrator.
- Mock banking adapter.

Exit criteria:
Synthetic payments pass complete lifecycle tests.

## PHASE 3 - Accounting Engine

Duration: Weeks 9-11

Deliverables:
- Account model.
- Double-entry journal.
- Atomic posting.
- Reversal.
- Balance calculation.
- Reconciliation framework.

Exit criteria:
All accounting invariants pass automated tests.

## PHASE 4 - Banking Sandbox

Duration: Weeks 12-15

Deliverables:
- Provider adapter.
- Official sandbox credentials.
- API contract tests.
- Status inquiry.
- Timeout handling.
- Provider reconciliation.

Exit criteria:
End-to-end sandbox integration verified.

## PHASE 5 - Security Engineering

Duration: Weeks 16-19

Deliverables:
- Authentication.
- MFA for administration.
- RBAC.
- Secrets management.
- Audit logging.
- Vulnerability scanning.
- Security test report.

Exit criteria:
Critical security findings resolved.

## PHASE 6 - PQC Integration

Duration: Weeks 20-23

Deliverables:
- Cryptographic inventory.
- ML-KEM evaluation.
- ML-DSA evaluation.
- Supported hybrid TLS evaluation.
- Key management integration.
- Performance benchmark.

Exit criteria:
Interoperability and security tests documented.

## PHASE 7 - QKD Laboratory Research

Duration: Weeks 24-30+

Deliverables:
- QKD protocol simulation.
- Laboratory requirements.
- Hardware evaluation.
- Authenticated key delivery.
- QKD key management integration.
- Independent security review.

Exit criteria:
Laboratory results and limitations documented.

A simulation does not satisfy hardware deployment acceptance.

## PHASE 8 - Production Readiness

Duration: Depends on regulatory and provider approvals.

Deliverables:
- Production infrastructure.
- Independent penetration test.
- Operational procedures.
- Disaster recovery test.
- Provider approval.
- Legal and compliance sign-off.
- Formal go-live approval.

Exit criteria:
All applicable requirements satisfied.

## PHASE GATES

G0: Requirements approved.

G1: Development platform working.

G2: Payment simulation verified.

G3: Ledger integrity verified.

G4: Banking sandbox integration verified.

G5: Security assessment passed.

G6: PQC interoperability demonstrated.

G7: QKD laboratory evaluation completed.

G8: Production authorization approved.

## Important

Production payment processing must not begin merely because software tests pass.

It also requires authorized provider connectivity, applicable regulatory permissions, operational controls and independent risk acceptance.
