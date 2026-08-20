# Ergaenzungen -- Vertiefende Inhalte ueber Einheitsgrenzen hinweg

> **Pruefungsrelevanz:** HOCH | Ergaenzt wissen/01-04 um Querverbindungen und Detailluecken

---

## 1. Star-Schema vs. Snowflake-Schema

### Grundprinzip: Dimensionale Modellierung im ROLAP

ROLAP basiert auf relationalen DBMS und speichert multidimensionale Datenmodelle in Tabellen ab, ohne dass Informationen verloren gehen (Humm & Wietek, 2005). Dabei gibt es zwei verschiedene Tabellenarten: **Dimensionstabellen** und **Faktentabellen**.

### Star-Schema (Sternschema)

**Aufbau (vgl. Skript Einheit 3, Abb. 12; Farkisch, 2011):**

- **Faktentabelle** (zentral): Enthaelt die Bewegungsdaten (z. B. Umsatz, Absatzmenge). Die Schluessel der Faktentabelle weisen auf die entsprechenden Dimensionstabellen (z. B. Ort_ID, Produkt_ID, Zeit_ID, Kunden_ID).
- **Dimensionstabellen** (sternfoermig um die Faktentabelle angeordnet): Enthalten die Stammdaten. Jede Dimension wird durch Eigenschaften charakterisiert (z. B. Produkt_ID -> Artikelnummer, Produktgruppe, Produktfamilie).
- Die Dimensionstabellen werden grafisch sternfoermig um die Faktentabelle verteilt -- daher der Name "Star-Schema" (Skript Einheit 3).

**Eigenschaften:**
- Denormalisierte Dimensionstabellen (alle Hierarchieebenen in einer Tabelle)
- Einfache, intuitive Struktur
- Wenige JOINs bei Abfragen noetig (schnelle Antwortzeiten)
- Redundanz in den Dimensionstabellen (z. B. Produktgruppe wird fuer jedes Produkt wiederholt)

### Snowflake-Schema (Schneeflockenschema)

Das Snowflake-Schema wird im Skript (Einheit 3) als alternative Implementierungsform neben dem Star-Schema fuer ROLAP genannt (Humm & Wietek, 2005). Es unterscheidet sich vom Star-Schema durch die **Normalisierung der Dimensionstabellen**:

**Aufbau:**
- **Faktentabelle** (zentral): Identisch zum Star-Schema -- enthaelt Bewegungsdaten mit Fremdschluesseln zu den Dimensionstabellen.
- **Dimensionstabellen** (normalisiert): Die Hierarchieebenen innerhalb einer Dimension werden in separate Tabellen aufgespalten. Beispiel: Statt einer einzigen Tabelle "Produkt" mit den Spalten Produkt_ID, Artikelnummer, Produktgruppe, Produktfamilie gibt es separate Tabellen fuer Produkt, Produktgruppe und Produktfamilie, die ueber Fremdschluessel verbunden sind.
- Die resultierende Struktur aehnelt einer Schneeflocke, da von der zentralen Faktentabelle ueber die Dimensionstabellen weitere Untertabellen abzweigen.

### Vergleich Star-Schema vs. Snowflake-Schema

| Kriterium | Star-Schema | Snowflake-Schema |
|-----------|-------------|------------------|
| **Dimensionstabellen** | Denormalisiert (flach) | Normalisiert (aufgeteilt in Hierarchieebenen) |
| **Anzahl Tabellen** | Weniger (eine pro Dimension) | Mehr (mehrere pro Dimension) |
| **Redundanz** | Hoeher (in Dimensionstabellen) | Geringer (durch Normalisierung) |
| **Abfragekomplexitaet** | Wenige JOINs, einfache Abfragen | Mehr JOINs, komplexere Abfragen |
| **Antwortzeit** | Tendenziell schneller | Tendenziell langsamer |
| **Speicherplatz** | Hoeher (wegen Redundanz) | Geringer (weniger Redundanz) |
| **Wartbarkeit der Dimensionen** | Aenderungen an Hierarchien erfordern Anpassung der gesamten Dimensionstabelle | Aenderungen nur in der betroffenen Hierarchietabelle |
| **Verstaendlichkeit** | Intuitiver, leichter verstaendlich | Komplexer in der Struktur |
| **Typischer Einsatz** | Haeufigste ROLAP-Variante (Skript) | Bei sehr grossen Dimensionstabellen mit vielen Hierarchieebenen |

**Pruefungshinweis:** Das Skript beschreibt das Star-Schema ausfuehrlich (Abb. 12, Farkisch 2011) und nennt das Snowflake-Schema als Alternative. Beide sind ROLAP-Implementierungen, die multidimensionale Datenmodelle in relationalen Tabellen abbilden.

