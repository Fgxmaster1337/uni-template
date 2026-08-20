# Wiederholungsfragen -- Einheit 4: Neuere Entwicklungen und Anwendungsbeispiele der BI

> Modul 32711 Business Intelligence, FernUniversitaet Hagen
> Quelle: Lehrbrief Einheit 4 + wissen/04_neuere_entwicklungen.md

---

### Aufgabe 1: Erlaeutern Sie die drei Latenzarten (Daten-, Analyse- und Entscheidungslatenz) und ordnen Sie diese in den Kontext der Right-Time Business Intelligence (RTBI) ein. Warum ist die Unterscheidung zwischen "right-time" und "real-time" wichtig?

**Antwort:**
**Datenlatenz** = Zeit nach Eintreten eines Realweltereignisses, um die betreffenden Daten fuer die Analyse bereitzustellen. Umfasst Erfassung im operativen System und ETL-Prozess ins DWH; nach unten begrenzt durch den Aktualisierungszyklus des DWH (Hackathorn, 2004). **Analyselatenz** = darueber hinaus benoetigte Zeit, um Daten zu analysieren und Ergebnisse den richtigen Personen bereitzustellen -- schafft die Grundlage fuer eine Entscheidung. **Entscheidungslatenz** = weitere Zeit, um die Information zu verarbeiten und eine Handlung zu initiieren; in neuerer Literatur ergaenzt um Handlungs- und Wirkungslatenz (Polites, 2006).

RTBI strebt nicht minimale, sondern **wirtschaftlich optimale** Latenzen an. Drei Faktoren bestimmen die akzeptable Latenz: (1) Ausgangswert der Information, (2) Halbwertszeit der Information, (3) Kosten fuer das gewuenschte Latenzniveau. Die Unterscheidung ist zentral, weil "real-time" perfekte Synchronizitaet von Modell und Realitaet meint -- praktisch nicht erreichbar. Fuer Informationen mit langer Halbwertszeit (z. B. Vorjahresumsaetze) waere Latenzreduktion eine Fehlinvestition. "Right-time" ergaenzt, ersetzt aber nicht "real-time".

**Aufgabentyp:** Definition / Diskussion
**Benoetigtes Wissen:** Einheit 4, Kapitel 2.1

---

### Aufgabe 2: Beschreiben Sie die fuenf Stufen des biMM und ordnen Sie die in Einheit 4 diskutierten Konzepte (RTBI, BAM, SSBI) den Stufen zu.

**Antwort:**
Das **biMM** (Business Intelligence Maturity Model, Chamoni & Gluchowski, 2004) umfasst drei Dimensionen: Fachlichkeit, Technik, Organisation.

| Stufe | Bezeichnung | Kernmerkmale |
|-------|-------------|-------------|
| 1 | Vordefiniertes Berichtswesen | Statische Berichte, keine Analysemoeglichkeit, keine einheitliche Semantik -- im Sinne des Lehrbriefs keine BI |
| 2 | BI pro Fachbereich | Inselloesungen, Ad-hoc-Analysen, OLAP, abteilungsweite Semantik |
| 3 | Unternehmensweite BI | Integrierte Fachbereiche, homogenisierte Semantik, Metadatenmanagement, Hub-&-Spokes-Architektur |
| 4 | Erweiterte Entscheidungsunterstuetzung | Prozessunterstuetzung, Closed-Loop, DM, Simulationstools, semi-strukturierte Daten |
| 5 | Aktives Wissensmanagement | Realtime-Betrieb, adaptives Lernen, Push-Technologie, Verschmelzung operativer und dispositiver Systeme |

Einordnung: Stufen 2-3 = klassische BI (Einheit 3). Stufe 4 = moderne BI (alle Einheiten). Stufe 5 war zum Zeitpunkt der biMM-Vorstellung kaum vorgefunden; erst juengere Technik macht sie erreichbar. **RTBI** und **BAM** gehoeren primaer zu Stufe 5 (Realtime-faehige Infrastruktur, aktive Komponenten). **SSBI** ist ab Stufe 3-4 einzuordnen, erreicht in Kombination mit Cloud und Echtzeit aber Stufe 5.

**Aufgabentyp:** Definition / Vergleich
**Benoetigtes Wissen:** Einheit 4, Kapitel 2

---

### Aufgabe 3: Erlaeutern Sie die TF-IDF-Heuristik. Warum ist eine naive Zaehlung der Worthaeufigkeiten unzureichend und wie loest TF-IDF dieses Problem?

**Antwort:**
Bei naiver Zaehlung der Worthaeufigkeiten (Term Frequency) dominieren haeufige, aber wenig informative Terme (Artikel, Konjunktionen wie "der", "und") die selteneren, aussagekraeftigeren Terme. Zwei Probleme: (1) Zu viele verschiedene Terme in grossen Korpora fuehren zu langen Featurevektoren und erhoehten Laufzeiten. (2) Haeufige Terme sagen wenig ueber den Inhalt aus.

**TF-IDF** loest dies durch Gewichtung: Die Termhaeufigkeit im Dokument (TF) wird mit dem Informationsgehalt des Auftretens multipliziert. Dieser Informationsgehalt ist der Logarithmus der **inversen Dokumentfrequenz** (IDF):

- tfreq(d_i, q_j) = Haeufigkeit von q_j in Dokument d_i (Formel 3.1)
- dfreq(q_j) = |X_q_j| / |X| = Anteil der Dokumente, die q_j enthalten (Formel 3.4)
- info(q_j) = log(1 / dfreq(q_j)) = log(|X| / |X_q_j|) (Formel 3.6)
- x_i,j = tfreq(d_i, q_j) * log(1 / dfreq(q_j)) (Formel 3.7)

