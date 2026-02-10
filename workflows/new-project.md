# Workflow: Neues Projekt starten

## 1. Idee besprechen
- Konversation in Root (`/srv/projects/`) oder `meta/` starten
- Klären: Name, Scope, Technologie

## 2. Ordner erstellen
```bash
mkdir /srv/projects/<projektname>
cd /srv/projects/<projektname>
git init && git branch -m main
```

## 3. CLAUDE.md erstellen
Vorlage:
```markdown
# CLAUDE.md — <Projektname>

## Zweck
[1-2 Sätze: Was macht dieses Projekt?]

## Tech-Stack
[Sprachen, Frameworks, Tools]

## Konventionen
[Projektspezifische Regeln, die Claude nicht selbst erkennt]
```

## 4. .claudeignore kopieren
```bash
cp /srv/projects/infra/security/templates/.claudeignore .
```

## 5. Devlog-Eintrag
Neuen Eintrag in `/srv/projects/meta/devlog.md` mit Begründung.

## 6. Weiterarbeiten
Ab jetzt: Neue Konversationen im Projektordner starten.
