# INDEX: 32711 BI-Anwendungsaufgabe — BAS Cycling GmbH

## Fallunternehmen: BAS Cycling GmbH

| Merkmal | Detail |
|---------|--------|
| Vollname | BAS Cycling GmbH |
| Kürzel | BAS Cycling |
| Sitz | Neuhagen (kreisfreie Großstadt, NRW, ~200.000 Einwohner) |
| Branche | Fahrradherstellung (Offroad + Straßenräder) |
| Gründung | 1997 |
| Geschäftsführer | Herr S. Rollnix |
| Marktposition | Führender Anbieter hochwertiger Fahrräder |
| Zielgruppe | Professionelle und Hobby-Radsportler |
| Philosophie | Qualität, Kundenzufriedenheit, Nachhaltigkeit |

---

## Unternehmensstruktur

### Produktion
- Aufgeteilt auf mehrere Abteilungen (je spezifische Komponenten/Prozesse)
- Modernste Technologien und Produktionsmethoden
- Höchste Qualitätsstandards

### Vertriebsstruktur

| Region | Vertriebsweg | Direktkundenbest. möglich? |
|--------|-------------|---------------------------|
| DACH (D, A, CH) | Handelsvertreter-Netzwerk (B2B) | NEIN |
| USA | Online-Direkthandel (D2C) | JA |

- DACH: Handelsvertreter beziehen Produkte in großen Mengen und verkaufen in eigenen Geschäften
- USA: Ausschließlich Online-Direktverkauf an Endkunden

---

## Rolle des Bearbeiters

> **BI-Spezialist bei BAS Cycling** (nach erfolgreichem Studienabschluss)

Aufgabenumfang laut Einführung:
1. **Datenaufbereitung** (KDD-Phase I: Vorbereitende Schritte)
2. **Analysen** (KDD-Phase II: Data Mining)
3. **Dashboards und Berichte** (KDD-Phase III: Nachbereitung / Präsentation)
4. Ziel: Daten in wertvolle Erkenntnisse verwandeln → Entscheidungsunterstützung für das Management

Methodischer Rahmen: **KDD-Prozess** (Fayyad 1996) → Einheit 2

---

## Aufgaben-Abschnitte
*(werden ergänzt, sobald weitere Informationen/Fragen vorliegen)*

| Abschnitt | Thema | Status |
|-----------|-------|--------|
| Ausgangssituation | Unternehmensbeschreibung BAS Cycling | ✅ erfasst |
| Unternehmensstruktur | Produktion, Vertrieb DACH/USA | ✅ erfasst |
| Rolleneinführung | BI-Spezialist, Aufgabenumfang (KDD, Dashboards) | ✅ erfasst |
| Software | R/RStudio (Data Mining), Tableau (Aufgabe 4, Dashboards) | ✅ erfasst |
| Fallstudie | Black-Friday-Angebot, Warenkorbanalyse USA-Transaktionen | ✅ erfasst |
| Aufgabe 1 | Auswahl der Daten (KDD-Phase I), Stern-Schema | ⏳ teilweise (Rest folgt) |
| Aufgabe 2 | Datenbereinigung (Kap. 3.3 Einheit 2), SQLite-Datenbank | ⏳ teilweise (Rest folgt) |
| Aufgabe 3 | ? | ⏳ ausstehend |
| Aufgabe 4 | Tableau Dashboard | ⏳ ausstehend |

---

## Schlüsselbegriffe & BI-Relevanz

| Begriff | Relevanz für Modul 32711 |
|---------|--------------------------|
| Handelsvertreter (DACH) | B2B-Daten, keine direkte Kundentransaktionsdaten |
| Online-Direkthandel (USA) | D2C-Transaktionsdaten direkt verfügbar → DWH-Quelle |
| Qualitätsmanagement | → Datenqualität (Einheit 3: Wang & Strong) |
| Produktionseffizienz | → OLAP-Analysen, KPIs (Einheit 3) |
| Kundensegmentierung | → Clusteranalyse, KDD (Einheit 2) |

