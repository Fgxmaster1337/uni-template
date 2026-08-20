---
name: trans
description: "Uebersetzungs-Check — strenger PASS/FAIL-Test gegen erkennbare Uebersetzungen. NUR bei englischem Skript. Laeuft NACH /para."
allowed-tools: Read, Grep, Glob
---

## Zweck

Strenger Gatekeeper gegen erkennbare Uebersetzungen. Prueft gezielt, ob Saetze die als GELB durchgegangen sind tatsaechlich akzeptabel sind — oder verkleidete Uebersetzungen.

## Der Test

Fuer jeden nicht-trivialen Satz:

1. Englisches Original in `docs/folien_text/` finden
2. Deutschen Satz und englisches Original NEBENEINANDER stellen
3. **Haette jemand diesen deutschen Satz schreiben koennen, OHNE das englische Original gelesen zu haben?**

- **JA → PASS**
- **NEIN → FAIL** — Satz komplett neu schreiben

## Erkennungsmerkmale einer Uebersetzung

- **Satzstruktur** folgt dem englischen Original
- **Kernwoerter** sind 1:1-Uebersetzungen
- Man koennte den **englischen Satz rekonstruieren**
- **Dieselben Informationen in derselben Reihenfolge**

## Wann NICHT pruefen

- Kein Folientreffer → automatisch PASS
- Feststehende Fachbegriffe
- Definitionen bei Define-Aufgaben

## Ausgabeformat

```
DE: "[deutscher Satz]"
EN: "[englisches Original]" — [datei:Zeile]
Urteil: PASS | FAIL
```

Ergebnis: X PASS / Y FAIL. Bei FAIL > 0: korrigierte Antwort ausgeben.
Bei FAIL: Satz KOMPLETT loeschen und frei neu schreiben — nicht am alten Satz herumschrauben.
