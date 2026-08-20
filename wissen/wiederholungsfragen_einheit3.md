# Wiederholungsfragen -- Einheit 3: Intelligente Datenhaltung und -bereitstellung

> **Modul:** 32711 Business Intelligence | **Quelle:** Uebungsaufgaben und Loesungen aus Einheit 3

---

### Aufgabe 1: Erlaeutern Sie die verschiedenen Typen von Business Rules!

**Antwort:**
Drei Typen nach Schacher & Graessle: **Ableitungsregeln** entstehen durch Rueckgriff auf bestehende Regeln oder Informationen, aus denen sich neue Business Rules ableiten lassen (z. B. Definition "zurueckgewonnener Kunde" aus Kombination bestehender Merkmale). **Einschraenkungen** sind Gebote oder Verbote, die zu jeder Zeit gelten (z. B. einmalige Praemie nur bei Erstkonto-Eroeffnung). **Prozessregeln** folgen dem Muster "wenn xyz dann abc" -- ein Sachverhalt oder eine Aktivitaet loest eine andere Aktion aus (z. B. bei Kreditantrag muss Kreditwuerdigkeit geprueft werden).

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 3, Kapitel 2.1 (Business Rules)

---

### Aufgabe 2: Erlaeutern Sie, weshalb fachliche Metadaten haeufig auch als unstrukturierte Metadaten bezeichnet werden!

**Antwort:**
Fachliche Metadaten koennen im Gegensatz zu technischen Metadaten haeufig nur unstrukturiert erhoben werden. Mitarbeiter der Fachabteilungen sammeln durch Anwendung und Erfahrung **implizites Wissen**, das erst in explizites Wissen transformiert werden muss -- etwa durch Interviews oder Beobachtungen. Technische Metadaten dagegen entstehen strukturiert bei Entwicklung, Betrieb und Wartung des Datenbanksystems und lassen sich automatisiert erfassen. Die manuelle, schwer standardisierbare Erhebung fachlicher Metadaten begruendet daher die Bezeichnung "unstrukturiert".

**Aufgabentyp:** Definition / Diskussion
**Benoetigtes Wissen:** Einheit 3, Kapitel 2.2 (Metadatenmanagement)

---

### Aufgabe 3: Erlaeutern Sie die Bedeutung von Metadaten anhand des Beispiels der Datumsangabe 10/12/99!

**Antwort:**
Die Datumsangabe 10/12/99 ist ohne Metadaten nicht eindeutig interpretierbar. Nach britischer Schreibweise: 12. Oktober 1999. Nach amerikanischer Schreibweise: 10. Dezember 1999. Metadaten legen die Struktur des Datenobjekts fest -- sie definieren, ob die Interpretation und Erfassung nach britischem oder amerikanischem Format erfolgen soll. Ohne diese "Daten ueber Daten" ist eine korrekte Auswertung unmoeglich, was die zentrale Rolle von Metadaten fuer die Datenqualitaet und -interpretation verdeutlicht.

**Aufgabentyp:** Transfer
**Benoetigtes Wissen:** Einheit 3, Kapitel 2.2 (Metadatenmanagement)

---

### Aufgabe 4: Grenzen Sie dispositive und operative Daten voneinander ab!

**Antwort:**
Zentrale Unterschiede in fuenf Dimensionen:

| Eigenschaft | Dispositive Daten | Operative Daten |
|-------------|-------------------|-----------------|
| **Ziel** | Entscheidungsunterstuetzung | Unterstuetzung des Tagesgeschaefts |
| **Zustand** | Kontrollierte Redundanzen, konsistent | Haeufig redundant und inkonsistent |
| **Modellierung** | Sachgebiets-/themenorientiert | Funktions-/transaktionsorientiert |
| **Zeitbezug** | Historienbetrachtung ueber Zeitverlauf | Aktuell, zeitpunktbezogen |
| **Ausrichtung** | Meist verdichtet, transformiert | Detaillierte, granulare Geschaeftsvorfalldaten |

Dispositive Daten dienen der Managementebene, operative Daten der Abteilungsebene.

**Aufgabentyp:** Vergleich
**Benoetigtes Wissen:** Einheit 3, Kapitel 3.1 (Data Warehouse)

