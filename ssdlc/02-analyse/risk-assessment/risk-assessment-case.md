# Risikovurdering i praksis

*Denne case viser, hvordan et lille udviklingsteam kan arbejde struktureret med risikovurdering i analysefasen af SSDLC – uden at drukne i teori.  
Casen er udviklet som en del af FoU-projektet “Sikkerhed som praksis”, hvor målet er at gøre sikkerhedsarbejde konkret, tilgængeligt og gennemførligt i små udviklingsteams.*

---

## 1. SSDLC-fase

**Primær:** Analyse  
**Sekundær:** Design  

Risikovurderingen gennemføres i analysefasen for at skabe et fælles billede af systemets risici, inden designet besluttes.  
Resultatet anvendes som input til designfasens trusselsmodellering og valg af sikkerhedskontroller.

---

## 2. Baggrund

Café-kæden **CoffeeShopChain** er ved at udvikle et nyt **ordrehåndteringssystem**, der håndterer bestillinger fra **POS-terminaler**[^1], kundeapps og leveringsintegrationer.  
Systemet lagrer kundeoplysninger, produktdata og betalingsstatus og skal fungere både i butikkerne og på tværs af lokationer.

Udviklingsteamet skal i analysefasen beslutte, hvilke dele af systemet der kræver særlig beskyttelse, før arbejdet fortsætter i design- og implementeringsfaserne.

---

## 3. Problemstilling

Hvordan kan et lille udviklingsteam identificere og vurdere de mest kritiske sikkerhedsrisici i systemet – uden at drukne i komplicerede metoder?  
Målet er at skabe et klart beslutningsgrundlag for, **hvilke risici der kræver handling først**, og hvordan de bedst kommunikeres til ledelsen.

---

## 4. Teoretisk reference

Casen trækker på følgende anerkendte kilder:

- **OWASP Top 10:** A04 – Insecure Design, A01 – Broken Access Control  
- **OWASP ASVS 4.0.3:** V1 Architecture, Design and Threat Modeling  
- **OWASP Risk Rating Methodology**  
- **ISO/IEC 27005:** Information Security Risk Management  

---

## 5. Praktisk løsning / tiltag

### a) Identifikation af aktiver  
Teamet starter med at kortlægge, *hvad der skal beskyttes*:

- Kundedata (navn, kontakt, ordrer)  
- Betalingsinformationer (transaktionsstatus, ikke kortdata)  
- API’er mellem POS, app og backend  
- Admin-dashboard til produktstyring  

### b) Identifikation af trusler  
Herefter diskuteres realistiske trusler mod hvert aktiv for at skabe fælles forståelse af trusselsbilledet:

- **Uautoriseret adgang til kundedata:**  
  Manglende tokenvalidering eller fejl i rollebaseret adgang kan give brugere indsigt i andres ordrer.  
- **Manipulation af ordrestatus:**  
  Hvis data ikke valideres server-side, kan en angriber ændre status fra “ikke betalt” til “betalt”.  
- **Aflytning af API-trafik:**  
  Manglende TLS-beskyttelse gør det muligt at opsnappe følsomme oplysninger.  
- **Utilsigtet dataeksponering via fejllogning:**  
  Fejlmeddelelser eller logfiler kan afsløre kundemails eller tokens.

### c) Risk scoring  
Risiko vurderes som: **risiko = sandsynlighed × konsekvens**,  
begge på en skala fra **1 (lav)** til **5 (høj)**.

| Trussel | Sandsynlighed | Konsekvens | Score | Risikoniveau |
|----------|----------------|-------------|--------|----------------|
| Uautoriseret adgang til kundedata | 5 | 5 | **25** | Kritisk |
| Manipuleret ordrestatus | 4 | 4 | **16** | Høj |
| Aflytning af API-trafik | 3 | 3 | **9** | Moderat |
| Fejllog eksponerer data | 2 | 3 | **6** | Lav |

### d) Threat matrix  
En enkel matrix giver visuelt overblik over, hvor risikoen er størst.

