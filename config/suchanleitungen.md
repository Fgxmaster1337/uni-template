# Suchanleitungen & Referenz

## Grep-Muster fuer Wissensdateien

| Suche nach | Grep-Muster | Wissensdatei |
|------------|-------------|--------------|
| Definition | `### Definition:` | alle |
| Konzept | `### Concept:` | alle |
| Modell | `### Model:` | alle |
| Framework | `### Framework:` | alle |
| Pruefungsfrage | `### Pruefungsfrage:` | alle |
| Begriffe im Glossar | `\| ` | wissen/glossar.md |
| Altklausur-Aufgabe | `## Aufgabe` | wissen/klausur_*.md |

## Folien-Text durchsuchen

Extrahierte Texte liegen in `docs/folien_text/`:

```bash
grep -i "[FACHBEGRIFF]" docs/folien_text/*.txt
```
