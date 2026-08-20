# Wiederholungsfragen -- Einheit 2: Methoden und Instrumente der BI

> **Quelle:** 32711-02, Uebungsaufgaben S. 89-90, Loesungen S. 97-101

---

### Aufgabe 1: Grenzen Sie die Begriffe KDD und DM voneinander ab!

**Antwort:**
KDD = gesamter Prozess von Problemdefinition bis Wissensgenerierung (9 Schritte nach Fayyad et al., 1996). DM = ein Schritt innerhalb dieses Prozesses, naemlich die eigentliche Mustersuche in vorbereiteten Daten.

Ohne die vorgelagerten Schritte (Datenauswahl, Bereinigung, Transformation) waeren DM-Ergebnisse wenig aussagekraeftig -- die Daten muessen erst zielgerichtet selektiert und aufbereitet werden. Ebenso braucht es nachgelagerte Schritte (Interpretation, Verwendung), damit Ergebnisse in Unternehmensentscheidungen einfliessen. DM liefert nur Analysemethoden, KDD den Rahmen, in dem diese sinnvoll eingesetzt werden. Alle Phasen dienen der Entscheidungsunterstuetzung.

**Aufgabentyp:** Definition / Vergleich
**Benoetigtes Wissen:** Einheit 2, Kapitel 2 (KDD-Definition) und Kapitel 3/4/5 (Prozessphasen)

---

### Aufgabe 2: Erlaeutern Sie die Eigenschaften des KDD-Prozesses: nicht-trivial, valide, potentiell nuetzlich, leicht verstaendlich!

**Antwort:**
**Nicht-trivial:** Zusammenhaenge gehen ueber reine Aggregation oder Wiedergabe einzelner Datenreihen hinaus -- es wird ein Modell entwickelt, das tiefergehende Muster abbildet.

**Valide, potentiell nuetzlich, leicht verstaendlich** beziehen sich auf die Guete der gefundenen Zusammenhaenge:

- **Valide:** Das Modell bildet die Realitaet moeglichst gut ab (Generalisierung, nicht nur Anpassung an bekannte Daten).
- **Leicht verstaendlich:** Ergebnisse muessen fuer den Entscheider interpretierbar sein. Das Vorwissen des Anwenders ist bei der Aufbereitung zu beruecksichtigen.
- **Potentiell nuetzlich:** Ergebnisse lassen sich in Handlungsempfehlungen umsetzen, z.B. Anpassung von Geschaeftsprozessen.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 2, Kapitel 2 (KDD-Definition nach Fayyad et al., 1996; Interpretation nach Duesing, 2006)

---

### Aufgabe 3: KDD-Prozess im Managementkreislauf (Beispiel Produktpalette)

**Antwort:**
Managementkreislauf: Entscheidungsproblem -> Entscheidungsvorbereitung -> Entscheidung -> Wirkungsanalyse (zyklisch).

KDD ordnet sich vor allem der Entscheidungsvorbereitung und Wirkungsanalyse zu. Beispiel: Soll die Produktpalette erweitert werden? In der Entscheidungsvorbereitung werden Alternativen betrachtet (flaechendeckend vs. regional, dauerhaft vs. befristet) und durch KDD prognostiziert, welche Auswirkungen diese haben. DM greift dabei auf historische Verkaufsdaten, Produktdaten und Preise aus dem DWH zu. Die Problemdefinition des KDD ergibt sich direkt aus dem Entscheidungsproblem.

Falls DM z.B. zeigt, dass eine Erweiterung nur in bestimmten Bundeslaendern sinnvoll ist (weil sich das Kaufverhalten dort unterscheidet), muss das Management diese Veraenderung erneut planen -- so schliesst sich der Kreislauf. Die Wirkungsanalyse prueft spaeter, ob die Veraenderung tatsaechlich die erwartete Wirkung hatte. Aus ihr koennen sich neue Entscheidungsprobleme ergeben.

**Aufgabentyp:** Transfer
**Benoetigtes Wissen:** Einheit 2, Kapitel 2.2 (Managementkreislauf) und Kapitel 3.1 (Problemdefinition)

---

