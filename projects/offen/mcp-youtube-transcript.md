# MCP YouTube Transcript Server

**Status:** Offen — Projektstruktur steht, Umsetzung in nächster Conversation
**Priorität:** Hoch

## Zweck

Minimaler Python MCP Server, der YouTube-Transkripte für Claude Code bereitstellt. Zwei Tools: Transkript abrufen (`get_transcript`) und verfügbare Sprachen auflisten (`list_transcript_languages`).

## Hintergrund

- Bestehende Node.js MCP Server existieren (kimtaeyoon83), aber Node.js ist nicht installiert
- Python 3.12 vorhanden → eigener MCP Server mit FastMCP + youtube-transcript-api
- Kein API-Key nötig (youtube-transcript-api scrapet direkt)
- MCP Server wird im User-Scope registriert (projektübergreifend verfügbar)

## Tech-Stack

Python 3.12, mcp SDK (FastMCP), youtube-transcript-api, pip + venv

## Voraussetzung

`python3-pip` und `python3-venv` müssen als walters-User installiert werden:
```bash
sudo apt install python3-pip python3-venv
```

## Nächste Schritte

1. pip + venv installieren (walters, sudo)
2. Neue Conversation in `~/projects/mcp-youtube-transcript/` starten
3. server.py + requirements.txt + setup.sh erstellen
4. Venv + Dependencies installieren
5. MCP Server registrieren und testen

## Entscheidungen

- Python statt Node.js (kein Node auf dem System, Python schon da)
- pip + venv statt uv (bewährt, Standard)
- User-Scope für MCP-Registrierung (überall verfügbar)
- Fehler als Strings, nicht als Exceptions (LLM-freundlich)
