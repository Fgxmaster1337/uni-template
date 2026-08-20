# Schwaechen-Analyse -- 32711 Business Intelligence

> Erstellt: 2026-08-20 | Ziel: Gezielte Klausurvorbereitung durch Identifikation von Luecken

---

## Themenabdeckung

### Einheit 1: Grundlagen der BI

**Gut abgedeckt:**
- BI-Definition (ganzheitlich), Hub-and-Spoke-Architektur (4 Stufen)
- PDCA-Kreislauf, CDM (3 Dimensionen), Ackoffs 5 Annahmen
- Daten-Information-Wissen-Abgrenzung, operative vs. dispositive Daten
- MDP-Formeln (aufgelistet), historische Entwicklung des BI-Begriffs

**Moegliche Luecken:**
- **Phasenmodelle nach Simon, SECI, OODA:** Im Wissensdokument nur als Aufzaehlung erwaehnt, aber nicht einzeln erlaeutert. In einer Klausur koennte nach Gemeinsamkeiten/Unterschieden dieser Modelle gefragt werden.
- **MDP-Berechnung:** Formeln sind dokumentiert, aber es gibt kein durchgerechnetes Beispiel. Wenn eine Aufgabe kommt, in der eine optimale Strategie oder Wertfunktion berechnet werden soll, fehlt die Uebung.
- **Luhn (1958) im Detail:** Die Verbindung Business-Intelligence-System ist erwaehnt, aber die konkrete Argumentation (warum das Konzept in Vergessenheit geriet und wie es wiederbelebt wurde) koennte vertiefter pruefungsrelevant sein.

### Einheit 2: Methoden und Instrumente

**Gut abgedeckt:**
- KDD-Prozess (9 Schritte, 3 Meta-Phasen), Abgrenzung KDD vs. DM
- Vier Grundaufgaben (Assoziation, Clustering, Klassifizierung, Approximation)
- Entscheidungsbaeume (CART vs. C4.5), Gini-Index, Entropie, GainRatio
- Clusteranalyse (hierarchisch, k-means, Linkage-Verfahren, Dendrogramm)
- Apriori-Algorithmus (Support, Konfidenz), KNN, Naive Bayes, k-NN
- Konfusionsmatrix, Recall, Precision, Accuracy
- Complete-Linkage-Berechnung (ein ausfuehrliches Beispiel vorhanden)
- Skalenniveaus, Kodierungsverfahren, Standardisierung, Normalisierung

**Moegliche Luecken:**
- **Gini-Index-Berechnung:** Formel vorhanden, aber KEIN durchgerechnetes Beispiel mit konkreten Zahlen. Dies ist einer der wahrscheinlichsten Berechnungsaufgabentypen.
- **Entropie/InformationGain-Berechnung:** Ebenfalls nur Formel, kein durchgerechnetes Beispiel. C4.5-Aufgaben erfordern log2-Berechnungen, die geuebte werden muessen.
- **Support/Konfidenz-Berechnung:** Formeln bekannt, aber kein Rechenbeispiel mit konkreter Transaktionsdatenbank vorhanden. Der Apriori-Algorithmus mit Mindestsupport und Mindestkonfidenz sollte schrittweise durchgerechnet werden.
- **Regressionskoeffizienten berechnen:** theta0 und theta1 mit der Methode der kleinsten Quadrate bestimmen -- keine Uebung vorhanden.
- **Naive-Bayes-Berechnung:** Bedingte Wahrscheinlichkeiten berechnen und Klassenzuordnung vornehmen -- keine Uebung vorhanden.
- **k-means-Algorithmus schrittweise:** Initiale Zentroiden, Zuordnung, Neuberechnung -- kein Durchlauf vorhanden.
- **Kodierungsverfahren anwenden:** Eins-aus-N, Dummy, Effekt, Unaer an konkretem Beispiel -- keine Uebung.
- **Logistische Regression:** Formel bekannt, aber die Maximum-Likelihood-Schaetzung und der praktische Unterschied zur linearen Regression koennten gefragt werden.

