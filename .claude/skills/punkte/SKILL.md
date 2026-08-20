---
name: punkte
description: Vollstaendigkeits-Check — prueft Punktebudget, fehlende Bausteine, Aufgabenabgleich.
allowed-tools: Read, Grep, Glob
---

## Auftrag

Geh die letzte Antwort Teilaufgabe fuer Teilaufgabe durch. Fuer jede Teilaufgabe:

### 1. Aufgabenstellung abgleichen
- Was GENAU wird gefragt? (zuordnen, beschreiben, sortieren, benennen, einordnen, erlaeutern, berechnen...)
- Jedes Verb ist ein Arbeitsauftrag. "Zuordnen UND begruenden" = zwei Dinge.
- Werden ALLE Teile der Frage beantwortet?

### 2. Punktebudget pruefen
- Wie viele Punkte gibt es?
- Grobe Faustregel: ~1.5-2 Punkte pro inhaltlichem Baustein
- Wenn eine Aufgabe nach einem Modell fragt, alle Teile abdecken
- Ist die Antwort zu duenn fuer die Punktzahl?

### 3. Fehlende Bausteine identifizieren
- Modelle/Frameworks vollstaendig? (Alle Phasen, Prozesse, Rollen?)
- Prozessschritte komplett?
- Rollen/Akteure alle genannt?

### 4. Ergaenzungen pruefen (KRITISCH)
Falls etwas fehlt, VOR dem Ergaenzen:
- Fachbegriffe aus `docs/folien_text/` pruefen — nicht ausdenken
- Begriffe nur aus den Folien, keine Lehrbuch-Synonyme
- Formulierung wie ein Student
- Nur das Fehlende praezise ergaenzen
- Kein Over-Engineering

## Ausgabeformat

Pro Teilaufgabe:
- **Vollstaendig** oder **Luecke:** [was fehlt] → [konkrete Ergaenzung]
- Bei Luecken: Begriffe gegen Folien gecheckt? Ja/Nein

Falls Ergaenzungen noetig: direkt umsetzen (Markdown + ggf. HTML).
