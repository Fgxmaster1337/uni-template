# 03 - Intelligente Datenhaltung und -bereitstellung

> **Quelle:** 32711-03-S#1-2001332.pdf (64 Seiten) | **Pruefungsrelevanz:** HOCH

## Ueberblick

Diese Einheit behandelt die Datenhaltung als Basis fuer die Wissensgenerierung im KDD-Prozess. Im Mittelpunkt stehen grundlegende Begriffe wie Business Rules, Metadatenmanagement und Datenqualitaetsmanagement. Darauf aufbauend wird die Architektur von Data Warehouse-Systemen mit ihren Komponenten (ETL, ODS, Metadatenbanksystem, Analysekomponenten) und Ebenen (nach Sinz et al.) erlaeutert. Als zentrale Analysekomponente wird OLAP mit seinen Anforderungen (Codd 12 Regeln, FASMI), Auspraegungen (ROLAP, MOLAP, HOLAP) und Operationen (Pivotierung, Roll-Up, Drill-Down, Slice, Dice) vorgestellt. Abschliessend werden Data Marts als alternative Ausgestaltungsform zum zentralen DWH verglichen.

---

## Kernkonzepte

### Definition: Business Rules

Business Rules sind nach Scheer/Werth „Richtlinien oder Geschaeftspraktiken, die das Verhalten eines Unternehmens beeinflussen oder leiten. Verhalten bedeutet in dem Zusammenhang, mit welchen Prozessen (wie) und mit welchen Ressourcen (womit), welche Produkte erstellt werden" (Scheer/Werth 2006, S. 52).

Allgemein: Ein Regelwerk oder eine Anleitung, die dabei helfen soll, das Alltagsgeschaeft zu steuern und zu organisieren (Schacher & Graessle, 2006). Business Rules geben den Weg vor, wie ein Ziel erreicht werden soll.

### Typen von Business Rules (nach Schacher & Graessle)

| Typ | Beschreibung | Beispiel |
|-----|-------------|----------|
| **Ableitungsregeln** | Regeln entstehen durch Rueckgriff auf bestehende Regeln oder Informationen, woraus sich neue Business Rules ableiten lassen | Eine Person ist ein zurueckgewonnener Kunde, wenn sie laenger als ein Jahr keine Leistungen bezogen hat und danach wieder bezieht |
| **Einschraenkungen** | Gebote oder Verbote, die zu jeder Zeit gelten | Ein Neukunde erhaelt nur bei der ersten Eroeffnung eines Bankkontos eine einmalige Praemie |
| **Prozessregeln** | Werden in der Form „wenn xyz dann abc" formuliert; ein Sachverhalt loest eine andere Aktion aus | Wenn ein Kunde einen Kredit beantragt, muss seine Kreditwuerdigkeit geprueft werden |

### Eigenschaften von Business Rules

- **Praezise**: Kein Interpretationsspielraum fuer Mitarbeiter
- **Verstaendlich**: Unabhaengig von Abteilung oder Wissensstand verstaendlich
- **Deklarativ**: Beschreibt nur, was das Ziel ist, nicht wie es erreicht werden soll

### Durchfuehrungslevel von Business Rules

| Level | Beschreibung |
|-------|-------------|
| **Strikte Durchsetzung** | Bei Nicht-Beachtung droht eine Strafe |
| **Aufgeschobene Durchsetzung** | Regel kann zurueckgestellt werden, muss aber spaeter beruecksichtigt werden |
| **Vorherige Autorisierung** | Regeln werden normalerweise umgesetzt; Ausnahmen moeglich ohne Strafe |
| **Ausnahme mit vorheriger Rechtfertigung** | Nichtbeachtung muss vorab geklaert und gerechtfertigt werden |
| **Ausnahme mit Erlaeuterung** | Bei Nichtbeachtung ist eine schriftliche Erlaeuterung erforderlich |
| **Richtwert** | Einhaltung denkbar, aber keinesfalls zwingend erforderlich |

Die Zuordnung zu den Durchfuehrungsleveln wird primaer durch die taktischen Handlungsoptionen eines Unternehmens festgelegt.

### Business Rules und DWH

Im DWH-Kontext umfassen Business Rules z. B. Vorschriften, wann Daten in das DWH geladen werden oder welche Transformationsregeln gelten. Zur Festlegung werden haeufig Interviews durchgefuehrt. Problem: Business Rules sind in der Regel unvollstaendig und schlecht dokumentiert. Eine Loesung ist das **Business Rules Mining**, das aehnlich wie Data Mining (speziell Rule Induction) funktioniert und das Verhalten der Systeme „durchschuerft", um Business Rules abzuleiten (Moore & Wall, 2000).

Zur formalen Implementierung existieren Sprachen wie **RuleML** (Rule Markup Language) und **BRML** (Business Rule Markup Language). Regeln werden zentral in einem **Regelrepositorium** abgelegt.

---

### Definition: Business Motivation Model (BMM)

Das BMM (Business Rules Group, 2010) bildet den Zusammenhang zwischen Geschaeftsregeln, Geschaeftspolitik und Unternehmensstrategie ab. Es unterteilt sich in zwei Bereiche:

**Unternehmenszweck (rechte Seite):**

| Element | Beschreibung |
|---------|-------------|
| **Vision** | Langfristige Vorstellung, wie sich das Unternehmen in Zukunft sieht; betrifft alle Teile des Unternehmens; beinhaltet nicht den Weg dorthin |
| **Ziele** | Betreffen Teile des Unternehmens; langfristig, qualitativ und eher allgemein formuliert |
| **Zielvorstellungen** | Kurzfristig, quantitativ, spezifisch, mit genauem Ende versehen; muessen realistisch, messbar und mit festem Zeithorizont sein; quantifizieren ein Ziel |

**Wege zur Erreichung des Zwecks (linke Seite):**

| Element | Beschreibung |
|---------|-------------|
| **Mission** | Operationalisiert die Vision; langfristig; wird durch Unternehmensstrategie bestimmt |
| **Handlungsoptionen** | Strategische (langfristig, breiter Anwendungsbereich) und taktische (kurzfristig) Handlungen; umfassen nicht die Geschaeftsprozesse selbst, koennen aber durch sie umgesetzt werden |
| **Vorschriften/Anweisungen** | Deklarativ; verantwortlich fuer Durchsetzung der Geschaeftsstruktur; Kontrolle und Beeinflussung des Verhaltens |

