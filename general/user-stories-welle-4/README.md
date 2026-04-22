# User Stories Welle 4

> **App:** Energieberater (Arbeitstitel)  
**Zeitraum:** KW14 — 06.–12. April 2026  
**Entwicklungszeit:** 16h  
**Status:** 🟡 Entwurf — ausstehend Rev

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# User Stories — Welle 4 "Berater Core"

**App:** Energieberater (Arbeitstitel)  
**Zeitraum:** KW14 — 06.–12. April 2026  
**Entwicklungszeit:** 16h  
**Status:** 🟡 Entwurf — ausstehend Review durch Product Owner (Erwin Moretz)

---

## Hauptprozess-Ziel

> Berater meldet sich an → legt Projekt an → füllt GEG-Begehungsformular aus → lädt Fotos hoch → sieht Projektübersicht im Dashboard ✅

---

## Rollen

| Kürzel | Rolle | Beschreibung |
|---|---|---|
| Berater | Energieberater | Freiberuflicher Energieberater, nutzt die App täglich |
| Besucher | Website-Besucher | Potenzieller Neukunde, sieht die Landingpage |

---

## US-W4-01 — Registrierung & Login

### User Story
> Als **Berater** möchte ich mich mit E-Mail und Passwort registrieren und anmelden,  
> damit ich sicher auf meine Projekte und Kundendaten zugreifen kann.

### Akzeptanzkriterien

- [ ] **AC-01.1** — Ein neuer Berater kann sich über ein Registrierungsformular mit E-Mail + Passwort registrieren.
- [ ] **AC-01.2** — Nach der Registrierung erhält der Berater eine Bestätigungs-E-Mail (Supabase Auth).
- [ ] **AC-01.3** — Ein registrierter Berater kann sich mit korrekten Zugangsdaten einloggen und wird auf das Dashboard weitergeleitet.
- [ ] **AC-01.4** — Bei falschen Zugangsdaten wird eine verständliche Fehlermeldung angezeigt (kein technischer Stack-Trace).
- [ ] **AC-01.5** — Ein eingeloggter Berater kann sich ausloggen. Die Session wird beendet und er wird auf die Login-Seite geleitet.
- [ ] **AC-01.6** — Geschützte Seiten (Dashboard, Formular) sind ohne Login nicht erreichbar — Redirect auf Login.
- [ ] **AC-01.7** — Das Passwort wird nicht im Klartext übertragen oder gespeichert (Supabase verwaltet Hashing).

---

## US-W4-02 — Projekt anlegen

### User Story
> Als **Berater** möchte ich ein neues Kundenprojekt anlegen,  
> damit ich alle Informationen zu einem Gebäude und Kunden strukturiert erfassen kann.

### Akzeptanzkriterien

- [ ] **AC-02.1** — Der Berater kann über einen "Neues Projekt"-Bu

*[truncated — see source for full prompt]*