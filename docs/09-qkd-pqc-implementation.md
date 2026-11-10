# 09 - QKD AND PQC IMPLEMENTATION

## 1. Architecture Principle

QKD and PQC provide cryptographic security capabilities.

They do not:
- Move money
- Approve payment instructions
- Confirm bank balances
- Replace account authorization
- Replace transaction accounting

## 2. PQC Standards

FIPS 203:
ML-KEM - Key encapsulation.

FIPS 204:
ML-DSA - Digital signatures.

FIPS 205:
SLH-DSA - Stateless hash-based digital signatures.

## 3. Recommended Migration Strategy

Stage 1:
Inventory existing cryptographic dependencies.

Stage 2:
Identify vulnerable public-key algorithms.

Stage 3:
Select maintained and supported PQC implementations.

Stage 4:
Test hybrid protocol support.

Stage 5:
Measure performance and interoperability.

Stage 6:
Deploy gradually with monitoring and rollback controls.

## 4. QKD Integration

Required components may include:

- Quantum transmitter
- Quantum receiver
- Quantum optical channel
- Authenticated classical channel
- QKD key management
- Key delivery interface
- Secure endpoint integration

## 5. Key Management

Track:
- Key identifier
- Algorithm
- Purpose
- Creation time
- Activation time
- Expiry
- Rotation status
- Owner
- Hardware or KMS reference

Never log raw secret key material.

## 6. Cryptographic Separation

Application encryption keys must be managed independently from payment business logic.

Prefer approved AEAD mechanisms such as AES-GCM with correct nonce management.

Do not invent custom cryptographic protocols.

## 7. QKD Deployment Stages

1. Literature and protocol review.
2. Software simulation.
3. Laboratory equipment evaluation.
4. Key management integration.
5. Authenticated endpoint testing.
6. Performance testing.
7. Independent security review.
8. Controlled deployment assessment.

A software simulation is not a real QKD implementation.
