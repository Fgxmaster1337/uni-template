# Berechnungsbeispiele -- Modul 32711 Business Intelligence

> Alle Beispiele vollstaendig durchgerechnet mit jedem Zwischenschritt.
> Formeln gemaess Einheit 2 (Methoden und Instrumente) und Einheit 4 (Neuere Entwicklungen).

---

## 1. Gini-Index und GiniGain (CART)

### Datensatz

10 Instanzen, 2 Klassen (Ja/Nein), 2 Attribute (Alter, Einkommen).
Szenario: Kauft ein Kunde ein Produkt?

| Nr | Alter   | Einkommen | Kauft |
|----|---------|-----------|-------|
| 1  | jung    | hoch      | Nein  |
| 2  | jung    | niedrig   | Nein  |
| 3  | jung    | niedrig   | Ja    |
| 4  | mittel  | hoch      | Ja    |
| 5  | mittel  | hoch      | Ja    |
| 6  | mittel  | niedrig   | Nein  |
| 7  | alt     | hoch      | Ja    |
| 8  | alt     | hoch      | Ja    |
| 9  | alt     | niedrig   | Ja    |
| 10 | jung    | hoch      | Nein  |

Klassenverteilung: Ja = {3,4,5,7,8,9} = 6 Instanzen, Nein = {1,2,6,10} = 4 Instanzen.

### Schritt 1: Gini-Index des Wurzelknotens

Formel: Gini(t) = 1 - Summe(p(Ci|t)^2)

    p(Ja|Wurzel) = 6/10 = 0,6
    p(Nein|Wurzel) = 4/10 = 0,4

    Gini(Wurzel) = 1 - (0,6)^2 - (0,4)^2
                 = 1 - 0,36 - 0,16
                 = 0,48

### Schritt 2: Alle moeglichen binaeren Splits bestimmen

CART fuehrt ausschliesslich binaere Splits durch. Fuer das Attribut **Alter** mit drei Werten
(jung, mittel, alt) gibt es drei moegliche binaere Aufteilungen. Fuer **Einkommen** (zwei Werte)
gibt es nur eine Aufteilung.

### Schritt 3: GiniGain fuer Attribut "Alter"

Formel: GiniGain = Gini(Elternknoten) - (|t_links|/|t|) * Gini(t_links) - (|t_rechts|/|t|) * Gini(t_rechts)

**Split A1: {jung} vs. {mittel, alt}**

Linker Knoten {jung} -- Instanzen 1, 2, 3, 10:
- Ja: 1 (Nr. 3), Nein: 3 (Nr. 1, 2, 10) --> n = 4
- Gini = 1 - (1/4)^2 - (3/4)^2 = 1 - 1/16 - 9/16 = 1 - 10/16 = 6/16 = 0,375

Rechter Knoten {mittel, alt} -- Instanzen 4, 5, 6, 7, 8, 9:
- Ja: 5 (Nr. 4, 5, 7, 8, 9), Nein: 1 (Nr. 6) --> n = 6
- Gini = 1 - (5/6)^2 - (1/6)^2 = 1 - 25/36 - 1/36 = 1 - 26/36 = 10/36 = 0,2778

GiniGain(A1) = 0,48 - (4/10) * 0,375 - (6/10) * 0,2778
             = 0,48 - 0,15 - 0,1667
             = **0,1633**

**Split A2: {mittel} vs. {jung, alt}**

Linker Knoten {mittel} -- Instanzen 4, 5, 6:
- Ja: 2 (Nr. 4, 5), Nein: 1 (Nr. 6) --> n = 3
- Gini = 1 - (2/3)^2 - (1/3)^2 = 1 - 4/9 - 1/9 = 4/9 = 0,4444

Rechter Knoten {jung, alt} -- Instanzen 1, 2, 3, 7, 8, 9, 10:
- Ja: 4 (Nr. 3, 7, 8, 9), Nein: 3 (Nr. 1, 2, 10) --> n = 7
- Gini = 1 - (4/7)^2 - (3/7)^2 = 1 - 16/49 - 9/49 = 24/49 = 0,4898

GiniGain(A2) = 0,48 - (3/10) * 0,4444 - (7/10) * 0,4898
             = 0,48 - 0,1333 - 0,3429
             = **0,0038**

**Split A3: {alt} vs. {jung, mittel}**

Linker Knoten {alt} -- Instanzen 7, 8, 9:
- Ja: 3 (Nr. 7, 8, 9), Nein: 0 --> n = 3
- Gini = 1 - (3/3)^2 - (0/3)^2 = 1 - 1 = **0** (reiner Knoten!)

Rechter Knoten {jung, mittel} -- Instanzen 1, 2, 3, 4, 5, 6, 10:
- Ja: 3 (Nr. 3, 4, 5), Nein: 4 (Nr. 1, 2, 6, 10) --> n = 7
- Gini = 1 - (3/7)^2 - (4/7)^2 = 1 - 9/49 - 16/49 = 24/49 = 0,4898

GiniGain(A3) = 0,48 - (3/10) * 0 - (7/10) * 0,4898
             = 0,48 - 0 - 0,3429
             = **0,1371**

### Schritt 4: GiniGain fuer Attribut "Einkommen"

**Split E1: {hoch} vs. {niedrig}**

Linker Knoten {hoch} -- Instanzen 1, 4, 5, 7, 8, 10:
- Ja: 4 (Nr. 4, 5, 7, 8), Nein: 2 (Nr. 1, 10) --> n = 6
- Gini = 1 - (4/6)^2 - (2/6)^2 = 1 - 16/36 - 4/36 = 16/36 = 0,4444

Rechter Knoten {niedrig} -- Instanzen 2, 3, 6, 9:
- Ja: 2 (Nr. 3, 9), Nein: 2 (Nr. 2, 6) --> n = 4
- Gini = 1 - (2/4)^2 - (2/4)^2 = 1 - 0,25 - 0,25 = 0,5

GiniGain(E1) = 0,48 - (6/10) * 0,4444 - (4/10) * 0,5
             = 0,48 - 0,2667 - 0,2
             = **0,0133**

### Schritt 5: Besten Split waehlen

| Split                        | GiniGain |
|------------------------------|----------|
| Alter: {jung} vs. {mittel, alt}   | **0,1633** |
| Alter: {alt} vs. {jung, mittel}   | 0,1371 |
| Alter: {mittel} vs. {jung, alt}   | 0,0038 |
| Einkommen: {hoch} vs. {niedrig}   | 0,0133 |

