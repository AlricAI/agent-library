# User Stories Welle 5

> **App:** Energieberater (Arbeitstitel)  
**Zeitraum:** KW15 — 13.–19. April 2026  
**Entwicklungszeit:** 16h  
**Status:** 🟡 Entwurf — ausstehend Rev

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# User Stories — Welle 5 "Navigator & Kundenportal"

**App:** Energieberater (Arbeitstitel)  
**Zeitraum:** KW15 — 13.–19. April 2026  
**Entwicklungszeit:** 16h  
**Status:** 🟡 Entwurf — ausstehend Review durch Product Owner (Erwin Moretz)

---

## Hauptprozess-Ziel

> Berater erfasst Gebäudedaten → Förder-Navigator zeigt passende Programme → Berater sendet Ergebnis an Kunden → Kunde loggt sich ins Portal ein und sieht Projektstatus ✅

---

## Rollen

| Kürzel | Rolle | Beschreibung |
|---|---|---|
| Berater | Energieberater | Freiberuflicher Energieberater, nutzt die App täglich |
| Kunde | Endkunde / Hausbesitzer | Auftraggeber des Beraters, nutzt das Kundenportal |
| Besucher | Website-Besucher | Potenzieller Neukunde, sieht die Landingpage |

---

## US-W5-01 — Kunden-Login & Portal-Zugang

### User Story
> Als **Kunde** möchte ich mich mit einem eigenen Login (E-Mail + Passwort) in das Kundenportal einloggen,  
> damit ich sicher auf die Informationen zu meinem Projekt zugreifen kann.

### Akzeptanzkriterien

- [ ] **AC-01.1** — Der Berater kann für einen Kunden ein Konto anlegen (Einladung per E-Mail via Supabase Auth).
- [ ] **AC-01.2** — Der Kunde erhält eine Einladungs-E-Mail mit einem sicheren Link zur Passwort-Vergabe.
- [ ] **AC-01.3** — Nach der Passwort-Vergabe kann sich der Kunde mit E-Mail + Passwort einloggen.
- [ ] **AC-01.4** — Nach dem Login wird der Kunde direkt auf sein Projektportal weitergeleitet — nicht auf das Berater-Dashboard.
- [ ] **AC-01.5** — Kunden können ausschließlich ihre eigenen Projekte sehen (RLS-Policy: Kunde sieht nur Projekte mit seiner `kunden_id`).
- [ ] **AC-01.6** — Berater-Seiten (Dashboard, GEG-Formular) sind für Kunden nicht erreichbar — Redirect auf das Kundenportal.
- [ ] **AC-01.7** — Bei falschen Zugangsdaten erscheint eine verständliche Fehlermeldung.

---

## US-W5-02 — Projektstatus im Kundenportal

### User Story
> Als **Kunde** möchte ich im Portal den aktuellen Status meines Projekts und alle relevanten In

*[truncated — see source for full prompt]*