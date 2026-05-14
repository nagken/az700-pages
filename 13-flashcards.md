# AZ-700 Flashcards

> Click any card to reveal the answer.

<section class="fc-section" data-fc-title="Hybrid networking">
<h2>1 - Hybrid networking</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">Cheapest hybrid connectivity over the Internet?</div><div class="fc-a"><strong>Site-to-site VPN</strong> (IPsec/IKEv2). Use route-based gateway.</div></div>

<div class="flashcard"><div class="fc-q">Predictable bandwidth + private path?</div><div class="fc-a"><strong>ExpressRoute</strong>. Private peering for VNets.</div></div>

<div class="flashcard"><div class="fc-q">Many branches, central management at scale?</div><div class="fc-a"><strong>Virtual WAN</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Connect two ER circuits in different geos?</div><div class="fc-a"><strong>ExpressRoute Global Reach</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Bypass the ER gateway data path for higher throughput?</div><div class="fc-a"><strong>FastPath</strong>.</div></div>

<div class="flashcard"><div class="fc-q">GatewaySubnet minimum size?</div><div class="fc-a"><strong>/27 or larger</strong>. No NSG.</div></div>

<div class="flashcard"><div class="fc-q">Encrypt ExpressRoute Direct at layer 2?</div><div class="fc-a"><strong>MACsec</strong>.</div></div>

</div>
</section>

<section class="fc-section" data-fc-title="Core networking">
<h2>2 - Core networking</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">Reserved IPs per subnet?</div><div class="fc-a"><strong>5</strong> (network, default GW, 2 DNS, broadcast).</div></div>

<div class="flashcard"><div class="fc-q">Subnet name for Azure Firewall?</div><div class="fc-a"><strong>AzureFirewallSubnet</strong> (/26).</div></div>

<div class="flashcard"><div class="fc-q">Auto-register VM A records in private DNS?</div><div class="fc-a">Enable <strong>auto-registration</strong> when linking the zone to the VNet.</div></div>

<div class="flashcard"><div class="fc-q">Connect two VNets across regions?</div><div class="fc-a"><strong>Global VNet peering</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Resolve PE FQDNs from on-premises?</div><div class="fc-a"><strong>DNS Private Resolver inbound endpoint</strong>; on-prem DNS forwards to its IP.</div></div>

<div class="flashcard"><div class="fc-q">Manage many VNets and rules declaratively?</div><div class="fc-a"><strong>Azure Virtual Network Manager (AVNM)</strong>.</div></div>

</div>
</section>

<section class="fc-section" data-fc-title="Routing">
<h2>3 - Routing</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">UDR vs BGP vs system - precedence?</div><div class="fc-a"><strong>UDR &gt; BGP &gt; system</strong>; tie-broken by longest prefix.</div></div>

<div class="flashcard"><div class="fc-q">NVA wants BGP into Azure routing?</div><div class="fc-a"><strong>Azure Route Server</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Force all spoke traffic through firewall?</div><div class="fc-a">UDR <code>0.0.0.0/0</code> -> Firewall private IP.</div></div>

<div class="flashcard"><div class="fc-q">Global L7 with WAF and edge cache?</div><div class="fc-a"><strong>Azure Front Door Premium</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Regional L7 with path-based routing + WAF?</div><div class="fc-a"><strong>Application Gateway v2 + WAF v2</strong>.</div></div>

<div class="flashcard"><div class="fc-q">DNS-based global routing?</div><div class="fc-a"><strong>Traffic Manager</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Outbound SNAT without exhaustion?</div><div class="fc-a"><strong>NAT Gateway</strong> on the subnet.</div></div>

</div>
</section>

<section class="fc-section" data-fc-title="Secure & monitor">
<h2>4 - Secure & monitor</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">FQDN filtering + IDPS + TLS inspection?</div><div class="fc-a"><strong>Azure Firewall Premium</strong>.</div></div>

<div class="flashcard"><div class="fc-q">L3/L4 volumetric attack defense?</div><div class="fc-a"><strong>DDoS Protection</strong> (Network or IP plan).</div></div>

<div class="flashcard"><div class="fc-q">L7 SQLi/XSS protection on web app?</div><div class="fc-a"><strong>WAF</strong> on App Gateway or Front Door.</div></div>

<div class="flashcard"><div class="fc-q">RDP/SSH without exposing public IP on VM?</div><div class="fc-a"><strong>Azure Bastion</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Recommended flow log technology?</div><div class="fc-a"><strong>VNet flow logs</strong> (NSG flow logs are retiring).</div></div>

<div class="flashcard"><div class="fc-q">Verify a NIC's effective routes?</div><div class="fc-a">Network Watcher <strong>Effective Routes</strong>.</div></div>

</div>
</section>

<section class="fc-section" data-fc-title="Private access">
<h2>5 - Private access</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">Private IP for PaaS inside your VNet?</div><div class="fc-a"><strong>Private Endpoint</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Lock storage to a subnet, no DNS changes?</div><div class="fc-a"><strong>Service Endpoint</strong> + storage firewall.</div></div>

<div class="flashcard"><div class="fc-q">Expose your own ILB-backed service privately to others?</div><div class="fc-a"><strong>Private Link Service</strong>.</div></div>

<div class="flashcard"><div class="fc-q">PE works but client still resolves public IP?</div><div class="fc-a">Missing <strong>Private DNS zone</strong> link to VNet.</div></div>

<div class="flashcard"><div class="fc-q">Disable public path on PaaS resource?</div><div class="fc-a">Set <strong>publicNetworkAccess = Disabled</strong> on the resource.</div></div>

</div>
</section>

---

[Master Index](00-MASTER-INDEX.md)
