# 04 - Neuere Entwicklungen und Anwendungsbeispiele der BI

> **Quelle:** 32711-04-S#1-S002664984.pdf (60 Seiten) | **Pruefungsrelevanz:** HOCH

## Ueberblick

Einheit 4 behandelt aktuelle Entwicklungen der Business Intelligence, insbesondere die Wirkung von BI auf Unternehmensprozesse (Echtzeit-BI, BAM, Mobile BI), Advanced Analytics (BI jenseits von Organisationsgrenzen, semi-/unstrukturierte Daten, Text Mining, In-Memory Analytics) sowie ausgewaehlte Anwendungsbeispiele (BI im Marketing/CRM, Fallstudien Newspaper Industry und Continental Airlines). Im Vordergrund steht der Uebergang von traditioneller, strategisch orientierter BI hin zu operativer, echtzeitnaher und prozessintegrierter BI. Die Einheit ordnet diese Entwicklungen in das biMM-Reifegradmodell ein und zeigt anhand konkreter Fallstudien, wie der KDD-/CRISP-DM-Prozess in der Praxis angewendet wird -- einschliesslich typischer Schwierigkeiten.

---

## Kernkonzepte

### Makrotrends und Forschungsbereiche (Baars et al., 2014)

Baars et al. (2014) fassen die Bedingungen, denen aktuelle BI-Systeme genuegen muessen, unter dem Begriff **Makrotrends** zusammen. Daraus resultieren fuenf Forschungsbereiche:

1. Integration von BI und Geschaeftsprozessmanagement
2. Ueber Unternehmensgrenzen hinaus kooperativ entwickelte und betriebene BI-Loesungen
3. Ansaetze zur Verarbeitung semi- und unstrukturierter Daten
4. Agile Bereitstellung und durch Nutzung gesteuerte BI-Systementwicklung
5. BI-Governance

Zwei uebergreifende Trends: (1) Neue BI-Technologien beguenstigen sich gegenseitig und werden staerker miteinander verknuepft (z. B. mit KM, Web 2.0). (2) BI wird durch kuerzere Entwicklungszyklen und Betrachtungszeitraeume insgesamt dynamischer.

### BI 2.0

Die Bezeichnung BI 2.0 ist inspiriert vom Web 2.0 und kann allgemeiner als die "naechste Version der BI" verstanden werden. Nach Nelson (2010) umfasst BI 2.0 u. a.:

- Proaktive Benachrichtigungen
- Echtzeit-Zugriff auf Information
- Advanced Analytics
- Unternehmensintegration
- Verbesserte Visualisierungen
- BI as a Service
- In-Memory Analytics
- OpenSource BI

Prinzipien des Web 2.0, die fuer BI 2.0 adaptiert werden koennen (Nelson, 2010):
- Entwickeln eigener "Apps" fuer das BI-System
- Zeitnahes Weiterempfehlen, Abonnieren und Bewerten von Inhalten
- Gemeinsames Kommentieren, Bearbeiten und Kategorisieren durch mehrere Personen
- Schnelles Veroeffentlichen eigener Interpretationen und Aufbereitungen
- Meta-Analyse des Nutzungsverhaltens im BI-System

### BI 3.0 (Chen et al., 2012)

Nach Chen et al. (2012) markiert die zusaetzliche Beruecksichtigung von webbasierten und unstrukturierten Inhalten den Uebergang zur BI 2.0. Werden darueber hinaus auch mobile und sensorbasierte Daten verarbeitet, sprechen die Autoren von **BI 3.0**.

- **BI 1.0:** Klassisches DM, Predictive Analytics, In-Memory Analytics, BI-gestuetztes CPM
- **BI 2.0:** Zusaetzliche Beruecksichtigung webbasierter und unstrukturierter Inhalte
- **BI 3.0:** Zusaetzlich mobile und sensorbasierte Daten

---

## Modelle / Frameworks / Verfahren

### biMM -- Business Intelligence Maturity Model (Chamoni & Gluchowski, 2004)

Reifegradmodell zur Einordnung von BI-Loesungen mit drei Dimensionen: **Fachlichkeit** (betriebswirtschaftlich inhaltliche Sicht), **Technik** (Komponenten und Architekturen) und **Organisation** (Einbettung in Aufbaustrukturen und Ablaufprozesse).

| Stufe | Bezeichnung | Fachlichkeit | Technik |
|-------|-------------|-------------|---------|
| 1 | Vordefiniertes Berichtswesen | Inhalte z. T. redundant berichtet; keine weitergehende Analysemoeglichkeit; fachbezogene Auswertungen; keine einheitliche Semantik | Statische, parametergesteuerte Berichte; einfache Darstellung (z. B. Listendruck); lokale Layoutstandards; Einbettung in operative IS |
| 2 | BI pro Fachbereich | Inselloesungen; Ad-hoc-Analysemoeglichkeiten; abteilungsweit gueltige Semantik | OLAP-Navigationsfunktionalitaet; Zeitreihenanalysen; Datenhistorisierung; Automatisierung ETL-Prozesse |
| 3 | Unternehmensweite BI | Integration verschiedener Fachbereiche; vereinheitlichtes Berichtswesen; unternehmensweit homogenisierte Semantik; einfache Forecastberechnungen; Integration externer Daten | Hub-&-Spokes-Architektur; Metadatenmanagement; uebergreifende Normen/Standards; hohe Verfuegbarkeit; Web-Oberflaechen; automatisierte Integration externer Daten |
| 4 | Erweiterte Entscheidungsunterstuetzung | Prozessunterstuetzung; Closed-Loop-Umsetzung; erweiterte Analysemethoden (z. B. DM); Trendberechnungen; Bildung komplexer Szenarien; Alternativenrechnungen | Einbeziehung semi-strukturierter Daten; DM; Planungs-/Simulationstools; Workflow-Systeme; Portaltechnologien |
| 5 | Aktives Wissensmanagement | Zeitnahe Analysen bis Realtime-Betrieb; adaptives Lernen; enge Kopplung quantitativer und qualitativer Wissensdomaenen; Benutzerrollenkonzepte; aktive Entscheidungsunterstuetzung | Realtime-faehige Infrastruktur; aktive Komponenten (Push-Technologie); Integration unstrukturierter Daten; agentenbasierte Informationssammlung; Verschmelzung operativer und dispositiver Systeme |

**Einordnung:** Stufe 1 ist im Sinne des Lehrbriefs keine BI. Stufen 2-3 = klassische BI (Einheit 3). Stufe 4 = moderne BI (alle Einheiten). Stufe 5 = zum Zeitpunkt der biMM-Vorstellung kaum vorgefunden, erst juengere Technik macht diese Stufe erreichbar.

### Wertbeitrag der BI (Popovic et al., 2010)

Konzeptuelles Modell: Ein erhoehter **BI-Reifegrad** fuehrt zu erhoehter **Informationsqualitaet** (Genauigkeit, Zeitnaehe, Menge, Verstaendlichkeit, knappe/konsistente Darstellung). Dies bedingt, gemeinsam mit **organisationalen Faktoren** (Strategic Alignment, Kultur der kontinuierlichen Verbesserung), dass die durch BI bereitgestellte Information in hoeherem Masse tatsaechlich in **Prozessen genutzt** wird, was zu besserer **Unternehmensleistung** fuehrt.

