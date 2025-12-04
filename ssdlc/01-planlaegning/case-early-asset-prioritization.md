# **Case: Tidlig afklaring af kritiske aktiver i et nyt ordrestyringssystem**

*Denne case viser, hvordan NordicApps arbejder med sikkerhed allerede i planlægningsfasen ved at identificere kritiske aktiver og tydeliggøre, hvilke handlinger systemet aldrig må understøtte. Casen demonstrerer, hvordan små udviklingsteams kan skabe et realistisk og praksisnært sikkerhedsgrundlag—uden tunge modeller eller lange dokumenter.*

## **1. SSDLC-fase**

**Primær:** 1. Planlægning
**Sekundær:** 2. Analyse

## **2. Baggrund**

NordicApps har fået en ny kunde: en lille kæde af takeaway-restauranter, som ønsker et simpelt ordrestyringssystem med:

* et kundeinterface (mobil-web)
* et internt bestillingsdashboard
* integration til et eksisterende økonomisystem

Kunden har haft problemer med manuel håndtering, fejlregistreringer og enkelte mistænkelige ordreændringer i deres tidligere løsning. De ønsker ikke “et stort og tungt system”, men forventer, at sikkerheden **er tænkt ind fra start**, da de arbejder med persondata, betalinger og driftskritiske workflows.

Teamet består af fire udviklere og en softwarearkitekt med begrænsede ressourcer. Derfor er målet at træffe *realistiske og prioriterede* sikkerhedsvalg i fase 1, så arbejdet i de næste faser bliver lettere.

## **3. Problemstilling**

Hvordan kan NordicApps i planlægningsfasen identificere de **kritiske aktiver** og definere klare **”må-ikke-handlinger”**, så teamet tidligt skaber et sikkerhedsgrundlag for design- og analysearbejdet—uden at bruge omfattende metoder?

## **4. Teoretisk reference**

Casen baserer sig på praksisprincipper fra:

* **Security by Design**
* **OWASP ASVS – V1: Architecture, Design and Threat Modeling Requirements**
* **OWASP Proactive Controls – C1: Define Security Requirements**

## **5. Praktisk løsning / tiltag**

NordicApps-afholder et kort planlægningsmøde (45 min.), hvor teamet udarbejder to centrale artefakter:

### **A. Liste over kritiske aktiver** (første version)

| Kategori    | Aktiv                                     | Hvorfor kritisk?                           |
| ----------- | ----------------------------------------- | ------------------------------------------ |
| Data        | Kundeoplysninger (navn, tlf., adresse)    | GDPR, risiko for misbrug                   |
| Data        | Ordrehistorik                             | Kan manipuleres mhp. svindel               |
| Funktion    | Oprettelse og ændring af ordre            | Kerneforretning, påvirker drift            |
| Funktion    | Rollebaserede handlinger for medarbejdere | Risiko for misbrug eller insiderfejl       |
| Integration | Økonomisystemet                           | Fejl eller misbrug kan give økonomiske tab |

Målet er ikke at være fuldstændig, men at identificere det *allermest kritiske*, så teamet kan begynde at arbejde iterativt med trusselsanalyse i fase 2.

### **B. Definition af "må-ikke-handlinger"**

Teamet opstiller fem handlinger, systemet **aldrig** må understøtte—hverken som følge af designvalg eller fejlimplementering:

1. **En medarbejder må ikke kunne ændre ordrestatus uden audit-log.**
2. **Kunder må ikke kunne se andre kunders ordrehistorik.**
3. **Eksterne systemer må ikke kunne udløse betalinger uden verificeret identitet.**
4. **Uautoriserede brugere må ikke kunne tilgå det interne dashboard via URL-gætning.**
5. **En integration må ikke kunne ændre ordredata uden eksplicit godkendelse.**

Øvelsen tager 10–15 minutter og kræver ingen tekniske detaljer. Den har to gevinster:

* teamet etablerer et tidligt sikkerhedsblik,
* de får konkrete pejlemærker til designfasen.

## **6. Typiske fejl og faldgruber**

Små teams oplever ofte:

* **Overdokumentation i fase 1**, hvor man forsøger at beskrive “alt”.
* **For få sikkerhedskrav**, fordi “vi tager det, når vi kommer til design”.
* **Uklarhed om roller og ansvar**, især i forhold til interne systemer.
* **Manglende aftale om sikkerhedsniveau**, hvilket fører til ad-hoc-beslutninger senere.

Casen demonstrerer en tilgang, der undgår begge ekstremer:
**simpel, prioriteret og rettet mod handling i de kommende faser.**

## **7. Læringspointer**

1. Start med *det mest kritiske*—ikke med alt.
2. Definér “må-ikke-handlinger”: de skaber klarhed og forebygger fejl senere.
3. Sikkerhed i planlægning handler om *retning*, ikke tung dokumentation.
4. Tidlige beslutninger reducerer risiko, scope creep og uklarhed.
5. Et lille team kan styrke sikkerheden markant med 45 minutters struktureret arbejde.

## **8. Relation til SSDLC**

Tidlig identifikation af aktiver og må-ikke-handlinger påvirker:

* **Analysefasen** (trusselstragt: hvad er mest sandsynligt / mest kritisk?)
* **Designfasen** (access matrix, krav til API design, flow for autorisation)
* **Implementering** (sikre defaults og klare sikkerhedskrave)
* **Test** (målrettede negative tests på må-ikke-handlinger)

Planlægningen fungerer dermed som fundament for hele forløbet.

## **9. Videre læsning / referencer**

* OWASP ASVS – Section V1: Architecture, Design & Threat Modeling
* OWASP Proactive Controls – C1

