# AZ-700 Pitfalls

> Mistakes that cost points and outage tickets.

## Address space

- Overlapping CIDR with on-prem - peering refused or blackholes.
- Sub-/29 subnets - Azure reserves 5 IPs, /29 has only 3 usable.
- Re-using same address range across spokes - peering technically works, routing breaks.

## Gateways

- NSG on `GatewaySubnet` - blocks management traffic, gateway flaps.
- Basic SKU VPN gateway in production - no SLA, no zone redundancy, no active-active.
- Mixing route-based and policy-based connections on the same gateway.

## ExpressRoute

- One circuit, one peering location - single point of failure. Use 2 circuits in different peering locations.
- Standard ER + cross-region VNets - need Premium add-on.
- FastPath enabled but custom UDRs intercept - FastPath silently bypasses, asymmetric routing.

## VNet peering

- Forgetting `AllowGatewayTransit` (hub) + `UseRemoteGateways` (spoke).
- Peering is non-transitive - hub-to-spoke + spoke-to-spoke does not exist without firewall/NVA.
- Service link reservations - cannot delete a subnet that hosts an injected service without removing the resource first.

## Routing

- Most-specific route wins - your UDR `10.0.0.0/8 -> NVA` is overridden by `10.0.1.0/24 -> Internet`.
- BGP propagation enabled on AzureFirewallSubnet - asymmetric routing.
- Adding UDR to AzureBastionSubnet - breaks Bastion control plane connectivity.

## Firewall and security

- Azure Firewall + Basic SKU public IPs - rejected. Need Standard.
- WAF in Detection mode forever - only prevents if Prevention mode.
- DDoS Network plan billed even with no traffic - consider IP Protection per-IP for small estates.
- TLS inspection on Azure Firewall Premium without Key Vault + managed identity correctly configured.

## DNS

- Private Endpoint without Private DNS zone link - clients still resolve public IP.
- Multiple PEs sharing one zone in different VNets - careful with auto-registration order.
- DNS Private Resolver outbound endpoint without forwarding rules - nothing forwards.

## Monitoring

- Connection Monitor (Classic) still in use - migrate to Connection Monitor.
- NSG flow logs without Traffic Analytics - lots of JSON, no insight.
- Sticking with NSG flow logs after VNet flow logs GA - missing future-proofed feature.

## Private access

- Service Endpoint + storage firewall + on-prem caller - on-prem must use ER/VPN; SE only applies to VNet subnets.
- PE created but PaaS public network access still enabled - "private" only in name.
- Private Link Service alias not approved on consumer side - PE stuck in pending.

---

[Master Index](00-MASTER-INDEX.md)
