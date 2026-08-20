---
name: check
description: Self-Review — prueft die letzte Antwort auf Exkurse, Fachbegriffe, AI-Muster und Studentenrealismus.
allowed-tools: Read, Grep, Glob
---

## Auftrag

Geh deine letzte Antwort Teilaufgabe fuer Teilaufgabe durch und pruefe JEDEN der folgenden Punkte. Antworte ehrlich und konkret — nicht "alles gut", sondern benenne exakt die Stelle.

### 1. Exkurse & Ueberschuss
- Habe ich irgendwo etwas erklaert, das NICHT gefragt wurde?
- Gibt es Saetze, die ein Student unter Zeitdruck weglassen wuerde?
- Habe ich ungefragt Beispiele oder Zusatzinformationen angefuegt?

### 2. Fachbegriffe-Check
- Werden die Fachbegriffe korrekt wie im Skript verwendet?
- Stimmen die Begriffe mit `docs/folien_text/` ueberein?
- Habe ich Lehrbuch-Synonyme benutzt, die NICHT im Skript stehen?

### 3. Zuordnungs-Check (bei Zuordnungsaufgaben)
- Ist jede Zuordnung mit einer kurzen Begruendung versehen?
- Habe ich aehnliche Begriffe verwechselt?
- Sind alle Zuordnungen bearbeitet — keine ausgelassen?

### 4. Aufgaben-Bezug-Check
- Habe ich das Konzept tatsaechlich auf die konkreten Aufgabeninhalte angewendet?
- Oder habe ich nur abstrakt erklaert, was das Konzept bedeutet?
- Nenne ich spezifische Details aus der Aufgabenstellung?

### 5. AI-Muster
- Einleitungssatz vor der eigentlichen Antwort?
- Zusammenfassung am Ende?
- Immer dasselbe Schema?
- Synonym-Dumping (mehr als 1 Synonym)?
- Skript-Inhalte 1:1 uebernommen statt paraphrasiert?
- Symmetrische Beispiel-Labels?
- Skript-Verweise ("laut Skript", "im Skript steht")?

### 6. Vollstaendige Saetze (PFLICHT bei Open Questions)
- Sind alle Antworten in vollstaendigen Saetzen formuliert?
- Gibt es Stichpunkte, die in Fliesstext umgewandelt werden muessen?

### 7. Studentenrealismus
- Koennte ein guter Student das in der Klausur so schreiben?
- Ist die Antwort zu lang fuer den Punktewert?
- Klingt es nach Lehrbuch oder nach jemandem, der den Stoff verstanden hat?

## Ausgabeformat

Fuer jede Teilaufgabe kurz:
- **OK** oder **Problem:** [was genau] → [Korrektur]

Falls Korrekturen noetig: direkt umsetzen.

**WICHTIG:** Nach dem Check IMMER die vollstaendige, korrigierte Antwort nochmal ausgeben (Markdown + ggf. HTML).