---

## 2. CRISP-DM vs. KDD-Prozess

### Tabellarische Gegenueberstallung

| CRISP-DM (Chapman et al., 2000) | KDD-Prozess (Fayyad et al., 1996) | Bemerkung |
|---|---|---|
| **1. Business Understanding** | **1. Problemdefinition** | CRISP-DM betont explizit, dass DM mit dem Verstehen der Situation und Ziele des Unternehmens beginnt (Skript Einheit 4). KDD definiert Problemstellung und Domaene. |
| **2. Data Understanding** | **2. Auswahl der Daten** | CRISP-DM sieht eine explizite Phase des "data understanding" vor. Im KDD-Prozess wird das Verstehen der Daten als Querschnittsaufgabe ueber alle Schritte der Datenvorbereitung verstanden (Skript Einheit 4). |
| **3. Data Preparation** | **3. Bereinigung und Aufbereitung** + **4. Reduktion/Projektion** | KDD unterteilt die Datenvorbereitung feiner (Bereinigung und Attributtransformation als separate Schritte). |
| **4. Modeling** | **5. Auswahl der Aufgabe** + **6. Auswahl des Algorithmus** + **7. Data Mining** | KDD unterscheidet Aufgabenwahl, Algorithmenwahl und Mustersuche; CRISP-DM fasst dies zusammen. |
| **5. Evaluation** | **8. Interpretation** | Bewertung der Ergebnisse. |
| **6. Deployment** | **9. Verwendung** | Integration des gewonnenen Wissens in die Praxis. |

### Gemeinsamkeiten

- Beide beschreiben einen **iterativen Prozess** (Rueckspruenge zwischen Phasen sind moeglich und erwuenscht)
- Beide betonen die Notwendigkeit, DM in einen **uebergeordneten Kontext** einzubetten (Managementkreislauf bzw. Unternehmensziele)
- Beide umfassen die drei **Meta-Phasen**: Vorbereitung, Analyse/Mining, Nachbereitung
- Die Fallstudie "Newspaper Industry" (Gunnarsson et al., 2007) zeigt die praktische Anwendung von CRISP-DM (Skript Einheit 4)

### Unterschiede

| Aspekt | CRISP-DM | KDD-Prozess |
|--------|----------|-------------|
| **Herkunft** | Von der Industrie entwickelter Standard (Chapman et al., 2000) | Aus der Forschung (Fayyad et al., 1996) |
| **Geschaeftsverstaendnis** | Explizite, eigenstaendige Phase ("Business Understanding") | Eingebettet in Problemdefinition |
| **Datenverstaendnis** | Explizite, eigenstaendige Phase ("Data Understanding") | Querschnittsaufgabe ueber alle vorbereitenden Schritte |
| **Granularitaet der Vorbereitung** | Eine Phase "Data Preparation" | Zwei separate Schritte (Bereinigung + Reduktion/Projektion) |
| **Granularitaet des Mining** | Eine Phase "Modeling" | Drei separate Schritte (Aufgabe, Algorithmus, Mining) |
| **Anzahl Phasen** | 6 Phasen | 9 Schritte |
| **Praxisorientierung** | Staerker praxisorientiert; Rahmen z. B. durch Modelle aus Einheit 1 (Skript Einheit 4) | Staerker methodisch-wissenschaftlich orientiert |

---

## 3. Phasenmodelle im Detail

Hummeltenberg (2008) hat vier typische Systematisierungen ausgewaehlt, die in der Literatur Verbreitung gefunden haben (Skript Einheit 1, Kap. 2.2.2). Alle vier Modelle beschreiben handlungsorientierte Entscheidungsprozesse und teilen Gemeinsamkeiten: Analysephase, Datensammlung, Alternativenermittlung, Bewertung, Auswahl, Reflektion. Der "Feedback Loop" fuer nachhaltiges organisationales Lernen ist allen gemein.

### 3.1 Phasenmodell nach Simon (1960/1977)

**Quelle:** Simon, H. A. (1977). The new science of management decision (3. ueberarb. Aufl.). Englewood Cliffs, NJ: Prentice-Hall. (Originalausgabe 1960)

**Kerngedanke:** Herbert A. Simon modelliert den Entscheidungsprozess als eine Abfolge von drei Kernphasen, die den kognitiven Prozess eines Entscheiders abbilden. Das Modell stammt urspruenglich aus der Managementwissenschaft und beschreibt, wie rationale Entscheidungen in Organisationen getroffen werden.

**Phasen:**