**Vorschriften unterteilen sich in:**
- **Geschaeftspolitik**: Wenig strukturiert, abstrakt, kein Standardvokabular, nicht automatisierbar; steuert Geschaeftsprozesse und bildet Basis fuer Business Rules
- **Business Rules**: Abstrakt aber klar und eindeutig durch Standardvokabular; klar strukturiert; teilweise automatisierbar

---

### Definition: Metadaten

Nach Sen umfasst der Bereich Metadaten die „Analyse der Daten ueber Daten" (Sen, 2004). Der Begriff „Meta" stammt aus dem Griechischen und bedeutet „auf einer hoeheren Stufe, Ebene befindlich" oder „uebergeordnet".

Zwei wesentliche Merkmale von Metadaten:

| Merkmal | Beschreibung |
|---------|-------------|
| **Beziehungsmerkmal** | Metadaten sind keine Daten mit festgeschriebenem Merkmal, sondern erst durch konkrete Bezugsdaten interpretierbar; relatives Konstrukt |
| **Abstraktionsmerkmal** | Metadaten beziehen sich auf eine hoehere Abstraktionsebene, beschreiben Eigenschaften der gleichartigen Bezugsdaten, nicht die einzelnen Bezugsdaten selbst |

### Entwicklung der Bedeutung von Metadaten

| Zeitraum | Bedeutung |
|----------|-----------|
| 1960er | Einfache Dateinamen und Feldnamen |
| 1970er | Nutzung zur Definition von Daten (Relationsbezeichnungen, Attributnamen, Schluessel- und Domaininformationen) |
| 1980er | Begriff „Asset" ersetzt „Daten"; Assets als Nebenprodukt der Anwendungsentwicklung |
| 1990er | Viele Forschungsarbeiten; Metadaten in DWHs (Front Room und Back Room-Metadaten) |

### Klassifizierung von Metadaten

| Typ | Beschreibung | Nutzer |
|-----|-------------|--------|
| **Technische Metadaten** | Beschreiben logische und physische Datenbankschemata und Datenfluesse; entstehen bei Entwicklung, Betrieb und Wartung des Datenbanksystems; strukturiert erhoben | Administratoren, Anwendungsentwickler |
| **Fachliche Metadaten** | Betriebswirtschaftliches, unternehmensbezogenes Wissen; ermoeglichen Interpretation der Daten; pflegeintensiv; muessen manuell erfasst werden; auch als **unstrukturierte Metadaten** bezeichnet | Endanwender |

### Acht Metadatenkategorien (nach Auth 2003)

| Kategorie | Beschreibung |
|-----------|-------------|
| **Terminologie** | Definition von Fachbegriffen, Beziehungen und Datenstrukturen |
| **Analyse** | Angaben zu Datenanalysemoeglichkeiten (Dimensionen, Kennzahlen, Mining-Algorithmen, Berichtsdefinitionen, Verantwortlichkeiten) |
| **Organisationsbezug** | Verknuepfung der Datenbank-Konstrukte mit Organisationsstruktur (Berechtigungen, Datenverwender, Vertraulichkeitsstufen) |
| **Qualitaet** | Messung der Datenqualitaet (Interpretierbarkeit, Nuetzlichkeit, Glaubwuerdigkeit, zeitlicher Bezug, Verfuegbarkeit) |
| **Struktur/Bedeutung** | Benennung und Beschreibung von Datenstrukturelementen (Name, Typ, Datentyp, Speicherelementgroesse, Ersteller, Erstelldatum, Verwendungszweck) |
| **Systembezug** | Angaben zum Informationssystem (Softwarekomponente, Version, Hersteller, Rechnername, technische Details) |
| **Transformation** | Spezifizierung von Datentransformationsprozessen (Transformationsschritte, Verwendungszweck, Ausfuehrungsprotokoll) |
| **Metadatenhistorie** | Festhalten von Veraenderungen der Metadaten (Version, Aenderungsbeschreibung, Aenderungsdatum, Aenderungsgrund, Verantwortlicher) |

### Definition: Metadatenmanagement

„Metadatenmanagement bezeichnet die Gesamtheit der Prozesse zur zielgerichteten Erzeugung, Bereitstellung, Verwaltung und Nutzung von Metadaten." (Melchert, 2004)

### Organisatorische Gestaltung des Metadatenmanagements (nach Auth)

Zwei Hauptprozesse: **Metadatennutzung** und **Metadatenmanagement**.

**Metadatennutzung:**
- **Anwendung** (Fachabteilungen, Datenanalyse)
- **Entwicklung** (Systementwicklung, technische Metadaten)

**Metadatenmanagement (vier Hauptprozesse):**
1. **Datenqualitaetsmanagement**: Qualitaetsplanung, Qualitaetslenkung, Qualitaetsrueckkopplung, Qualitaetsverbesserung
2. **Datenstrukturmanagement**: Bereinigung, Entwicklung, Migration
3. **Terminologiemanagement**: Neuerfassung, Wiederverwendung, Aenderung, Bereinigung von Terminologien
4. **Datenkontextmanagement**: Kontextplanung, Kontextbereitstellung

---

### Definition: Datenqualitaet

Nach Wuerthele: „Datenqualitaet ist ein mehrdimensionales Mass fuer die Eignung von Daten, den an ihre Erfassung/Generierung gebundenen Zweck zu erfuellen. Diese Eignung kann sich ueber die Zeit aendern, wenn sich die Beduerfnisse aendern" (Wuerthele, 2003).

Nach English (1999): Qualitaet der Daten wird anhand der Beduerfnisse der **Kunden** und **Wissensverarbeiter** beurteilt. Ein Wissensverarbeiter ist eine Person, die die Daten zur Ausuebung ihrer Haupttaetigkeit nutzen muss.

**Konsistenz** ist ein Hauptproblem: Daten sind konsistent, wenn abgerufene Informationen unabhaengig von der Quelle gleich sind.

### Datenqualitaetskriterien nach Wang und Strong (1996)

Vier Kategorien mit zugeordneten Qualitaetseigenschaften:

| Kategorie | Qualitaetseigenschaften | Beschreibung |
|-----------|------------------------|-------------|
| **Intrinsische Datenqualitaet** | Glaubwuerdigkeit, Genauigkeit, Objektivitaet, Reputation | Qualitaet der Daten an sich; z. B. Korrektheit, Unvoreingenommenheit, Vertrauen in Datenquelle |
| **Kontextabhaengige Datenqualitaet** | Mehrwert, Relevanz, Aktualitaet, Vollstaendigkeit, angemessene Menge | Qualitaet hinsichtlich der Anforderungen aus Fragestellung/Kontext; z. B. Nutzen, Hilfe bei Aufgaben, Alter der Daten, realistische Nachbildung der Realwelt |
| **Darstellungsqualitaet** | Interpretierbarkeit, Verstaendlichkeit, konsistente Darstellung, knappe Darstellung | Qualitaet hinsichtlich Darstellung; z. B. sprachliche Verstaendlichkeit, Eindeutigkeit, Kompatibilitaet, uebersichtliche Kompaktheit |
| **Zugangsqualitaet** | Verfuegbarkeit, Zugriffssicherheit | Daten erreichbar und vor unbefugtem Zugang geschuetzt |

---

## Modelle / Frameworks / Verfahren

### Datenqualitaetsmanagement (Plan-Do-Check-Act nach Deming, modifiziert)

Regelkreis nach Apel et al. (2009):
1. **Planen**: Qualitaetskriterien definieren und Sollwerte festlegen
2. **Ausfuehren (Do)**: Ist-Werte der Datenqualitaetskriterien ermitteln
3. **Ueberpruefen (Check)**: Ist-Werte mit Soll-Richtwerten abgleichen
4. **Verbessern (Act)**: Bei Abweichungen Annaeherung des Ist-Wertes an den Soll-Wert

### Total Quality Management-Konzept nach English (1999)

Fuenf Phasen:

| Phase | Bezeichnung | Beschreibung |
|-------|-------------|-------------|
| 1 | **Datendefinition und Informationsarchitektur** | Standards und Kriterien festlegen, wonach Daten vorgehalten und bereitgestellt werden |
| 2 | **Beurteilung der Informationsqualitaet** | Informationsgruppen identifizieren/bestaetigen; Eigenschaften der Datenqualitaet ableiten (Aktualitaet, Genauigkeit, Vollstaendigkeit) |
| 3 | **Messung der Kosten** | Kosten durch unzureichende Qualitaet messen (Kundenzufriedenheit, Gewinne, Kostenreduktion); schlechte Qualitaet fuehrt zu Kundenabwanderung und verlorenen Ertraegen |
| 4 | **Datenueber­arbeitung und -bereinigung** | Zwei Teilphasen: (a) Datenquellen identifizieren, Ursachen erkennen, Daten korrigieren/vervollstaendigen, Redundanzen beheben; (b) Daten transformieren, zusammenfassen, ETL in DWH/Data Mart |
| 5 | **Verbesserung der Informationsprozessqualitaet** | Ursachen erkennen, Prozessveraenderungen implementieren; langfristige Verbesserung der Informationsqualitaet |

### Drei Strategien zur Verbesserung der Datenqualitaet (nach Redman 1995)

| Strategie | Beschreibung |
|-----------|-------------|
| **Fehlererkennung und -korrektur** | Bestehende Fehler erkennen und korrigieren |
| **Prozessmanagement** | Direkt bei Fehlerursache ansetzen: Verantwortlichkeitsbereich definieren, Kundenanforderungen und Prozesse definieren, Messgroessen festlegen, Ueberwachung, Prozessanalyse, Verbesserung |
| **Prozessdesign** | Prozesse weniger fehleranfaellig machen; z. B. durch Einbindung von IT (Automatisierung, Lesegeraete); langfristig oft die bessere Alternative |

### Fuenf Schritte zur nachhaltigen Verbesserung der Datenqualitaet

1. Datenqualitaetsprobleme identifizieren (Kosten-Nutzen-Betrachtung)
2. Ziel-/Richtwerte fuer Datenqualitaetskriterien festlegen
3. Analyse der aufgetretenen Probleme, Gruende erkennen und in Prozessen identifizieren
4. Fehler verursachenden Prozess veraendern
5. Veraenderungen bewerten und ueberpruefen

---

### DWH-Gesamtarchitektur (5 Ebenen nach Sinz et al. 2001)

| Ebene | Komponenten | Beschreibung |
|-------|-------------|-------------|
| **Ebene der operativen Systeme** (vorgelagert, nicht Teil des DWH-Systems) | Operative Datenquellen, externe Datenquellen | Verschiedene Datenquellen, die Daten in das DWH-System einspeisen |
| **Datenerfassungsebene** | Arbeitsbereich (staging area), ETL-Komponente | Schnittstelle zu operativen Systemen; Daten werden physisch in DWH-System gebracht; Bereinigung, Harmonisierung, Zusammenfuehrung |
| **Datenhaltungsebene** | Data Warehouse, Operational Data Store (ODS) | Basisschicht (Tabellen direkt aus Quellsystemen) und Aggregationsschicht (fuer OLAP-Anfragen optimiert) |
| **Datenbereitstellungsebene** | Analysekomponenten (u. a. OLAP) | Zweckmaessige Aufbereitung der Informationen fuer Entscheidungstraeger |
| **Praesentationsebene** (nicht mehr Teil des eigentlichen DWH-Systems) | Data Mining, Tabellenkalkulationsprogramme, Data Access | Adaequate Aufbereitung und Praesentation der Daten; Ueberwachung von Erfolgsgroessen |

Die Architektur wird auch als **Speichenarchitektur** (Hub and Spoke Architecture) bezeichnet.

### Definition: Data Warehouse (nach Inmon)

„A subject-oriented, integrated, nonvolatile, and time-variant collection of data in support of management's decisions" (Inmon, 2000).

### SINT-Eigenschaften eines DWH

| Eigenschaft | Englisch | Beschreibung |
|-------------|----------|-------------|
| **Themenorientierung** | Subject-oriented | Daten werden themenorientiert gehalten (z. B. Kunden, Produkte, Mitarbeiter), nicht an Applikationen orientiert |
| **Integration** | Integrated | Daten aus verschiedenen Datenquellen werden integriert; Herausforderung: unterschiedliche Kodierungen und Massangaben in verschiedenen Applikationen |
| **Nicht-Volatilitaet** | Nonvolatile | Daten werden dauerhaft vorgehalten und nicht ueberschrieben; einmal abgelegte Daten bleiben erhalten; alte und neue Werte koexistieren |
| **Zeitraumbezug** | Time-variant | Daten werden zeitraumbezogen (nicht zeitpunktbezogen) abgelegt; Zeithorizont von 5-10 Jahren; mittlerweile teilweise durch **Granularitaet** ersetzt |

