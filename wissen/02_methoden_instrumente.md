# 02 - Methoden und Instrumente der Business Intelligence

> **Quelle:** 32711-02-S#1-S002664968.pdf (114 Seiten) | **Pruefungsrelevanz:** HOCH

## Ueberblick

Diese Einheit behandelt den Knowledge Discovery in Databases (KDD)-Prozess als zentralen Prozess der BI, der aus Rohdaten wettbewerbsrelevantes Wissen generiert. Der Prozess gliedert sich in drei Meta-Phasen: vorbereitende Schritte (Problemdefinition, Datenauswahl, Datenbereinigung, Attributtransformation), Data Mining (Aufgabenauswahl, Algorithmenauswahl, Mustersuche) und nachbereitende Schritte (Evaluation, Interpretation, Verwendung). Es werden die wichtigsten DM-Verfahren ausfuehrlich vorgestellt: Entscheidungsbaumverfahren (TDIDT, CART, C4.5), Regressionsanalyse, Clusteranalyse (hierarchisch, k-means), Apriori-Algorithmus, Kuenstliche Neuronale Netze, Naive Bayes und k-Nearest Neighbour. Die Einheit betont, dass KDD kein rein technischer Prozess ist, sondern in den Managementkreislauf eingebettet werden muss.

---

## Kernkonzepte

### Definition: Knowledge Discovery in Databases (KDD)

"Knowledge Discovery in Databases is the non-trivial process of identifying valid, novel, potentially useful, and ultimately understandable patterns in data." (Fayyad et al., 1996, S. 6)

**Interpretation nach Duesing (2006):**
- **Nicht-trivial:** Zusammenhaenge werden ermittelt, die ueber die reine Wiedergabe oder Aggregation einzelner Datenreihen hinausgehen; es wird ein Modell entwickelt.
- **Valide, neuartig, potentiell nuetzlich, leicht verstaendlich:** Beziehen sich auf die Guete der ermittelten Zusammenhaenge.
- **Muster:** Regelmaessigkeiten oder Auffaelligkeiten in den Daten, die durch ein Modell dargestellt werden koennen und eine Hypothese ueber die Domaene bilden.

### Definition: Data Mining (DM)

"Data Mining is the process of extracting hitherto unknown and potentially useful patterns, trends, anomalies and rules from stored historical data for business promotion, decision making and classification." (Chattamvelli, 2009, S. 13)

DM ist ein Schritt im uebergreifenden KDD-Prozess und umfasst im Wesentlichen die Mustersuche und -erkennung innerhalb vorbereiteter Daten. Die Begriffe KDD und DM werden im Skript bewusst getrennt gehalten.

### Abgrenzung KDD vs. DM

- **Fayyad et al. (1996):** DM beschreibt Methoden und Instrumente, die in einem Teil des uebergreifenden KDD-Prozesses eingesetzt werden. KDD ist die hoehere, abstraktere Ebene.
- **Wiedmann et al. (2001):** "KDD und DM sind im betriebswirtschaftlichen Kontext Synonyme." (Alternative Sichtweise, die im Skript abgelehnt wird.)
- Im Skript gilt: KDD = gesamter Prozess, DM = zentraler Analyseschritt innerhalb des KDD.

---

## Modelle / Frameworks / Verfahren

### Der KDD-Prozess

#### KDD-Prozess nach Fayyad et al. (1996) -- 9 Schritte

1. **Problemdefinition:** Problemstellung, Ziele und Domaene definieren
2. **Auswahl der Daten:** Relevante Daten aus der Gesamtheit auswaehlen
3. **Bereinigung und Aufbereitung:** Behandlung von Datenqualitaetsproblemen (Noise, fehlende Werte, Ausreisser)
4. **Reduktion oder Projektion:** Attribute verwerfen, verrechnen oder transformieren (z.B. Kodierung)
5. **Auswahl der Aufgabe:** Grundaufgabe waehlen (Klassifizierung, Clustering, Assoziation, Approximation)
6. **Auswahl des Algorithmus:** Geeignete DM-Methode(n) auswaehlen
7. **Data Mining:** Gezielt nach Mustern in den Daten suchen
8. **Interpretation:** Gefundene Muster evaluieren und interpretieren
9. **Verwendung:** Wissen dokumentieren, verbreiten, zur Entscheidungsfindung einsetzen

#### Drei Meta-Phasen

| Meta-Phase | Fayyad et al. (1996) | Ester & Sander (2000) | Duesing (2006) | Linoff & Berry (2011) |
|---|---|---|---|---|
| **I. Vorbereitende Schritte** | Schritte 1-4 | Fokussieren, Vorverarbeitung, Transformation | Auswahl, Aufbereitung | Problemdefinition |
| **II. Data Mining** | Schritte 5-7 | DM | Festlegung, Analyse | Transformation (Daten -> Wissen) |
| **III. Nachbereitende Schritte** | Schritte 8-9 | Evaluation | Interpretation | Handlung |

#### Einordnung in den Managementkreislauf

- KDD ist kein Selbstzweck, sondern ordnet sich den Wissenszielen des Unternehmens unter
- Der KDD-Prozess ist ein Spezialfall des Intelligence Cycle (Nonaka & Takeuchi, 1995)
- Unterstuetzende Funktion vor allem fuer Entscheidungsvorbereitung und Wirkungsanalyse
- Managementkreislauf: Entscheidungsproblem -> Entscheidungsvorbereitung -> Entscheidung -> Wirkungsanalyse (zyklisch)
- KDD steht in Wechselwirkung mit der Strategieebene und der IKT-Ebene des Unternehmens

### Phase I: Vorbereitende Schritte

#### 3.1 Problemdefinition

**Struktur von Entscheidungsproblemen (nach Reichmann, 2011):**
Wohl-strukturiert, wenn vier Eigenschaften vorliegen:
1. Endliche, vollstaendig bekannte Menge von Handlungsalternativen
2. Konsequenzen und Ergebnisse jeder Alternative sind bekannt
3. Der Entscheider kann Ziele bezueglich der Ergebnisse formulieren
4. Alternativen koennen algorithmisch in eine Rangfolge gebracht werden

Schlecht-strukturiert = ein oder mehrere Merkmale fehlen.

