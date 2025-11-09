# Designfasen i SSDLC – fra trusler til kontroller

## 1. Formål
Designfasen i SSDLC handler om at **omsætte viden om risici til konkrete designbeslutninger og sikkerhedskontroller**.  
Her bliver sikkerhed ikke tilføjet bagefter, men integreret i arkitekturen, dataflows og brugerroller.  

For små udviklingsteams handler det om at finde den rette balance mellem **struktur og pragmatik** – nok til at skabe overblik, men ikke så meget, at arbejdet går i stå.


## 2. Sammenhæng med analysefasen
Resultatet af [risikovurderingen i analysefasen](../02-analyse/risk-assessment) danner fundamentet for designarbejdet.  
I analysefasen blev de mest kritiske trusler og aktiver identificeret – i designfasen handler det om **hvordan** de håndteres.

| Analysefase | Output | Videre i designfasen |
|--------------|---------|----------------------|
| Risk Assessment | Identificerede risici og deres konsekvens | Bruges som input til trusselsmodellering (STRIDE) |
| Business Impact | Overblik over forretningsmæssige konsekvenser | Bruges til at vurdere behov for kontroller |
| Prioritering | Oversigt over vigtigste indsatsområder | Bruges til at styre designbeslutninger |


## 3. Aktiviteter i designfasen
Designfasen kan gennemføres som en serie af korte, fokuserede workshops.  
Hver aktivitet bidrager til et samlet overblik over trusler, prioriteringer og tiltag.

| Aktivitet | Formål | Output | Case |
|------------|--------|---------|------|
| **Design af kontroller (Broken Access Control)** | Omsætte prioriterede risici til konkrete tekniske tiltag. | Eksempler på sikre designmønstre og kode. | [Broken Access Control](broken-access-control-case.md) |


## 4. Designfasens output
Når designfasen er gennemført, skal teamet stå med:

- Et dokumenteret overblik over trusler (fx i et simpelt regneark eller Markdown-dokument).  
- En prioriteret liste over tekniske risici og backlog-opgaver.  
- Besluttede sikkerhedskontroller – med henvisning til ASVS-krav eller interne retningslinjer.  
- Eventuelle designartefakter (diagrammer, sekvensbeskrivelser, API-specifikationer).


## 5. Typiske faldgruber
- **For meget teori:** Modellerne må ikke stå i vejen for handling – brug dem som samtaleredskaber.  
- **Ingen opfølgning:** STRIDE og prioritering giver kun værdi, hvis resultaterne omsættes til konkrete krav og tests.  
- **Isoleret sikkerhedsarbejde:** Designfasen bør involvere både udviklere, produktejer og drift – sikkerhed er et fælles ansvar.  


## 6. Relation til SSDLC
Designfasen udgør **broen mellem analyse og implementering**.  
Outputtet bliver direkte input til:

- **Implementering:** hvor kontrollerne kodes og testes.  
- **Verifikation:** hvor sikkerhedskrav dokumenteres og valideres.  
- **Drift:** hvor trusler og hændelser overvåges i praksis.


## 7. Videre læsning
- [OWASP Threat Modeling Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html)  
- [OWASP ASVS 4.0.3 – V1: Architecture, Design and Threat Modeling Requirements](https://github.com/OWASP/ASVS/blob/master/4.0/OWASP%20Application%20Security%20Verification%20Standard%204.0.3-en.pdf)  
- [OWASP SAMM 2.0 – Design: Threat Assessment](https://owaspsamm.org/model/design/threat-assessment/)  

---

*Udarbejdet som del af FoU-projektet “Sikkerhed som praksis” – UCN, 2025.*