Terme mit hohem TF-IDF-Wert sind insgesamt selten, aber in einem bestimmten Dokument haeufig -- sie repraesentieren ihr Dokument sehr gut. Attributselektion: Die N_Q Terme mit den hoechsten TF-IDF-Werten werden ausgewaehlt (Jing et al., 2002). TF-IDF ist informationstheoretisch begruendbar, bleibt aber eine Heuristik (Aizawa, 2003; Robertson, 2004).

**Aufgabentyp:** Definition / Berechnung
**Benoetigtes Wissen:** Einheit 4, Kapitel 3.2

---

### Aufgabe 4: Welche zentralen Probleme traten in der Fallstudie "Newspaper Industry" auf und welche Lehren lassen sich daraus fuer den KDD-/CRISP-DM-Prozess ziehen?

**Antwort:**
US-Tageszeitung mit ca. 200.000 Auflage, sinkende Auflagenhoehe, kein DWH/DM vorhanden. Drei Zielbloecke wurden definiert: (1) Abwanderungspraevention, (2) Cross Selling / Upgrades, (3) Neue Perspektiven (potenzielle Neukunden).

Hauptproblem: **unzureichende Datenbasis**. Konkret:
- Haushaltsdaten: Datenschutztransformation fuehrte zu Informationsverlust
- Kontaktdaten: Freitextfelder mit unterschiedlichen Formulierungen fuer gleiche Sachverhalte -- auch Textanalyseverfahren lieferten keine Loesung
- Werbedaten: Zu unspezifisch, kein Erfolgsmass vorhanden
- Datenqualitaetsprobleme: Duplikate, unvollstaendige Datensaetze, syntaktisch falsche Feldnutzung, Inkonsistenzen bei Integration verschiedener Datenbanken
- Erhebliche Reduktion der verfuegbaren Datensaetze

Von drei Zielbloecken konnte nur die **Abwanderungspraevention** adressiert werden. Verfahrenswahl: Entscheidungsbaum (statt Regression oder KNN) wegen leichter Visualisierung, einfacher Interpretation und Eignung fuer unternehmensinterne Diskussion. Datenaufteilung: 40% Training, 30% Validierung, 30% Test (gleicher Datensatz fuer Entwicklung und Validierung fuehrt zu Overfitting).

Zentrale Lehren: (a) Beduerfnisse der Datenanalyse muessen **schon bei der operativen Datenerhebung** mitgedacht werden. (b) Ohne geeignete Datenbasis kein Nutzenzuwachs durch DM. (c) "Lehrstueck ueber die Bedeutung einer geeigneten Datenbasis."

**Aufgabentyp:** Transfer / Diskussion
**Benoetigtes Wissen:** Einheit 4, Kapitel 4.2; Einheit 2 (KDD/CRISP-DM)

---

### Aufgabe 5: Erklaeren Sie, wie Continental Airlines RTBI eingesetzt hat und welche Rolle die Unternehmenskultur dabei spielte. Erlaeutern Sie den Reklamationsprozess als Beispiel fuer Prozessverbesserung.

**Antwort:**
Ausgangslage Anfang 1990er: Massive Probleme (Unpuenktlichkeit, Ueberbuchung, Gepaeckverlust, letzter Rang unter den zehn groessten US-Fluggesellschaften). IT-Infrastruktur von Drittanbieter betrieben, nur vorher festgelegte Anfragen verarbeitbar, keine bereichsuebergreifenden Informationsabfragen.

**1998:** Einfuehrung DWH -- Integration von Daten aus verschiedenen Quellen, erstmals ertragorientierte flexible Preispolitik. **2001:** DWH wird teilweise echtzeitfaehig mit vier Datenstroemen:
1. Kundendaten -- ereignisgesteuert aus Reservierungssystem/Vielfliegerprogramm
2. Flugdaten -- direkt von Maschinen aus der Luft
3. Reservierungsdaten -- stuendlich ins DWH
4. Check-In-Daten -- zunehmend in Echtzeit (einzelne Schritte pro Passagier)

Konkrete Anwendungen: Echtzeitpreisanpassung, schnelle Identifikation betroffener Passagiere bei technischen Problemen, sofortige Erkennung wertvoller Kunden an jedem Kontaktpunkt.

**Unternehmenskultur** als Erfolgsfaktor: Offener Datenzugang -- alle auf Anwendungsseite erhielten Zugang zum DWH (sofern keine wichtigen Gruende dagegen sprachen). 2007: ueber 1.400 Mitarbeitende mit DWH-Zugang. Stetige Ausdehnung auf weitere Abteilungen und international (Japan: angepasste Analyseroutinen noetig).

**Reklamationsprozess:**
- Vorher: Kunde wendet sich an Reservierung statt Kundenbetreuung. Durch inkompatible Systeme: Ausdruck, Handeingabe -- langer Prozess, hohe Latenz.
- Nachher: Agent erfasst Fall direkt im System. BRE ermittelt auf Basis von Falldetails, historischen Kundendaten und Ticketinformationen automatisch eine Kompensation. Agent bestaetigt direkt. Kunde erhaelt in quasi Echtzeit am Telefon die Loesung.

Kernaussage: RTBI-Potenzial wird erst voll ausgeschoepft, wenn nicht nur bestehende Prozesse unterstuetzt, sondern auch **veraendert** werden.

**Aufgabentyp:** Transfer / Diskussion
**Benoetigtes Wissen:** Einheit 4, Kapitel 4.3

---

### Aufgabe 6: Grenzen Sie Social Business Intelligence (SBI) und Collaborative Business Intelligence (CBI) voneinander ab. Beschreiben Sie die drei Kooperationsstufen von CBI nach Kaufmann (2015).