**Ergebnis:** CART waehlt den Split **{jung} vs. {mittel, alt}** mit dem hoechsten GiniGain von 0,1633.

### Pruefungshinweis:
- CART verwendet **immer binaere Splits**, auch bei Attributen mit mehr als zwei Werten. Deshalb muessen fuer "Alter" alle drei binaeren Aufteilungen geprueft werden.
- Der Gini-Index misst die Wahrscheinlichkeit einer Fehlklassifikation bei zufaelliger Zuordnung. Minimum = 0 (reiner Knoten), Maximum = (c-1)/c (bei c Klassen, hier 0,5).
- Gini = 0,48 ist nahe am Maximum 0,5 -- der Wurzelknoten ist also sehr unrein.
- Verwechslungsgefahr: GiniGain ist nicht dasselbe wie der Gini-Index! GiniGain = Verbesserung der Reinheit durch den Split.

---

## 2. Entropie, InformationGain und GainRatio (C4.5)

### Datensatz

Derselbe Datensatz wie in Beispiel 1 (10 Instanzen, Attribute Alter und Einkommen, Klasse Kauft).

### Schritt 1: Entropie des Wurzelknotens

Formel: H(t) = -Summe(p(Ci|t) * log2(p(Ci|t)))

    p(Ja|Wurzel) = 6/10 = 0,6
    p(Nein|Wurzel) = 4/10 = 0,4

    H(Wurzel) = -(0,6) * log2(0,6) - (0,4) * log2(0,4)

Zwischenrechnung der Logarithmen:
    log2(0,6) = ln(0,6) / ln(2) = -0,5108 / 0,6931 = -0,7370
    log2(0,4) = ln(0,4) / ln(2) = -0,9163 / 0,6931 = -1,3219

Einsetzen:
    H(Wurzel) = -(0,6) * (-0,7370) - (0,4) * (-1,3219)
              = 0,4422 + 0,5288
              = **0,9710 bit**

### Schritt 2: InformationGain fuer Attribut "Alter"

C4.5 spaltet qualitative Attribute in **alle moeglichen Werte** auf.
Alter hat drei Werte, also drei Kindknoten.

Formel: InformationGain = H(Elternknoten) - Summe((|t_v|/|t|) * H(t_v))

**Kindknoten "jung"** -- Instanzen 1, 2, 3, 10 (n=4):
- Ja: 1, Nein: 3
- H(jung) = -(1/4) * log2(1/4) - (3/4) * log2(3/4)
  - log2(0,25) = -2,0000
  - log2(0,75) = ln(0,75)/ln(2) = -0,2877/0,6931 = -0,4150
- H(jung) = -(0,25) * (-2,0) - (0,75) * (-0,4150)
          = 0,5 + 0,3113
          = **0,8113 bit**

**Kindknoten "mittel"** -- Instanzen 4, 5, 6 (n=3):
- Ja: 2, Nein: 1
- H(mittel) = -(2/3) * log2(2/3) - (1/3) * log2(1/3)
  - log2(2/3) = ln(2/3)/ln(2) = -0,4055/0,6931 = -0,5850
  - log2(1/3) = ln(1/3)/ln(2) = -1,0986/0,6931 = -1,5850
- H(mittel) = -(0,6667) * (-0,5850) - (0,3333) * (-1,5850)
            = 0,3900 + 0,5283
            = **0,9183 bit**

**Kindknoten "alt"** -- Instanzen 7, 8, 9 (n=3):
- Ja: 3, Nein: 0
- H(alt) = -(3/3) * log2(3/3) - (0/3) * log2(0/3)
- Konvention: 0 * log2(0) = 0 (Grenzwert)
- H(alt) = -1 * 0 - 0 = **0 bit** (reiner Knoten)

Gewichtete Entropie der Kindknoten:
    H_gewichtet(Alter) = (4/10) * 0,8113 + (3/10) * 0,9183 + (3/10) * 0
                       = 0,3245 + 0,2755 + 0
                       = 0,6000

    InformationGain(Alter) = 0,9710 - 0,6000
                           = **0,3710 bit**

### Schritt 3: InformationGain fuer Attribut "Einkommen"

Einkommen hat zwei Werte (binaere Aufspaltung).

**Kindknoten "hoch"** -- Instanzen 1, 4, 5, 7, 8, 10 (n=6):
- Ja: 4, Nein: 2
- H(hoch) = -(4/6) * log2(4/6) - (2/6) * log2(2/6)
  - log2(4/6) = log2(0,6667) = -0,5850
  - log2(2/6) = log2(0,3333) = -1,5850
- H(hoch) = -(0,6667) * (-0,5850) - (0,3333) * (-1,5850)
          = 0,3900 + 0,5283
          = **0,9183 bit**

**Kindknoten "niedrig"** -- Instanzen 2, 3, 6, 9 (n=4):
- Ja: 2, Nein: 2
- H(niedrig) = -(2/4) * log2(2/4) - (2/4) * log2(2/4)
             = -(0,5) * (-1,0) - (0,5) * (-1,0)
             = 0,5 + 0,5
             = **1,0 bit** (maximale Entropie bei 2 Klassen)

Gewichtete Entropie:
    H_gewichtet(Einkommen) = (6/10) * 0,9183 + (4/10) * 1,0
                           = 0,5510 + 0,4
                           = 0,9510

    InformationGain(Einkommen) = 0,9710 - 0,9510
                               = **0,0200 bit**

### Schritt 4: SplitInfo berechnen

Formel: SplitInfo(q) = -Summe((|t_v|/|t|) * log2(|t_v|/|t|))

SplitInfo misst, wie gleichmaessig ein Attribut die Instanzen auf die Kindknoten verteilt.

**SplitInfo(Alter):**

    SplitInfo(Alter) = -(4/10)*log2(4/10) - (3/10)*log2(3/10) - (3/10)*log2(3/10)

Zwischenrechnung:
    log2(0,4) = -1,3219
    log2(0,3) = ln(0,3)/ln(2) = -1,2040/0,6931 = -1,7370

    SplitInfo(Alter) = -(0,4) * (-1,3219) - (0,3) * (-1,7370) - (0,3) * (-1,7370)
                     = 0,5288 + 0,5211 + 0,5211
                     = **1,5710**

