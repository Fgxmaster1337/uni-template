# Workflow — Klausur-Wissensmanagement Gesamtprozess

> Dieses Dokument beschreibt den kompletten Ablauf von "leerer Ordner" bis "Klausurtag".
> Jede Phase wird einzeln abgeschlossen, bevor die naechste beginnt.

---

## Phase 0: Projekt aufsetzen (Tag 1)

**Dauer:** 30 Minuten

1. Ordnerstruktur anlegen (siehe SKILL.md Schritt 2)
2. CLAUDE.md erstellen (aus CLAUDE_TEMPLATE.md, Platzhalter ersetzen)
3. Config-Dateien kopieren und anpassen
4. .gitignore anlegen
5. Git initialisieren, erster Commit
6. PDFs in `docs/folien/` ablegen

**Ergebnis:** Leeres Projekt mit Infrastruktur, PDFs liegen bereit.

---

## Phase 1: Folien einpflegen (je PDF 1-2 Stunden)

**Pro PDF folgende Schritte:**

### 1a. Text extrahieren

- PDF oeffnen, Text extrahieren
- Ergebnis als `.txt` in `docs/folien_text/` speichern
- Gleicher Dateiname wie PDF, nur `.txt` statt `.pdf`
- Ziel: Durchsuchbar via Grep fuer spaetere Fachbegriff-Pruefung

### 1b. Wissensdatei erstellen

Fuer jedes PDF eine `wissen/NN_thema.md` erstellen. Schema:

```markdown
# NN - [Thema]

> **Quelle:** [datei.pdf] ([N] Seiten/Folien) | **Pruefungsrelevanz:** [HOCH/MITTEL/NIEDRIG]

## Ueberblick

[3-5 Saetze: Was wird in diesem Kapitel behandelt? Zentrale Konzepte? Zusammenhang zu anderen Kapiteln?]

---

## Kernkonzepte

### Definition: [Begriff 1]
[Definition — feststehende Begriffe duerfen woertlich, alles andere paraphrasiert]

### Definition: [Begriff 2]
[...]

---

## [Modelle / Frameworks / Verfahren — fachspezifisch]

### Model: [Modellname]
[Beschreibung, Komponenten, Zusammenhaenge]

### Framework: [Frameworkname]
[Beschreibung, Dimensionen, Anwendung]

### Verfahren: [Verfahrensname]          ← nur bei quantitativen Faechern
[Formel, Voraussetzungen, Interpretation]

---

## Definitionstabelle

| Begriff | Definition | [Formel] |
|---------|-----------|----------|
| [Begriff] | [Kurzdefinition] | [LaTeX falls quantitativ] |

---

## Querverweise

- Siehe auch: `wissen/XX_verwandtes_thema.md` — [Zusammenhang]

---

## Typische Pruefungsfragen

### Pruefungsfrage: [Frage 1]
**Antwort:** [Musterloesung im Pruefungsmodus-Stil]

### Pruefungsfrage: [Frage 2]
[...]

---

## Tags

`[tag1]` `[tag2]` `[tag3]`
```

### 1c. Wissensindex updaten

Nach jeder fertigen Wissensdatei in CLAUDE.md:
- Status von `OFFEN` auf `FERTIG` aendern
- Ggf. Thema praezisieren

### 1d. Commit

```
git add wissen/NN_thema.md docs/folien_text/datei.txt
git commit -m "feat: Wissensdatei NN_thema erstellt"
```

**Reihenfolge:** PDFs eins nach dem anderen abarbeiten. Nicht parallel.

---

## Phase 2: Glossar erstellen (nach allen Wissensdateien)

**Dauer:** 1-2 Stunden

Datei: `wissen/glossar.md`

### Schema — Qualitatives Fach:

```markdown
# Glossar — [MODULNAME] ([MODULNUMMER])

## A

| Begriff | Definition | Unit | Quelle |
|---------|-----------|------|--------|
| **[Begriff]** | [Kurzdefinition auf Deutsch] | [Unit-Nr] | [Autor Jahr] |

## B
[...]
```

### Schema — Quantitatives Fach:

```markdown
# Glossar — [MODULNAME] ([MODULNUMMER])

## Begriffsverzeichnis

| Begriff | Definition | Kapitel |
|---------|-----------|--------|
| **[Begriff]** | [Definition] | [Kap.] |

## Formelsammlung

| Formel | LaTeX | Kontext | Kapitel |
|--------|-------|---------|--------|
| [Name] | $[LaTeX]$ | [Wann anwenden] | [Kap.] |

## Testverzeichnis (falls relevant)

| Test | H0 | H1 | Teststatistik | Entscheidungsregel |
|------|----|----|---------------|--------------------|
| [Testname] | [H0] | [H1] | [Formel] | [Wann verwerfen] |
```

### Qualitaetskriterien:

- Alphabetisch sortiert
- Kreuzreferenzen zu Wissensdateien
- Nur Begriffe aus dem Skript, keine Lehrbuch-Synonyme
- Bei englischem Skript: Englischer Fachbegriff + deutsche Erklaerung

---

## Phase 3: Altklausuren aufarbeiten (je Klausur 2-3 Stunden)

**Pro Altklausur:**

1. PDF in `docs/klausuren/` ablegen
2. Wissensdatei erstellen: `wissen/klausur_YYYY_monat.md`

### Schema:

```markdown
# Klausur [Semester] — [MODULNAME]

## Ueberblick

| Aspekt | Detail |
|--------|--------|
| Semester | [z.B. Maerz 2026] |
| Dauer | [z.B. 120 Minuten] |
| Gesamtpunkte | [z.B. 100] |
| Format | [z.B. Online/Papier] |

## Themenverteilung

| Aufgabe | Thema | Punkte | Schwierigkeit |
|---------|-------|--------|---------------|
| 1 | [Thema] | [P] | [leicht/mittel/schwer] |
| 2 | [Thema] | [P] | [leicht/mittel/schwer] |

---

## Aufgabe 1: [Titel] ([P] Punkte)

### Aufgabenstellung
[Original-Aufgabentext]

### Musterloesung
[Im Pruefungsmodus-Stil: Keywords, keine AI-Struktur, paraphrasiert]

### Aufgabentyp-Analyse
- Typ: [Definition / Berechnung / Transfer / Diskussion]
- Benoetigtes Wissen: [Unit/Kapitel]
- Schwierigkeit: [leicht/mittel/schwer]

---

## Beobachtungen fuer die Klausurvorbereitung

- [Welche Themen kommen besonders haeufig vor?]
- [Welche Aufgabentypen dominieren?]
- [Ueberraschende Fragestellungen?]
- [Punkteverteilung: Wo gibt es leichte Punkte?]
```

3. Wissensindex in CLAUDE.md updaten
4. Commit

---

## Phase 4: Wiederholungsfragen durcharbeiten (je Set 1-2 Stunden)

**Workflow:**

1. PDFs in `docs/wiederholungsfragen/` ablegen
2. Pruefungsmodus aktivieren (`/exam`)
3. Eine Frage nach der anderen beantworten
4. Nach je 5 Fragen:
   - Aufgabenstellungen + Antworten in Markdown sammeln
   - Cross-Check mit zweiter AI (NotebookLM, Gemini, etc.)
   - Abweichungen identifizieren und Luecken schliessen
5. Ergebnis als `wissen/wiederholungsfragen_thema.md` speichern
6. Status in CLAUDE.md updaten
7. Commit

---

## Phase 5: Schwaechen identifizieren (nach Phase 3+4)

**Dauer:** 1 Stunde

Optional: `wissen/schwaechen.md` erstellen

- Welche Themen sind noch unsicher?
- Welche Aufgabentypen fallen schwer?
- Wo gab es Abweichungen beim Cross-Check?
- Gezielt nacharbeiten: Folien nochmal greppen, Wissensdateien ergaenzen

---

## Phase 6: Klausurtag-Vorbereitung (1-2 Tage vorher)

### 6a. Klausurtag-Prompt vorbereiten
- `config/klausurtag_prompt.md` mit finalen Daten ausfuellen
- Testen: Prompt in frische Session laden, kurze Probefrage stellen

### 6b. MathJax installieren (nur quantitative Faecher)
```bash
npm install mathjax@3
```

### 6c. HTML-Template testen
- Dark-Mode-CSS funktioniert?
- Formeln rendern korrekt? (nur quantitativ)
- Datei wird in `wissen/klausur_antworten/` gespeichert?

### 6d. Gameplan erstellen (optional)
- `wissen/klausur_gameplan.html` — Ablauf, Zeitplan, Checkliste
- Aufgabentypen-Uebersicht
- Haeufige Stolperfallen

### 6e. Generalprobe
- Altklausur komplett im Pruefungsmodus durchspielen
- Quality-Pipeline durchlaufen (/check, /punkte, ggf. /para, /trans, /eng)
- Cross-Check mit zweiter AI
- Timing pruefen: Schaffe ich alle Aufgaben in der vorgegebenen Zeit?

---

## Phase 7: Klausurtag

### Vorbereitung (15 Min vor Klausur)
- Repo lokal, Claude Code laeuft
- Klausurtag-Prompt laden (config/klausurtag_prompt.md)
- Pruefungsmodus aktiv
- Zweite AI bereit (NotebookLM/Gemini)
- [Moodle/Klausurbogen] geoeffnet

### Pro Aufgabe (Zyklus)

```
1. Aufgabentext kopieren → an Claude
2. Claude loest (Markdown + HTML)
3. Quality-Pipeline (manuell ausloesen)
4. Cross-Check mit zweiter AI
5. [Optional: /authentic]
6. Antwort abtippen/abschreiben
7. /clear → naechste Aufgabe
```

### Quality-Pipeline — Varianten

**Deutsches Skript (einfach):**
- Eine Runde: `/check` + `/punkte`

**Englisches Skript (drei Runden):**
- Runde 1: `/punkte` + `/para` (Vollstaendigkeit + Paraphrase)
- Runde 2: `/trans` + `/eng` (Uebersetzungs-Check + Englisch-Filter)
- Runde 3: `/check` (finale Validierung)

### Zeitbudget-Empfehlung
- Pflichtaufgabe: max 30 Min
- Je Wahlaufgabe: 20-30 Min
- Puffer: 10-15 Min am Ende

---

## Zusammenfassung: Phasen-Uebersicht

| Phase | Was | Wann | Dauer |
|-------|-----|------|-------|
| 0 | Projekt aufsetzen | Tag 1 | 30 Min |
| 1 | Folien einpflegen (je PDF) | Wochen 1-3 | 1-2h pro PDF |
| 2 | Glossar erstellen | Nach Phase 1 | 1-2h |
| 3 | Altklausuren aufarbeiten | Nach Phase 2 | 2-3h pro Klausur |
| 4 | Wiederholungsfragen | Nach Phase 2 | 1-2h pro Set |
| 5 | Schwaechen identifizieren | Nach Phase 3+4 | 1h |
| 6 | Klausurtag-Vorbereitung | 1-2 Tage vorher | 2-3h |
| 7 | Klausurtag | Am Tag | Klausurdauer |
