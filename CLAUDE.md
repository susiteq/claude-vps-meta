# Meta – Projekt-Inkubator

> **Dieses Verzeichnis dient ausschließlich der Projektplanung und CLAUDE.md-Erstellung.**
> Hier wird nie Projektarbeit geleistet – nach Abschluss startet Susi eine neue Conversation im Zielverzeichnis.

---

## Strikte Abgrenzung

- **Hier:** Planen, strukturieren, CLAUDE.md schreiben, Verzeichnisse anlegen
- **Output:** Immer eine Planungsdatei in `projects/` + ggf. CLAUDE.md/Verzeichnis im Ziel + Root-CLAUDE.md-Update
- **Nie hier:** Code schreiben, Konfigurationen bauen, Packages installieren, Projekte implementieren
- **Abschluss:** Konkrete Ziel-Conversation benennen, in der die Umsetzung erfolgt

---

## projects/ – Projektverwaltung

- Drei Unterordner: `offen/` (geplant), `laufend/` (in Arbeit), `erledigt/` (abgeschlossen)
- **Nicht scannen** bei Conversation-Start – nur auf explizite Aufforderung
- Susi öffnet die relevante Projektdatei im IDE → daraus ergibt sich der Kontext
- Wenn keine Projektdatei geöffnet/vorhanden → neue in `offen/` erstellen
- Bei Projektstart: Datei per `git mv` von `offen/` nach `laufend/` verschieben
- Bei Abschluss: Datei per `git mv` von `laufend/` nach `erledigt/` verschieben

---

## Workflow: Neues Projekt

1. **Klären:** Was ist das Projekt? Zweck, Umfang, beteiligte Services/Tools
2. **Projektdatei erstellen** in `projects/offen/`
3. **CLAUDE.md schreiben** – Vorlage: `templates/claude-md.md`, Goldene Regel beachten
4. **Verzeichnis erstellen** und CLAUDE.md dort ablegen — Projektdatei aus `meta/projects/` im Zielverzeichnis verlinken
5. **`.claudeignore` kopieren** aus `~/projects/infra/security/templates/`
6. **Root-CLAUDE.md aktualisieren** falls nötig
7. **Susi informieren:** „Neue Conversation in `<zielverzeichnis>/` starten"

Checkliste zum Abhaken: `templates/checkliste.md` – **immer durcharbeiten!**

> **Wichtig:** Der primäre Output jeder Meta-Conversation ist eine Planungsdatei in `projects/`.
> Erst wenn diese steht, werden Verzeichnisse/CLAUDE.md angelegt und Root-CLAUDE.md aktualisiert.

## Workflow: Bestehendes Projekt

1. **Ist-Zustand prüfen:** Verzeichnisstruktur, vorhandene CLAUDE.md, Codebase scannen
2. **Lücken identifizieren:** Fehlende CLAUDE.md? Veralteter Inhalt? Fehlende Root-Referenz?
3. **CLAUDE.md erstellen oder aktualisieren** – bestehende Referenzen nicht brechen
4. **Root-CLAUDE.md synchronisieren** falls Status/Beschreibung veraltet
5. **Keine Projektarbeit starten** – nur Dokumentation und Struktur

---

## Hinweise

- Zielgröße projektspezifischer CLAUDE.md: 15–25 Zeilen
- Alles was in Root-CLAUDE.md steht, dort referenzieren statt duplizieren
- Goldene Regel: Kurz, spezifisch, nur was Claude nicht selbst herausfinden kann

## Devlog-Regeln

- Format: siehe Root-CLAUDE.md (Kategorie, Bereich, Dateien, Kontext, Commit)
- Pro Repo: `DEVLOG.md` im jeweiligen Repo, neueste Einträge oben
- Global: `DEVLOG-GLOBAL.md` in meta/ — Format: `### [reponame] Titel — Datum`
- Bei >500 Zeilen: Ältere Einträge in `DEVLOG-ARCHIV-YYYY.md` auslagern
- Bei Änderungen an mehreren Repos: Eintrag in jedem betroffenen DEVLOG.md + DEVLOG-GLOBAL.md
