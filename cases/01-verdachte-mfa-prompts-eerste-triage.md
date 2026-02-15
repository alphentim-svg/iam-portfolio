**Ticket titel**

01 - Verdachte MFA prompts - eerste triage

## **Context (wie, wat, waarom) – max 3 regels**

- Gebruiker meldt: “Ik krijg MFA pushmeldingen terwijl ik niet inlog.”
- Tijdstip: ’s nachts, locatie gebruiker: NL.
- Risico: iemand heeft wachtwoord en probeert MFA te omzeilen (“MFA fatigue”).

## **Risico (wat kan er misgaan)**

- Account takeover met toegang tot mail/SSO-apps.
- Aanvaller zet mailbox forwarding/rules om data weg te sluizen.
- Laterale beweging naar andere systemen als SSO breed is.

**Actieplan (stappen)**

1. **Identiteit verifiëren** (alternate verification) voordat je resets uitvoert.
2. **Containment:** force password reset + sessies/token intrekken + MFA reset/re-enroll.
3. **Logcheck:** laatste succesvolle logins, failed attempts, IP/geo, device info.
4. **Mailbox check:** forwarding, rules, nieuwe OAuth app-consents (als relevant).
5. **Communicatie:** gebruiker instrueren (nooit “Approve” klikken), phishing-checklist.
6. **Nazorg:** extra monitoring 7 dagen + access review op gevoelige rechten.

## **Benodigde info (wat móet je weten vóór je toegang geeft?)**

- Exact tijdstip(s) van MFA prompts + screenshots (indien mogelijk).
- Heeft gebruiker ergens ingelogd op nieuw device? Klikte hij op links?
- Welke accounts/apps hangen aan SSO? (impact inschatten)

## **Beslissing (least privilege)**

- Tijdelijke blokkade of strengere policy totdat oorzaak duidelijk is.
- Geen MFA-uitzonderingen; eerder verhogen van zekerheid (step-up MFA).

## **Bewijs (wat sla je op?)**

- Export/screenshot van login events + MFA events.
- Ticketlog met acties (reset/sessies ingetrokken) en manager/user communicatie.
- Check-resultaat mailbox rules/forwarding.

## **Nazorg (review/follow-up)**

- Follow-up na 48 uur en 7 dagen: nog prompts/verdachte activiteit?
- Eventueel awareness: korte training of phishing-simulatie aanbevelen.