### Einheit 3: Intelligente Datenhaltung und -bereitstellung

**Gut abgedeckt:**
- Business Rules (Typen, Durchfuehrungslevel, BMM)
- Metadaten (Definition, Klassifizierung, 8 Kategorien nach Auth)
- Datenqualitaet (Wang/Strong, TQM nach English, 3 Strategien nach Redman)
- DWH-Architektur (5 Ebenen, SINT, ETL, ODS, Staging Area)
- OLAP (Codd-Regeln, FASMI, ROLAP/MOLAP/HOLAP, 5 Operationen)
- Data Marts vs. DWH (ausfuehrlicher Vergleich)

**Moegliche Luecken:**
- **Star-Schema vs. Snowflake-Schema:** Das Star-Schema ist beschrieben (Faktentabelle + Dimensionstabellen). Das Snowflake-Schema wird in den Wissensdokumenten NICHT erklaert. In Klausuren wird haeufig nach dem Unterschied gefragt.
- **OLAP-Operationen an konkretem Beispiel:** Roll-Up, Drill-Down, Slice, Dice sind definiert, aber es fehlt eine Uebung, in der man an einem konkreten OLAP-Wuerfel diese Operationen durchfuehrt.
- **Codds 12+6 Regeln im Detail:** Alle 18 Regeln sind aufgelistet -- in einer Klausur reicht moeglicherweise eine Auswahl, aber die Faehigkeit, einzelne Regeln mit Beispielen zu erlaeutern, sollte geuebt werden.
- **Business Rules Mining:** Nur kurz erwaehnt. Koennte als Transferfrage kommen (Verbindung zu Rule Induction/Apriori aus Einheit 2).
- **ODS vs. DWH:** Die Abgrenzung ist vorhanden, aber eine praegsame Gegenueberstallung mit konkreten Anwendungsszenarien fehlt.

### Einheit 4: Neuere Entwicklungen und Anwendungsbeispiele

**Gut abgedeckt:**
- biMM (5 Stufen, 3 Dimensionen), Wertbeitrag der BI (Popovic)
- RTBI, Latenzarten (Daten-, Analyse-, Entscheidungslatenz), Halbwertszeit
- BAM (5 Komponenten), SSBI (4 Stufen), CPM, MBI, BYOD
- BIaaS, Cloud-BI (8 Dimensionen), SBI vs. CBI
- Text Mining, Bag-of-Words, TF-IDF (vollstaendige Formeln)
- Fallstudien Newspaper Industry und Continental Airlines
- BI 1.0/2.0/3.0, CRISP-DM

**Moegliche Luecken:**
- **TF-IDF-Berechnung:** Alle Formeln sind dokumentiert, aber es gibt KEIN durchgerechnetes Beispiel mit konkretem Korpus. Dies ist ein sehr wahrscheinlicher Berechnungsaufgabentyp.
- **Normierung von Featurevektoren:** Formel vorhanden, aber keine Uebung zur Normierung und anschliessenden Distanzberechnung zwischen Dokumenten.
- **CRISP-DM vs. KDD detaillierter Vergleich:** Die Unterschiede (Business Understanding, Data Understanding als explizite Phasen) sind erwaehnt, aber eine tabellarische Gegenueberstallung wuerde die Klausurantwort verbessern.
- **Makrotrends nach Baars et al.:** Die 5 Forschungsbereiche sind genannt, aber die Faehigkeit, konkrete Beispiele aus dem Kurs zuzuordnen, sollte geuebt werden.
- **BI-Governance:** Nur als MBI-Governance angerissen; koennte breiter gefragt werden.

---

## Schwierige Aufgabentypen

### 1. Berechnungsaufgaben (KRITISCH)

Die groesste Schwaeche des Materials: Es gibt kaum durchgerechnete Beispiele. In Klausuren an der FernUni werden erfahrungsgemaess 1-2 Berechnungsaufgaben gestellt. Betroffen sind:

| Berechnung | Status | Risiko |
|------------|--------|--------|
| Gini-Index + GiniGain | Nur Formel, kein Beispiel | **HOCH** |
| Entropie + InformationGain + GainRatio | Nur Formel, kein Beispiel | **HOCH** |
| TF-IDF (inkl. dfreq, info) | Nur Formel, kein Beispiel | **HOCH** |
| Support + Konfidenz (Apriori) | Nur Formel, kein Beispiel | **HOCH** |
| Complete-Linkage Clustering | 1 Beispiel vorhanden | Mittel |
| Min-Max-Normalisierung | 1 einfaches Beispiel | Mittel |
| z-Transformation | Nur Formel, kein Beispiel | Mittel |
| Lineare Regression (theta0, theta1) | Nur Formel, kein Beispiel | Mittel |
| k-means (schrittweise) | Nur Beschreibung, kein Beispiel | Mittel |
| Naive Bayes (bedingte Wahrsch.) | Nur Beschreibung, kein Beispiel | Mittel |
| Distanzmatrix berechnen | Im Linkage-Beispiel implizit | Niedrig |

### 2. Transferaufgaben (KRITISCH)

Transferaufgaben verlangen, gelerntes Wissen auf ein neues Szenario anzuwenden. Das Material enthaelt einige gute Beispiele (IBAN-Fehlerart, Kreditwuerdigkeit), aber es fehlen:

- **Verfahrensauswahl:** "Fuer folgendes Problem -- welches DM-Verfahren waehlen Sie und warum?" (erfordert Kenntnis aller vier Grundaufgaben + Verfahrenseigenschaften)
- **Fehlerklassifikation in neuen Szenarien:** Ueber den IBAN-Fall hinaus sollten weitere Fehlerbeispiele klassifiziert werden (semantisch/syntaktisch/coverage)
- **OLAP-Operationen an Szenarien:** "Ein Manager moechte X sehen -- welche OLAP-Operation ist noetig?"
- **biMM-Einordnung:** "Beschreiben Sie ein Unternehmen und ordnen Sie es einer biMM-Stufe zu"
- **Latenz-Szenarien:** "Fuer Informationstyp X -- lohnt sich Latenzreduktion?"

### 3. Diskussionsaufgaben (MITTLERES RISIKO)

Einige Diskussionsaufgaben sind gut vorbereitet (Ackoffs Annahmen, Vor-/Nachteile sozialer Netzwerke, Fallstudien-Lessons-Learned). Schwaechen:

- **Kritische Wuerdigung von Verfahren:** Wann versagt k-means? Wann ist ein Entscheidungsbaum besser als KNN? Wann Naive Bayes trotz "naiver" Annahme gut?
- **Ethische/rechtliche Aspekte:** Datenschutz bei BI, BYOD-Risiken -- nur oberflaechlich behandelt
- **Vor-/Nachteile von DWH vs. Data Marts aus Managersicht:** Gut dokumentiert, aber die argumentative Aufbereitung fuer eine Diskussionsfrage fehlt

---

## Berechnungs-Schwaechen

### Prioritaet 1: Unbedingt ueben (hohe Klausurwahrscheinlichkeit)

**a) Gini-Index und GiniGain (CART)**

Formel: Gini(t) = 1 - Summe(p(Ci|t)^2)

Typische Aufgabe: Gegeben ein Datensatz mit Klassen A und B, berechne den Gini-Index fuer einen Knoten und den GiniGain fuer verschiedene Splits. Waehle den besten Split.

Schwierigkeit: Die gewichtete Berechnung des GiniGain (Gewichtung nach Anzahl Instanzen in Kindknoten) wird oft vergessen.

**b) Entropie und InformationGain (C4.5)**

Formel: H(t) = -Summe(p(Ci|t) * log2(p(Ci|t)))

Typische Aufgabe: Berechne Entropie des Wurzelknotens, dann InformationGain fuer jedes Attribut. Berechne ggf. GainRatio.

