# MCP YouTube Transcript Server

**Status:** Auf Eis — Implementierung fertig, aber YouTube blockt Requests vom VPS (IP-basiert)
**Priorität:** Niedrig

## Zweck

Minimaler Python MCP Server, der YouTube-Transkripte für Claude Code bereitstellt. Zwei Tools: Transkript abrufen (`get_transcript`) und verfügbare Sprachen auflisten (`list_transcript_languages`).

## Ergebnis

- Server implementiert und funktionsfähig (`~/projects/mcp-youtube-transcript/`)
- MCP im User-Scope registriert
- GitHub: `susiteq/claude-vps-mcp-youtube-transcript` (privat)
- **Problem:** YouTube blockt Transkript-Requests von VPS-IPs. Ohne Proxy/Residential IP nicht nutzbar.

## Mögliche Lösungen (falls später relevant)

- Proxy mit Residential IP
- Lokale Ausführung statt VPS
- Alternative API (kostenpflichtig)
