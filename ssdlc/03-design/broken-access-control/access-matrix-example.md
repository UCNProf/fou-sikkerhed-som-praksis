# Eksempel på Access Control Matrix

Dette er et udvidet eksempel, der kan bruges som udgangspunkt for design-dokumentation eller arkitekturworkshops i små udviklingsteams.  
Formålet er at skabe **overblik over roller, data og handlinger** – uden at det kræver dyre værktøjer eller tunge processer.

| Ressource / Handling | Administrator | Medarbejder | Kunde | Kommentar |
|----------------------|----------------|--------------|---------|------------|
| **Ordredata (alle)** | Læs / Opret / Rediger / Slet | Læs / Opret / Rediger | Læs (egne) / Opret | Adgangsgrænser baseret på rolle og ejerskab |
| **Brugerdata** | Læs / Rediger / Deaktivér | Læs | Læs (egne) | Kunde kan kun se egne oplysninger |
| **Rapporter** | Læs / Eksportér | Læs | ❌ | Rapporter er interne |
| **Systemopsætning** | Læs / Rediger | ❌ | ❌ | Kun administratorer |

---

## 1. Designfase

Udvikling af adgangsstyring starter ofte som en arkitekturøvelse, men i små teams skal løsningen kunne laves **hurtigt, forståeligt og uden store værktøjsinvesteringer**.  
I denne fase bruges *Access Control Matrix* som et **lavpraktisk samarbejdsredskab**, ikke som et formelt sikkerhedsdokument.

Sådan gøres det praksisnært og realistisk:

- Brug et **simpelt regneark eller delt dokument** (fx Google Sheets, Notion, Miro).  
- **Invitér både udviklere og forretningsfolk** til at udfylde matricen sammen. Det sikrer fælles forståelse af roller og handlinger.  
- **Hold detaljeniveauet lavt** – målet er overblik, ikke fuld implementering.  
  Brug ikke meget tid på denne aktivitet; det vigtigste er, at teamet får en fælles forståelse, som kan udvikles over tid.    
- **Genbrug matricen** som reference i de næste faser – det gør arbejdet effektivt og kontinuerligt.  
- **Opdater løbende**, når nye funktioner eller roller opstår.

På den måde bliver adgangsstyring en **integreret, agil del af designarbejdet**, i stedet for en tung sikkerhedsaktivitet, der kræver specialroller eller eksterne konsulenter.

---

## 2. Analysefase

I analysefasen handler det om at forstå **hvad der skal beskyttes**, og **hvem der interagerer med systemet**.  
I små virksomheder kan dette ofte klares med en hurtig session frem for et fuldt trusselsmodelleringsforløb.

Praksisnær tilgang:

- Start med **3-5 typiske brugerscenarier** (f.eks. "kunde opretter ordre", "medarbejder retter pris", "admin sletter bruger").  
- Identificér for hver, hvilke data der håndteres, og hvor der kan ske misbrug.  
- Brug en whiteboard-session eller online mindmap – det vigtigste er dialogen, ikke dokumentformatet.  
- Notér kun **de mest sandsynlige risici**, så teamet bevarer fokus.

Dette niveau af analyse er tilstrækkeligt til at danne et realistisk grundlag for designbeslutninger i et mindre team.

---

## 3. Implementering

Når matricen er på plads, bliver den et **arbejdsredskab for udviklerne**.  
I stedet for at lave komplekse frameworks, kan man ofte bruge eksisterende funktioner i det sprog eller framework, teamet allerede arbejder i.

Eksempler på lavpraktiske implementeringer:

- Brug **policy-based authorization** i ASP.NET Core, eller **middleware guards** i Express/Node.  
- Gem rolledefinitioner i en **konfigurationsfil** i stedet for en tung database.  
- Dokumentér reglerne i kodekommentarer eller README, så nye udviklere forstår dem.  
- Automatisér validering med et simpelt testscript eller enhedstest, så fejl opdages tidligt.

Det vigtigste er, at implementeringen er **forståelig, vedligeholdelsesvenlig og realistisk** for teamets ressourcer.

---

## 4. Testfase

Test af adgangsstyring behøver ikke være kompliceret.  
En enkel tilgang kan give stor effekt, hvis den udføres systematisk.

Praksisnær teststrategi:

- Brug matricen som tjekliste for både **positive** (må få adgang) og **negative** (må ikke få adgang) tests.  
- Skriv små, automatiserede tests der forsøger at tilgå ressourcer med forkerte roller.  
- Brug Postman, Insomnia eller `curl` – det kræver ingen ekstra licenser.  
- Dokumentér resultaterne kort i samme fil eller som kommentarer i testscriptet.

Ved at bygge test på den eksisterende matrix får teamet **sammenhæng mellem design, kode og test** uden ekstra kompleksitet.

---

## Fordele
- Skaber fælles forståelse mellem forretning og udvikling.  
- Reducerer risikoen for “Broken Access Control”.  
- Gør det lettere at skrive sikkerhedstest og audits senere.  
- Kræver hverken store investeringer eller dedikerede sikkerhedsroller.

---

*Eksemplet kan frit genbruges og tilpasses andre projekter.  
En del af projektet **“Sikkerhed som praksis” – UCN, 2025.***
