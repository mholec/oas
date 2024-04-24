---
stoplight-id: ixz3tv6qm3a05
title: 3. Konvence
---

# Konvence

API využívá standardní formátování dat ve formátu JSON s **camelCase** syntaxí. Při práci s časovými údaji se používá jako základní jednotka **sekunda**.

## Chybové struktury
Veškeré chyby vychází ze standardu [RFC 9457](https://datatracker.ietf.org/doc/html/rfc9457). Typická podoba chybové struktury je:

```json
{
  "type": "https://datatracker.ietf.org/doc/html/rfc9457",
  "title": "Internal Server Error",
  "status": 500,
  "detail": "Available on dev environment"
}
```

V případě validačních chyb je struktura rozšířena o seznam chyb:

```json
{
  "type": "https://datatracker.ietf.org/doc/html/rfc9457",
  "title": "Validation Failed",
  "status": 400,
  "detail": "See errors for more details",
  "errors": [
    {}
  ]
}
```