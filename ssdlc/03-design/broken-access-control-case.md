# **Broken Access Control i designfasen – adgangsstyring før koden skrives**

*Casen viser, hvordan et udviklingsteam kan forebygge fejl i adgangsstyring ved at tænke roller og rettigheder ind allerede i designfasen. Den er udviklet som en del af projektet **Sikkerhed som praksis**, der har til formål at gøre sikkerhed operationel og økonomisk realistisk i små udviklingsteams.*

---

## 1. SSDLC-fase

**Primær:** Design
**Sekundær:** Implementering

Casen placerer sig i designfasen, hvor adgangsstyring planlægges og dokumenteres, men har direkte konsekvenser for implementering og test.

---

## 2. Baggrund

Et lille udviklingsteam bygger en intern bestillingsplatform, hvor medarbejdere kan oprette og håndtere kundeordrer.
Under en gennemgang af arkitekturen opdages det, at rolle- og adgangsstyring ikke er specificeret. Udviklerne er begyndt at kode endpoints uden klare regler for, hvem der må gøre hvad.

Situationen afspejler en typisk udfordring i små udviklingsmiljøer, hvor sikkerhed sjældent bliver dokumenteret som en del af designet.

---

## 3. Problemstilling

Hvordan sikrer man, at kun autoriserede brugere kan se, oprette og ændre ordrer **før** systemet implementeres?
Hvordan kan adgangsstyring designes som en integreret del af systemarkitekturen i stedet for et efterfølgende “fix”?

---

## 4. Teoretisk reference

Casen relaterer til følgende frameworks og principper:

* **OWASP Top 10 (2021): A01 – Broken Access Control**
* **ASVS 4.0.3 – V4: Access Control Verification Requirements**

  * V4.1: Enforce Access Control on Trusted Server-Side Code
  * V4.2: Deny Access by Default
* **Principle of Least Privilege**

---

## 5. Praktisk løsning / tiltag

Teamet udarbejder en **Access Control Matrix** som del af design-dokumentationen.
Matrice beskriver, hvilke roller der må udføre hvilke handlinger på systemets ressourcer:

| Rolle         | Se ordrer | Opret ordrer | Rediger ordrer | Slet ordrer |
| ------------- | --------- | ------------ | -------------- | ----------- |
| Administrator | ✅         | ✅            | ✅              | ✅           |
| Medarbejder   | ✅         | ✅            | ✅              | ❌           |
| Kunde         | ✅ (egne)  | ✅            | ❌              | ❌           |

Tiltagene omfatter:

* Roller og rettigheder dokumenteres eksplicit i designet.
* API-specifikationen (OpenAPI) udvides med autorisationskrav pr. endpoint.
* Testcases planlægges for både tilladte og afviste handlinger.
* Implementeringsteamet anvender et fælles auth-bibliotek og central policy.

Tilgangen kræver ingen avancerede værktøjer – et simpelt regneark eller dokument er tilstrækkeligt – hvilket gør metoden realistisk for små teams.

*Se [bilag 1](case-broken-access-control-bilag-01.md) for et konkret eksempel på den anvendte access-matrix.*

---

## 6. Typiske fejl og faldgruber

* Adgangsstyring udskydes til implementeringsfasen.
* Roller defineres implicit (“hvis du kan logge ind, må du alt”).
* Ingen sammenhæng mellem forretningsroller og systemroller.
* Manglende test af negative cases.
* Overkomplicerede løsninger, der ikke kan vedligeholdes i små teams.

---

## 7. Læringspointer

* Tænk adgangsstyring **før koden skrives**.
* Dokumentér roller og rettigheder eksplicit i designet.
* Adskil roller, handlinger og dataområder.
* Planlæg test for både tilladte og afviste handlinger.
* Enkle, systematiske tiltag er ofte mere bæredygtige end komplekse frameworks.

---

## 8. Relation til SSDLC

Casen hører hjemme i **designfasen**, men påvirker både **implementering** (gennem rolle- og policy-kode) og **test** (validering af adgangslogik).
Ved at etablere adgangsstyring tidligt reduceres risikoen for fejl i senere faser og sparer tid på efterfølgende rettelser.

---

## 9. Videre læsning / referencer

* [OWASP A01: Broken Access Control](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)
* [OWASP ASVS 4.0.3 – V4 Access Control](https://owasp.org/www-project-application-security-verification-standard/)
* [OWASP Cheat Sheet: Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)
* [OWASP Web Security Testing Guide – Authorization Testing](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/05-Authorization_Testing/)

---

*En del af projektet **“Sikkerhed som praksis” – UCN, 2025.***