Wirkungskette: BI-Reifegrad -> Informationsqualitaet -> (+ organisationale Faktoren) -> Verwendung in Prozessen -> Unternehmensleistung

### Verhaeltnis von BI-Systemen und Prozessen

Vier moegliche Ausgestaltungen:
1. Strategische Prozesse verwenden den Output des BI-Systems (klassisches DSS/MIS-Verstaendnis)
2. Strategische Verwendung gestaltet operative Prozesse (langfristiger, indirekter Einfluss)
3. Operative Prozesse werden ihrem Ergebnis nach ueberwacht (kurzfristige, aber weiterhin indirekte Effekte ueber Managementprozesse)
4. BI-Systeme beeinflussen operative Prozesse und Systeme direkt -- dies stellt einen **Paradigmenwechsel** dar (Sandu, 2008)

### Echtzeit-BI und Latenzarten

**Echtzeit-BI im engeren Sinne** bezeichnet die Synchronizitaet von Modell und Realitaet (Hackathorn, 2004). Praktisch ist perfekte Synchronizitaet nicht erreichbar.

**Halbwertszeit von Information:** Information verliert ueber die Zeit an Wert. Der Wertverlust wird als exponentiell angenommen, charakterisiert durch die Zeit, in der sich der Wert halbiert (Pant & Ravichandran, 2001). Naeherungsweise gilt: Je kuerzer die Halbwertszeit, desto wertvoller ist die Information anfaenglich.

**Latenz** ist der zeitliche Abstand zwischen dem Eintreten eines Realweltereignisses und der Reaktion auf die das Ereignis betreffende Information. Die Gesamtlatenz wird differenziert in drei Arten:

| Latenzart | Definition |
|-----------|-----------|
| **Datenlatenz** | Zeit nach Eintreten des Ereignisses, um die betreffenden Daten fuer die weitere Analyse bereitzustellen. Umfasst Erfassung im operativen System und ETL-Prozess ins DWH. Nach unten begrenzt durch den Aktualisierungszyklus des DWH. (Hackathorn, 2004; Golfarelli et al., 2004) |
| **Analyselatenz** | Darueber hinaus benoetigte Zeit, um die Daten zu analysieren und die Analyseergebnisse den richtigen Personen bereitzustellen. Schafft die Grundlage fuer eine Entscheidung. (Hackathorn, 2004) |
| **Entscheidungslatenz** | Darueber hinaus benoetigte Zeit, um die generierte Information zu verarbeiten und eine Handlung zu initiieren. In neuerer Literatur ergaenzt um Handlungs- und Wirkungslatenz. (Hackathorn, 2004; Polites, 2006) |

### RTBI -- Right-Time Business Intelligence

**Definition:** RTBI bezeichnet das Streben nach moeglichst wirtschaftlichen, statt moeglichst kurzen, Latenzen in der BI (Hackathorn, 2004; Davis, 2006; Polites, 2006). "Right-time" ist nicht zu verwechseln mit "real-time" ("Echtzeit") und koennte mit "Rechtzeit" uebersetzt werden.

Kerngedanke: Ein Unternehmen sollte die akzeptable Latenz individuell fuer einzelne Geschaeftsprozesse und Informationstypen festlegen, unter Beruecksichtigung von:
- Ausgangswert der Information
- Halbwertszeit der Information
- Kosten fuer das gewuenschte Latenzniveau

**Traditionelle BI vs. RTBI:**
- Traditionelle BI: Taeglich oder seltener aktualisiert, durch verfuegbare Verfahren/Modelle getrieben
- RTBI: Kuerzere Aktualisierungszyklen, durch Ereignisse und Informationsbedarfe getrieben

**Geschlossener RTBI-Kreislauf:** Die handlungsorientierte RTBI ergaenzt die Transformation von Daten in Informationen (traditionelle BI) um die Ruecktransformation von Informationen in Handlungen. Ueber diese Handlungen wirkt RTBI direkt zurueck auf die Geschaeftsprozesse, die wiederum neue Daten generieren. Drei Schichten:
1. **Operative Schicht:** Operative Systeme (CRM, ERP)
2. **Datenintegrationsschicht:** Anbindung operativer Systeme an DWH (bei RTBI: kontinuierlich)
3. **Analyseschicht:** Ergaenzt um fortgeschrittene Verfahren; Hauptunterschied: Feedbacksysteme

### BAM -- Business Activity Monitoring (Golfarelli et al., 2004)

BAM dient der Echtzeitanalyse auf operativer Ebene im Rahmen des CPM. BAM-Systeme bestehen aus fuenf Komponenten:

1. **Integrator:** Integriert Daten aus dem DWH nahezu in Echtzeit mit Daten aus anderen Systemen
2. **Dynamischer Datenspeicher:** Haelt integrierte Daten fuer den Zeitraum der Analyse vor
3. **KPI-Manager:** Berechnet gewuenschte KPIs aus den Daten und stellt sie zur Verfuegung
4. **DM-Werkzeuge:** Geeignet fuer historische Daten im DWH und dynamische Daten
5. **Business Rule Engine (BRE):** Beobachtet Ereignisse und leitet auf Basis von Business Rules geeignete Massnahmen ein (z. B. gezielte Information bestimmter Personen)

BAM umfasst somit nicht lediglich die Ueberwachung einzelner Geschaeftsprozesse, sondern ermoeglicht eine integrierte Analyse verteilter Aktivitaeten. Die verstaerkte Datenintegration verringert die Datenlatenz, der Rueckbezug schafft den geschlossenen Kreislauf.

### SSBI -- Self-Service Business Intelligence

SSBI hat sich unter denselben Zielen wie die klassische BI entwickelt. Die Nutzung erfolgt ueber bekannte Oberflaechen (z. B. Webbrowser) ohne clientseitige Softwareinstallation (Alpar & Schulz, 2016). Die Datenhaltung kann in die Cloud verschoben werden.

**Intensitaetsstufen von SSBI-Systemen** (nach steigendem Grad der Selbstbestimmtheit):
1. **Lesen** von Inhalten (auch in klassischer BI)
2. **Erstellen** von Inhalten (auch in klassischer BI)
3. **Neue Quellen hinzuziehen** und mit vorhandenen kombinieren (Risiken: unterschiedliche Datenqualitaet, sich ueberschneidende Datensaetze)
4. **Mashups erstellen** -- bereits programmierte Elemente/Funktionalitaeten fuer aktuellen Gebrauch kombinieren

Herausforderung: Passende Sicherheitsvorkehrungen treffen, ohne SSBI unbenutzbar zu machen.

### CPM -- Corporate Performance Management

Nach Reichmann (2011) ist das Ziel des Controllings, die "Entscheidungsqualitaet auf allen Fuehrungsstufen" zu verbessern. In diesem Kontext hat sich CPM entwickelt.