| Phase | Bezeichnung | Beschreibung |
|-------|-------------|-------------|
| 1 | **Intelligence** (Aufklaerung) | Erkennen und Definieren des Entscheidungsproblems. Umwelt wird systematisch nach Problemen und Chancen abgesucht. Daten werden gesammelt, um das Problem zu verstehen. Entspricht der Frage: "Was ist das Problem?" |
| 2 | **Design** (Entwurf) | Entwicklung und Analyse moeglicher Handlungsalternativen. Modelle werden erstellt, um Konsequenzen der Alternativen abzuschaetzen. Entspricht der Frage: "Welche Loesungsmoeglichkeiten gibt es?" |
| 3 | **Choice** (Auswahl) | Auswahl der besten Alternative aus den entwickelten Optionen. Bewertung anhand von Kriterien und Zielen. Entspricht der Frage: "Welche Alternative ist die beste?" |

**Erweiterung (1977):** Simon ergaenzte spaeter eine vierte Phase: **Implementation** (Umsetzung) -- die getroffene Entscheidung wird umgesetzt und ueberwacht.

**Bezug zur BI:** Die Intelligence-Phase entspricht dem Informationsbedarf, den BI-Systeme befriedigen sollen (Domaeneninformation, Trendanalysen). Die Design-Phase wird durch Simulationen, Szenarien und OLAP-Analysen unterstuetzt. Die Choice-Phase nutzt Bewertungs- und Risikoanalysen. BI liefert somit in jeder Phase spezifische Unterstuetzung (vgl. Hummeltenberg 2008, 4 Phasen der Entscheidung, Einheit 1).

### 3.2 SECI-Modell nach Nonaka und Takeuchi (1995)

**Quelle:** Nonaka, I. & Takeuchi, H. (1995). The knowledge-creating company. New York: Oxford University Press.

**Kerngedanke:** Das SECI-Modell beschreibt die organisationale Wissensgenerierung als spiralfoermigen Prozess der Wissensumwandlung zwischen **implizitem Wissen** (Erfahrungswissen, schwer formulierbar, personengebunden) und **explizitem Wissen** (kodifizierbar, dokumentierbar, uebertragbar). Der Prozess durchlaeuft vier Phasen, die sich zyklisch wiederholen und dabei auf immer hoeheren Ebenen (Individuum -> Gruppe -> Organisation -> Interorganisation) vollziehen.

**Phasen:**

| Phase | Bezeichnung | Wissensumwandlung | Beschreibung |
|-------|-------------|-------------------|-------------|
| **S** | **Sozialisation** | Implizit -> Implizit | Implizites Wissen wird durch gemeinsame Erfahrung, Beobachtung und Nachahmung von Person zu Person weitergegeben. Beispiel: Meister-Lehrling-Verhaeltnis, Learning by Doing. |
| **E** | **Externalisierung** | Implizit -> Explizit | Implizites Wissen wird in explizite Konzepte, Modelle oder Dokumentationen ueberfuehrt. Beispiel: Ein Experte formuliert seine Erfahrungsregeln als dokumentierte Geschaeftsregeln (Business Rules). |
| **C** | **Kombination** | Explizit -> Explizit | Verschiedene explizite Wissensbestaende werden systematisch zusammengefuehrt, sortiert, kategorisiert und zu neuem, komplexerem explizitem Wissen kombiniert. Beispiel: Daten aus verschiedenen Quellen werden im DWH integriert und durch OLAP/DM zu neuem Wissen verknuepft. |
| **I** | **Internalisierung** | Explizit -> Implizit | Explizites Wissen wird durch Anwendung und Uebung verinnerlicht und zu persoenlichem Erfahrungswissen. Beispiel: Aus DM-Ergebnissen werden Handlungsempfehlungen abgeleitet, die durch wiederholte Anwendung zu implizitem Expertenwissen werden. |

**Bezug zur BI:** Der KDD-Prozess kann als Spezialfall des SECI-Modells interpretiert werden (Skript Einheit 2: "KDD ist ein Spezialfall des Intelligence Cycle"). Insbesondere die Kombinations-Phase (explizit -> explizit) entspricht der maschinellen Datenanalyse im DWH/OLAP/DM. BI-Systeme unterstuetzen primaer die Kombinations- und Externalisierungsphase.

### 3.3 OODA-Loop nach Boyd (1995)

**Quelle:** Boyd, J. R. (1995). The essence of winning and losing.