**SplitInfo(Einkommen):**

    SplitInfo(Einkommen) = -(6/10)*log2(6/10) - (4/10)*log2(4/10)
                         = -(0,6) * (-0,7370) - (0,4) * (-1,3219)
                         = 0,4422 + 0,5288
                         = **0,9710**

### Schritt 5: GainRatio berechnen

Formel: GainRatio(q) = InformationGain(q) / SplitInfo(q)

    GainRatio(Alter) = 0,3710 / 1,5710 = **0,2362**

    GainRatio(Einkommen) = 0,0200 / 0,9710 = **0,0206**

### Schritt 6: Ergebnis und Vergleich mit CART

| Attribut   | GiniGain (CART, bester Split) | InformationGain (C4.5) | GainRatio (C4.5) |
|------------|-------------------------------|------------------------|------------------|
| Alter      | 0,1633                        | 0,3710                 | **0,2362**       |
| Einkommen  | 0,0133                        | 0,0200                 | 0,0206           |

**Ergebnis:** Beide Verfahren waehlen **Alter** als bestes Attribut fuer den ersten Split.

Unterschiede:
- CART teilt binaer auf ({jung} vs. {mittel, alt}), C4.5 erzeugt drei Kindknoten (jung, mittel, alt)
- C4.5 erzeugt sofort einen reinen Knoten fuer "alt" (H = 0)
- GainRatio normalisiert den InformationGain, um Attribute mit vielen Werten nicht zu bevorzugen

### Pruefungshinweis:
- Entropie und Gini sind verschiedene Unreinheitsmasse, aber liefern oft das gleiche Attribut.
- InformationGain bevorzugt Attribute mit vielen Werten (z.B. Kundennummer mit 10 verschiedenen Werten haette maximalen InformationGain). Deshalb normalisiert C4.5 mit SplitInfo zur **GainRatio**.
- SplitInfo kann zufaellig gleich der Entropie sein (hier bei Einkommen), wenn die Aufteilung der Instanzen zufaellig der Klassenverteilung entspricht.
- Konvention: 0 * log2(0) = 0 (muss man wissen!).
- log2 ist der Logarithmus zur Basis 2 (Einheit: bit).

---

## 3. TF-IDF (Term Frequency -- Inverse Document Frequency)

### Datensatz

Korpus D mit 4 Dokumenten, Lexikon mit 7 Termen.

| Dokument | Text (vereinfacht als Bag-of-Words) |
|----------|-------------------------------------|
| d1       | Daten Analyse Daten Mining Daten |
| d2       | Business Intelligence Daten Mining |
| d3       | Daten Warehouse Daten Warehouse |
| d4       | Business Intelligence Entscheidung Analyse |

**Terme (Q):** Daten, Analyse, Mining, Business, Intelligence, Warehouse, Entscheidung

### Schritt 1: Term Frequency (tfreq) zaehlen

tfreq(d_i, q_j) = Haeufigkeit, mit der Term q_j in Dokument d_i vorkommt.

| Term          | d1 | d2 | d3 | d4 |
|---------------|----|----|----|----|
| Daten         | 3  | 1  | 2  | 0  |
| Analyse       | 1  | 0  | 0  | 1  |
| Mining        | 1  | 1  | 0  | 0  |
| Business      | 0  | 1  | 0  | 1  |
| Intelligence  | 0  | 1  | 0  | 1  |
| Warehouse     | 0  | 0  | 2  | 0  |
| Entscheidung  | 0  | 0  | 0  | 1  |

### Schritt 2: Document Frequency (dfreq) berechnen

dfreq(q_j) = |X_q_j| / |X|

|X| = 4 (Gesamtzahl der Dokumente)

|X_q_j| = Anzahl der Dokumente, in denen q_j mindestens einmal vorkommt.

| Term          | Vorkommt in       | \|X_q_j\| | dfreq = \|X_q_j\|/4 |
|---------------|-------------------|------------|----------------------|
| Daten         | d1, d2, d3        | 3          | 3/4 = 0,7500         |
| Analyse       | d1, d4            | 2          | 2/4 = 0,5000         |
| Mining        | d1, d2            | 2          | 2/4 = 0,5000         |
| Business      | d2, d4            | 2          | 2/4 = 0,5000         |
| Intelligence  | d2, d4            | 2          | 2/4 = 0,5000         |
| Warehouse     | d3                | 1          | 1/4 = 0,2500         |
| Entscheidung  | d4                | 1          | 1/4 = 0,2500         |

### Schritt 3: Informationsgehalt (IDF) berechnen

Formel: info(q_j) = log2(|X| / |X_q_j|) = log2(1 / dfreq(q_j))

| Term          | 1/dfreq   | info = log2(1/dfreq) |
|---------------|-----------|----------------------|
| Daten         | 4/3 = 1,3333 | log2(1,3333) = **0,4150** |
| Analyse       | 4/2 = 2,0    | log2(2) = **1,0000** |
| Mining        | 4/2 = 2,0    | log2(2) = **1,0000** |
| Business      | 4/2 = 2,0    | log2(2) = **1,0000** |
| Intelligence  | 4/2 = 2,0    | log2(2) = **1,0000** |
| Warehouse     | 4/1 = 4,0    | log2(4) = **2,0000** |
| Entscheidung  | 4/1 = 4,0    | log2(4) = **2,0000** |

**Interpretation des IDF:** "Daten" kommt in 3 von 4 Dokumenten vor und hat daher den niedrigsten
Informationsgehalt (0,4150). "Warehouse" und "Entscheidung" kommen jeweils nur in einem Dokument
vor und haben den hoechsten Informationsgehalt (2,0).

### Schritt 4: TF-IDF-Werte berechnen

Formel: x_i,j = tfreq(d_i, q_j) * info(q_j)