**Formale Elemente:**
- **Alternativenmenge A** = {a1, a2, ..., a_NA}, jede Alternative ai ist ein Vektor von Entscheidungsvariablen
- **Zustandsmenge Z** = {z1, z2, ..., z_NZ}, beschrieben durch Umfeldvariablen (nicht beeinflussbar)
- **Ergebnismenge R** = G1 x G2 x ... x G_NG (Zielvariablen)
- **Ergebnisfunktion** rho: A x Z -> R

**Anforderungen an Ziele:**
- Inhalt muss operational sein (messbar durch Zielvariable)
- Ausmaß (begrenzt oder unbegrenzt)
- Zeitraumbezug: statisch, kinetisch oder dynamisch

**Zielbeziehungen:**
- **Indifferenz:** Realisierung eines Ziels wirkt sich nicht auf das andere aus
- **Komplementaritaet:** Erreichung eines Ziels beeinflusst das andere positiv (symmetrisch oder asymmetrisch)
- **Konkurrenz:** Realisierung eines Ziels fuehrt zur Verschlechterung des anderen

#### 3.2 Auswahl der Daten

**Zentrale Begriffe:**
- **Universum (U):** Betrachteter Realweltausschnitt (endliche, geschlossene Menge)
- **Konzept (X):** Uneindeutiges und potentiell fehlerhaftes Abbild von U; der fuer KDD relevante Datenbestand
- **Instanz (xi):** Einzelne Nachricht/Zeile in X, charakterisiert durch Attribute
- **Attribut (q):** Spalte in X mit Wertebereich Vi
- **Featurevektor:** Vektor der Attributwerte einer Instanz

**Informationssystem (IS):**
- Beschreibt den Zusammenhang zwischen Objekten in U und Nachrichten in X
- **Vollkommenes IS:** Jedem Objekt wird genau eine Nachricht zugeordnet
- **Unvollkommenes IS:** Zuordnung ist nicht eindeutig

**Problematik der Datenversorgung:**
- Technische Probleme (Anforderungen der DM-Methoden nicht erfuellt)
- Organisatorische Probleme (fehlende Zugriffsrechte)
- Rechtliche Einschraenkungen (Datenschutz)

**Datenreduktion:** Durch Aggregation (z.B. Monatsumsaetze zu Jahresumsatz) oder Stichproben.

#### 3.3 Bereinigung und Aufbereitung der Daten

**Drei Modelle der Datengenerierung (nach Fonseca & Fieller, 2006):**
1. **Ideales Modell:** Instanzen waeren eine unabhaengige, identisch verteilte Stichprobe von U
2. **Tatsaechliches Modell:** Beeinflusst durch die Sammlung der Daten im IS
3. **Angenommenes Modell:** Das Modell, das durch DM-Verfahren gebildet wird

**Drei Fehlerklassen (nach Mueller & Freytag, 2003):**

| Fehlerart | semantisch | syntaktisch | coverage |
|---|---|---|---|
| Verschmutzungen | x | | |
| Noisy Data | x | | |
| Unzulaessige Werte | | x | |
| Fehlende Werte | | | x |
| Unvollstaendige Werte | | | x |
| Redundanz | x | | |
| Unregelmaessigkeiten | | x | |

- **Semantische Fehler:** Daten bilden das Universum inhaltlich nicht korrekt ab (z.B. Falscheingabe)
- **Syntaktische Fehler:** Daten weichen strukturell vom Datenmodell ab (z.B. "m" statt 0 fuer maennlich)
- **Coverage-Fehler:** Abgebildeter Realitaetsausschnitt kleiner als angenommen (z.B. fehlende Werte)

**Fehlerarten im Detail:**
- **Verschmutzung:** Abweichung von der Realitaet, obwohl das korrekte Datum vorlag (z.B. Tippfehler)
- **Noisy Data:** Drei Arten: (1) Instanzen, die nicht zum Universum gehoeren, (2) Attribute ohne Aufschluss, (3) falsch beobachtete Attributwerte
- **Gauss'scher Noise:** Nachrichten folgen Normalverteilung mit tatsaechlichem Objekt als Mittelwert und konstanter Standardabweichung
- **Unzulaessige Werte:** Syntaktisch im Datenmodell nicht zulassig (automatisch erkennbar durch Konsistenzpruefungen)
- **Fehlende Werte (Nullwerte):** Behandlung: wahren Wert nachtraeglich finden, Instanzen ignorieren, oder Ersatzwert bestimmen
- **Redundanz:** Gleiche Daten in unterschiedlichen Datenbanken
- **Unregelmaessigkeit:** Nicht-einheitliche Verwendung von Attributeintraegen (z.B. falsche Waehrung oder Skalierung)

**Umgang mit Fehlern (drei Vorgehensweisen):**
1. **Laissez Faire:** Keine Massnahmen, wenn Aufwand > Nutzen
2. **Reaktives Vorgehen:** Fehler wird bei Entdeckung bereinigt, aber keine praeventiven Massnahmen
3. **Proaktives Vorgehen:** Fehler bereinigen + Massnahmen zur kuenftigen Vermeidung (= proaktives DQM)

**Acht Beurteilungskriterien fuer Fehler (nach Zwirner, 2008):**
Bedeutung der Daten, Anforderungsgrundlage, Natur der Fehlerursache (fachlich/technisch), Art der moeglichen Bereinigung (manuell/maschinell), Aenderungshaeufigkeit der Daten, Anzahl der Datenfehler, Massnahmen zur Vermeidung, Aufwand fuer Massnahmen.

#### 3.4 Projektion und Reduktion von Attributen

**Skalenniveaus:**

| Niveau | Eigenschaft | Beispiel |
|---|---|---|
| **Nominal** | Unterscheidbar, ueberschneidungsfrei | Waagennummer |
| **Ordinal** | Zusaetzlich: Rangfolge | Beliebtheit (hoch/mittel/niedrig) |
| **Intervall** | Zusaetzlich: Differenzen bildbar | Datum (Verbrauchsdatum) |
| **Verhaeltnis** | Zusaetzlich: natuerlicher Nullpunkt, Verhaeltnisse | Liefermenge (Kisten) |

- Nominal + Ordinal = **qualitativ/kategorisch** (diskret)
- Intervall + Verhaeltnis = **quantitativ/numerisch** (diskret oder kontinuierlich)
- Wechsel von hoeherem auf niedrigeres Niveau immer moeglich (unter Informationsverlust)

