# AZ-700 Glossary

| Term | Definition |
|---|---|
| **VNet** | Virtual Network - isolated address space in Azure. |
| **Subnet** | CIDR block inside a VNet hosting NICs. |
| **NSG** | Network Security Group - stateful 5-tuple ACL on subnet/NIC. |
| **ASG** | Application Security Group - logical grouping of NICs for NSG rules. |
| **UDR** | User-Defined Route - custom route table attached to a subnet. |
| **BGP** | Border Gateway Protocol - dynamic routing exchange. |
| **Service tag** | Microsoft-managed alias for groups of IPs (e.g. AzureLoadBalancer, Storage). |
| **Hub-spoke** | Topology: central hub VNet with shared services peered to workload spokes. |
| **VNet peering** | Direct private connection between two VNets, non-transitive. |
| **GatewaySubnet** | Reserved subnet for VPN/ER gateways. |
| **VPN Gateway** | Site-to-site / point-to-site IPsec gateway. |
| **ExpressRoute** | Private dedicated circuit to Azure via partner. |
| **Virtual WAN** | Managed hub-and-spoke fabric. |
| **Global Reach** | ExpressRoute feature linking circuits across geos. |
| **FastPath** | ER feature that bypasses the ER Gateway on the data path. |
| **Azure Firewall** | Stateful managed L3/L7 firewall service. |
| **Firewall Manager** | Central policy management for Firewalls and Secured Hubs. |
| **DDoS Protection** | L3/L4 volumetric attack mitigation. |
| **WAF** | Web Application Firewall (App Gateway or Front Door). |
| **Application Gateway** | Regional L7 load balancer with WAF v2. |
| **Front Door** | Global L7 load balancer with WAF, anycast, caching. |
| **Traffic Manager** | DNS-based global routing. |
| **Azure Load Balancer** | Regional L4 load balancer (Standard SKU). |
| **NAT Gateway** | Subnet-scoped outbound SNAT service. |
| **Bastion** | Browser-based RDP/SSH without public IP on the VM. |
| **Network Watcher** | Diagnostics + monitoring suite for Azure networking. |
| **Connection Monitor** | Synthetic-probe-based connectivity testing. |
| **VNet flow logs** | Modern flow log capture; replaces NSG flow logs. |
| **Service Endpoint** | Subnet-aware path to a PaaS public endpoint over backbone. |
| **Private Endpoint** | NIC in your subnet mapped to a PaaS resource via Private Link. |
| **Private Link Service** | Publish your own ILB-backed service for private consumption. |
| **Private DNS zone** | Internal DNS zone linked to one or more VNets. |
| **DNS Private Resolver** | PaaS inbound/outbound DNS resolver inside VNet. |
| **AVNM** | Azure Virtual Network Manager - declarative connectivity + security at scale. |
| **Routing intent** | Virtual WAN feature: declare inspect-internet / inspect-private. |
| **MACsec** | Layer 2 encryption on ExpressRoute Direct ports. |

---

[Master Index](00-MASTER-INDEX.md)
