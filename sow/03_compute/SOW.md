# SOW — Compute (Proxmox, K3s, VPS)
## Scope
Proxmox (cluster‑ready single node), K3s LAB (Traefik/MetalLB/External‑Secrets), VPS staging (Traefik + WG).

## Deliverables
- Proxmox bridges/templates/PBS; K3s single node; VPS dual‑stack
- Provisioning from `soc/sizing.bom.yml` (cloud‑init/LXC templates)

## Acceptance
- VM backup/restore OK; k3s whoami OK; VPS AAAA Traefik OK
