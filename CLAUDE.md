# CLAUDE.md — meta

Systemweite Entwicklungsdokumentation und Workflows.

## Scope

Konversationen hier haben genau zwei Phasen:

**Phase 1 — Besprechen:** Idee/Aufgabe verstehen, Zielordner bestimmen (neues Projekt oder bestehender Ordner wie `infra/`).

**Phase 2 — Anlegen und Übergeben:**
1. Ordner + Git-Repo erstellen (nur bei neuem Projekt, Workflow: `workflows/new-project.md`)
2. CLAUDE.md bzw. Task-Datei im Zielordner erstellen — mit vollständigem Kontext aus der Diskussion
3. Devlog-Eintrag schreiben
4. Fertig. Hinweis an User: „Neue Konversation im Zielordner starten."

**Das ist ALLES was hier passiert.** Keine Implementierungsplanung, keine Schrittanleitungen, keine technische Analyse. Das gehört in den Zielordner.

## Zuständigkeit

- Devlog pflegen
- Workflows aktualisieren
- Strukturentscheidungen dokumentieren

## Devlog-Regeln

- Neue Einträge OBEN einfügen (nach dem Header, vor bestehenden Einträgen)
- Bei >500 Zeilen: Ältere Einträge in `devlog-archiv-YYYY.md` auslagern
- Jeder Eintrag: Datum, Kurztitel, Ordner, Was, Warum
