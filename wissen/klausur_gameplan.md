# Klausur-Gameplan — 32711 Business Intelligence

## Eckdaten

- **Modul:** 32711 Business Intelligence
- **Format:** Online via Moodle / Einsendeaufgaben
- **Dauer:** 120 Minuten
- **Hilfsmittel:** Alle erlaubt (Online-Klausur)

---

## Themen-Haeufigkeit und Gewichtung

### Einheit 1: Grundlagen (Basis fuer alles)
| Thema | Erwartete Fragetypen | Prioritaet |
|-------|---------------------|-----------|
| BI-Definition (ganzheitlich) | Definition, Erlaeuterung | HOCH |
| Hub-and-Spoke-Architektur (4 Stufen) | Beschreibung, Zuordnung | HOCH |
| CDM (3 Dimensionen) | Erlaeuterung, Diskussion | HOCH |
| Daten / Information / Wissen | Abgrenzung, Definition | HOCH |
| Operative vs. dispositive Daten | Vergleich (Tabelle) | HOCH |
| PDCA-Kreislauf | Beschreibung, Anwendung | MITTEL |
| MDP (Formeln) | Berechnung, Erlaeuterung | MITTEL |
| Luhn 1958, BI-Begriffsentwicklung | Nachvollziehen | MITTEL |
| Ackoffs 5 Annahmen | Diskussion | NIEDRIG |

### Einheit 2: Methoden und Instrumente (umfangreichste Einheit)
| Thema | Erwartete Fragetypen | Prioritaet |
|-------|---------------------|-----------|
| KDD-Prozess (9 Schritte, 3 Meta-Phasen) | Definition, Abgrenzung KDD vs DM | HOCH |
| Entscheidungsbaeume (CART/C4.5) | Berechnung (Gini, Entropie, GainRatio) | HOCH |
| Clusteranalyse (hierarchisch, k-means) | Berechnung (Distanzmatrix, Linkage) | HOCH |
| Konfusionsmatrix (TP/FP/TN/FN) | Berechnung (Recall, Precision, Accuracy) | HOCH |
| Fehlerklassen (semantisch/syntaktisch/coverage) | Zuordnung, Beispiele | HOCH |
| Skalenniveaus + Kodierung | Zuordnung, Vergleich | HOCH |
| Apriori (Support, Konfidenz) | Berechnung, Erlaeuterung | MITTEL |
| Regressionsanalyse (linear, logistisch) | Berechnung, Vergleich | MITTEL |
| KNN (Perceptron, Backpropagation) | Erlaeuterung | MITTEL |
| Naive Bayes, k-NN | Definition, Vergleich | MITTEL |
| No Free Lunch, Occam's Razor | Erlaeuterung | NIEDRIG |
| z-Transformation, Min-Max-Normalisierung | Berechnung | MITTEL |

### Einheit 3: Datenhaltung und -bereitstellung
| Thema | Erwartete Fragetypen | Prioritaet |
|-------|---------------------|-----------|
| DWH (Inmon-Definition, SINT) | Definition, Erlaeuterung | HOCH |
| ETL-Prozess (3 Phasen) | Beschreibung | HOCH |
| Data Marts vs. DWH | Vergleich (Tabelle) | HOCH |
| OLAP (Codd 12 Regeln, FASMI) | Erlaeuterung, Aufzaehlung | HOCH |
| OLAP-Operationen (5 Stueck) | Beschreibung, Zuordnung | HOCH |
| Business Rules (3 Typen, BMM) | Definition, Erlaeuterung | MITTEL |
| Metadaten (fachlich vs. technisch) | Vergleich, Beispiele | MITTEL |
| Datenqualitaet (Wang & Strong, TQM) | Erlaeuterung, Zuordnung | MITTEL |
| ROLAP / MOLAP / HOLAP | Vergleich | MITTEL |
| DWH-Architektur (5 Ebenen Sinz) | Beschreibung | MITTEL |
| ODS | Definition | NIEDRIG |