**CPM nach Oehler (2006):** CPM beschreibt eine integrierte Unternehmenssteuerungsarchitektur. Verschiedene Managementunterstuetzungssysteme (BI, ERP, CRM, KM, Business Process Management) werden aufeinander abgestimmt und zu einem gemeinsamen System integriert. CPM bezieht ueber den traditionellen BI-Begriff hinaus auch die **Steuerung von Prozessen** ein und integriert ISe auch auf operativer Ebene. Durch die Einbeziehung der operativen Ebene entsteht eine Rueckkopplung.

**Fuenf Elemente des Controllingkonzepts als fachliche Basis des CPM:**
1. Controllingobjekte: Was wird gesteuert?
2. Wirkungsbeziehungen: Wie haengen die Objekte zusammen?
3. Metriken: Wodurch lassen sich die Objekte messbar machen?
4. Rollen mit Aufgaben: Wer nimmt die Informationsversorgung wahr?
5. Berichtswesen: Wie werden Vorgaben, Standards, Ergebnisse, Massnahmen dokumentiert?

### MBI -- Mobile Business Intelligence

MBI bezeichnet die mobile Nutzung von BI, unabhaengig von Zeit und Ort, auch ausserhalb des Bueros (Cowie & Burstein, 2007).

**Wahrgenommener Nutzen:**
- Moeglichkeit des staendigen Zugriffs auf Informationen
- Bessere und schnellere Entscheidungsfindung
- Bessere Unterstuetzung fuer mobiles und zielorientiertes Arbeiten

**Aufbau eines MBI-Systems:**
- Stationaere Data Marts werden als **Mobile Data Marts** auf Endgeraeten repliziert
- Synchronisationsverfahren sorgen fuer permanenten Abgleich
- Sicherheitsmechanismen verhindern unberechtigten Zugriff
- Mobile Data Marts gewaehrleisten Datenzugriff auch bei Verbindungsausfall
- Mobiler BI-Client bereitet Daten bedarfsgerecht auf

**Zwei Arten von Client-Anwendungen:**
- **Native Clients:** Direkt auf Endgeraet installiert; mehr Funktionalitaeten, kompliziertere Abfragen/Visualisierungen; hoehere Leistungsanforderungen; Kompatibilitaetsprobleme
- **Webbasierte Clients:** Keine Kompatibilitaetseinschraenkungen; begrenzter Funktionsumfang

**Phasenorientiertes MBI-Vorgehensmodell** (in Erweiterung von Hansen, 1998):

| Phase | Kernaufgaben |
|-------|-------------|
| 1. Analysephase | Kosten-Nutzen-Berechnung; grundsaetzliche Klaerung, ob Nutzen Kosten rechtfertigt |
| 2. Designphase | Auswahl/Gestaltung von Hard-/Software; Beruecksichtigung von Anzeigebeschraenkungen, Kompatibilitaet, IT-Sicherheit |
| 3. Realisierungsphase | Inbetriebnahme; Sicherheitskonzept; BYOD-Entscheidung; Schulung der Mitarbeitenden; MBI-Governance |
| 4. Betriebs-/Weiterentwicklungsphase | Kontinuierliche Ueberwachung; Anpassung an technische Entwicklungen und geaenderte Anforderungen |

**Drei uebergreifende Aspekte ueber alle Phasen:**
- Langfristigkeit
- Business/IT-Alignment
- Kostenkontrolle

**Drei Rollen:**
- Organisatorische Seite: Uebergeordnete Kontrollfunktion, Abstimmung mit Gesamtunternehmensstrategie
- Fachliche Seite: Bedarfsdefinition, Anforderungen an das System
- Technische Seite: IT-Abteilung und ggf. externe Dienstleistung; Umsetzung, Leistungsueberwachung

**BYOD (Bring Your Own Device):** Nutzung privater Geraete fuer Geschaeftszwecke. Vorteile: Kein Umlernen, Akzeptanz, Kosteneinsparung. Nachteile: Datenschutz, Datensicherheit, Virengefahr, sensible Daten auf privaten Geraeten.

**Sicherheitsrisiken bei MBI** (Friedman & Hoffman, 2008):
- Erhoehte Gefahr von Verlust/Diebstahl mobiler Geraete
- Kommunikation ueber oeffentliche, ungeschuetzte Netzwerke
- Erhoehte Virengefahr ausserhalb der Unternehmens-Firewall
- Begrenzte IT-Ressourcen fuer mobile Sicherheit

### BIaaS -- Business Intelligence as a Service

Bei BIaaS steht ausserhalb des Unternehmens bei einem Dienstleister ein Analyseteam zur Verfuegung. BIaaS lagert den Betrieb des BI-Systems als Dienstleistung aus. Das BI-System wird als externer Service konfiguriert und ueber das Internet zugaenglich gemacht.

**Abgrenzung:**
- **Open Source BI:** Inhouse betrieben, kein direkter Support, Kompetenzen intern oder zugekauft
- **BIaaS:** Auch Betrieb als Dienstleistung ausgelagert
- **SOA-basierte BI:** Einzelne Komponenten (Services) nach Baukastenprinzip, intern oder als Dienstleistung betrieben

### Cloud-BI / Cloudbasierte BI

Auslagerung in bestehende externe Infrastruktur. Unterscheidung: (a) Auslagerung eines selbstadministrierten BI-Systems in die Cloud; (b) zusaetzliche Auslagerung der Administration (= BIaaS).

**Acht Dimensionen und Erfolgsfaktoren cloudbasierter BI** (Schirm et al., 2015):

| Dimension | Erfolgsfaktoren |
|-----------|----------------|
| Agilitaet | Flexibilitaet; Skalierbarkeit |
| Kosten | Kosteneinsparung; Pay-per-Use |
| Positive Auswirkungen auf Kerngeschaeft | Konzentration auf Kernkompetenzen; Wettbewerbsvorteile |
| Performance | Performance; In-Memory; Echtzeit |
| Customizing | Entwicklungsmoeglichkeiten; Administration des Servers; Funktionale Erweiterbarkeit; SSBI |
| Usability / Vernetztes Cloud-Computing | Interoperabilitaet; Nutzung der Services von Drittanbietern; Mobilitaet |
| Zuverlaessigkeit und Vertrauen | Verfuegbarkeit; Zuverlaessigkeit; Support; Security |
| Cloudbetrieb | On-the-fly Updates; Umsetzung von Standards |

### SBI -- Social Business Intelligence

SBI bezeichnet die Einbettung von Social Media Daten in ein BI-System (Dinter & Lorenz, 2012). Synonyme/verwandte Begriffe: Social Media Intelligence, Social Media Analytics, Social Intelligence, BI 2.0.

**Social Media Daten unterscheiden sich von klassischen Daten durch:**
- Hohe Dynamik in Datenaktualisierungen und -volumen
- Individuelle Struktur in dezentralen Datenbanken, User Generated Content
- Semi-/unstrukturierte Daten
- Interpretationsabhaengigkeit vom Kontext, unstrukturiertes Peer-Feedback
- Unbekannte Datenqualitaet
- Multiple Plattformen als Datenquellen, Collaborative Filtering
- Massiv vernetzte, dynamische Nutzernetzwerke
- Unklare Rechtslage (Urheberrecht, Datenschutz)

### CBI -- Collaborative Business Intelligence

