# Selfhosted Apps — zentrales Config-Repo

**Status:** Offen — Struktur planen, Repo anlegen
**Priorität:** Mittel

## Zweck

Alle Self-hosted Apps (docker-compose.yml + .env) in einem einzigen Git-Repo versionieren. Erstmal nur Versionierung, kein automatisches Deployment.

## Hintergrund

- Alles läuft auf einem Server
- Apps bestehen im Wesentlichen aus docker-compose.yml + .env
- Ähnliches Setup existiert bei der Firmeninstanz (TeReBe)
- Caddy + Authelia als Reverse Proxy / Auth (siehe vw-send-authelia)

## Offene Fragen (für die Planungsphase)

- Beste Ordnerstruktur: flach (Ordner pro App) vs. gruppiert (nach Kategorie)?
- Umgang mit .env-Dateien: gitignore + .env.example? Oder verschlüsselt (sops, git-crypt)?
- Shared configs (z.B. Caddy, Authelia, Netzwerke) — eigener Ordner oder bei den Apps?
- Welche Apps sind aktuell im Einsatz?

## Nächste Schritte

1. Bestandsaufnahme: welche Apps laufen, wie sehen die Configs aus
2. Struktur entscheiden
3. Repo anlegen, Configs migrieren
