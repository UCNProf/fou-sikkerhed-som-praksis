# STRIDE i praksis – trusselsmodellering i designfasen

*Denne case er en del af FoU-projektet **“Sikkerhed som praksis”** ved UCN.  
Den beskriver STRIDE-metoden i struktureret form og hænger tæt sammen med en praksisfortælling, der viser STRIDE udført i et realistisk lille udviklingsteam.*

---

## 🔗 Supplerende materiale: praksisfortælling  
For at se STRIDE anvendt i en konkret, lavpraktisk workshop-situation, læs den tilhørende Security Practice Story:

➡️ **[NordicApps’ første STRIDE-workshop](../../stories/stride-first-workshop.md)**

Denne fortælling giver et levende billede af, hvordan teamet finder trusler, diskuterer dem og omsætter dem til handling i praksis.

---

## 1. Titel
**“STRIDE i designfasen – systematisk trusselsmodellering for små udviklingsteams”**

---

## 2. SSDLC-fase
**Primær:** Design  
**Sammenhæng:** Input fra analysefasens risikovurdering. Output bruges til teknisk risikoprioritering og valg af sikkerhedskontroller.

---

## 3. Baggrund
Udviklingsvirksomheden **NordicApps** er i gang med designfasen af en ny bestillingsplatform til cafébranchen.  
I analysefasen har de identificeret kritiske risici for både drift, data og kundetillid.

I designfasen skal teamet skabe et mere detaljeret overblik over **tekniske trusler** i systemets arkitektur.  
Platformen består af:

- Et centralt **API**  
- En **POS-terminal** i butikken[^1]  
- En **kundeapp**  
- Et **admin-dashboard**  

STRIDE hjælper teamet med at identificere trusler **før der skrives kode**, så designbeslutninger træffes på et informeret grundlag.

---

## 4. Problemstilling
Hvordan kan et lille udviklingsteam uden sikkerhedsspecialister gennemføre en effektiv trusselsmodellering, der er til at forstå, giver konkret værdi og fører til realistiske backlog-punkter?

---

## 5. Teoretisk reference
- **STRIDE-modellen**  
  *(Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege)*  
- **OWASP SAMM 2.0 – Threat Assessment**  
- **OWASP ASVS 4.0.3 – V1: Architecture, Design and Threat Modeling**

---

## 6. Praktisk løsning / tiltag
STRIDE-workshoppen gennemføres på 90 minutter og består af fire trin:  
1) Forberedelse  
2) Gennemgang af STRIDE-kategorier  
3) Dokumentation af trusler  
4) Overførsel til backlog og prioritering  

Metoden afspejler praksisfortællingen i *“NordicApps’ første STRIDE-workshop”*.

---

### a) Forberedelse
Teamet bruger:

- Whiteboard eller Miro med arkitekturdiagram  
- Liste over komponenter og dataflows  
- En facilitator  
- En “angriberrolle” (tester) til at prøve ideer af  
- Produktansvarlig for at sikre forretningsforståelse  

---

### b) Anvendelse af STRIDE – med eksempler fra workshoppen

| STRIDE | Spørgsmål | Fund i praksis (fra storyen) |
|--------|-----------|------------------------------|
| **S – Spoofing** | Kan nogen udgive sig for en anden enhed eller bruger? | Et gammelt POS-token virker stadig; testeren udgiver sig for POS-enheden. |
| **T – Tampering** | Kan data manipuleres? | `"paid": false` ændres til `"paid": true`, og API’et accepterer ændringen. |
| **R – Repudiation** | Kan nogen benægte en handling? | Ingen audit-log – teamet kan ikke se, hvem der slettede en ordre. |
| **I – Information Disclosure** | Kan følsomme data lække? | Stacktraces returneres til klienten og afslører interne databasefelter. |
| **D – Denial of Service** | Kan systemet gøres utilgængeligt? | Et requests-script lammer API’et på få sekunder. |
| **E – Elevation of Privilege** | Kan nogen få flere rettigheder end tiltænkt? | En lav-privilege bruger kan ændre produktpriser via admin-endpoints. |

---

### c) Dokumentation af fund

Fundene registreres i et simpelt skema:

| Komponent | STRIDE | Trussel | Mulig løsning |
|----------|--------|----------|----------------|
| API | Tampering | Ordredata kan manipuleres | Server-side validering og signering |
| Dashboard | Elevation | Admin-endpoints uden rettighedskontrol | Rollebaseret adgangskontrol (RBAC) |
| POS/API | Spoofing | Tokens uden rotation | Short-lived tokens + rotation |
| API/Client | Information Disclosure | Stacktrace i responses | Saniterede fejlbeskeder |
| System | DoS | API lammes af request-storm | Rate limiting + throttling |

---

### d) Workshop-output

Efter workshoppen står teamet med:

- En prioriteret liste over tekniske trusler  
- Et foto eller digitalt diagram over fundne angrebsveje  
- En række backlog-punkter med beskrivelse, konsekvens og ansvar  
- En fælles forståelse af systemets svagheder  

---

## 7. Typiske fejl og faldgruber
- **Overdetaljering:** STRIDE skal give overblik, ikke 40 siders dokumentation  
- **Kun udviklere deltager:** PO og tester bringer vigtig kontekst  
- **Ingen kobling til backlog:** Trusselslister uden handling mister mening  
- **Engangsaktivitet:** STRIDE bør gentages ved større arkitekturændringer  

---

## 8. Læringspointer
- STRIDE giver hurtigt overblik over, *hvor der er noget at gøre ved*  
- De bedste fund opstår ofte, når teamet “tænker som angriber”  
- Modellen virker særligt godt i små teams, fordi alle perspektiver er til stede  
- Det vigtigste er **fælles forståelse og handling**, ikke perfektion  

---

## 9. Relation til SSDLC

STRIDE hører til **designfasen**, hvor analyser fra tidligere faser omsættes til konkrete tekniske beslutninger.

Output bruges til:

- Risiko-prioritering (Likelihood × Impact)  
- Designvalg og dokumentation i henhold til ASVS  
- Mitigation cases såsom adgangsstyring og inputvalidering  

---

## 10. Videre læsning / referencer

- **OWASP Threat Modeling Cheat Sheet**  
  https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html  
- **OWASP ASVS v4.0.3 – V1: Architecture, Design & Threat Modeling**  
  https://github.com/OWASP/ASVS/blob/master/4.0/OWASP%20Application%20Security%20Verification%20Standard%204.0.3-en.pdf  

---

*Udarbejdet som del af FoU-projektet “Sikkerhed som praksis” – UCN, 2025.*

[^1]: **POS (Point of Sale)** – kasseterminalen i caféen, hvor baristaen registrerer ordrer.
