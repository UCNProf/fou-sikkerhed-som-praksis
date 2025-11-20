# **STRIDE – NordicApps’ første trusselsmodellering (Security Practice Story)**

*Denne story er en del af FoU-projektet **“Sikkerhed som praksis”** ved UCN.
Formålet er at vise, hvordan STRIDE kan anvendes lavpraktisk i et lille udviklingsteam – uden forudsætning om sikkerhedsekspertise.*

---

## 1. Introduktion

NordicApps er en lille fempersoners udviklingsvirksomhed, som bygger web- og mobil­løsninger for lokale kunder.
De har fået til opgave at udvikle en **bestillingsplatform** for café-kæden KaffeKæden – med API, POS-enheder, kundeapp og admin-dashboard.

Teamet har talt om “at tænke sikkerhed tidligere”, og beslutter at afholde deres første **STRIDE-workshop**:
90 minutter, ét whiteboard, og hele teamet samlet.

---

## 2. Team og roller

| Navn       | Rolle             | Motivation                                                    |
| ---------- | ----------------- | ------------------------------------------------------------- |
| **Sofie**  | Teamlead          | Vil etablere en fast sikkerhedspraksis                        |
| **Kasper** | Backend-udvikler  | Nysgerrig og teknisk stærk – elsker at udfordre egne systemer |
| **Maja**   | Frontend-udvikler | Fokus på UX – men hader support-sager                         |
| **Lasse**  | Tester            | “Angriberhjerne”, elsker at pille ting fra hinanden           |
| **Line**   | Product Owner     | Vil undgå dårlige kundeoplevelser og driftsproblemer          |

---

## 3. Systemkontekst

Platformen består af:

* Et centralt **API**, der håndterer alle ordrer og produkter
* **POS-terminaler** i caféerne[^1]
* En **kundeapp**
* Et **admin-dashboard** med højere privilegier

Kritiske data: ordrestatus, brugerkonti, produktpriser, rettigheder, m.m.

---

## 4. Story – STRIDE i handling

### S — **Spoofing**

**Hvad sker der?**
Lasse (testeren) finder ud af, at et gammelt token fra en POS-enhed stadig fungerer i API’et.

Han kopierer tokenet fra en logfil og bruger Postman til at kalde:
`POST /order/update`

**Serverens svar:** *200 OK*
Selvom tokenet burde være ugyldigt.

**Hvem udgiver sig for hvem?**
➡️ Lasse udgiver sig for at være **en autoriseret POS-enhed**.

**Hvordan opdages det?**
Kasper spørger undrende:

> “Hvorfor virker det token stadig? Burde de ikke roteres?”

De opdager, at *token rotation aldrig blev implementeret*.

**Teamets beslutning:**

* Indfør short-lived tokens
* Automatisk rotation
* Binding mellem enhed og token

### T — **Tampering**

**Hvad sker der?**
Lasse ændrer i et ordre-JSON objekt:
`"paid": false` → `"paid": true`

API’et accepterer ændringen uden klage.

**Hvordan opdages det?**

> “Jeg ændrede bare feltet, og det gik igennem,” siger Lasse.

Serveren validerer hverken oprindelse eller integritet.

**Konsekvens:**
Gratis kaffe og manipulerede transaktioner.

**Teamets beslutning:**

* Server-side validering
* Signering af ordredata
* Aldrig stole på klientdata

### R — **Repudiation**

**Hvad sker der?**
Line spørger:

> “Kan vi se, hvem der slettede en ordre sidste uge?”

Det kan de ikke.

**Årsag:**

* Ingen audit-log
* Ingen bruger-ID
* Intet timestamp

**Konsekvens:**
Både fejl og angreb er usynlige.

**Tiltag:**

* Central audit-log
* Beskyttet logning (append-only)
* Registrering af endpoint, bruger, tidspunkt, ændring

### I — **Information Disclosure**

**Hvad sker der?**
En frontend-fejl afslører et fuldt stacktrace i browserens netværkslog.
Heraf fremgår interne databasefelter.

**Hvordan opdages det?**
Maja fremviser et mislykket API-kald.

**Konsekvens:**
En angriber kan lære om interne tabeller, felter og frameworks.

**Løsning:**

* Generaliserede fejlmeddelelser til brugere
* Detaljeret teknisk info kun i serverlog
* Feltmaskering i responses

### D — **Denial of Service**

**Hvad sker der?**
Lasse skriver et lille script der sender 2000 requests/min.

API’et går i knæ.

**Hvordan opdages det?**
Cloud dashboard eksploderer i røde tal.

**Konsekvens:**
POS-enheder kan ikke oprette ordrer – køerne i caféen stopper.

**Tiltag:**

* Rate limiting
* Throttling på IP
* Alarmer og auto-skaleringsregler
* Circuit breaker-mønster

### E — **Elevation of Privilege**

**Hvad sker der?**
Kasper tester et admin-endpoint med en lav-privilege bruger.

`POST /admin/products` → *200 OK*

**Hvordan opdages det?**
Line spørger:

> “Kan alle brugere ændre priser?!”

Ja.

**Årsag:**
Manglende rollebaseret adgangskontrol.

**Tiltag:**

* RBAC fra dag 1
* Mapping af roller → endpoints
* Server-side enforcement

---

## 5. Læringspointer

* STRIDE fungerer fremragende som *praktisk teamøvelse*.
* De fleste trusler opdages ved *nysgerrighed*, ikke ved ekspertviden.
* Når teamet diskuterer trusler sammen, får de et fælles billede af deres system.
* Den vigtigste effekt er **backlog-punkter, der fører til handling**.

---

## 6. Relation til SSDLC

Denne story viser STRIDE i **designfasen**.
Output bruges efterfølgende i:

* Risiko-prioritering (Likelihood × Impact)
* Designvalg for kontroller
* Implementering og test

---

*Udarbejdet som del af FoU-projektet “Sikkerhed som praksis” – UCN, 2025.*

---

[^1]: **POS (Point of Sale)** – en fysisk salgs- og bestillingsterminal i caféen.

