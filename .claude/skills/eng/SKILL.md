---
name: eng
description: "Englisch-Filter — prueft ob englische Begriffe echte Fachbegriffe oder beschreibende Phrasen sind. NUR bei englischem Skript."
allowed-tools: Read, Grep, Glob
---

## Kernproblem

Das Skript ist auf Englisch. AI-Tendenz: JEDE englische Formulierung als "Fachbegriff" behandeln. Ein Student merkt sich die Logik, einige feststehende Begriffe, und formuliert den Rest auf Deutsch.

## Der Test: Ist es ein Fachbegriff?

Drei Fragen, ALLE muessen Ja sein:
1. **Ist es ein NAME?** Modellname, Konzeptname, gepraegte Bezeichnung? Oder BESCHREIBUNG?
2. **Wuerde ein Student diesen Begriff als englischen Term auswendig lernen?**
3. **Verliert man Praezision wenn man es auf Deutsch sagt?**

Eine Frage Nein → auf Deutsch formulieren.

## Kategorie 1: Immer auf Englisch
Modell-/Framework-Namen, gepraegte Konzepte, Rollen, feststehende Kurzdefinitionen.

## Kategorie 2: Immer auf Deutsch
Tabellenbeschreibungen, erklaerende Phrasen, Aufzaehlungspunkte aus dem Skript.

## Die zwei AI-Tells

### 1. Systematische Klammer-Labels
VERBOTEN: Jeden Punkt mit dem gleichen englischen Label-Schema taggen.
STATTDESSEN: Dimensionen EINMAL erwaehnen, danach auf Deutsch.

### 2. Beschreibende Phrasen fett und prominent
VERBOTEN: Beschreibende Phrasen fett in die Antwort schreiben.
STATTDESSEN: Idee auf Deutsch ausdruecken.

## Anker-dann-Fluss-Prinzip

Englischen Fachbegriff EINMAL als Anker setzen, danach auf Deutsch/verkuerzt weiterarbeiten. Nicht in jeden Satz den vollen englischen Term reinzwingen.
