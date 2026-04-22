# Ux Review 2 April 2026

> **Branch:** `design/ux-review-2`  
**Stand:** 04.04.2026  
**Basis:** Aktueller Implementierungsstand nach Welle 4 + UX-Redesign 1

---

## Ausgangsla

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# UX-Review 2 — April 2026

**Branch:** `design/ux-review-2`  
**Stand:** 04.04.2026  
**Basis:** Aktueller Implementierungsstand nach Welle 4 + UX-Redesign 1

---

## Ausgangslage

Die Anwendung verfügt nach dem ersten UX-Redesign über:
- Linke Sidebar-Navigation (nur Desktop, `md:flex hidden`)
- Breadcrumbs auf Unterseiten
- Light Mode, Orange als Akzentfarbe
- Lucide Icons durchgehend
- Workflow-Tracker auf der Projektdetailseite
- Inline-Foto-Upload je Formularabschnitt

---

## Kritische Befunde (vor den Vorschlägen)

| Schwere | Bereich | Problem |
|---|---|---|
| 🔴 KRITISCH | Mobile | Keine Navigation auf Mobilgeräten — Sidebar ist `hidden md:flex`, kein Fallback |
| 🔴 KRITISCH | Mobile | Dashboard-Tabelle bricht auf kleinen Screens ab |
| 🟠 HOCH | Workflow | Status „Abgeschlossen" kann nicht gesetzt werden — kein UI vorhanden |
| 🟠 HOCH | Navigation | „Dashboard" und „Projekte" zeigen auf dieselbe Route (`/dashboard`) — verwirrend |
| 🟡 MITTEL | Forms | Kein visuelles Feedback beim Speichern / Keine Auto-Save-Anzeige |
| 🟡 MITTEL | Fotos | Delete-Button nur per Hover erreichbar — auf Touch unmöglich |

---

## Verbesserungsvorschläge

---

### V1 — Mobile Bottom Navigation Bar

**Problem:** Die Sidebar ist auf Mobilgeräten vollständig ausgeblendet (`hidden md:flex`). Ein Nutzer auf dem Smartphone hat nach dem Login keine Navigationsmöglichkeit — er ist auf der Seite gefangen.

**Lösung:** Feste Bottom-Navigation am unteren Bildschirmrand auf Mobile (`md:hidden`), mit den 4 wichtigsten Zielen als Icon + Label.

```
┌─────────────────────────────────┐
│  [Dashboard] [Projekte] [+Neu]  │
│     🏠          📁       ➕      │
└─────────────────────────────────┘
```

| **Vorteile** | **Nachteile** |
|---|---|
| Behebt den kritischsten Mangel — App auf Mobile überhaupt nutzbar | Verliert ~56px Viewport-Höhe für Content |
| Native App-Feeling (entspricht iOS/Android-Patterns) | Kollisionsgefahr mit Browser-Navigationsleiste auf manchen Geräten |
| Daumen-freund

*[truncated — see source for full prompt]*