**Kerngedanke:** Der OODA-Loop wurde urspruenglich im militaerischen Kontext entwickelt und beschreibt einen Entscheidungszyklus, der auf **Geschwindigkeit** ausgerichtet ist. Die Grundidee: Wer den OODA-Loop schneller durchlaeuft als der Gegner (bzw. die Konkurrenz), erlangt einen Vorteil. Das Modell betont die Dynamik und Iterativitaet von Entscheidungsprozessen in sich schnell aendernden Umgebungen.

**Phasen:**

| Phase | Bezeichnung | Beschreibung |
|-------|-------------|-------------|
| **O** | **Observe** (Beobachten) | Informationen ueber die aktuelle Situation sammeln. Umfelddaten erfassen, Veraenderungen wahrnehmen. Entspricht der Datensammlung und -erfassung in BI-Systemen (ETL, operative Systeme). |
| **O** | **Orient** (Orientieren) | Gesammelte Informationen analysieren, interpretieren und in den eigenen Kontext einordnen. Fruehere Erfahrungen, kulturelle Praegungen und mentale Modelle fliessen ein. Dies ist die **kritischste Phase** -- hier werden Daten zu handlungsrelevanter Information. Entspricht der Analyse- und Interpretationsphase (OLAP, Data Mining, KDD-Schritte 5-8). |
| **D** | **Decide** (Entscheiden) | Auf Basis der Orientierung eine Handlungsoption auswaehlen. Nicht als isolierter Akt, sondern als Hypothese, die getestet wird. |
| **A** | **Act** (Handeln) | Die Entscheidung umsetzen. Die Auswirkungen der Handlung erzeugen neue Beobachtungen und der Kreislauf beginnt erneut. |

**Bezug zur BI:** Der OODA-Loop ist besonders relevant fuer **Echtzeit-BI (RTBI)** und **BAM** (Business Activity Monitoring). Die Idee, den Entscheidungszyklus schneller zu durchlaufen, korrespondiert direkt mit dem Konzept der Latenzreduktion (Datenlatenz, Analyselatenz, Entscheidungslatenz) aus Einheit 4. RTBI verkuerzt alle vier OODA-Phasen.

### Vergleich der Phasenmodelle

| Aspekt | Simon | SECI | OODA | PDCA |
|--------|-------|------|------|------|
| **Ursprung** | Managementwissenschaft | Wissensmanagement | Militaerstrategie | Qualitaetsmanagement |
| **Fokus** | Rationaler Entscheidungsprozess | Wissensgenerierung und -transformation | Geschwindigkeit im Entscheidungszyklus | Kontinuierliche Prozessverbesserung |
| **Phasen** | Intelligence, Design, Choice (+ Implementation) | Sozialisation, Externalisierung, Kombination, Internalisierung | Observe, Orient, Decide, Act | Plan, Do, Check, Act |
| **Zyklisch?** | Bedingt (mit Erweiterung) | Ja (Wissensspirale) | Ja (Loop) | Ja (Kreislauf) |
| **BI-Bezug** | Informationsversorgung fuer Entscheidungen | DWH/DM als Kombination expliziten Wissens | RTBI/BAM fuer schnelle Zyklen | Mess- und Steuerkreislauf, Controllingperspektive |

---

## 4. ODS vs. DWH

### Stichpunktartige Gegenueberstallung

| Kriterium | ODS (Operational Data Store) | DWH (Data Warehouse) |
|-----------|----------------------------|---------------------|
| **Definition** | "Themenorientierte, integrierte, nicht dauerhafte, detaillierte Sammlung von Daten" (Inmon) | "A subject-oriented, integrated, nonvolatile, and time-variant collection of data in support of management's decisions" (Inmon, 2000) |
| **Persistenz** | **Nicht dauerhaft/nicht persistent** -- Daten werden regelmaessig aktualisiert und ueberschrieben | **Dauerhaft (nonvolatile)** -- Daten werden nicht ueberschrieben; alte und neue Werte koexistieren |
| **Zeitbezug** | **Zeitpunktbezogen** -- aktuelle, zeitnahe Daten | **Zeitraumbezogen** -- historische Daten ueber 5-10 Jahre |
| **Detaillierungsgrad** | **Detailliert** -- granulare Einzeldaten | **Aggregiert bis detailliert** -- Basisschicht (Tabellen aus Quellsystemen) und Aggregationsschicht (fuer OLAP optimiert) |
| **Datenaktualitaet** | **Sehr aktuell/zeitnah** -- Daten fuer zeitnahe Auswertungen | **Historisch** -- Daten werden periodisch geladen (Refresh) |
| **Zweck** | Zeitnahe, **operativ-integrierte Auswertungen**, die in Quellsystemen nicht oder nur schwer moeglich sind | **Strategische Entscheidungsunterstuetzung** -- langfristige Analysen und Trendbetrachtungen |
| **Integration** | Integration von Daten aus einer oder mehreren Datenquellen fuer **transaktionsorientierte und integrierte Datenhaltung** | Integration **aller** relevanten internen und externen Datenquellen |
| **Zielgruppe** | Operativ taetige Mitarbeiter, die aktuelle integrierte Informationen benoetigen | Management und Entscheidungstraeger auf allen Ebenen |

