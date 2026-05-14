# AZ-700 Hands-On Labs

> Practical exercises to build muscle memory. All work in a free or pay-go subscription.

## Lab 1: Hub-spoke with VPN gateway

1. Create hub VNet `10.0.0.0/16`, GatewaySubnet `10.0.255.0/27`, AzureFirewallSubnet `10.0.1.0/26`.
2. Create spoke1 `10.1.0.0/16`, spoke2 `10.2.0.0/16`.
3. Peer hub<->spoke1 and hub<->spoke2 with `AllowGatewayTransit` (hub) + `UseRemoteGateways` (spokes).
4. Deploy VPN Gateway VpnGw2 with active-active and BGP.
5. Configure a simulated on-prem (another VNet + VPN GW or local lab) and bring up tunnels.
6. Verify with `az network vnet-gateway list-bgp-peer-status`.

## Lab 2: Private Endpoint + Private DNS

1. Create storage account `stdemo<suffix>`. Disable public network access.
2. Create Private Endpoint for `blob` sub-resource into spoke1.
3. Create Private DNS zone `privatelink.blob.core.windows.net`. Link to hub + spoke1.
4. From a VM in spoke1, `nslookup stdemo<suffix>.blob.core.windows.net` - should resolve to a 10.x IP.
5. Validate that public access from your laptop now fails.

## Lab 3: Azure Firewall + UDR

1. Deploy Azure Firewall Standard in hub `AzureFirewallSubnet`.
2. Create network rule: allow spoke1 -> Internet :443.
3. Create application rule: allow `*.microsoft.com` from spoke1.
4. Add UDR on spoke1 subnet: `0.0.0.0/0 -> firewall private IP`.
5. From spoke1 VM, `curl https://www.microsoft.com` -> succeeds; `curl https://example.com` blocked.
6. Inspect Firewall logs in Log Analytics.

## Lab 4: VNet flow logs + Traffic Analytics

1. Create a Log Analytics workspace.
2. Enable VNet flow logs on spoke1's VNet, target the workspace.
3. Generate traffic (Bastion in, curl out).
4. After 10 minutes, run KQL: `NTANetAnalytics | take 50`.
5. Open Traffic Analytics blade for visualizations.

## Lab 5: Application Gateway v2 with WAF

1. Deploy App Gateway v2 with WAF v2 (OWASP CRS 3.2) in front of two backend VMs.
2. Add a path-based rule: `/api/*` -> backend pool A; default -> backend pool B.
3. Add custom rule: rate-limit 100 req/min per client IP.
4. Run a known-bad request (e.g. `?id=' or 1=1 --`) and observe block in WAF logs.

## Lab 6: Private Link Service

1. Deploy a tiny web app on a VM behind a Standard Internal Load Balancer in your VNet.
2. Create a Private Link Service over the ILB.
3. From a separate subscription/VNet, create a Private Endpoint pointing at the Private Link Service alias.
4. Approve the connection on the producer side.
5. Verify the consumer can `curl` the service via the PE private IP.

---

[Master Index](00-MASTER-INDEX.md)
