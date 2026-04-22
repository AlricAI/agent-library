# OmniLore Dossier Generisches Framework

> > **Status:** Konzept-Skizze / Diskussionsgrundlage
> **Ziel:** Wie kann die `7w_wiki` Engine so konfiguriert werden, dass "Siebenwind" zu einer austa

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Dossier: Projekt "Nexus" – Skizze zur Entkopplung der Lore-Engine

> **Status:** Konzept-Skizze / Diskussionsgrundlage
> **Ziel:** Wie kann die `7w_wiki` Engine so konfiguriert werden, dass "Siebenwind" zu einer austauschbaren Variablen wird, ohne die bestehende Ordnerstruktur (Wiki/Quellen) zu zerstören?

## Ausgangslage

Aktuell ist das Projekt eng mit dem Begriff "Siebenwind" und spezifischer Lore (z.B. der Zeitrechnung "Sonnenzirkel") verflochten. Diese festen Bezüge finden sich in:
- CLI-Beschreibungen und Output-Texten
- System-Prompts der Agenten (`SKILL.md` Dateien)
- Titel und Metadaten der generierten Markdown-Files
- Taxonomie-Logik ("Wo kommt ein Artikel hin?")

**Die Idee:** Wir erhalten die etablierten Strukturen (wie `Siebenwind_Wiki` und `Quellen`), aber wir ersetzen **innerhalb des Codes** harte Strings durch Variablen, die aus einer zentralen Konfiguration (z.B. einem `lore_manifest.json` oder `universe.toml`) bezogen werden. 

**WICHTIG:** Die aktuelle Siebenwind-Implementierung bleibt als das kanonische, voll funktionsfähige Beispiel (die "Referenz-Instanz") für dieses Framework unangetastet bestehen. Wir bauen das Framework *um* Siebenwind herum, sodass Siebenwind der erste und primäre Tenant der neuen OmniLore-Engine ist.

---

## Konzept: Orchestrierung durch Script-Assembly

Anstelle fester Strings könnte ein Builder-Skript oder die Laufzeitumgebung (z.B. `7w.py`) die nötigen Komponenten dynamisch zur Laufzeit zusammensetzen.

### 1. Zentralisierung der Variablen (Das "World Config")
Man könnte das bestehende `lore_manifest.json` erweitern, sodass es die "DNA" des Projekts abbildet:
```json
{
  "lore": {
    "world_name": "Siebenwind",
    "chronology": "Sonnenzirkel",
    "tone": "immersiv, historisch",
    "directories": {
      "wiki": "Siebenwind_Wiki",
      "sources": "Quellen"
    }
  }
}
```

### 2. Dynamische Prompts für Agenten
Die System-Prompts (z.B. `<skill_dir>/SKILL.md`) könnten Template-Tags enthalten (wie `{{WORLD_NAME}}` o

*[truncated — see source for full prompt]*