**Kodierungsverfahren fuer kategorische Attribute:**

| Verfahren | Beschreibung | Ersatzattribute |
|---|---|---|
| **Eins-aus-N** | Fuer jeden Attributwert ein binaeres Ersatzattribut; genau eines = 1 | N |
| **n-aus-N** | Binaere Merkmale, die Attributwerte differenzieren (z.B. rot/bissfest) | < N |
| **Dummy-Kodierung (N-1)** | Wie Eins-aus-N, aber ein Referenzwert wird durch alle = 0 dargestellt | N-1 |
| **Effekt-Kodierung** | Wie Dummy, aber Referenzwert = -1 statt 0 (Erwartungswert der Ersatzattribute = 0) | N-1 |
| **Unaere Kodierung (Thermometer)** | Fuer ordinale Attribute: Vektoren werden betragmaessig groesser mit hoeherem Rang | N-1 |

**Standardisierung (z-Transformation):**
Fuer annaehernd normalverteilte Attribute, sodass mu = 0 und sigma = 1:

    v' = (v - x_quer) / s

wobei x_quer = Stichprobenmittel, s = Wurzel der Stichprobenvarianz

    x_quer = (1/NX) * Summe(xi,q)
    s^2 = (1/(NX-1)) * Summe((xi,q - x_quer)^2)

**Normalisierung (Min-Max):**
Fuer Attribute ohne Normalverteilungsannahme, Abbildung auf [0,1]:

    v' = (v - v_min) / (v_max - v_min)

**Attributauswahl:**
- **Filteransatz:** Unabhaengig vom DM-Algorithmus werden relevante Attribute ausgewaehlt (Problem: kann irrelevante Korrelationen entdecken)
- **Wrapperansatz:** DM-Algorithmus wird als Blackbox auf Teilmengen von Q angewendet und die beste Attributmenge Q' gewaehlt
- Weitere Verfahren: LDA, PCA

**Abschaetzung der Verteilung (nach Tukey, 1977):**
Fuenf Kennzahlen fuer Boxplot: Minimum, 1. Quartil (0.25-Perzentil), Median (0.5-Perzentil), 3. Quartil (0.75-Perzentil), Maximum.

### Phase II: Data Mining

#### 4.1 Vier Grundaufgaben des DM

1. **Assoziationsanalyse (Affinitaetsgruppierung):**
   - Welche Attributwerte treten haeufig gemeinsam auf?
   - Ergebnis: "wenn-dann"-Regeln (z.B. Kunde kauft Chips => Kunde kauft Cola)
   - Anwendung: Warenkorbanalyse

2. **Clusteranalyse:**
   - Heterogene Grundgesamtheit in homogene Gruppen (Cluster) unterteilen
   - Cluster sind vorab nicht definiert
   - Unueberwachtes Lernen

3. **Klassifizierung:**
   - Zuordnungsvorschrift finden, die Instanzen aufgrund ihrer Attributwerte Klassen zuordnet
   - Klassen muessen vorab bekannt sein (diskret, endlich)
   - Ueberwachtes Lernen
   - Q = Qf (Features) vereinigt Qg (Zielattribut/Target)
   - Binaere Klassifizierung: |Vqg| = 2

4. **Approximation (Vorhersage/Regression):**
   - Verallgemeinerung der Klassifizierung auf unendlich viele, oft kontinuierliche Klassen
   - Funktionalen Zusammenhang h: X -> Y approximieren
   - Anwendung: Regressionsanalyse

**Abgrenzung Clusteranalyse vs. Klassifizierung:**
- Clusteranalyse: Daten und Zuordnungsvorschrift ("moeglichst homogen") bekannt, aber Anzahl/Semantik der Cluster und tatsaechliche Zuordnung unbekannt
- Klassifizierung: Klassen und tatsaechliche Zuordnung (fuer Trainingsdaten) bekannt, Zuordnungsvorschrift unbekannt

#### 4.2 Auswahl des Algorithmus

**Modellbildung und Training:**
- DM-Algorithmen erzeugen aus historischen Daten ein angenommenes Modell h
- Modellklasse H wird festgelegt, dann wird das beste h in H gesucht (mit Modellparameter theta)
- Automatisiertes Schliessen von Daten auf Modelle = **Training**

**Trainings- und Testdaten:**
- X wird aufgeteilt in Trainingsdaten (XTr) und Testdaten
- Aufteilung muss **vor** der Algorithmusauswahl erfolgen
- Testdaten duerfen erst zur Evaluation des endgueltig gewaehlten Algorithmus verwendet werden

**Ueberwachtes vs. unueberwachtes Lernen:**
- **Ueberwachtes Lernen:** Zielgroesse in Trainingsdaten bekannt (Klassifizierung, Approximation)
- **Unueberwachtes Lernen:** Strukturen vorab nicht bekannt (Clusteranalyse)

**Generalisierung:**
- Faehigkeit, aus bekannten Daten Modelle fuer unbekannte Daten zu erzeugen
- **Overfitting:** Eigenheiten der Trainingsdaten werden gelernt, die sich nicht generalisieren lassen

**Validierung im Training:**
- **Validierungsdaten:** Abgetrennter Teil der Trainingsdaten zur Validierung
- **Kreuzvalidierung (k-fold):** Trainingsdaten in k gleich grosse Teile teilen; jeweils einen Teil zum Testen, Rest zum Trainieren; Ergebnisse mitteln

**Occam's Razor:**
Bei gleicher Erklaerungskraft ist das einfachere Modell zu bevorzugen. Praktisch geleitet durch Laufzeitkomplexitaet und Interpretierbarkeit.

**No Free Lunch Theorem (Wolpert, 1996):**
- Es gibt keinen allgemein besten ML-Algorithmus
- Es gibt kein allgemeines Verfahren zur Auswahl von ML-Algorithmen
- Es gibt keinen festen Zusammenhang zwischen Trainings- und Testperformance
- Aus guter Trainingsperformance eines einfachen Modells folgt nicht automatisch gute Testperformance
- **Konsequenz:** Annahmen ueber die Daten und deren Struktur sind immer noetig und koennen nicht aus den Daten selbst gewonnen werden