**Antwort:**
**SBI** (Dinter & Lorenz, 2012) = Einbettung von Social Media Daten in ein BI-System. Es werden also externe Daten (aus sozialen Medien) in das bestehende BI-System integriert. Die Datenintegration ist einseitig.

**CBI** (Kaufmann, 2015) = bewusste Erweiterung des Analysekreises um unternehmensinterne und -externe Analysewerkzeuge sowie die Oeffnung der eigenen Datenbestaende. Bei CBI findet eine **umfassende Kooperation** statt -- nicht nur Datenintegration, sondern auch Teilen eigener Daten und Werkzeuge mit anderen Unternehmen.

Drei Kooperationsstufen (steigender Kooperationsgrad):
1. **Interne Kommunikation:** Mehr Team-Mitglieder an der BI-Nutzung beteiligt, auch ausgewaehlte externe Einheiten. Unternehmensinterne Erweiterung personell und technisch.
2. **Gemeinschaftliche Datenhaltung:** Interne Daten zur externen Nutzung bereitgestellt, externe Daten intern einbezogen -- ohne Aenderung der Analysevorgehen.
3. **Partnerschaftliche Analyse:** Die Analyse selbst wird partnerschaftlich vorgenommen, z. B. ueber externe zentralisierte BI-Systeme.

Der Kooperationsgrad tendiert von Stufe zu Stufe hoeher (Kaufmann, 2015).

**Aufgabentyp:** Vergleich / Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 3.1

---

### Aufgabe 7: Beschreiben Sie das konzeptuelle Modell fuer den Wertbeitrag der BI nach Popovic et al. (2010). Wie entsteht Unternehmensleistung aus BI?

**Antwort:**
Wirkungskette nach Popovic et al. (2010):

**BI-Reifegrad** -> **Informationsqualitaet** -> (+ organisationale Faktoren) -> **Verwendung in Prozessen** -> **Unternehmensleistung**

Ein erhoehter BI-Reifegrad (im Sinne des biMM) fuehrt zu erhoehter Informationsqualitaet. Kriterien dafuer: Genauigkeit, Zeitnaehe, Menge, Verstaendlichkeit, knappe und konsistente Darstellung (analog zur Datenqualitaet aus Einheit 3). Erhoehte Informationsqualitaet allein genuegt aber nicht -- zusaetzlich muessen **organisationale Faktoren** gegeben sein: Strategic Alignment und eine Kultur der kontinuierlichen Verbesserung. Erst beides zusammen bedingt, dass die bereitgestellte Information tatsaechlich in Prozessen genutzt wird, was zu besserer Unternehmensleistung fuehrt.

Kernaussage: Der Wert der BI entsteht indirekt ueber die Anwendung in Prozessen -- BI als Mittel zur Entscheidungsunterstuetzung bezieht ihren Wert daraus, dass die betreffenden Entscheidungen zu effektiver und effizienter Wertschoepfung beitragen (Willams & Williams, 2003).

**Aufgabentyp:** Definition / Transfer
**Benoetigtes Wissen:** Einheit 4, Kapitel 2

---

### Aufgabe 8: Beschreiben Sie die vier moeglichen Ausgestaltungen des Verhaeltnisses von BI-Systemen und Prozessen. Inwiefern stellt die vierte Ausgestaltung einen Paradigmenwechsel dar?

**Antwort:**
Vier Ausgestaltungen mit zunehmendem direktem Einfluss auf operative Prozesse:

1. **Strategische Prozesse verwenden den Output des BI-Systems.** Klassisches DSS/MIS-Verstaendnis -- BI liefert Information fuer strategische Entscheidungen.
2. **Strategische Verwendung gestaltet operative Prozesse.** Der Einfluss der BI ist langfristig und indirekt. BI ist an den operativen Prozessen nicht unmittelbar beteiligt.
3. **Operative Prozesse werden ihrem Ergebnis nach ueberwacht.** BI hat kurzfristige Effekte auf das operative Geschaeft, wirkt aber immer noch indirekt ueber Managementprozesse (vgl. BAM).
4. **BI-Systeme beeinflussen operative Prozesse und Systeme direkt.** Dies stellt einen **Paradigmenwechsel** dar (Sandu, 2008).

Der Paradigmenwechsel liegt darin, dass die traditionelle Trennung zwischen operativen und dispositiven Systemen aufgeweicht wird. BI ist nicht mehr nur passives Analysewerkzeug, sondern reagiert aktiv auf Ereignisse, macht Entscheider aufmerksam und schlaegt Massnahmen vor. Die Ruecktransformation von Informationen in Handlungen -- der geschlossene RTBI-Kreislauf -- ermoeglicht direkten Einfluss auf das operative Geschaeft.

**Aufgabentyp:** Vergleich / Diskussion
**Benoetigtes Wissen:** Einheit 4, Kapitel 2

---

### Aufgabe 9: Erlaeutern Sie die fuenf Komponenten eines BAM-Systems nach Golfarelli et al. (2004) und ordnen Sie BAM in den geschlossenen RTBI-Kreislauf ein.

**Antwort:**
BAM (Business Activity Monitoring) dient der Echtzeitanalyse auf operativer Ebene im Rahmen des CPM. Fuenf Komponenten:

1. **Integrator:** Integriert Daten aus dem DWH nahezu in Echtzeit mit Daten aus anderen Systemen (CRM, ERP).
2. **Dynamischer Datenspeicher:** Haelt die integrierten Daten fuer den Zeitraum der Analyse vor.
3. **KPI-Manager:** Berechnet gewuenschte KPIs aus den Daten und stellt sie zur Verfuegung.
4. **DM-Werkzeuge:** Geeignet fuer historische Daten im DWH und dynamische Daten.
5. **Business Rule Engine (BRE):** Beobachtet Ereignisse und leitet auf Basis von Business Rules geeignete Massnahmen ein (z. B. gezielte Information bestimmter Personen).