**Definition (in Anlehnung an Kaufmann, 2015):** CBI beschreibt die bewusste Erweiterung des Analysekreises des genutzten BI-Systems um unternehmensinterne und -externe Analysewerkzeuge sowie die dafuer notwendige Oeffnung der Datenbestaende der Beteiligten.

**Abgrenzung SBI vs. CBI:** Bei SBI werden Daten aus sozialen Medien in das BI-System integriert. Bei CBI findet darueber hinaus eine aktive Zusammenarbeit mit anderen Unternehmen/Organisationen statt -- Nutzung externer Daten/Werkzeuge UND Teilen eigener Daten/Werkzeuge.

**Drei Abstufungen von CBI** (Kaufmann, 2015; steigender Kooperationsgrad):
1. **Interne Kommunikation:** Mehr Team-Mitglieder an der BI-Nutzung beteiligt, auch ausgewaehlte externe Einheiten
2. **Gemeinschaftliche Datenhaltung:** Interne Daten zur externen Nutzung bereitgestellt, externe Daten intern einbezogen (ohne Aenderung der Analysevorgehen)
3. **Partnerschaftliche Analyse:** Analyse selbst partnerschaftlich, z. B. ueber externe zentralisierte BI-Systeme

### BI mit semi- und unstrukturierten Daten

**Begriffliche Unterscheidung (Albescu et al., 2008):** "Inhalte" = unstrukturierte Daten; "Daten" impliziert bereits eine Struktur. Unstrukturierte Inhalte machen laut Endeca (2011) ca. 80% des fuer Unternehmen relevanten Datenvolumens aus.

**Beispiele fuer unstrukturierte Inhalte (Endeca, 2011):**

| Kundenkontakt | Social Media | Dokumentation | Presse/PR |
|--------------|-------------|--------------|-----------|
| Call-Center-Mitschnitte | Rezensionen/Bewertungen | Zertifizierungsunterlagen | Nachrichten |
| Kundenbefragungen | Forenbeitraege | Gespraechsprotokolle | RSS-Feeds |
| Kundenkorrespondenz | Microblogging/Tweets | Vertraege | Konkurrenz-Webseiten |
| Kundendienstberichte | Blogartikel | Quartalsberichte | Kommerzielle Informationsdienste |
| Vertriebsprotokolle | Likes/Facebook-Meldungen | Sonstige Dokumente | |

**Drei Vorgehensweisen zur Integration (Baars & Kemper, 2008):**

1. **Integrierte Praesentation:** Strukturierte Daten und unstrukturierte Inhalte in getrennten Quellen; Integration nur auf Praesentationsebene durch gekoppelte Navigations-/Suchfunktionen (z. B. aus OLAP-Sicht automatische Suchanfrage an Inhaltsdatenbank). Vorteil: Geringer Aufwand.
2. **Analyse von Inhaltssammlungen (Extraktion von Metadaten):** Metadaten (Autor, Erstellungszeitpunkt, Schlagwoerter, Klassifizierungen) werden manuell oder algorithmisch (z. B. Text Mining) extrahiert und in strukturierte Datenbank integriert. Ermoeglicht dauerhafte Verknuepfung.
3. **Verbreitung von Analyseergebnissen als Inhalte:** Umgekehrte Richtung -- strukturierte Analyseergebnisse werden in menschenlesbarer Form als unstrukturierte Inhalte aufbereitet. Nicht nur Ergebnisse, sondern auch Vorgehensweisen werden verbreitet. Idealerweise Anbindung an KM-System.

### Text Mining

Text Mining extrahiert aus unstrukturierten Textdokumenten strukturierte Metadaten. Moderne Systeme koennen anhand der Satzstruktur identifizieren:
- Namen von Personen, Unternehmen, Produkten, Orten
- Beziehungen zwischen identifizierten Entitaeten
- Fuer den Text typische Begriffe und Saetze (Thema)
- **Sentiment Analyse:** Vergleich identifizierter Schluesselbegriffe mit einer Datenbank von Begriffskonnotationen (positiv, neutral, negativ) zur Ermittlung der Meinung des Autors (Nasukawa & Yi, 2003)

### Bag-of-Words-Ansatz und TF-IDF

**Bag-of-Words:** Texte werden als unstrukturierte Ansammlung von Woertern betrachtet. Anstelle echten Textverstaendnisses wird gezaehlt, wie oft einzelne Begriffe vorkommen (Fan et al., 2006).

**Begriffe:**
- **Korpus (D):** Sammlung von Dokumenten, entspricht dem Konzept X
- **Instanz:** Einzelnes Dokument d_i
- **Lexikon:** Menge der im Korpus vorkommenden Woerter
- **Term:** Einzelnes Wort q_j aus dem Lexikon
- **Featurevektor:** Strukturierte Repraesentation eines Dokuments als Vektor

**Probleme des naiven Ansatzes:**
1. Sehr viele verschiedene Terme in grossen Korpora fuehren zu langen Featurevektoren und erhoehten Laufzeiten
2. Sehr haeufige Terme (Artikel, Konjunktionen) sagen wenig ueber den Inhalt aus, dominieren aber seltenere, aussagekraeftigere Terme

### TF-IDF -- Term Frequency-Inverse Document Frequency (vollstaendige Formeln)

TF-IDF ist eine haeufig verwendete, informationstheoretisch begruendbare Heuristik fuer die Gewichtung von Termen (Robertson, 2004).

**1. Term Frequency (TF):**

```
tfreq: D x Q -> N                                           (3.1)
```
tfreq(d_i, q_j) = Haeufigkeit, mit der Term q_j in Dokument d_i vorkommt.

**2. Supportmenge des Terms:**

```
X_q_j = { x_i | tfreq(d_i, q_j) > 0 }                      (3.2)
```
Menge der Instanzen, in deren zugehoerigem Dokument der Term vorkommt.

**3. Document Frequency (dfreq):**

```
dfreq: Q -> R                                                (3.3)
dfreq(q_j) = |X_q_j| / |X| = |X_q_j| / N_I                 (3.4)
```
Schaetzer, wie wahrscheinlich es ist, dass in einem beliebigen Dokument der Term vorkommt.

**4. Informationsgehalt (Inverse Document Frequency):**

```
info: Q -> R                                                  (3.5)
info(q_j) = -log( |X_q_j| / |X| ) = log( |X| / |X_q_j| ) = log( 1 / dfreq(q_j) )    (3.6)
```
Der Informationsgehalt des Auftretens von q_j ist der Logarithmus der inversen Dokumentfrequenz.

**5. TF-IDF Berechnung des Featurevektors:**

```
x_i,j = tfreq(d_i, q_j) * log( 1 / dfreq(q_j) )            (3.7)
```

**Interpretation:** Terme mit hohem TF-IDF-Wert sind solche, die insgesamt selten, aber in einem bestimmten Dokument haeufig zu finden sind. Diese repraesentieren ihr jeweiliges Dokument sehr gut.

**Attributselektion mittels TF-IDF (Jing et al., 2002):** Zur Auswahl einer gewuenschten Anzahl der Attribute (N_Q) werden diejenigen N_Q Terme mit den hoechsten TF-IDF-Werten herangezogen.

### Normierung und Zentroiden-basierte Klassifikation

