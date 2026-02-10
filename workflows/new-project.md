# Workflow: Neues Projekt starten

## 1. Idee besprechen
- Konversation in Root (`~/projects/`) oder `meta/` starten
- Klären: Name, Scope, Technologie

## 2. Ordner erstellen
```bash
mkdir ~/projects/<projektname>
cd ~/projects/<projektname>
git init && git branch -m main
```

## 3. CLAUDE.md erstellen
Alle wesentlichen Ergebnisse der meta/-Diskussion eintragen — nicht nur Platzhalter ausfüllen.
Die CLAUDE.md ist der vollständige Briefing-Zettel für die erste Konversation im Projektordner.

Vorlage:
```markdown
# CLAUDE.md — <Projektname>

## Status
Idee und Grundrichtung wurden in meta/ vorbesprochen. Dokumentation unten ist der vereinbarte Startpunkt.
→ Hier weiterarbeiten: Planung vertiefen, dann umsetzen.

## Zweck
[1-2 Sätze: Was macht dieses Projekt?]

## Hintergrund
[Was wurde in meta/ besprochen? Kernentscheidungen, gewählter Ansatz, Abgrenzungen]

## Tech-Stack
[Sprachen, Frameworks, Tools]

## Nächste Schritte
[Konkrete erste Aufgaben für die weitere Planung/Umsetzung]

## Offene Fragen
[Was noch geklärt werden muss — oder Abschnitt löschen wenn nichts offen]

## Konventionen
[Projektspezifische Regeln, die Claude nicht selbst erkennt]
```

## 4. .claudeignore kopieren
```bash
cp ~/projects/infra/security/templates/.claudeignore .
```

## 5. Devlog-Eintrag
Neuen Eintrag in `~/projects/meta/devlog.md` mit Begründung.

## 6. Weiterarbeiten
Ab jetzt: Neue Konversationen im Projektordner starten.
Claude hat über die CLAUDE.md den vollen Kontext — kein Nachfragen zu bereits Besprochenem nötig.
