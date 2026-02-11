# Symlink-Auflösung: /home/claude-code/projects/ als echtes Root

## Problem

Claude Code speichert Sessions basierend auf dem aufgelösten Pfad. Zwei Symlinks zeigen auf `/srv/projects/`:
- `/home/claude-code/projects` → `/srv/projects`
- `/home/walters/projects` → `/srv/projects`

VSCode öffnet über `/home/claude-code/projects/...`, aber Sessions landen unter `-srv-projects-*`. Dadurch sind Past Conversations in der UI nicht sichtbar. Betrifft alle Unterordner (meta/, und jedes zukünftige Projekt).

Der `/srv/projects`-Symlink ist ein Überbleibsel vom User-Wechsel `walters` → `claude-code`.

## Schritte

### 1. Symlink entfernen, Verzeichnis verschieben

```bash
rm /home/claude-code/projects
mv /srv/projects /home/claude-code/projects
```

### 2. walters-Symlink umbiegen

```bash
# Erfordert ggf. walters/sudo
rm /home/walters/projects
ln -s /home/claude-code/projects /home/walters/projects
```

### 3. Rück-Symlink für Kompatibilität

```bash
# Erfordert ggf. walters/sudo (da /srv/ root gehört)
ln -s /home/claude-code/projects /srv/projects
```

### 4. Claude-Session-Daten migrieren

```bash
cd ~/.claude/projects/
rm -f -- -home-claude-code-projects          # alter Symlink
mv -- -srv-projects -home-claude-code-projects
mv -- -srv-projects-meta -home-claude-code-projects-meta
```

### 5. Pfad-Referenzen aktualisieren

`/srv/projects/` → `/home/claude-code/projects/` in:
- `infra/root-config/CLAUDE.md` (= Root-CLAUDE.md)
- `infra/CLAUDE.md`
- `meta/workflows/new-project.md`
- Auto-Memory Dateien in `~/.claude/projects/`

### 6. Commits + Devlog

- infra-Repo: Root-CLAUDE.md, CLAUDE.md, tasks/
- meta-Repo: Workflow, Devlog

## Hinweis

Schritte 2 und 3 erfordern möglicherweise `walters`-Rechte (`claude-code` hat kein sudo). Falls nötig, als manuelle Anweisung ausgeben.

## Verifikation

1. `ls -la /home/claude-code/projects/` — echtes Verzeichnis, kein Symlink
2. `readlink /home/walters/projects` → `/home/claude-code/projects`
3. `ls ~/.claude/projects/ | grep home-claude` — Session-Daten unter neuem Pfad
4. Claude Code in meta/ neu starten → Past Conversations sichtbar