**Normierung:** Da der Betrag ||x_i|| mit der Textlaenge waechst und die Klasse unabhaengig von der Laenge sein sollte, wird der Featurevektor normiert:

```
x'_i,j = x_i,j / ||x_i||                                    (3.8)
```

**Distanz zweier Dokumente:** Winkel zwischen den zugehoerigen normierten Vektoren:

```
dist_D(d_i, d_j) = dist(x_i, x_j) = arccos( <x_i, x_j> / (||x_i|| * ||x_j||) )    (3.9)
```
Nach Normierung ist der Nenner = 1, es bleibt das Skalarprodukt (Han & Karypis, 2000).

**Zentroid einer Klasse c_k:**

```
C_k = { x_i in X_Tr | x_i,Label = c_k }                     (3.10)
mu_c_k = ( x_c_k,1_mean, ..., x_c_k,N_Q_mean )              (3.11)
x_c_k,j_mean = (1 / |C_k|) * SUM x_i,j (fuer x_i in C_k)   (3.12)
```

**Klassifizierungsfunktion:**

```
h(x_i) = arg min_c_k ( dist(x_i, mu_c_k) ) = arg max_c_k ( <x_i, mu_c_k> )    (3.13)
```

### Predictive und In-Memory Analytics

**In-Memory Analytics (Acker et al., 2011):** "A technology that will allow operational data to be held in a single database that can handle all the day-to-day customer transactions and updates, as well as analytical requests -- in virtually real time."

Technisch: Verlagerung der Daten von langsamen Massenspeichern (Festplatten) in den schnelleren Hauptspeicher (RAM). Erste Forschung seit den 1980er Jahren. Treiber: Wachsende Datenmengen mit haeufigen, zeitintensiven Ladevorgaengen. Enabler: Stark fallende Hardwarepreise.

**Wirkung:** (1) Daten aus operativen Systemen muessen nicht erst in dispositive Systeme uebertragen werden. (2) Erhebliche Senkung der Datenlatenz. In-Memory Analytics ist somit ein wesentlicher Schritt hin zur RTBI und Enabler fuer viele Anwendungen der Einheit.

---

## Anwendungsbeispiele

### BI im Marketing und CRM

BI im Marketing ist besonders geeignet, wenn:
- Grosse Datenbestaende als Entscheidungsbasis vorliegen, in denen Beziehungen/Muster vorhanden sein koennten
- Daten in mehreren verschiedenen Quellen (auch extern) vorliegen, die detaillierteres Bild ueber Stimmungen, Trends und Beduerfnisse zulassen

**Drei CRM-Typen:**

| CRM-Typ | Funktion |
|---------|---------|
| **Analytisches CRM** | Alle Daten ueber bestehende/potentielle Kunden zusammenfuehren; Wissen ueber Trends/Beduerfnisse erzeugen; Retention Management; Betrugsfrueherkennung; zukunftsgerichtet |
| **Operatives CRM** | Konkrete Kundensegmente definieren; Marktanalysen; Kundenwert ermitteln; Kampagnen planen/durchfuehren; an der Schnittstelle zum Kundenprozess |
| **Kommunikatives CRM** | Planung der Kommunikationskanaele; durch Web 2.0 an Bedeutung gewonnen; bidirektionale Kommunikation (auch ueber Soziale Netzwerke) |

Ergaenzend: **Collaborative CRM** (ueberschreiten von Abteilungs-/Unternehmensgrenzen) und **Social CRM** (Interaktionen/Transaktionen in sozialen Netzwerken).

**Analytisches CRM + BI -- Anwendungsfelder ueber den gesamten Kundenlebenszyklus:**

- **Neukundengewinnung:** Trendanalyse; Verbesserungsvorschlaege von Nicht-Kunden; Luecken im Kundenprozess identifizieren
- **Pflege des Kundenbestands:** Zusatzangebote; Kundenbindungsprogramme; Praesenz in Sozialen Netzwerken; Multiplikatoren identifizieren
- **Retention Management:** Anforderungen an Kundenkommunikation auf Online-Plattformen; Stimmungsanalyse; Benchmarking von Massnahmen mit Konkurrenten

### Fallstudie "Newspaper Industry" (Gunnarsson et al., 2007)

**Einordnung:** Beispiel fuer BI-Einsatz im CRM, Vorgehen angelehnt an CRISP-DM.

**CRISP-DM (Cross-Industry Standard Process for Data Mining):** Von der Industrie entwickelter Standard mit vielen Parallelen zum KDD-Prozess. Betont besonders:
- **Business Understanding:** DM beginnt mit dem Verstehen der Situation und Ziele des Unternehmens
- **Data Understanding:** Explizite Phase (im KDD-Prozess aus Einheit 2 als Querschnittsaufgabe verstanden)

**Ausgangssituation:** US-Tageszeitung mit ca. 200.000 Auflage. Auflagenhoehe ueber Jahre gesunken, Anzeigenkunden nutzten alternative Kanaele, Investition in DWH/DM wurde gescheut.

**Zieldefinition (durch Fragebogen, alle Unternehmensbereiche beteiligt):**

Drei Zielbloecke:

1. **Abwanderungspraevention:**
   - Zu welchem Zeitpunkt nach Kuendigung sollten ehemalige Kunden kontaktiert werden?
   - Ab wann sollte ein Kunde wie ein Neukunde behandelt werden?
   - Wie haeufig sollten ehemalige Kunden zur Neuanmeldung aufgefordert werden?

2. **Cross Selling / Upgrades:**
   - Welche Kunden koennen durch langfristiges Abonnement gebunden werden?
   - Welche Kunden haben Interesse an Upgrade-Programmen?
   - Gibt es saisonale Trends fuer Upgrades?
   - Gibt es Preismodelle/Preisgrenzen fuer maximale Antwortrate?

3. **Neue Perspektiven (potenzielle Neukunden):**
   - Modell fuer beste Kontaktaufnahmefrequenzen
   - Beschreibung/Identifikation von Personen ohne bisheriges Abonnement
   - Unterschiede/Gemeinsamkeiten ehemaliger vs. nie vorhandener Kunden

**Probleme mit der Datenbasis:**
- Haushaltsdaten: Datenschutzgruende erforderten Transformation (Loeschung sensibler Daten), dadurch Informationsverlust
- Kontaktdaten: Freitextfelder konnten nicht automatisiert verarbeitet werden; unterschiedliche Begriffe/Formulierungen fuer gleiche Sachverhalte; Textanalyseverfahren lieferten keine Loesung
- Werbedaten: Zu unspezifisch, kein Erfolgsmass vorhanden
- Erkenntnis: Nach operativen Gesichtspunkten erhobene Daten sind fuer Analyse oft ungeeignet. Konsequenz: **Beduerfnisse der Datenanalyse muessen schon bei der Erhebung mitgedacht werden.**

**Datenaufbereitung:**
- Doppelte Datensaetze herausfiltern
- Unvollstaendige Datensaetze
- Syntaktisch falsche Benutzung von Datenfeldern durch Mitarbeitende
- Inkonsistenzen bei Integration verschiedener Datenbanken
- Erhebliche Reduktion der verfuegbaren Datensaetze
- Aggregation: Transaktions-/Werbungsdaten den Haushaltsdatensaetzen zuteilen