---

### Aufgabe 5: Erlaeutern Sie die zentralen Eigenschaften eines DWH nach Inmon!

**Antwort:**
Vier SINT-Eigenschaften: **Themenorientiert (Subject-oriented)** -- Daten werden nach Themen wie Kunden, Produkte oder Mitarbeiter gehalten, nicht funktions-/transaktionsorientiert wie in operativen Systemen. Themen variieren je nach Unternehmen. **Integriert (Integrated)** -- Daten aus verschiedenen Applikationen mit unterschiedlichen Formaten und Kodierungen werden so angepasst, dass ein einheitlicher, integrierter Datenbestand entsteht. **Zeitraumbezogen (Time-variant)** -- Daten werden ueber einen Zeitverlauf betrachtet, sodass die historische Entwicklung beruecksichtigt werden kann (Zeithorizont typisch 5-10 Jahre). **Nicht-volatil (Nonvolatile)** -- Daten sind dauerhaft und werden nicht ueberschrieben. Alte und neue Werte koexistieren, woraus sich auch der Zeitraumbezug ergibt.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 3, Kapitel 3.1 (Data Warehouse, SINT-Eigenschaften)

---

### Aufgabe 6: Nennen und erlaeutern Sie die drei Phasen im ETL-Prozess!

**Antwort:**
**Extraktion:** Daten werden von der Datenquelle in den Arbeitsbereich (Staging Area) uebertragen. Beschaffenheit und Relevanz der Daten muessen beruecksichtigt werden. Die Extraktion soll moeglichst automatisiert erfolgen. Neben der Auswahl der zu extrahierenden Daten ist auch die Haeufigkeit festzulegen (periodisch, anfragegesteuert, ereignisgesteuert, sofort nach Veraenderung).

**Transformation:** Daten werden an das Format des DWH angepasst. Typische Schritte: Standardisierung von Zeichenketten und Kodierungen, Korrektur oder Bereinigung fehlerhafter Daten, Loeschung redundanter oder veralteter Daten.

**Laden:** Daten werden in das DWH uebertragen. Zwei Ladephasen: beim **Initial Load** werden die Daten einmalig in das DWH geladen; beim **Refresh** erfolgt die Aktualisierung in regelmaessigen Abstaenden, oft ausserhalb der Auslastungshoehen (Wochenende, nachts).

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 3, Kapitel 3.2 (ETL-Komponente)

---

### Aufgabe 7: Welche verschiedenen Ebenen lassen sich in einem DWH-System unterscheiden? Erlaeutern Sie diese kurz!

**Antwort:**
Fuenf Ebenen nach Sinz et al.:

1. **Ebene der operativen Systeme** -- Verschiedene Datenquellen, aus denen die Daten stammen. Eigentlich dem DWH-System vorgelagert, nicht Teil davon.
2. **Datenerfassungsebene** -- Daten werden physisch in das DWH-System gebracht. Hier erfolgt die Bereinigung, Harmonisierung und Zusammenfuehrung der Daten (Staging Area, ETL-Komponente).
3. **Datenhaltungsebene** -- Daten werden durch die ETL-Komponente dem DWH zugefuehrt und dort persistent gespeichert (DWH, ODS).
4. **Datenbereitstellungsebene** -- Zweckmaessige Aufbereitung der entscheidungsrelevanten Informationen fuer den Entscheidungstraeger (OLAP, Analysekomponenten).
5. **Praesentationsebene** -- Adaequate Aufbereitung und Praesentation der Daten. Erfolgsgroessen werden kritisch ueberwacht; bei Ueberschreitung kritischer Wertgrenzen erfolgt eine Benachrichtigung an den Entscheidungstraeger.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 3, Kapitel 3 (DWH-Gesamtarchitektur nach Sinz et al.)

---

### Aufgabe 8: Grenzen Sie Data Marts und DWHs voneinander ab!