| Term          | info   | d1            | d2            | d3            | d4            |
|---------------|--------|---------------|---------------|---------------|---------------|
| Daten         | 0,4150 | 3 * 0,4150 = **1,2450** | 1 * 0,4150 = **0,4150** | 2 * 0,4150 = **0,8300** | 0 * 0,4150 = **0**      |
| Analyse       | 1,0000 | 1 * 1,0 = **1,0000**    | 0 * 1,0 = **0**         | 0 * 1,0 = **0**         | 1 * 1,0 = **1,0000**    |
| Mining        | 1,0000 | 1 * 1,0 = **1,0000**    | 1 * 1,0 = **1,0000**    | 0 * 1,0 = **0**         | 0 * 1,0 = **0**         |
| Business      | 1,0000 | 0 * 1,0 = **0**         | 1 * 1,0 = **1,0000**    | 0 * 1,0 = **0**         | 1 * 1,0 = **1,0000**    |
| Intelligence  | 1,0000 | 0 * 1,0 = **0**         | 1 * 1,0 = **1,0000**    | 0 * 1,0 = **0**         | 1 * 1,0 = **1,0000**    |
| Warehouse     | 2,0000 | 0 * 2,0 = **0**         | 0 * 2,0 = **0**         | 2 * 2,0 = **4,0000**    | 0 * 2,0 = **0**         |
| Entscheidung  | 2,0000 | 0 * 2,0 = **0**         | 0 * 2,0 = **0**         | 0 * 2,0 = **0**         | 1 * 2,0 = **2,0000**    |

### Schritt 5: Repraesentativste Terme bestimmen

Der repraesentativste Term eines Dokuments ist derjenige mit dem hoechsten TF-IDF-Wert:

| Dokument | Repraesentativster Term | TF-IDF | Begruendung |
|----------|-------------------------|--------|-------------|
| d1 | **Daten**         | 1,2450 | Kommt 3x vor, trotz niedrigem IDF durch hohe Frequenz dominant |
| d2 | Mining / Business / Intelligence | je 1,0 | Drei Terme gleichauf; "Daten" hat nur 0,415 |
| d3 | **Warehouse**     | 4,0000 | Hoechster TF-IDF im gesamten Korpus! Kommt 2x vor und nur in d3 (hoher IDF) |
| d4 | **Entscheidung**  | 2,0000 | Kommt nur in d4 vor (hoher IDF) |

**Ergebnis:** "Warehouse" in d3 hat den hoechsten TF-IDF-Wert im gesamten Korpus (4,0).
Dies zeigt das Prinzip: Terme, die in einem Dokument haeufig, aber im Gesamtkorpus selten vorkommen,
repraesentieren ihr Dokument am besten.

### Pruefungshinweis:
- Die Logarithmusbasis ist im Skript nicht explizit festgelegt. In der Pruefung log2 verwenden (konsistent mit der Entropie), sofern nicht anders angegeben.
- Ein Term, der in **allen** Dokumenten vorkommt, haette dfreq = 1 und info = log2(1) = 0. Sein TF-IDF waere fuer jedes Dokument 0 -- er ist nicht diskriminierend.
- TF-IDF allein sagt nichts ueber die Aehnlichkeit von Dokumenten aus. Dafuer wird der Featurevektor normiert und der Winkel zwischen Vektoren verglichen (Formel 3.9 im Skript).
- Haeufige Fehlerquelle: dfreq zaehlt Dokumente, nicht Vorkommen! "Daten" kommt in d1 dreimal vor, aber |X_Daten| = 3 (drei Dokumente), nicht 6 (Gesamthaeufigkeit).

---

## 4. Apriori-Algorithmus (Support und Konfidenz)

### Datensatz

6 Transaktionen, 5 Items (A, B, C, D, E). Mindestsupport: 50% (= 3/6). Mindestkonfidenz: 70%.

| Transaktion | Items       |
|-------------|-------------|
| T1          | A, B, C     |
| T2          | A, B, D     |
| T3          | A, B, C, D  |
| T4          | B, C, E     |
| T5          | A, C, D     |
| T6          | A, B, C     |

### Schritt 1: Haeufige 1-Itemsets (I1) bestimmen

Formel: support(I) = |{T : I Teilmenge von T}| / |Gesamt|

| Itemset | Enthalten in          | Anzahl | Support   | >= 50%? |
|---------|-----------------------|--------|-----------|---------|
| {A}     | T1, T2, T3, T5, T6   | 5      | 5/6 = 83,3% | Ja    |
| {B}     | T1, T2, T3, T4, T6   | 5      | 5/6 = 83,3% | Ja    |
| {C}     | T1, T3, T4, T5, T6   | 5      | 5/6 = 83,3% | Ja    |
| {D}     | T2, T3, T5            | 3      | 3/6 = 50,0% | Ja    |
| {E}     | T4                    | 1      | 1/6 = 16,7% | **Nein** |

**I1 = { {A}, {B}, {C}, {D} }** -- Item E wird eliminiert.

### Schritt 2: Kandidaten fuer 2-Itemsets generieren und pruefen

Aus I1 werden alle Paare gebildet: {A,B}, {A,C}, {A,D}, {B,C}, {B,D}, {C,D}.

| Itemset | Enthalten in    | Anzahl | Support   | >= 50%? |
|---------|-----------------|--------|-----------|---------|
| {A, B}  | T1, T2, T3, T6  | 4      | 4/6 = 66,7% | Ja    |
| {A, C}  | T1, T3, T5, T6  | 4      | 4/6 = 66,7% | Ja    |
| {A, D}  | T2, T3, T5      | 3      | 3/6 = 50,0% | Ja    |
| {B, C}  | T1, T3, T4, T6  | 4      | 4/6 = 66,7% | Ja    |
| {B, D}  | T2, T3          | 2      | 2/6 = 33,3% | **Nein** |
| {C, D}  | T3, T5          | 2      | 2/6 = 33,3% | **Nein** |

**I2 = { {A,B}, {A,C}, {A,D}, {B,C} }**

### Schritt 3: Kandidaten fuer 3-Itemsets generieren und pruefen

Kandidaten werden aus Paaren in I2 gebildet, die sich in genau einem Element unterscheiden.
Zusaetzlich muessen **alle Untermengen** der Groesse 2 in I2 enthalten sein (Apriori-Prinzip).

Moegliche Kandidaten:
- {A,B} vereinigt {A,C} = {A,B,C}
  - Pruefung: {A,B} in I2? Ja. {A,C} in I2? Ja. {B,C} in I2? Ja.
  - --> Kandidat wird zugelassen.

- {A,B} vereinigt {A,D} = {A,B,D}
  - Pruefung: {B,D} in I2? **Nein!**
  - --> Kandidat wird durch Apriori-Prinzip **eliminiert**.

- {A,C} vereinigt {A,D} = {A,C,D}
  - Pruefung: {C,D} in I2? **Nein!**
  - --> Kandidat wird **eliminiert**.

