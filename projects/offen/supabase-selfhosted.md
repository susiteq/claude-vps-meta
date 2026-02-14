# Supabase Self-Hosted

**Status:** Offen — Docker Compose aufsetzen
**Priorität:** Hoch (Grundlage für claude-memory + gobot-telegram)

## Zweck

Self-hosted Supabase-Instanz via Docker Compose. Dient als Datenbank-Backend für Claude-Memory (semantisches Langzeitgedächtnis) und zukünftige App-Projekte.

## Hintergrund

- Tutorial-Referenz: Autonomee/Gobot (YouTube: BYEaLMnfIjg) — nutzt Supabase Cloud, wir machen Self-Hosted
- Teil eines 3-Projekte-Ökosystems: **supabase** → claude-memory → gobot-telegram
- Server hat bereits Caddy + Authelia als Reverse Proxy / Auth
- Eine Instanz für alles (Memory + Apps) — verschiedene Schemas/Datenbanken zur Trennung

## Tech-Stack

- Docker Compose
- PostgreSQL 15+ mit pgvector Extension
- Supabase-Services: GoTrue, PostgREST, Realtime, Storage, Studio, Kong
- Caddy (Reverse Proxy) + Authelia (Auth) — bestehende Infra nutzen

## Nächste Schritte

1. Offizielles Supabase Docker-Setup evaluieren (github.com/supabase/supabase/docker)
2. Docker Compose anpassen (Ports, Volumes, Netzwerk)
3. pgvector Extension aktivieren
4. Caddy-Config für Studio + API-Zugang
5. Authelia-Bypass für API-Endpoints konfigurieren
6. Testen: Studio erreichbar, API funktioniert, pgvector aktiv

## Offene Fragen

- Welche Supabase-Services werden tatsächlich gebraucht? (Realtime? Storage? Oder erstmal nur PostgreSQL + PostgREST + GoTrue?)
- Ressourcen-Bedarf auf dem Server — genug RAM/CPU für alle Services?
- Backup-Strategie: Integration in bestehendes Borg-Setup?

## Bezug zu anderen Projekten

- **selfhosted-repo:** Configs können später ins zentrale Repo migriert werden
- **claude-memory:** Braucht laufende Supabase-Instanz als Voraussetzung
- **gobot-telegram:** Braucht Supabase + Memory als Voraussetzung
