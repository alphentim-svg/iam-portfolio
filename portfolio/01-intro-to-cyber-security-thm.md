md

**Doel**

Basisbegrippen uit offensive en defensive security begrijpen, en ze kunnen vertalen naar praktische stappen in een organisatie.

**In normale taal**

Cybersecurity gaat over het voorkomen, ontdekken en oplossen van misbruik van systemen. In **offensive security** probeer je als aanvaller te denken: je zoekt zwakke plekken en misconfiguraties om te zien wat er mis kan gaan. Een voorbeeld is het ontdekken van “verborgen” paden of pagina’s op een website door directory-zoekwerk (bijv. met dirb). **Defensive security** (blue team) richt zich juist op beschermen en snel reageren: activiteiten monitoren, verdachte signalen herkennen en incidenten afhandelen. Veel organisaties doen dit vanuit een **SOC**, waar analisten meldingen opvolgen en aanvallen onderzoeken. Hiervoor gebruiken ze vaak een **SIEM**, dat logs en alerts verzamelt zodat je sneller afwijkingen ziet. Belangrijke verdedigingsmiddelen zijn training van medewerkers, firewalls, intrusion detection en duidelijke security policies. In de praktijk draait het om vijf kerntaken: monitoren & detecteren, incident response, threat intelligence, vulnerability management en investigation/analysis.

**Stappen (praktisch)**

1. Bepaal wat je wil beschermen (accounts, apps, data) en welke logbronnen je nodig hebt.
2. Zet monitoring aan: verzamel relevante logs (auth/logins, netwerk, endpoints, apps).
3. Gebruik een SIEM om logs te centraliseren en detectieregels/alerts te bouwen.
4. Triage alerts: bepaal “false positive vs echte dreiging” met vaste checklist.
5. Reageer: account beveiligen/isoleren, oorzaak achterhalen, nazorg & verbeteractie vastleggen.

## **Checks / bewijs**

- Overzicht van logbronnen + retention (hoe lang bewaar je logs).
- Voorbeeld van SIEM-alert + opvolging in een ticket (tijdlijn, acties, conclusie).
- Policy die MFA/least privilege verplicht stelt + bewijs dat dit actief is.

## **Veelgemaakte fouten**

- Monitoring aanzetten zonder duidelijke “wat doen we bij een alert?” playbook.
- Te veel alerts (noise) waardoor echte signalen worden gemist.
- Uitzonderingen (bijv. MFA uit) zonder einddatum/approval en zonder logging.

**Mini-voorbeeld**

Een medewerker krijgt ’s nachts meerdere MFA-pushmeldingen zonder zelf in te loggen. In het SOC controleer je loginlogs en locatie/IP, reset je het wachtwoord na identiteitscheck en trek je actieve sessies in. Daarna check je mailbox rules en zet je extra monitoring aan. Alles leg je vast in een ticket als bewijs.
