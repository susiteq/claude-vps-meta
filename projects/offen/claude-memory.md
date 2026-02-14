# Claude Memory — Semantisches Langzeitgedächtnis

**Status:** Offen — Schema + MCP-Server konfigurieren
**Priorität:** Hoch
**Abhängigkeit:** supabase-selfhosted muss laufen

## Zweck

Semantisches Langzeitgedächtnis für Claude Code via Supabase + MCP. Ergänzt die bestehenden CLAUDE.md/Auto-Memory mit strukturierter, durchsuchbarer Wissensdatenbank.

## Hintergrund

- Bestehende Memory-Mechanismen: CLAUDE.md (statisch) + Auto-Memory (textbasiert, max 200 Zeilen)
- Supabase-Memory bietet: semantische Suche (pgvector), Intent Detection (Fakten/Ziele), skalierbar
- Tutorial-Referenz: Autonomee/Gobot nutzt Supabase für conversations, messages, facts, goals + embeddings
- Offizieller Supabase MCP Server als Brücke zu Claude Code

## Tech-Stack

- Supabase MCP Server (offiziell von Supabase)
- PostgreSQL/pgvector (auf Self-Hosted-Instanz aus Projekt 1)
- OpenAI Embeddings API (text-embedding-3-small)
- Supabase Edge Functions für Embedding-Generierung
- SQL für Schema-Definition

## Nächste Schritte

1. Supabase MCP Server installieren + konfigurieren
2. Datenbank-Schema erstellen: conversations, messages, facts, goals
3. pgvector-Tabelle für Embeddings anlegen
4. Edge Function für Embedding-Generierung deployen
5. OpenAI API Key als Supabase Secret hinterlegen (OPENAI_API_KEY)
6. Claude Code MCP-Konfiguration testen
7. Abgrenzung zu Auto-Memory klären: was bleibt in MEMORY.md, was geht in Supabase?

## Offene Fragen

- Edge Functions bei Self-Hosted: Funktionieren die genauso wie bei Supabase Cloud?
- Embedding-Modell: text-embedding-3-small vs. text-embedding-3-large?
- Automatisches Speichern vs. explizites "merke dir das"?
