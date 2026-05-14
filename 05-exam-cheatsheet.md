# AZ-700 Exam Decision Reference

> Fast lookup table by problem wording. Use during review.

## Hybrid connectivity

| Wording | Pick |
|---|---|
| "encrypted tunnel over Internet to Azure" | Site-to-site VPN |
| "private predictable circuit" | ExpressRoute |
| "many branches, central management" | Virtual WAN |
| "remote roaming users" | Point-to-site VPN |
| "connect 2 ER circuits in different geos" | Global Reach |
| "bypass ER gateway for line-rate VM" | FastPath |
| "encrypt over ER private peering" | IPsec inside Azure or MACsec on ER Direct |

## Core networking

| Wording | Pick |
|---|---|
| "two VNets same region" | VNet peering |
| "two VNets different regions" | Global VNet peering |
| "100s of VNets, declarative config" | Azure Virtual Network Manager |
| "name resolution across on-prem and Azure" | DNS Private Resolver |
| "auto-register VM in private zone" | Private DNS zone with auto-registration |

## Routing

| Wording | Pick |
|---|---|
| "force all spoke egress through firewall" | UDR 0/0 -> firewall private IP |
| "stop spokes learning on-prem routes via gateway" | Disable BGP propagation on subnet |
| "automate NVA route injection" | Azure Route Server |
| "global L7 routing + WAF + caching" | Front Door (Premium) |
| "regional L7, WAF, path-based" | Application Gateway v2 + WAF |
| "regional L4 zone-redundant" | Standard Azure Load Balancer |
| "DNS-based geo or priority" | Traffic Manager |

## Secure & monitor

| Wording | Pick |
|---|---|
| "stateful FW with FQDN, IDPS, TLS inspect" | Azure Firewall Premium |
| "many firewalls central policy" | Azure Firewall Manager |
| "L3/L4 volumetric attack" | DDoS Protection (Network or IP plan) |
| "L7 SQLi/XSS protection on web app" | WAF on App Gateway or Front Door |
| "RDP/SSH without public IP" | Azure Bastion |
| "long-term flow telemetry" | VNet flow logs |
| "verify TCP/UDP allowed" | Network Watcher IP flow verify |
| "see next hop for a NIC" | Network Watcher next hop |

## Private access

| Wording | Pick |
|---|---|
| "lock storage to specific subnet" | Service endpoint + storage firewall |
| "private IP for SQL inside VNet" | Private Endpoint |
| "expose your own service privately to customers" | Private Link Service |
| "PE works but clients still hit public IP" | Missing Private DNS zone link |
| "on-prem clients resolve PE FQDN" | DNS Private Resolver inbound endpoint |

## Common gotchas to memorize

- GatewaySubnet must be /27 or larger; **no NSG on it**.
- AzureBastionSubnet /26 minimum (was /27, raised).
- Public IP Basic SKU retired Sep 2025 - use Standard.
- Azure Firewall requires Standard SKU public IPs.
- Most-specific UDR wins; UDR > BGP > system.
- BGP propagation on the firewall subnet causes asymmetric routing.

---

[Master Index](00-MASTER-INDEX.md)