BAM umfasst nicht lediglich die Ueberwachung einzelner Geschaeftsprozesse, sondern ermoeglicht eine **integrierte Analyse verteilter Aktivitaeten**. Die verstaerkte Datenintegration verringert die Datenlatenz. Der Rueckbezug (BRE, aktive Benachrichtigungen, Handlungsempfehlungen) schafft den **geschlossenen Kreislauf** und deckt den Steuerungsaspekt des CPM ab. Die Datenintegrationsschicht verbindet operative und analytische Schicht in eine Richtung; das Feedback stellt die andere Richtung dar -- zusammen ergibt sich der geschlossene RTBI-Kreislauf.

**Aufgabentyp:** Definition / Transfer
**Benoetigtes Wissen:** Einheit 4, Kapitel 2.2

---

### Aufgabe 10: Was ist SSBI (Self-Service Business Intelligence)? Beschreiben Sie die vier Intensitaetsstufen und die zentrale Herausforderung.

**Antwort:**
SSBI hat sich unter denselben Zielen wie die klassische BI entwickelt. Nutzung ueber bekannte Oberflaechen (z. B. Webbrowser) ohne clientseitige Softwareinstallation (Alpar & Schulz, 2016). Die Datenhaltung kann in die Cloud verschoben werden.

Vier Intensitaetsstufen (steigender Grad der Selbstbestimmtheit):
1. **Lesen** von Inhalten -- auch in klassischer BI moeglich.
2. **Erstellen** von Inhalten -- ebenfalls in klassischer BI enthalten.
3. **Neue Quellen hinzuziehen** und mit vorhandenen kombinieren -- hier entstehen neue Risiken: unterschiedliche Datenqualitaet, sich ueberschneidende Datensaetze.
4. **Mashups erstellen** -- bereits programmierte Elemente/Funktionalitaeten werden fuer den aktuellen Gebrauch kombiniert; erleichtert durch entsprechende Oberflaeche.

Zentrale Herausforderung: Das jeweils **passende Mass an Sicherheitsvorkehrungen** treffen, ohne die SSBI-Systeme sicherheitskritisch oder unbenutzbar zu machen. SSBI-Systeme unterscheiden sich von klassischen BI-Systemen vor allem durch hoehere Skalierbarkeit und an die jeweiligen Kenntnisse angepasste Nutzungsoberflaechen.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 2.2

---

### Aufgabe 11: Beschreiben Sie das phasenorientierte MBI-Vorgehensmodell. Welche drei uebergreifenden Aspekte und welche drei Rollen sind ueber alle Phasen relevant?

**Antwort:**
Das MBI-Vorgehensmodell (in Erweiterung von Hansen, 1998) umfasst vier Phasen:

| Phase | Kernaufgaben |
|-------|-------------|
| 1. Analysephase | Kosten-Nutzen-Berechnung; grundsaetzliche Klaerung, ob Nutzen Kosten rechtfertigt |
| 2. Designphase | Auswahl/Gestaltung von Hard-/Software; Beruecksichtigung von Anzeigebeschraenkungen, Kompatibilitaet, IT-Sicherheit |
| 3. Realisierungsphase | Inbetriebnahme; Sicherheitskonzept; BYOD-Entscheidung; Schulung der Mitarbeitenden; MBI-Governance |
| 4. Betriebs-/Weiterentwicklungsphase | Kontinuierliche Ueberwachung; Anpassung an technische Entwicklungen und geaenderte Anforderungen |

Drei uebergreifende Aspekte ueber alle Phasen: (1) **Langfristigkeit**, (2) **Business/IT-Alignment**, (3) **Kostenkontrolle**. Alle Entscheidungen sollten hinsichtlich dieser drei Punkte ueberprueft werden.

Drei Rollen:
- **Organisatorische Seite:** Uebergeordnete Kontrollfunktion, Abstimmung mit Gesamtunternehmensstrategie, Anstoss des Projekts, Zuteilung von Rollen.
- **Fachliche Seite:** Bedarfsdefinition, Anforderungen an das System. Grosse Bedeutung in Analyse- und Betriebsphase. Fehlerhafte Bedarfserhebung kann zum Scheitern fuehren.
- **Technische Seite:** IT-Abteilung und ggf. externe Dienstleistung. Umsetzung, Leistungsueberwachung. Aktivitaeten in Phasen 2-4.

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 2.3

---

### Aufgabe 12: Was ist BYOD und welche Vor- und Nachteile ergeben sich daraus im Kontext von MBI? Nennen Sie die Sicherheitsrisiken nach Friedman und Hoffman (2008).

**Antwort:**
**BYOD** (Bring Your Own Device) = Nutzung privater Endgeraete fuer Geschaeftszwecke.

Vorteile:
- Kein Umlernen noetig (eigenes Geraet)
- Hoehere Akzeptanz und Produktivitaet
- Kosteneinsparungen (Unternehmen muss weniger investieren)

Nachteile:
- Datenschutz- und Datensicherheitsbedenken
- Virengefahr bei externem Zugriff auf Unternehmensdaten
- Sensible Informationen auf privat genutzten Geraeten

Sicherheitsrisiken nach Friedman und Hoffman (2008):
1. Erhoehte Gefahr von Verlust/Diebstahl mobiler Geraete bedingt durch Mobilitaet
2. Kommunikation ueber oeffentliche, ungeschuetzte Netzwerke (anfaellig fuer Abhoeren, IP-Manipulation)
3. Erhoehte Virengefahr ausserhalb der Unternehmens-Firewall bei begrenztem integriertem Virenschutz
4. Begrenzte finanzielle und personelle IT-Ressourcen fuer mobile Sicherheit (Fokus auf internes IT-System)

