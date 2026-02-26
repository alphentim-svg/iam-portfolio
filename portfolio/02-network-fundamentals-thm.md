# 02 - Network Fundamentals (THM) — Room: What is Networking?

## TL;DR
- Een netwerk is een set apparaten die met elkaar verbonden zijn om data te delen.
- Apparaten identificeren zich o.a. met een **IP-adres** (logisch adres) en **MAC-adres** (hardware-adres).
- `ping` test bereikbaarheid en gebruikt **ICMP**.

## Key concepts
- **Netwerk:** apparaten die verbonden zijn (bijv. thuisnetwerk, bedrijfsnetwerk).
- **Internet vs Web:** het internet is de onderliggende netwerk-infrastructuur; **Tim Berners-Lee** bedacht het **World Wide Web** (WWW).
- **IP-adres (Internet Protocol):** logisch adres om apparaten te bereiken.
- **Public IP:** zichtbaar op het internet; meestal toegewezen door je **ISP**.
- **Private IP:** intern adres binnen je LAN (thuis/bedrijf) om apparaten onderling te identificeren.
- **MAC-adres:** hardware-adres van een netwerkkaart; meestal weergegeven als **12 hex-tekens** (bijv. `AA:BB:CC:DD:EE:FF`).
- **Octet:** elke “groep” in een IPv4-adres (bijv. in `192.168.1.10` zijn dat 4 octets).
- **ICMP:** protocol voor netwerkdiagnose (o.a. gebruikt door `ping`).
- **Ping:** stuurt ICMP echo requests om te checken of een host bereikbaar is en hoe snel.
- **Syntax:** `ping x.x.x.x`

## Commands used
- `ping x.x.x.x`

## Mini diagram (simpel)
Device (private IP + MAC) → Router (NAT) → Internet (public IP)

## In het echt (logging/alerts)
- Veel ICMP/ping verkeer kan wijzen op **reconnaissance** (verkennen van hosts).
- IP/MAC relaties zie je terug in DHCP/ARP logs (handig bij incidenten: “welk device hoorde bij dit IP?”).
- Public vs private IP helpt bij triage: “is dit verkeer intern of van buiten?”

## Common mistakes
- “Tim Berners-Lee heeft het internet uitgevonden” → hij bedacht vooral het **World Wide Web**.
- IP-adres en MAC-adres door elkaar halen: IP kan veranderen; MAC is gekoppeld aan de netwerkkaart.
- Denken dat ping altijd werkt: ICMP kan geblokkeerd zijn door firewalls (dus “geen ping” ≠ “down”).

## Room: Intro to LAN

### TL;DR
- **Topology** beschrijft hoe een netwerk fysiek/logisch is opgebouwd (star/bus/ring).
- **Switches** sturen verkeer efficiënt door op basis van MAC-adressen (beter dan hubs).
- LAN-bouwstenen zoals **subnetting, ARP en DHCP** bepalen hoe apparaten elkaar vinden en IP’s krijgen.

### Key concepts
- **LAN (Local Area Network):** een lokaal netwerk binnen één locatie (thuis/bedrijf).
- **Topology:** hoe apparaten onderling verbonden zijn.
  - **Star topology:** meest voorkomend; apparaten hangen aan een centraal punt (switch/router). Valt het centrale punt uit, dan ligt (bijna) alles plat.
  - **Bus topology:** één backbone-kabel; goedkoop maar storingsgevoelig (kabelbreuk/te veel verkeer = problemen voor iedereen).
  - **Ring / token topology:** verkeer gaat rond in een ring; relatief weinig kabels, maar een breuk kan de hele ring raken.
- **Switch:** verbindt apparaten binnen een LAN (Ethernet) en leert welke **MAC** op welke poort zit → gericht doorsturen.
- **Router:** verbindt **netwerken** met elkaar en routeert verkeer tussen netwerken (bijv. LAN ↔ internet).
- **Subnetting:** verdelen van een netwerk in kleinere delen via **subnet mask/CIDR** (bijv. /24, /26) voor controle, efficiëntie en security-segmentatie.
- **Subnet mask:** bepaalt welk deel netwerk vs host is (IPv4 = 32 bits = 4 bytes; elk “octet” 0–255).
- **Network address:** het “beginadres” dat het netwerk zelf identificeert (geen host).
- **ARP (Address Resolution Protocol):** vertaalt **IP → MAC** binnen hetzelfde LAN via ARP request/reply; resultaten komen in de ARP cache.
- **DHCP:** deelt automatisch IP-config uit (IP, gateway, DNS). Flow: **Discover → Offer → Request → ACK**.

### In het echt (security link)
- Topology + segmentatie (subnetting/VLANs) bepalen hoe snel een aanvaller lateraal kan bewegen.
- ARP is misbruikbaar (ARP spoofing/poisoning) → kan leiden tot man-in-the-middle binnen een LAN.
- DHCP misconfig of rogue DHCP server kan verkeer omleiden (slechte gateway/DNS) → phishing/malware risico.

### Common mistakes
- Denken dat subnetting “altijd” over het laatste octet gaat; het draait om het subnet mask/CIDR.
- Switch en router verwarren: switch = binnen LAN, router = tussen netwerken.
- “Geen IP, dus kapot”: vaak is DHCP het probleem (of verkeerde VLAN/poort).
