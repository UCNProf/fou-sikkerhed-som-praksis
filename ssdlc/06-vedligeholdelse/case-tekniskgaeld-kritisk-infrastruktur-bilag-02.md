# Bilag 02 – Eksempel på security debt backlog

**Relateret case:** Sikkerhedsrelateret teknisk gæld i et system til kritisk infrastruktur  
**Formål:**  
Dette bilag viser et eksempel på, hvordan sikkerhedsrelateret teknisk gæld kan struktureres og prioriteres i en backlog. Backloggen er tænkt som et praktisk værktøj, der gør sikkerhedsarbejde synligt, prioriterbart og håndterbart over tid.

---

## 1. Hvad er en security debt backlog?

En security debt backlog er en eksplicit oversigt over kendte sikkerhedsrelaterede mangler og kompromiser i et system, som:

- endnu ikke er løst  
- er accepteret midlertidigt  
- indebærer en kendt risiko  

Formålet er ikke at eliminere al teknisk gæld, men at **kunne prioritere, dokumentere og reducere risiko systematisk**.

---

## 2. Struktur for backlog-elementer

Hvert backlog-element beskrives med følgende felter:

- **ID** – entydig reference  
- **Beskrivelse** – kort og konkret  
- **Risiko** – vurderet via risikomatrix (Bilag 01 / 01a)  
- **Konsekvens (GDPR)** – kort beskrivelse af potentielle effekter  
- **Anbefalet tiltag** – foreslået handling  
- **Estimat** – grov indsats (S/M/L)  
- **Status** – fx Open, Planned, Accepted, Mitigated  

Denne struktur understøtter dialog mellem udvikling, ledelse og compliance.

---

## 3. Eksempel på security debt backlog

| ID | Beskrivelse | Risiko | GDPR-konsekvens | Anbefalet tiltag | Estimat | Status |
|----|------------|--------|-----------------|------------------|---------|--------|
| SD-01 | Forældede tredjepartsbiblioteker med kendte sårbarheder | Høj | Potentiel udnyttelse kan føre til databrud | Opgradér eller udskift komponenter | M | Open |
| SD-02 | Inkonsekvent rolle- og rettighedsstyring | Høj | Uautoriseret adgang til sundhedsdata | Konsolider adgangsmodel | L | Planned |
| SD-03 | Mangelfuld sikkerhedslogning | Middel | Manglende sporbarhed ved hændelser | Udvid logging og loganalyse | M | Open |
| SD-04 | Forældet kryptografisk praksis | Middel–høj | Risiko for kompromittering af data | Opdater krypteringsmekanismer | M | Accepted |
| SD-05 | Uklar slette- og arkiveringspraksis | Høj | Brud på opbevaringsprincipper | Afklar og implementer sletteregler | L | Planned |

---

## 4. Prioriteringsprincipper

Når backloggen anvendes i praksis, anbefales følgende:

1. Backlog-elementer med **høj eller kritisk risiko** bør altid være synlige for ledelsen  
2. Små tiltag med stor risikoreduktion bør prioriteres tidligt  
3. Ikke-prioriterede elementer skal **accepteres eksplicit**  
4. Status bør revurderes løbende – især ved ændringer i systemet  

Backloggen er et levende artefakt og bør opdateres kontinuerligt.

---

## 5. Sammenhæng til udviklingsarbejdet

Security debt backloggen bør:

- integreres i den eksisterende produkt- eller tekniske backlog  
- bruges i planlægning og sprint-gennemgang  
- kobles til releases og større ændringer  
- anvendes som dokumentation ved interne og eksterne gennemgange  

Dette gør sikkerhedsarbejdet synligt uden at skabe parallelle processer.

---

## 6. Ledelsesmæssigt perspektiv

Backloggen fungerer som et beslutningsgrundlag, der:

- synliggør kendte risici  
- dokumenterer aktive fravalg  
- understøtter ansvarlig risikostyring  
- reducerer afhængighed af enkeltpersoners viden  

For systemer, der behandler sundhedsdata, kan dette være afgørende ved tilsyn og audits.

---

## 7. Konklusion

En security debt backlog gør det muligt at arbejde struktureret med sikkerhedsrelateret teknisk gæld uden at stoppe udviklingen. Den understøtter en praksis, hvor sikkerhed håndteres løbende og transparent – i tråd med både SSDLC og GDPR-krav.

---

> **Note:**  
> Eksemplet er illustrativt. Backloggen skal tilpasses systemets kompleksitet, risikoprofil og organisatoriske kontekst.
