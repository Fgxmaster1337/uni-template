# Startprompt — Neues Klausur-Projekt

> Kopiere den Prompt unten in eine neue Claude-Code-Session im Projektordner.
> Ersetze alle `[PLATZHALTER]`.

---

## DER PROMPT:

```
Dieses Projekt nutzt das uni-template aus dem Vulture Depot. Die Ordnerstruktur, CLAUDE.md, Skills (/exam, /check, /punkte, /authentic) und Config-Dateien sind bereits angelegt.

Lies zuerst workflow.md fuer den 7-Phasen-Gesamtprozess.

Jetzt die Platzhalter in CLAUDE.md und config/ ersetzen:

- **Modulname:** [MODULNAME]
- **Modulnummer:** [MODULNUMMER]
- **Universitaet:** [UNIVERSITAET]
- **Prof:** [PROF]
- **Klausurdauer:** [DAUER]
- **Gesamtpunktzahl:** [PUNKTE]
- **Klausurdatum:** [DATUM]
- **Klausurformat:** [Online via Moodle / Handschriftlich]
- **Aufgabenformat:** [z.B. 1 Pflichtaufgabe (40P) + 3 von 4 Wahlaufgaben (je 20P)]
- **Zugelassene Hilfsmittel:** [erlaubt / nicht erlaubt]
- **Skriptsprache:** [Deutsch / Englisch]
- **Quantitatives Fach:** [Ja / Nein]

Fachspezifische Anpassungen:
- Englisches Skript? → Skills /para, /trans, /eng sind schon vorhanden, in CLAUDE.md die Quality-Pipeline anpassen
- Quantitatives Fach? → Formelkonventionen-Sektion in CLAUDE.md ergaenzen
- Wahlaufgaben? → Skill /aufgabenwahl ist schon vorhanden

Vorlesungs-PDFs (in docs/folien/):

| # | Dateiname | Thema |
|---|-----------|-------|
| 1 | [datei1.pdf] | [Thema 1] |
| 2 | [datei2.pdf] | [Thema 2] |

Ersetze alle {{PLATZHALTER}} in CLAUDE.md und config/klausurtag_prompt.md, dann starte mit Phase 1 (erstes PDF einpflegen).
```
