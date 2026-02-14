# Supabase Self-Hosted

**Status:** In Arbeit — Dateien erstellt, Deployment steht aus
**Priorität:** Hoch (Grundlage für claude-memory + gobot-telegram)

## Zweck

Self-hosted Supabase-Instanz via Docker Compose als DB-Backend für Claude-Memory und zukünftige Apps.

## Setup

- **VPS:** 3. Hostinger KVM4 (App-VPS), Domain: `data.genwal.cloud`
- **Stack:** Vollständig (alle 13 Services) — offizielles Docker-Setup + minimale Overrides
- **Caddy** in Docker als Reverse Proxy (Auto-HTTPS)
- **Auth:** Auto-Confirm (SMTP später via mailbox.org, siehe `mailbox-smtp.md`)
- **pgvector** aktiviert für Vektor-Suche

## Dateien (im Repo ~/projects/supabase/)

- `docker-compose.yml` — offiziell, unverändert
- `docker-compose.override.yml` — Caddy-Service + pgvector-Volume
- `Caddyfile` — Reverse-Proxy für data.genwal.cloud
- `generate-secrets.sh` — Generiert .env mit allen Secrets + JWT-Tokens
- `volumes/` — offizielle Init-Scripts + pgvector

## Nächste Schritte

1. Coolify auf App-VPS stoppen
2. DNS: A-Record `data.genwal.cloud` → App-VPS IP
3. Repo auf App-VPS klonen, `generate-secrets.sh` ausführen
4. `docker compose up -d`
5. Verifizieren: Studio, REST-API, pgvector

## Bezug zu anderen Projekten

- **claude-memory:** Braucht laufende Supabase-Instanz als Voraussetzung
- **gobot-telegram:** Braucht Supabase + Memory als Voraussetzung
- **mailbox-smtp:** SMTP für Supabase Auth