Unabhaengig von BYOD ist ein Sicherheitskonzept in der Realisierungsphase zu erstellen, abgeleitet aus den Richtlinien der uebergeordneten Informationslogistik.

**Aufgabentyp:** Definition / Diskussion
**Benoetigtes Wissen:** Einheit 4, Kapitel 2.3

---

### Aufgabe 13: Grenzen Sie Open Source BI, BIaaS und Cloud-BI voneinander ab. Was sind die acht Dimensionen cloudbasierter BI nach Schirm et al. (2015)?

**Antwort:**
Drei Auspraegungen der BI jenseits von Organisationsgrenzen:

- **Open Source BI:** Betrieb inhouse, kein direkter Support, Kompetenzen intern oder zugekauft. Unternehmen bezahlt nicht fuer das System, sondern fuer den Betrieb.
- **BIaaS (Business Intelligence as a Service):** Betrieb als Dienstleistung ausgelagert. BI-System als externer Service konfiguriert und ueber das Internet zugaenglich. Auch das Analyseteam kann extern zur Verfuegung stehen.
- **Cloud-BI:** Auslagerung in bestehende externe Infrastruktur. Unterscheidung: (a) Selbstadministriertes BI-System in der Cloud, (b) zusaetzliche Auslagerung der Administration (= BIaaS).
- SOA-basierte BI als Mischform: Einzelne Komponenten (Services) nach Baukastenprinzip, intern oder als Dienstleistung betrieben.

Acht Dimensionen cloudbasierter BI (Schirm et al., 2015):
1. **Agilitaet** -- Flexibilitaet, Skalierbarkeit
2. **Kosten** -- Kosteneinsparung, Pay-per-Use
3. **Positive Auswirkungen auf Kerngeschaeft** -- Konzentration auf Kernkompetenzen, Wettbewerbsvorteile
4. **Performance** -- Verarbeitungsgeschwindigkeit, In-Memory, Echtzeit
5. **Customizing** -- Entwicklungsmoeglichkeiten, Administration, funktionale Erweiterbarkeit, SSBI
6. **Usability / Vernetztes Cloud-Computing** -- Interoperabilitaet, Nutzung von Drittanbieter-Services, Mobilitaet
7. **Zuverlaessigkeit und Vertrauen** -- Verfuegbarkeit, Zuverlaessigkeit, Support, Security
8. **Cloudbetrieb** -- On-the-fly Updates, Umsetzung von Standards

**Aufgabentyp:** Vergleich / Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 3.1

---

### Aufgabe 14: Erlaeutern Sie die drei Vorgehensweisen zur Integration von strukturierten Daten und unstrukturierten Inhalten nach Baars und Kemper (2008).

**Antwort:**
Begriffliche Unterscheidung (Albescu et al., 2008): "Inhalte" = unstrukturierte Daten; "Daten" impliziert bereits eine Struktur. Laut Endeca (2011) machen unstrukturierte Inhalte ca. 80% des fuer Unternehmen relevanten Datenvolumens aus.

Drei Vorgehensweisen:

1. **Integrierte Praesentation:** Strukturierte Daten und unstrukturierte Inhalte werden weiterhin in getrennten Quellen gehalten. Integration nur auf Praesentationsebene durch gekoppelte Navigations-/Suchfunktionen (z. B. aus der aktuellen OLAP-Sicht wird automatisch eine Suchanfrage an die Inhaltsdatenbank generiert). Vorteil: Geringer Aufwand, etablierte Methoden weiterverwendbar. Nachteil: Keine dauerhafte Verknuepfung.

2. **Analyse von Inhaltssammlungen (Extraktion von Metadaten):** Metadaten (Autor, Erstellungszeitpunkt, Schlagwoerter, Klassifizierungen) werden manuell oder algorithmisch (z. B. Text Mining) extrahiert und in strukturierte Datenbank integriert. Ermoeglicht dauerhafte Verknuepfung von Daten und Inhalten. Richtung: unstrukturiert -> strukturiert.

3. **Verbreitung von Analyseergebnissen als Inhalte:** Umgekehrte Richtung -- strukturierte Analyseergebnisse werden in menschenlesbarer Form als unstrukturierte Inhalte aufbereitet. Nicht nur Ergebnisse, sondern auch Vorgehensweisen werden verbreitet (Wissen ueber BI an sich). Idealerweise Anbindung an KM-System. Richtung: strukturiert -> unstrukturiert.

**Aufgabentyp:** Definition / Vergleich
**Benoetigtes Wissen:** Einheit 4, Kapitel 3.2

---

### Aufgabe 15: Was ist Text Mining? Erlaeutern Sie den Bag-of-Words-Ansatz und erklaeren Sie die Begriffe Korpus, Instanz, Lexikon, Term und Featurevektor.

**Antwort:**
**Text Mining** extrahiert aus unstrukturierten Textdokumenten strukturierte Metadaten. Moderne Systeme koennen identifizieren: Namen (Personen, Unternehmen, Produkte, Orte), Beziehungen zwischen Entitaeten, typische Begriffe/Saetze (Thema), sowie Stimmungen mittels **Sentiment Analyse** (Vergleich identifizierter Schluesselbegriffe mit Datenbank von Begriffskonnotationen: positiv, neutral, negativ; Nasukawa & Yi, 2003).

**Bag-of-Words-Ansatz** (Fan et al., 2006): Texte werden als unstrukturierte Ansammlung von Woertern betrachtet ("Beutel"). Anstelle echten Textverstaendnisses wird gezaehlt, wie oft einzelne Begriffe vorkommen.

