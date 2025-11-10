# **Bilag 01 – Access Control Matrix**

**Relateret case:** Broken Access Control i designfasen – adgangsstyring før koden skrives  
**Fil:** `case-broken-access-control.md`  
**Forfatter:** Lars Nysom  
**Dato:** 2025-11-07  

---

## 1. Formål
Dette bilag dokumenterer det **Access Control Matrix-værktøj**, der anvendes i casen *Broken Access Control*.  
Formålet er at vise, hvordan små udviklingsteams kan etablere et praktisk overblik over roller, data og handlinger – uden brug af dyre værktøjer eller tunge processer.  
Bilaget fungerer som eksempel på lavpraktisk sikkerhedsdokumentation i designfasen.

---

## 2. Indhold

### Eksempel på Access Control Matrix
| Ressource / Handling | Administrator | Medarbejder | Kunde | Kommentar |
|----------------|----------------|--------------|---------|-------------|
| **Ordredata (alle)** | Læs / Opret / Rediger / Slet | Læs / Opret / Rediger | Læs (egne) / Opret | Adgangsgrænser baseret på rolle og ejerskab |
| **Brugerdata** | Læs / Rediger / Deaktivér | Læs | Læs (egne) | Kunde kan kun se egne oplysninger |
| **Rapporter** | Læs / Eksportér | Læs | ❌ | Rapporter er interne |
| **Systemopsætning** | Læs / Rediger | ❌ | ❌ | Kun administratorer |

---

### Designfase
Udvikling af adgangsstyring starter som en arkitekturøvelse, men i små teams skal løsningen kunne laves **hurtigt, forståeligt og uden store værktøjsinvesteringer**.  
Access Control Matrix bruges her som et **lavpraktisk samarbejdsredskab**, ikke som et formelt sikkerhedsdokument.

Praksisnær tilgang:
- Brug et simpelt regneark eller delt dokument (fx Google Sheets, Notion eller Miro).  
- Invitér både udviklere og forretningsfolk til at udfylde matricen sammen.  
- **Hold detaljeniveauet lavt** – målet er overblik, ikke fuld implementering.  
  Brug ikke meget tid på denne aktivitet; det vigtigste er en fælles forståelse.  
- Genbrug matricen i de næste faser og opdater den løbende, når nye funktioner eller roller opstår.

---

### Analysefase
I analysefasen fokuseres på **hvad der skal beskyttes** og **hvem der interagerer med systemet**.  
Små virksomheder kan klare dette med en kort workshop frem for et fuldt trusselsmodel-forløb.

Fremgangsmåde:
- Start med 3-5 brugerscenarier (fx “kunde opretter ordre”, “medarbejder retter pris”).  
- Identificér for hvert scenarie, hvilke data der håndteres, og hvor misbrug kan ske.  
- Brug whiteboard eller mindmap – dialogen er vigtigere end formatet.  
- Notér kun de mest sandsynlige risici for at bevare fokus.

---

### Implementering
Når matricen er på plads, fungerer den som **arbejdsredskab for udviklerne**.

**Lavpraktiske implementeringer:**
- Policy-based authorization i ASP.NET Core eller middleware/guards i Express/Node.  
- Rolledefinitioner kan ligge i en **konfigurationsfil** i stedet for en database.  
- Dokumentér regler i kodekommentarer eller README.  
- Automatisér validering med små enhedstests/integrationstests.

#### Kodeeksempel (Express / Node.js)

**1) Autorisations-middleware (rollebaseret + ejerskab)**