### Konkrete Anwendungsszenarien

**ODS-Szenarien:**
- Angebotserstellung in Abhaengigkeit zeitnaher Boersenkurse (Skript Einheit 3)
- Echtzeit-Kundenbetreuung: Agenten sehen integrierte Kundendaten aus mehreren Systemen in Echtzeit (vgl. Continental Airlines)
- Bestandsabfragen ueber mehrere Lagerstandorte hinweg fuer zeitnahe Lieferzusagen
- Zusammenfuehrung von Transaktionsdaten aus verschiedenen Filialen fuer tagesaktuelle Umsatzuebersichten

**DWH-Szenarien:**
- Langfristige Trendanalyse: Umsatzentwicklung ueber 5 Jahre nach Produktgruppen, Regionen, Zeitraeumen (OLAP-Analyse)
- Kundensegmentierung und Abwanderungspraevention mittels Data Mining (vgl. Fallstudie Newspaper Industry)
- Ertragsorientierte Preispolitik auf Basis integrierter historischer Daten (vgl. Continental Airlines, ab 1998)
- Strategische Planung: Soll-Ist-Vergleiche, Forecastberechnungen, Szenarioanalysen

---

## 5. OLAP-Operationen am Beispiel

### Der OLAP-Wuerfel: Produkt x Region x Zeit

Beispiel: Ein Einzelhandelsunternehmen analysiert seine **Umsatzdaten** anhand von drei Dimensionen:
- **Produkt-Dimension:** Getraenke, Lebensmittel, Bekleidung (mit Hierarchie: z. B. Lebensmittel -> Gemuese, Fleisch, Konserven, Brot, Suesswaren; vgl. Skript Einheit 3, Abb. 15)
- **Region-Dimension:** Nord, Sued, West, Ost (mit Hierarchie: Land -> Bundesland -> Stadt)
- **Zeit-Dimension:** Q1 2024, Q2 2024, Q3 2024, Q4 2024 (mit Hierarchie: Jahr -> Quartal -> Monat)

Die Faktentabelle enthaelt die Kennzahl **Umsatz** (in EUR). Die Schluessel Produkt_ID, Region_ID und Zeit_ID verweisen auf die Dimensionstabellen (vgl. Star-Schema, Skript Einheit 3, Abb. 12).

### Operation 1: Pivotierung / Rotation

**Beschreibung:** Der OLAP-Wuerfel wird um seine horizontale oder vertikale Achse gedreht. Betrachtete Dimensionen werden gegeneinander ausgetauscht. Die Datentiefe aendert sich nicht (Skript Einheit 3).

**Beispiel:**
- **Vorher:** Zeilen = Produkte, Spalten = Regionen (fuer Q1 2024)
- **Nachher:** Zeilen = Regionen, Spalten = Produkte (fuer Q1 2024)

```
Vorher:                          Nachher (nach Pivotierung):
            Nord  Sued  West              Getraenke  Lebensmittel  Bekleidung
Getraenke   120   150   90     Nord          120         200           80
Lebensmittel 200  180  160     Sued          150         180          110
Bekleidung   80   110   70     West           90         160           70
```

Die Daten bleiben identisch -- nur die Perspektive (welche Dimension auf welcher Achse) aendert sich.

### Operation 2: Roll-Up (Aggregation)

**Beschreibung:** Daten werden staerker zusammengefasst, indem die Hierarchieebene "nach oben" verschoben wird (Skript Einheit 3, Abb. 15).

**Beispiel (Region-Dimension):**
- **Vorher:** Umsaetze pro **Stadt** (Hamburg, Muenchen, Koeln, Berlin)
- **Nachher:** Umsaetze pro **Bundesland** (Hamburg -> HH, Muenchen -> Bayern, Koeln -> NRW, Berlin -> Berlin)
- **Noch weiter:** Umsaetze pro **Land** (Deutschland gesamt)

```
Detailliert (Stadt):      Roll-Up (Bundesland):     Roll-Up (Land):
Hamburg      120           HH          120            Deutschland  800
Muenchen     200           Bayern      200
Koeln        180           NRW         300
Duesseldorf  120
Berlin       180           Berlin      180
```

### Operation 3: Drill-Down (Disaggregation)