**Eager Learning vs. Lazy Learning vs. Ensemble Learning:**
- **Eager Learning:** Sofort Modell aus Trainingsdaten erstellen (z.B. Entscheidungsbaeume, Naive Bayes)
- **Lazy Learning:** Generalisierung aufschieben bis neue Instanzen klassifiziert werden muessen; instanzbasiert (z.B. k-NN)
- **Ensemble Learning:** Kombination vieler einfacher Modelle mit instanzbasierter Gewichtung (z.B. AdaBoost)

#### 4.3 Entscheidungsbaumverfahren

**Zentrale Idee:**
- Partitionierung des Featureraums X = B1 vereinigt ... vereinigt Bc
- Klasse wird bestimmt durch h(x) = Ci genau dann wenn x in Bi liegt
- EB besteht aus Knoten (Wurzel, innere Knoten, Blaetter/Endknoten) und Kanten

**Generischer TDIDT-Algorithmus (Top-Down Induction of Decision Trees):**
- Beginne an der Wurzel mit ganz X
- An jedem inneren Knoten: Waehle das beste Attribut zur Aufspaltung (mittels Entropiemass)
- Spalte X weiter auf, bis Abbruchkriterium erreicht
- Rekursive Funktion SplitTree

**Spezialisierungen von TDIDT (vier Bestandteile):**
1. **Attributauswahl (Gain):** Mittels Entropiemass (Purity, Gini-Index, InformationGain)
2. **Aufspaltung (SplitAttribute):** Binaer oder mehrfach
3. **Abbruchkriterium (StoppingCriterion):** z.B. Impurity = 0 oder Unterschreitung einer Schwelle (early Stopping)
4. **Post-Pruning (PruneTree):** Zurueckschneiden des Baums zur Verbesserung der Generalisierung

**Purity und Impurity:**
- **Purity:** Maximaler Anteil einer Klasse an den Instanzen einer Partition (max. 1, min. 1/c)
- **Impurity:** 1 - Purity (max. (c-1)/c, min. 0)
- **PurityGain:** Impurity des Ausgangsknotens minus gewichtete Impurity der Kindknoten

**Reiner vs. unreiner Knoten:**
- **Reiner Knoten:** Alle Trainingsinstanzen gehoeren zur selben Klasse
- **Unreiner Knoten:** Noch verschiedene Klassen vorhanden; Zuordnung zur Mehrheitsklasse

**CART (Classification and Regression Trees, Breiman et al., 1984):**
- Verwendet den **Gini-Index** zur Attributauswahl
- **Alle Aufteilungen sind binaer**
- Cost-Complexity Pruning
- Kein early Stopping (Stopp bei Impurity = 0)
- **Gini-Index:** Gini(t) = 1 - Summe(p(Ci|t)^2) fuer alle Klassen Ci
  - p(Ci|t) = Anteil der Klasse Ci an den Trainingsinstanzen in Knoten t
  - Minimum 0 (reiner Knoten), Maximum (c-1)/c
- **GiniGain:** Gini des Elternknotens - gewichteter Gini der Kindknoten
- Binaere Aufspaltung: SplitAttributeBinary gibt alle moeglichen binaeren Splits zurueck

**C4.5 (Quinlan, 1993):**
- Basiert auf **informationstheoretischer Entropie** statt Gini-Index
- **Entropie:** H(t) = -Summe(p(Ci|t) * log2(p(Ci|t)))
- **InformationGain:** Entropie des Elternknotens - gewichtete Entropie der Kindknoten
- InformationGain bevorzugt Attribute mit vielen Werten
- Deshalb besser: **GainRatio** = InformationGain / SplitInfo (normalisiert)
- Aufspaltung: binaer fuer quantitative, alle moeglichen Werte fuer qualitative Attribute
- Early Stopping: wenn Anzahl der Trainingsinstanzen unter Schwelle faellt
- Error-Based Pruning

#### 4.4 Regressionsanalyse

**Zentrale Idee:**
Modellierung als Funktion h: X -> Y (nicht als Entscheidungsbaum)

**Lineare Regression:**

    xi,qg = h(xi,Qf) = theta0 + Summe(theta_q * xi,q) + epsilon_i

- xi,qg = Regressand (abhaengige Variable)
- xi,q = Regressor (unabhaengige Variable)
- theta = Koeffizientenvektor (Modellparameter)
- epsilon_i = Residuum (Abweichung)

**Methode der kleinsten Quadrate:**

    Summe(epsilon_i^2) -> min

Fuer Einfachregression (ein Regressor):

    theta0 = x_quer_qg - theta1 * x_quer_qf
    theta1 = Cov(xi,qf, xi,qg) / Var(xi,qf)

Multivariate Regression: Verallgemeinerung auf mehrere Regressoren (erfordert Matrixinversion).

**Logistische Regression:**
- Fuer Zweiklassenfall (Y = {-1, +1})
- Anforderungen: h(x) in [0,1], h(x) fuer Klasse 1 + h(x) fuer Klasse -1 = 1
- Logistische Funktion: h(x) = 1 / (1 + e^(-theta0 - theta1*x))
- Parameter theta wird mit Maximum-Likelihood-Ansatz geschaetzt (nicht mit kleinsten Quadraten)

#### 4.5 Clusteranalyse

**Zentrale Idee:**
Instanzen nach objektiv nachvollziehbaren Kriterien gruppieren, ohne dass die Gruppierung vorab bekannt waere (unueberwachtes Verfahren).

**Distanzfunktionen (fuer metrischen Featureraum):**
Drei Eigenschaften: (1) dist(x,y) >= 0, (2) dist(x,y) = dist(y,x), (3) Dreiecksungleichung

- **Euklidische Distanz:** dist(x,y) = sqrt(Summe((xi - yi)^2))
- **Manhattan-Distanz:** dist(x,y) = Summe(|xi - yi|)
- Bei qualitativen Attributen: Jaccard-Koeffizient oder M-Koeffizient

**Distanzmatrix D:** Matrix aller paarweisen Distanzen; wegen Symmetrie reicht Dreiecksmatrix.

**Anforderungen an eine Partitionierung:**
1. Jede Partition enthaelt mindestens eine Instanz
2. Die Partitionierung ist disjunkt
3. Paarweise Distanz innerhalb der Cluster -> min
4. Paarweise Distanz zwischen Clustern -> max