**Neue Variable:** "Abgewandert" = keine Transaktionen innerhalb der letzten 30 Monate.

**Verwendetes Verfahren: Entscheidungsbaum**
- Regression nicht praktikabel (zu viele Vorannahmen noetig)
- KNN diskutiert, aber verworfen
- Entscheidungsbaum gewaehlt wegen: leichte Visualisierung, einfache Interpretation, Eignung fuer unternehmensinterne Diskussion

**Datenaufteilung:**
- 40% Trainingsdaten (Modellanwendung/-anpassung)
- 30% Validierungsdaten (Feintuning)
- 30% Testdaten (Schaetzfehler ermitteln)
- Begruendung: Gleicher Datensatz fuer Entwicklung und Validierung fuehrt zu Overfitting

**Ergebnis:** Von 100 Variablen wurden 22 im Entscheidungsbaum verwendet, davon nur 7 signifikant (u. a. Haeufigkeit des Bezugs, automatische Zahlung, Kinder im Haushalt, Geschlecht, Einkommen). Aufgrund der schlechten Datenbasis konnte nur das Thema Abwanderungspraevention adressiert werden.

**Kernlektion:** "Lehrstueck ueber die Bedeutung einer geeigneten Datenbasis."

### Fallstudie "Continental Airlines" (Anderson-Lehman et al., 2008; Wixom et al., 2008)

**Ausgangssituation (Anfang 1990er):** Massive finanzielle Probleme. Unpuenktliche/ueberbuchte Fluege, fehlgeleitetes Gepaeck, Kundenbeschwerden. Letzter Rang unter den zehn groessten US-Fluggesellschaften. 1994: Gordon Bethune wird CEO, "Go Forward Plan".

**IT-Probleme vor BI-Einfuehrung:**
- IT-Infrastruktur von Drittanbieter betrieben
- Nur vorher festgelegte Anfragen verarbeitbar
- Keine bereichsuebergreifenden Informationsabfragen
- Keine Informationen ueber gesamte Reise bei indirekten Fluegen

**1998: Einfuehrung DWH:**
- Integration von Daten aus verschiedenen Quellen (Flugplaene, Fluggastdaten)
- Ermoeglichte erstmals ertragsorientierte flexible Preispolitik
- Massnahmen zu Flugplanung, Kundenbindung, Zusammenarbeit mit Reisebueros
- Zusaetzliche Ertraege/Einsparungen in Millionenhoehe

**2001: DWH wird teilweise echtzeitfaehig -- vier zentrale Datensstroeme:**
1. **Kundendaten:** Ereignisgesteuert aus Reservierungssystem, Vielfliegerprogramm, Firmenwebsite
2. **Flugdaten:** Direkt von Maschinen aus der Luft uebertragen
3. **Reservierungsdaten:** Stuendlich aus Reservierungssystem ins DWH
4. **Check-In-Daten:** Zunaechst gesammelt bei Tuerenschliessung, spaeter einzelne Schritte fuer jeden Passagier in Echtzeit

**Konkrete RTBI-Anwendungen:**
- Preise in Echtzeit anpassen und Auswirkungen direkt beobachten
- Kontingente fuer Preisniveaus festlegen
- Bei technischem Problem: Betroffene Passagiere mit fehlenden Reservierungen bei anderen Airlines schnell identifizieren und nachholen, bevor Kunden etwas bemerken
- Wertvolle Kunden an jedem Kundenkontaktpunkt sofort identifizieren und bevorzugt behandeln
- Auf Verspaetungen fuer wertvollste Kunden reagieren

**Unternehmenskultur als Erfolgsfaktor:**
- Offener Datenzugang: Alle auf Anwendungsseite erhielten Zugang zum DWH (sofern keine wichtigen Gruende dagegen sprachen)
- 2007: Ueber 1.400 Mitarbeitende in verschiedenen Niederlassungen mit DWH-Zugang
- Stetige Ausdehnung auf weitere Abteilungen (z. B. Personalabteilung, technische Zuverlaessigkeitsueberwachung)
- Globale Ausdehnung (Japan: Reisebueros uebermittelten Daten erst 30 Tage vor Abflug en-bloc, erforderte angepasste Analyseroutinen)

**Prozessverbesserung -- Reklamationsprozess (vorher/nachher):**

| Vorher | Nachher (mit RTBI) |
|--------|-------------------|
| Kunde wendet sich an Reservierungsabteilung statt Kundenbetreuung | Agent erfasst Fall direkt im System |
| Reservierungsagent leitet Fall weiter | System ermittelt mittels BRE auf Basis von Falldetails, historischen Kundendaten und Ticketinformationen eine Kompensation |
| Inkompatible Systeme: Ausdruck aus internem System, Handeingabe ins Kundenbetreuungssystem | Agent bestaetigt Vorschlag direkt |
| Langer Prozess, hohe Latenz | Kunde erhaelt in quasi Echtzeit am Telefon Mitteilung ueber Loesung |

---

## Definitionstabelle