Schwierigkeit: log2-Werte muessen bekannt sein oder berechnet werden koennen (log2(3) ≈ 1.585, log2(5) ≈ 2.322). Die SplitInfo-Berechnung fuer GainRatio ist ein zusaetzlicher Schritt.

**c) TF-IDF-Berechnung**

Formeln:
- tfreq(d_i, q_j) = Haeufigkeit von q_j in d_i
- dfreq(q_j) = |X_q_j| / |X|
- TF-IDF: x_i,j = tfreq(d_i, q_j) * log(|X| / |X_q_j|)

Typische Aufgabe: Gegeben 3-5 Dokumente und ein Lexikon. Berechne TF-IDF-Werte fuer ausgewaehlte Terme. Bestimme die repraesentativsten Terme.

Schwierigkeit: Logarithmus-Berechnungen; Unterscheidung tfreq vs. dfreq.

**d) Support und Konfidenz (Apriori)**

Formeln:
- support(Ih -> Ic) = |{xi : Ih vereinigt Ic Teilmenge Q+(xi)}| / |XTr|
- confidence(Ih -> Ic) = support(Ih -> Ic) / support(Ih)

Typische Aufgabe: Gegeben eine Transaktionsdatenbank. Bestimme haeufige Itemsets (Mindestsupport), leite Regeln ab (Mindestkonfidenz). Beachte: Konfidenz ist NICHT symmetrisch.

### Prioritaet 2: Sollte geuebt werden

**e) Clusteranalyse-Distanzmatrizen**

Ein Beispiel ist vorhanden (Complete-Linkage), aber:
- Single-Linkage und Average-Linkage sollten ebenfalls durchgerechnet werden
- Euklidische vs. Manhattan-Distanz an einem Beispiel berechnen
- k-means schrittweise: Initialisierung, Zuordnung, Neuberechnung der Zentroiden

**f) Konfusionsmatrix-Kennzahlen**

Die Formeln sind klar, aber die korrekte Zuordnung von TP/FP/TN/FN in einem konkreten Szenario muss sicher sitzen. Insbesondere: Welche Klasse ist "positiv"?

**g) Normalisierung und Standardisierung**

Min-Max ist mit einem einfachen Beispiel vorhanden. Die z-Transformation (Berechnung von x_quer und s) sollte ebenfalls geuebte werden.

---

## Querverbindungen zwischen Einheiten

Die folgenden Themen tauchen in mehreren Einheiten auf und eignen sich besonders fuer Transferfragen:

### 1. Datenqualitaet (Einheiten 2 + 3)

- **Einheit 2:** Fehlerklassen (semantisch, syntaktisch, coverage), Umgang mit Fehlern (Laissez Faire, reaktiv, proaktiv), "Garbage in -- Garbage out"
- **Einheit 3:** Datenqualitaetskriterien nach Wang/Strong, TQM nach English, 3 Strategien nach Redman, PDCA-Regelkreis fuer DQM
- **Transferfrage:** "Ordnen Sie die Fehlerklassen aus Einheit 2 den Datenqualitaetskategorien aus Einheit 3 zu. Wie unterstuetzt ein proaktives DQM den KDD-Prozess?"

### 2. DWH und ETL (Einheiten 1 + 3 + 4)

- **Einheit 1:** Hub-and-Spoke-Architektur, ETL als Teil der Architektur
- **Einheit 3:** Detaillierte ETL-Beschreibung, 5-Ebenen-Architektur, ODS, Staging Area
- **Einheit 4:** Datenlatenz haengt vom DWH-Aktualisierungszyklus ab; In-Memory Analytics als Alternative
- **Transferfrage:** "Wie veraendert In-Memory Analytics die klassische DWH-Architektur? Welche Ebenen der 5-Ebenen-Architektur sind betroffen?"

### 3. Operative vs. dispositive Daten (Einheiten 1 + 3 + 4)

