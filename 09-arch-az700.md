# AZ-700 Reference Architectures

> Canonical Azure networking patterns. Memorize the shapes.

## 1. Hub-and-spoke with Azure Firewall

```mermaid
flowchart TB
    OnPrem[On-premises]
    OnPrem -- VPN/ER --> GW[VPN/ER Gateway in hub]
    GW --> Hub[Hub VNet]
    Hub --> AFW[Azure Firewall]
    AFW --> Spoke1[Spoke 1: workload]
    AFW --> Spoke2[Spoke 2: workload]
    AFW --> Internet[Internet egress]
    Spoke1 -. peering .- Hub
    Spoke2 -. peering .- Hub
```

- Spokes UDR 0/0 -> firewall private IP.
- Hub gateway transit + spokes "use remote gateway".
- Inbound web traffic via App Gateway in front of AFW (DNAT) or via Front Door.

## 2. Virtual WAN with Secured Virtual Hub

```mermaid
flowchart TB
    Branches[Branch sites] -- VPN --> VWAN[Virtual WAN]
    HQ[HQ datacenter] -- ExpressRoute --> VWAN
    Users[Roaming users] -- P2S --> VWAN
    VWAN --> Hub1[Secured Virtual Hub region A]
    VWAN --> Hub2[Secured Virtual Hub region B]
    Hub1 --> Spokes1[Workload VNets A]
    Hub2 --> Spokes2[Workload VNets B]
    Hub1 -. routing intent .- Hub2
```

- Routing intent: "all internet via firewall" + "all private via firewall".
- Hub-to-hub transit handled by Microsoft.

## 3. Private Endpoint hub for PaaS

```mermaid
flowchart LR
    Spoke[App in spoke] --> PE[Private Endpoint]
    PE --> SQL[Azure SQL DB]
    Spoke --> DNS[Linked Private DNS zone]
    DNS --> PE
    OnPrem[On-prem app] -- via DNS Resolver --> DNS
```

- Centralize PEs in a hub VNet, link Private DNS zones to all spokes.
- DNS Private Resolver inbound endpoint serves on-prem DNS forwarders.

## 4. Global L7 with Front Door Premium + private origin

```mermaid
flowchart LR
    User[User] --> AFD[Front Door Premium / WAF]
    AFD -- Private Link --> AGW[App Gateway internal v2]
    AGW --> AKS[AKS / VMSS / App Service]
```

- Front Door Premium reaches internal App Gateway v2 via Private Link.
- WAF at edge; AppGw WAF disabled to avoid double rule hits.

## 5. Active-active VPN gateway with BGP

```mermaid
flowchart LR
    OnPrem[On-prem device] -- Tunnel 1 --> VGW1[VPN GW instance 1]
    OnPrem -- Tunnel 2 --> VGW2[VPN GW instance 2]
    VGW1 -- BGP --> Routes[Effective routes]
    VGW2 -- BGP --> Routes
```

- Two public IPs, two tunnels, two instances. BGP advertises routes from both.

---

[Master Index](00-MASTER-INDEX.md)
