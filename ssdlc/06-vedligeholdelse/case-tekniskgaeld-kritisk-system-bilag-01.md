# Bilag 01 – Risikomatrice for sikkerhedsrelateret teknisk gæld

**Relateret case:** Sikkerhedsrelateret teknisk gæld i et system til kritisk infrastruktur  
**Formål:**  
Dette bilag understøtter casen ved at give et konkret værktøj til at identificere, vurdere og prioritere sikkerhedsrelateret teknisk gæld i systemer, der indgår i kritisk infrastruktur og behandler sundhedsdata.

---

## 1. Formål og anvendelse

Risikomatricen har til formål at:

- skabe et fælles sprog mellem udvikling, ledelse og forretning  
- synliggøre konsekvenserne af ikke at handle  
- understøtte prioritering af sikkerhedsarbejde i vedligeholdelsesfasen  

Matricen er ikke tænkt som en fuld risikovurdering, men som et **praktisk beslutningsværktøj**, der kan anvendes iterativt.

---

## 2. Risikodimensioner

### Sandsynlighed (Likelihood)

| Niveau | Beskrivelse |
|------|-------------|
| Lav | Kræver særlige forudsætninger eller sjældne hændelser |
| Middel | Kan forventes at forekomme over tid |
| Høj | Forventelig eller gentagende hændelse |

### Konsekvens (Impact)

Ved systemer til kritisk infrastruktur og sundhedsdata bør konsekvens vurderes bredt:

| Niveau | Beskrivelse |
|------|-------------|
| Lav | Begrænset påvirkning af drift eller data |
| Middel | Driftsforstyrrelser, begrænset databrud, lokal påvirkning |
| Høj | Brud på fortrolighed af sundhedsdata, alvorlig driftsforstyrrelse, regulatoriske konsekvenser |

---

## 3. Risikomatrix

| Konsekvens \\ Sandsynlighed | Lav | Middel | Høj |
|----------------------------|-----|--------|-----|
| **Lav**    | Lav risiko | Lav–middel risiko | Middel risiko |
| **Middel** | Lav–middel risiko | Middel risiko | Høj risiko |
| **Høj**    | Middel risiko | Høj risiko | Kritisk risiko |

---

## 4. Eksempler på sikkerhedsrelateret teknisk gæld

| Område | Beskrivelse | Sandsynlighed | Konsekvens | Samlet risiko |
|------|-------------|---------------|------------|---------------|
| Afhængigheder | Forældede tredjepartskomponenter med kendte sårbarheder | Høj | Middel | Høj |
| Adgangsstyring | Inkonsekvent rolle- og rettighedsmodel | Middel | Høj | Høj |
| Logging | Mangelfuld sikkerhedslogning | Middel | Middel | Middel |
| Kryptering | Ældre kryptografiske løsninger | Lav–middel | Høj | Middel–høj |
| Dokumentation | Manglende dokumentation af sikkerhedsantagelser | Høj | Middel | Høj |

*Bemærk: Eksemplerne er illustrative og skal tilpasses det konkrete system.*

---

## 5. Prioriteringsprincipper

Ved begrænsede ressourcer anbefales følgende tilgang:

1. Reducér **kritiske risici** først  
2. Prioritér tiltag med **høj risikoreduktion og lav implementeringsomkostning**  
3. Indarbejd forbedringer som del af eksisterende udviklingsopgaver  
4. Accepter lav risiko eksplicit – og dokumentér beslutningen  

Dette gør sikkerhedsarbejdet transparent og beslutningsdrevet.

---

## 6. Typiske organisatoriske observationer

- Teknisk gæld undervurderes ofte, fordi konsekvenserne er indirekte  
- Risikoen vokser over tid, selv uden ændringer i systemet  
- Manglende handling er en aktiv risikobeslutning  
- Synliggørelse af konsekvenser øger ledelsens ejerskab  

---

## 7. Konklusion

Risikomatricen gør det muligt at flytte dialogen om sikkerhedsrelateret teknisk gæld fra tekniske detaljer til forretningsmæssige og organisatoriske konsekvenser. Den understøtter en praksis, hvor sikkerhed ikke er et særskilt projekt, men en løbende del af vedligeholdelse og udvikling.

---

> **Note:**  
> Matricen er bevidst enkel. Dens styrke ligger i anvendelighed og dialog – ikke i detaljeringsgrad.
