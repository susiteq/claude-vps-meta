# Gobot Telegram — Claude Code Chat-Bot

**Status:** Offen — Repo klonen, Setup durchführen
**Priorität:** Mittel
**Abhängigkeit:** supabase-selfhosted + claude-memory müssen stehen

## Zweck

Telegram-Bot als Chat-Interface zu Claude Code mit Supabase-Memory. Ermöglicht Kommunikation mit Claude Code von überall via Telegram (Text + Voice).

## Hintergrund

- Basiert auf Autonomee/Gobot (GitHub, open source, 175+ Stars)
- Tutorial: YouTube BYEaLMnfIjg — automatisiertes Setup, läuft in ~2 Min
- Basis-Version zuerst: Text-Chat + Memory. Kein VPS-Hybrid, kein Multi-Agent.
- Always-On via systemd (Linux), nicht launchd/PM2

## Tech-Stack

- Bun (JavaScript Runtime)
- TypeScript
- Telegram Bot API (BotFather)
- Claude Code (Subscription)
- Supabase (Self-Hosted, aus Projekt 1+2)
- systemd (Always-On)

## Nächste Schritte

1. Autonomee/gobot Repo forken + klonen
2. Bun installieren (falls nicht vorhanden)
3. Automatisiertes Setup durchlaufen (Bot Token, User ID, Supabase URL + Anon Key)
4. Supabase-Anbindung auf Self-Hosted-Instanz umkonfigurieren
5. Testen: Telegram-Nachricht → Antwort mit Memory-Kontext
6. systemd-Service erstellen für Always-On
7. Security: Bot nur für eigene User ID zugänglich

## Offene Fragen

- Gobot-Repo aktueller Stand? Features der Basis-Version prüfen
- Bun auf dem Server vs. lokal? (Tutorial: lokal auf Mac/PC)
- Voice-Messages: in Basis-Version enthalten oder nur Full?
