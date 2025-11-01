# Broken Access Control i designfasen – adgangsstyring før koden skrives

## SDLC-fase
Primær: **Design**  
Sekundær: **Implementering**

---

## Baggrund
Et lille udviklingsteam arbejder på en intern bestillingsplatform, hvor medarbejdere kan oprette og håndtere kundeordrer.  
Under en gennemgang af arkitekturen opdager teamet, at rolle- og adgangsstyring ikke er specificeret — udviklerne er begyndt at kode endpoints uden klare krav til, hvem der må gøre hvad.

---

## Problemstilling
Hvordan sikrer man, at kun autoriserede brugere kan se, oprette og ændre ordrer, **før** systemet implementeres?  
Hvordan kan man designe adgangsstyring som en del af systemets arkitektur, i stedet for at lappe på det efterfølgende?

---

## Teoretisk reference
- **OWASP Top 10 (2021): A01 – Broken Access Control**  
- **ASVS 4.0.3 – V4: Access Control Verification Requirements**  
- **Princippet om Least Privilege (NIST SP 800-53 AC-6)**

---

## Praktisk løsning / tiltag
Teamet udarbejder en *Access Control Matrix* som en del af design-dokumentationen:

| Rolle | Se ordrer | Opret ordrer | Rediger ordrer | Slet ordrer |
|-------|------------|---------------|----------------|--------------|
| Administrator | ✅ | ✅ | ✅ | ✅ |
| Medarbejder   | ✅ | ✅ | ✅ | ❌ |
| Kunde         | ✅ (egne) | ✅ | ❌ | ❌ |

- Roller og rettigheder dokumenteres i designet.  
- API-specifikation (OpenAPI) opdateres med autorisationskrav pr. endpoint.  
- Testcases planlægges for både tilladte og afviste handlinger.  
- Implementeringsteamet anvender eksisterende auth-bibliotek og central policy.

Denne tilgang er bevidst valgt, fordi den kan udføres med enkle midler (f.eks. delt regneark eller dokument) og uden behov for specialværktøjer — i tråd med projektets mål om praksisnær og økonomisk realistisk sikkerhedsarbejde.

Se evt. [access-matrix-example.md](./access-matrix-example.md) for en trinvis, praksisnær metode.

---

## Typiske fejl og faldgruber
- Adgangsstyring overlades til implementeringsfasen.  
- Roller defineres implicit (“hvis du kan logge ind, må du alt”).  
- Manglende sammenhæng mellem forretningsroller og systemroller.  
- Ingen test af negative cases.
- Overkomplicerede løsninger, der ikke kan vedligeholdes i små teams.

---

## Læringspointer
- Tænk adgangsstyring **før koden skrives**.  
- Dokumentér roller og rettigheder eksplicit i designet.  
- Adskil roller, handlinger og dataområder.  
- Automatisér validering af rettigheder, hvor det er muligt.
- Gode sikkerhedsløsninger behøver ikke være komplekse – små, enkle tiltag kan gøre en stor forskel, når de gøres systematisk.

---

## Relation til SSDLC
Denne case hører primært hjemme i **designfasen**, men påvirker både **implementering** (kode) og **test** (verificering).  
En god rolle- og adgangsmodel reducerer risikoen for sikkerhedsfejl senere i forløbet.

---

## Videre læsning
- [OWASP Cheat Sheet – Access Control Design](https://cheatsheetseries.owasp.org/cheatsheets/Access_Control_Cheat_Sheet.html)  
- [ASVS 4.0.3 – Section V4](https://github.com/OWASP/ASVS/blob/master/4.0/en/0x14-V4-Access-Control.md)  
- [NIST SP 800-218 – Secure Software Development Framework](https://csrc.nist.gov/publications/detail/sp/800-218/final)

---

*En del af projektet **“Sikkerhed som praksis” – UCN, 2025.***
