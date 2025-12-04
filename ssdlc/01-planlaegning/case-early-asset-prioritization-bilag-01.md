# **Bilag 01 – Aktiver og “må-ikke” handlinger**

**Relateret case:** Tidlig afklaring af kritiske aktiver i et nyt ordrestyringssystem
**Fil:** `case-early-asset-prioritization.md`
**Forfatter:** NordicApps (fiktion)
**Dato:** 2025-01-XX

## **1. Formål**

Dette bilag dokumenterer den første version af NordicApps’ liste over kritiske aktiver i det nye ordrestyringssystem samt de “må-ikke” handlinger, som teamet definerede i planlægningsfasen. Formålet er at give et struktureret grundlag for trusselsmodellering og designbeslutninger i de efterfølgende SSDLC-faser.

## **2. Indhold**

### **A. Kritiske aktiver**

| Kategori    | Aktiv                                                  | Hvorfor kritisk?                           |
| ----------- | ------------------------------------------------------ | ------------------------------------------ |
| Data        | Kundeoplysninger (navn, tlf., adresse)                 | Persondata (GDPR), risiko for lækage       |
| Data        | Ordrehistorik                                          | Kan manipuleres mhp. svindel               |
| Funktion    | Oprettelse, ændring og annullering af ordre            | Kerneforretning, driftskritisk             |
| Funktion    | Rollebaserede handlinger (staff, manager, integration) | Risiko for misbrug eller insiderfejl       |
| Integration | Økonomisystemets ordreinterface                        | Fejl eller misbrug kan give økonomiske tab |
| Logging     | Audit logs                                             | Skal være manipulationssikre               |

Aktiverne udgør grundlaget for den første iteration af trusselsanalysen i Fase 2.

### **B. Definerede “må-ikke” handlinger**

1. En medarbejder må **ikke** kunne ændre ordrestatus uden audit-log.
2. En kunde må **ikke** kunne se eller gætte sig til andre kunders ordredata.
3. Eksterne systemer må **ikke** kunne påvirke betalinger uden verificeret identitet.
4. Uautoriserede brugere må **ikke** kunne tilgå det interne dashboard via URL-gæt.
5. En integration må **ikke** kunne ændre ordredata uden eksplicit godkendelse.

## **3. Refleksion**

Bilaget blev brugt af NordicApps’ arkitekt og udviklere som referencepunkt i både designfasen og i udarbejdelsen af access-control matrixen (senere bilag). Det gav en fælles forståelse for, hvad der faktisk er kritisk – og hvad teamet kan nedprioritere.

## **4. Referencer**

* OWASP ASVS v4 – V1 Architectural Requirements
* OWASP Proactive Controls – C1