**Clusteringverfahren-Typen:**
- **Partitionierende Verfahren:** Initiale Partitionierung, dann iterativ Instanzen verschieben
- **Dichtebasierte Verfahren:** Spezialfall, basiert auf Dichtefunktion statt Distanz
- **Hierarchische Verfahren:** Erzeugen eine Hierarchie der Instanzen

**Hierarchisch-agglomeratives Clustering:**
1. Jede Instanz = ein Cluster
2. Distanzmatrix berechnen
3. Zwei Cluster mit geringster Distanz finden
4. Diese zusammenfassen
5. Wiederholen bis gewuenschte Clusteranzahl oder nur noch ein Cluster

**Distanz zwischen Clustern (Linkage-Verfahren):**

| Verfahren | Prinzip |
|---|---|
| **Single-Linkage** | Minimale paarweise Entfernung |
| **Complete-Linkage** | Maximale paarweise Entfernung |
| **Average-Linkage** | Mittlere paarweise Entfernung |
| **Centroid** | Abstand der Mittelpunkte (Zentroiden) |
| **Ward** | Minimiert Varianz innerhalb des neuen Clusters (beste Ergebnisse, hoechste Anforderungen) |

**Dendrogramm:** Graphische Darstellung der Clusterhierarchie als Baumstruktur; Kantenlange proportional zur Distanz.

**Elbow-Kriterium:** Sprunghafte Zunahme der Distanz bei der Zusammenfassung deutet auf die "natuerliche" Clusteranzahl hin.

**Varianzminimierendes Partitionierungsverfahren:**
- Jeder Cluster wird durch seinen Zentroid (Mittelwertvektor) repraesentiert
- **Zentroid:** mu_Ci = (1/|Ci|) * Summe(x) fuer alle x in Ci
- **Varianz innerhalb eines Clusters:** Summe(dist(x, mu_Ci)^2) fuer alle x in Ci
- **Stabile Partitionierung:** Jede Instanz ist dem Cluster zugeordnet, dessen Zentroid am naechsten ist

**k-means Algorithmus:**
1. k (Anzahl Cluster) als Parameter vorgeben
2. Initiale Zentroiden (z.B. erste k Instanzen)
3. Jede Instanz dem naechsten Zentroiden zuordnen
4. Zentroiden neu berechnen
5. Wiederholen bis Partitionierung stabil
- Findet lokales Minimum (abhaengig von Initialisierung)
- Sensitiv fuer Reihenfolge der Trainingsinstanzen
- Kann nur sphaerische Cluster entdecken

#### 4.6 Apriori-Algorithmus

**Zielsetzung:** Erkennung von "wenn-dann"-Regeln (Assoziationsregeln) in Transaktionsdaten.

**Notation:**
- Jedes Item entspricht einem Attribut q mit Vq = {0, 1}
- **Itemset:** Untermenge von Q
- **Regel:** Ih -> Ic (Ih = Praemisse/Bedingung, Ic = Konsequenz/Konklusion)
- Instanz xi erfuellt Regel Ih -> Ic wenn Ih vereinigt Ic Teilmenge von Q+(xi)

**Support:**

    support(Ih -> Ic) = |{xi in XTr : Ih vereinigt Ic Teilmenge Q+(xi)}| / |XTr|

Anteil der Instanzen, die sowohl Praemisse als auch Konsequenz enthalten.

**Konfidenz:**

    confidence(Ih -> Ic) = support(Ih -> Ic) / support(Ih)

Anteil der Instanzen mit der Praemisse, die auch die Konsequenz enthalten. Achtung: confidence(Ih -> Ic) != confidence(Ic -> Ih)

**Parameter:**
- **Mindestsupport:** Ab welchem Supportwert Regelkandidaten beruecksichtigt werden
- **Mindestkonfidenz:** Ab welchem Konfidenzwert Regeln in die Ergebnismenge aufgenommen werden

**Apriori-Prinzip:**
- Wenn I ein haeufiges Itemset ist, dann ist auch jede Untermenge I' von I haeufig
- Umkehrung gilt NICHT
- Sukzessive Generierung: Itemsets der Groesse k+1 aus haeufigen Itemsets der Groesse k

**Algorithmus:**
1. Bestimme haeufige 1-Itemsets (I1) mittels Mindestsupport
2. Generiere Kandidaten der Groesse k+1 durch Vereinigung von Paaren aus Ik, die sich in genau einem Element unterscheiden
3. Pruefe Kandidaten auf Mindestsupport
4. Leite Regeln ab und pruefe auf Mindestkonfidenz

#### 4.7 Kuenstliche Neuronale Netze (KNN)

**Separierende Hyperebenen:**
- Hyperebene h: Summe(wj * xj) + w0 = 0 (Ebenengleichung mit Normalenvektor w)
- Linear separierbar: Es existiert eine Hyperebene, die alle positiven von allen negativen Instanzen trennt

**Perceptron (idealisiertes Neuron):**
- Eingaenge (Dendriten), Signalverarbeitung (Zellkoerper), Ausgang (Axon)
- Summiert gewichtete Eingangssignale: Summe(wj * xi,j)
- "Feuert" (+1) wenn Summe > 0, sonst -1
- Nachbildung der separierenden Hyperebene

**Perceptron-Algorithmus:**
1. Starte mit zufaelligem Gewichtsvektor w
2. Wenn eine Instanz fehlklassifiziert wird: Passe Gewichte an
3. Richtung der Anpassung: aus der bekannten Klasse
4. Groesse: Multiplikation mit Lernrate eta
5. Funktioniert nur fuer linear separierbare Daten

**Mehrschichtige Feedforward-Netzwerke:**
- Eingabeschicht -> Verborgene Schicht(en) -> Ausgabeschicht
- Verbindungen nur zwischen benachbarten Schichten (kreisfrei)
- Statt Perceptron: differenzierbare Sigmoidfunktion (z.B. logistische Funktion)
- Koennen mit 1-2 verborgenen Schichten im Prinzip jede Funktion approximieren

**Backpropagation-Algorithmus:**
1. Eingabe vorwaerts durch das Netzwerk propagieren
2. Fehler an der Ausgabeschicht messen
3. Fehler rueckwaerts propagieren und Gewichte anpassen

**Limitationen:** Anzahl benoetigter Neurone unbekannt; Laufzeit waechst schnell; gelernte Gewichte oft nicht interpretierbar (Blackbox).

#### 4.8 Weitere Klassifizierungsverfahren

