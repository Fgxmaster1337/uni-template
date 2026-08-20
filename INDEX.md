# INDEX -- Modul 32711: Business Intelligence

## Dateien im Ordner

| Datei | Einheit | Titel | Seiten |
|-------|---------|-------|--------|
| `32711-01-S#1-S002664941.pdf` | 1 | Grundlagen der Business Intelligence | 54 |
| `32711-02-S#1-S002664968.pdf` | 2 | Methoden und Instrumente der Business Intelligence | 114 |
| `32711-03-S#1-2001332.pdf` | 3 | Intelligente Datenhaltung und -bereitstellung | 64 |
| `32711-04-S#1-S002664984.pdf` | 4 | Neuere Entwicklungen und Anwendungsbeispiele der BI | 60 |

---

## Einheit 1 -- Grundlagen der Business Intelligence

**Autoren:** Prof. Dr. Ulrike Baumoel; Ueberarb.: Prof. Dr. Stefan Smolnik, Dr. Katharina Ebner, Christian Anschuetz

### Kapiteluebersicht
| Kap. | Thema | Seite |
|------|-------|-------|
| 1 | Einfuehrung (Praxisbeispiele, Vor-/Nachteile BI) | 1 |
| 2 | Konzeptionelle Grundlagen (Begriffsentwicklung, Entscheidungsmodelle) | 8 |
| 2.1 | Entwicklung des BI-Konzepts (Luhn 1958 bis heute) | 8 |
| 2.2 | BI als Entscheidungsunterstuetzung (MDP, PDCA) | 15 |
| 3 | BI-Architektur (Hub-and-Spoke, 4 Stufen) | 23 |
| 4 | Einordnung ins betriebliche Informationsmanagement | 27 |
| 4.1 | Daten, Informationen, Wissen | 28 |
| 4.2 | Comprehensive Decision Model (CDM) | 31 |
| 5 | Zusammenfassung | 33 |
| 7 | Loesungen zu den Uebungsaufgaben | 38 |

### Schluesselkonzepte
- **BI-Definition** (ganzheitlich): Entscheidungsproblem-orientierte Analyse + adressatengerechte Bereitstellung wettbewerbsrelevanter Informationen
- **Hub-and-Spoke-Architektur**: Datenquellen -> Staging/ETL -> DWH/Data Marts -> Auswertung (OLAP, DM)
- **PDCA-Kreislauf** (Deming): Plan-Do-Check-Act
- **Markov Decision Process** (Formeln 2.1-2.3): Formale Entscheidungsmodellierung
- **Comprehensive Decision Model (CDM)**: 3 Dimensionen (Akteur, Organisation, Applikationen)
- **Operative vs. dispositive Daten** (Kemper et al.)
- **Daten -> Information -> Wissen** (Begriffsabgrenzung)
- **Individuelle vs. organisatorische Intelligenz**
- **Ackoffs 5 kritische Annahmen** zum Informationsmanagement
- **Luhn (1958)**: Erste dokumentierte Verwendung des Begriffs "Business Intelligence"

---

## Einheit 2 -- Methoden und Instrumente der Business Intelligence

**Autoren:** Prof. Dr. Ulrike Baumoel, Sarah Hackstein, Alexander Kornrumpf

