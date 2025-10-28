## Secure Software Development Lifecycle (SSDLC)

I de fleste udviklingsteams beskrives arbejdet med software gennem en klassisk *Software Development Lifecycle (SDLC)* – en række faser fra planlægning til vedligeholdelse.
Modellen giver struktur, men i mange organisationer håndteres **sikkerhed** stadig som et særskilt spor: noget, der tages op til sidst, eller kun når compliance kræver det.

![Software Development Lifecycle](/assets/diagrams/sdlc.png)

**Secure Software Development Lifecycle (SSDLC)** ændrer på dette perspektiv.
Det er ikke en ny metode, men en måde at arbejde, hvor sikkerhed **integreres i hver fase af udviklingen** – fra de første idéer til drift og løbende vedligeholdelse.
Målet er ikke at gøre udviklingen tungere, men at gøre sikkerheden lettere at praktisere.
I stedet for at spørge *“hvordan tester vi for sikkerhed til sidst?”*, spørger SSDLC:
*“hvordan kan vi tænke sikkerhed med i alt, hvad vi gør?”*

---

## SSDLC i praksis – tilpasset virkeligheden

Modellen for SSDLC dækker hele livscyklussen for et softwareprodukt, men **de færreste virksomheder arbejder med alle faser**.
Mange mindre udviklingshuse leverer kun dele af et system, fx et API, en integration eller en frontend, mens drift og vedligeholdelse varetages af andre.
Det ændrer ikke relevansen af SSDLC – men måden, den anvendes på.

SSDLC skal forstås som en **ramme for refleksion og ansvar**, ikke som et krav om at dække alt fra idé til drift.
Spørgsmålet er ikke, *“er vi med i alle faser?”* men derimod:
*“hvordan kan vi styrke sikkerheden dér, hvor vi faktisk har indflydelse?”*

Eksempler:

* En **frontend-leverandør** kan sikre inputvalidering, session-håndtering og tryg API-kommunikation – selv om driften ligger hos kunden.
* En **backend-udvikler** kan arbejde med adgangskontrol, logging og fejlrobusthed – uafhængigt af infrastrukturansvar.
* En **integrationspartner** kan fokusere på autentifikation, kryptering og datahygiejne mellem systemer.
* En **vedligeholdelsespartner** kan reagere hurtigt på sårbarheder og holde afhængigheder opdaterede, selv om de ikke udviklede produktet.

SSDLC giver altså **et fælles sprog for sikker praksis** – et værktøj til at identificere, hvor et team bedst kan bidrage til et sikrere samlet produkt.

---

## Sikkerhedsaktiviteter i de seks faser

Når man anvender SSDLC i praksis, handler det om at koble **sikkerhedsaktiviteter** til de aktiviteter, der allerede findes i udviklingsarbejdet.
Faserne nedenfor kan bruges som inspiration – ikke som en tjekliste.

---

### 1. Planlægning

Planlægning handler om retning, prioritering og ansvar.
De vigtigste sikkerhedsaktiviteter i denne fase er:

* Identificér og dokumentér **sikkerhedsmål** – hvad skal beskyttes, og hvorfor.
* Lav en **overordnet risikovurdering**, så indsatsen matcher systemets kritikalitet.
* Afklar **roller og ansvar**: hvem har ejerskab for sikkerhed undervejs.
* Overvej **regulative krav** (fx GDPR, NIS2, ISO 27001) fra starten.
* Integrér **sikkerhedsopgaver** i planlægningsværktøjer og sprint backlog, så de ikke glemmes.

---

### 2. Analyse

I analysefasen kortlægges, hvad systemet skal gøre – og hvor det kan angribes.

* Udfør **dataflow-analyse** for at se, hvor data bevæger sig, og hvem der har adgang.
* Kortlæg **trust boundaries** mellem systemer og eksterne aktører.
* Lav en **trusselsmodel** (fx STRIDE) for at identificere risici og prioriterede fokusområder.
* Dokumentér **sikkerhedskrav** og **ikke-funktionelle krav** sammen med de funktionelle.
* Fastlæg tidligt **autentifikations- og autorisationsprincipper**, så de bliver en del af arkitekturen.

---

### 3. Design

Designfasen handler om at omsætte analyserne til teknisk struktur med sikkerhed indbygget.

* Brug **principperne for Secure og Privacy by Design**.
* Gennemfør **arkitektur-reviews** med fokus på isolation, mindst privilegium og dataflow.
* Indarbejd **sikkerhedskontroller** i diagrammer og designspecifikationer.
* Definér **standarder** for API-sikkerhed, kryptering og autentifikation.
* Planlæg **logging og overvågning**, så hændelser kan spores fra starten.

---

### 4. Implementation

Her realiseres designet, og det er her, sårbarheder typisk opstår.

* Følg **sikre kodestandarder** og anvend systematisk code reviews.
* Brug **automatiseret scanning** (SAST, dependency checks) i build-processen.
* Undgå **hardcodede credentials**, og brug sikre secrets managers.
* Brug **parametriserede forespørgsler** for at undgå injection.
* Implementér **fejlhåndtering og logging**, der ikke afslører interne detaljer.
* Kombinér **peer review** og **pair programming**, især i kritiske komponenter.

---

### 5. Test og integration

Her bekræftes ikke kun, at systemet virker – men at det også **opfører sig sikkert**.

* Integrér **sikkerhedstests i CI/CD** (SAST, DAST, dependency-scanning).
* Gennemfør **manuelle tests** af højrisikofunktioner som login og adgangsstyring.
* Udfør **penetration testing** før release, hvor det er relevant.
* Gennemgå **konfigurationer og deployment pipelines** for misconfigurations.
* Sørg for, at **testdata** er anonymiseret og ikke eksponerer personoplysninger.

---

### 6. Vedligeholdelse

Når systemet er i drift, handler sikkerhed om opmærksomhed og læring.

* Udfør **patch management** og opdater afhængigheder løbende.
* Overvåg **logs og hændelser** for uregelmæssigheder.
* Etabler en **incident response-proces**: hvordan håndteres hændelser.
* Udfør **post-mortem reviews** efter fejl for at forbedre praksis.
* Gennemfør **periodiske sikkerhedsreviews** og genbesøg trusselsmodeller ved ændringer.
* Sørg for, at **viden og ansvar fastholdes**, også når teamet eller leverandører skifter.

---

### Sammenfatning

SSDLC er en ramme, ikke en opskrift.
Den hjælper udviklingsteams med at identificere, **hvor i deres egen proces de faktisk kan gøre en forskel** for sikkerheden.
Om man bygger hele systemer eller blot enkelte dele, kan SSDLC give et fælles sprog for, hvordan sikkerhed tænkes, prioriteres og dokumenteres i praksis.

> Formålet er ikke at skabe mere proces – men mere bevidst praksis.

---

Vil du have, at jeg laver en **kort introversion** af denne tekst (ca. 1 side), som du kan bruge som “SSDLC i praksis – overblik” i begyndelsen af dokumentet eller som en hånd-out til workshops?
