# Case 01 — Verdachte MFA prompts (eerste triage)

## Context (wie, wat, waarom) — max 3 regels
- Gebruiker meldt: “Ik krijg MFA pushmeldingen terwijl ik niet inlog.”
- Tijdstip: ’s nachts; verwachte locatie gebruiker: NL.
- Vermoeden: mogelijke credential compromise + **MFA push fatigue** poging.

## Risico (wat kan er misgaan)
- Account takeover met toegang tot e-mail en SSO-apps.
- Persistence via mailbox rules/forwarding of OAuth app-consents.
- Laterale beweging naar andere systemen als SSO breed gekoppeld is.

## Triage verdict (voorlopig)
- **Verdict:** Suspicious (waarschijnlijk MFA push fatigue / credential compromise)
- **Severity:** Medium (→ High bij bewijs van mailbox rules/OAuth consent of succesvolle login vanaf afwijkende locatie)
- **Confidence:** Medium (totdat sign-in logs + device info bevestigd zijn)

## Actieplan (stappen)
1. **Identiteit verifiëren** via alternatieve verificatie (voordat je resets uitvoert).
2. **Containment (direct):** password reset + **revoke sessions/tokens** + MFA reset/re-enroll.
3. **Logcheck:** laatste succesvolle logins, failed attempts, IP/geo, device info, “impossible travel”.
4. **Mailbox/OAuth check:** forwarding, rules, inbox rules, nieuwe OAuth app-consents (indien van toepassing).
5. **Communicatie:** gebruiker instrueren (nooit “Approve” klikken), korte phishing-checklist.
6. **Nazorg:** extra monitoring 7 dagen + access review op gevoelige rechten.

## Benodigde info (wat móet je weten)
- [ ] Exact tijdstip(s) van MFA prompts + screenshots (indien mogelijk).
- [ ] Is er (recent) ingelogd op een **nieuw device** of via een onbekende browser?
- [ ] Heeft gebruiker op links geklikt of credentials ingevuld op een verdachte pagina?
- [ ] Welke kritieke accounts/apps hangen aan SSO? (impact inschatten)

## Beslissing (least privilege)
- Tijdelijk blokkeren of **step-up MFA/conditional access** afdwingen totdat oorzaak duidelijk is.
- Geen MFA-uitzonderingen; liever zekerheid verhogen (bijv. number matching / phishing-resistant MFA waar mogelijk).

## Bewijs (wat sla je op)
- Export/screenshot van sign-in events + MFA events.
- Ticketlog met acties (password reset, sessions revoked, MFA reset) + communicatie met gebruiker/manager.
- Resultaat mailbox/OAuth checks (rules/forwarding/consents).

### Voorbeeld (fictief) indicatoren die escalatie triggeren
- Succesvolle login vanaf afwijkende geo + 10+ MFA prompts in minuten + nieuw device → escaleren naar (mogelijk) confirmed compromise.

## Nazorg (review/follow-up)
- Follow-up na 48 uur en na 7 dagen: nog prompts/verdachte activiteit?
- Overweeg awareness: korte training of phishing-simulatie aanbevelen.