| Begriff | Definition |
|---------|-----------|
| biMM | Business Intelligence Maturity Model -- Reifegradmodell zur Einordnung von BI-Loesungen in den Dimensionen Fachlichkeit, Technik und Organisation (Chamoni & Gluchowski, 2004) |
| BI 2.0 | Naechste Version der BI, inspiriert vom Web 2.0; umfasst u. a. proaktive Benachrichtigungen, Echtzeit-Zugriff, Advanced Analytics, BIaaS, In-Memory Analytics (Nelson, 2010) |
| BI 3.0 | BI 2.0 plus Verarbeitung mobiler und sensorbasierter Daten (Chen et al., 2012) |
| Latenz | Zeitlicher Abstand zwischen Eintreten eines Realweltereignisses und der Reaktion auf die betreffende Information (Hackathorn, 2004) |
| Datenlatenz | Zeit nach Eintreten des Ereignisses bis zur Bereitstellung der Daten fuer die Analyse (Hackathorn, 2004) |
| Analyselatenz | Ueber die Datenlatenz hinaus benoetigte Zeit zur Analyse und Bereitstellung der Ergebnisse (Hackathorn, 2004) |
| Entscheidungslatenz | Ueber die Analyselatenz hinaus benoetigte Zeit zur Verarbeitung der Information und Initiierung einer Handlung (Hackathorn, 2004) |
| Halbwertszeit (Information) | Zeit, in der sich der Wert einer Information halbiert; exponentieller Wertverlust angenommen (Pant & Ravichandran, 2001) |
| RTBI | Right-Time Business Intelligence -- wirtschaftlich optimale (nicht minimal kurze) Latenzen fuer einzelne Prozesse/Informationstypen (Hackathorn, 2004) |
| BAM | Business Activity Monitoring -- Echtzeitanalyse auf operativer Ebene mit fuenf Komponenten: Integrator, dynamischer Datenspeicher, KPI-Manager, DM-Werkzeuge, BRE (Golfarelli et al., 2004) |
| SSBI | Self-Service Business Intelligence -- BI-Nutzung ueber bekannte Oberflaechen (z. B. Browser) ohne clientseitige Installation, in verschiedenen Intensitaetsstufen (Alpar & Schulz, 2016) |
| CPM | Corporate Performance Management -- integrierte Unternehmenssteuerungsarchitektur, die verschiedene Managementunterstuetzungssysteme aufeinander abstimmt (Oehler, 2006) |
| MBI | Mobile Business Intelligence -- mobile Nutzung von BI unabhaengig von Zeit und Ort (Cowie & Burstein, 2007) |
| BYOD | Bring Your Own Device -- Nutzung privater Endgeraete fuer Geschaeftszwecke |
| BIaaS | Business Intelligence as a Service -- Betrieb des BI-Systems als externe Dienstleistung ueber das Internet |
| Cloud-BI | Auslagerung des BI-Systems in externe Cloud-Infrastruktur |
| SBI | Social Business Intelligence -- Einbettung von Social Media Daten in ein BI-System (Dinter & Lorenz, 2012) |
| CBI | Collaborative Business Intelligence -- bewusste Erweiterung des Analysekreises um interne und externe Werkzeuge sowie Oeffnung der Datenbestaende der Beteiligten (Kaufmann, 2015) |
| Advanced Analytics | "A suite or cluster of analytical applications that helps measure, predict, and optimize organizational performance and customer relationships" (Bose, 2009) |
| Text Mining | Extraktion strukturierter Metadaten aus unstrukturierten Textdokumenten mittels algorithmischer Verfahren |
| Sentiment Analyse | Auffinden von Textstellen, die ein Sentiment (Stimmung) bezueglich eines Themas ausdruecken, mit Erkennung der Polaritaet (positiv/negativ) (Nasukawa & Yi, 2003) |
| Bag-of-Words | Ansatz, bei dem Texte als unstrukturierte Ansammlung von Woertern betrachtet werden; Haeufigkeit einzelner Begriffe wird gezaehlt (Fan et al., 2006) |
| TF-IDF | Term Frequency-Inverse Document Frequency -- Heuristik zur Gewichtung von Termen: Termhaeufigkeit im Dokument multipliziert mit dem Logarithmus der inversen Dokumentfrequenz (Robertson, 2004) |
| Korpus | Sammlung von Dokumenten, auf die sich die Text-Mining-Analyse bezieht |
| In-Memory Analytics | Verlagerung zu analysierender Daten in den Hauptspeicher (RAM) fuer quasi-Echtzeit-Analyse (Acker et al., 2011) |
| CRISP-DM | Cross-Industry Standard Process for Data Mining -- von der Industrie entwickelter Standard fuer DM-Vorgehen mit besonderer Betonung von Business und Data Understanding (Chapman et al., 2000) |
| CRM (analytisch) | Zusammenfuehrung aller Kundendaten zur Erzeugung von Wissen ueber Trends und Beduerfnisse; zukunftsgerichtet |
| CRM (operativ) | Konkrete Umsetzung an der Kundenschnittstelle: Segmentierung, Kampagnen, Vertrieb |
| CRM (kommunikativ) | Planung und Steuerung der Kommunikationskanaele zum Kunden |
| BRE | Business Rule Engine -- beobachtet Ereignisse und leitet auf Basis von Business Rules geeignete Massnahmen ein |
| SOA | Service Oriented Architecture -- modulare Architektur, bei der BI-Komponenten als einzelne Services bereitgestellt werden |

---

## Querverweise

- Siehe auch: wissen/01_grundlagen_bi.md -- Entscheidungsprozess und BI-Leitbild (Einheit 4 baut auf dem handlungsorientierten Entscheidungsprozess auf; RTBI vervollstaendigt den geschlossenen Kreislauf); Geschaeftsmodellbegriff (Fallstudie Newspaper: disruptive Innovation)
- Siehe auch: wissen/02_methoden_instrumente.md -- DM-Verfahren (Entscheidungsbaeume, Clustering, k-means, k-NN), KDD-Prozess, Featurevektoren, Distanzfunktionen, Normierung/Standardisierung, Projektion/Reduktion (alles Grundlagen fuer Text Mining/TF-IDF); Overfitting-Problem (Fallstudie Newspaper: Aufteilung Trainings-/Testdaten)
- Siehe auch: wissen/03_datenhaltung_bereitstellung.md -- DWH-Architektur und ETL-Prozess (Datenlatenz haengt vom DWH-Aktualisierungszyklus ab); Datenqualitaet (Informationsqualitaet als Analogon); Business Rules (BRE als Komponente von BAM); operative vs. dispositive Datenbestaende (RTBI weicht diese Trennung auf)

---

## Typische Pruefungsfragen

### Frage 1: Latenzarten bei der Echtzeit-BI
**Frage:** Erlaeutern Sie die drei Latenzarten (Daten-, Analyse- und Entscheidungslatenz) und ordnen Sie diese in den Kontext der Right-Time Business Intelligence (RTBI) ein. Warum ist es wichtig, zwischen "right-time" und "real-time" zu unterscheiden?

**Musterloesung:** Die **Datenlatenz** ist die Zeit nach Eintreten eines Realweltereignisses, um die betreffenden Daten fuer die Analyse bereitzustellen (Erfassung im operativen System + ETL-Prozess ins DWH). Die **Analyselatenz** ist die darueber hinaus benoetigte Zeit, um die Daten zu analysieren und Ergebnisse den richtigen Personen bereitzustellen. Die **Entscheidungslatenz** ist die weitere Zeit, um die Information zu verarbeiten und eine Handlung zu initiieren. RTBI strebt nicht minimale, sondern wirtschaftlich optimale Latenzen an. Dabei werden Ausgangswert der Information, Halbwertszeit und Kosten der Latenzreduktion beruecksichtigt. Die Unterscheidung ist wichtig, weil Echtzeit ("real-time") perfekte Synchronizitaet meint, die praktisch nicht erreichbar und auch nicht immer wirtschaftlich ist. Fuer Informationen mit langer Halbwertszeit (z. B. Vorjahresumsaetze) waere Latenzreduktion eine Fehlinvestition. "Right-time" ergaenzt, ersetzt aber nicht "real-time".

### Frage 2: biMM-Reifegradmodell
**Frage:** Beschreiben Sie die fuenf Stufen des biMM und ordnen Sie die in Einheit 4 diskutierten Konzepte (RTBI, BAM, SSBI) den Stufen zu.

**Musterloesung:** Stufe 1 (Vordefiniertes Berichtswesen): Statische Berichte, keine Analyse -- im Sinne des Lehrbriefs keine BI. Stufe 2 (BI pro Fachbereich): Inselloesungen, OLAP, abteilungsweite Semantik. Stufe 3 (Unternehmensweite BI): Integrierte Fachbereiche, homogenisierte Semantik, Metadatenmanagement. Stufe 4 (Erweiterte Entscheidungsunterstuetzung): Prozessunterstuetzung, Closed-Loop, DM, Simulationstools. Stufe 5 (Aktives Wissensmanagement): Realtime-Betrieb, adaptives Lernen, Push-Technologie, Verschmelzung operativer und dispositiver Systeme. RTBI und BAM gehoeren primaer zu Stufe 5 (Realtime-faehige Infrastruktur, aktive Komponenten). SSBI ist als Ansatz der verbesserten Zugaenglichkeit uebergreifend ab Stufe 3-4 einzuordnen, erreicht in Kombination mit Cloud und Echtzeit aber Stufe 5.