**Bayes-Klassifikator:**
- Bester moeglicher Klassifikator: maximiert P(xi,qg = C | xi,Qf) (a-posteriori-Wahrscheinlichkeit)
- Basiert auf dem Satz von Bayes

**Naive Bayes:**
- Vereinfacht die Schaetzung durch die Annahme, dass Attribute gegeben eine Klasse voneinander unabhaengig sind
- P(xi,Qf | C) = Produkt(P(xi,q | C)) fuer alle q in Qf
- Fuer qualitative Attribute: Anteil von Wert v an der Klasse
- Fuer quantitative Attribute: Normalverteilung unterstellt mit geschaetzten mu und sigma
- Theoretisch naiv, aber empirisch oft gute Ergebnisse

**k-Nearest Neighbour (k-NN):**
- Lazy Learner: Baut kein Modell auf
- Weise einer Instanz die Klasse zu, die unter ihren k naechsten Nachbarn in XTr die Mehrheit hat
- Nachbarschaft ueber Distanzmass bestimmt
- Herausforderung: Effiziente Speicherung fuer schnelle Nachbarschaftssuche

### Phase III: Nachbereitende Schritte

#### 5.1 Evaluation

**Konfusionsmatrix (fuer binaere Klassifizierung Y = {-1, +1}):**

| | Vorhersage: +1 | Vorhersage: -1 |
|---|---|---|
| **Tatsaechlich: +1** | Richtig Positiv (TP) | Falsch Negativ (FN) |
| **Tatsaechlich: -1** | Falsch Positiv (FP) | Richtig Negativ (TN) |

**Kennzahlen:**
- **Korrektklassifikationsrate (Accuracy):** (TP + TN) / (TP + TN + FP + FN)
- **Richtigpositivrate (Recall/Sensitivitaet):** TP / (TP + FN)
- **Falschpositivrate:** FP / (FP + TN)
- **Precision:** TP / (TP + FP)

Zum Vergleich von Modellen: Recall und Falschpositivrate oder Recall und Precision gemeinsam in einem Diagramm abtragen.

**Kriterien zur Beurteilung von DM-Ergebnissen:**
1. **Validitaet:** Wie gut bildet das Modell die Realitaet ab? Generalisierung auf unbekannte Instanzen (nicht nur Anpassung an bekannte Daten)
2. **Neuigkeitsgehalt:** Triviale oder bereits bekannte Regeln sind nicht nuetzlich
3. **Kompaktheit/Verstaendlichkeit:** Ergebnisse muessen dem Entscheider verstaendlich praesentiert werden
4. **Nuetzlichkeit:** Aus Ergebnissen muessen Handlungsempfehlungen ableitbar sein

#### 5.2 Interpretation und Verwendung

- Ergebnisse in den Kontext des Unternehmens und des Entscheidungsproblems einordnen
- Grenzen des DM kennen: Theoretische Grenzen (No Free Lunch), Bedingungen der Algorithmen (Skalierung, Verteilung)
- Jedes DM-Ergebnis ist zunaechst eine Aussage ueber die Daten, nicht ueber die Realitaet
- Vom Ergebnis zur Handlung: Entscheider muss Bezug zwischen Modell und Handlungsalternativen herstellen

---

## Uebersicht DM-Algorithmen

| Verfahrensgruppe | Beispiele | Grundaufgabe | Lernen |
|---|---|---|---|
| Regressionsverfahren | Lineare Regression, Logistische Regression | Approximation, Klassifizierung | Ueberwacht |
| Projektionsverfahren | PCA, LDA | Dimensionsreduktion | PCA: unueberwacht, LDA: ueberwacht |
| Entscheidungsbaumverfahren | CART, C4.5 (ID3) | Klassifizierung, Approximation | Ueberwacht |
| Clusteringverfahren | k-means, Hierarchisch (aggl./div.) | Clusteranalyse | Unueberwacht |
| Soft-Computing | SVM, ES, PageRank | Verschiedene | Verschiedene |
| Rule Induction | Apriori-Algorithmus | Assoziationsanalyse | - |
| Eager Learning | Naive Bayes, Entscheidungsbaeume | Klassifizierung | Ueberwacht |
| Lazy Learning | k-NN | Klassifizierung | Ueberwacht |
| Ensemble Learning | AdaBoost | Klassifizierung | Ueberwacht |
| Neuronale Netze | Perceptron, Feedforward-KNN | Klassifizierung, Approximation | Ueberwacht |

---

## Definitionstabelle

