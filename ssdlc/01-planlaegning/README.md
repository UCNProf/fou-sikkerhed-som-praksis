# **Fase 1 – Planlægning**

*Secure Software Development Lifecycle (SSDLC)*
*Projekt: Sikkerhed som praksis – Awareness og implementering af softwaresikkerhed i små udviklingsvirksomheder*

## **Formål med planlægningsfasen**

Planlægningsfasen er fundamentet for resten af SSDLC-forløbet. Målet er at skabe **retning, fokus og fælles forståelse** for systemets sikkerhedsmæssige krav – uden at producere unødigt tunge dokumenter.

For små udviklingsteams (5–10 personer), som NordicApps, handler planlægning ikke om lange rapporter, men om at:

* identificere det mest **kritiske** i systemet,
* afklare hvilke handlinger systemet **aldrig må** understøtte,
* aftale et realistisk **sikkerhedsniveau**, der matcher ressourcer og projektets kompleksitet,
* sætte rammen for analyse- og designarbejdet i de efterfølgende faser.

Planlægning er derfor ikke det modsatte af agilitet – det er en forudsætning for **sikker og effektiv** agil udvikling.


## **Hvorfor arbejde med planlægning i SSDLC?**

I FoU-projektet *Sikkerhed som praksis* har interviews og observationer fra små udviklingsvirksomheder vist, at:

* barriererne for sikkerhed sjældent er modvilje,
* udviklere ofte mangler et *lavpraktisk udgangspunkt*,
* usikkerhed i starten af et projekt fører til dårligere beslutninger senere,
* små teams får mest effekt ved at arbejde med **få ting – men tidligere**.

Denne fase tager derfor udgangspunkt i letvægtsmetoder, der giver høj værdi med lav investering.


## **Centrale aktiviteter i fase 1**

Fase 1 indeholder tre kerneelementer, som går igen i alle cases:

### **1. Identifikation af kritiske aktiver**

En kort og fokuseret øvelse, hvor teamet identificerer 3–6 aktiver, der er mest sårbare eller mest værdifulde for systemet.

Aktiverne danner grundlag for prioritering i analysefasen.


### **2. Fastlæggelse af “må-ikke” handlinger**

Teamet definerer 3–5 handlinger, som systemet aldrig må understøtte.
Disse fungerer senere som:

* negative testcases
* designprincipper
* pejlemærker for adgangskontrol og logging
* proaktive sikkerhedskrav

“Må-ikke”-handlinger er en central del af projektets praksisnære tilgang til security-by-design.


### **3. Aftale af sikkerhedens serviceniveau**

En realistisk, fælles forståelse for:

* hvilket ambitionsniveau teamet arbejder efter
* hvilke standarder der følges (fx “ASVS Light”)
* hvordan sikkerhed reviewer integreres i udviklingsprocessen

Dette sikrer, at alle udviklere arbejder efter samme forventninger – en afgørende faktor i små teams.


## **Cases i Fase 1**

Fasen udbygges løbende med cases, der viser, hvordan NordicApps og deres kunder arbejder med planlægningspraksisser.

### **Eksisterende cases**

| Case                                                                  | Indhold                                                                            | Fokus                                                    |
| --------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | -------------------------------------------------------- |
| [**Tidlig afklaring af kritiske aktiver i et nyt ordrestyringssystem**](case-early-asset-prioritization.md)) | NordicApps identificerer aktiver og må-ikke-handlinger for et takeaway-ordresystem | Kritiske aktiver, sikkerhedsniveau, “må-ikke”-handlinger |

*(Nye cases tilføjes her efterhånden som de udvikles.)*


## **Bilag i Fase 1**

Bilagene indeholder skabeloner, eksempler og artefakter, der kan bruges af udviklingsteams til egen praksis.

| Bilag                                             | Beskrivelse                                                     |
| ------------------------------------------------- | --------------------------------------------------------------- |
| **Bilag 01 – Aktiver og må-ikke-handlinger**      | Dokumenteret eksempel fra NordicApps’ arbejde i fase 1          |
| **Bilag 02 – Kickoff-skema til planlægningsmøde** | Letvægtsværktøj til planlægning af et 30–45 min. sikkerhedsmøde |
| **Bilag 03 – Mini-tjekliste for små teams**       | Hurtig checkliste til brug før sprint 0 eller projektopstart    |

Yderligere bilag (fx udfyldte eksempler, visuelle modeller eller eksterne guides) kan tilføjes efter behov.


## **Relation til de øvrige SSDLC-faser**

Planlægningsfasen leverer input til:

* **Analyse (fase 2):** hvilke aktiver er vigtigst at modellere trusler for?
* **Design (fase 3):** hvilke må-ikke-handlinger skal designet gøre umulige?
* **Implementering:** hvilke sikkerhedskrav skal være default?
* **Test:** negative testcases baseret på må-ikke-handlinger
* **Drift:** hvilke elementer skal overvåges eller logges med ekstra opmærksomhed?

Planlægning ∴ mindre friktion + færre fejl senere.


## **Hvordan bruges materialet i praksis?**

Dette repos materiale kan anvendes af:

* små udviklingsteams, der vil styrke deres sikkerhedspraksis
* undervisere, der ønsker praksisnære eksempler
* studerende, der arbejder med SSDLC og sikker software
* virksomheder, der ønsker letvægtsværktøjer til sikkerhed i projekter

Alle cases og bilag er designet til at være:

* korte
* praksisnære
* økonomisk realistiske
* lette at integrere i eksisterende workflows

## **Videre udvikling**

Fase 1 vil løbende blive udvidet med:

* flere cases fra NordicApps og deres kunder
* templates til sikkerhedskrav, roller og ansvar
* konkrete eksempler på planlægningsfejl og læringspointer
* integration til undervisningsmaterialer om SSDLC

Alle bidrag dokumenteres i GitHub-repoet og indgår i projektets samlede FoU-resultater.


# **Bidrag**

Forslag, rettelser og nye cases modtages gerne via pull requests.
Retningslinjer findes i `CONTRIBUTING.md`.