### Aufgabe 4: Erlaeutern Sie das Prinzip "Garbage in -- Garbage out"!

**Antwort:**
Der Output eines DM-Verfahrens kann nur so gut sein wie der Input. Werden Daten mit schlechter Qualitaet oder irrelevante Daten verwendet, koennen die Ergebnisse nicht besser sein als die Eingangsdaten es zulassen. "Muell" rein = "Muell" raus.

Das unterstreicht die hohe Bedeutung der Datenqualitaet fuer DM-Anwendungen und begruendet, warum die vorbereitenden Schritte (Datenauswahl, Bereinigung, Aufbereitung) im KDD-Prozess so zentral sind.

**Aufgabentyp:** Definition / Diskussion
**Benoetigtes Wissen:** Einheit 2, Kapitel 3.2/3.3 (Datenauswahl, Bereinigung und Aufbereitung)

---

### Aufgabe 5: Fehlerart bei IBAN-Verwechslung und Umgangsmoeglichkeiten

**Antwort:**
**Fehlerart:** Syntaktischer Fehler -- die Werte (Kontonummer + BLZ) sind inhaltlich korrekt, entsprechen aber nicht dem erwarteten Datenmodell-Format (IBAN).

**Drei Umgangsmoeglichkeiten:**

1. **Laissez Faire:** Keine Massnahmen. Hier ungeeignet, da die Ueberweisung sonst nicht durchgefuehrt wird.
2. **Reaktives Vorgehen:** Fehler einmalig beheben (IBAN manuell aus Kontonummer und BLZ konstruieren). Es wird angenommen, der Fehler wiederholt sich nicht. Problem: Waehrend der Umstellungsphase tritt der Fehler haeufig auf, daher dauerhaft hohe Kosten.
3. **Proaktives Vorgehen:** Fehler bereinigen und Massnahmen zur kuenftigen Vermeidung einfuehren, z.B. automatische Umwandlung oder Kundenbenachrichtigung, dass Ueberweisungen im alten Format kuenftig nicht mehr bearbeitet werden.

**Empfehlung:** Proaktives Vorgehen, da der Fehler waehrend der Umstellungsphase haeufig auftritt und reaktive Einzelbereinigung zu teuer waere.

**Aufgabentyp:** Transfer / Diskussion
**Benoetigtes Wissen:** Einheit 2, Kapitel 3.3 (Fehlerklassen: semantisch/syntaktisch/coverage; Umgang mit Fehlern)

---

### Aufgabe 6: Normalisierung des Attributs Einkommen auf [0,1]

**Antwort:**
Min-Max-Normalisierung mit der Formel:

    v' = (v - v_min) / (v_max - v_min)

Gegeben: v_max = 75.000, v_min = 22.000, also Spannweite = 53.000.

Beispielberechnung fuer v = 22.000:

    v' = (22.000 - 22.000) / (75.000 - 22.000) = 0 / 53.000 = 0

Fuer v = 75.000:

    v' = (75.000 - 22.000) / 53.000 = 53.000 / 53.000 = 1

Jeder Wert wird so auf das Intervall [0,1] abgebildet, wobei der kleinste Wert auf 0 und der groesste auf 1 faellt. Die Normalisierung wird eingesetzt, wenn keine Normalverteilungsannahme vorliegt (im Gegensatz zur z-Transformation/Standardisierung).

**Aufgabentyp:** Berechnung
**Benoetigtes Wissen:** Einheit 2, Kapitel 3.4 (Normalisierung, Min-Max-Transformation)

---

### Aufgabe 7: Agglomeratives vs. divisives Clustering

**Antwort:**
Beides sind hierarchische Clusteringverfahren, arbeiten aber genau gegenlaeutig:

- **Agglomerativ (bottom-up):** Anfangs bildet jede Instanz ein eigenes Cluster. Schrittweise werden die beiden aehnlichsten (naechsten) Cluster zusammengefasst, bis nur noch ein einziges Cluster uebrig ist.
- **Divisiv (top-down):** Anfangs bilden alle Instanzen ein einziges Cluster. Dieses wird schrittweise in kleinere Cluster aufgeteilt, bis jede Instanz ein eigenes Cluster bildet.