| Begriff | Definition |
|---------|-----------|
| KDD | "Knowledge Discovery in Databases is the non-trivial process of identifying valid, novel, potentially useful, and ultimately understandable patterns in data." (Fayyad et al., 1996) |
| Data Mining | "Data Mining is the process of extracting hitherto unknown and potentially useful patterns, trends, anomalies and rules from stored historical data for business promotion, decision making and classification." (Chattamvelli, 2009) |
| Konzept (X) | Der fuer das betrachtete KDD-Problem relevante Datenbestand; uneindeutiges, potentiell fehlerhaftes Abbild des Universums U |
| Universum (U) | Betrachteter Realweltausschnitt; endliche, geschlossene Menge (auch: Miniwelt, Universe of Discourse) |
| Instanz (xi) | Eine einzelne Nachricht/Zeile im Konzept X, charakterisiert durch Attribute |
| Attribut (q) | Eine Eigenschaft/Spalte im Konzept mit definiertem Wertebereich Vi |
| Featurevektor | Vektor der Attributwerte einer Instanz (wenn Vi Teilmenge von R) |
| Skalenniveau | Vier Stufen: nominal, ordinal, intervall, verhaeltnis |
| Trainingsdaten (XTr) | Teil von X, der zum Training des Modells verwendet wird |
| Testdaten | Teil von X, der zur Evaluation des endgueltig gewaehlten Modells verwendet wird |
| Validierungsdaten | Abgetrennter Teil der Trainingsdaten zur Validierung waehrend der Algorithmusauswahl |
| Generalisierung | Faehigkeit, aus bekannten Daten Modelle fuer unbekannte Daten zu erzeugen |
| Overfitting | Eigenheiten der Trainingsdaten werden gelernt, die sich nicht generalisieren lassen |
| Kreuzvalidierung (k-fold) | Trainingsdaten in k Teile teilen; jeweils einen Teil testen, Rest trainieren; Ergebnisse mitteln |
| Gini-Index | Gini(t) = 1 - Summe(p(Ci|t)^2); Mass fuer die Unreinheit eines Knotens |
| Information Gain | Entropie des Elternknotens minus gewichtete Entropie der Kindknoten |
| Gain Ratio | InformationGain / SplitInfo; vermeidet Bevorzugung von Attributen mit vielen Werten |
| Purity / Impurity | Reinheit = max. Anteil einer Klasse; Unreinheit = 1 - Purity |
| Pruning | Zurueckschneiden eines Entscheidungsbaums zur Verbesserung der Generalisierung |
| Early Stopping | Abbruch des Baumwachstums an unreinen Knoten zur Vermeidung von Overfitting |
| Support | Anteil der Instanzen, die sowohl Praemisse als auch Konsequenz einer Regel enthalten |
| Konfidenz | Anteil der Instanzen mit der Praemisse, die auch die Konsequenz enthalten |
| Konfusionsmatrix | Tabelle mit vier Feldern (TP, FP, TN, FN) zur Bewertung von Klassifikationsmodellen |
| Recall (Sensitivitaet) | TP / (TP + FN); Anteil korrekt erkannter positiver Faelle |
| Precision | TP / (TP + FP); Anteil tatsaechlich positiver unter den als positiv klassifizierten |
| TDIDT | Top-Down Induction of Decision Trees; generischer Algorithmus fuer Entscheidungsbaeume |
| CART | Classification and Regression Trees; binaere Splits mit Gini-Index |
| C4.5 | Entscheidungsbaumverfahren mit Entropie/InformationGain und GainRatio |
| Perceptron | Idealisiertes Neuron; Nachbildung einer separierenden Hyperebene |
| Backpropagation | Lernalgorithmus fuer mehrschichtige KNN; Fehler wird rueckwaerts propagiert |
| k-means | Partitionierendes Clusteringverfahren; minimiert Varianz innerhalb der Cluster |
| Dendrogramm | Baumdarstellung einer hierarchischen Clusterhierarchie |
| Apriori-Prinzip | Wenn ein Itemset haeufig ist, sind auch alle seine Untermengen haeufig |
| No Free Lunch Theorem | Es gibt keinen allgemein besten ML-Algorithmus (Wolpert, 1996) |
| Occam's Razor | Bei gleicher Erklaerungskraft ist das einfachere Modell zu bevorzugen |
| Naive Bayes | Klassifikator mit der (naiven) Annahme bedingter Unabhaengigkeit der Attribute gegeben die Klasse |
| k-NN (k-Nearest Neighbour) | Lazy Learner; klassifiziert nach Mehrheit unter den k naechsten Nachbarn |
| RFM-Analyse | Kundensegmentierung nach recency, frequency, monetary |
| Datenbereinigung | Nachtraegliche Korrektur bereits entstandener Fehler in der Datenbasis |
| Semantische Fehler | Daten bilden Universum inhaltlich nicht korrekt ab |
| Syntaktische Fehler | Daten weichen strukturell vom Datenmodell ab |
| Coverage-Fehler | Abgebildeter Realitaetsausschnitt kleiner als angenommen |
| Standardisierung (z-Transformation) | Attributwerte so transformieren, dass mu = 0 und sigma = 1 |
| Normalisierung (Min-Max) | Attributwerte auf das Intervall [0,1] abbilden |

---

## Querverweise

- Siehe auch: wissen/01_grundlagen_bi.md -- BI-Definition, Entscheidungsprozesse, handlungsorientierte Modellierung, Intelligence Cycle, ganzheitliches Unternehmensmodell, ERM
- Einheit 3: Data Warehouse (DWH), OLAP, Datenqualitaetsmanagement (DQM) -- unterstuetzt die Schritte 2 und 3 des KDD-Prozesses
- Einheit 4: Neue Entwicklungen und Anwendungsbeispiele der BI

---

## Typische Pruefungsfragen

### Frage 1: Abgrenzung KDD und DM
**Frage:** Grenzen Sie die Begriffe KDD und DM voneinander ab!

**Musterantwort:** KDD umfasst den gesamten Prozess von der Definition der Problemstellung bis zur Generierung von Wissen. DM stellt lediglich einen Schritt im Rahmen des KDD-Prozesses dar -- die eigentliche Suche nach Mustern in den vorbereiteten Daten. Ohne die vorgelagerten Schritte (Problemdefinition, Datenauswahl, Datenbereinigung) waeren die DM-Ergebnisse wenig aussagekraeftig. Ebenso muessen die nachgelagerten Schritte (Interpretation, Verwendung) durchlaufen werden, damit das Unternehmen profitieren kann. DM umfasst also lediglich Analysemethoden, waehrend KDD den gesamten Rahmen liefert, in dem diese sinnvoll eingesetzt werden koennen.

### Frage 2: Einordnung des KDD-Prozesses in den Managementkreislauf
**Frage:** Erlaeutern Sie, wie sich der KDD-Prozess in den Managementkreislauf einbettet!

**Musterantwort:** Der Managementkreislauf besteht aus den Phasen Entscheidungsproblem, Entscheidungsvorbereitung, Entscheidung und Wirkungsanalyse. KDD hat eine unterstuetzende Funktion, vor allem bei der Entscheidungsvorbereitung (Informationsbeschaffung, Alternativenbewertung) und der Wirkungsanalyse (Analyse der Handlungswirkungen). Das Entscheidungsproblem definiert gleichzeitig die Wissensziele fuer KDD. Die Ergebnisse des KDD fliessen als Handlungsempfehlungen in den Entscheidungsprozess ein. Aus der Wirkungsanalyse koennen sich neue Entscheidungsprobleme ergeben -- der Kreislauf schliesst sich. KDD ist somit als Spezialfall des Intelligence Cycle zu verstehen.

### Frage 3: Fehlerklassen und Umgang mit Fehlern
**Frage:** Bei einer Ueberweisung gibt ein Kunde noch Kontonummer und Bankleitzahl statt der IBAN an. Um welche Fehlerart handelt es sich? Welches Vorgehen wuerden Sie der Bank empfehlen?

