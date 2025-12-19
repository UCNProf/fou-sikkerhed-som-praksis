# Sikkerhedsrelateret teknisk gæld i et system til kritisk infrastruktur

Denne case beskriver en realistisk udfordring i en virksomhed, der udvikler og vedligeholder et softwaresystem anvendt som del af kritisk infrastruktur. Systemet behandler følsomme sundhedsdata og har været i drift i mange år med løbende videreudvikling. Casen har fokus på sikkerhedsrelateret teknisk gæld og de organisatoriske udfordringer, der ofte gør det vanskeligt at prioritere arbejdet med at reducere den.

Casen er rettet mod virksomheder, ledere og beslutningstagere med ansvar for softwareudvikling, drift og risikostyring.

---

## 1. SSDLC-fase

**Primær fase:** Vedligeholdelse  
**Sekundære faser:** Planlægning, Analyse

Casen illustrerer, hvordan manglende prioritering i vedligeholdelsesfasen kan føre til gradvist stigende sikkerhedsrisiko og påvirke hele Secure Software Development Lifecycle (SSDLC).

---

## 2. Baggrund

Virksomheden driver og videreudvikler et softwaresystem, der indgår i driften af kritisk infrastruktur. Systemet understøtter centrale forretnings- og samfundsmæssige funktioner og behandler samtidig sundhedsdata, hvilket stiller høje krav til fortrolighed, integritet og tilgængelighed.

Systemet har været i drift i en længere årrække og er løbende blevet udbygget i tæt samarbejde med brugerne. Udviklingsafdelingen er relativt lille sammenlignet med virksomhedens samlede størrelse, og udviklingsarbejdet er i høj grad præget af inkrementelle ændringer og tilpasninger.

---

## 3. Problemstilling

Over tid har systemet opbygget betydelig **sikkerhedsrelateret teknisk gæld**. Denne gæld er ikke resultatet af enkeltstående fejl, men af mange pragmatiske beslutninger truffet under tidspres.

Eksempler på udfordringer kan være:

- Forældede afhængigheder og platformskomponenter  
- Arkitektoniske kompromiser, der vanskeliggør konsekvent adgangsstyring  
- Mangelfuld dokumentation af sikkerhedsforudsætninger  
- Midlertidige løsninger, der er blevet permanente  

Udviklingsteamet er bevidst om problemets omfang, men oplever, at det er vanskeligt at få afsat ressourcer til arbejdet. Sikkerhedsforbedringer konkurrerer med nye funktioner, lovændringer, driftsstabilitet og kundeønsker, og fremstår ofte som en omkostning uden umiddelbar synlig værdi.

---

## 4. Teoretisk reference

Casen relaterer sig til kendte udfordringer inden for softwaresikkerhed, herunder:

- Akkumuleret risiko som følge af manglende vedligeholdelse  
- Flere kategorier fra OWASP Top 10, afhængigt af systemets konkrete udformning  
- ASVS-krav relateret til vedligeholdelse, ændringer og teknisk konsistens  

Fælles for disse er, at risikoen sjældent kan reduceres gennem enkeltstående tiltag, men kræver en systematisk og vedvarende indsats.

---

## 5. Praktisk tilgang i virksomheden

Virksomheden vælger at adressere problemstillingen med fokus på realisme og forankring i den eksisterende udviklingspraksis frem for gennem et større “oprydningsprojekt”.

Tilgangen omfatter blandt andet:

- Overordnet kortlægning af sikkerhedsrelateret teknisk gæld  
- Grov prioritering baseret på sandsynlighed og potentiel konsekvens  
- Indarbejdelse af mindre sikkerhedsforbedringer som en del af almindelige udviklingsopgaver  
- Oversættelse af tekniske risici til konsekvenser for drift, compliance, ansvar og omdømme  

Målet er at reducere den samlede risikoprofil over tid og gøre sikkerhed til en legitim del af den løbende udvikling.

---

## 6. Typiske fejl og faldgruber

Virksomheder i lignende situationer støder ofte på de samme mønstre:

- Sikkerhedsarbejde udskydes til "næste større tekniske omlægning"  
- Risikoen undervurderes, fordi systemet har fungeret stabilt i mange år  
- Sikkerhed behandles som et teknisk anliggende frem for et organisatorisk ansvar  
- Manglende fælles sprog mellem udvikling, ledelse og forretning  

Disse forhold bidrager til, at sikkerhedsrelateret teknisk gæld fortsætter med at vokse.

---

## 7. Læringspointer

- Sikkerhedsrelateret teknisk gæld er en akkumuleret og stigende risiko  
- Vedligeholdelse er en aktiv og kritisk fase i SSDLC  
- Små, løbende forbedringer kan have stor effekt på den samlede sikkerhed  
- Manglende prioritering af sikkerhed er i sig selv en risikobeslutning  

---

## 8. Relation til SSDLC

Casen viser, hvordan manglende handling i vedligeholdelsesfasen:

- Øger den operationelle og regulatoriske risiko  
- Forringer fremtidige udviklingsmuligheder  
- Skaber yderligere teknisk kompleksitet  
- Flytter problemer frem i tid i stedet for at reducere dem  

Samtidig understreges det, at arbejdet med sikkerhed starter i planlægning og analyse, men skal fastholdes gennem hele systemets levetid.

---

## 9. Videre læsning / referencer

- OWASP Top 10  
- OWASP Application Security Verification Standard (ASVS)  
- ENISA – Threat Landscape og risici relateret til kritisk infrastruktur  

---

> **Note:**  
> Casen er anonymiseret og generaliseret. Den er baseret på virkelige problemstillinger, som mange virksomheder med systemer til kritisk infrastruktur og behandling af sundhedsdata kan genkende.
