# 01 - Grundlagen der Business Intelligence

> **Quelle:** 32711-01-S#1-S002664941.pdf (54 Seiten) | **Pruefungsrelevanz:** HOCH

## Ueberblick

Diese Einheit legt die begrifflichen und konzeptionellen Grundlagen fuer Business Intelligence. Sie zeigt, dass BI weit mehr als Software ist — ein ganzheitliches Konzept, das Entscheidungsprozesse, organisatorische Strukturen, Entscheidungstraeger und technische Architektur integriert. Zentral sind die Entwicklung des BI-Begriffs (Luhn 1958 bis heute), die Systematisierung von Entscheidungsprozessen (formale und handlungsorientierte Modellierung) sowie die Einordnung in das betriebliche Informationsmanagement ueber das Comprehensive Decision Model (CDM).

---

## Kernkonzepte

### Definition: Business Intelligence (BI)
Business Intelligence ist die an einem Entscheidungsproblem orientierte Analyse und adressatengerechte, technikgestuetzte Bereitstellung von wettbewerbsrelevanten Informationen mit dem Ziel, den Entscheidungsprozess zu unterstuetzen. BI umfasst die zur Entscheidungsunterstuetzung eingesetzten Konzepte, Methoden und Informationssysteme.

### Definition: Business-Intelligence-Systeme
Nach Hummeltenberg (2019) sind BI-Systeme informationsgetriebene Entscheidungsunterstuetzungssysteme zur Gewinnung und Verbreitung von Erkenntnissen fuer und ueber betriebliche Ablaeufe.

### Definition: Data Warehouse (DWH)
Eine unternehmensweite Datenbank, die als zentraler Speicher eine einheitliche und konsistente Datenbasis zur Entscheidungsunterstuetzung aller Bereiche und Ebenen im Unternehmen bietet und unabhaengig von operativen Anwendungssystemen betrieben wird. Im DWH werden alle relevanten internen und externen Daten zusammengefuehrt und fuer verschiedenartige Auswertungen und Analysen fuer laengere Zeitraeume gespeichert (Hansen und Neumann 2019).

### Definition: Data Marts
Ein aggregierter Teilausschnitt des Data Warehouse, der die relevanten Daten fuer einen bestimmten abgegrenzten Themen- und/oder Anwenderkreis enthaelt. Data Marts beinhalten z.B. die Daten der einzelnen Geschaeftsprozesse (Kemper et al. 2010; Kimball und Ross 2011).

### Definition: Data Mining (DM)
Softwaregestuetzte Ermittlung bisher unbekannter Zusammenhaenge, Muster, Regeln und Trends in umfangreichen Datenbestaenden, die bei der Unterstuetzung der Entscheidungsfindung und bei der Prognose von zukuenftigen Ereignissen helfen koennen (Hansen und Neumann 2019).

### Definition: Online Analytical Processing (OLAP)
Ein Ansatz, um Daten eines Data Warehouse nach mehreren Dimensionen zu analysieren. "Online" steht fuer eine Just-in-time-Bereitstellung der Daten. Im Gegensatz zu Managementunterstuetzungsverfahren ist OLAP auf die Analyse sehr grosser Datenvolumina ausgerichtet.

### Definition: Betriebliches Informationsmanagement (BIM)
Der gesamte informationsverarbeitende Teilbereich einer Organisation, bestehend aus Menschen, der Aufbau- und Ablauforganisation, der IT sowie allen Kommunikationsverbindungen.

### Definition: Daten
Syntaktisch geordnete Wahrnehmungen ueber verschiedene Dinge und Sachverhalte, die in gedruckter, gespeicherter, visueller, akustischer oder sonstiger Form vorliegen (Smolnik 2006).

### Definition: Information
Daten in einem bestimmten Bedeutungskontext. Anwendungs- und Informationssysteme speichern Daten und bieten die Moeglichkeit, diese so in einen Kontext zu stellen, dass Menschen sie leichter aufnehmen koennen (Riempp 2004).

### Definition: Informationsobjekte
Kontextuell aufbereitete Daten, d.h. physische oder digitale Objekte (z.B. Dokumente, E-Mails, Webseiten). Erst durch den Prozess der Aufnahme entfaltet sich beim Aufnehmenden der Bedeutungsgehalt — Informationsobjekte werden zu verstandenen Informationen (Riempp 2004).

