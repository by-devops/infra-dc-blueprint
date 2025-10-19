# Project Charter (Vision) — RUP

## Mission
A modular, idempotent on‑prem & hybrid datacenter blueprint using SoC (configuration data)
and SoT (NetBox) to drive automated, testable deployments.

## Principles
- Separation of Concerns: **SoC** (YAML data) vs **SOW** (how) vs **Runbooks** (operate)
- **NetBox as SoT**: validators, webhooks, push/pull via AWX
- Idempotent automation (Ansible/AWX), reproducible artifacts (Helm/Compose)
- Security by default: least privilege, MFA/SSO, secrets in Vault

## Environments
- `lab`, `stg`, `prod` (promotion by image digest + values)

## Governance
- Change via PR + approvals
- Naming policy enforced in NetBox
- Versioning per topic (semantic)
