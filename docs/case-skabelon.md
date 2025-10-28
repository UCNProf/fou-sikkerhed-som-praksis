## Format for “Sikkerhed som praksis” – Casebeskrivelser

### 1. Titel

Kort og præcis, fx:
**“Broken Access Control i designfasen – adgangsstyring før koden skrives”**

---

### 2. SDLC-fase

Angiv hvilken fase i **Secure Development Lifecycle** casen relaterer sig til:

* Planlægning
* Design
* Implementering
* Test
* Deployment/Drift

Evt. marker med primær + sekundær fase (fx *primær: Design, sekundær: Implementering*).

---

### 3. Baggrund

Kort beskrivelse af det system eller produkt casen udspringer af.
Det kan være fiktivt (fx “en online bestillingsplatform for caféer”) eller realistisk (“et API til ordrehåndtering i en intern platform”).
Her etableres *forretningskonteksten* — hvad forsøger teamet at bygge, og hvilke sikkerhedskrav er relevante?

---

### 4. Problemstilling

Forklar hvilken *sikkerhedsudfordring* casen adresserer.
Fx: “Hvordan sikrer man, at kun autoriserede brugere kan se, oprette og ændre kundeordrer?”
Her kan du citere OWASP eller ASVS for at vise den teoretiske reference.

---

### 5. Teoretisk reference

Kobl problemstillingen til en eller flere **OWASP Top 10**, **ASVS controls** eller andre frameworks.
Fx:

* **OWASP A01: Broken Access Control**
* **ASVS 4.0.3 – V4: Access Control Verification Requirements**

---

### 6. Praktisk løsning / tiltag

Beskriv den konkrete tilgang, der gør teorien operationel i udviklingsarbejdet.
Her kan du fx vise:

* Et diagram (f.eks. *Access Control Matrix*)
* Et uddrag af et design-dokument
* Eksempel på policy i kode (pseudo eller rigtigt eksempel)
* Proces- eller værktøjsændringer (f.eks. “alle endpoints dokumenteres i API Spec med rollekrav”)

---

### 7. Typiske fejl og faldgruber

Beskriv hvad der ofte går galt i praksis, og hvordan det kan undgås.
Dette afsnit skaber læring og refleksion.

---

### 8. Læringspointer

Opsummer 3–5 konkrete takeaways:

* “Tænk adgangsstyring før koden skrives.”
* “Dokumentér roller og rettigheder eksplicit i designet.”
* “Automatisér validering, hvor det er muligt.”

---

### 9. Relation til SDLC

Et lille diagram eller kort tekst, der viser hvor i SDLC dette arbejde placeres, og hvordan det påvirker de øvrige faser.

---

### 10. Videre læsning / referencer

Links til OWASP, ASVS-sektioner, NIST, værktøjer eller cases fra industrien.

---

### 11. Bilag (valgfrit)

Eventuelle eksempler, kodeuddrag eller skabeloner, du vil gøre tilgængelige for læseren.