---

## Verweise auf Kursmaterialien

| Thema | Einheit | Kapitel |
|-------|---------|---------|
| DWH als zentrale Datenbasis | 1, 3 | E1:Kap.3 / E3:Kap.3 |
| ETL-Prozess (Datenintegration) | 3 | Kap. 3.3 |
| Data Mining / KDD | 2 | Kap. 2, 4 |
| OLAP-Analysen | 3 | Kap. 4 |
| Datenqualitätsmanagement | 3 | Kap. 2.3 |
| Business Rules | 3 | Kap. 2.1 |
| RTBI / BAM (Echtzeit) | 4 | Kap. 2.1, 2.2 |

---

## Fallstudie: Black-Friday-Angebot

### Auftraggeber
Herr S. Rollnix (Geschäftsführer, BAS Cycling) per E-Mail

### Kernfrage
> „Welche unserer Produkte im Onlinehandel werden häufig **zusammen gekauft**?"

### Ziel
- Identifikation von Produktgruppen, die häufig gemeinsam erworben werden
- Entwicklung von **Bundle-Angeboten** für den Black Friday
- Datenbasis: **US-Transaktionsdaten** (Online-Direkthandel USA)
- Nebeneffekt: Grundlage für zukünftige Verkaufsstrategien

### BI-Methode → **Assoziationsanalyse / Warenkorbanalyse**
**Apriori-Algorithmus** (Einheit 2, Kap. 4.6)

| Konzept | Bedeutung |
|---------|-----------|
| **Support** | Wie häufig kommt eine Produktkombination vor? |
| **Konfidenz** | Wenn Produkt A gekauft → wie oft auch Produkt B? |
| **Assoziationsregel** | „Wenn A gekauft wird, wird auch B gekauft" |

Verweis auf Kursunterlagen: Einheit 2, Kap. 4.6 „Apriori-Algorithmus"

---

## Aufgabe 1: Auswahl der Daten (KDD-Phase I)

### Thema
Auswahl und Begründung relevanter Daten für spezifische Analysen im KDD-Prozess.

### Datenbasis
- Zugang zu BAS Cycling **Vertriebsdatenbank** (von Herrn Rollnix)
- Datei: **"Aufgabe 1"** (Download aus Moodle)
- Struktur: **Stern-Schema** (Star Schema)

### Stern-Schema Erklärung (laut Aufgabe)
> „Ein Stern-Schema ist ein relationales Datenbankschema für die mehrdimensionale Datenmodellierung [...] für lesende Zugriffe optimiert, hat sich besonders im Kontext von Data Warehouses durchgesetzt."

| Element | Beschreibung |
|---------|-------------|
| **Faktentabelle** (zentral) | Enthält Primärschlüssel aller Dimensionen + eigene Attribute (Messwerte) |
| **Dimensionstabellen** (außen) | Dimension1–N, je mit Primärschlüssel + Attributen; umgeben die Faktentabelle sternförmig |

Kursmaterial-Verweis: Einheit 3, Kap. 4.2 (ROLAP → Star-Schema / Snowflake-Schema)

### Datenbankstruktur: Zwei Stern-Schemata

#### Schema 1: FactAuftragHV (Handelsvertreter, DACH)
| Tabelle | Felder |
|---------|--------|
| **FactAuftragHV** (Fakt) | BestellungNummer🔑, ProduktKey🔑, VertreterKey🔑, LandKey🔑, BestellungDatum, Auftragsmenge, Umsatz |
| DimProdukt | ProduktKey🔑, ProduktBuKey, Modellreihe, ProduktName, Listenpreis, Farbe, Groesse, Gewicht, ProduktGruppeKey, ProduktGruppeBuKey, ProduktGruppeName, ProduktKategorieKey, ProduktKategorieName |
| DimHandelsvertreter | VertreterKey🔑, VertreterNummer, VertreterName, VertreterHauptsitz |
| DimLand | LandKey🔑, LandISOKennung, LandName, LandAnzahlEinwohner |

