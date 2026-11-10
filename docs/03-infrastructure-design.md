# 03 - INFRASTRUCTURE DESIGN

## 1. Development Environment

Recommended local development:

- Ubuntu 22.04 or later
- Python 3.12+
- FastAPI
- PostgreSQL
- Redis
- Docker and Docker Compose
- Git
- pytest
- Ruff
- OpenAPI
- Nginx or equivalent reverse proxy

Versions must be pinned and tested before deployment.

## 2. Environment Separation

Development:
- Local Docker environment.
- Synthetic customer data.
- Mock bank connector.

Testing:
- Automated integration tests.
- Isolated test database.
- Provider sandbox when available.

Staging:
- Production-like infrastructure.
- Restricted access.
- Synthetic or approved test data.

Production:
- Approved hosting.
- Hardened infrastructure.
- Managed secrets.
- Backup and disaster recovery.
- Monitoring and incident response.

## 3. Suggested Server Topology

Initial pilot:

1. Reverse proxy
2. Backend application
3. PostgreSQL
4. Background worker
5. Monitoring agent

Production expansion:

1. Redundant application instances
2. Private database subnet
3. Managed PostgreSQL with backups
4. Message broker
5. Centralized log storage
6. Secrets manager or KMS
7. WAF and DDoS protection
8. Separate administration access
9. Disaster recovery environment

## 4. Network Zones

PUBLIC:
- HTTPS ingress only.

APPLICATION:
- API and worker services.

DATA:
- Database and message broker.

SECURITY:
- Secrets management and key services.

ADMIN:
- Restricted operational access.

## 5. Network Security

- Do not expose PostgreSQL publicly.
- Restrict administrative ports.
- Use SSH keys and MFA.
- Apply firewall allowlists where appropriate.
- Enforce TLS.
- Rotate credentials.
- Maintain network access logs.

## 6. Infrastructure Sizing

Do not purchase large infrastructure before load testing.

Start with a small non-production environment and benchmark:

- CPU utilization
- Memory utilization
- Database connections
- Disk IOPS
- Network throughput
- API latency
- Queue backlog

Scale based on measured workload.