**Antwort:**
**Adressat:** Data Mart richtet sich an eine Abteilung, DWH an das gesamte Unternehmen.
**Anzahl:** Viele Data Marts pro Unternehmen (z. B. je Abteilung), aber nur ein DWH.
**Detaillierungsgrad:** Data Marts enthalten hoeher aggregierte Daten, DWH den kleinsten Detaillierungsgrad.
**Datenmenge:** Data Marts eher gering, DWH hoch.
**Externe Datenquellen:** Data Marts integrieren diese in der Regel nicht, DWH integriert saemtliche verfuegbaren externen Quellen.
**Endanwenderzugriff:** Bei Data Marts direkt moeglich, bei DWH haeufig nur ueber IT-Abteilung.
**Modellierungskonventionen:** Data Marts oft heterogen (bei proprietaeren), DWH einheitlich.
**Freiheitsgrad der Analysen:** Data Marts begrenzt (kein Blick ueber Abteilungsgrenzen), DWH flexibel mit unternehmensweiter Sicht.
**Betriebswirtschaftliches Ziel:** Data Marts unterstuetzen Entscheider einer Abteilung effizient, DWH leistet strategische, taktische und operative Managementunterstuetzung.

**Aufgabentyp:** Vergleich
**Benoetigtes Wissen:** Einheit 3, Kapitel 3.3 (Data Marts)

---

### Aufgabe 9: Erlaeutern Sie die Eigenschaften online, analytical und processing im Rahmen von OLAP!

**Antwort:**
**Online** -- Anwender koennen direkt auf den zentralen Datenbestand zugreifen, um Daten zu betrachten oder zu manipulieren. Kein Batch-Betrieb, sondern unmittelbarer Zugang.
**Analytical** -- Im Vordergrund stehen unterschiedliche Sichten fuer Entscheidungstraeger, nicht die einzelnen Geschaeftsvorfaelle wie beim OLTP. Analyse historischer, konsolidierter Datenbestaende statt transaktionaler Verarbeitung.
**Processing** -- Schnelle Berechnungen und Manipulationen koennen durch den Anwender selbst durchgefuehrt werden. Der Nutzer ist aktiv in der Datenauswertung, nicht nur passiver Empfaenger von Berichten.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 3, Kapitel 4 (OLAP)

---

### Aufgabe 10: Was besagt das Prinzip FASMI im Rahmen von OLAP?

**Antwort:**
FASMI = **Fast Analysis of Shared Multidimensional Information** (Pendse/Creeth, 1995). Fuenf Anforderungen an OLAP-Systeme:

- **Fast (Geschwindigkeit):** Anfragen sollen innerhalb von maximal fuenf Sekunden beantwortet werden. Haeufige Anfragen schneller, komplexere duerfen laenger dauern.
- **Analysis (Analysemoeglichkeit):** Intuitive, benutzerfreundliche Analysefunktionen. Anwender sollen einfache Funktionen fuer eigene Berechnungen nutzen koennen.
- **Shared (Mehrbenutzerfaehigkeit):** Mehrere Anwender koennen gleichzeitig auf ein und dieselben Daten zugreifen.
- **Multidimensional (Multidimensionalitaet):** Anwender koennen mehrere Dimensionen nach ihren Beduerfnissen miteinander kombinieren und fuer Analysen verwenden.
- **Information (Kapazitaet):** Sehr grosse Datenmengen muessen analysierbar sein, wobei die Antwortzeiten unabhaengig von Datenmenge und Anfragenanzahl stabil bleiben muessen.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 3, Kapitel 4 (OLAP, FASMI-Prinzip)

---

### Aufgabe 11: Erlaeutern Sie die Funktionalitaet "Pivotierung" im Rahmen von OLAP!

**Antwort:**
Bei der Pivotierung wird der OLAP-Wuerfel um seine eigene Achse gedreht -- entweder um die horizontale oder die vertikale Achse. Ziel ist es, die betrachteten Dimensionen gegeneinander auszutauschen, um so eine andere Perspektive auf die Daten zu erhalten und weitere Analysen zu ermoeglichen. Die Datentiefe aendert sich dabei nicht, nur die Anordnung der Dimensionen. In tabellarischer Darstellung wird die Pivotierung durch Pivottabellen realisiert: Zeilen- und Spaltendimensionen werden vertauscht, um denselben Datenbestand aus einer anderen Blickrichtung zu betrachten.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 3, Kapitel 4.2 (OLAP-Operationen)

---

*Letzte Aktualisierung: 2026-08-20*
