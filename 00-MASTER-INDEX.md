# AZ-700 - Designing and Implementing Microsoft Azure Networking Solutions - Visual Study Guide

> Concept-only study aid. No exam questions reproduced. Source PDF (if any) stays local + gitignored.

**Skills outline:** https://learn.microsoft.com/credentials/certifications/resources/study-guides/az-700

## Master mind map

```mermaid
mindmap
  root((AZ-700))
    Hybrid networking
      VPN Gateway
        Site-to-site IPsec
        Point-to-site
        Active-active
      ExpressRoute
        Private peering
        Microsoft peering
        FastPath
        Global Reach
      Virtual WAN
        Hub-and-spoke at scale
        Secure hub
    Core networking
      VNet design
        Address space
        Subnets
        Peering hub-spoke
      IP addressing
        Public IP SKUs
        Standard vs Basic
      Name resolution
        Azure DNS
        Private DNS zones
        DNS resolver
      VNet integration
        Service injection
        Delegated subnet
    Routing
      System routes
      User-defined routes UDR
      BGP propagation
      Azure Route Server
      Hub-and-spoke routing
      Virtual WAN routing
        Routing intent
        Custom route tables
      Load balancing
        Azure Load Balancer
        Application Gateway
        Front Door
        Traffic Manager
    Secure and monitor
      Azure Firewall
        Standard Premium Basic
        Firewall Policy
      NSG and ASG
      DDoS Protection
        Network IP plans
      Web Application Firewall
      Bastion
      Network Watcher
        Connection Monitor
        NSG flow logs
        VNet flow logs
        Topology
        Packet capture
    Private access
      Service Endpoints
      Private Endpoints
      Private Link Service
      VNet integration for PaaS
      Azure DNS integration
```

## Domain map

```mermaid
flowchart LR
    Master["AZ-700 Master Index"]
    D01["Hybrid networking"]
    Master --> D01
    D02["Core networking"]
    Master --> D02
    D03["Routing and load balancing"]
    Master --> D03
    D04["Secure and monitor"]
    Master --> D04
    D05["Private access"]
    Master --> D05
```

## Domain weights

```mermaid
pie showData
    title AZ-700 domain weights
    "Hybrid networking" : 15
    "Core networking" : 25
    "Routing" : 25
    "Secure and monitor" : 20
    "Private access" : 15
```

## Recommended study order

```mermaid
gantt
    title Suggested study plan
    dateFormat X
    axisFormat Day %d
    section Plan
    Core networking         :t1, 0, 3d
    Routing                 :t2, after t1, 3d
    Hybrid networking       :t3, after t2, 2d
    Secure and monitor      :t4, after t3, 2d
    Private access          :t5, after t4, 2d
    Cheatsheet and review   :t6, after t5, 1d
```

---

**Next:** open [01-hybrid-networking.md](01-hybrid-networking.md)
