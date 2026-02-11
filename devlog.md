# Devlog

Globales Entwicklungslog. Neueste Einträge zuerst.

---

## 2026-02-11 — Umstrukturierung meta/ zum Projekt-Inkubator
**Ordner:** meta/
**Was:** meta/ von Docs-Ordner zum Projekt-Inkubator umgebaut. Neue Struktur: `projects/offen|laufend|erledigt/` für Projektstatus-Verwaltung, `templates/` mit CLAUDE.md-Vorlage und Checkliste. `workflows/` aufgelöst (Inhalt in CLAUDE.md + templates/ integriert). CLAUDE.md komplett neu geschrieben. Root-CLAUDE.md-Verweise aktualisiert.
**Warum:** Bewährtes Muster von der Firmen-Instanz übernommen. Projektplanung bekommt explizite Statusverwaltung statt loser Dateien.

## 2026-02-10 — Symlink-Fix: /home/claude-code/projects/ ist echtes Root
**Ordner:** infra/, meta/, ~/.claude/projects/
**Was:** Symlink aufgelöst: `/home/claude-code/projects/` ist jetzt echtes Verzeichnis, `/srv/projects` und `/home/walters/projects` sind Symlinks hierher. Claude-Session-Daten migriert (`-srv-projects*` → `-home-claude-code-projects*`). Pfad-Referenzen in Root-CLAUDE.md, infra/CLAUDE.md, new-project-Workflow und Auto-Memory aktualisiert.
**Warum:** Past Conversations waren nicht sichtbar, weil Claude Code Sessions unter aufgelöstem Pfad `-srv-projects-*` speicherte, VSCode aber unter `-home-claude-code-*` suchte.

## 2026-02-10 — Symlink-Problem: Past Conversations nicht sichtbar
**Ordner:** meta/ (Planung), infra/ (Ausführung)
**Was:** Ursache identifiziert: `/home/claude-code/projects` → `/srv/projects` Symlink führt dazu, dass Claude Code Sessions unter `-srv-projects-*` speichert, VSCode aber unter `-home-claude-code-*` sucht. Auch `/home/walters/projects` → `/srv/projects` betroffen. Plan erstellt: Symlink auflösen, `/home/claude-code/projects/` als echtes Root, Session-Daten migrieren.
**Warum:** Past Conversations in meta/ (und zukünftig jedem Unterordner) nicht in der UI sichtbar. Wiederkehrendes Problem seit User-Wechsel walters → claude-code.

## 2026-02-10 — Scope-Abgrenzung und Kontextübergang meta/ → Projekt
**Ordner:** meta/, Root
**Was:** meta/CLAUDE.md um expliziten Scope ergänzt (keine Umsetzung hier). Workflow-Vorlage für neue Projekte um Status-, Hintergrund-, Nächste-Schritte- und Offene-Fragen-Abschnitte erweitert. Sichergestellt, dass beim Konversations-Umzug in den Projektordner der volle Kontext in der CLAUDE.md steht.
**Warum:** Ohne explizite Abgrenzung war unklar, dass meta/ nur für Einordnung/Strukturierung ist. Ohne Kontextübergabe ging Diskussionswissen beim Konversationswechsel verloren.

## 2026-02-10 — Grundstruktur: Selbstverbesserndes System
**Ordner:** Root + meta/
**Was:** meta/-Ordner erstellt mit Devlog und Workflows. Root-CLAUDE.md um Selbstverbesserungs-Direktiven erweitert. Auto-Memory initialisiert.
**Warum:** Fundament für selbstverbesserndes KI-Assistenten-System. Dokumentation ab Tag 1.
