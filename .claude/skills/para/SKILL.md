---
name: para
description: "Paraphrase-Check — vergleicht verbale Saetze mit dem englischen Original. NUR bei Faechern mit englischem Skript."
allowed-tools: Read, Grep, Glob
---

## Kernprinzip

Feststehende Definitionen und englische Fachbegriffe duerfen woertlich uebernommen werden. ALLES ANDERE muss in eigenen Worten formuliert sein. Dieser Check oeffnet die Folien neu und vergleicht jeden verbalen Satz mit dem Original.

## Qualitaetsziel

**0% ROT — immer. ROT ist nicht verhandelbar.**
- Mindestens **70% GRUEN** bei allen Fragetypen
- GELB nur bei unvermeidbarer begrifflicher Ueberlappung in kurzen Phrasen

## PFLICHT: Drei-Phasen-Schreiben

**Phase A — Recherche:** Folien greppen, Fachbegriffe verifizieren.
**Phase B — Erklaersatz-Extrakt:** Pro Konzeptpunkt EIN formloser Satz: "Was ist der PUNKT?" Rekonstruktions-Test: Kann man aus dem deutschen Satz das englische Original rekonstruieren? Ja → nochmal.
**Phase C — Freies Schreiben:** Antwort NUR aus den Erklaersaetzen. Englischen Originaltext ab hier NICHT mehr verwenden.

## Techniken

1. **Eigene Rahmenbilder** statt Skript-Formulierungen
2. **Eigene Beispiele** statt Skript-Aufzaehlungen uebersetzen
3. **Eigene Analyse** zwischen Fakten einbauen
4. **Andere Reihenfolge** als das Skript wo moeglich
5. **Selektieren** statt alle Unterpunkte oberflaechlich auflisten

## Ablauf

1. Verbale Saetze sammeln
2. Folienstelle finden (in `docs/folien_text/`)
3. Vergleich: **GRUEN** (eigenstaendig) | **GELB** (kurze Ueberlappung) | **ROT** (erkennbare Uebersetzung)
4. Rote/Gelbe Stellen umformulieren

## Ausgabeformat

```
Satz: "[mein Satz]"
Folie: [datei.txt:Zeile] "[Original]" oder KEIN TREFFER
Bewertung: GRUEN | GELB | ROT
Aktion: - (ok) | Umformulierung: "[neuer Satz]"
```

Am Ende: Anzahl Gruen/Gelb/Rot. Bei Gelb/Rot: direkt korrigieren.