- **Einheiten 1 + 3:** Klassische Trennung mit detaillierter Vergleichstabelle
- **Einheit 4:** RTBI und BAM weichen diese Trennung auf (Verschmelzung operativer und dispositiver Systeme in biMM Stufe 5)
- **Transferfrage:** "Inwiefern stellt RTBI die klassische Trennung zwischen operativen und dispositiven Daten in Frage?"

### 4. Entscheidungsprozesse und BI-Unterstuetzung (Einheiten 1 + 2 + 4)

- **Einheit 1:** PDCA-Kreislauf, CDM, handlungsorientierte Modellierung
- **Einheit 2:** KDD im Managementkreislauf
- **Einheit 4:** Geschlossener RTBI-Kreislauf, 4 Ausgestaltungen des BI-Prozess-Verhaeltnisses
- **Transferfrage:** "Vergleichen Sie den PDCA-Kreislauf aus Einheit 1 mit dem geschlossenen RTBI-Kreislauf aus Einheit 4. Welche Rolle spielt der KDD-Prozess?"

### 5. Business Rules (Einheiten 3 + 4)

- **Einheit 3:** Definition, Typen, Durchfuehrungslevel, BMM, Business Rules Mining
- **Einheit 4:** BRE als Komponente von BAM; Einsatz im Reklamationsprozess (Continental Airlines)
- **Transferfrage:** "Wie werden Business Rules in einem BAM-System operationalisiert? Erklaeren Sie am Beispiel."

### 6. Data Mining in der Praxis (Einheiten 2 + 4)

- **Einheit 2:** Alle DM-Verfahren theoretisch
- **Einheit 4:** Entscheidungsbaum in der Fallstudie Newspaper Industry; CRISP-DM vs. KDD
- **Transferfrage:** "Warum wurde in der Newspaper-Fallstudie ein Entscheidungsbaum gewaehlt und nicht k-NN oder Regression?"

### 7. Distanzfunktionen und Clustering (Einheiten 2 + 4)

- **Einheit 2:** Euklidische/Manhattan-Distanz, Clusteranalyse, k-means
- **Einheit 4:** Zentroidenbasierte Klassifikation im Text Mining, Normierung, Winkeldistanz
- **Transferfrage:** "Vergleichen Sie die Distanzberechnung in der klassischen Clusteranalyse mit der Dokumentendistanz im Text Mining."

### 8. PDCA-Kreislauf (Einheiten 1 + 3)

- **Einheit 1:** Als handlungsorientiertes Entscheidungsmodell
- **Einheit 3:** Als Regelkreis fuer Datenqualitaetsmanagement
- **Transferfrage:** "Erlaeutern Sie, wie der PDCA-Kreislauf sowohl auf Entscheidungsprozesse (Einheit 1) als auch auf Datenqualitaetsmanagement (Einheit 3) angewendet wird."

---

## Empfehlungen zur Nacharbeit

### Prioritaet 1: SOFORT ueben (hoechste Pruefungsrelevanz)

1. **Berechnungsaufgaben durchrechnen:**
   - Gini-Index + GiniGain an einem Datensatz mit 2-3 Klassen und 2-3 Attributen komplett durchrechnen (CART-Entscheidungsbaum Schritt fuer Schritt aufbauen)
   - Entropie + InformationGain + GainRatio an demselben Datensatz berechnen (C4.5 zum Vergleich)
   - TF-IDF fuer einen kleinen Korpus (3-5 Dokumente, 5-8 Terme) komplett berechnen
   - Support + Konfidenz fuer eine Transaktionsdatenbank (5-8 Transaktionen) berechnen und Apriori-Algorithmus schrittweise durchfuehren
   - k-means mit 2 Clustern und 5-6 Instanzen in 2D schrittweise durchfuehren

2. **Verfahrensauswahl uebeN:**
   - Fuer jede der 4 Grundaufgaben (Assoziation, Clustering, Klassifizierung, Approximation) ein konkretes Unternehmensszenario formulieren und das passende Verfahren begruenden
   - Die Grenzen jedes Verfahrens kennen (k-means: nur sphaerische Cluster, findet lokales Minimum; Entscheidungsbaeume: Overfitting-Gefahr; k-NN: kein Modell, speicherintensiv)

