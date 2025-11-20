# Bidrag til *Sikkerhed som praksis*

Tak fordi du vil bidrage til projektet!  
Dette repository samler **praksisnær viden om sikker softwareudvikling** med fokus på små udviklingsteams. Materialet udvikles som en del af projektet *Sikkerhed som praksis* og bruges i undervisning, cases og samarbejde med virksomheder.

Målet er at gøre sikkerhed mere tilgængeligt, konkret og relevant for udviklere, tech leads og beslutningstagere.


## Hvad du kan bidrage med

Du kan bidrage på mange måder:

- **Tilføje en case** – en konkret erfaring eller situation knyttet til én eller flere SSDLC-faser. Benyt gerne case-skabelonen i `docs/cases/case-skabelon.md`.
- **Udvikle en mini-guide** – kort, handlingsorienteret materiale om et specifikt emne (fx “Threat Modeling for små teams”).
- **Dele refleksioner** – via *Discussions*-fanen på GitHub.
- **Forbedre eksisterende indhold** – formatering, rettelser, flere eksempler eller udvidelser.

## Brug af fiktiv kontekst

Dette repository anvender to fiktive virksomheder – **NordicApps** og **Café Sanchez** – som fælles referencepunkt i alle cases, eksempler og bilag. Ved at bruge en gennemgående kontekst sikrer vi ensartethed på tværs af materialet og undgår at involvere virkelige virksomheder.

Når du bidrager til repoet:

- Brug kun NordicApps og Café Sanchez som organisatorisk eller forretningsmæssig kontekst, med mindre andet er aftalt.
- Undgå at introducere egne fiktive virksomheder.
- Sørg for, at beskrivelser, diagrammer og kodeeksempler passer ind i den eksisterende fortælling.
- Henvis gerne til virksomhedsfilerne i `docs/virksomheder/` for at sikre konsistens.
- Undlad at bruge virkelige virksomhedsnavne, kundedata eller cases fra konkrete projekter.

Formålet er at gøre materialet tilgængeligt, genbrugeligt og overskueligt for både undervisere, studerende og samarbejdspartnere.

## Sådan indsender du ændringer

1. **Fork projektet**  
   Klik på *Fork* øverst på siden og opret din egen kopi af repo’et.

2. **Lav en ny branch**  
   Brug et beskrivende navn, fx `add-threat-modeling-case` eller `update-guide-authentication`.

3. **Lav dine ændringer**  
   Sørg for at følge strukturen i repo’et, og brug markdown-format.

4. **Commit og push**  
   Skriv en kort og klar commit-besked, fx “Added case on secure session handling”.

5. **Opret et Pull Request (PR)**  
   Beskriv kort, hvad dit bidrag indeholder, og hvilken SDLC-fase det relaterer sig til.

## Review- og feedbackproces

Alle bidrag bliver manuelt gennemgået for kvalitet, tydelighed og sammenhæng.  
Målet er ikke at finde fejl – men at hjælpe bidraget til at blive så brugbart som muligt.

### Review-kriterier

1. **Form og struktur**  
   - Overholder bidraget case-skabelonen?  
   - Er sprog og tone i tråd med projektets stil (praksisnært og inkluderende)?  

2. **Teknisk og faglig gennemgang**  
   - Er eksemplerne forståelige og relevante for udviklere?  
   - Henvises der korrekt til frameworks (OWASP, ASVS, NIST osv.)?  
   - Undgår bidraget følsomme eller proprietære oplysninger?  

3. **Kontekst og konsistens**
   - Er konteksten korrekt knyttet til NordicApps og/eller Café Sanchez?
   - Placeres materialet korrekt i SSDLC-faserne?
   
4. **Feedback og dialog**  
   Kommentarer lægges direkte i PR’en, fx:

   "Godt eksempel – måske kan du tilføje lidt om hvordan teamet opdagede problemet?"
   
   "Overvej at henvise til ASVS kapitel 4 her, så det bliver tydeligere."
   
   "Super relevant erfaring – kan vi lægge den under Design-fasen i stedet?"

Når eventuelle rettelser er på plads, merges PR’en, og bidragyderen krediteres i commit-historikken og evt. i docs/Sikkerhed_som_praksis_model.md.

## Retningslinjer for cases og guides

- Hold fokus på praksis og erfaringer, ikke teori alene.
- Brug konkrete eksempler fra udviklingsarbejde, også gerne i pseudokode.
- Henvis gerne til **OWASP**, **ASVS** eller andre frameworks, men skriv i et tilgængeligt sprog.
- Du må gerne nævne teknologier, men undgå at reklamere for produkter eller kommercielle værktøjer.
- Del kun **ikke-følsomme erfaringer** og ingen oplysninger om kunder, kodebaser eller fortrolige systemer.

## Licens og kreditering

Ved at indsende bidrag accepterer du, at indholdet udgives under
**Creative Commons BY-SA 4.0**.

Det betyder, at:

- Du krediteres som bidragyder.
- Andre må frit genbruge og videreudvikle dit indhold, så længe de angiver kilde og deler under samme licens.

## Tak

Dette projekt bygger på fællesskab og erfaringsdeling.
Hvert bidrag – stort som småt – hjælper med at gøre sikkerhed som praksis mere tilgængelig for udviklere, teams og undervisere.

“Ingen har hele svaret – men sammen kan vi bygge en bedre praksis.”