- {B,C} vereinigt {A,B} = {A,B,C} -- bereits generiert.
- {B,C} vereinigt {A,C} = {A,B,C} -- bereits generiert.

Einziger verbleibender Kandidat: **{A,B,C}**

Support pruefen:
    {A,B,C} enthalten in: T1, T3, T6
    support({A,B,C}) = 3/6 = 50,0% >= 50% --> Ja!

**I3 = { {A,B,C} }**

### Schritt 4: 4-Itemsets

Fuer 4-Itemsets benoetigt man zwei 3-Itemsets, die sich in genau einem Element unterscheiden.
Da I3 nur ein Element enthaelt, sind keine Kandidaten moeglich.

**Der Algorithmus terminiert.**

### Schritt 5: Assoziationsregeln ableiten (Mindestkonfidenz 70%)

Formel: confidence(Ih -> Ic) = support(Ih vereinigt Ic) / support(Ih)

**Regeln aus 2-Itemsets:**

| Regel     | support(Ih -> Ic) | support(Ih) | Konfidenz        | >= 70%? |
|-----------|-------------------|-------------|------------------|---------|
| A -> B    | 4/6               | 5/6         | (4/6)/(5/6) = 4/5 = **80,0%** | Ja |
| B -> A    | 4/6               | 5/6         | (4/6)/(5/6) = 4/5 = **80,0%** | Ja |
| A -> C    | 4/6               | 5/6         | 4/5 = **80,0%** | Ja |
| C -> A    | 4/6               | 5/6         | 4/5 = **80,0%** | Ja |
| A -> D    | 3/6               | 5/6         | (3/6)/(5/6) = 3/5 = **60,0%** | **Nein** |
| D -> A    | 3/6               | 3/6         | (3/6)/(3/6) = 3/3 = **100%**  | Ja |
| B -> C    | 4/6               | 5/6         | 4/5 = **80,0%** | Ja |
| C -> B    | 4/6               | 5/6         | 4/5 = **80,0%** | Ja |

**Regeln aus 3-Itemset {A,B,C}:**

| Regel      | support(Ih -> Ic) | support(Ih) | Konfidenz            | >= 70%? |
|------------|-------------------|-------------|----------------------|---------|
| A,B -> C   | 3/6               | 4/6         | (3/6)/(4/6) = 3/4 = **75,0%** | Ja |
| A,C -> B   | 3/6               | 4/6         | 3/4 = **75,0%** | Ja |
| B,C -> A   | 3/6               | 4/6         | 3/4 = **75,0%** | Ja |
| A -> B,C   | 3/6               | 5/6         | (3/6)/(5/6) = 3/5 = **60,0%** | **Nein** |
| B -> A,C   | 3/6               | 5/6         | 3/5 = **60,0%** | **Nein** |
| C -> A,B   | 3/6               | 5/6         | 3/5 = **60,0%** | **Nein** |

### Ergebnis: Gueltige Regeln (Support >= 50% und Konfidenz >= 70%)

| Nr | Regel      | Support | Konfidenz |
|----|------------|---------|-----------|
| 1  | A -> B     | 66,7%   | 80,0%     |
| 2  | B -> A     | 66,7%   | 80,0%     |
| 3  | A -> C     | 66,7%   | 80,0%     |
| 4  | C -> A     | 66,7%   | 80,0%     |
| 5  | D -> A     | 50,0%   | 100%      |
| 6  | B -> C     | 66,7%   | 80,0%     |
| 7  | C -> B     | 66,7%   | 80,0%     |
| 8  | A,B -> C   | 50,0%   | 75,0%     |
| 9  | A,C -> B   | 50,0%   | 75,0%     |
| 10 | B,C -> A   | 50,0%   | 75,0%     |

### Nachweis: Konfidenz ist nicht symmetrisch

    confidence(A -> D) = 3/5 = 60%
    confidence(D -> A) = 3/3 = 100%

"Wenn ein Kunde A kauft, kauft er mit 60% Wahrscheinlichkeit auch D."
"Wenn ein Kunde D kauft, kauft er mit 100% Wahrscheinlichkeit auch A."

D kommt nur in 3 Transaktionen vor und immer zusammen mit A. Aber A kommt in 5 Transaktionen
vor, davon nur 3 mit D. Deshalb ist die Richtung der Regel entscheidend.

### Pruefungshinweis:
- Konfidenz ist **nicht symmetrisch**: conf(A -> D) != conf(D -> A). Dies wird haeufig abgefragt.
- Das Apriori-Prinzip erlaubt effizientes Pruning: Wenn {B,D} nicht haeufig ist, kann kein Superset von {B,D} haeufig sein. Deshalb wird {A,B,D} gar nicht erst geprueft.
- Umkehrung des Apriori-Prinzips gilt NICHT: Aus "alle Untermengen von I sind haeufig" folgt nicht "I ist haeufig".
- Support bezieht sich immer auf die **Vereinigung** von Praemisse und Konsequenz: support(A -> B) = support({A,B}), nicht support({A}) oder support({B}).

---

## 5. k-means Clusteranalyse

### Datensatz

6 Punkte in 2D, k = 2 Cluster.

| Punkt | x   | y   |
|-------|-----|-----|
| P1    | 1   | 2   |
| P2    | 2   | 1   |
| P3    | 1   | 1   |
| P4    | 8   | 8   |
| P5    | 9   | 7   |
| P6    | 8   | 9   |

### Schritt 1: Initiale Zentroiden waehlen

Wahl: Die ersten k Instanzen als initiale Zentroiden (Standardansatz).

    C1 = P1 = (1, 2)
    C2 = P4 = (8, 8)

### Schritt 2: Iteration 1 -- Zuordnung zum naechsten Zentroiden

Distanzformel (euklidisch): dist(P, C) = sqrt((x_P - x_C)^2 + (y_P - y_C)^2)

**Distanzen zu C1 = (1, 2):**

    dist(P1, C1) = sqrt((1-1)^2 + (2-2)^2) = sqrt(0 + 0)     = 0
    dist(P2, C1) = sqrt((2-1)^2 + (1-2)^2) = sqrt(1 + 1)     = sqrt(2)  = 1,414
    dist(P3, C1) = sqrt((1-1)^2 + (1-2)^2) = sqrt(0 + 1)     = sqrt(1)  = 1,000
    dist(P4, C1) = sqrt((8-1)^2 + (8-2)^2) = sqrt(49 + 36)   = sqrt(85) = 9,220
    dist(P5, C1) = sqrt((9-1)^2 + (7-2)^2) = sqrt(64 + 25)   = sqrt(89) = 9,434
    dist(P6, C1) = sqrt((8-1)^2 + (9-2)^2) = sqrt(49 + 49)   = sqrt(98) = 9,899

