# STRIDE i praksis – trusselsmodellering i designfasen

## 1. Titel
**“STRIDE i designfasen – systematisk trusselsmodellering for små udviklingsteams”**


## 2. SDLC-fase
*Primær:* Design  
*Sammenhæng:* Input fra analysefasens risikovurdering. Output bruges i teknisk risikoprioritering og valg af kontroller.


## 3. Baggrund
Virksomheden **CoffeeShopChain** har afsluttet analysefasen og identificeret de mest kritiske risici i deres kommende ordrehåndteringssystem.  
Udviklingsteamet skal nu i designfasen kortlægge **konkrete trusler mod systemarkitekturen** for at kunne vælge relevante sikkerhedskontroller.

Systemet består af:
- Et centralt **API**, som håndterer ordrer og produktdata  
- En **POS-terminal** til baristaen[^1]  
- En **kundevisningsskærm** i butikken  
- Et **admin-dashboard** til ledelsen  

Formålet med øvelsen er at finde potentielle angrebspunkter i arkitekturen – *før* der skrives kode.


## 4. Problemstilling
Hvordan kan et lille udviklingsteam uden dedikeret sikkerhedsspecialist identificere og dokumentere de mest relevante trusler mod deres system, så sikkerhed bliver en del af designarbejdet – ikke en eftertanke?


## 5. Teoretisk reference
- **Microsoft STRIDE-model**  
  *(Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege)*  
- **OWASP SAMM 2.0:** Design → Threat Assessment  
- **OWASP ASVS 4.0.3:** V1 Architecture, Design and Threat Modeling  


## 6. Praktisk løsning / tiltag
Teamet afholder en 90-minutters **trusselsmodellering-workshop** baseret på STRIDE.  
De starter med et simpelt arkitekturdiagram over systemet og identificerer trusler for hvert komponent og dataflow.

### a) Forberedelse
- Whiteboard eller Miro-board med arkitekturdiagram  
- Liste over systemkomponenter og dataflows  
- Roller: udvikler (facilitator), produktansvarlig (domæneviden), evt. tester (angrebsperspektiv)

### b) Anvendelse af STRIDE
Teamet gennemgår hvert element i systemet ud fra de seks STRIDE-kategorier:

| STRIDE-kategori | Spørgsmål at stille | Eksempel i CoffeeShopChain |
|-----------------|--------------------|-----------------------------|
| **S – Spoofing** | Kan nogen udgive sig for en anden bruger eller service? | En kunde manipulerer token og logger ind som admin. |
| **T – Tampering** | Kan data ændres undervejs eller i databasen? | En angriber ændrer ordrestatus fra “ikke betalt” til “betalt”. |
| **R – Repudiation** | Kan nogen benægte en handling, de faktisk udførte? | En barista sletter en ordre og nægter at have gjort det. |
| **I – Information Disclosure** | Kan følsomme data blive eksponeret utilsigtet? | API’et returnerer kundemails i JSON-respons. |
| **D – Denial of Service** | Kan systemet gøres utilgængeligt for brugere? | Script sender tusindvis af ordreanmodninger på kort tid. |
| **E – Elevation of Privilege** | Kan nogen få højere rettigheder end tiltænkt? | Dashboard-bruger får adgang til administrative endpoints. |

### c) Dokumentation af fund
Truslerne registreres i et simpelt regneark eller markdown-dokument:

| Komponent | STRIDE-kategori | Trussel | Mulig modforanstaltning |
|------------|----------------|----------|--------------------------|
| API | Tampering | Manipulation af ordrestatus | Signering og server-side validering |
| Dashboard | Elevation of Privilege | Uautoriseret adgang til admin-funktioner | Rollebaseret adgangskontrol (RBAC) og sessionkontrol |
| Database | Information Disclosure | Utilsigtet eksponering af PII i fejlmeddelelser | Maskering og fejlhåndtering |
| POS | Spoofing | Forfalsket login via modificeret app | Token-baseret autentifikation |
| System | Denial of Service | Overbelastning via script | Rate limiting og IP-throttling |

### d) Workshop-output
- En liste over identificerede trusler (ca. 10–15 realistiske eksempler)  
- Én eller flere sandsynlige “angrebsveje” visualiseret på diagrammet  
- Et prioriteret sæt sikkerhedskrav, som kan indgå i backloggen  


## 7. Typiske fejl og faldgruber
- **For høj detaljeringsgrad:** STRIDE skal skabe overblik, ikke være et sikkerhedsreview.  
- **Manglende tværfaglighed:** Hvis kun udviklere deltager, overses forretningsaspekter.  
- **Intet ejerskab:** Hvis trusler ikke omsættes til backlog-items, forsvinder effekten.  
- **Ingen iteration:** Modellen bruges én gang – men bør genbesøges ved større ændringer.  


## 8. Læringspointer
- STRIDE gør trusselsmodellering gennemførlig for små teams.  
- Visualisering af dataflows afslører ofte skjulte afhængigheder.  
- Brug workshoppen som samtaleværktøj – ikke som checkliste.  
- Det vigtigste output er **fælles forståelse**, ikke perfekte trusselslister.  


## 9. Relation til SSDLC
Trusselsmodellering gennem STRIDE hører til **designfasen** i SSDLC og bygger videre på resultaterne fra **analysefasens risikovurdering**.  
Outputtet bruges som grundlag for:
- **Risikoprioritering (Likelihood × Impact)** – vurdering af, hvilke trusler der skal håndteres først.  
- **Design af kontroller** – fx *adgangsstyring*, *kryptering* og *inputvalidering*.  
- **Mitigation cases** – fx *Broken Access Control*, hvor en trussel omsættes til konkret løsning.


## 10. Videre læsning / referencer
- [OWASP Threat Modeling Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html)  
- [OWASP ASVS 4.0.3 – V1: Architecture, Design and Threat Modeling Requirements](https://github.com/OWASP/ASVS/blob/master/4.0/OWASP%20Application%20Security%20Verification%20Standard%204.0.3-en.pdf)  

---

*Udarbejdet som del af FoU-projektet “Sikkerhed som praksis” – UCN, 2025.*

[^1]: **POS (Point of Sale)** – systemet eller terminalen, hvor kunden gennemfører sin bestilling og betaling. I denne case bruges betegnelsen om baristaens kasseterminal i caféen.