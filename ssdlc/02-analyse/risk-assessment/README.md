# Risikovurdering i praksis

## 1.  Analysefasen i SSDLC

Denne case beskriver den **tekniske risikovurdering**, som udføres i **analysefasen** af SSDLC – efter den overordnede forretningsmæssige risikovurdering i planlægningsfasen. Formålet er at identificere konkrete trusler, vurdere sandsynlighed og konsekvens, og skabe et beslutningsgrundlag for design af sikkerhedskontroller.

## 2. SSDLC-fase
*Primær:* Analyse  
*Sammenhæng:* Resultaterne bruges i designfasen til valg af sikkerhedskontroller

## 3. Baggrund
Café-kæden **CoffeeShopChain** er i gang med at udvikle et nyt **ordrehåndteringssystem**, der håndterer bestillinger fra POS-terminaler, kundeapps og leveringsintegrationer. Systemet skal håndtere kundeoplysninger, betalingsstatus og interne produktdata.  

Udviklingsteamet står i analysefasen og skal beslutte, hvilke dele af systemet der kræver særlig beskyttelse, før de går videre til design og implementering. Formålet er at få et fælles billede af risikoen – både teknisk og forretningsmæssigt.

## 4. Problemstilling
Hvordan kan et lille udviklingsteam identificere og vurdere de mest kritiske sikkerhedsrisici i systemet – uden at drukne i teori eller komplicerede metoder?  
Målet er at prioritere indsatsen, så de mest alvorlige risici håndteres først.

## 5. Teoretisk reference
- **OWASP Top 10:** A04 – Insecure Design, A01 – Broken Access Control  
- **OWASP ASVS 4.0.3:** V1 Architecture, Design and Threat Modeling  
- **NIST SP 800-30:** Guide for Conducting Risk Assessments  
- **SSDLC-princip:** Risikoidentifikation og -vurdering i analysefasen som grundlag for designbeslutninger.

## 6. Praktisk løsning / tiltag
### a) Identifikation af aktiver
Teamet starter med at identificere, hvad der skal beskyttes:
- Kundedata (navn, kontakt, ordrer)
- Betalingsinformationer (transaktionsstatus, ikke kortdata)
- API’er mellem POS, App og backend
- Admin-dashboard til produktstyring

### b) Identifikation af trusler  
Teamet identificerer mulige trusler mod hvert aktiv ved at diskutere **realistiske eksempler på, hvordan sårbarheder typisk opstår**. Formålet er at skabe forståelse for trusselsbilledet – ikke at dokumentere faktiske angreb eller producere omfattende dokumentation.

- **Uautoriseret adgang til ordrer eller kundedata:**  
  Kan opstå, hvis adgangskontrol i API’et ikke håndhæves korrekt, fx manglende tokenvalidering eller fejl i rollebaseret adgang. Et eksempel er, at en bruger ændrer et endpoint-kald og får adgang til en andens ordrer.  

- **Manipulation af ordrestatus:**  
  Kan ske, hvis data ikke valideres på serveren, eller hvis forbindelsen mellem POS og backend ikke er krypteret. Et klassisk eksempel er et *man-in-the-middle*-angreb, hvor en angriber ændrer status fra “ikke betalt” til “betalt”.  

- **Aflytning af API-trafik mellem POS og backend:**  
  Truslen opstår, når kommunikationen ikke er beskyttet med TLS, og en tredjepart kan opsnappe følsomme oplysninger som tokens eller ordredetaljer.  

- **Utilsigtet dataeksponering via fejllogning:**  
  Kan ske, hvis fejlmeddelelser eller logfiler indeholder følsomme oplysninger som kundemail eller adgangstokens, som senere eksponeres gennem CI/CD-pipelines eller fejlanalyser.  

### c) Risk scoring
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

### d) Threat Matrix (tekstbaseret eksempel)
Når scoringerne er fastlagt, kan teamet visualisere dem i en enkel Threat Matrix for at skabe overblik og kommunikere risikoen til andre interessenter.

| Sandsynlighed | Lav konsekvens | Mellem konsekvens | Høj konsekvens |
|---------------|----------------|------------------|----------------|
| **Lav** | – | Logdata eksponeret |  |
| **Mellem** | – | API-aflytning |  |
| **Høj** | – | Manipuleret ordrestatus | Uautoriseret adgang til kundedata |

*(En visuel version af denne matrix kan tilføjes som `diagram.png` i mappen.)*

### e) Business Impact
Teamet vurderer konsekvenserne i et sprog, der giver mening for forretningen:
- **Kundetillid:** Databrud vil skade brandet og kundernes tillid.
- **Drift:** Manipulerede ordrer påvirker leveringer og økonomi.
- **Compliance:** Brud på persondataforordningen (GDPR) kan udløse bøder.

Resultatet deles med ledelsen, som prioriterer indsatsområder sammen med udviklerne.

### f) Fra vurdering til handling

Når scoringen er gennemført, omsætter teamet resultaterne til konkrete handlinger. Det er vigtigt, at arbejdet herefter **prioriteres systematisk**, så indsatsen bruges dér, hvor den gør størst forskel.

Teamet opdeler tiltagene i fire niveauer:

| Prioritet                                    | Risikoniveau | Tiltag                                                                                                                  | Begrundelse                                                                                |
| -------------------------------------------- | ------------ | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **1 – Kritisk (handle straks)**              | Risiko 25    | **Uautoriseret adgang til kundedata** → Indfør *rollebaseret adgangskontrol (RBAC)* og *inputvalidering på API-niveau*. | Brud på persondataforordningen (GDPR) og tab af kundetillid kan få alvorlige konsekvenser. |
| **2 – Høj (planlæg hurtigst muligt)**        | Risiko 16    | **Manipuleret ordrestatus** → Implementér *signering og validering af ordretransaktioner*.                              | Påvirker virksomhedens drift og økonomi direkte.                                           |
| **3 – Moderat (indfør ved næste iteration)** | Risiko 9     | **Aflytning af API-trafik** → Aktivér *tvungen HTTPS* og korrekt *TLS-konfiguration* i alle services.                   | Kan udnyttes af angribere, men sandsynligheden er lavere med interne netværk.              |
| **4 – Lav (overvåg og forbedr senere)**      | Risiko 6     | **Fejllog eksponerer data** → Maskér PII[^1] i logfiler og justér fejlhåndtering.                                           | Konsekvensen er begrænset, men tiltaget er nemt at implementere.                           |

Ved at koble hver risiko til et konkret kontrol- og prioriteringsniveau får teamet et klart beslutningsgrundlag. Det gør det tydeligt, **hvad der skal gøres først**, og **hvilke tiltag der kan planlægges ind i fremtidige iterationer**.

Tilgangen hjælper samtidig med at balancere sikkerhed og produktivitet — en vigtig forudsætning for, at små teams faktisk får gennemført arbejdet.

## 7. Typiske fejl og faldgruber i risikovurdering

Selv en enkel risikovurdering kan miste sin værdi, hvis den udføres uden et klart formål. Erfaringen fra både undervisning og praksis viser, at mindre udviklingsteams ofte støder på de samme udfordringer, når de forsøger at integrere sikkerhed i arbejdet.

### Hyppige faldgruber

- **At springe vurderingen over:** Systemet virker måske “ufarligt”, men selv små datalæk kan få store konsekvenser, hvis systemet senere kobles til andre dele af infrastrukturen.
- **At fokusere for snævert:** Mange fokuserer på tekniske sårbarheder, men glemmer forretningspåvirkningen — driftstab, kundetillid eller omdømme.
- **Manglende fælles forståelse:** Hvis udviklere og ledelse ikke taler samme sprog, bliver risikoen enten undervurderet eller overreageret på.
- **At gøre processen for tung:** Risikovurderingen skal støtte arbejdet, ikke forsinke det. For detaljerede modeller dræner ofte fokus og energi.
- **At mangle opfølgning:** Risikoer ændrer sig, når systemet vokser. Hvis vurderingen kun sker én gang, bliver den hurtigt forældet.

En god risikovurdering skal være let at gentage, enkel at kommunikere og altid tilgængelig som beslutningsstøtte – ikke som bilag.

## 8. Læringspointer og refleksion

Når risikovurdering gøres konkret, bliver den et aktivt værktøj – ikke en formel øvelse. Denne case viser, at små teams kan arbejde effektivt med sikkerhed, hvis fokus ligger på forståelse frem for formalia.

### Vigtige pointer

- Risikovurdering handler om **indsigt, ikke dokumentation**.
- En **Threat Matrix** giver visuelt overblik og gør det lettere at kommunikere resultater.
- **Risk scoring** skaber et fælles sprog mellem teknik og forretning.
- **Business impact** hjælper med at oversætte tekniske fund til ledelsesbeslutninger.
- Arbejdet stopper ikke efter analysen – brug resultaterne aktivt i design, test og drift.

Afslutningsvis bør risikovurdering ses som en **løbende dialog** mellem teknik og forretning. Jo mere den integreres i hverdagen, desto mindre føles den som ekstraarbejde – og desto større bliver den faktiske sikkerhed.

## 9. Relation til SSDLC
Risikovurderingen ligger i **analysefasen**, men påvirker alle efterfølgende faser.  
Outputtet danner grundlag for:
- valg af sikkerhedskontroller i **designfasen**,
- teststrategi i **verifikationsfasen**,
- og driftsmonitorering i **deployment**.

## 10. Videre læsning / referencer
- [OWASP Risk Rating Methodology](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology)  
- [NIST SP 800-30: Risk Assessment Guide](https://csrc.nist.gov/publications/detail/sp/800-30/rev-1/final)  
- [OWASP ASVS v4.0.3 – V1 Architecture, Design and Threat Modeling](https://github.com/OWASP/ASVS/blob/master/4.0/OWASP%20Application%20Security%20Verification%20Standard%204.0.3-en.pdf)  
- [SSDLC – Microsoft Security Development Lifecycle (til sammenligning)](https://learn.microsoft.com/en-us/security/sdl/)

## 11. Bilag
Placeholder: `diagram.png` – illustrativ Threat Matrix-grafik.

---

*Udarbejdet som del af FoU-projektet “Sikkerhed som praksis” – UCN, 2025.*

[^1]: **PII (Personally Identifiable Information)** – personhenførbare oplysninger, dvs. data som direkte eller indirekte kan bruges til at identificere en person (f.eks. navn, e-mail, IP-adresse eller kundedata).
