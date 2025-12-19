# Bilag 01a – Risikomatrice for sikkerhedsrelateret teknisk gæld  
## (GDPR og sundhedsdata)

**Relateret case:** Sikkerhedsrelateret teknisk gæld i et system til kritisk infrastruktur  
**Formål:**  
Dette bilag udvider den generelle risikomatrice med en konsekvensvurdering, der er specifikt rettet mod behandling af sundhedsdata og kravene i GDPR. Formålet er at gøre regulatoriske, driftsmæssige og tillidsmæssige konsekvenser tydelige i prioriteringsarbejdet.

---

## 1. Anvendelseskontekst

Matricen er tiltænkt systemer, der:

- behandler personoplysninger om helbred (GDPR art. 9)  
- indgår i eller understøtter kritisk infrastruktur  
- er i drift og videreudvikles løbende  

Matricen understøtter dialog mellem udvikling, ledelse, compliance og evt. DPO.

---

## 2. Sandsynlighed (Likelihood)

| Niveau | Beskrivelse |
|------|-------------|
| Lav | Kræver usandsynlige forudsætninger eller sjældne kombinationer af fejl |
| Middel | Kan forventes at forekomme over tid, fx ved kendte sårbarheder |
| Høj | Forventelig hændelse, gentagende svaghed eller kendt angrebsflade |

---

## 3. Konsekvens (Impact – GDPR og sundhedsdata)

Konsekvens vurderes ud fra **juridiske, organisatoriske og samfundsmæssige effekter**.

### Lav konsekvens

- Ingen eller meget begrænset påvirkning af personoplysninger  
- Ingen brud på fortrolighed, integritet eller tilgængelighed  
- Ingen underretningspligt  
- Ingen væsentlig påvirkning af borgeres eller brugeres tillid  

---

### Middel konsekvens

- Begrænset brud på fortrolighed eller integritet af sundhedsdata  
- Krav om intern hændelseshåndtering og dokumentation  
- Potentiel anmeldelse til Datatilsynet  
- Midlertidig driftsforstyrrelse eller funktionsnedsættelse  
- Risiko for negativ omtale eller tab af tillid  

---

### Høj konsekvens

- Brud på fortrolighed af særligt følsomme sundhedsdata (GDPR art. 9)  
- Pligt til anmeldelse til Datatilsynet og underretning af registrerede  
- Risiko for betydelige administrative bøder  
- Alvorlig påvirkning af drift i kritisk infrastruktur  
- Betydelig skade på tillid, omdømme og samarbejdsrelationer  

---

## 4. Risikomatrix (GDPR-fokuseret)

| Konsekvens \\ Sandsynlighed | Lav | Middel | Høj |
|----------------------------|-----|--------|-----|
| **Lav**    | Lav risiko | Lav–middel risiko | Middel risiko |
| **Middel** | Lav–middel risiko | Middel risiko | Høj risiko |
| **Høj**    | Middel risiko | Høj risiko | Kritisk risiko |

---

## 5. Eksempler på sikkerhedsrelateret teknisk gæld (GDPR-perspektiv)

| Område | Beskrivelse | Sandsynlighed | Konsekvens | Samlet risiko |
|------|-------------|---------------|------------|---------------|
| Adgangsstyring | Utilstrækkelig rolleopdeling ved adgang til sundhedsdata | Middel | Høj | Høj |
| Logning | Manglende revisionsspor for adgang til personoplysninger | Middel | Middel | Middel |
| Kryptering | Manglende eller forældet kryptering af data i hvile | Lav–middel | Høj | Middel–høj |
| Sletning | Uklar eller inkonsistent håndtering af slettefrister | Høj | Middel | Høj |
| Leverandører | Manglende overblik over underdatabehandlere | Middel | Høj | Høj |

---

## 6. Prioriteringsanbefalinger (GDPR-kontekst)

Når systemet behandler sundhedsdata, bør følgende vægte tungt:

1. Risici med **høj konsekvens** bør altid prioriteres, uanset sandsynlighed  
2. Forhold med potentiel **underretningspligt** bør adresseres tidligt  
3. Forbedringer, der styrker dokumentation og sporbarhed, giver ofte stor effekt  
4. Accepteret risiko skal være **eksplicit besluttet og dokumenteret**  

Dette reducerer både teknisk, juridisk og organisatorisk usikkerhed.

---

## 7. Ledelsesmæssig refleksion

I GDPR-kontekst er spørgsmålet sjældent *om* der er risiko, men:

- om virksomheden kan dokumentere, at risikoen er kendt  
- om der er truffet informerede beslutninger  
- om der arbejdes systematisk med risikoreduktion  

Manglende prioritering kan i sig selv udgøre et problem ved tilsyn.

---

## 8. Konklusion

Denne risikomatrice understøtter en praksis, hvor sikkerhedsrelateret teknisk gæld behandles som en forretnings- og ledelsesopgave – ikke kun som et teknisk problem. Ved at koble risiko direkte til GDPR og sundhedsdata bliver konsekvenserne tydelige og beslutningsgrundlaget styrket.

---

> **Note:**  
> Matricen er et støtteværktøj og erstatter ikke en fuld DPIA, men kan fungere som forberedelse og løbende opfølgning.