```js
// auth/authorize.js
function authorize({ roles = [], allowOwner = false } = {}) {
  return (req, res, next) => {
    const user = req.user; // antages sat af tidligere JWT-auth middleware
    if (!user) return res.status(401).json({ message: 'Unauthorized' });

    // Rollekrav (deny-by-default)
    if (roles.length > 0 && !roles.includes(user.role)) {
      if (!(allowOwner && req.params && user.id === req.params.id)) {
        return res.status(403).json({ message: 'Forbidden' });
      }
    }

    // Ejerskab (fx /users/:id er kun til egen profil, med mindre admin)
    if (allowOwner && req.params?.id && user.id === req.params.id) {
      return next();
    }

    if (roles.length === 0) return next();
    return next();
  };
}

module.exports = { authorize };
```

**2) Ruteeksempler, der afspejler Access Control Matrix**

```js
// routes/users.js
const express = require('express');
const router = express.Router();
const { authorize } = require('../auth/authorize');

// GET /users/:id
router.get('/:id',
  authorize({ roles: ['admin'], allowOwner: true }),
  async (req, res) => {
    const user = await db.users.findById(req.params.id);
    if (!user) return res.status(404).json({ message: 'Not found' });
    res.json(user);
  }
);

// DELETE /users/:id
router.delete('/:id',
  authorize({ roles: ['admin'] }),
  async (req, res) => {
    await db.users.delete(req.params.id);
    res.status(204).end();
  }
);

module.exports = router;
```

```js
// routes/orders.js
const express = require('express');
const router = express.Router();
const { authorize } = require('../auth/authorize');

router.get('/:id',
  async (req, res, next) => {
    req.order = await db.orders.findById(req.params.id);
    if (!req.order) return res.status(404).json({ message: 'Not found' });
    next();
  },
  (req, res, next) => {
    req.params.id = String(req.order.ownerId);
    next();
  },
  authorize({ roles: ['admin', 'employee'], allowOwner: true }),
  (req, res) => res.json(req.order)
);

module.exports = router;
```

**3) Minimal integrationstest (SuperTest)**
```js
const request = require('supertest');
const app = require('../app');

describe('Access control', () => {
  it('forbyder kunde at slette en bruger', async () => {
    const customerToken = await loginAs('customer1');
    await request(app)
      .delete('/users/abc123')
      .set('Authorization', `Bearer ${customerToken}`)
      .expect(403);
  });

  it('tillader admin at slette en bruger', async () => {
    const adminToken = await loginAs('admin1');
    await request(app)
      .delete('/users/abc123')
      .set('Authorization', `Bearer ${adminToken}`)
      .expect(204);
  });
});
```

---

### Testfase
Test af adgangsstyring kan udføres enkelt og effektivt.

Strategi:
- Brug matricen som tjekliste for både **positive** (må få adgang) og **negative** (må ikke få adgang) tests.  
- Skriv små, automatiserede tests, der forsøger uautoriserede kald.  
- Brug Postman, Insomnia eller `curl` – kræver ingen ekstra licenser.  
- Dokumentér resultaterne direkte i testscript eller som kommentarer.

Dette skaber **sammenhæng mellem design, kode og test** uden ekstra kompleksitet.

---

### Fordele
- Skaber fælles forståelse mellem forretning og udvikling.  
- Reducerer risikoen for *Broken Access Control*.  
- Gør det lettere at skrive sikkerhedstest og audits.  
- Kræver hverken store investeringer eller dedikerede sikkerhedsroller.

---

## 3. Refleksion eller konklusion
Access Control Matrix-tilgangen tydeliggør sammenhængen mellem **roller, handlinger og dataområder**.  
Bilaget viser, hvordan adgangsstyring kan gøres håndgribeligt og samarbejdsbaseret i små teams, og hvordan dokumentet kan fungere som reference gennem hele SSDLC-forløbet.

---

## 4. Referencer
- [OWASP Cheat Sheet – Access Control](https://cheatsheetseries.owasp.org/cheatsheets/Access_Control_Cheat_Sheet.html)  
- [OWASP ASVS V4 – Access Control Requirements](https://owasp.org/www-project-application-security-verification-standard/)  

---

*En del af projektet **“Sikkerhed som praksis” – UCN, 2025.***