**Beschreibung:** Gegenteil von Roll-Up. Daten werden eine Hierarchieebene tiefer disaggregiert (Skript Einheit 3, Abb. 15).

**Beispiel (Produkt-Dimension, vgl. Skript):**
- **Vorher:** Umsatz fuer "Lebensmittel" gesamt = 500
- **Nachher:** Aufschluesselung in Gemuese (80), Fleisch (150), Konserven (70), Brot (120), Suesswaren (80)

```
Aggregiert:                 Drill-Down:
Lebensmittel   500    ->    Gemuese       80
                            Fleisch      150
                            Konserven     70
                            Brot         120
                            Suesswaren    80
```

### Operation 4: Slice (Scheibe)

**Beschreibung:** Eine Dimension wird auf einen einzigen Wert reduziert, alle anderen Dimensionen behalten alle Werte. Ergebnis: eine "Scheibe" aus dem Wuerfel (Skript Einheit 3).

**Beispiel:**
- **Slice auf Zeit = Q2 2024:** Die Zeit-Dimension wird fixiert. Ergebnis ist eine 2D-Tabelle (Produkt x Region) nur fuer Q2 2024.

```
3D-Wuerfel (Produkt x Region x Zeit)

Slice: Zeit = "Q2 2024"    ->    2D-Tabelle:

                Nord    Sued    West    Ost
Getraenke       130     160     100      85
Lebensmittel    210     195     170     140
Bekleidung       95     120      80      65
```

### Operation 5: Dice (Teilwuerfel)

**Beschreibung:** Der Anwender waehlt einzelne Bloecke / eine Teilauswahl aus dem Gesamtwuerfel. In **mehreren** Dimensionen werden Werte eingeschraenkt. Ergebnis: ein neuer, kleinerer Datenwuerfel (Skript Einheit 3).

**Beispiel:**
- **Dice:** Produkt IN {Getraenke, Lebensmittel} UND Region IN {Nord, Sued} UND Zeit IN {Q1, Q2}

```
Gesamtwuerfel: 3 Produkte x 4 Regionen x 4 Quartale

Dice-Ergebnis: 2 Produkte x 2 Regionen x 2 Quartale

                    Q1                Q2
              Nord    Sued      Nord    Sued
Getraenke     120     150       130     160
Lebensmittel  200     180       210     195
```

### Zusammenfassung der Operationen

| Operation | Was passiert? | Dimensionen | Ergebnis |
|-----------|--------------|-------------|----------|
| **Pivotierung** | Achsen tauschen | Gleiche Anzahl, andere Anordnung | Gleicher Wuerfel, andere Sichtweise |
| **Roll-Up** | Hierarchie aufwaerts | Grobere Granularitaet in einer Dimension | Aggregierte Daten |
| **Drill-Down** | Hierarchie abwaerts | Feinere Granularitaet in einer Dimension | Detailliertere Daten |
| **Slice** | Eine Dimension fixieren | Reduzierung um eine Dimension | Scheibe (n-1 Dimensionen) |
| **Dice** | Mehrere Dimensionen einschraenken | Alle Dimensionen bleiben, aber mit Teilmengen | Kleinerer Teilwuerfel |

---

## 6. Transferfragen ueber Einheitsgrenzen

### Frage 1: ETL-Prozess und KDD-Prozess

**Frage:** Vergleichen Sie den ETL-Prozess (Einheit 3) mit den vorbereitenden Schritten des KDD-Prozesses (Einheit 2). Welche Parallelen und Unterschiede bestehen?

**Musterantwort:** Der ETL-Prozess (Extraktion, Transformation, Laden) und die vorbereitenden KDD-Schritte (Datenauswahl, Bereinigung/Aufbereitung, Reduktion/Projektion) weisen deutliche Parallelen auf: Beide befassen sich mit der Selektion relevanter Daten, der Bereinigung von Qualitaetsproblemen und der Transformation in ein analysegeeignetes Format. Der zentrale Unterschied liegt im **Ziel**: ETL bereitet Daten fuer die dauerhafte, strukturierte Speicherung im DWH vor (Integration heterogener Quellen, Vereinheitlichung von Kodierungen). Die KDD-Vorbereitungsschritte bereiten Daten spezifisch fuer einen konkreten DM-Analyseschritt vor (z. B. Behandlung fehlender Werte, Attributselektion, Normalisierung). ETL ist infrastrukturell und wiederkehrend; KDD-Vorbereitung ist problemspezifisch und einmalig pro Analyseprojekt.

### Frage 2: Datenqualitaet und Fallstudie Newspaper Industry

**Frage:** Inwiefern illustriert die Fallstudie "Newspaper Industry" (Einheit 4) die Datenqualitaetskategorien nach Wang und Strong (Einheit 3)?

