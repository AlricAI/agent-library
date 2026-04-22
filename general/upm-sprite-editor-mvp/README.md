# Upm Sprite Editor Mvp

> ## Current spec

Das MVP ist jetzt weitgehend definiert: Im UPM-Paket `com.ecs2d.renderer` sollen zwei minimale Unity-Editor-Tools entstehen. Der Wiza

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ich möchte nun editor windows erstellen, damit das erstllen von spritesheets und animationset einfacher geht, sowas wie ein wizard, auch soll es ein window geben das alle spritesheets scritable anzeigt, damit man dann leicht sieht welche id man gegeben hat.

## Current spec

Das MVP ist jetzt weitgehend definiert: Im UPM-Paket `com.ecs2d.renderer` sollen zwei minimale Unity-Editor-Tools entstehen. Der Wizard soll in 2 bis 3 Schritten mit Next/Back durch das Anlegen oder Aktualisieren von genau einem SpriteSheet plus einem Animationsset führen, sowohl importierte Sprites als auch manuelle Eingaben unterstützen, Animationen per Namensmuster vorschlagen und nachbearbeitbar machen, eine kleine Sprite-Preview zeigen, Namenskonventionen vorschlagen, aber nur warnen, und vor dem Speichern möglichst vollständig validieren. Bei bestehender ID soll ein vorhandenes Asset zum Aktualisieren angeboten werden, wobei das Update-Verhalten pro Bereich auswählbar ist. Das Übersichtsfenster soll zunächst read-only bleiben, alle SpriteSheet-ScriptableObjects projektweit automatisch finden, nach ID/Name/Pfad filterbar sein und direkt ID, Name, Pfad sowie Sprite- und Animation-Anzahl anzeigen; Aktionen sind Öffnen und ID-Kopieren. Beide Tools sollen über Menüeinträge und Kontextmenüs auf relevanten Assets inklusive Sprites erreichbar sein.

## Q&A history

Q: Welche Aufgaben soll der erste Wizard konkret abdecken?
A: SpriteSheet + Animationsset anlegen

Q: Woher sollen die SpriteSheets im Übersichtsfenster kommen?
A: zuerst automatisch suchen, später filterbar

Q: Welche Eingaben soll der Wizard im ersten Schritt unterstützen?
A: beides unterstützen

Q: Wie soll die SpriteSheet-ID vergeben werden?
A: automatisch vorschlagen, manuell änderbar

Q: Welche Assets soll der Wizard am Ende tatsächlich erzeugen oder aktualisieren?
A: neu anlegen oder bestehende aktualisieren

Q: Welche Aktionen brauchst du direkt im SpriteSheet-Übersichtsfenster?
A: anzeigen + öffnen + ID kopieren

Q: Wie solle

*[truncated — see source for full prompt]*