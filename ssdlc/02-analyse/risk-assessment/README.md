## Risikovurdering i praksis – Analysefasen i SSDLC

### 1. Titel
**Risikovurdering i analysefasen – fra trusler til prioriterede handlinger**

---

### 2. SSDLC-fase
*Primær:* Analyse  
*Sammenhæng:* Resultaterne bruges i designfasen til valg af sikkerhedskontroller

---

### 3. Baggrund
Café-kæden **CoffeeShopChain** er i gang med at udvikle et nyt **ordrehåndteringssystem**, der håndterer bestillinger fra POS-terminaler, kundeapps og leveringsintegrationer. Systemet skal håndtere kundeoplysninger, betalingsstatus og interne produktdata.  

Udviklingsteamet står i analysefasen og skal beslutte, hvilke dele af systemet der kræver særlig beskyttelse, før de går videre til design og implementering. Formålet er at få et fælles billede af risikoen – både teknisk og forretningsmæssigt.

---

### 4. Problemstilling
Hvordan kan et lille udviklingsteam identificere og vurdere de mest kritiske sikkerhedsrisici i systemet – uden at drukne i teori eller komplicerede metoder?  
Målet er at prioritere indsatsen, så de mest alvorlige risici håndteres først.

---

### 5. Teoretisk reference
- **OWASP Top 10:** A04 – Insecure Design, A01 – Broken Access Control  
- **OWASP ASVS 4.0.3:** V1 Architecture, Design and Threat Modeling  
- **NIST SP 800-30:** Guide for Conducting Risk Assessments  
- **SSDLC-princip:** Risikoidentifikation og -vurdering i analysefasen som grundlag for designbeslutninger.

---

### 6. Praktisk løsning / tiltag
#### a) Identifikation af aktiver
Teamet starter med at identificere, hvad der skal beskyttes:
- Kundedata (navn, kontakt, ordrer)
- Betalingsinformationer (transaktionsstatus, ikke kortdata)
- API’er mellem POS, App og backend
- Admin-dashboard til produktstyring

#### b) Identifikation af trusler
For hvert aktiv diskuteres relevante trusler, fx:
- Uautoriseret adgang til ordrer eller kundedata
- Manipulation af ordrestatus (fra “betalt” til “ikke betalt”)
- Aflytning af API-trafik mellem POS og backend
- Utilsigtet dataeksponering via fejllogning

#### c) Threat Matrix (tekstbaseret eksempel)
| Sandsynlighed | Lav konsekvens | Mellem konsekvens | Høj konsekvens |
|---------------|----------------|------------------|----------------|
| **Lav** | – | Logdata eksponeret |  |
| **Mellem** | – | API-aflytning |  |
| **Høj** | – | Manipuleret ordrestatus | Uautoriseret adgang til kundedata |

*(En visuel version af denne matrix kan tilføjes som `diagram.png` i mappen.)*

#### d) Risk scoring
For at kunne prioritere risikoer anvendes en simpel model, hvor **risiko = sandsynlighed × konsekvens**.  
Begge faktorer vurderes på en skala fra **1 (lav)** til **5 (høj)**.

**Sandsynlighed** handler om, hvor let en trussel kan realiseres i praksis.  
Her vurderes fx:
- Er systemet eksponeret mod internettet?
- Kræver angrebet særlig viden eller adgang?
- Er der allerede kontroller, der mindsker risikoen?

**Konsekvens** handler om, hvor alvorlige følger det har, *hvis* truslen realiseres.  
Her vurderes fx:
- Tab af data eller systemadgang
- Økonomiske konsekvenser for virksomheden
- Skade på omdømme og tillid
- Brud på lovgivning eller kontrakter

Tallene bruges til at skabe et fælles sprog mellem udviklere og beslutningstagere. Et højt tal betyder ikke nødvendigvis, at noget er teknisk komplekst – men at det **bør prioriteres højt** i designfasen.

| Trussel | Sandsynlighed | Konsekvens | Score | Risikoniveau |
|----------|----------------|-------------|--------|----------------|
| Uautoriseret adgang til kundedata | 5 | 5 | **25** | Kritisk |
| Manipuleret ordrestatus | 4 | 4 | **16** | Høj |
| Aflytning af API-trafik | 3 | 3 | **9** | Moderat |
| Fejllog eksponerer data | 2 | 3 | **6** | Lav |

#### f) Fra vurdering til handling
Når scoringen er gennemført, omsætter teamet resultaterne til konkrete handlinger.  
Eksempelvis:
- Risiko **25 (kritisk)**: Uautoriseret adgang til kundedata → **Tiltag:** rollebaseret adgangskontrol (RBAC) og inputvalidering på API-niveau.
- Risiko **16 (høj)**: Manipuleret ordrestatus → **Tiltag:** signering og validering af ordretransaktioner.
- Risiko **9 (moderat)**: Aflytning af API-trafik → **Tiltag:** tvungen HTTPS og TLS-konfiguration i alle services.
- Risiko **6 (lav)**: Fejllog eksponerer data → **Tiltag:** maskering af PII i logfiler.

Ved at koble hver risiko til en konkret kontrol får teamet et direkte link fra analyse til design – og kan senere verificere, at tiltaget faktisk reducerer risikoen.

#### e) Business Impact
Teamet vurderer konsekvenserne i et sprog, der giver mening for forretningen:
- **Kundetillid:** Databrud vil skade brandet og kundernes tillid.
- **Drift:** Manipulerede ordrer påvirker leveringer og økonomi.
- **Compliance:** Brud på persondataforordningen (GDPR) kan udløse bøder.

Resultatet deles med ledelsen, som prioriterer indsatsområder sammen med udviklerne.

---

### 7. Typiske fejl og faldgruber
- At springe risikovurderingen over, fordi systemet “ikke er følsomt nok”  
- At fokusere for meget på tekniske trusler og glemme forretningspåvirkningen  
- At mangle en fælles forståelse mellem udviklere og beslutningstagere  

---

### 8. Læringspointer
- Risikovurdering behøver ikke være tung – det handler om overblik og prioritering.  
- Brug en **Threat Matrix** til at kommunikere risiko visuelt.  
- Kombinér **risk scoring** med **business impact** for at sikre fælles beslutninger.  
- Brug resultaterne aktivt i næste fase (design), når sikkerhedskontroller vælges.  

---

### 9. Relation til SSDLC
Risikovurderingen ligger i **analysefasen**, men påvirker alle efterfølgende faser.  
Outputtet danner grundlag for:
- valg af sikkerhedskontroller i **designfasen**,
- teststrategi i **verifikationsfasen**,
- og driftsmonitorering i **deployment**.

---

### 10. Videre læsning / referencer
- [OWASP Risk Rating Methodology](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology)  
- [NIST SP 800-30: Risk Assessment Guide](https://csrc.nist.gov/publications/detail/sp/800-30/rev-1/final)  
- [OWASP ASVS v4.0.3 – V1 Architecture, Design and Threat Modeling]  
- [SSDLC – Microsoft Security Development Lifecycle (til sammenligning)](https://learn.microsoft.com/en-us/security/sdl/)

---

### 11. Bilag
Placeholder: `diagram.png` – illustrativ Threat Matrix-grafik.

---

*Udarbejdet som del af FoU-projektet “Sikkerhed som praksis” – UCN, 2025.*