**Distanzen zu C2 = (8, 8):**

    dist(P1, C2) = sqrt((1-8)^2 + (2-8)^2) = sqrt(49 + 36)   = sqrt(85) = 9,220
    dist(P2, C2) = sqrt((2-8)^2 + (1-8)^2) = sqrt(36 + 49)   = sqrt(85) = 9,220
    dist(P3, C2) = sqrt((1-8)^2 + (1-8)^2) = sqrt(49 + 49)   = sqrt(98) = 9,899
    dist(P4, C2) = sqrt((8-8)^2 + (8-8)^2) = sqrt(0 + 0)     = 0
    dist(P5, C2) = sqrt((9-8)^2 + (7-8)^2) = sqrt(1 + 1)     = sqrt(2)  = 1,414
    dist(P6, C2) = sqrt((8-8)^2 + (9-8)^2) = sqrt(0 + 1)     = sqrt(1)  = 1,000

**Zuordnung (jeweils zum naechsten Zentroiden):**

| Punkt | dist zu C1 | dist zu C2 | Zuordnung |
|-------|------------|------------|-----------|
| P1    | 0          | 9,220      | **Cluster 1** |
| P2    | 1,414      | 9,220      | **Cluster 1** |
| P3    | 1,000      | 9,899      | **Cluster 1** |
| P4    | 9,220      | 0          | **Cluster 2** |
| P5    | 9,434      | 1,414      | **Cluster 2** |
| P6    | 9,899      | 1,000      | **Cluster 2** |

Cluster 1 = {P1, P2, P3}, Cluster 2 = {P4, P5, P6}

### Schritt 3: Iteration 1 -- Zentroiden neu berechnen

Formel: mu_Ci = (1/|Ci|) * Summe(x) fuer alle x in Ci

**Neuer Zentroid C1:**

    C1_x = (1 + 2 + 1) / 3 = 4/3 = 1,333
    C1_y = (2 + 1 + 1) / 3 = 4/3 = 1,333
    C1_neu = (1,333; 1,333)

**Neuer Zentroid C2:**

    C2_x = (8 + 9 + 8) / 3 = 25/3 = 8,333
    C2_y = (8 + 7 + 9) / 3 = 24/3 = 8,000
    C2_neu = (8,333; 8,000)

### Schritt 4: Iteration 2 -- Zuordnung mit neuen Zentroiden

**Distanzen zu C1_neu = (1,333; 1,333):**

    dist(P1, C1) = sqrt((1-1,333)^2 + (2-1,333)^2) = sqrt(0,111 + 0,444) = sqrt(0,556) = 0,745
    dist(P2, C1) = sqrt((2-1,333)^2 + (1-1,333)^2) = sqrt(0,444 + 0,111) = sqrt(0,556) = 0,745
    dist(P3, C1) = sqrt((1-1,333)^2 + (1-1,333)^2) = sqrt(0,111 + 0,111) = sqrt(0,222) = 0,471
    dist(P4, C1) = sqrt((8-1,333)^2 + (8-1,333)^2) = sqrt(44,49 + 44,49) = sqrt(88,98) = 9,433
    dist(P5, C1) = sqrt((9-1,333)^2 + (7-1,333)^2) = sqrt(58,78 + 32,11) = sqrt(90,89) = 9,534
    dist(P6, C1) = sqrt((8-1,333)^2 + (9-1,333)^2) = sqrt(44,49 + 58,78) = sqrt(103,27) = 10,162

**Distanzen zu C2_neu = (8,333; 8,000):**

    dist(P1, C2) = sqrt((1-8,333)^2 + (2-8,000)^2) = sqrt(53,78 + 36,00) = sqrt(89,78) = 9,475
    dist(P2, C2) = sqrt((2-8,333)^2 + (1-8,000)^2) = sqrt(40,11 + 49,00) = sqrt(89,11) = 9,440
    dist(P3, C2) = sqrt((1-8,333)^2 + (1-8,000)^2) = sqrt(53,78 + 49,00) = sqrt(102,78) = 10,138
    dist(P4, C2) = sqrt((8-8,333)^2 + (8-8,000)^2) = sqrt(0,111 + 0)     = sqrt(0,111) = 0,333
    dist(P5, C2) = sqrt((9-8,333)^2 + (7-8,000)^2) = sqrt(0,444 + 1,000) = sqrt(1,444) = 1,202
    dist(P6, C2) = sqrt((8-8,333)^2 + (9-8,000)^2) = sqrt(0,111 + 1,000) = sqrt(1,111) = 1,054

**Zuordnung:**

| Punkt | dist zu C1 | dist zu C2 | Zuordnung |
|-------|------------|------------|-----------|
| P1    | 0,745      | 9,475      | **Cluster 1** |
| P2    | 0,745      | 9,440      | **Cluster 1** |
| P3    | 0,471      | 10,138     | **Cluster 1** |
| P4    | 9,433      | 0,333      | **Cluster 2** |
| P5    | 9,534      | 1,202      | **Cluster 2** |
| P6    | 10,162     | 1,054      | **Cluster 2** |

### Schritt 5: Konvergenzpruefung

Die Zuordnung hat sich gegenueber Iteration 1 **nicht veraendert**.

Cluster 1 = {P1, P2, P3} (wie zuvor)
Cluster 2 = {P4, P5, P6} (wie zuvor)

Die Zentroiden bleiben identisch, da die Clusterzusammensetzung gleich geblieben ist.

**Der Algorithmus hat nach 2 Iterationen konvergiert. Die Partitionierung ist stabil.**

### Endergebnis

    Cluster 1: {P1(1,2), P2(2,1), P3(1,1)} mit Zentroid (1,333; 1,333)
    Cluster 2: {P4(8,8), P5(9,7), P6(8,9)} mit Zentroid (8,333; 8,000)