### Frage 3: TF-IDF
**Frage:** Erlaeutern Sie die TF-IDF-Heuristik. Warum ist eine naive Zaehlung der Worthaeufigkeiten unzureichend und wie loest TF-IDF dieses Problem?

**Musterloesung:** Bei naiver Zaehlung der Worthaeufigkeiten (Term Frequency) dominieren sehr haeufige, aber wenig informative Terme (Artikel, Konjunktionen) die selteneren, aussagekraeftigeren Terme. TF-IDF loest dies durch Gewichtung: Die Termhaeufigkeit im Dokument wird mit dem Informationsgehalt des Auftretens multipliziert. Dieser Informationsgehalt ist der Logarithmus der inversen Dokumentfrequenz -- log(|X| / |X_q_j|). Je seltener ein Term in allen Dokumenten vorkommt, desto hoeher ist sein Informationsgehalt. Terme mit hohem TF-IDF-Wert sind solche, die insgesamt selten, aber in einem bestimmten Dokument haeufig vorkommen -- sie repraesentieren ihr Dokument sehr gut. TF-IDF ist eine Heuristik, die informationstheoretisch begruendbar ist, aber auf Annahmen basiert, die in der Realitaet moeglicherweise nicht zutreffen (Aizawa, 2003).

### Frage 4: Fallstudie "Newspaper Industry" -- Lessons Learned
**Frage:** Welche zentralen Probleme traten in der Fallstudie "Newspaper Industry" auf und welche Lehren lassen sich daraus ziehen?

**Musterloesung:** Das Hauptproblem war die unzureichende Datenbasis. Obwohl das Unternehmen grosse Datenmengen gesammelt hatte, waren diese fuer die formulierten Analyseziele ungeeignet: (1) Haushaltsdaten mussten aus Datenschutzgruenden transformiert werden, wodurch Informationen verloren gingen. (2) Freitextfelder konnten nicht automatisiert verarbeitet werden, da unterschiedliche Formulierungen fuer gleiche Sachverhalte verwendet wurden. (3) Werbedaten waren zu unspezifisch (kein Erfolgsmass). (4) Erhebliche Datenqualitaetsprobleme (Duplikate, unvollstaendige Datensaetze, syntaktisch falsche Feldnutzung, Inkonsistenzen). Von drei geplanten Zielbloecken (Abwanderungspraevention, Cross Selling, neue Perspektiven) konnte nur die Abwanderungspraevention ueberhaupt adressiert werden. Zentrale Lehren: (a) Die Beduerfnisse der Datenanalyse muessen schon bei der operativen Datenerhebung mitgedacht werden. (b) Ohne geeignete Datenbasis kann kein zusaetzliches Wissen generiert werden. (c) Die Wahl des Entscheidungsbaumverfahrens war sinnvoll wegen Visualisierbarkeit und Interpretierbarkeit.

### Frage 5: Continental Airlines -- RTBI-Erfolgsfaktoren
**Frage:** Erklaeren Sie, wie Continental Airlines RTBI eingesetzt hat und welche Rolle die Unternehmenskultur dabei spielte. Erlaeutern Sie den Reklamationsprozess als Beispiel fuer Prozessverbesserung.

**Musterloesung:** Continental Airlines fuehrte 1998 ein DWH ein und machte es 2001 teilweise echtzeitfaehig mit vier Datenstroemen: Kundendaten (ereignisgesteuert), Flugdaten (direkt von Maschinen), Reservierungsdaten (stuendlich) und Check-In-Daten (zunehmend in Echtzeit). Konkrete Anwendungen: Echtzeit-Preisanpassung, schnelle Identifikation betroffener Passagiere bei Problemen, bevorzugte Behandlung wertvoller Kunden. Die Unternehmenskultur war entscheidend: Offener Datenzugang (ueber 1.400 Mitarbeitende mit DWH-Zugang), stetige Ausdehnung auf weitere Abteilungen und international. Beim Reklamationsprozess mussten vorher Faelle von der Reservierung an die Kundenbetreuung weitergeleitet werden, mit Medienbruch (Ausdrucken und Handeingabe). Mit RTBI erfasst der Agent den Fall direkt, das System ermittelt mittels BRE unter Verwendung von Falldetails, historischen Kundendaten und Ticketinformationen automatisch eine Kompensation, die der Agent sofort bestaetigen kann. Der Kunde erhaelt in quasi Echtzeit am Telefon eine Loesung.

### Frage 6: SBI vs. CBI
**Frage:** Grenzen Sie Social Business Intelligence (SBI) und Collaborative Business Intelligence (CBI) voneinander ab. Beschreiben Sie die drei Kooperationsstufen von CBI nach Kaufmann (2015).

**Musterloesung:** SBI bezeichnet die Einbettung von Social Media Daten in ein BI-System -- es werden also externe (Social Media) Daten in das bestehende BI-System integriert. CBI geht weiter: CBI beschreibt die bewusste Erweiterung des Analysekreises um unternehmensinterne und -externe Analysewerkzeuge sowie die Oeffnung der Datenbestaende der Beteiligten (Kaufmann, 2015). Bei CBI findet also eine umfassende Kooperation statt -- nicht nur Datenintegration, sondern auch Teilen eigener Daten/Werkzeuge mit anderen Unternehmen. Die drei Kooperationsstufen nach Kaufmann (2015): (1) Interne Kommunikation: Mehr Team-Mitglieder beteiligt, evtl. ausgewaehlte externe Einheiten; unternehmensinterne Erweiterung personell und technisch. (2) Gemeinschaftliche Datenhaltung: Interne Daten extern bereitgestellt und externe Daten intern einbezogen, ohne Aenderung der Analysevorgehen. (3) Partnerschaftliche Analyse: Die Analyse selbst wird partnerschaftlich vorgenommen, z. B. ueber externe zentralisierte BI-Systeme. Der Kooperationsgrad steigt von Stufe zu Stufe, mit Tendenz zum hoechsten Grad.

---

## Tags

`Einheit4` `Neuere-Entwicklungen` `BI-2.0` `BI-3.0` `biMM` `Reifegradmodell` `RTBI` `Echtzeit-BI` `Latenz` `Datenlatenz` `Analyselatenz` `Entscheidungslatenz` `Halbwertszeit` `BAM` `Business-Activity-Monitoring` `BRE` `SSBI` `Self-Service-BI` `CPM` `Corporate-Performance-Management` `MBI` `Mobile-BI` `BYOD` `BIaaS` `Cloud-BI` `SBI` `Social-BI` `CBI` `Collaborative-BI` `Advanced-Analytics` `Text-Mining` `TF-IDF` `Bag-of-Words` `Sentiment-Analyse` `In-Memory-Analytics` `Predictive-Analytics` `CRM` `CRISP-DM` `Fallstudie-Newspaper` `Fallstudie-Continental-Airlines` `Entscheidungsbaum` `Prozessverbesserung` `Open-Source-BI` `SOA` `Makrotrends`