**Musterantwort:** Die Fallstudie zeigt Probleme in mehreren Kategorien: (1) **Intrinsische Datenqualitaet**: Freitextfelder mit inkonsistenten Formulierungen fuer gleiche Sachverhalte verletzen die Genauigkeit. (2) **Kontextabhaengige Datenqualitaet**: Werbedaten waren zu unspezifisch und enthielten kein Erfolgsmass -- die Relevanz und Vollstaendigkeit fuer die Analyseziele waren nicht gegeben. Operative Daten waren fuer Analysezwecke ungeeignet (fehlende Relevanz). (3) **Darstellungsqualitaet**: Unterschiedliche Begriffe fuer gleiche Sachverhalte verletzten die konsistente Darstellung. (4) **Zugangsqualitaet**: Haushaltsdaten mussten aus Datenschutzgruenden transformiert werden, was zu Informationsverlust fuehrte. Die zentrale Erkenntnis: "Beduerfnisse der Datenanalyse muessen schon bei der Erhebung mitgedacht werden" (Skript Einheit 4).

### Frage 3: OLAP-Operationen und Entscheidungsunterstuetzung

**Frage:** Erklaeren Sie, wie die OLAP-Operationen Roll-Up und Drill-Down den Entscheidungsprozess nach dem PDCA-Kreislauf (Einheit 1) konkret unterstuetzen koennen.

**Musterantwort:** In der **Plan-Phase** kann ein Manager per Roll-Up zunaechst aggregierte Umsatzdaten auf Laenderebene betrachten, um Problembereiche zu identifizieren. Durch Drill-Down wird der auffaellige Bereich tiefer analysiert (Land -> Bundesland -> Stadt), um die genaue Ursache einzugrenzen. In der **Check-Phase** werden nach Umsetzung einer Massnahme (Do) die Messergebnisse erneut per Roll-Up aggregiert betrachtet und per Drill-Down im Detail ueberprueft. Roll-Up liefert den Ueberblick fuer die strategische Bewertung, Drill-Down die Detailtiefe fuer die operative Ursachenanalyse -- beide Perspektiven sind fuer den PDCA-Kreislauf notwendig.

### Frage 4: Business Rules und BAM

**Frage:** Erlaeutern Sie den Zusammenhang zwischen Business Rules (Einheit 3) und der Business Rule Engine (BRE) als Komponente des BAM (Einheit 4).

**Musterantwort:** Business Rules sind Richtlinien, die das Unternehmensverhalten steuern (Scheer/Werth 2006). Sie werden im DWH-Kontext u. a. als Transformationsregeln genutzt (Einheit 3). Die BRE als BAM-Komponente (Einheit 4) beobachtet Ereignisse in Echtzeit und leitet auf Basis operationalisierter Business Rules automatisiert geeignete Massnahmen ein -- z. B. die gezielte Information bestimmter Personen bei Grenzwertueberschreitungen. Waehrend Business Rules in Einheit 3 primaer statisch im DWH-Kontext beschrieben werden (Regelrepositorium, RuleML, BRML), macht die BRE sie dynamisch und echtzeitfaehig. Das Fallbeispiel Continental Airlines zeigt dies konkret: Die BRE ermittelt bei Reklamationen automatisch eine Kompensation auf Basis von Falldetails, historischen Kundendaten und Ticketinformationen (Skript Einheit 4).

### Frage 5: Operative vs. dispositive Daten und RTBI

**Frage:** Inwiefern weicht RTBI (Einheit 4) die klassische Trennung zwischen operativen und dispositiven Daten (Einheit 1/3) auf?

**Musterantwort:** Klassisch sind operative Daten aktuell und transaktionsorientiert (Tagesgeschaeft), dispositive Daten historisch und verdichtet (Entscheidungsunterstuetzung). RTBI durchbricht diese Trennung, indem operative Daten nahezu in Echtzeit fuer analytische Zwecke verfuegbar gemacht werden. In-Memory Analytics (Einheit 4) ermoeglicht, dass Daten aus operativen Systemen nicht erst in dispositive Systeme uebertragen werden muessen. Im biMM (Stufe 5) wird die "Verschmelzung operativer und dispositiver Systeme" als Merkmal aktiven Wissensmanagements genannt. Continental Airlines illustriert dies: Flugdaten werden direkt von Maschinen in der Luft uebertragen und fuer Analysen genutzt -- die Daten sind gleichzeitig operativ (aktuelle Fluglage) und dispositiv (Basis fuer analytische Entscheidungen).

### Frage 6: Data Marts und ODS