**Musterantwort:** Es handelt sich um einen syntaktischen Fehler -- die Werte sind inhaltlich korrekt, entsprechen aber nicht dem erwarteten Datenmodell-Format. Die Bank hat drei Moeglichkeiten: (1) Laissez Faire: nichts unternehmen -- hier ungeeignet, da die Ueberweisung sonst nicht durchgefuehrt wird. (2) Reaktives Vorgehen: Die korrekte IBAN manuell aus Kontonummer und BLZ konstruieren -- bei haeufigem Auftreten dauerhaft teuer. (3) Proaktives Vorgehen: Fehler bereinigen und Massnahmen zur Vermeidung einfuehren (z.B. automatische Umwandlung oder Kundenbenachrichtigung). Empfehlung: proaktives Vorgehen, da der Fehler waehrend der Umstellungsphase haeufig auftritt.

### Frage 4: Vergleich CART und C4.5
**Frage:** Vergleichen Sie die Entscheidungsbaumverfahren CART und C4.5 hinsichtlich Attributauswahl und Aufspaltung!

**Musterantwort:** CART verwendet den Gini-Index als Mass fuer die Unreinheit (Gini(t) = 1 - Summe(p(Ci|t)^2)), waehrend C4.5 auf der informationstheoretischen Entropie basiert (H(t) = -Summe(p(Ci|t) * log2(p(Ci|t)))). Bei C4.5 wird statt des InformationGain bevorzugt die GainRatio verwendet, um die Bevorzugung von Attributen mit vielen moeglichen Werten zu vermeiden. Hinsichtlich der Aufspaltung unterscheiden sich die Verfahren: CART fuehrt ausschliesslich binaere Splits durch (fuer qualitative und quantitative Attribute), waehrend C4.5 quantitative Attribute binaer und qualitative Attribute in alle moeglichen Werte aufspaltet.

### Frage 5: Clusteranalyse -- Grundidee und Verfahren
**Frage:** Erlaeutern Sie die Grundidee der Clusteranalyse und grenzen Sie agglomeratives und divisives Clustering voneinander ab!

**Musterantwort:** Die Grundidee der Clusteranalyse ist es, Instanzen so in Gruppen (Cluster) einzuordnen, dass die Cluster in sich moeglichst homogen (geringe paarweise Distanz innerhalb) und untereinander moeglichst heterogen (grosse paarweise Distanz zwischen Clustern) sind. Es handelt sich um unueberwachtes Lernen. Agglomeratives und divisives Clustering sind beides hierarchische Verfahren. Beim agglomerativen Verfahren beginnt jede Instanz als eigenes Cluster; schrittweise werden die aehnlichsten Cluster zusammengefasst, bis nur noch ein Cluster uebrig bleibt. Beim divisiven Verfahren beginnt man mit einem Cluster, das alle Instanzen enthaelt, und teilt dieses schrittweise auf. Die Verfahren arbeiten also genau gegenlaeutig.

### Frage 6: Konfusionsmatrix und Kennzahlen
**Frage:** Erlaeutern Sie die Begriffe "falsch-positiv" und "falsch-negativ" am Beispiel der Klassifizierung von Bankkunden in "kreditwuerdig" und "nicht kreditwuerdig"!

**Musterantwort:** Die positive Klasse sei "nicht kreditwuerdig" (das kritische Merkmal). Falsch-negativ bedeutet, dass nicht-kreditwuerdige Kunden faelschlicherweise als kreditwuerdig eingestuft werden -- dies kann hohe Kosten verursachen, da der Kredit moeglicherweise nicht zurueckgezahlt wird. Falsch-positiv bedeutet, dass kreditwuerdige Kunden als nicht-kreditwuerdig eingestuft werden -- dies fuehrt zu Opportunitaetskosten (entgangenes Geschaeft), die aber vergleichsweise gering sind. Der falsch-negative Fehler hat somit deutlich gravierendere Folgen. Deshalb ist hier der Recall (Sensitivitaet = TP/(TP+FN)) besonders wichtig.

### Frage 7: Apriori-Algorithmus
**Frage:** Erklaeren Sie die Begriffe Support und Konfidenz im Kontext des Apriori-Algorithmus!

**Musterantwort:** Der Support einer Regel Ih -> Ic misst den Anteil aller Transaktionen, die sowohl alle Items der Praemisse als auch alle Items der Konsequenz enthalten. Er gibt an, wie haeufig die Regel insgesamt in den Daten vorkommt. Die Konfidenz einer Regel Ih -> Ic misst den Anteil der Transaktionen mit der Praemisse, die auch die Konsequenz enthalten. Sie gibt an, wie zuverlaessig die Regel ist. Wichtig: Die Konfidenz ist nicht symmetrisch -- confidence(Ih -> Ic) ist nicht gleich confidence(Ic -> Ih). Dem Apriori-Algorithmus werden Mindestsupport und Mindestkonfidenz als Parameter uebergeben. Das Apriori-Prinzip besagt: Wenn ein Itemset haeufig ist, sind auch alle seine Untermengen haeufig (Umkehrung gilt nicht). Dies erlaubt effizientes Pruning des Suchraums.

---

## Tags

`KDD` `Data Mining` `KDD-Prozess` `Fayyad` `Duesing` `Entscheidungsproblem` `Datenbereinigung` `Fehlerklassen` `semantisch` `syntaktisch` `coverage` `Skalenniveau` `nominal` `ordinal` `intervall` `verhaeltnis` `Kodierung` `Eins-aus-N` `Dummy` `Effekt` `unaer` `z-Transformation` `Standardisierung` `Normalisierung` `Entscheidungsbaum` `TDIDT` `CART` `C4.5` `Gini-Index` `InformationGain` `GainRatio` `Pruning` `Overfitting` `Regressionsanalyse` `lineare Regression` `logistische Regression` `Methode der kleinsten Quadrate` `Clusteranalyse` `k-means` `hierarchisch` `agglomerativ` `divisiv` `Dendrogramm` `Distanzfunktion` `Euklidisch` `Manhattan` `Single-Linkage` `Complete-Linkage` `Ward` `Apriori` `Support` `Konfidenz` `Itemset` `Warenkorbanalyse` `KNN` `Perceptron` `Backpropagation` `Naive Bayes` `k-NN` `Konfusionsmatrix` `Recall` `Precision` `Kreuzvalidierung` `No Free Lunch` `Occam Razor` `Generalisierung` `Trainings-Testdaten` `RFM-Analyse`
