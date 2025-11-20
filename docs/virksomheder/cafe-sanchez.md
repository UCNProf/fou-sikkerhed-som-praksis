# Café Sanchez – Virksomhedsprofil

Café Sanchez er en fiktiv restaurant- og cafékæde, der fungerer som primær kundecase i projektet *Sikkerhed som praksis*. Virksomheden bruges som forretningskontekst i cases, SSDLC-eksempler, STRIDE-stories og andet materiale i repoet. 

Formålet med profilen er at skabe en realistisk, sammenhængende og genbrugelig ramme for eksempler, der involverer POS-systemer, ordrer, kundedata og interne processer.

---

## 1. Introduktion

**Café Sanchez** er en mellemstor dansk café- og restaurantkæde med flere lokationer fordelt i større byer. Kæden er kendt for hurtig service, takeaway-løsninger og en afslappet atmosfære. Virksomheden er i vækst og har de seneste år satset på digitale løsninger for at effektivisere drift og forbedre kundeoplevelsen.

Caféens ledelse har prioriteret digital modernisering, men mangler teknisk indsigt. Derfor har de engageret NordicApps som deres faste udviklingspartner til at udvikle og drifte en række systemer, der understøtter driften.

---

## 2. Organisation og roller

Café Sanchez består af:

- En mindre central ledelse, der håndterer økonomi, marketing og drift  
- Caféledere på hver lokation  
- Medarbejdere i køkken og front-of-house  
- Eksterne samarbejdspartnere for IT, vedligehold og logistik  

Virksomheden har **ingen intern IT-afdeling**, hvilket gør dem afhængige af eksterne leverandører som NordicApps for både udvikling og drift.

---

## 3. Kunder og produkter

Café Sanchez tilbyder:

- Café- og restaurantoplevelser  
- Online bestilling og takeaway  
- Catering til mindre events  
- Kundeklub og loyalitetsprogram  

Deres målgruppe er primært:

- Studerende  
- Unge voksne  
- Pendlere  
- Mindre familier  
- Kontormiljøer, der bestiller frokost  

Kædens kerneforretning afhænger i stigende grad af digitale systemer, der håndterer bestillinger, betalinger og driftsstyring.

---

## 4. IT-systemer

NordicApps udvikler og drifter for Café Sanchez:

- **POS-systemet** på caféerne  
- **Kundeordreskærmen** (Customer Order Display)  
- **Management-dashboard** til administration, sortiment, priser og tilbud  
- **En API-platform** til ordrer, lager og cafédata  
- **Notifikations- og beskedsystemer**  
- **Eksport og integration** til økonomisystemer  

Disse systemer er en central del af repoets cases, hvor de danner kontekst for:

- Access control  
- Inputvalidering  
- Trusselsmodellering  
- Logning og overvågning  
- DRM-lignende datakonsistens  
- POS-relaterede sikkerhedsrisici  

---

## 5. Teknologi og arkitektur

Systemerne, som NordicApps bygger til kæden, benytter:

- En webbaseret POS-løsning (tablet eller touchskærm)  
- Centraliseret backend i .NET  
- Databaser i PostgreSQL og Redis  
- En bestillingsflow-frontend i Node.js  
- API’er til mobile bestillinger og selvbetjening  
- Dashboard med rollebaseret adgang  
- Deployment via GitHub + kundens cloud-løsning  

Som kunde stiller Café Sanchez få tekniske krav – de fokuserer primært på pris, hurtig levering og stabil drift.

---

## 6. Driftsmæssige behov og udfordringer

Café Sanchez oplever typisk:

- Udfordringer med **spidsbelastninger**, hvor mange kunder bestiller samtidigt  
- Fejl i ordrehåndtering, der påvirker serviceoplevelsen  
- Behov for stabil POS-integration mellem lokationerne  
- Manglende overblik over lager og bestillinger  
- Afhængighed af få medarbejdere, som forstår systemerne  
- Frustration over nedetid eller langsom support  

Disse forhold gør virksomheden meget afhængig af NordicApps’ løsninger og drift.

---

## 7. Sikkerhedsmodenhed

Sikkerhed er ikke en bevidst del af Café Sanchez’ arbejdsgange. Deres primære fokus er:

- Driftssikkerhed  
- Hurtig ekspedition  
- Kort træningstid for personale  
- Stabil mobil- og webbestilling  

Ledelsen forventer, at deres IT-leverandør “tager sig af sikkerhed”, uden at stille konkrete krav. 

Reelle risici for virksomheden omfatter:

- Manipulation af priser og rabatter i POS  
- Uautoriseret adgang til dashboard  
- Tab eller læk af kundedata (navn, kontaktinfo, ordrer)  
- Mangelfuld logning ved misbrug  
- Fejlhåndtering af betalinger under travlhed  
- Risici ved integration til økonomisystemer  

Dette gør virksomheden ideel som eksempel på en kunde, der *ikke selv* driver sikkerhed, men påvirkes direkte af den.

---

## 8. Relation til repoets cases

Café Sanchez optræder som:

- Kunden i **Broken Access Control-casen**  
- Eksemplet i **STRIDE-stories**  
- Kontekst i **design- og analysefasemateriale**  
- Virksomheden bag **POS-økosystemet**, som bruges til at forklare SSDLC-faser  
- Scenariet hvor små teams møder virkelige krav om sikkerhed  

De danner en praktisk ramme, der gør det muligt at koble tekniske sikkerhedsprincipper til konkrete forretningsscenarier.

---

## 9. Kort version (til brug i cases)

**Café Sanchez** er en dansk café- og restaurantkæde uden egen IT-afdeling. De anvender digitale systemer til POS, bestilling, drift og administration, som udvikles og driftes af NordicApps. Virksomheden har begrænset teknisk indsigt og stiller få sikkerhedskrav, men er stærkt afhængig af stabile løsninger. Reelle risici omfatter uautoriseret adgang, fejl i ordrehåndtering og læk af kundedata.

---

## 10. Ultrakort version (til SSDLC og bilag)

**Café Sanchez** – dansk cafékæde uden IT-afdeling.  
Systemer: POS, dashboard, bestillingsflow, API’er.  
Afhængig af NordicApps.  
Fokus: drift, hurtig service.  
Risici: uautoriseret adgang, pris- og ordre-manipulation, datalæk.