### Drei Funktionen des DWH

1. **Sammel-/Integrationsfunktion**: Daten aus verschiedenen Quellen zentral sammeln und bereitstellen
2. **Distributionsfunktion**: Gesammelte Daten an das DWH-System im Unternehmen verteilen
3. **Auswertungsfunktion**: Einzelne Analysen der gesammelten Daten durchfuehren

### Ziele eines DWH

- Daten effizient fuer Auswertungen und Analysen bereitstellen (Behme & Muksch, 2001)
- Geschaeftsprozesse unterstuetzen und zur Strategieerreichung beitragen
- Abschaffung von Inselloesungen (Totok, 2000)

### Operative vs. dispositive Daten

| Eigenschaft | Dispositive Daten | Operative Daten |
|-------------|-------------------|-----------------|
| **Ziel** | Entscheidungsunterstuetzung | Unterstuetzung des Tagesgeschaefts |
| **Zustand** | Kontrollierte Redundanzen und konsistent | Haeufig redundant und inkonsistent |
| **Modellierung** | Sachgebiets- und themenorientiert | Funktions-/transaktionsorientiert |
| **Zeitbezug** | Historienbetrachtung ueber den Zeitverlauf | Aktuell, zeitpunktbezogen |
| **Ausrichtung** | Meist verdichtet, transformiert | Detaillierte, granulare Geschaeftsvorfalldaten |
| **Ebene** | Managementebene | Abteilungsebene |

---

### Komponenten eines DWH-Systems

#### 1. Data Warehouse (DWH)
Kern des DWH-Systems mit drei Funktionen (Sammel-, Distributions-, Auswertungsfunktion).

#### 2. Operational Data Store (ODS)

Nach Inmon: „Ein ODS ist eine themenorientierte, integrierte, nicht dauerhafte bzw. nicht persistente detaillierte Sammlung von Daten, um eine Organisationseinheit bei ihrem Bedarf nach aktuellen, betrieblichen, integrierten und ganzheitlichen Informationen zu unterstuetzen."

Eigenschaften:
- Datenbank zur Integration von Daten aus einer oder mehreren Datenquellen
- Daten werden fuer **zeitnahe Auswertungen** bereitgestellt, die in Quellsystemen nicht/schwer moeglich sind
- Ermoeglicht **transaktionsorientierte und integrierte Datenhaltung**
- Beispiel: Angebotserstellung in Abhaengigkeit zeitnaher Boersenkurse

#### 3. Arbeitsbereich (Staging Area)
- Temporaere Zwischenspeicherung von Daten
- Verhindert Beeintraechtigung von DWH und Datenquellen im laufenden Betrieb
- Zentrale Komponente des Datenbeschaffungsbereichs
- Daten werden nach Regeln transformiert und integriert
- Nach Laden in DWH werden Daten aus dem Arbeitsbereich geloescht

#### 4. ETL-Komponente (Extraktion - Transformation - Laden)

**Extraktion:**
- Daten von Datenquelle in Arbeitsbereich uebertragen
- Zwei Faktoren: Beschaffenheit der Daten und Relevanz der Daten
- Soll moeglichst automatisiert erfolgen
- Vier Vorgehensweisen:

| Extraktionsart | Beschreibung | Beispiel |
|----------------|-------------|----------|
| **Periodisch** | In regelmaessig festgesetzten Zeitraeumen | Verkaufsdaten jeden Abend |
| **Anfragegesteuert** | Durch einen Anstoss bei wichtiger Veraenderung | Neues Produkt im Sortiment |
| **Ereignisgesteuert** | Automatisch bei bestimmter Anzahl Aenderungen oder Grenzwert | Bestimmte Umsatzgrenze erreicht |
| **Sofort nach Veraenderung** | Daten im DWH immer aktuell; sehr aufwaendig | Veraenderung von Boersenkursen |

**Transformation:**
- Anpassung der Daten fuer DWH-Ladung
- Standardisierung (Zeichenketten, Kodierungen)
- Bereinigung fehlerhafter Daten
- Loeschung redundanter/veralteter Daten

**Laden:**
- Zwei Ladephasen:
  - **Initiales Laden (Initial Load)**: Einmalige Ladung der Daten von Quellsystemen in DWH
  - **Aktualisierung (Refresh)**: Regelmaessige Auffrischung; zeitintensiv, daher oft ausserhalb der Auslastungshoehen (Wochenende, nachts)
- Daten werden nach Laden nicht geloescht, sondern im DWH gehalten (Historisierung)

#### 5. Metadatenbanksystem (Business Data Directory)
- Liefert dem DWH Hintergrundinformationen ueber Datenquellen, Transformationen und Verdichtungen
- Zwei Informationsarten: datenverarbeitungstechnische und betriebswirtschaftliche
- Ziel: Transparenz schaffen und Mitarbeiter unterstuetzen

Zwei Komponenten:
- **Informationskatalog**: Informationsobjekte (Grafiken, Tabellen, Texte, Abfragen, Programme, Dateien) verstaendlich beschrieben
- **Navigationshilfe (Browser)**: Unterstuetzung bei Suche, Recherche und Analyse in Metadaten

Weitere bereitzustellende Informationen: Lexikon, Thesaurus, Datenstrukturverzeichnis, Glossar, Data Directory

#### 6. Analysekomponente
Werkzeuge zur Unterstuetzung der Datenauswertung:
- **Data Mining** (vgl. Einheit 2)
- **Data Access**: Berichtswerkzeuge, die Daten lesen und einfache Operationen durchfuehren; Ampelfunktion (Rot/Gelb/Gruen fuer verschiedene Groessen)
- **OLAP-Verfahren** (s. unten)
- **Data Marts** (s. unten)

---

### Data Marts

Data Marts sind „spezielle analyseorientierte Systeme mit einer Ausrichtung auf das jeweilige Anwendungsthema" (Farkisch, 2011). Sie entsprechen kleinen autonomen DWHs mit eigener Datenhaltung in Form einer spezialisierten analytischen Datenbank, zugeschnitten auf Fachbeduerfnisse bestimmter Benutzergruppen.

