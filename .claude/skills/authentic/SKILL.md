---
name: authentic
description: Authentizitaets-Check — schwaecht die Antwort gezielt ab auf Studenten-Niveau. Nur auf explizite Anfrage.
allowed-tools: Read, Grep, Glob
---

## Zweck

Die perfekte Pruefungsantwort gezielt abschwaechen, damit sie wie die Arbeit eines sehr guten Studenten wirkt — nicht wie eine AI-generierte Musterloesung.

## Punktebudget

- Gesamtbudget pro Klausur: **max. 5-8 Punkte** opfern (Ziel: 92-97% der Gesamtpunktzahl)
- Nicht gleichmaessig verteilen: 2-3 Aufgaben unangetastet, bei 1-2 gezielt kuerzen
- Budget wird ueber Aufgaben getrackt (Meldung: "Bisheriges Budget: X/8P verbraucht")

## Ablauf

1. Aktuelle Antwort analysieren
2. 2-4 konkrete Kuerzungsvorschlaege mit geschaetztem Punkteverlust listen
3. Empfehlung geben
4. Bei Zustimmung: Modifizierte Antwort erzeugen

## Erlaubte Eingriffe (SICHER)

- Letzte Unterpunkte bei langen Aufzaehlungen kuerzen
- Nebensaetze streichen, die keine Kernpunkte bringen
- Begruendungen kuerzen (nicht entfernen)
- Abkuerzungen verwenden ("d.h.", "bzgl.")
- Bei spaeterer Aufgabe telegraphischer schreiben (simuliert Zeitdruck)

## VERBOTEN (NIEMALS)

- Richtige Zuordnung AENDERN
- Kernbegriffe (Fachbegriffe) streichen
- Falsche Definitionen oder Fachbegriffe einbauen
- Kernaussagen oder Schlagwoerter streichen

## Wann /authentic KEINEN Sinn macht

- Zuordnungsaufgaben — binaer richtig/falsch
- SC/MC-Fragen
- Antwort bereits knapp
- Punktebudget aufgebraucht

## Ausgabe-Format

```
=== AUTHENTIZITAETS-CHECK ===
Aufgabe: [X] ([Y] Punkte)
Bisheriges Budget: [Z]/8P verbraucht

Vorschlaege:
1. [Stelle] — [Was kuerzen] — ~[N]P Verlust
2. [Stelle] — [Was kuerzen] — ~[N]P Verlust

Empfehlung: [Vorschlag X / Keine Aenderung noetig]
```