Begriffe:
- **Korpus (D):** Sammlung von Dokumenten, auf die sich die Analyse bezieht. Entspricht dem Konzept X.
- **Instanz:** Einzelnes Dokument d_i aus dem Korpus.
- **Lexikon:** Menge der im Korpus vorkommenden Woerter = Q.
- **Term:** Einzelnes Wort q_j aus dem Lexikon.
- **Featurevektor:** Strukturierte Repraesentation eines Dokuments als Vektor x_i. Ueberführung der unstrukturierten Textrepraesentation in eine strukturierte Vektorrepraesentation.

Durch den Featurevektor wird das Dokument den DM-Verfahren aus Einheit 2 zugaenglich (Klassifikation, Clustering).

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 3.2

---

### Aufgabe 16: Erlaeutern Sie die zentroidenbasierte Klassifikation von Dokumenten. Warum wird der Featurevektor normiert und wie wird die Distanz zweier Dokumente berechnet?

**Antwort:**
Die Normierung ist noetig, weil der Betrag ||x_i|| mit der Textlaenge von d_i waechst. Da die Klasse eines Dokuments unabhaengig von der Laenge sein sollte, wird der Featurevektor normiert:

x'_i,j = x_i,j / ||x_i|| (Formel 3.8)

Nach Normierung liegt jedes Dokument auf der Einheitshyperkugel (||x'_i|| = 1).

**Distanz** zweier Dokumente = Winkel zwischen den zugehoerigen normierten Vektoren:

dist(d_i, d_j) = arccos(<x_i, x_j> / (||x_i|| * ||x_j||)) (Formel 3.9)

Nach Normierung ist der Nenner = 1, es bleibt das Skalarprodukt (Han & Karypis, 2000).

**Zentroid** einer Klasse c_k: Mittelwert aller Featurevektoren, die zur Klasse gehoeren (Formeln 3.10-3.12). Die **Klassifizierungsfunktion** weist unbekannten Instanzen die Klasse zu, deren Zentroid der Instanz am aehnlichsten ist:

h(x_i) = arg min_{c_k}(dist(x_i, mu_{c_k})) = arg max_{c_k}(<x_i, mu_{c_k}>) (Formel 3.13)

Parallelen zu k-means und k-Nearest Neighbour aus Einheit 2, aber als ueberwachtes Klassifikationsverfahren: Bekannte Klassen aus Trainingsdaten werden genutzt, um unbekannte Dokumente einzuordnen.

**Aufgabentyp:** Berechnung / Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 3.2; Einheit 2 (Distanzfunktionen, Clustering)

---

### Aufgabe 17: Was ist In-Memory Analytics und inwiefern ist es ein Enabler fuer RTBI?

**Antwort:**
**In-Memory Analytics** (Acker et al., 2011): "A technology that will allow operational data to be held in a single database that can handle all the day-to-day customer transactions and updates, as well as analytical requests -- in virtually real time."

Technisch: Verlagerung der zu analysierenden Daten von langsamen Massenspeichern (Festplatten) in den schnelleren Hauptspeicher (RAM). Erste Forschung seit den 1980er Jahren.

- **Treiber:** Wachsende Datenmengen mit haeufigen, zeitintensiven Ladevorgaengen
- **Enabler:** Stark fallende Hardwarepreise, die genuegend RAM ermoeglichen

Wirkung als RTBI-Enabler:
1. Daten aus operativen Systemen muessen **nicht erst in dispositive Systeme uebertragen** werden, bevor sie der Analyseschicht zur Verfuegung stehen.
2. **Erhebliche Senkung der Datenlatenz** -- der wesentliche Flaschenhals der traditionellen BI (DWH-Aktualisierungszyklus) wird stark reduziert.

In-Memory Analytics ist somit ein wesentlicher Schritt hin zur Echtzeit-BI bzw. RTBI und Enabler fuer viele der in Einheit 4 beschriebenen Anwendungen (BAM, CPM, operative BI).

**Aufgabentyp:** Definition / Transfer
**Benoetigtes Wissen:** Einheit 4, Kapitel 3.3

---

### Aufgabe 18: Beschreiben Sie CPM (Corporate Performance Management) nach Oehler (2006). Nennen Sie die fuenf Elemente des Controllingkonzepts als fachliche Basis.

**Antwort:**
**CPM** (Oehler, 2006) beschreibt eine integrierte Unternehmenssteuerungsarchitektur. Verschiedene Managementunterstuetzungssysteme (BI, ERP, CRM, KM, Business Process Management) werden aufeinander abgestimmt und zu einem gemeinsamen System integriert.

Abgrenzung zur traditionellen BI: CPM bezieht ueber den traditionellen BI-Begriff hinaus auch die **Steuerung von Prozessen** ein und integriert ISe auch auf operativer Ebene. Durch die Einbeziehung der operativen Ebene entsteht eine **Rueckkopplung** -- Ergebnisse des CPM wirken ueber automatische Regelungsmechanismen und wohlinformierte Handlungen auf das operative Geschaeft zurueck. CPM ist das konsequente Weiterdenken des geschlossenen RTBI-Kreislaufs zu einem ganzheitlichen System.

Fuenf Elemente des Controllingkonzepts als fachliche Basis:
1. **Controllingobjekte:** Was wird gesteuert?
2. **Wirkungsbeziehungen:** Wie haengen die Objekte zusammen, wie wirken sie aufeinander?
3. **Metriken:** Wodurch lassen sich die Objekte operationalisieren, d. h. messbar machen?
4. **Rollen mit Aufgaben:** Wer nimmt die Informationsversorgung wahr, mit welchen Kompetenzen und Verantwortlichkeiten?
5. **Berichtswesen:** Wie werden Vorgaben, Standards, Ergebnisse und Massnahmen dokumentiert?

Ziel des Controllings nach Reichmann (2011): Verbesserung der "Entscheidungsqualitaet auf allen Fuehrungsstufen".

**Aufgabentyp:** Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 2.2

---

### Aufgabe 19: Erlaeutern Sie die Begriffe BI 1.0, BI 2.0 und BI 3.0 nach Chen et al. (2012) und Nelson (2010). Welche Prinzipien des Web 2.0 koennen fuer BI 2.0 adaptiert werden?

**Antwort:**
Evolutionsstufen nach Chen et al. (2012):
- **BI 1.0:** Klassisches DM, Predictive Analytics, In-Memory Analytics, BI-gestuetztes CPM. Trotz aktiver Erforschung dieser Verfahren: BI auf Basis strukturierter Daten.
- **BI 2.0:** Zusaetzliche Beruecksichtigung webbasierter und unstrukturierter Inhalte. Kennzeichnend: Integration von Text Mining, Inhaltsanalyse.
- **BI 3.0:** Zusaetzlich mobile und sensorbasierte Daten (vgl. MBI, Kapitel 2.3).

BI 2.0 nach Nelson (2010) umfasst u. a.: Proaktive Benachrichtigungen, Echtzeit-Zugriff, Advanced Analytics, Unternehmensintegration, verbesserte Visualisierungen, BIaaS, In-Memory Analytics, OpenSource BI.

Adaptierbare Web-2.0-Prinzipien (Nelson, 2010):
1. Entwickeln eigener "Apps" fuer das BI-System
2. Zeitnahes Weiterempfehlen, Abonnieren und Bewerten von Inhalten
3. Gemeinsames Kommentieren, Bearbeiten und Kategorisieren durch mehrere Personen
4. Schnelles Veroeffentlichen eigener Interpretationen und Aufbereitungen
5. Meta-Analyse des Nutzungsverhaltens im BI-System

Zwei uebergreifende Trends: (1) Neue BI-Technologien beguenstigen sich gegenseitig und werden staerker verknuepft. (2) BI wird durch kuerzere Entwicklungszyklen insgesamt dynamischer.

**Aufgabentyp:** Definition / Vergleich
**Benoetigtes Wissen:** Einheit 4, Kapitel 1

---

### Aufgabe 20: Beschreiben Sie die Rolle von BI im analytischen CRM. Welche Fragestellungen koennen ueber den gesamten Kundenlebenszyklus mit BI unterstuetzt werden?

**Antwort:**
BI im Marketing ist besonders geeignet, wenn: (1) grosse Datenbestaende als Entscheidungsbasis vorliegen, in denen Beziehungen/Muster vorhanden sein koennten; (2) Daten in mehreren verschiedenen Quellen (auch extern) vorliegen, die detaillierteres Bild ueber Stimmungen, Trends und Beduerfnisse zulassen.

Drei CRM-Typen:
- **Analytisches CRM:** Zusammenfuehrung aller Kundendaten, Wissen ueber Trends erzeugen, Retention Management, Betrugsfrueherkennung; zukunftsgerichtet.
- **Operatives CRM:** Konkrete Kundensegmente, Marktanalysen, Kampagnen; an der Kundenschnittstelle.
- **Kommunikatives CRM:** Planung der Kommunikationskanaele; durch Web 2.0 an Bedeutung gewonnen; bidirektional.

BI-gestuetzte Fragestellungen ueber den Kundenlebenszyklus:

**Neukundengewinnung:**
- Welche Trends lassen sich aus internen und externen Daten erkennen?
- Welche Verbesserungsvorschlaege kommen von Nicht-Kunden?
- Welche Luecken im Kundenprozess koennen adressiert werden?

**Pflege des Kundenbestands:**
- Welche zusaetzlichen Angebote/Dienstleistungen sind fuer den Kunden interessant?
- Welche Kundenbindungsprogramme sind wirksam?
- Welche Multiplikatoren koennen identifiziert werden?

**Retention Management:**
- Anforderungen an Kundenkommunikation auf Online-Plattformen
- Stimmungsanalyse (vgl. Sentiment Analyse)
- Benchmarking von Massnahmen mit Konkurrenten

Ergaenzend: Collaborative CRM (Ueberschreiten von Abteilungs-/Unternehmensgrenzen) und Social CRM (Interaktionen in sozialen Netzwerken; Alt & Reinhold, 2012).

**Aufgabentyp:** Transfer / Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 4.1

---

### Aufgabe 21: Beschreiben Sie den geschlossenen RTBI-Kreislauf und seine drei Schichten. Wie unterscheidet sich RTBI von traditioneller BI hinsichtlich des Informationsflusses?

**Antwort:**
Die handlungsorientierte RTBI ergaenzt die traditionelle Transformation von Daten in Informationen um die **Ruecktransformation von Informationen in Handlungen**. Ueber diese Handlungen wirkt RTBI direkt zurueck auf die Geschaeftsprozesse, die wiederum neue Daten generieren -- ein geschlossener Kreislauf.

Drei Schichten:
1. **Operative Schicht:** Operative Systeme (CRM, ERP) -- hier entstehen und wirken die Daten/Handlungen.
2. **Datenintegrationsschicht:** Anbindung operativer Systeme an DWH. Bei RTBI: **kontinuierliche** Integration (nicht nur naechtlich), damit Analyse auf aktuellen Daten erfolgt.
3. **Analyseschicht:** Ergaenzt um fortgeschrittene Verfahren; Hauptunterschied zur traditionellen BI: **Feedbacksysteme** (BAM, BRE).

Unterschiede im Informationsfluss:
- **Traditionelle BI:** Datenfluss nur in eine Richtung (operativ -> DWH -> Analyse). Hohe Latenzen, kein systematischer Rueckkanal. Information ist deskriptiv, nicht handlungsorientiert. Direkter Einfluss auf operative Prozesse nicht praktikabel.
- **RTBI:** Bidirektionaler Informationsfluss. Verkuerzte Latenzen in beiden Richtungen. RTBI als Enabler, der operatives Handeln auf Grundlage von BI ueberhaupt erst ermoeglicht. Erst als geschlossener Kreislauf kann BI ihre Rolle im handlungsorientierten Entscheidungsprozess (vgl. Einheit 1) voll erfuellen.

**Aufgabentyp:** Vergleich / Definition
**Benoetigtes Wissen:** Einheit 4, Kapitel 2.1 und 2.2

---

### Aufgabe 22: Erlaeutern Sie das Konzept der Halbwertszeit von Information. Warum wird angenommen, dass Information mit kurzer Halbwertszeit anfaenglich besonders wertvoll ist?

**Antwort:**
**Halbwertszeit von Information** (Pant & Ravichandran, 2001): Information verliert ueber die Zeit an Wert (sie veraltet oder wird ueberholt). Der Wertverlust wird als **exponentiell** angenommen und durch die Zeit charakterisiert, in der sich der Wert halbiert. Verschiedene Informationstypen haben unterschiedliche Halbwertszeiten -- Boersenkurse veralten schneller als Analyseberichte.

Naeherungsweise gilt: Je kuerzer die Halbwertszeit, desto hoeher ist der **anfaengliche Wert** der Information. Intuition: Informationen, die schnell ihren Wert verlieren, muessen einen hohen Ausgangswert haben, um fuer das Unternehmen ueberhaupt relevant zu sein. Die schnelle Verarbeitung solcher Informationen ist daher nicht nur akademisch, sondern hochgradig praxisrelevant.

Daraus folgt: Die Investition in verkuerzte Latenzen lohnt sich besonders bei Informationen mit **kurzer Halbwertszeit und hohem Ausgangswert** (z. B. Echtzeit-Preisdaten, Flugbelegungsdaten). Fuer Informationen mit langer Halbwertszeit (z. B. Vorjahresumsaetze) waere Latenzreduktion hingegen eine Fehlinvestition. Dies ist der Kern des RTBI-Konzepts.

**Aufgabentyp:** Definition / Diskussion
**Benoetigtes Wissen:** Einheit 4, Kapitel 2.1

---

### Aufgabe 23: Nennen Sie die fuenf Forschungsbereiche nach Baars et al. (2014) und ordnen Sie sie den Kapiteln der Einheit 4 zu.

**Antwort:**
Baars et al. (2014) fassen unter dem Begriff **Makrotrends** die Bedingungen zusammen, denen aktuelle BI-Systeme genuegen muessen. Daraus resultieren fuenf Forschungsbereiche:

1. **Integration von BI und Geschaeftsprozessmanagement** -> Kapitel 2 (Wirkung der BI auf Prozesse: RTBI, BAM, CPM)
2. **Ueber Unternehmensgrenzen hinaus kooperativ entwickelte und betriebene BI-Loesungen** -> Kapitel 3.1 (BIaaS, Cloud-BI, SBI, CBI)
3. **Ansaetze zur Verarbeitung semi- und unstrukturierter Daten** -> Kapitel 3.2 (Text Mining, TF-IDF, Bag-of-Words)
4. **Agile Bereitstellung und durch Nutzung gesteuerte BI-Systementwicklung** -> Kapitel 2.2 (SSBI)
5. **BI-Governance** -> Kapitel 2.3 (MBI-Governance als Beispiel)

Zwei uebergreifende Trends: (1) Neue BI-Technologien beguenstigen sich gegenseitig und werden staerker miteinander verknuepft (z. B. mit KM, Web 2.0). (2) BI wird durch kuerzere Entwicklungszyklen und Betrachtungszeitraeume insgesamt dynamischer.

**Aufgabentyp:** Definition / Transfer
**Benoetigtes Wissen:** Einheit 4, Kapitel 1

---

### Aufgabe 24: Vergleichen Sie den CRISP-DM-Prozess mit dem KDD-Prozess aus Einheit 2. Was betont CRISP-DM besonders, und wie zeigt sich dies in der Fallstudie "Newspaper Industry"?

**Antwort:**
**CRISP-DM** (Cross-Industry Standard Process for Data Mining) ist ein von der Industrie entwickelter Standard mit vielen Parallelen zum KDD-Prozess aus Einheit 2. Besondere Betonung:

- **Business Understanding:** DM beginnt mit dem Verstehen der Situation und Ziele des Unternehmens -- nicht mit den Daten. Im KDD-Prozess ist dies weniger explizit herausgearbeitet.
- **Data Understanding:** Explizite Phase im CRISP-DM. Im KDD-Prozess aus Einheit 2 dagegen als Querschnittsaufgabe ueber alle Schritte verstanden.

In der Fallstudie "Newspaper Industry":
- **Business Understanding:** Durchgefuehrt via Fragebogen an alle Unternehmensbereiche. Ergebnis: drei Zielbloecke (Abwanderungspraevention, Cross Selling, neue Perspektiven). Nur haeufig vorkommende Fragen wurden beruecksichtigt.
- **Data Understanding:** Hier offenbarten sich die gravierenden Probleme. Die operativ erhobenen Daten waren fuer die formulierten Analyseziele ungeeignet. Datenschutztransformationen, Freitextfelder, fehlende Erfolgsmasse -- alles erst durch explizites Data Understanding sichtbar geworden.

Kernlektion: Die explizite Trennung von Business und Data Understanding im CRISP-DM haette frueher aufzeigen koennen, dass die Datenbasis fuer zwei von drei Zielbloecken nicht ausreicht. Die Fallstudie bestaetigt die Notwendigkeit beider Phasen.

**Aufgabentyp:** Vergleich / Transfer
**Benoetigtes Wissen:** Einheit 4, Kapitel 4.2; Einheit 2 (KDD-Prozess)