| Sandsynlighed | Lav konsekvens | Mellem konsekvens | Høj konsekvens |
|---------------|----------------|------------------|----------------|
| **Lav** | – | Logdata eksponeret | – |
| **Mellem** | – | API-aflytning | – |
| **Høj** | – | Manipuleret ordrestatus | Uautoriseret adgang til kundedata |

*(En grafisk version kan tilføjes som bilag.)*

### e) Business impact  
Teamet vurderer konsekvenserne i et sprog, som ledelsen kan forstå:

- **Kundetillid:** Databrud vil skade brandet og kundernes tillid.  
- **Drift:** Manipulerede ordrer påvirker leveringer og økonomi.  
- **Compliance:** Brud på GDPR kan udløse bøder.

### f) Fra vurdering til handling  
Risici omsættes til konkrete tiltag og prioriteres i fire niveauer:

| Prioritet | Risikoniveau | Tiltag | Begrundelse |
|------------|---------------|--------|--------------|
| **1 – Kritisk (handle straks)** | 25 | Rollebaseret adgangskontrol (RBAC) og server-side validering. | Databrud og lovbrud kan få alvorlige konsekvenser. |
| **2 – Høj (planlæg hurtigt)** | 16 | Signering og validering af ordretransaktioner. | Påvirker virksomhedens drift og økonomi. |
| **3 – Moderat (næste iteration)** | 9 | Tvungen HTTPS og korrekt TLS-konfiguration. | Mindsker risikoen for aflytning. |
| **4 – Lav (overvåg)** | 6 | Maskering af følsomme data i logfiler. | Nem forbedring med lav risiko. |

---

## 6. Typiske fejl og faldgruber

- At **springe vurderingen over**, fordi systemet virker “ufarligt”.  
- At **fokusere for snævert** på tekniske trusler uden forretningsperspektiv.  
- At **mangle fælles sprog** mellem teknik og ledelse.  
- At **gøre processen for tung**, så arbejdet stopper op.  
- At **glemme opfølgning**, når systemet ændrer sig.

---

## 7. Læringspointer

- Risikovurdering skal være **operationel og gentagelig**.  
- **Simpel scoring** skaber fælles forståelse på tværs af roller.  
- **Business impact** forbinder teknik og ledelse.  
- Resultaterne skal **bruges aktivt** i design- og testfaserne.  
- Balancen mellem sikkerhed og produktivitet er afgørende for, at små teams får det gjort.

---

## 8. Relation til SSDLC

Risikovurderingen ligger i **analysefasen**, men påvirker alle efterfølgende faser:

- **Design:** Input til trusselsmodellering (STRIDE) og valg af kontroller.  
- **Implementering:** Grundlag for udviklings- og testprioriteringer.  
- **Drift:** Bruges som reference ved hændelser og revisioner.

> **Overgang til designfasen:**  
> Resultatet her danner udgangspunkt for **trusselsmodellering (STRIDE)** og **teknisk risikoprioritering (Likelihood × Impact)**, hvor truslerne konkretiseres i forhold til arkitektur og dataflows.

---

## 9. Videre læsning / referencer

- [OWASP Risk Rating Methodology](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology)  
- [OWASP ASVS v4.0.3 – V1: Architecture, Design and Threat Modeling](https://github.com/OWASP/ASVS/blob/master/4.0/OWASP%20Application%20Security%20Verification%20Standard%204.0.3-en.pdf)  
- [ENISA Indispensable baseline security requirements for the procurement of secure ICT products and services](https://docs.evolveum.com/midpoint/compliance/enisa-baseline/?utm_source=chatgpt.com)  
- [Advancing Software Security in the EU] (https://eipacc.eu/wp-content/uploads/2021/08/ENISA-Report-Advancing-Software-Security-in-the-EU.pdf?utm_source=chatgpt.com)

---

*Udarbejdet som del af FoU-projektet “Sikkerhed som praksis” – UCN, 2025.*

[^1]: **POS (Point of Sale)** – systemet eller terminalen, hvor kunden gennemfører sin bestilling og betaling.  
I denne case bruges betegnelsen om baristaens kasseterminal i caféen.