### Prioritaet 2: DIESE WOCHE vertiefen

3. **Fehlende Vergleiche erstellen:**
   - CRISP-DM vs. KDD-Prozess: Tabellarische Gegenueberstallung mit Phasen und Schwerpunkten
   - Star-Schema vs. Snowflake-Schema: Aufbau, Vor-/Nachteile (Snowflake-Schema ist im Material NICHT enthalten -- unbedingt ergaenzen)
   - ODS vs. DWH: Stichpunktartige Gegenueberstallung

4. **Querverbindungen aktiv ueben:**
   - Fuer jede der 8 oben genannten Querverbindungen eine Transferfrage formulieren und beantworten
   - Besonders wichtig: Datenqualitaet (E2+E3), DWH/ETL/RTBI (E1+E3+E4), operative/dispositive Daten (E1+E3+E4)

5. **Schwache OLAP-Praxis:**
   - Einen 3-dimensionalen OLAP-Wuerfel skizzieren und alle 5 Operationen (Pivotierung, Roll-Up, Drill-Down, Slice, Dice) daran durchspielen
   - OLAP vs. OLTP: Nochmals sicher verinnerlichen

### Prioritaet 3: VOR DER KLAUSUR wiederholen

6. **Definitionen sicher beherrschen:**
   - BI-Definition, KDD-Definition (Fayyad et al.), DWH-Definition (Inmon), OLAP-Definition
   - SINT-Eigenschaften, FASMI-Prinzip, Ackoffs 5 Annahmen
   - Daten vs. Information vs. Wissen
   - Die Definitionen sollten WORTGENAU oder sehr nahe am Original reproduzierbar sein

7. **Fallstudien-Argumentation:**
   - Newspaper Industry: Die Lehre ("Beduerfnisse der Datenanalyse schon bei der Erhebung mitdenken") als argumentativen Baustein fuer verschiedene Fragestellungen bereithalten
   - Continental Airlines: RTBI-Erfolgsfaktoren (Unternehmenskultur, offener Datenzugang, Prozessveraenderung) als argumentativen Baustein bereithalten

8. **Formelblatt erstellen:**
   - Alle klausurrelevanten Formeln auf ein Blatt: Gini, Entropie, GainRatio, Support, Konfidenz, TF-IDF, z-Transformation, Min-Max, Euklidische Distanz, Recall, Precision, Accuracy, lineare Regression (theta0, theta1)
   - Dieses Blatt mehrfach aus dem Gedaechtnis reproduzieren

---

## Zusammenfassung der kritischsten Luecken

| Rang | Luecke | Einheit | Massnahme |
|------|--------|---------|-----------|
| 1 | Keine Berechnungsbeispiele fuer Gini/Entropie | 2 | Sofort Beispielaufgaben rechnen |
| 2 | Keine TF-IDF-Berechnungsuebung | 4 | Sofort Beispielaufgaben rechnen |
| 3 | Keine Support/Konfidenz-Berechnungsuebung | 2 | Sofort Beispielaufgaben rechnen |
| 4 | Snowflake-Schema fehlt komplett | 3 | Ergaenzen und mit Star-Schema vergleichen |
| 5 | Keine k-means-Schrittberechnung | 2 | Beispiel durchrechnen |
| 6 | Keine Transferfragen ueber Einheitsgrenzen | 1-4 | Querverbindungen als Fragen formulieren |
| 7 | Verfahrensauswahl nicht geuebte | 2 | Szenarien mit Begruendung durchspielen |
| 8 | OLAP-Operationen nur theoretisch | 3 | Am Wuerfel-Beispiel durchspielen |
| 9 | Phasenmodelle (Simon, SECI, OODA) nur erwaehnt | 1 | Kerngedanken je Modell ergaenzen |
| 10 | CRISP-DM vs. KDD nicht tabellarisch | 2, 4 | Vergleichstabelle erstellen |
