# **Bilag 03 – Mini-tjekliste for små teams (Planlægningsfase)**

## **1. Formål**

Mini-tjeklisten er designet til små udviklingsteams (5–10 personer), som ønsker et realistisk og praksisnært sikkerhedsgrundlag uden tunge modeller. Listen kan bruges før sprint 0, som del af projektets opstart eller ved større ændringer.

## **2. Indhold – Mini-tjekliste**

### **A. Systemforståelse**

* [ ] Systemets primære brugere er identificeret
* [ ] De vigtigste forretningsflows er kendt
* [ ] Der er afklaret, hvilke eksterne systemer vi integrerer med

### **B. Kritiske aktiver**

* [ ] Vi har en liste over de 3–6 mest kritiske aktiver
* [ ] Der er aftalt, hvorfor hvert aktiv er vigtigt
* [ ] Der er noteret konsekvenser ved kompromittering

### **C. "Må-ikke" handlinger**

* [ ] Der er defineret 3–5 handlinger systemet aldrig må understøtte
* [ ] Hver må-ikke-handling har en forretningsmæssig begrundelse
* [ ] Handlingerne er forstået af både udviklere og PO/arkitekt

### **D. Sikkerhedsniveau**

* [ ] Teamet har aftalt et realistisk “serviceniveau” for sikkerhed
* [ ] Der er valgt et passende framework (fx ASVS light)
* [ ] Security-reviews er aftalt (hyppighed og ansvar)

### **E. Output til næste fase**

* [ ] Vi har afklaret, hvilke aktiver der skal trusselsmodelleres først
* [ ] Eventuelle risici eller spørgsmål er noteret til Fase 2 – Analyse
* [ ] Dokumenterne er tilgængelige for hele teamet (GitHub, wiki, osv.)

## **3. Refleksion**

Mini-tjeklisten blev udviklet, fordi mange små teams hos NordicApps oplevede, at sikkerhed i planlægningen enten blev for tung eller for løs. Tjeklisten giver en *lav tærskel* for at komme i gang og bliver ofte brugt i forbindelse med kickoffs, nye features eller større refactorings.

## **4. Referencer**

* OWASP ASVS (anvendt som inspirationskilde, ikke som fuld implementering)