### Vergleichstabelle: Data Marts vs. Data Warehouses

| Eigenschaft | Data Mart | Data Warehouse |
|-------------|-----------|----------------|
| **Adressat** | Abteilung | Unternehmen |
| **Anzahl** | Mehrere bis viele | Eins bis sehr wenige |
| **Detaillierungsgrad** | Zumeist hoeher aggregierte Daten | Kleinster Grad der Detaillierung |
| **Datenmenge** | Niedrig | Hoch |
| **Menge historischer Daten** | Niedrig | Hoch |
| **Einfluss externer Datenquellen** | Zumeist nicht gegeben; wenn, dann nur spezifischer Ausschnitt | Hoch; saemtliche verfuegbaren externen Datenquellen werden integriert |
| **Direkter Zugriff durch Endanwender** | In der Regel moeglich | Haeufig nicht erlaubt; zentraler Betrieb durch IT-Abteilung |
| **Modellierungskonventionen** | Heterogen (proprietaere Data Marts) bzw. einheitlich (abgeleitete Data Marts) | Einheitlich |
| **Freiheitsgrad der Analysen** | Eher gering (Anwender kann ueber Abteilungsgrenzen nicht hinaussehen) | Flexibel; saemtliche zugaengliche Informationen koennen einfliessen |
| **Betriebswirtschaftliches Ziel** | Effiziente Unterstuetzung der Entscheider einer Abteilung | Effiziente Managementunterstuetzung durch strategische, taktische und operative Informationsobjekte |

### Vorteile von Data Marts

- Autonomer Zugriff der Abteilungen auf benoetigte Daten (hohe Flexibilitaet)
- Geringere Rechnerleistung erforderlich, geringere Anschaffungs- und Betriebskosten
- Datenmodelle anpassbar an fachliche, organisatorische und technische Gegebenheiten
- Geringeres Datenvolumen durch Fokus auf eine Abteilung
- Vereinfachte Wartung und schnellere Zugriffszeiten
- Schnelle und kostenguenstige Einrichtung
- Optimierung hinsichtlich Antwortzeit und Abfragefreundlichkeit

### Nachteile von Data Marts

- Qualitaetssicherungs-, Konsolidierungs- und Historisierungsmassnahmen fuer jedes einzelne Data Mart erforderlich
- Redundante Datenhaltung an verschiedenen Orten
- Hoehere Netzbelastung
- Nur beschraenkte Sicht auf Daten; keine unternehmensweite Sicht; abteilungsuebergreifende Analysen nur schwer moeglich

---

### Online Analytical Processing (OLAP)

Nach Gluchowski/Dittmar/Gabriel: OLAP ist „eine Software-Technologie, die Managern wie auch qualifizierten Mitarbeitern aus den Fachabteilungen schnelle, interaktive und vielfaeltige Zugriffe auf relevante und konsistente Informationen ermoeglichen sollen. Im Vordergrund stehen dabei dynamische und multidimensionale Analysen auf historischen, konsolidierten Datenbestaenden" (Gluchowski, Dittmar, & Gabriel, 2008).

Urspruenglich entwickelt von Codd et al. 1993. Darstellung klassischerweise als **OLAP-Wuerfel** (fuer 3 Dimensionen). Alternative Darstellungen: **Pivottabellen** und **Rechenschiebermodelle**.

### Eigenschaften von OLAP (aus der Abkuerzung)

| Buchstabe | Eigenschaft | Beschreibung |
|-----------|-------------|-------------|
| **O** | Online | Anwender koennen direkt auf zentralen Datenbestand zugreifen |
| **A** | Analytical | Unterschiedliche Sichten fuer Entscheidungstraeger (im Gegensatz zu OLTP: Geschaeftsvorfaelle) |
| **P** | Processing | Schnelle Berechnungen und Manipulationen durch Anwender |

### Zwoelf Regeln nach Codd (1993)

| Nr. | Regel | Beschreibung |
|-----|-------|-------------|
| 1 | **Multidimensionale konzeptionelle Sichtweise** | Multidimensionale Analyse, Aggregation und Korrelation von Daten; visualisierte Ergebnisse |
| 2 | **Transparenz** | Abfragen ohne Kenntnis der zugrundeliegenden Datenstrukturen |
| 3 | **Zugriffsmoeglichkeit** | Analysen auf Basis interner und externer Datenquellen |
| 4 | **Gleichbleibende Antwortzeit** | Antwortzeit unabhaengig von Dimensionsanzahl oder Datensatzanzahl |
| 5 | **Client-Server-Architektur** | Trennung von Speicherung, Verarbeitung und Darstellung; offene Schnittstelle |
| 6 | **Generische Dimensionalitaet** | Alle Dimensionen einheitlich in Struktur und Funktionalitaet; symmetrisch; austauschbar (kritisiert: z. B. Zeit sollte vorbelegt sein koennen) |
| 7 | **Dynamische Behandlung unvollstaendig besetzter Matrizen** | Funktionalitaet nicht eingeschraenkt bei fehlenden Werten in Kombinationen |
| 8 | **Mehrbenutzerunterstuetzung** | Paralleler Zugriff mehrerer Benutzer; Konsistenz; Rechteverwaltung (Lese-/Schreibrechte) |
| 9 | **Uneingeschraenkte kreuzdimensionale Operationen** | Alle Berechnungen unabhaengig von Dimensionen und ueber beliebige Dimensionen hinweg |
| 10 | **Intuitive Darstellung und Bearbeitung** | Selbststaendige Analyse ohne groessere Systemkenntnisse; intuitive Navigation |
| 11 | **Flexible Berichterstellung** | Flexible Anordnung; Berichtselemente frei positionierbar |
| 12 | **Unbegrenzte Anzahl von Dimensionen und Klassifikationsebenen** | Beliebige Dimensionsanzahl; Praxis: 5-8 Dimensionen; 15-20 gleichzeitig sollten reichen |

### Sechs zusaetzliche Regeln (Erweiterung durch Codd)