### Kapiteluebersicht
| Kap. | Thema | Seite |
|------|-------|-------|
| 1 | Einfuehrung (Anwendungsfelder KDD) | 1 |
| 2 | Knowledge Discovery in Databases (Definition, Prozesse) | 7 |
| 3 | Phase I: Vorbereitende Schritte | 15 |
| 3.1 | Problemdefinition (Alternativenmengen, Zielbeziehungen) | 15 |
| 3.2 | Auswahl der Daten (Universum, Konzept, IS) | 21 |
| 3.3 | Bereinigung und Aufbereitung (Fehlerklassen, Noise) | 24 |
| 3.4 | Projektion und Reduktion (Skalenniveaus, Kodierung, z-Transformation) | 32 |
| 4 | Phase II: Data Mining | 40 |
| 4.1 | Auswahl der Aufgabe (4 Grundaufgaben) | 40 |
| 4.2 | Auswahl des Algorithmus (No Free Lunch, Occam's Razor) | 43 |
| 4.3 | Entscheidungsbaumverfahren (TDIDT, CART/Gini, C4.5/Entropie) | 54 |
| 4.4 | Regressionsanalyse (linear, logistisch) | 62 |
| 4.5 | Clusteranalyse (hierarchisch, k-means) | 65 |
| 4.6 | Apriori-Algorithmus (Support, Konfidenz) | 75 |
| 4.7 | Kuenstliche Neuronale Netze (Perceptron, Backpropagation) | 79 |
| 4.8 | Weitere Verfahren (Naive Bayes, k-NN) | 81 |
| 5 | Phase III: Nachbereitende Schritte (Konfusionsmatrix) | 84 |
| 6 | Zusammenfassung | 88 |
| 7 | Uebungsaufgaben + Loesungen | 89/97 |

### Schluesselkonzepte
- **KDD-Definition** (Fayyad 1996): "non-trivial process of identifying valid, novel, potentially useful, and ultimately understandable patterns in data"
- **KDD-Prozess**: 3 Meta-Phasen (Vorbereitung, Data Mining, Nachbereitung)
- **4 DM-Grundaufgaben**: Assoziation, Clustering, Klassifizierung, Regression
- **No Free Lunch Theorem** (Wolpert): Kein allgemein bester Algorithmus
- **Occam's Razor**: Einfacheres Modell bevorzugen
- **Entscheidungsbaeume**: TDIDT, CART (Gini-Index), C4.5 (InformationGain, GainRatio), Pruning
- **Regressionsanalyse**: Lineare Regression (kleinste Quadrate), logistische Regression
- **Clusteranalyse**: Hierarchisch-agglomerativ (single/complete/average-linkage, Ward), k-means
- **Apriori-Algorithmus**: Support, Konfidenz, Warenkorbanalyse
- **Neuronale Netze**: Perceptron, Backpropagation, Sigmoidfunktion
- **Naive Bayes, k-NN**: Weitere Klassifizierer
- **Konfusionsmatrix**: Recall, Precision, Korrektklassifikationsrate, Falschpositivrate
- **Skalenniveaus**: Nominal, Ordinal, Intervall, Verhaeltnis
- **Kodierung**: Eins-aus-N, Dummy, Effekt, unaere Kodierung
- **z-Transformation** (Standardisierung), **Min-Max-Normalisierung**
- **3 Fehlerklassen**: Semantisch, Syntaktisch, Coverage

---

## Einheit 3 -- Intelligente Datenhaltung und -bereitstellung

**Autoren:** Prof. Dr. Ulrike Baumoel, Sarah Hackstein

### Kapiteluebersicht
| Kap. | Thema | Seite |
|------|-------|-------|
| 1 | Einfuehrung | 1 |
| 2 | Grundlegende Begriffe und Konzepte | 4 |
| 2.1 | Business Rules (BMM, Durchfuehrungslevel) | 4 |
| 2.2 | Metadatenmanagement (8 Kategorien, fachlich vs. technisch) | 9 |
| 2.3 | Datenqualitaetsmanagement (Wang & Strong, TQM) | 13 |
| 3 | Data Warehouse-Systeme | 20 |
| 3.1 | Gesamtarchitektur (5 Ebenen nach Sinz) | 21 |
| 3.2 | Definition und Ziele (Inmon, SINT-Eigenschaften) | 22 |
| 3.3 | Komponenten (ETL, ODS, Staging Area, Metadatenbanksystem) | 24 |
| 3.4 | Data Marts (Vergleich DWH vs. Data Mart) | 29 |
| 4 | Online Analytical Processing (OLAP) | 33 |
| 4.1 | Anforderungen (12 Regeln nach Codd, FASMI) | 34 |
| 4.2 | Auspraegungen (ROLAP, MOLAP, HOLAP) | 37 |
| 4.3 | Operationen (Pivotierung, Roll-Up, Drill-Down, Slice, Dice) | 39 |
| 5 | Zusammenfassung | 45 |
| 6 | Uebungsaufgaben + Loesungen | 46/51 |

### Schluesselkonzepte
- **DWH-Definition** (Inmon): "subject-oriented, integrated, nonvolatile, time-variant collection of data"
- **SINT-Eigenschaften**: Subject-oriented, Integrated, Nonvolatile, Time-variant
- **DWH-Architektur** (Sinz): 5 Ebenen (operative Systeme, Datenerfassung, Datenhaltung, Datenbereitstellung, Praesentation)
- **6 DWH-Komponenten**: DWH, ODS, Staging Area, ETL, Metadatenbanksystem, Analysekomponente
- **ETL-Prozess**: Extraktion (4 Vorgehensweisen), Transformation, Laden
- **Data Marts vs. DWH** (9 Vergleichskriterien)
- **Business Rules**: 3 Typen (Ableitung, Einschraenkung, Prozess), 6 Durchfuehrungslevel
- **Business Motivation Model (BMM)**: Verknuepfung Business Rules mit Strategie
- **Metadaten**: Fachlich vs. Technisch, 8 Kategorien nach Auth
- **Datenqualitaet** (Wang & Strong): 4 Kategorien (intrinsisch, kontextabhaengig, Darstellung, Zugang)
- **TQM** (English): 5 Phasen der Datenqualitaetsverbesserung
- **OLAP**: 12 Regeln nach Codd + 6 Erweiterungsregeln
- **FASMI**: Fast Analysis of Shared Multidimensional Information
- **OLAP-Typen**: ROLAP (Star-/Snowflake-Schema), MOLAP, HOLAP
- **5 OLAP-Operationen**: Pivotierung, Roll-Up, Drill-Down, Slice, Dice

---

## Einheit 4 -- Neuere Entwicklungen und Anwendungsbeispiele

**Autoren:** Prof. Dr. Ulrike Baumoel, Birgit Groesser, Alexander Kornrumpf

### Kapiteluebersicht
| Kap. | Thema | Seite |
|------|-------|-------|
| 1 | Einfuehrung (BI 2.0, Forschungsbereiche) | 1 |
| 2 | Wirkung der BI auf Unternehmensprozesse | 5 |
| 2.1 | Echtzeit-BI (Latenzarten, RTBI) | 7 |
| 2.2 | Business Activity Monitoring (BAM, SSBI, CPM) | 12 |
| 2.3 | Mobile BI (MBI-Vorgehensmodell, BYOD) | 15 |
| 3 | Advanced Analytics | 22 |
| 3.1 | BI jenseits von Organisationsgrenzen (BIaaS, Cloud, SBI, CBI) | 23 |
| 3.2 | BI mit semi-/unstrukturierten Daten (Text Mining, TF-IDF) | 27 |
| 3.3 | Predictive und In-Memory Analytics | 35 |
| 4 | Ausgewaehlte Anwendungsbeispiele | 36 |
| 4.1 | BI im Marketing (CRM) | 36 |
| 4.2 | Fallstudie "Newspaper Industry" (CRISP-DM) | 38 |
| 4.3 | Fallstudie "Continental Airlines" (RTBI) | 42 |
| 5 | Zusammenfassung | 45 |

### Schluesselkonzepte
- **BI 2.0 / BI 3.0**: Weiterentwicklung (proaktiv, Echtzeit, Advanced Analytics, In-Memory)
- **biMM** (Chamoni/Gluchowski): 5 Reifegradstufen der BI
- **RTBI** (Right-Time BI): Wirtschaftlich optimale Latenzen (nicht maximal kurz)
- **3 Latenzarten**: Datenlatenz, Analyselatenz, Entscheidungslatenz
- **Halbwertszeit von Information**: Exponentieller Wertverfall
- **BAM**: 5 Komponenten (Integrator, dyn. Datenspeicher, KPI-Manager, DM-Werkzeuge, BRE)
- **SSBI** (Self-Service BI): Erhoehte Zugaenglichkeit
- **CPM** (Corporate Performance Management)
- **Mobile BI**: 4-Phasen-Vorgehensmodell, BYOD
- **Advanced Analytics**: "measure, predict, optimize" (Bose 2009)
- **BIaaS** (BI as a Service), **Cloud-BI** (8 Dimensionen, 23 Erfolgsfaktoren)
- **SBI** (Social BI) vs. **CBI** (Collaborative BI)
- **Text Mining**: Bag-of-Words, TF-IDF (Formeln 3.1-3.13), Zentroidbasierte Klassifikation
- **Sentiment-Analyse**
- **In-Memory Analytics**: RAM statt Festplatte, Enabler fuer RTBI
- **CRM**: Analytisch, operativ, kommunikativ; Social CRM
- **CRISP-DM**: Industriestandard-Vorgehensmodell fuer Data Mining
- **Fallstudie Newspaper**: Datenqualitaetsprobleme, Entscheidungsbaum, 40/30/30-Split
- **Fallstudie Continental Airlines**: DWH + RTBI + BRE, Unternehmenskultur als Erfolgsfaktor

---

## Schnell-Suchindex nach Themen

| Thema | Einheit(en) | Kapitel |
|-------|-------------|---------|
| BI-Definition | 1 | 1, 2.1 |
| BI-Architektur (Hub-and-Spoke) | 1 | 3 |
| PDCA-Kreislauf | 1 | 2.2.2 |
| Operative vs. dispositive Daten | 1 | 4.1 |
| Daten / Information / Wissen | 1 | 4.1 |
| CDM (Comprehensive Decision Model) | 1 | 4.2 |
| KDD-Prozess | 2 | 2 |
| Problemdefinition / Entscheidungsprobleme | 2 | 3.1 |
| Datenbereinigung / Fehlerklassen | 2 | 3.3 |
| Skalenniveaus / Kodierung | 2 | 3.4 |
| Standardisierung / Normalisierung | 2 | 3.4 |
| Entscheidungsbaeume (CART, C4.5) | 2 | 4.3 |
| Regression (linear, logistisch) | 2 | 4.4 |
| Clusteranalyse (hierarchisch, k-means) | 2 | 4.5 |
| Apriori-Algorithmus | 2 | 4.6 |
| Neuronale Netze / Perceptron | 2 | 4.7 |
| Naive Bayes / k-NN | 2 | 4.8 |
| Konfusionsmatrix | 2 | 5.1 |
| Business Rules / BMM | 3 | 2.1 |
| Metadaten / Metadatenmanagement | 3 | 2.2 |
| Datenqualitaet (Wang & Strong) | 3 | 2.3 |
| DWH (Inmon, SINT) | 3 | 3.2 |
| DWH-Architektur (5 Ebenen) | 3 | 3.1 |
| ETL-Prozess | 1, 3 | 1:3 / 3:3.3 |
| Data Marts | 1, 3 | 1:3 / 3:3.4 |
| ODS (Operational Data Store) | 3 | 3.3 |
| OLAP (Codd, FASMI, Operationen) | 3 | 4 |
| ROLAP / MOLAP / HOLAP | 3 | 4.2 |
| Pivotierung, Roll-Up, Drill-Down, Slice, Dice | 3 | 4.3 |
| Echtzeit-BI / RTBI | 4 | 2.1 |
| BAM / SSBI / CPM | 4 | 2.2 |
| Mobile BI | 4 | 2.3 |
| biMM (Reifegradmodell) | 4 | 2 |
| BIaaS / Cloud-BI | 4 | 3.1 |
| SBI / CBI | 4 | 3.1 |
| Text Mining / TF-IDF | 4 | 3.2 |
| In-Memory Analytics | 4 | 3.3 |
| CRM / Marketing-BI | 4 | 4.1 |
| CRISP-DM | 4 | 4.2 |
| Fallstudien (Newspaper, Continental) | 4 | 4.2, 4.3 |
