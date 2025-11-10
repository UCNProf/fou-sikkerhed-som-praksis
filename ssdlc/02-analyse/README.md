# Analysefasen i SSDLC – forstå systemet og dets risici

## 1. Formål
Analysefasen i SSDLC handler om at **forstå systemets kontekst, aktiver og trusler**, før der træffes designbeslutninger.  
For små udviklingsteams er målet ikke at lave omfattende dokumentation, men at skabe **indsigt og fælles forståelse** af, hvad der skal beskyttes, og hvorfor.

Denne del af projektet “Sikkerhed som praksis” viser, hvordan risikoarbejde kan gøres **enkelt og operationelt**, så det bliver en naturlig del af udviklingsprocessen – ikke et separat compliance-krav.

---

## 2. Sammenhæng med planlægning og design
Analysefasen ligger mellem **planlægning** (hvor formål og interessenter fastlægges)  
og **designfasen** (hvor arkitektur og kontroller besluttes).

I praksis betyder det:
- Fra **planlægning** arver teamet overordnede mål og rammer.  
- Til **design** afleveres en kortfattet vurdering af aktiver, trusler og risici – det konkrete input til trusselsmodellering og valg af sikkerhedskontroller.

| Forrige fase | Output | Videre til analyse |
|---------------|---------|--------------------|
| **Planlægning** | Forretningsmål, scope, interessenter | Systemets formål og grænser |
| **Analyse** | Aktiver, trusler, risikovurdering | Input til design og kontrolvalg |
| **Design** | Arkitektur og sikkerhedskontroller | Implementering og test |

---

## 3. Aktiviteter i analysefasen

| Aktivitet | Formål | Output | Case |
|------------|--------|---------|------|
| **Aktiv- og dataidentifikation** | Kortlæg, hvad systemet håndterer og hvorfor det er følsomt. | Liste over aktiver og datatyper. | Indgår i [Risk Assessment](risk-assessment-case.md) |
| **Trusselsidentifikation** | Forstå realistiske trusler mod systemet. | Overblik over potentielle angreb eller fejl. | [Risk Assessment](risk-assessment-case.md) |
| **Risikovurdering** | Kombinér sandsynlighed og konsekvens for at prioritere indsatsen. | Threat matrix og prioriteret liste. | [Risk Assessment](risk-assessment-case.md) |
| **Forretningspåvirkning (Business Impact)** | Oversæt tekniske risici til konsekvenser for drift, omdømme og jura. | Kort business impact-vurdering. | [Risk Assessment](risk-assessment-case.md) |

---

## 4. Analysefasens output
Efter analysefasen skal teamet stå med:

- En kort **liste over systemets aktiver og dataflows**  
- En **risikovurdering** (fx i tabel- eller matrixform)  
- Et overblik over **prioriterede indsatsområder**  
- En **overlevering til designfasen**, hvor trusler modelleres og kontroller vælges  

Outputtet kan være et markdown-dokument, et regneark eller et simpelt diagram – formålet er at skabe handling, ikke formalia.

---

## 5. Typiske faldgruber
- **At springe analysen over**, fordi systemet virker simpelt.  
- **At gøre den for teoretisk**, så den mister relevans for udviklere.  
- **At overse forretningen**, så vurderingen bliver rent teknisk.  
- **At lade dokumentet samle støv**, i stedet for at bruge det i designarbejdet.

---

## 6. Relation til SSDLC
Analysefasen udgør det første egentlige sikkerhedsarbejde i SSDLC.  
Den danner grundlag for de efterfølgende aktiviteter i designfasen, herunder:

- [STRIDE – trusselsmodellering i praksis](../03-design/stride-case.md) *(kommer i 03-design)*  
- [Risk Prioritization – Likelihood × Impact](../03-design/risk-prioritization-likelihood-impact.md) *(kommer i 03-design)*

> **Overgang til designfasen:**  
> Outputtet fra analysefasen anvendes direkte i designfasen, hvor trusler konkretiseres og prioriteres i forhold til arkitektur, dataflows og adgangskontroller.

---

## 7. Videre læsning
- [OWASP Risk Rating Methodology](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology)  
- [OWASP ASVS 4.0.3 – V1: Architecture, Design and Threat Modeling](https://github.com/OWASP/ASVS/blob/master/4.0/OWASP%20Application%20Security%20Verification%20Standard%204.0.3-en.pdf)  
- [ENISA – Advancing Software Security in the EU (2019)](https://eipacc.eu/wp-content/uploads/2021/08/ENISA-Report-Advancing-Software-Security-in-the-EU.pdf)  
- [BSI TR-03185 – Secure Software Lifecycle](https://www.bsi.bund.de/SharedDocs/Downloads/EN/BSI/Publications/TechGuidelines/TR03185/BSI-TR-03185.pdf?__blob=publicationFile&v=4)

---

*Udarbejdet som del af FoU-projektet “Sikkerhed som praksis” – UCN, 2025.*
