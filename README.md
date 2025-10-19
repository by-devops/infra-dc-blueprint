# infra-dc-blueprint

**Open Datacenter Architecture Blueprint — SoC/SoT, GitOps, RUP-compliant.**  
This repository provides a modular, idempotent infrastructure blueprint for on‑prem & hybrid DCs
covering pfSense (edge), Proxmox/K3s (compute), NetBox (SoT), Keycloak/Vault (identity & secrets),
DevOps (GitLab/Nexus/AWX), Observability, and more.

- **System of Configuration (SoC)**: small YAMLs driving everything (VLANs, WAN/VIPs, services, BOM).
- **Source of Truth (SoT)**: NetBox authoritative; validations + push/pull via AWX.
- **RUP alignment**: Vision, Use Cases, Design (per SOW topic), Test Plans, Deployment Runbooks.
- **Provisioning**: Cloud‑init & LXC templates for Proxmox; K3s manifests/Helm; VPS bootstrap.

## Topics (SOW merged by domain)

- `01_edge-pfsense/` — pfSense Core, IPv6, NAT/VIP, Rule Matrix, OTT policy
- `02_network-topology-switch/` — VLAN topology, Admin/OOB Switch, Wi‑Fi/mDNS/Casting
- `03_compute/` — Proxmox (cluster‑ready), K3s (LAB, staging, prod), VPS staging
- `04_identity-secrets/` — Keycloak SSO/MFA, Janitor, Vault & Vaultwarden
- `05_devops/` — GitLab, Nexus, AWX, CI/CD Matrix
- `06_data-services/` — Storage/Nextcloud, DB/Redis Matrix, Mail SoC, Print/Scan/Fax, FreePBX
- `07_observability/` — Logs/Metrics/Flows/SNMPv3, Grafana/Prometheus
- `08_netbox_sot_governance/` — NetBox bootstrap, Naming, Sync/Runbooks

> All documents remain **in English**, while collaboration can be in French.

## Quick start

1. Edit `soc/*.yml` with your environment data (domains, VLANs, WAN/VIPs, services, BOM).
2. Review each SOW topic under `sow/` and its **NetBox-Model**.
3. Use `runbooks/` to operate and test; AWX templates ensure idempotency.
4. (Optional) Use the provided GitHub topics for discoverability.

## License

Apache License 2.0 — see [LICENSE](LICENSE).

---

**Keywords / Topics**: proxmox, pfsense, k3s, kubernetes, netbox, keycloak, hashicorp‑vault, ansible,
devops, gitops, infrastructure‑as‑code, datacenter, observability, grafana, prometheus, wireguard,
traefik, unifi‑network, cloud‑init, homelab, blueprint