### Pruefungshinweis:
- k-means findet ein **lokales Minimum**, nicht zwingend das globale. Das Ergebnis haengt von der Initialisierung ab.
- Initiale Zentroiden koennen die ersten k Instanzen, zufaellig gewaehlte Instanzen oder sonstige Heuristiken sein.
- k-means kann nur **sphaerische Cluster** (in 2D: kreisfoermig) entdecken. Elongierte oder unregelmaessige Cluster werden nicht korrekt erkannt.
- Die **Reihenfolge** der Trainingsinstanzen kann das Ergebnis beeinflussen (bei unterschiedlicher Initialisierung).
- In der Pruefung: Distanzberechnungen sauber aufschreiben. Haeufigster Fehler: Wurzel vergessen oder Vorzeichen innerhalb der Quadrate falsch.

---

## 6. Konfusionsmatrix und Kennzahlen

### Szenario: Spam-Erkennung

Ein Spam-Filter klassifiziert 20 eingehende E-Mails als "Spam" oder "Kein Spam".
Positive Klasse (+1) = Spam, Negative Klasse (-1) = Kein Spam.

| Nr | Betreff               | Tatsaechlich | Vorhersage | Ergebnis |
|----|-----------------------|--------------|------------|----------|
| 1  | "Gewinn 10.000 EUR!"  | Spam         | Spam       | TP       |
| 2  | "Meeting morgen 10h"  | Kein Spam    | Kein Spam  | TN       |
| 3  | "Gratis Angebot"      | Spam         | Spam       | TP       |
| 4  | "Projektbericht Q3"   | Kein Spam    | Kein Spam  | TN       |
| 5  | "Rechnung 04/2024"    | Kein Spam    | Spam       | FP       |
| 6  | "Sie haben gewonnen"  | Spam         | Spam       | TP       |
| 7  | "Teammeeting Freitag" | Kein Spam    | Kein Spam  | TN       |
| 8  | "Sonderangebot heute" | Spam         | Kein Spam  | FN       |
| 9  | "Newsletter Firma"    | Kein Spam    | Spam       | FP       |
| 10 | "Billige Medikamente" | Spam         | Spam       | TP       |
| 11 | "Urlaubsantrag"       | Kein Spam    | Kein Spam  | TN       |
| 12 | "Kreditangebot 0%"    | Spam         | Spam       | TP       |
| 13 | "Budgetplanung 2025"  | Kein Spam    | Kein Spam  | TN       |
| 14 | "Abschlussbericht"    | Kein Spam    | Kein Spam  | TN       |
| 15 | "Exklusiver Rabatt"   | Spam         | Spam       | TP       |
| 16 | "Neue Stellenausschr."| Kein Spam    | Kein Spam  | TN       |
| 17 | "Dringendes Angebot"  | Spam         | Kein Spam  | FN       |
| 18 | "Schulung naechste W."| Kein Spam    | Kein Spam  | TN       |
| 19 | "Werbung Sonderpreis" | Kein Spam    | Spam       | FP       |
| 20 | "Kundenpraesentation" | Kein Spam    | Kein Spam  | TN       |

### Schritt 1: Werte zaehlen

    TP (Richtig Positiv): Nr. 1, 3, 6, 10, 12, 15  -->  TP = 6
    TN (Richtig Negativ): Nr. 2, 4, 7, 11, 13, 14, 16, 18, 20  -->  TN = 9
    FP (Falsch Positiv): Nr. 5, 9, 19  -->  FP = 3
    FN (Falsch Negativ): Nr. 8, 17  -->  FN = 2

Kontrolle: 6 + 9 + 3 + 2 = 20 Instanzen. Korrekt.

### Schritt 2: Konfusionsmatrix aufstellen

|                        | Vorhersage: Spam (+1) | Vorhersage: Kein Spam (-1) | Summe |
|------------------------|----------------------:|---------------------------:|------:|
| **Tatsaechlich: Spam (+1)**     | TP = 6                | FN = 2                     | 8     |
| **Tatsaechlich: Kein Spam (-1)**| FP = 3                | TN = 9                     | 12    |
| **Summe**              | 9                     | 11                         | 20    |

### Schritt 3: Kennzahlen berechnen

**Accuracy (Korrektklassifikationsrate):**

    Accuracy = (TP + TN) / (TP + TN + FP + FN)
             = (6 + 9) / (6 + 9 + 3 + 2)
             = 15 / 20
             = **0,75 = 75%**

Interpretation: 75% aller E-Mails werden korrekt klassifiziert.

**Recall (Richtigpositivrate / Sensitivitaet):**

    Recall = TP / (TP + FN)
           = 6 / (6 + 2)
           = 6 / 8
           = **0,75 = 75%**

Interpretation: Von 8 tatsaechlichen Spam-Mails werden 6 erkannt. 2 Spam-Mails landen im Posteingang.

**Precision:**

    Precision = TP / (TP + FP)
              = 6 / (6 + 3)
              = 6 / 9
              = **0,6667 = 66,67%**

Interpretation: Von 9 als Spam markierten E-Mails sind nur 6 tatsaechlich Spam. 3 legitime E-Mails
werden faelschlich als Spam markiert.

**Falschpositivrate:**

    FPR = FP / (FP + TN)
        = 3 / (3 + 9)
        = 3 / 12
        = **0,25 = 25%**

Interpretation: Von 12 tatsaechlich legitimen E-Mails werden 3 (= 25%) faelschlich als Spam markiert.

### Schritt 4: Interpretation im Kontext

- **FN-Fehler** (2 Spam-Mails nicht erkannt): Unangenehm, aber Nutzer sieht sie und kann manuell loeschen.
- **FP-Fehler** (3 legitime E-Mails als Spam markiert): Potenziell schlimmer, da wichtige E-Mails (z.B. Nr. 5 "Rechnung") im Spam-Ordner landen und uebersehen werden koennten.

In diesem Szenario waere es sinnvoll, die **Precision** zu erhoehen (weniger FP), selbst wenn dadurch der Recall sinkt. Das haengt aber vom konkreten Anwendungsfall ab.

### Pruefungshinweis:
- Zuerst festlegen, welche Klasse die **positive Klasse** ist! Im Skript: +1 = die "interessante" Klasse.
- Recall und Precision beziehen sich auf unterschiedliche Grundgesamtheiten: Recall = aus Sicht der tatsaechlichen Positiven, Precision = aus Sicht der vorhergesagten Positiven.
- Accuracy allein kann taeuschend sein: Bei 95% Kein-Spam und 5% Spam haette ein Modell, das immer "Kein Spam" vorhersagt, 95% Accuracy, aber 0% Recall.
- Falschpositivrate = 1 - Spezifitaet. Die Spezifitaet (= TN/(TN+FP)) ist das Gegenstueck zum Recall fuer die negative Klasse.
- FP und FN haben in der Regel **unterschiedliche Kosten**. Typische Pruefungsfrage: "Welcher Fehlertyp ist gravierender?" (kontextabhaengig argumentieren!)

