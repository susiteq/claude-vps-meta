# Devlog: Uhrzeit in Einträgen ergänzen

**Status:** Offen — Umsetzung in infra/hooks + ggf. Root-CLAUDE.md
**Priorität:** Niedrig

## Zweck

Devlog-Einträge (DEVLOG.md und DEVLOG-GLOBAL.md) sollen neben dem Datum auch die Uhrzeit enthalten, um bei mehreren Einträgen am selben Tag die Reihenfolge nachvollziehbar zu machen.

## Ist-Zustand

- Format: `### YYYY-MM-DD — [Kurztitel]`
- Uhrzeit fehlt

## Soll-Zustand

- Format: `### YYYY-MM-DD HH:MM — [Kurztitel]` (oder ähnlich)
- Gilt für DEVLOG.md (lokal) und DEVLOG-GLOBAL.md

## Umsetzung

1. Post-commit Devlog-Hook in infra/ anpassen (Timestamp-Format erweitern)
2. Devlog-Format in Root-CLAUDE.md aktualisieren
3. Testen: neuer Commit → Eintrag mit Uhrzeit