In jedem Schritt werden also entweder zwei Cluster zusammengefuegt (agglomerativ) oder ein Cluster getrennt (divisiv). Die Ergebnisse lassen sich als Dendrogramm darstellen.

**Aufgabentyp:** Vergleich
**Benoetigtes Wissen:** Einheit 2, Kapitel 4.5 (Clusteranalyse, hierarchische Verfahren)

---

### Aufgabe 8: Grundidee der Clusteranalyse

**Antwort:**
Instanzen so in Gruppen (Cluster) einordnen, dass die Cluster in sich moeglichst homogen und untereinander moeglichst heterogen sind. "Homogen" = geringe paarweise Distanz innerhalb eines Clusters; "heterogen" = grosse paarweise Distanz zwischen Clustern.

Die Aehnlichkeit wird ueber Distanzfunktionen gemessen, z.B. Euklidische Distanz oder Manhattan-Distanz. Clusteranalyse ist unueberwachtes Lernen -- die Cluster sind vorab nicht definiert, sondern ergeben sich aus den Daten.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 2, Kapitel 4.5 (Clusteranalyse, Distanzfunktionen)

---

### Aufgabe 9: Falsch-positiv und falsch-negativ (Kreditwuerdigkeit)

**Antwort:**
Positive Klasse = "nicht kreditwuerdig" (das kritische Merkmal).

- **Falsch-negativ (FN):** Nicht-kreditwuerdige Kunden werden faelschlicherweise als kreditwuerdig eingestuft. Folge: Bank vergibt Kredit an Kunden mit hohem Ausfallrisiko -- potenziell hohe Kosten durch Kreditausfall.
- **Falsch-positiv (FP):** Kreditwuerdige Kunden werden faelschlicherweise als nicht-kreditwuerdig eingestuft. Folge: entgangenes Geschaeft (Opportunitaetskosten), aber vergleichsweise gering.

Der falsch-negative Fehler ist hier deutlich gravierender. Deshalb ist der Recall (Sensitivitaet = TP/(TP+FN)) besonders wichtig -- er misst, wie viele der tatsaechlich nicht-kreditwuerdigen Kunden korrekt erkannt werden.

**Aufgabentyp:** Transfer / Diskussion
**Benoetigtes Wissen:** Einheit 2, Kapitel 5.1 (Konfusionsmatrix, Evaluation)

---

### Aufgabe 10: Complete-Linkage Clustering (Distanzmatrix, 3 Iterationen)

**Antwort:**
Ausgangsdistanzmatrix:

```
      A    B    C    D    E
A     -
B    10    -
C     5    7    -
D     8    9    5    -
E     5    8    4    7    -
```

**Complete-Linkage:** Die Distanz zwischen zwei Clustern ist die maximale paarweise Entfernung aller Instanzenpaare aus den beiden Clustern.

**Iteration 1:** Geringste Distanz = 4 (C, E). Zusammenfassung zu {C,E}.
Neue Distanzen (jeweils Maximum):
- dist({C,E}, A) = max(5, 5) = 5
- dist({C,E}, B) = max(7, 8) = 8
- dist({C,E}, D) = max(5, 7) = 7

```
       A    B   {C,E}   D
A      -
B     10    -
{C,E}  5    8     -
D      8    9     7     -
```

**Iteration 2:** Geringste Distanz = 5 (A, {C,E}). Zusammenfassung zu {A,C,E}.
Neue Distanzen:
- dist({A,C,E}, B) = max(10, 8) = 10
- dist({A,C,E}, D) = max(8, 7) = 8

```
         B   {A,C,E}   D
B        -
{A,C,E} 10      -
D        9      8      -
```

**Iteration 3:** Geringste Distanz = 8 ({A,C,E}, D). Zusammenfassung zu {A,C,D,E}.
Neue Distanzen:
- dist({A,C,D,E}, B) = max(10, 9) = 10

```
            B   {A,C,D,E}
B           -
{A,C,D,E}  10       -
```

**Aufgabentyp:** Berechnung
**Benoetigtes Wissen:** Einheit 2, Kapitel 4.5 (Hierarchisch-agglomeratives Clustering, Linkage-Verfahren)
