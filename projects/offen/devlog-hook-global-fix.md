# Devlog-Hook: DEVLOG-GLOBAL.md wird nicht mit-committed

**Status:** Offen — Umsetzung in infra/hooks
**Priorität:** Niedrig

## Zweck

Der post-commit Devlog-Hook aktualisiert sowohl `DEVLOG.md` als auch `DEVLOG-GLOBAL.md`, committed aber nur `DEVLOG.md`. Die DEVLOG-GLOBAL.md bleibt als unstaged change liegen und muss manuell nachcommitted werden.

## Ist-Zustand

- Hook: `infra/hooks/post-commit-devlog` (oder ähnlich)
- `DEVLOG.md` → wird korrekt committed
- `DEVLOG-GLOBAL.md` → wird aktualisiert, aber NICHT staged/committed

## Erwartetes Verhalten

Beide Dateien sollen im automatisch erzeugten Devlog-Commit enthalten sein.

## Umsetzung

1. Hook-Script in infra/ sichten
2. `git add` für DEVLOG-GLOBAL.md ergänzen
3. Testen: normaler Commit → beide Devlog-Dateien im Folge-Commit
