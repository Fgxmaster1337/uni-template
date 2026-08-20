# 32711 Business Intelligence — Klausur-Wissensmanagement

## KERNREGELN (IMMER BEFOLGEN)

> Diese Regeln haben hoechste Prioritaet. Bei Verletzung einer Kernregel ist die Antwort WERTLOS.

1. **KEYWORDS ALS ANKER:** Der Korrektor scannt nach Fachbegriffen, nicht nach schoenen Saetzen. Fachbegriffe muessen als erkennbare Brocken in der Antwort stehen. NICHT umschreiben, SONDERN direkt den Fachbegriff nennen + kurze Erklaerung.

2. **KEINE AI-STRUKTUR:** Echte Studenten schreiben nicht symmetrisch. VERBOTEN: Einleitungssatz, immer-gleiches Muster, Zusammenfassung am Ende, uebermaessige Formatierung, kuenstlich variierte Uebergaenge. Stattdessen: Direkt mit dem Kernkonzept anfangen.
   **AUSNAHME:** "Name: Erklaerung"-Format bei Aufzaehlungs-Aufgaben ist KEIN AI-Muster.

3. **VOKABULAR NUR AUS SKRIPT:** Nur Begriffe, die Prof. Dr. Baumoel / Prof. Dr. Smolnik benutzen. Keine Lehrbuch-Synonyme. Im Zweifel: `docs/folien_text/` durchsuchen.

4. **PARAPHRASIEREN — ABSOLUT KRITISCH:** Feststehende Definitionen und Fachbegriffe duerfen woertlich uebernommen werden. ALLES ANDERE muss in eigenen Worten formuliert sein.

5. **UNKLARHEITEN → STOPP:** Bei fehlenden Antwortalternativen, unklarem Kontext, mehrdeutiger Fragestellung: NICHT loesen, nachfragen.

---

## Modul-Info

- **Modul:** 32711 Business Intelligence
- **Universitaet:** FernUniversitaet in Hagen
- **Prof:** Prof. Dr. Ulrike Baumoel / Prof. Dr. Stefan Smolnik
- **Klausurdauer:** 120 Minuten
- **Klausurformat:** Online via Moodle
- **Klausurdatum:** TBD
- **Format:** Einsendeaufgaben (4 Einheiten)
- **Gesamtpunktzahl:** TBD

---

## Skills (Slash-Commands)

| Skill | Trigger | Beschreibung |
|-------|---------|-------------|
| Pruefungsmodus | `/exam` | Klausurantwort-Modus: knapp, keywords, doppelte Ausgabe (MD + HTML) |
| Self-Review | `/check` | 7-Punkte-Pruefung der letzten Antwort |
| Vollstaendigkeits-Check | `/punkte` | Punktebudget, fehlende Bausteine |
| Authentizitaets-Check | `/authentic` | Gezieltes Abschwaechen auf Studenten-Niveau |

### Lernmodus (Standard — kein Trigger noetig)
Ausfuehrlich, paedagogisch, Intuition vor Formalismus, Rueckfragen stellen.

---

## Zugelassene Hilfsmittel

**Erlaubt:** Alle (Online-Klausur / Einsendeaufgaben)
**NICHT erlaubt:** —

---

## Verhaltensregeln

1. **Sprache:** Deutsch (Fachbegriffe wie im Skript)
2. **Quellen im Pruefungsmodus:** Primaerquelle ist IMMER `docs/folien_text/`. Die `wissen/`-Dateien sind Nachschlagewerk.
3. **Vor jeder Antwort:** Zuerst `wissen/` fuer Orientierung, dann `docs/folien_text/` fuer exakte Begriffe
4. **Quellenangabe:** Kapitel/Seite referenzieren
5. **PDFs in `docs/folien/` sind READ-ONLY** — niemals veraendern

---

## Wissensindex

| # | PDF | Status | Wissensdatei | Thema |
|---|-----|--------|-------------|-------|
| 1 | 32711-01-S#1-S002664941.pdf | FERTIG | wissen/01_grundlagen_bi.md | Grundlagen der Business Intelligence |
| 2 | 32711-02-S#1-S002664968.pdf | FERTIG | wissen/02_methoden_instrumente.md | Methoden und Instrumente der BI |
| 3 | 32711-03-S#1-2001332.pdf | FERTIG | wissen/03_datenhaltung_bereitstellung.md | Intelligente Datenhaltung und -bereitstellung |
| 4 | 32711-04-S#1-S002664984.pdf | FERTIG | wissen/04_neuere_entwicklungen.md | Neuere Entwicklungen und Anwendungsbeispiele |

---

## Projektstruktur

```
BI/
├── CLAUDE.md
├── .claude/
│   ├── settings.json
│   └── skills/          # /exam, /check, /punkte, /authentic, ...
├── config/
│   ├── klausurtag_prompt.md
│   └── suchanleitungen.md
├── docs/
│   ├── folien/          # Original-PDFs (READ-ONLY)
│   ├── folien_text/     # Extrahierte Texte (durchsuchbar)
│   ├── klausuren/       # Altklausuren
│   ├── wiederholungsfragen/
│   ├── uebungen/
│   └── sonstiges/
├── wissen/              # Generierte Wissensdateien
│   └── klausur_antworten/  # HTML-Ausgaben
└── workflow.md          # 7-Phasen-Gesamtprozess
```
