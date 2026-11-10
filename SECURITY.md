# KFIP Security Policy

**Project:** Kongali Financial Infrastructure Platform (KFIP)
**Integration Component:** FAM Crypto Host
**Document Type:** Repository Security Policy
**Status:** Active Policy — Implementation Evidence Required

---

## 1. Purpose

This document defines the security reporting and vulnerability
handling policy for the Kongali Financial Infrastructure Platform
(KFIP) repository.

It establishes expectations for responsible vulnerability
disclosure, security assessment, access control, data protection,
and security incident handling.

This policy complements:

- `docs/12-security-compliance.md`
- `docs/25-cryptohost-integration-architecture.md`

This policy does not constitute a security certification,
regulatory approval, penetration-test report, or guarantee
of production security.

## 2. Scope

This policy applies to security issues affecting project-controlled
components, including:

- KFIP source code and application components.
- FAM Crypto Host application code.
- Authentication and authorization mechanisms.
- Tenant membership and tenant data isolation.
- Payment orchestration and transaction controls.
- Database models, migrations, and access controls.
- API endpoints and application integrations.
- Deployment configuration and infrastructure definitions.
- Cryptographic implementations and key-management integrations.
- Repository workflows and software supply-chain dependencies.
- Project documentation where inaccurate instructions create
  security exposure.

Third-party banking systems, external payment networks, cloud
providers, and other systems not controlled by this project are
outside the project's direct testing authority.

## 3. Vulnerability Reporting

Security vulnerabilities must not be disclosed through public
GitHub issues, public discussions, or publicly accessible
pull requests before maintainers have had an opportunity
to assess the report.

### Preferred reporting channel

If GitHub Private Vulnerability Reporting is enabled for this
repository, use the repository's Security tab and select
**Report a vulnerability**.

Repository:
https://github.com/kongali1720/qkd-financial-infrastructure

If private vulnerability reporting is unavailable, contact
the repository maintainers through a verified private channel.

Do not publish exploit details, credentials, private keys,
personal information, or sensitive financial records.

### Suggested report contents

A useful vulnerability report should include:

1. A clear description of the issue.
2. Affected component, file, endpoint, or version.
3. Conditions required to reproduce the issue.
4. Reproduction steps in an authorized test environment.
5. Expected and actual behaviour.
6. Potential security impact.
7. Supporting logs or screenshots with sensitive information
   removed.
8. Suggested mitigation, if known.

Do not include live credentials, complete account numbers,
private keys, access tokens, or real customer transaction data.

## 4. Responsible Disclosure

Security researchers and contributors are expected to:

- Act in good faith.
- Limit testing to systems they own or are explicitly authorized
  to assess.
- Avoid accessing, modifying, or deleting other users' data.
- Avoid service disruption and denial-of-service testing.
- Avoid social engineering or phishing.
- Avoid persistence, lateral movement, or unauthorized access.
- Stop testing when sensitive information or unintended access
  is encountered.
- Report findings privately before public disclosure.

Researchers must not test production banking infrastructure,
bank portals, payment networks, or third-party services without
explicit authorization from the respective owners.

## 5. Vulnerability Severity and Triage

Maintainers should assess reported vulnerabilities based on:

- Exploitability.
- Required privileges and attacker access.
- Confidentiality impact.
- Integrity impact.
- Availability impact.
- Financial and transaction impact.
- Tenant isolation impact.
- Potential regulatory and operational consequences.

Suggested severity categories:

| Severity | Description |
|---|---|
| Critical | Direct compromise of sensitive systems, unauthorized financial actions, or broad tenant data exposure |
| High | Significant privilege escalation, cross-tenant access, or compromise of sensitive information |
| Medium | Limited unauthorized access or security weaknesses requiring specific conditions |
| Low | Limited-impact security weaknesses or hardening opportunities |
| Informational | Security recommendations without a demonstrated vulnerability |

Severity is assigned after technical assessment.
A reported issue is not automatically confirmed.

No fixed response or remediation SLA is established
by this document.

## 6. Security Response Process

The intended response process is:

1. Receive the private vulnerability report.
2. Acknowledge and record the report.
3. Validate the reported behaviour in an authorized environment.
4. Determine affected components and severity.
5. Identify required containment and remediation.
6. Develop and test a corrective change.
7. Review the security impact of the proposed fix.
8. Publish a security advisory when appropriate.
9. Document remediation and relevant lessons learned.

Security incidents involving financial data, credentials,
or tenant isolation require priority assessment.

## 7. Identity and Access Security

The project security baseline includes:

- Multi-factor authentication for privileged users.
- Role-based access control.
- Service-to-service authentication.
- Short-lived credentials.
- Periodic access reviews.
- Privileged action logging.
- Least-privilege access.
- Secure account lifecycle management.

For multi-tenant operations:

- Every protected request must validate active company membership.
- Authorization must use company-scoped permissions.
- A company identifier supplied by a client is not proof
  of authorization.
- Beneficiary and payment records must be tenant-scoped.
- Cross-tenant access must be denied by default.
- Privileged cross-tenant operations must be explicitly
  authorized and audited.

Tenant isolation requirements are architectural targets
until implementation and security tests provide evidence.

## 8. Application and API Security

The application security baseline includes:

- Input validation and output encoding.
- SQL injection protection.
- CSRF protection where applicable.
- SSRF controls.
- Secure HTTP headers.
- Rate limiting.
- Dependency scanning.
- Secret scanning.
- Secure error handling.
- Authentication and authorization testing.
- API request validation.
- Protection against replay and duplicate requests.

Security-sensitive endpoints must enforce authorization
independently of frontend controls.

## 9. Financial Transaction Security

Financial transaction controls should include:

- Maker–Checker approval where required.
- Separation of duties.
- Transaction limits.
- Velocity checks.
- Duplicate payment detection.
- Idempotency controls.
- Suspicious activity escalation.
- Immutable accounting journal, when implemented.
- Independent reconciliation, when implemented.
- Auditability of payment lifecycle transitions.

An internal payment approval must not be interpreted as
proof of bank submission or settlement.

Mock and simulated adapter responses must not be represented
as real movement of funds.

## 10. Cryptographic Security

The cryptographic security baseline includes:

- TLS for protected communications.
- Approved key-management processes.
- Encryption at rest where applicable.
- Key rotation and revocation.
- Certificate lifecycle management.
- Secure cryptographic library maintenance.
- Post-quantum cryptography migration planning.

QKD and PQC are separate technologies with different
security responsibilities.

QKD does not perform payment processing or transfer funds.

The use of cryptographic algorithms in project documentation
does not establish that those algorithms have been deployed
in a production environment.

Production QKD or PQC claims require implementation evidence,
interoperability testing, key lifecycle controls,
and independent security validation.

## 11. Secrets and Sensitive Data

Contributors must never commit:

- Passwords.
- API keys and access tokens.
- Private keys and seed phrases.
- Database credentials.
- Production environment files.
- Bank portal credentials.
- Sensitive customer or beneficiary information.
- Unredacted financial transaction records.

Recommended controls:

- Use environment variables or an approved secrets manager.
- Keep `.env` files outside version control.
- Maintain an appropriate `.gitignore`.
- Rotate credentials if exposure is suspected.
- Revoke compromised credentials promptly.
- Redact sensitive information from logs and reports.
- Restrict backup access and protect backup archives.

Removing a secret from the latest commit does not guarantee
that it has been removed from Git history or other copies.

## 12. Operational Security and Incident Management

Operational security should include:

- Separation of duties.
- Production access approval.
- Change management.
- Incident management.
- Vulnerability management.
- Backup protection.
- Monitoring and alerting.
- Security event logging.
- Recovery procedures.
- Periodic security reviews.

Suspected compromise of production credentials or sensitive
financial records must be escalated to authorized maintainers
and the responsible system owner.

## 13. Compliance and Regulatory Considerations

Applicable regulatory and contractual obligations must be
assessed with qualified legal and compliance professionals.

Potentially relevant areas include:

- Bank Indonesia requirements.
- Otoritas Jasa Keuangan requirements.
- Indonesian personal data protection requirements.
- Payment system licensing.
- Anti-money laundering obligations.
- Counter-terrorism financing obligations.
- PCI DSS, where cardholder data is involved.
- Contractual banking and provider requirements.

The applicability of each requirement depends on the actual
business model, services, data processed, and legal entities
involved.

This repository policy is not a legal compliance certification
or regulatory authorization.

## 14. Security Testing Boundaries

Security testing must be conducted only against systems
for which the tester has explicit authorization.

Permitted project testing environments should be isolated
development, test, or staging environments.

Testing must not:

- Target bank production systems without authorization.
- Attempt unauthorized financial transactions.
- Access real customer accounts or funds.
- Extract or disclose confidential information.
- Disrupt third-party services.
- Bypass provider security controls.

Testing results must be documented with scope, methodology,
limitations, and evidence.

## 15. Security Status and Limitations

The following capabilities must not be assumed to be
production-ready solely because they are described
in this repository:

- Production tenant isolation.
- Production bank connectivity.
- Production financial settlement.
- Complete double-entry ledger implementation.
- Independent reconciliation.
- QKD deployment.
- PQC production deployment.
- Regulatory certification.
- Independent security certification.

Security claims must be supported by implementation,
testing, and review evidence.

## 16. Related Documentation

- `docs/12-security-compliance.md`
- `docs/25-cryptohost-integration-architecture.md`
- `README.md`

---

**Policy Version:** 1.0.0
**Review Status:** Initial repository security policy
**Last Updated:** 2026-11-11