| Nr. | Regel | Beschreibung |
|-----|-------|-------------|
| 1 | **Datenintegration** | Zugriff auf eigene multidimensionale Datenstruktur und darunterliegende Daten |
| 2 | **Unterstuetzung verschiedener Analysemodelle** | Vier Datenmodelle: kategorisch (historisch vs. aktuell), exegetisch (Ursachenermittlung), kontemplativ (Simulation), formelbasiert (Zielzustand erreichen) |
| 3 | **Trennung analyseorientierter von operativen Daten** | Veraenderungen im DWH duerfen nicht ins Quellsystem uebernommen werden |
| 4 | **Trennung der Speicherorte** | Veraenderungen nicht auf produktivem Datenbestand speichern |
| 5 | **Unterscheidung Null- und Fehlwerte** | Fehlende Werte und numerischer Wert 0 muessen unterscheidbar sein |
| 6 | **Behandlung fehlender Werte** | Effiziente Verwaltung fuer optimale Speicherkapazitaet |

### FASMI-Prinzip (Pendse und Creeth 1995)

FASMI = **F**ast **A**nalysis of **S**hared **M**ultidimensional **I**nformation

| Eigenschaft | Beschreibung |
|-------------|-------------|
| **Fast (Geschwindigkeit)** | Anfragen in unter 5 Sekunden beantwortet; haeufige Anfragen schneller, komplexere laenger |
| **Analysis (Analysemoeglichkeit)** | Intuitive, benutzerfreundliche Analyse; einfache Funktionen fuer eigene Berechnungen; extern eingebundene oder eigene Funktionen |
| **Shared (Sicherheit)** | Mehrere Anwender koennen gleichzeitig auf dieselben Daten zugreifen |
| **Multidimensional (Multidimensionalitaet)** | Mehrere Dimensionen nach Beduerfnissen miteinander verbinden und analysieren |
| **Information (Kapazitaet)** | Sehr grosse Datenmengen zur Analyse; Antwortzeiten muessen stabil bleiben unabhaengig von Anfragenanzahl und Datenmenge |

### OLAP-Auspraegungen

| Auspraegung | Basis | Beschreibung | Vorteile | Nachteile |
|-------------|-------|-------------|----------|-----------|
| **ROLAP** (Relational OLAP) | Relationale DBMS (Star-Schema, Snowflake-Schema) | Multidimensionale Sichten werden dynamisch erzeugt; Dimensionstabellen und Faktentabellen | Grosse Datenvolumina; flexible Dimensionsanzahl; vorhandenes Know-How; robuste Technologie; keine Vorberechnungen noetig | Langsameres Antwortverhalten als MOLAP |
| **MOLAP** (Multidimensional OLAP) | Mehrdimensionale Datenbanken | Daten physisch in mehrdimensionalen Datenbanken gespeichert | Schnelleres Antwortverhalten | Hoeheres Datenvolumen; begrenzte Dimensionsanzahl; weniger flexibel; hoher Vorberechnungsaufwand; nur fuer kleinere Datenmengen empfehlenswert |
| **HOLAP** (Hybrid OLAP) | Kombination ROLAP + MOLAP | Versucht Vorteile beider zu kombinieren und Nachteile zu eliminieren | Kombination der Vorteile | - |

### Star-Schema (ROLAP)

- **Faktentabelle** in der Mitte: enthaelt Bewegungsdaten; Schluessel weisen auf Dimensionstabellen
- **Dimensionstabellen** sternfoermig um die Faktentabelle: enthalten Stammdaten
- Dimensionen werden durch Eigenschaften charakterisiert (z. B. Produkt_ID -> Artikelnummer, Produktgruppe, Produktfamilie)

### OLAP vs. OLTP

| Eigenschaft | OLAP | OLTP |
|-------------|------|------|
| **Zweck** | Analyse von Entscheidungen | Unterstuetzung des operativen Geschaefts |
| **Daten** | Historisch und aggregiert | Sehr aktuell und detailliert |
| **Operationen** | Multidimensionale Abfragen, Ad-hoc-Abfragen | Anlegen, Lesen, Aendern, Loeschen von Daten |

### OLAP-Operationen

| Operation | Beschreibung |
|-----------|-------------|
| **Pivotierung / Rotation** | OLAP-Wuerfel wird um horizontale oder vertikale Achse gedreht; betrachtete Dimensionen werden gegeneinander ausgetauscht; Datentiefe aendert sich nicht; in Tabellen durch Pivottabellen realisiert |
| **Roll-Up** | Staerkeres Zusammenfassen (Aggregieren) der Daten; Hierarchieebene wird „nach oben" verschoben (z. B. Staedte -> Bundeslaender -> Laender) |
| **Drill-Down** | Gegenteil von Roll-Up; Daten werden eine Hierarchieebene tiefer disaggregiert (z. B. Lebensmittel -> Gemuese, Fleisch, Konserven, Brot, Suesswaren) |
| **Slice** | Eine Dimension wird auf einen einzigen Wert reduziert, alle anderen Dimensionen behalten alle Werte; Ergebnis: eine „Scheibe" aus dem Wuerfel |
| **Dice** | Anwender waehlt einzelne Bloecke/Teilauswahl aus dem Gesamtwuerfel (z. B. zwei Produkte, zwei Regionen, zwei Kunden); Ergebnis: ein neuer, kleinerer Datenwuerfel |

---

## Definitionstabelle

