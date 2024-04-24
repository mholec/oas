---
stoplight-id: ixz3tv6qm3a05
title: 3. Konvence
---

# Konvence

API dodržuje mimo standardů níže uvedené konvence.


| Vlastnost      | Formátování                     | Příklad                  |
| -------------- | ------------------------------- | ------------------------ |
| JSON struktura | camelCase                       | { "firstName" : "John" } |
| Datum a čas    | RFC 3339 - YYYY-MM-DDTHH:MM:SSZ | 2024-12-24T12:05:00Z     |
| Datum          | RFC 3339 - YYYY-MM-DD           | 2024-12-24               |
| Doba trvání    | RFC 3339 - PTnMnS               | PT20M10S                 |


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