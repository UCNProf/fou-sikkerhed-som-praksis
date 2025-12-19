# Bilag 03 – Eksempel på accepteret risiko og ledelsesbeslutning

**Relateret case:** Sikkerhedsrelateret teknisk gæld i et system til kritisk infrastruktur  
**Formål:**  
Dette bilag dokumenterer, hvordan en virksomhed eksplicit kan acceptere en kendt sikkerhedsrisiko relateret til teknisk gæld, herunder den tilhørende ledelsesbeslutning, begrundelse og opfølgning. Bilaget understøtter ansvarlig risikostyring i systemer, der behandler sundhedsdata.

---

## 1. Kontekst

Virksomheden har identificeret en række elementer i sin security debt backlog, som indebærer kendte risici. På grund af ressourcebegrænsninger, afhængigheder og forretningsmæssige hensyn er det ikke muligt at adressere alle risici samtidigt.

For at sikre transparens og ansvarlighed er der etableret en proces for **eksplicit risikoejerskab og dokumenteret accept**.

---

## 2. Beskrivelse af den accepterede risiko

| Felt | Indhold |
|-----|--------|
| Risiko-ID | SD-04 |
| Kort beskrivelse | Forældet kryptografisk praksis i afgrænset del af systemet |
| Relateret backlog-element | Security debt backlog, Bilag 02 |
| Vurderet risiko | Middel–høj |
| Behandling af sundhedsdata | Ja |
| Berørte systemdele | Ældre integrationskomponent |

---

## 3. Risikovurdering (sammenfatning)

- **Sandsynlighed:** Lav–middel  
- **Konsekvens:** Høj (potentiel kompromittering af sundhedsdata)  
- **Samlet risikoniveau:** Middel–høj  

Risikoen er vurderet ved hjælp af risikomatricen beskrevet i Bilag 01a.

---

## 4. Begrundelse for accept

Ledelsen har besluttet midlertidigt at acceptere risikoen på baggrund af følgende forhold:

- Systemdelen er isoleret og eksponeres ikke direkte mod eksterne brugere  
- En teknisk opdatering kræver arkitektoniske ændringer, som pt. ikke er planlagt  
- Der er iværksat kompenserende foranstaltninger (fx netværksbegrænsning og overvågning)  
- Risikoen vurderes som lavere end konsekvensen ved uplanlagt nedetid i kritisk infrastruktur  

Beslutningen er truffet med henblik på at balancere sikkerhed, stabil drift og forretningsmæssige hensyn.

---

## 5. Ledelsesbeslutning

| Element | Beskrivelse |
|-------|-------------|
| Beslutning | Risiko accepteres midlertidigt |
| Risikoejer | Direktør for IT og Digitalisering |
| Gyldighed | 6 måneder |
| Næste revurdering | 2025-06-01 |
| Beslutningsgrundlag | Risikomatrix (Bilag 01a) og security debt backlog (Bilag 02) |

Risikoejeren er ansvarlig for, at risikoen revurderes rettidigt.

---

## 6. Kompenserende foranstaltninger

Følgende tiltag er implementeret for at reducere den faktiske risiko:

- Begrænset adgang til berørte komponenter  
- Øget overvågning og logning  
- Skærpet beredskab for hændelseshåndtering  
- Dokumentation af arkitektoniske antagelser  

Tiltagene reducerer sandsynligheden for udnyttelse, men eliminerer ikke risikoen.

---

## 7. Opfølgning og exit-strategi

Accept af risikoen er midlertidig og forudsætter:

- At der udarbejdes en plan for permanent udbedring  
- At risikoen genvurderes ved større ændringer i systemet  
- At beslutningen genbesøges senest ved udløb af gyldighedsperioden  

Målet er at fjerne eller reducere risikoen til et acceptabelt niveau.

---

## 8. Ledelsesmæssig refleksion

Accept af risiko er ikke et fravalg af ansvar, men en aktiv beslutning.  
Ved systemer, der behandler sundhedsdata, er dokumentation af denne beslutning afgørende for:

- ansvarlig ledelse  
- compliance med GDPR’s krav om passende sikkerhed  
- dialog med tilsynsmyndigheder  

Manglende dokumentation kan i sig selv udgøre en væsentlig risiko.

---

## 9. Konklusion

Dette bilag viser, hvordan virksomheder kan håndtere sikkerhedsrelateret teknisk gæld på en moden og ansvarlig måde. Ved at dokumentere accepteret risiko og ledelsesbeslutninger skabes transparens, ejerskab og mulighed for løbende forbedring – i tråd med både SSDLC og GDPR.

---

> **Note:**  
> Eksemplet er generaliseret og skal tilpasses virksomhedens organisatoriske struktur og governance-model.
