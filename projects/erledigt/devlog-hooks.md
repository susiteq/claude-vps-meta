# Devlog-Hooks & Automation

**Status:** Phase 1 umgesetzt (Hook + Installer). Phase 2 (n8n) offen.
**Zielverzeichnis:** `~/projects/infra/`
**Priorität:** Mittel

## Zweck

Post-Commit-Hooks für automatische DEVLOG.md-Einträge und n8n-Aggregation nach DEVLOG-GLOBAL.md — analog zum Firmen-System.

## Umfang

### 1. Post-Commit-Hook-Script
- Speicherort: `infra/root-config/hooks/post-commit-devlog.sh`
- Liest Commit-Message, extrahiert Kategorie (aus Prefix oder Tag)
- Generiert DEVLOG.md-Eintrag im korrekten Format
- Fügt Eintrag oben in DEVLOG.md ein

### 2. Install-Script
- Speicherort: `infra/root-config/hooks/install-hooks.sh`
- Installiert Hook in alle Repos unter `~/projects/`
- Idempotent (mehrfach ausführbar)

### 3. n8n-Aggregation (Phase 2)
- Täglicher Workflow: Alle DEVLOG.md einlesen → DEVLOG-GLOBAL.md aktualisieren
- Webhook-Endpunkt für Echtzeit-Updates
- Umsetzung in `n8n-builder/`

## Entscheidungen

- **Kategorie-Erkennung:** Commit-Message-Prefix (z.B. `[Feature]`, `[Bugfix]`, `[Doku]`, `[Infra]`, `[Refactoring]`, `[Security]`, `[Config]`)
- **Global-Update:** Hook aktualisiert beides — DEVLOG.md im Repo + DEVLOG-GLOBAL.md in `~/projects/meta/`

## Nächste Schritte

- Phase 2: n8n-Aggregation (DEVLOG-GLOBAL.md automatisch per Webhook/Timer)