| Begriff | Definition |
|---------|-----------|
| Business Rules | Richtlinien oder Geschaeftspraktiken, die das Verhalten eines Unternehmens beeinflussen oder leiten (Scheer/Werth 2006) |
| Business Motivation Model (BMM) | Modell der Business Rules Group, das den Zusammenhang zwischen Geschaeftsregeln, Geschaeftspolitik und Unternehmensstrategie abbildet |
| Metadaten | „Analyse der Daten ueber Daten" (Sen, 2004); charakterisiert durch Beziehungsmerkmal und Abstraktionsmerkmal |
| Metadatenmanagement | „Gesamtheit der Prozesse zur zielgerichteten Erzeugung, Bereitstellung, Verwaltung und Nutzung von Metadaten" (Melchert, 2004) |
| Datenqualitaet | „Mehrdimensionales Mass fuer die Eignung von Daten, den an ihre Erfassung/Generierung gebundenen Zweck zu erfuellen" (Wuerthele, 2003) |
| Wissensverarbeiter | Person, die Daten zur Ausuebung ihrer Haupttaetigkeit nutzen muss (English, 1999) |
| Konsistenz | Daten sind konsistent, wenn abgerufene Informationen unabhaengig von der Quelle gleich sind |
| Data Warehouse (DWH) | „A subject-oriented, integrated, nonvolatile, and time-variant collection of data in support of management's decisions" (Inmon, 2000) |
| SINT-Eigenschaften | Subject-oriented, Integrated, Nonvolatile, Time-variant (Eigenschaften eines DWH nach Inmon) |
| Operational Data Store (ODS) | Themenorientierte, integrierte, nicht dauerhafte, detaillierte Datensammlung fuer aktuelle, betriebliche, integrierte Informationen (Inmon) |
| Arbeitsbereich (Staging Area) | Temporaere Zwischenspeicherung von Daten vor Laden in DWH |
| ETL-Prozess | Extraktion - Transformation - Laden; Prozess zur Vereinheitlichung, Konsolidierung und Bereitstellung von Daten aus Quellsystemen im DWH |
| Metadatenbanksystem | Business Data Directory; liefert dem DWH Hintergrundinformationen ueber Datenquellen, Transformationen und Verdichtungen |
| Data Mart | Spezielle analyseorientierte Systeme mit Ausrichtung auf das jeweilige Anwendungsthema (Farkisch, 2011); kleine autonome DWHs fuer Fachabteilungen |
| Data Access | Berichtswerkzeuge, die Daten lesen, einfache Operationen durchfuehren und zu Praesentationszwecken aufbereiten (z. B. Ampelfunktion) |
| OLAP | Software-Technologie fuer schnelle, interaktive, vielfaeltige Zugriffe auf relevante, konsistente Informationen; dynamische, multidimensionale Analysen auf historischen, konsolidierten Datenbestaenden (Gluchowski/Dittmar/Gabriel, 2008) |
| OLTP | Online Transactional Processing; unterstuetzt operatives Geschaeft; aktuelle, detaillierte Daten; Operationen: Anlegen, Lesen, Aendern, Loeschen |
| FASMI | Fast Analysis of Shared Multidimensional Information (Pendse/Creeth, 1995); beschreibt fuenf OLAP-Eigenschaften |
| ROLAP | Relational OLAP; basiert auf relationalen DBMS; dynamisch erzeugte multidimensionale Sichten |
| MOLAP | Multidimensional OLAP; Daten physisch in mehrdimensionalen Datenbanken gespeichert |
| HOLAP | Hybrid OLAP; Kombination aus ROLAP und MOLAP |
| Star-Schema | Datenbankschema mit zentraler Faktentabelle und sternfoermig angeordneten Dimensionstabellen |
| Pivotierung/Rotation | OLAP-Operation: Wuerfel um Achse drehen, Dimensionen austauschen |
| Roll-Up | OLAP-Operation: Daten staerker aggregieren (Hierarchie aufwaerts) |
| Drill-Down | OLAP-Operation: Daten weiter disaggregieren (Hierarchie abwaerts) |
| Slice | OLAP-Operation: Eine Dimension auf einen Wert reduzieren (Scheibe aus Wuerfel) |
| Dice | OLAP-Operation: Teilblock/Teilwuerfel aus Gesamtwuerfel auswaehlen |
| Geschaeftspolitik | Wenig strukturiert, abstrakt, kein Standardvokabular, nicht automatisierbar; Basis fuer Business Rules |
| Operative Daten | Daten zur Unterstuetzung des Tagesgeschaefts; aktuell, detailliert, funktionsorientiert |
| Dispositive Daten | Daten zur Entscheidungsunterstuetzung; verdichtet, transformiert, themenorientiert, historisch |
| Hub-and-Spoke-Architektur | Speichenarchitektur; DWH als zentrale Datendrehscheibe mit angeschlossenen Quell- und Analysesystemen |
| Business Rules Mining | Verfahren aehnlich Data Mining/Rule Induction; durchschuerft Systemverhalten zur Ableitung von Business Rules |

---

## Querverweise

- Siehe auch: wissen/01_grundlagen_bi.md -- Operative vs. dispositive Daten wurden dort bereits eingefuehrt; DWH-Systeme als Bestandteil der BI-Gesamtarchitektur
- Siehe auch: wissen/02_methoden_instrumente.md -- KDD-Prozess als Rahmen fuer Datenhaltung; Data Mining-Verfahren werden als Analysekomponente im DWH-System genutzt; Datenselektion und Datentransformation im KDD-Prozess korrespondieren mit ETL-Prozess

---

## Typische Pruefungsfragen

### Frage 1: Erlaeutern Sie die SINT-Eigenschaften eines Data Warehouse nach Inmon!

