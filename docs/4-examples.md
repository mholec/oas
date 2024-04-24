---
stoplight-id: 9w3j5x6uvljre
title: 4. Příklady
---

# Příklady

Na této stránce najdete příklady požadavků, které by se odesílali na REST API, aby bylo možné realizovat design mobilní aplikace prezentované v mém školení.

### Zobrazení dashboardu

Endpoint pro senzory již vrátí automaticky senzory seřazené dle vychozího pravidla (název). 

```json
https://localhost:5001/sensors
```

### Zobrazení dashboardu - průměrné hodnoty u senzorů

Využijeme endpoint pro metriky. Výchozí agregační funkce je již průměr, čili pouze nastavíme scale na hodiny a omezíme čas na posledních 5 minut (obrazovka mobilní aplikace ukazuje čas 9:41). Povinně musíme uvést všechny ID senzorů.

```json
https://localhost:5001/metrics?datefrom=2024-04-01T09:36:00&dateto=2024-04-01T09:41:00&scale=hour&sensorids=S1-HALA-A-PRG,S2-HALA-A-PRG,S1-HALA-B-PRG,S2-HALA-B-PRG,S3-HALA-B-PRG
```

### Detail senzoru

Použijeme endpoint pro detail senzoru

```json
https://localhost:5001/sensors/S1-HALA-A-PRG
```

### Detail senzoru - graf

Pro vykreslení grafu potřebujeme opět metriky. Uvedeme požadované ID senzoru a časový rozsah (na obrázku od 1.4. do 9.4.). Granularitu volíme po dnech a implicitně je již zvolená agregační funkce AVG (průměr).

```json
https://localhost:5001/metrics?datefrom=2024-04-01T00:00:00&dateto=2024-09-01T00:00:00&scale=day&sensorids=S1-HALA-A-PRG
```

### Detail senzoru - naměřené hodnoty

Endpoint measurings vrací jednotlivé hodnoty. Filtrujeme dle senzoru, volíme hodnoty dle data (od 13:00) a na obrazovku zobrazíme 5 záznamů. 

```json
https://localhost:5001/measurings?sensorid=S1-HALA-A-PRG&datefrom=2024-04-01T13:00:00&pagesize=5
```


### Detail alertu + aktualizace

Jednoduché načtení upozornění dle ID (je shodné s ID senzoru). V případě aktualizace je to stejný endpoint a jen použijeme replace metodu PUT.

```json
https://localhost:5001/alerts/S1-HALA-A-PRG
```