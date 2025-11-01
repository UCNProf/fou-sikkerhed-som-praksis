# Secure Software Development Lifecycle (SSDLC)

Dette katalog samler cases, guides og eksempler struktureret efter faserne i **Secure Software Development Lifecycle (SSDLC)**.  
Formålet er at gøre det let for udviklingsteams at finde inspiration og praksisnære tiltag, der passer til netop den fase, de arbejder i.

---

## Struktur

Indholdet er opdelt i seks hovedfaser:

1. **Planlægning** – sikkerhedsmål, risikovurdering og awareness
2. **Analyse** – trusselsmodellering, databeskyttelse og krav til sikkerhed
3. **Design** – arkitektur, adgangsstyring, sikkerhedsprincipper
4. **Implementering** – sikker kodning, afhængigheder, secret management
5. **Test & Integration** – statisk og dynamisk test, review og automatisering
6. **Drift & Vedligeholdelse** – patching, overvågning, incident response

---

## Case-format

Alle cases følger den fælles skabelon, som findes i [`/docs/case-skabelon.md`](../docs/case-skabelon.md).  
En case skal typisk indeholde:

- **Baggrund** og forretningskontekst  
- **Problemstilling** med reference til OWASP, ASVS eller tilsvarende  
- **Praktisk løsning** og tiltag i udviklingsarbejdet  
- **Typiske fejl** og **læringspointer**

Skabelonen gør det muligt at beskrive både realistiske og fiktive situationer, og understøtter en praksisnær læringstilgang.

---

## Sådan bidrager du

1. Find den fase, casen passer til.
2. Opret en ny mappe med en kort, sigende titel  
   f.eks. `03-design/broken-access-control/`
3. Opret en `README.md` i den mappe og udfyld den efter skabelonen.
4. Tilføj eventuelt kode, diagrammer eller bilag under samme mappe.
5. Send et pull request med en kort beskrivelse af dit bidrag.

Bidrag, der bygger på egne erfaringer, undervisning eller konkrete projekter, er særligt velkomne — også selv om de ikke er “perfekte”.  
Målet er at dele realistiske erfaringer med, hvordan **sikkerhed kan blive en naturlig del af udviklingspraksis**.

---

## Inspiration

- [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/)
- [OWASP SAMM](https://owaspsamm.org/)
- [NIST Secure Software Development Framework (SSDF)](https://csrc.nist.gov/publications/detail/sp/800-218/final)

---

*Dette materiale er en del af projektet **“Sikkerhed som praksis”**, der udvikles ved UCN som led i et FoU-projekt om praksisnær awareness og implementering af softwaresikkerhed i små udviklingsvirksomheder.*
