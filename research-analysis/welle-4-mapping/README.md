# Welle 4 Mapping

> **Branch:** `analysis/welle-4-mapping`  
**Erstellt:** 01. April 2026  
**Basis:** Anforderungsdokument v2.0 + User Stories Welle 4  
**Zweck:** Abgle

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Welle 4 — Implementierungsmapping
**Branch:** `analysis/welle-4-mapping`  
**Erstellt:** 01. April 2026  
**Basis:** Anforderungsdokument v2.0 + User Stories Welle 4  
**Zweck:** Abgleich des aktuellen Implementierungsstands gegen die aktualisierten Anforderungen

---

## Gesamtstatus

| Feature | Anforderung | Implementierungsstand | Lücken |
|---|---|---|---|
| Supabase Auth & Schema | W4 #1 | ✅ Vollständig | — |
| Berater-Dashboard | W4 #2 | ✅ Vollständig | — |
| GEG-Begehungsformular | W4 #3 | 🟡 ~90% | Lüftung prüfen |
| Foto-Upload | W4 #4 | ✅ Vollständig | AC-05.1: Upload-Button im Formular selbst fehlt |
| Landingpage (DE/EN) | W4 #5 | ✅ Vollständig | Kein Features-Abschnitt mit ≥3 Features? Prüfen |
| User Stories & ACs | W4 #6 | ✅ Vorhanden | Status noch "Entwurf", Review ausstehend |
| Testing lokal + live | W4 #7 | 🟡 Offen | Smartphone-Test (AC-07.5) noch nicht dokumentiert |
| Polish | W4 #8 | 🟡 Teilweise | — |
| Produkthandbuch | W4 #9 | ❌ Fehlt | HOWTO.md ist kein vollständiges Handbuch |

---

## Detailmapping je User Story

---

### US-W4-01 — Registrierung & Login

**Implementierung:** [src/app/[locale]/auth/login/page.tsx](../src/app/%5Blocale%5D/auth/login/page.tsx) · [src/app/[locale]/auth/register/page.tsx](../src/app/%5Blocale%5D/auth/register/page.tsx) · [src/app/auth/callback/route.ts](../src/app/auth/callback/route.ts) · [middleware.ts](../middleware.ts)

| AC | Beschreibung | Status | Befund |
|---|---|---|---|
| AC-01.1 | Registrierungsformular E-Mail + Passwort | ✅ | Implementiert in `register/page.tsx` |
| AC-01.2 | Bestätigungs-E-Mail nach Registrierung | ✅ | Supabase Auth, `callback/route.ts` vorhanden |
| AC-01.3 | Login → Redirect auf Dashboard | ✅ | Implementiert, Middleware schützt Routen |
| AC-01.4 | Fehlermeldung bei falschen Zugangsdaten | ✅ | Implementiert |
| AC-01.5 | Logout → Session beendet | ✅ | `LogoutButton.tsx` vorhanden |
| AC-01.6 | Geschützte Seiten — Redirect auf Login | ✅ | `middleware.ts` implementiert |
| A

*[truncated — see source for full prompt]*