#### Schema 2: FactAuftragDK (Direktkunden, USA) ← RELEVANT für Black Friday
| Tabelle | Felder |
|---------|--------|
| **FactAuftragDK** (Fakt) | BestellungNummer🔑, ProduktKey🔑, DirektkudeKey🔑, LandKey🔑, Auftragsmenge, Umsatz, BestellungDatum |
| DimProdukt | (identisch zu oben) |
| DimDirektkunden | DirektkudeKey🔑, Vorname, Nachname, Stadt, Bundesstaat, LandKey, Phone1, Phone2, Email, Kunde_seit |
| DimLand | (identisch zu oben) |

### Besonderheiten der Faktentabelle (Beispiel)
- BestellungNummer kann mehrfach vorkommen (Bestellung mit mehreren Produkten)
- Kombination BestellungNummer + ProduktKey ist **eindeutig** (kommt nur 1x vor)
- Beispiel: Bestellung 1002 enthält ProduktKey 135713 (Zeile 1) UND 135891 (Zeile 2)

### Aufgabenstellung
> „Treffen Sie eine fundierte Auswahl von Daten für das Black-Friday-Angebot (beziehen Sie die E-Mail von Herrn Rollnix ein!)"

**Korrekte Datenselektion:**
- ✅ **FactAuftragDK** (USA Direktkunden → Online-Direkthandel)
- ✅ **DimProdukt** (ProduktName / Produktgruppen für Warenkorbanalyse)
- ❌ FactAuftragHV (DACH Handelsvertreter → kein Online-Direkthandel, Herr Rollnix spricht explizit von USA)

**Relevante Felder für Apriori-Algorithmus:**
- BestellungNummer (= Transaktion / "Warenkorb")
- ProduktKey / ProduktName (= Item im Warenkorb)

### Konkrete Fragen
*(folgen noch — nächste Seiten der Aufgabe)*

---

## Software-Anforderungen

| Tool | Zweck | Aufgabe |
|------|-------|---------|
| **R** | Statistik-Programmiersprache, de-facto Standard im Data Mining | Aufgaben 1–3 (KDD, Datenaufbereitung, Analyse) |
| **RStudio** | IDE für R | Aufgaben 1–3 |
| **Tableau Desktop** | BI-Visualisierungssoftware | **Aufgabe 4** (Dashboards) |

### Wichtige R-Grundbefehle (Referenz)

```r
install.packages("Paketname")   # Package installieren
library(Paketname)              # Package laden
setwd('Ordnerpfad')             # Arbeitsverzeichnis setzen
A <- 1                          # Variablenzuweisung (kein strenges Typensystem)
transaktionen <- read_excel('BeispielTransaktionen.xlsx')  # Excel einlesen
```

- `#` = Kommentar (wird nicht ausgeführt)
- Operator `<-` = Zuweisung

---

## Aufgabe 2: Datenbereinigung

### Kontext
Nach einem Update des Online-Shops haben Kunden Fehler gemeldet. Diese haben zu fehlerhaften/unvollständigen Datensätzen geführt (z.B. unvollständige Bestelldatensätze).

### Datenbasis
SQLite-Datenbank: `FahrradweltNeuHagen.db`

### R-Verbindungsbefehl
```r
dbFahrradweltNeuhagen <- dbConnect(SQLite(), dbname = 'FahrradweltNeuHagen.db')
```

### Relevante Kursinhalte
- Einheit 2, Kap. 3.3: Bereinigung und Aufbereitung der Daten
- SQL-Grundlagen (Einführung in SQL)
- Fehlerklassen: Semantisch, Coverage, Syntaktisch

### Konkrete Fragen
*(folgen — Rest der Aufgabe wird gepostet)*

---

*Datei wird fortlaufend ergänzt. Bitte restliche Aufgabenteile posten.*