**Musterloesung:**
SINT steht fuer Subject-oriented, Integrated, Nonvolatile, Time-variant.
- **Themenorientierung (S):** Daten werden nach Themen wie Kunden, Produkte oder Mitarbeiter gehalten, nicht an Applikationen orientiert.
- **Integration (I):** Daten aus verschiedenen Datenquellen werden in ein einheitliches Format integriert. Herausforderung: unterschiedliche Kodierungen (z. B. Geschlecht als „m/w", „1/0" oder „maennlich/weiblich") und Massangaben muessen vereinheitlicht werden.
- **Nicht-Volatilitaet (N):** Daten werden dauerhaft vorgehalten und nicht ueberschrieben. Alte Werte bleiben erhalten, neue Daten werden zusaetzlich hochgeladen.
- **Zeitraumbezug (T):** Daten werden ueber einen Zeitraum von 5-10 Jahren zeitraumbezogen abgelegt, nicht zeitpunktbezogen wie in operativen Systemen. Diese Eigenschaft wird mittlerweile teilweise durch Granularitaet ersetzt.

### Frage 2: Nennen und erlaeutern Sie die drei Phasen des ETL-Prozesses!

**Musterloesung:**
- **Extraktion:** Daten werden von den Datenquellen in den Arbeitsbereich (Staging Area) uebertragen. Dabei muessen Beschaffenheit und Relevanz der Daten beruecksichtigt werden. Die Extraktion kann periodisch, anfragegesteuert, ereignisgesteuert oder sofort nach Veraenderung erfolgen.
- **Transformation:** Daten werden an das Format des DWH angepasst. Dies umfasst Standardisierung (z. B. Vereinheitlichung von Zeichenketten, Konvertierung von Kodierungen), Bereinigung fehlerhafter Daten und Loeschung redundanter/veralteter Daten.
- **Laden:** Daten werden in das DWH uebertragen. Unterschieden wird das initiale Laden (einmalig zur Initialisierung) und die regelmaessige Aktualisierung (Refresh). Der Ladevorgang ist zeitintensiv und erfolgt oft ausserhalb der Auslastungshoehen.

### Frage 3: Grenzen Sie ROLAP, MOLAP und HOLAP voneinander ab!

**Musterloesung:**
- **ROLAP** basiert auf relationalen Datenbankmanagementsystemen und erzeugt multidimensionale Sichten dynamisch (z. B. Star-Schema). Vorteile: grosse Datenvolumina, flexible Dimensionsanzahl, vorhandenes Know-How, keine Vorberechnungen noetig.
- **MOLAP** speichert Daten physisch in mehrdimensionalen Datenbanken. Vorteil: schnelleres Antwortverhalten. Nachteile: hoeheres Datenvolumen, begrenzte Dimensionsanzahl, hoher Vorberechnungsaufwand; nur fuer kleinere Datenmengen empfehlenswert.
- **HOLAP** kombiniert ROLAP und MOLAP, um die Vorteile beider Ansaetze zu vereinen und die jeweiligen Nachteile zu eliminieren.

### Frage 4: Erlaeutern Sie die vier Datenqualitaetskategorien nach Wang und Strong (1996)!

**Musterloesung:**
- **Intrinsische Datenqualitaet:** Qualitaet der Daten an sich (Glaubwuerdigkeit, Genauigkeit, Objektivitaet, Reputation). Beispiel: Sind die Daten korrekt und stammen sie aus einer vertrauenswuerdigen Quelle?
- **Kontextabhaengige Datenqualitaet:** Qualitaet hinsichtlich des Verwendungskontexts (Mehrwert, Relevanz, Aktualitaet, Vollstaendigkeit, angemessene Menge). Beispiel: Sind die Daten aktuell genug fuer die anstehende Entscheidung?
- **Darstellungsqualitaet:** Qualitaet der Darstellung (Interpretierbarkeit, Verstaendlichkeit, konsistente Darstellung, knappe Darstellung). Beispiel: Werden die Daten immer im gleichen Format ausgegeben?
- **Zugangsqualitaet:** Verfuegbarkeit und Zugriffssicherheit. Beispiel: Sind die Daten fuer befugte Personen erreichbar und vor unbefugtem Zugriff geschuetzt?

### Frage 5: Grenzen Sie Data Marts und zentrale Data Warehouses anhand von mindestens fuenf Merkmalen voneinander ab!

**Musterloesung:**
1. **Adressat:** Data Marts richten sich an einzelne Abteilungen, ein DWH an das gesamte Unternehmen.
2. **Anzahl:** Es gibt mehrere bis viele Data Marts, aber nur ein zentrales DWH.
3. **Datenmenge und Detaillierungsgrad:** Data Marts haben ein geringeres Datenvolumen mit hoeher aggregierten Daten; das DWH hat ein hohes Datenvolumen mit kleinstem Detaillierungsgrad.
4. **Zugriff:** Bei Data Marts koennen Endanwender in der Regel direkt zugreifen; beim DWH ist dies haeufig nur der IT-Abteilung vorbehalten.
5. **Freiheitsgrad:** Data Marts bieten eingeschraenkte Analysen (nur abteilungsintern); das DWH ermoeglicht flexible, unternehmensweite Analysen.
6. **Externe Datenquellen:** Bei Data Marts meist nicht integriert; beim DWH werden alle verfuegbaren externen Quellen integriert.

### Frage 6: Erlaeutern Sie die fuenf OLAP-Operationen Pivotierung, Roll-Up, Drill-Down, Slice und Dice!

**Musterloesung:**
- **Pivotierung/Rotation:** Der OLAP-Wuerfel wird um eine Achse gedreht, sodass betrachtete Dimensionen gegeneinander ausgetauscht werden. Die Datentiefe aendert sich nicht.
- **Roll-Up:** Daten werden staerker aggregiert, indem die Hierarchieebene nach oben verschoben wird (z. B. von Staedten zu Bundeslaendern).
- **Drill-Down:** Gegenteil von Roll-Up; Daten werden weiter disaggregiert, indem die Hierarchieebene nach unten verschoben wird (z. B. von Lebensmitteln zu Gemuese, Fleisch etc.).
- **Slice:** Eine Dimension wird auf genau einen Wert reduziert, waehrend alle anderen Dimensionen vollstaendig erhalten bleiben. Ergebnis ist eine „Scheibe" des Wuerfels.
- **Dice:** Aus dem Gesamtwuerfel wird ein Teilblock mit eingeschraenkten Werten in mehreren Dimensionen ausgewaehlt. Ergebnis ist ein neuer, kleinerer Datenwuerfel.

### Frage 7: Was besagt das FASMI-Prinzip und welche Anforderungen leiten sich daraus fuer OLAP ab?

**Musterloesung:**
FASMI steht fuer Fast Analysis of Shared Multidimensional Information (Pendse/Creeth, 1995) und beschreibt fuenf Anforderungen an OLAP:
- **Fast:** Anfragen sollen in unter 5 Sekunden beantwortet werden.
- **Analysis:** Intuitive, benutzerfreundliche Analysemoeglichkeiten mit einfachen Funktionen.
- **Shared:** Mehrere Anwender koennen gleichzeitig auf dieselben Daten zugreifen.
- **Multidimensional:** Mehrere Dimensionen koennen nach Beduerfnissen miteinander kombiniert werden.
- **Information:** Grosse Datenmengen mit stabilen Antwortzeiten unabhaengig von Anfragenanzahl und Datenmenge.

---

## Tags

`#einheit3` `#datenhaltung` `#datenbereitstellung` `#DWH` `#DataWarehouse` `#ETL` `#OLAP` `#ROLAP` `#MOLAP` `#HOLAP` `#DataMart` `#ODS` `#SINT` `#FASMI` `#BusinessRules` `#BMM` `#Metadaten` `#Metadatenmanagement` `#Datenqualitaet` `#WangStrong` `#TQM` `#Codd` `#Pivotierung` `#DrillDown` `#RollUp` `#Slice` `#Dice` `#StarSchema`
