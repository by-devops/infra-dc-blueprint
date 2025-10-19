# SOW — Edge & pfSense (Merged Topic)
## Dependencies
- SoC: `network.vlans.yml`, `edge.wan.yml`, `firewall.aliases.yml`, `firewall.rules.yml`
- SoT: NetBox (Sites, VLANs, Prefixes, Devices, Circuits)

## Scope
Single L3 gateway & policy engine with dual‑WAN, IPv4 NAT44, IPv6 /48 (no NAT66), VIP publishing (Traefik), WG VPN, DNS/DoT enforcement, policy routing (Guest/Labs/Gaming/OTT).

## Deliverables
- Base config (WANs, VIPs, gateways), VLAN interfaces (/24 v4, /64 v6), RA/DHCPv6 Assisted
- Interface Groups, baseline allows (DNS/NTP/OBS), per‑VLAN rules (DNS redirect, DoH/DoT blocks, mDNS via gateway)
- Policy routing + kill‑switch for Guest/OTT
- NAT/port‑fw VIP→Traefik, AAAA direct to Traefik
- Runbook (outage access, backup/restore)

## Acceptance
- Dual‑stack where allowed; explicit v6 block elsewhere
- DNS enforcement; publishing A/AAAA working; policy routing per VLAN; WG users scoped
- Readbacks to SoT (leases/ARP/GW) nightly; drift=0

## NetBox Model
- Objects: Site, Device (pfSense), Interfaces (WANs + VLANs), VLANs, Prefixes v4/v6, IPs, Circuits
- Tags: env/plane/wan/role
- Custom fields: vip_ipv4_map (JSON), ipv6_prefix_root, dns_policy, egress_path, wg_user_scope

## Test Plan (scripts)
- precheck.sh → validate SoC presence & NetBox base objects
- apply.sh → AWX job `pfSense_core_apply` (idempotent)
- verify.sh → dig A/AAAA Traefik, guest kill‑switch, DNS redirect, admin IPv6 reach
- readback.sh → AWX job `pfSense_readback_to_NetBox`