### Einheit 4: Neuere Entwicklungen
| Thema | Erwartete Fragetypen | Prioritaet |
|-------|---------------------|-----------|
| 3 Latenzarten (Daten/Analyse/Entscheidung) | Definition, Zuordnung | HOCH |
| RTBI (Right-Time vs Real-Time) | Erlaeuterung, Abgrenzung | HOCH |
| biMM (5 Reifegradstufen) | Beschreibung, Einordnung | MITTEL |
| BAM (5 Komponenten) | Aufzaehlung, Erlaeuterung | MITTEL |
| TF-IDF (Formeln) | Berechnung, Erlaeuterung | HOCH |
| Text Mining / Sentiment Analyse | Erlaeuterung | MITTEL |
| CRISP-DM | Beschreibung, Vergleich mit KDD | MITTEL |
| Fallstudien (Newspaper, Continental) | Transfer, Diskussion | MITTEL |
| Cloud-BI / BIaaS | Definition, Vergleich | NIEDRIG |
| SBI vs. CBI | Abgrenzung | NIEDRIG |
| Mobile BI / BYOD | Erlaeuterung | NIEDRIG |

---

## Berechnungen, die sitzen muessen

1. **Gini-Index:** Gini(t) = 1 - Σ p(Ci|t)²
2. **Entropie:** H(t) = -Σ p(Ci|t) · log2(p(Ci|t))
3. **GainRatio:** InformationGain / SplitInfo
4. **Support:** |{xi: Ih∪Ic ⊆ Q+(xi)}| / |XTr|
5. **Konfidenz:** support(Ih→Ic) / support(Ih)
6. **Recall:** TP / (TP + FN)
7. **Precision:** TP / (TP + FP)
8. **Accuracy:** (TP + TN) / (TP + TN + FP + FN)
9. **z-Transformation:** v' = (v - x̄) / s
10. **Min-Max:** v' = (v - v_min) / (v_max - v_min)
11. **TF-IDF:** tfreq(d,q) · log(|X| / |X_q|)
12. **Euklidische Distanz:** √(Σ(xi - yi)²)
13. **Zentroid:** μ_C = (1/|C|) · Σ x

---

## Haeufige Stolperfallen

1. **KDD ≠ DM:** KDD ist der Gesamtprozess, DM nur der Analyseschritt
2. **Konfidenz ist nicht symmetrisch:** confidence(A→B) ≠ confidence(B→A)
3. **RTBI ≠ Real-Time:** "Right-Time" = wirtschaftlich optimal, nicht maximal schnell
4. **Operative vs. dispositive Daten** nicht verwechseln — BI verarbeitet operative und erzeugt dispositive
5. **Gini vs. Entropie:** Gini = CART (binaer), Entropie = C4.5 (auch mehrfach)
6. **InformationGain bevorzugt viele Werte** → GainRatio als Korrektur
7. **k-means findet lokales Minimum** — abhaengig von Initialisierung
8. **Overfitting:** Gute Trainingsperformance ≠ gute Testperformance
9. **CDM-Dimensionen** werden alternierend analysiert, nicht sequentiell
10. **SINT:** Subject-oriented, Integrated, Nonvolatile, Time-variant — Reihenfolge merken

---

## Checkliste vor der Klausur

- [ ] Repo lokal, Claude Code laeuft
- [ ] Klausurtag-Prompt geladen (config/klausurtag_prompt.md)
- [ ] Pruefungsmodus aktiv (/exam)
- [ ] Zweite AI bereit (NotebookLM/Gemini)
- [ ] Moodle geoeffnet
- [ ] Glossar und Wissensdateien griffbereit
- [ ] Formelsammlung im Glossar pruefen

---

## Workflow am Klausurtag

```
Pro Aufgabe:
1. Aufgabentext kopieren → an Claude
2. Claude loest (Markdown + HTML)
3. /check (Self-Review)
4. /punkte (Vollstaendigkeits-Check)
5. Cross-Check mit zweiter AI
6. [Optional: /authentic]
7. Antwort abtippen
8. /clear → naechste Aufgabe
```

**Zeitbudget-Empfehlung (bei 120 Min):**
- Aufgaben lesen und priorisieren: 5 Min
- Pro Aufgabe inkl. Quality-Pipeline: 20-25 Min
- Puffer am Ende: 10-15 Min