### Definition: Wissen
Die Gesamtheit der Kenntnisse und Faehigkeiten, die Menschen zur Loesung von Problemen einsetzen. Umfasst theoretische Erkenntnisse und praktische Alltagsregeln. Stuetzt sich auf Daten und Informationen, ist aber immer an Menschen gebunden. Wissen entsteht als individueller Prozess in einem spezifischen Kontext und manifestiert sich in Handlungen (Smolnik 2006).

### Definition: Individuelle Intelligenz
Der willentliche und planmaessige Einsatz der individuellen Faehigkeit zur Nutzung von Informationen und das Vermoegen, aus der Interpretation Schlussfolgerungen zu ziehen.

### Definition: Organisatorische Intelligenz
Die Organisation als soziotechnisches System, konstituiert durch die Beziehungen zwischen Akteuren, der Organisation und der technischen Infrastruktur. "Intelligent", wenn sie (1) durch Informationsprozesse Anforderungen erkennen, analysieren und interpretieren kann, (2) durch Feedbackmechanismen lernt ("lernende Organisation"), (3) ein geplantes Ziel verfolgen und erreichen kann.

---

## Modelle / Frameworks

### Historische Entwicklung des BI-Begriffs

| Entwicklungsschritt | Fragestellung | Technologie | Charakteristik |
|---------------------|---------------|-------------|----------------|
| Datensammlung (1960er) | "Gesamtertraege der letzten 5 Jahre?" | Computer, Magnetbaender | Retrospektiv, statisch |
| Datenzugriff (1980er) | "Welche Produkte in NRW im Maerz?" | RDBMS, SQL, ODBC | Retrospektiv, dynamisch auf Datensatzebene |
| DWH/Entscheidungsunterstuetzung (1990er) | "Produkte in NRW im Maerz? Aufschluesselung fuer Hagen." | OLAP, multidim. DB, DWH-Systeme | Retrospektiv, dynamisch auf versch. Ebenen |
| Data Mining (2000-2010) | "Welche Produkte werden sich verkaufen? Weshalb?" | Advanced Algorithms, hoch-parallele Verarbeitung | Prospektiv, proaktive Bereitstellung |
| Cloud-Computing (ab 2010) | "Wie kurzfristige Entscheidungen treffen?" | Mobile BI, Echtzeitverarbeitung | Ortsunabhaengig, jederzeit verfuegbar |

- **Luhn (1958):** Erste dokumentierte Verwendung des Begriffs "Business Intelligence". Stellte die Verbindung her zwischen unternehmerischem Auftrag (Business), Informationen als Entscheidungsbasis (Intelligence) und technischer Unterstuetzung (BI-System).
- **BI as a Service:** Betrieb des BI-Systems als Dienstleistung ueber einen Drittanbieter (z.B. Cloud-Service).
- **Real-Time BI:** Daten innerhalb des BI-Systems werden in Echtzeit aktualisiert.

### Ackoffs 5 kritische Annahmen (1967)
1. "The critical deficiency under which most managers operate is the lack of relevant information." — Teilweise richtig, aber Manager leiden vor allem an einem Ueberangebot irrelevanter Daten.
2. "The manager needs the information he wants." — Subjektiver Informationsbedarf ("wants") kann vom objektiven ("needs") abweichen; ohne Modell des Entscheidungsprozesses wird die nachgefragte Menge zu gross.
3. "If a manager has the information he needs his decision making will improve." — Von Information bis zur Entscheidung ist es noch ein weiter Weg; ein geeignetes Modell hilft, die Information richtig zu verwerten.
4. "Better communication between managers improves organizational performance." — Kommunikation verursacht Aufwand; Kommunikationspaare wachsen ueberproportional; ein "Zuviel" kann schaedlich sein.
5. "A manager does not have to understand how his information systems works, only how to use it." — Manager brauchen ausreichende Kompetenz bezueglich der inneren Ablaeufe von IT-Systemen, um diese zu evaluieren und Plausibilitaet einzuschaetzen.

