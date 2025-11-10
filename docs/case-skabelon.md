# [Titel på casen]

*Kort indledning (2–4 linjer), der beskriver casens formål, kontekst og relevans i projektet “Sikkerhed som praksis”.  
Her kan du fx nævne, hvilken praksis eller udfordring casen udspringer af, og hvordan den bidrager til forståelsen af sikkerhed som en del af udviklingsarbejdet.*

---

## 1. SSDLC-fase

Angiv hvilken fase i **Secure Software Development Lifecycle (SSDLC)** casen relaterer sig til.  
Der kan markeres både *primær* og *sekundær* fase, fx *primær: Design, sekundær: Implementering*.

De seks faser i SSDLC er:

1. Planlægning  
2. Analyse  
3. Design  
4. Implementering  
5. Test og integration  
6. Vedligeholdelse

---

## 2. Baggrund

Kort beskrivelse af det system eller produkt, som casen udspringer af.  
Det kan være fiktivt (fx “en online bestillingsplatform for caféer”) eller realistisk (“et API til ordrehåndtering i en intern platform”).  
Her etableres *forretningskonteksten* — hvad forsøger teamet at bygge, og hvilke sikkerhedskrav er relevante?

---

## 3. Problemstilling

Forklar hvilken *sikkerhedsudfordring* casen adresserer.  
Fx: “Hvordan sikrer man, at kun autoriserede brugere kan se, oprette og ændre kundeordrer?”  
Her kan du citere OWASP eller ASVS for at vise den teoretiske reference.

---

## 4. Teoretisk reference

Kobl problemstillingen til en eller flere **OWASP Top 10**, **ASVS-controls** eller andre frameworks.  
Fx:

* **OWASP A01: Broken Access Control**  
* **ASVS 4.0.3 – V4: Access Control Verification Requirements**

---

## 5. Praktisk løsning / tiltag

Beskriv den konkrete tilgang, der gør teorien operationel i udviklingsarbejdet.  
Her kan du fx vise:

* Et diagram (f.eks. *Access Control Matrix*)  
* Et uddrag af et design-dokument  
* Eksempel på policy i kode (pseudo eller rigtigt eksempel)  
* Proces- eller værktøjsændringer (f.eks. “alle endpoints dokumenteres i API-specifikationen med rollekrav”)

---

## 6. Typiske fejl og faldgruber

Beskriv hvad der ofte går galt i praksis, og hvordan det kan undgås.  
Dette afsnit skaber læring og refleksion.

---

## 7. Læringspointer

Opsummer 3–5 konkrete takeaways, fx:

* “Tænk adgangsstyring før koden skrives.”  
* “Dokumentér roller og rettigheder eksplicit i designet.”  
* “Automatisér validering, hvor det er muligt.”

---

## 8. Relation til SSDLC

Et lille diagram eller kort tekst, der viser hvor i SSDLC dette arbejde placeres, og hvordan det påvirker de øvrige faser.

---

## 9. Videre læsning / referencer

Links til OWASP, ASVS-sektioner, værktøjer eller cases fra industrien.  
(NIST-referencer frarådes i projektet.)

---

> **Bilag**
>
> Bilag oprettes som separate Markdown-filer og navngives konsekvent:
>  
> `case-[slug]-bilag-01.md`, `case-[slug]-bilag-02.md`, osv.  
>  
> Bilag kan fx indeholde kodeuddrag, diagrammer, tjeklister eller procesbeskrivelser, der understøtter casen.