---

## 7. z-Transformation (Standardisierung)

### Datensatz

5 Messwerte eines Attributs (z.B. Umsatz in Tsd. EUR):

    v1 = 12,  v2 = 18,  v3 = 15,  v4 = 22,  v5 = 8

### Schritt 1: Stichprobenmittelwert berechnen

Formel: x_quer = (1/NX) * Summe(xi,q)

    x_quer = (12 + 18 + 15 + 22 + 8) / 5
           = 75 / 5
           = **15**

### Schritt 2: Stichprobenvarianz berechnen

Formel: s^2 = (1/(NX - 1)) * Summe((xi,q - x_quer)^2)

Beachte: Teilen durch **(NX - 1)**, nicht durch NX! (Bessel-Korrektur fuer Stichprobenvarianz)

Einzelne Abweichungen:
    (v1 - x_quer)^2 = (12 - 15)^2 = (-3)^2 = 9
    (v2 - x_quer)^2 = (18 - 15)^2 = (3)^2  = 9
    (v3 - x_quer)^2 = (15 - 15)^2 = (0)^2  = 0
    (v4 - x_quer)^2 = (22 - 15)^2 = (7)^2  = 49
    (v5 - x_quer)^2 = (8 - 15)^2  = (-7)^2 = 49

Summe der quadrierten Abweichungen:
    9 + 9 + 0 + 49 + 49 = 116

Stichprobenvarianz:
    s^2 = 116 / (5 - 1)
        = 116 / 4
        = **29**

### Schritt 3: Standardabweichung berechnen

    s = sqrt(s^2) = sqrt(29) = **5,3852**

### Schritt 4: z-Werte berechnen

Formel: v' = (v - x_quer) / s

    z1 = (12 - 15) / 5,3852 = -3 / 5,3852     = **-0,5571**
    z2 = (18 - 15) / 5,3852 = 3 / 5,3852      = **0,5571**
    z3 = (15 - 15) / 5,3852 = 0 / 5,3852      = **0**
    z4 = (22 - 15) / 5,3852 = 7 / 5,3852      = **1,2999**
    z5 = (8 - 15) / 5,3852  = -7 / 5,3852     = **-1,2999**

### Schritt 5: Ergebnisuebersicht

| Wert | Original (v) | v - x_quer | z-Wert (v') |
|------|-------------:|-----------:|------------:|
| v1   | 12           | -3         | -0,5571     |
| v2   | 18           | 3          | 0,5571      |
| v3   | 15           | 0          | 0           |
| v4   | 22           | 7          | 1,2999      |
| v5   | 8            | -7         | -1,2999     |

### Schritt 6: Kontrolle

**Kontrolle 1:** Summe der z-Werte muss 0 ergeben.

    -0,5571 + 0,5571 + 0 + 1,2999 + (-1,2999) = 0  --> Korrekt!

**Kontrolle 2:** Werte unter dem Mittelwert haben negative z-Werte, Werte darueber positive.

    v1 = 12 < 15 --> z1 = -0,5571 (negativ)  --> Korrekt!
    v4 = 22 > 15 --> z4 = 1,2999 (positiv)   --> Korrekt!

**Kontrolle 3:** v3 = x_quer = 15, daher z3 = 0.  --> Korrekt!

### Interpretation

- v4 = 22 liegt 1,30 Standardabweichungen ueber dem Mittelwert
- v5 = 8 liegt 1,30 Standardabweichungen unter dem Mittelwert
- v3 = 15 entspricht exakt dem Mittelwert

Die z-Transformation macht Attribute mit unterschiedlichen Massstaaeben vergleichbar,
indem alle auf mu = 0 und sigma = 1 transformiert werden.

### Pruefungshinweis:
- **NX - 1 im Nenner der Varianz**, nicht NX! Die Bessel-Korrektur sorgt fuer eine erwartungstreue Schaetzung der Populationsvarianz.
- Die z-Transformation setzt eine annaehernd normalverteilte Stichprobe voraus. Fuer nicht normalverteilte Attribute ist die **Min-Max-Normalisierung** besser: v' = (v - v_min) / (v_max - v_min).
- Schnelle Kontrolle: Die Summe aller z-Werte muss exakt 0 ergeben. Wenn nicht, liegt ein Rechenfehler vor.
- z-Werte haben keine Einheit mehr -- sie druecken die Abweichung in Standardabweichungen aus.
- Typischer Fehler: Wurzel aus der Varianz vergessen (s, nicht s^2 in die Formel einsetzen).

---

## Formelsammlung (Kurzreferenz)

| Verfahren | Formel |
|-----------|--------|
| Gini-Index | Gini(t) = 1 - Summe(p(Ci\|t)^2) |
| GiniGain | Gini(Eltern) - Summe((n_v/n) * Gini(v)) |
| Entropie | H(t) = -Summe(p(Ci\|t) * log2(p(Ci\|t))) |
| InformationGain | H(Eltern) - Summe((n_v/n) * H(v)) |
| SplitInfo | -Summe((n_v/n) * log2(n_v/n)) |
| GainRatio | InformationGain / SplitInfo |
| TF-IDF | tfreq(d_i, q_j) * log2(\|X\| / \|X_q_j\|) |
| Support | \|{T : Ih vereinigt Ic Teilmenge T}\| / \|X_Tr\| |
| Konfidenz | support(Ih -> Ic) / support(Ih) |
| Eukl. Distanz | sqrt(Summe((x_i - y_i)^2)) |
| Zentroid | mu = (1/\|C\|) * Summe(x) fuer x in C |
| Accuracy | (TP + TN) / (TP + TN + FP + FN) |
| Recall | TP / (TP + FN) |
| Precision | TP / (TP + FP) |
| Falschpositivrate | FP / (FP + TN) |
| z-Transformation | v' = (v - x_quer) / s |
| Stichprobenvarianz | s^2 = (1/(NX-1)) * Summe((x_i - x_quer)^2) |
| Min-Max-Normalisierung | v' = (v - v_min) / (v_max - v_min) |
