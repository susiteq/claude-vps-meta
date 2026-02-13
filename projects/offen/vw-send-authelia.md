# Vaultwarden Send-Pfade bei Authelia ausnehmen

**Status:** Offen — Umsetzung direkt auf dem Server (Caddy/Authelia/Docker Compose)
**Priorität:** Mittel

## Zweck

Vaultwarden-Send-Links für externe Empfänger erreichbar machen, ohne den Authelia-Schutz für den Rest (Login, Admin-Panel) zu entfernen.

## Hintergrund

- Stack: Caddy → Authelia (Forward Auth) → Vaultwarden, alles Docker Compose
- Domain: `vaultwarden.geniusmoment.de`
- Send-URL-Muster: `/#/send/<id>/<key>` (Fragment = Client-Side-Routing)
- Configs liegen auf dem Server, nicht in einem lokalen Repo

## Problem-Analyse

Das `#`-Fragment wird nie an den Server gesendet. Der Browser lädt die Root-Seite (`/`), dann macht das SPA API-Aufrufe. Für Send-Empfänger müssen diese Server-Pfade Authelia bypassen:

1. **SPA laden:** `GET /` + statische Assets (`/app/*`, `/images/*`, `/fonts/*`, `/locales/*`)
2. **Send-API:** `POST /api/sends/access/<send_id>`
3. **Config-API:** `GET /api/config` (SPA-Initialisierung)
4. **Health:** `GET /alive`

## Ansatz: Authelia access_control bypass

In Authelia `configuration.yml` gezielt Bypass-Regeln ergänzen:

```yaml
access_control:
  rules:
    # Vaultwarden Send — öffentlich erreichbar
    - domain: vaultwarden.geniusmoment.de
      resources:
        - '^/$'
        - '^/app/.*$'
        - '^/images/.*$'
        - '^/fonts/.*$'
        - '^/locales/.*$'
        - '^/api/sends/access/.*$'
        - '^/api/config$'
        - '^/alive$'
      policy: bypass

    # Admin-Panel — streng geschützt
    - domain: vaultwarden.geniusmoment.de
      resources:
        - '^/admin.*$'
      policy: two_factor

    # Rest (API, Login) — Authelia-geschützt
    - domain: vaultwarden.geniusmoment.de
      policy: one_factor
```

Alternative: Caddy-Matcher statt Authelia-Regeln. Authelia ist sauberer (zentrale Policy-Verwaltung).

## Entscheidungen

- **Authelia access_control** statt Caddy-Matcher
- **Nur Send-Pfade** freigeben, nicht komplett
- Login-Page wird sichtbar (unvermeidbar wegen SPA), bleibt durch eigene Auth geschützt

## Umsetzung

1. Auf dem Server: aktuelle Authelia-Config + Caddyfile sichten
2. Bypass-Regeln in Authelia ergänzen
3. Authelia-Container neu starten (`docker compose restart authelia`)
4. Send-Link im Inkognito-Browser testen
5. Prüfen: Admin-Panel + API weiterhin geschützt
6. Falls Bypass allein nicht reicht: Caddy-Matcher anpassen
