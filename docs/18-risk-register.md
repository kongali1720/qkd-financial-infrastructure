# 18 - RISK REGISTER

| Risk | Impact | Mitigation |
|------|--------|------------|
| Duplicate payments | Critical | Idempotency and provider inquiry |
| Ledger imbalance | Critical | Atomic double-entry posting |
| Provider timeout | High | Unknown state and inquiry |
| Credential leakage | Critical | Secret manager and rotation |
| API compromise | Critical | Authentication, authorization and testing |
| Database loss | Critical | Backup and recovery tests |
| Key compromise | Critical | KMS, rotation and incident response |
| QKD hardware cost | Medium | Laboratory-first strategy |
| Provider integration delay | High | Mock adapter and sandbox |
| Regulatory restrictions | Critical | Early legal review |
| Incorrect reconciliation | High | Independent matching and exception queue |
| Software supply-chain risk | High | Dependency pinning and scanning |

## Risk Ownership

Each risk must have:
- Owner
- Severity
- Probability
- Mitigation
- Due date
- Residual risk
- Approval status

## Escalation

Critical financial integrity or security incidents must stop affected processing until the incident is contained and assessed.
