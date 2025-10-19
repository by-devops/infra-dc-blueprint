# Naming Convention (NetBox‑aligned)

## Objects
- Site: `HOM`, `VPS-DE`
- Devices: `HOM-PFS-01`, `HOM-PVE-01`, `HOM-SWO-01`
- VLAN: `VL099-ADMIN`, `VL041-WIFI-GUEST`
- VM/Service: `svc-<name>-<env>-<nn>`
- Traefik router: `rt-<app>-<env>`
- DNS: `<app>.<env>.example.com`

## Tags
- `env:` `lab|stg|prod`
- `plane:` `mgmt|data`
- `wan:` `telenet|proximus|wg`
- `class:` `ott|gaming|cctv|iot`
- `role:` `fw|switch|pve|vm|ap|nas|pbs`

## NetBox Validation (examples)
- Regex for VLAN names: `^VL\d{{3}}-[A-Z0-9-]+$`
- Block invalid names on create/update