**Frage:** Grenzen Sie Data Marts und den Operational Data Store (ODS) voneinander ab. Fuer welche Szenarien eignet sich welcher Ansatz?

**Musterantwort:** Beide sind Komponenten der DWH-Gesamtarchitektur (Einheit 3), unterscheiden sich aber grundlegend: **Data Marts** sind analyseorientierte Systeme mit eigenem Datenbestand, zugeschnitten auf Fachbeduerfnisse bestimmter Benutzergruppen (Farkisch, 2011). Sie enthalten aggregierte, historische Daten fuer analytische Abfragen (z. B. Marketing-Analysen, Controlling-Reports). Der **ODS** hingegen haelt detaillierte, aktuelle Daten fuer zeitnahe, operativ-integrierte Auswertungen bereit, die in Quellsystemen nicht moeglich sind. ODS-Daten sind nicht dauerhaft (Inmon). **Szenarien:** Data Marts eignen sich, wenn eine Fachabteilung regelmaessig historische Analysen durchfuehren muss (Trend, Segmentierung). Der ODS eignet sich, wenn zeitnahe Daten aus mehreren integrierten Quellen benoetigt werden (z. B. Boersenkurs-abhaengige Angebotserstellung, Echtzeit-Kundenservice).

### Frage 7: Metadaten und Text Mining

**Frage:** Vergleichen Sie die Rolle von Metadaten in der DWH-Architektur (Einheit 3) mit der Extraktion von Metadaten durch Text Mining (Einheit 4).

**Musterantwort:** In der DWH-Architektur (Einheit 3) sind Metadaten "Daten ueber Daten" (Sen, 2004), die im Metadatenbanksystem (Business Data Directory) verwaltet werden. Sie umfassen technische Metadaten (Schemata, Datenfluesse) und fachliche Metadaten (betriebswirtschaftliches Wissen, Interpretationshilfen). Diese werden primaer strukturiert erhoben bzw. manuell erfasst. Text Mining (Einheit 4) ergaenzt diesen Ansatz, indem es automatisiert strukturierte Metadaten aus **unstrukturierten** Textdokumenten extrahiert: Namen, Beziehungen, Themen, Stimmungen (Sentiment Analyse). Dies entspricht dem zweiten Vorgehensmodell nach Baars und Kemper (2008): "Analyse von Inhaltssammlungen zur Extraktion von Metadaten". TF-IDF liefert dabei die gewichtete Relevanz einzelner Terme. Die extrahierten Metadaten koennen in die strukturierte Datenbank des DWH integriert werden und so die fachlichen Metadaten anreichern.

### Frage 8: CRISP-DM, CDM und Continental Airlines

**Frage:** Zeigen Sie am Beispiel der Fallstudie Continental Airlines (Einheit 4), wie die Dimensionen des CDM (Einheit 1) und der CRISP-DM-Ansatz zusammenwirken.

**Musterantwort:** Das CDM (Einheit 1) fordert die Beruecksichtigung von Akteur, Organisation und Applikationen. Bei Continental Airlines: (1) **Akteur:** Entscheider in verschiedenen Abteilungen (ueber 1.400 Mitarbeitende mit DWH-Zugang) mit unterschiedlichem Informationsbedarf -- vom Reservierungsagenten bis zum strategischen Management. Die offene Datenkultur foerdert die individuelle Informationsnutzung. (2) **Organisation:** Der "Go Forward Plan" gibt die strategische Ausrichtung vor; die stetige Ausdehnung auf weitere Abteilungen zeigt die organisatorische Einbettung. (3) **Applikationen:** DWH mit vier echtzeitfaehigen Datenstroemen, BRE fuer automatisierte Entscheidungen. Der CRISP-DM-Ansatz zeigt sich in der Vorgehensweise: Business Understanding (Geschaeftsziele nach Bethune), Data Understanding (Integration heterogener Datenquellen), Data Preparation (ETL fuer Flug-, Kunden-, Reservierungsdaten), Modeling/Evaluation (ertragsgesteuerte Preispolitik), Deployment (Reklamationsprozess mit BRE). Der Erfolg beruht darauf, dass alle drei CDM-Dimensionen gleichzeitig adressiert wurden.

---

## Tags

`#ergaenzungen` `#StarSchema` `#SnowflakeSchema` `#CRISP-DM` `#KDD` `#Phasenmodelle` `#Simon` `#SECI` `#OODA` `#PDCA` `#ODS` `#DWH` `#OLAP-Operationen` `#Pivotierung` `#RollUp` `#DrillDown` `#Slice` `#Dice` `#Transferfragen` `#einheituebergreifend`