### Markov Decision Process (MDP)
Formale Modellierung von Entscheidungsprozessen. System in Zustand z ∈ Z, durch Aktion a ∈ A mit Wahrscheinlichkeit Pa(z,z') Uebergang in neuen Zustand z'. Entscheider erhaelt Belohnung Ra(z,z'). **Markov-Eigenschaft:** Neuer Zustand haengt nur vom aktuellen Zustand und der aktuellen Aktion ab, nicht von frueheren.

- **Formel 2.1:** Diskontierte Summe zukuenftiger Belohnungen: Σ γ^t · R_at(zt, zt+1) fuer t=0 bis ∞
- **Formel 2.2:** Optimale Strategie π*(z) := argmax_a { Σ Pa(z,z') · (Ra(z,z') + γ·V(z')) }
- **Formel 2.3:** Wertfunktion V(z) := Σ P_π(z)(z,z') · (R_π(z)(z,z') + γ·V(z')) — rekursiv definiert

### Framework: PDCA-Kreislauf (Deming 1982)
Handlungsorientierte Modellierung von Entscheidungsprozessen. Vier Phasen:
1. **Plan:** Entscheidungssituation erfassen, Verbesserungsmoeglichkeiten untersuchen, ggf. prototypisch umsetzen.
2. **Do:** Erfolgversprechende Alternativen umsetzen. Gleichzeitig Ergebnisse messen (Kennzahlen schon in Plan-Phase festlegen). Ggf. Pilotprojekt.
3. **Check:** Messergebnisse ueberpruefen und auswerten. Ergebnisse im Entscheiderkreis diskutieren.
4. **Act:** Entscheidung ueber Verbesserungen faellen, konkrete Veraenderung und Anpassung der Ablauforganisation.

Kreislauf: Nach Act geht es wieder in Plan ueber (kontinuierliche Verbesserung). Strategische Sicht moeglich durch rekursive Verschachtelung (aeusserer Kreislauf = strategisch, innerer = operativ).

### Weitere Phasenmodelle (nach Hummeltenberg 2008)
- Phasenmodell nach Simon (1960/1977)
- SECI-Modell nach Nonaka und Takeuchi (1995)
- OODA-Loop nach Boyd (1995)
- PDCA-Kreislauf nach Deming (1982)

Gemeinsamkeiten: Analysephase, Datensammlung, Alternativenermittlung, Bewertung, Auswahl, Reflektion. "Feedback loop" fuer nachhaltiges organisationales Lernen.

### 4 Phasen der Entscheidung und zugehoerige BI (nach Hummeltenberg 2008)

| Phase | Gefoerdertes Fachwissen | Business Intelligence |
|-------|------------------------|----------------------|
| I | Problemloesungswissen | Domaeneninformation, Trendanalysen, Szenarien |
| II | Transformationswissen (Change-Management) | Systemverhalten, Kontextanalysen, SWOT |
| III | Methodenwissen (Leistungsmessung) | Messmethoden, Risikoanalysen, Qualitaetsinformation |
| IV | Steuerungswissen | Soll-Ist-Vergleiche, Planzahlen, Leistungskennzahlen |

### Framework: Hub-and-Spoke-Architektur (BI-Architektur)
Vier Stufen:
1. **Datenquellen:** Interne (ERP, CRM, SCM) und externe Datenquellen
2. **Staging:** ETL-Prozess (Extraktion-Transformation-Laden) — Daten extrahieren, aufbereiten, in DWH uebernehmen
3. **Datenhaltung:** Data Warehouse (Langzeitspeicher) + Data Marts (themenbezogene Teilausschnitte, z.B. Marketing, Personal)
4. **Auswertung/Praesentation:** Berichtsgeneratoren, Abfragesprachen, OLAP, Data Mining, Bueroinformationssysteme, browserbasierte Werkzeuge

Vorteile des DWH: Verbesserte Datenqualitaet durch Standardisierung, schneller Zugriff auf entscheidungsrelevante Daten, Kostenreduktion bei Datensuche, anwenderfreundliches Frontend.

### Framework: Comprehensive Decision Model (CDM)
Ziel: Informationslogistik im Unternehmen sicherstellen. Drei Dimensionen:

1. **Akteur:** Individueller, subjektiver Informationsbedarf des Entscheiders. Erfahrungen, Ausbildung, Einstellung beeinflussen die Interpretation. Informationsbereitstellung muss individuell angepasst sein.
2. **Organisation:** Rahmengebend fuer Datenerhebung (Informationsproduktion) und Informationsverwendung. Durch Ziele und Strategie entsteht der objektive Informationsbedarf. Restriktionen und Freiheitsgrade der Organisation beruecksichtigen.
3. **Applikationen:** Technische Grundlage fuer Informationsproduktion. Speicherung, Aufbereitung, Verbreitung der Informationen. Muss Ergonomie-Anforderungen der Akteure und Analysebedarfe der Organisation erfuellen. Datenqualitaet, flexible Architektur, Sicherheit.

Vorgehensweise: Nicht streng sequentiell, sondern alternierend, da Einbettung in bestehende Organisation und Infrastruktur.

---

## Operative vs. dispositive Daten (Kemper et al. 2006)

| Kriterium | Operative Daten | Dispositive Daten |
|-----------|----------------|-------------------|
| Ziel | Abwicklung der Geschaeftsprozesse | Entscheidungsorientiert; Managementunterstuetzung |
| Ausrichtung | Detaillierte, granulare Geschaeftsvorfalldaten | Verdichtete, transformierte Daten; umfassendes Metadatenangebot |
| Zeitbezug | Aktuell, zeitpunktbezogen | Unterschiedliche Aktualitaet; Historienbetrachtung |
| Modellierung | Altbestaende oft nicht modelliert (funktionsorientiert) | Sachgebiets-/themenbezogen, standardisiert, endnutzertauglich |
| Zustand | Haeufig redundant, inkonsistent | Konsistent modelliert, kontrollierte Redundanz |
| Update | Laufend und konkurrierend | Ergaenzend; Fortschreibung abgeleiteter, aggregierter Daten |
| Queries | Strukturiert, meist statisch im Programmcode | Ad-hoc fuer komplexe, wechselnde Fragestellungen + Standardauswertungen |

---

## Definitionstabelle

| Begriff | Definition |
|---------|-----------|
| **Business Intelligence** | Entscheidungsproblem-orientierte Analyse + adressatengerechte Bereitstellung wettbewerbsrelevanter Informationen |
| **BI-System** | Informationsgetriebenes Entscheidungsunterstuetzungssystem (Hummeltenberg 2019) |
| **Data Warehouse** | Unternehmensweite, zentrale, konsistente Datenbasis zur Entscheidungsunterstuetzung (Hansen/Neumann 2019) |
| **Data Marts** | Aggregierter Teilausschnitt des DWH fuer bestimmten Themen-/Anwenderkreis |
| **Data Mining** | Softwaregestuetzte Ermittlung unbekannter Zusammenhaenge in umfangreichen Datenbestaenden |
| **OLAP** | Multidimensionale Analyse von DWH-Daten mit Just-in-time-Bereitstellung |
| **BIM** | Gesamter informationsverarbeitender Teilbereich einer Organisation |
| **Daten** | Syntaktisch geordnete Wahrnehmungen (Smolnik 2006) |
| **Information** | Daten in einem bestimmten Bedeutungskontext (Riempp 2004) |
| **Informationsobjekte** | Kontextuell aufbereitete Daten (physisch/digital) |
| **Wissen** | Personengebundene Kenntnisse und Faehigkeiten zur Problemloesung (Smolnik 2006) |
| **Individuelle Intelligenz** | Faehigkeit zur planmaessigen Nutzung von Informationen und Schlussfolgerungen |
| **Organisatorische Intelligenz** | Faehigkeit der Organisation als soziotechnisches System zum Erkennen, Lernen, Zielverfolgen |
| **MDP** | Markov Decision Process — formale Modellierung mehrstufiger Entscheidungen |
| **PDCA** | Plan-Do-Check-Act — Kreislauf zur kontinuierlichen Verbesserung (Deming 1982) |
| **CDM** | Comprehensive Decision Model — 3 Dimensionen (Akteur, Organisation, Applikationen) |
| **Hub-and-Spoke** | BI-Architektur in 4 Stufen (Datenquellen, Staging/ETL, DWH/Data Marts, Auswertung) |
| **ETL** | Extraktion-Transformation-Laden-Prozess |
| **Operative Daten** | Granulare Geschaeftsvorfalldaten zur Abwicklung der Geschaeftsprozesse |
| **Dispositive Daten** | Verdichtete, transformierte Daten zur Entscheidungsunterstuetzung |

---

## Querverweise

- Siehe auch: `wissen/02_methoden_instrumente.md` — KDD-Prozess und Data-Mining-Verfahren (in Einheit 1 eingefuehrt, in Einheit 2 vertieft)
- Siehe auch: `wissen/03_datenhaltung_bereitstellung.md` — DWH-Architektur, ETL, OLAP (hier eingefuehrt, in Einheit 3 vertieft)
- Siehe auch: `wissen/04_neuere_entwicklungen.md` — BI as a Service, Real-Time BI (hier erwaehnt, in Einheit 4 vertieft)

---

## Typische Pruefungsfragen

### Pruefungsfrage: Was ist Business Intelligence? Erlaeutern Sie das Konzept ganzheitlich.
**Antwort:** BI ist die an einem Entscheidungsproblem orientierte Analyse und adressatengerechte, technikgestuetzte Bereitstellung wettbewerbsrelevanter Informationen. BI ist kein rein technisches Konzept — es integriert fachliche Grundlagen (Entscheidungsprozesse, Geschaeftsmodell), organisatorische Strukturen (wer braucht welche Informationen) und technische Architektur (DWH, ETL, OLAP, DM). Der ganzheitliche Ansatz beruecksichtigt den Entscheider als Individuum, die Organisation als Rahmen und die Applikationen als technische Basis (vgl. CDM).

### Pruefungsfrage: Beschreiben Sie die Hub-and-Spoke-Architektur und ihre vier Stufen.
**Antwort:** Stufe 1: Interne und externe Datenquellen (ERP, CRM, SCM etc.). Stufe 2 (Staging): ETL-Prozess — Daten werden extrahiert, transformiert und in das DWH geladen. Stufe 3: Datenhaltung im DWH (Langzeitspeicher) sowie in Data Marts (themenbezogene Teilausschnitte). Stufe 4: Auswertung und Praesentation — OLAP, Data Mining, Berichtsgeneratoren, browserbasierte Werkzeuge zur Entscheidungsunterstuetzung.

### Pruefungsfrage: Grenzen Sie Daten, Information und Wissen voneinander ab.
**Antwort:** Daten sind syntaktisch geordnete Wahrnehmungen ohne Bedeutungskontext. Information entsteht, wenn Daten in einen Bedeutungskontext gestellt werden — aus "Bank" wird erst durch die Interpretationsvorschrift (Sprache, Kontext) eine verstandene Information. Wissen ist personengebunden und entsteht durch die mentale Verknuepfung von Daten und Informationen. Anders als Daten und Informationen ist Wissen immer an den Menschen gebunden und manifestiert sich in Handlungen.

### Pruefungsfrage: Erlaeutern Sie den PDCA-Kreislauf und seine Bedeutung fuer die BI.
**Antwort:** Der PDCA-Kreislauf (Deming 1982) modelliert Entscheidungsprozesse in vier Phasen: Plan (Situation analysieren, Verbesserungen planen), Do (umsetzen und messen), Check (Messergebnisse auswerten), Act (Entscheidung faellen, Ablauforganisation anpassen). Danach beginnt der Kreislauf erneut — kontinuierliche Verbesserung. Fuer die BI liefert jede Phase spezifischen Informationsbedarf. Durch rekursive Verschachtelung kann auch die strategische Ebene abgebildet werden.

### Pruefungsfrage: Was ist das CDM und welche drei Dimensionen umfasst es?
**Antwort:** Das Comprehensive Decision Model sichert die Informationslogistik im Unternehmen. Dimension 1 — Akteur: individueller, subjektiver Informationsbedarf basierend auf Erfahrungen, Ausbildung, Kontext. Dimension 2 — Organisation: gibt den Rahmen fuer Informationsproduktion und -verwendung vor, bestimmt den objektiven Informationsbedarf. Dimension 3 — Applikationen: technische Grundlage fuer Speicherung, Aufbereitung und Verbreitung von Informationen. Die Dimensionen werden nicht sequentiell, sondern alternierend analysiert.

---

## Tags

`BI-Definition` `Luhn-1958` `Hub-and-Spoke` `PDCA` `MDP` `CDM` `DWH` `Data-Marts` `Data-Mining` `OLAP` `ETL` `Daten-Information-Wissen` `operative-dispositive-Daten` `Ackoff` `Entscheidungsunterstuetzung` `BIM`
