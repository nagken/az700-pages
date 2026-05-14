# AZ-700 Extra Concepts

> Subtle distinctions that show up in exam wording.

## VPN vs ExpressRoute vs Virtual WAN

| Trait | VPN | ExpressRoute | Virtual WAN |
|---|---|---|---|
| Path | Internet | Private circuit | Microsoft backbone |
| Latency | Variable | Predictable | Predictable |
| Bandwidth ceiling | ~1.25 Gbps per tunnel | 10/100 Gbps (Direct) | Many circuits aggregated |
| Encryption | IPsec by default | None native; add IPsec or MACsec | Same as underlying transport |
| Best for | Branch, dev, low cost | Critical workloads, predictable | Many sites + central security |

## ExpressRoute peerings cheat

| Peering | What you reach |
|---|---|
| Private | Your VNets (IaaS) |
| Microsoft | Microsoft 365 + public Azure PaaS endpoints over private path |
| Public (deprecated) | Replaced by Microsoft peering |

## Standard vs Premium ER

| Capability | Standard | Premium |
|---|---|---|
| Cross-geo VNet connectivity | No | Yes |
| Route limit | 4000 | 10000 |
| Number of VNets | 10 | 100+ (varies by bandwidth) |
| Office 365 access | No | No (use Microsoft peering anyway) |

## Active-active VPN gateway

- Two gateway instances, two public IPs, two tunnels per device.
- Requires BGP. ASN cannot be 65515 (reserved by Azure).
- Provides ~2x throughput + faster failover.

## Hub VNet vs Virtual WAN hub

| Aspect | Hub VNet (you build) | Virtual WAN hub (managed) |
|---|---|---|
| Routing | UDR + NVA | Built-in route tables + routing intent |
| Firewall | Azure Firewall in hub VNet | Secured Virtual Hub |
| ER + VPN coexistence | Yes, design carefully | Native, all in hub |
| Cost model | Per resource | Per hub + per scale unit |

## Service Endpoint vs Private Endpoint

| Trait | Service Endpoint | Private Endpoint |
|---|---|---|
| Private IP in VNet? | No - subnet identity sent to PaaS | Yes - NIC in your subnet |
| Disables public path? | No (use storage firewall) | Yes (when public access disabled) |
| DNS impact | None | Need Private DNS zone |
| Cross-region | Limited | Yes |
| Cost | Free | Per PE per hour + bandwidth |

## NSG processing order

1. Subnet **inbound** rules (lowest priority # wins).
2. NIC **inbound** rules.
3. NIC **outbound** rules.
4. Subnet **outbound** rules.

If any layer denies, packet is dropped. Effective rules view collapses both.

## Azure Bastion SKUs

| SKU | Adds |
|---|---|
| Developer | Free, single VM, no scaling |
| Basic | Browser-based RDP/SSH |
| Standard | Native client, host scaling, IP-based connect, shareable link, file copy |
| Premium | Session recording, private-only deployment |

## NAT Gateway

- Recommended for **outbound** Internet from a subnet.
- Eliminates SNAT port exhaustion vs Load Balancer outbound rules.
- Attach to subnet; uses 1 or more Standard public IPs / public IP prefixes.

## VNet flow logs vs NSG flow logs

| Trait | NSG flow logs | VNet flow logs |
|---|---|---|
| Scope | NSG | VNet/subnet/NIC |
| Versions | v1 (legacy), v2 | New format |
| Required NSGs to capture? | Yes | **No** - works without NSG |
| Future | Retiring Sep 2027 | **Recommended** |

---

[Master Index](00-MASTER-INDEX.md)
