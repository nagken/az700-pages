# AZ-700 Microsoft Learn Path Summaries

> Condensed take-aways from the official AZ-700 learning paths.

## Path 1: Design and implement core networking infrastructure

- Plan address space without overlap; reserve room for growth.
- Use VNet peering for same-region/same-tenant; AVNM for scale.
- Public IP Standard SKU is the default for any new design.
- Private DNS zones + linked VNets are how PaaS Private Endpoints become resolvable.

## Path 2: Design, implement, and manage hybrid networking

- Pick VPN for low-cost branch, ER for critical workloads, Virtual WAN for many sites.
- Active-active gateways + BGP + redundant on-prem devices = HA.
- ExpressRoute with private peering = best private path; FastPath if bypassing the ER gateway helps.
- Encryption over ER: IPsec inside Azure (VPN over ER) or MACsec on ER Direct.

## Path 3: Design and implement routing

- UDR + NSG together control traffic; UDR > BGP > system.
- Azure Route Server eliminates manual UDRs when NVAs participate in BGP.
- Hub-spoke patterns: spokes either go through hub firewall or directly to Internet (UDR decides).
- Choose load balancer by layer (L4 vs L7) and scope (regional vs global).

## Path 4: Secure and monitor networks

- Layered defense: NSG/ASG inside VNet, Azure Firewall at the boundary, WAF for L7 web, DDoS for L3/L4.
- Bastion replaces public RDP/SSH; pick SKU by feature need.
- VNet flow logs is the new standard - migrate away from NSG flow logs before deprecation.
- Connection Monitor is your synthetic probe + topology view.

## Path 5: Design and implement private access to Azure services

- Service Endpoints lock down PaaS firewall to a subnet; no private IP.
- Private Endpoint gives a private IP + need a Private DNS zone.
- Private Link Service lets you publish your own ILB-fronted service privately.
- Disable public network access on the PaaS resource to actually close the public path.

---

[Master Index](00-MASTER-INDEX.md)
