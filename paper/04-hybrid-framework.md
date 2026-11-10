# Chapter 4 - Proposed Hybrid QKD-PQC Framework

## 4.1 Design Objectives

The architecture seeks to support:

- Confidentiality
- Integrity
- Authentication
- Cryptographic agility
- Operational resilience
- Auditable security controls

## 4.2 Security Layers

### Quantum Layer

QKD establishes shared key material over suitable quantum and authenticated classical channels.

### Post-Quantum Layer

ML-KEM supports post-quantum key establishment.

ML-DSA and SLH-DSA provide standardized post-quantum digital signatures.

### Symmetric Encryption Layer

AES-256 may be used for protected data transport with appropriately established and managed keys.

### Financial Application Layer

Banking applications enforce transaction validation, authorization, access control, and business rules.

## 4.3 Key Combining

Where multiple independent key-establishment methods are used, a formally analyzed cryptographic combiner should be selected.

The security of the combined system depends on protocol design, authentication, implementation, and operational assumptions.

## 4.4 Threat Model

Threats to evaluate include:

- Harvest-now-decrypt-later attacks
- Man-in-the-middle attacks
- Compromised endpoints
- Side-channel attacks
- Key management failures
- Unauthorized API access
- Insider threats

## 4.5 Evaluation Criteria

Future experiments should measure:

- Key generation rate
- QBER
- Network latency
- Availability
- Recovery behavior
- Integration complexity
- Operational costs
