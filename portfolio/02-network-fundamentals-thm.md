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
