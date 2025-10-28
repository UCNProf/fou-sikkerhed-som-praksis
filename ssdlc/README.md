## SSDLC i praksis – Overblik

**Secure Software Development Lifecycle (SSDLC)** handler ikke om at tilføje endnu et lag proces oven på udviklingsarbejdet.
Det handler om at gøre **sikkerhed til en naturlig del af de aktiviteter, teams allerede udfører** – uanset om man arbejder med hele systemet eller blot én komponent.

De fleste mindre udviklingsvirksomheder dækker kun **dele af livscyklussen**.
Nogle udvikler et modul, andre står for integration, vedligeholdelse eller support.
SSDLC skal derfor forstås som en **ramme for refleksion og ansvar** – et fælles sprog for, hvordan man styrker sikkerheden dér, hvor man faktisk har indflydelse.

---

### Grundidéen

Sikkerhed integreres i hver fase af udviklingsprocessen, ikke som et særskilt trin til sidst.
Hver fase bidrager med sit eget perspektiv på sikkerhed:

| Fase                    | Fokus for sikkerhed i praksis                                                                                |
| ----------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Planlægning**         | Fastlæg sikkerhedsmål, risikovillighed og ansvar. Indbyg sikkerhed i projektplaner og sprint backlog.        |
| **Analyse**             | Forstå data, brugere og trusler. Kortlæg dataflows, trust boundaries og dokumentér sikkerhedskrav.           |
| **Design**              | Byg sikkerhed ind i arkitekturen. Arbejd efter principperne for *secure* og *privacy by design*.             |
| **Implementation**      | Kod sikkert. Brug code reviews, scanning, parametriserede forespørgsler og korrekt håndtering af secrets.    |
| **Test og integration** | Test sikkerheden som en del af CI/CD. Udfør både automatiske og manuelle tests af risikofyldte funktioner.   |
| **Vedligeholdelse**     | Overvåg, opdater og lær. Patch systemer, reager på hændelser og fasthold sikkerhed som en løbende aktivitet. |

---

### Pointen

SSDLC er ikke kun for dem, der styrer hele processen – det er en måde at **arbejde ansvarligt og bevidst** med sikkerhed, uanset om man leverer koden, integrationen eller driften.

Målet er ikke flere procedurer, men **mere bevidst praksis**:
at de beslutninger, vi alligevel træffer hver dag som udviklere, bliver truffet med sikkerhed for øje.

