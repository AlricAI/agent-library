# Projekt Beschreibung Landingpage Basis

> **Erstellt:** 07. April 2026  
**Zweck:** Basis für Landingpage, Investoren-Pitch, Onboarding neuer Entwickler  
**Status:** Welle 4 abgeschlossen · W

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Energieberater App — Projektbeschreibung
**Erstellt:** 07. April 2026  
**Zweck:** Basis für Landingpage, Investoren-Pitch, Onboarding neuer Entwickler  
**Status:** Welle 4 abgeschlossen · Welle 5 in Planung

---

## Kurzbeschreibung (Hero-Text-Basis)

> **Energieberatung. Digital. Effizient.**
>
> Die Energieberater-App ist das digitale Werkzeug für freiberufliche Energieberater und KMU — von der ersten Projekt-Anlage bis zur vollständigen Gebäudebegehung. Vor Ort. Am Smartphone. DSGVO-konform.

---

## Das Problem, das wir lösen

Energieberater verbringen heute **3–6 Stunden pro Projekt** mit manueller Nacharbeit:

- Gebäudedaten auf Papier oder PDF-Formular erfassen
- Fotos auf dem Handy, nicht dem Projekt zugeordnet
- Förderprogramme (BAFA/KfW) manuell recherchieren
- Ergebnisse nochmals in Word/Excel abtippen für den Bericht
- Kundenkommunikation per E-Mail, Unterlagen über Dropbox verteilt

Der Berater ist kein Schreibtischarbeiter —  
**er steht im Keller, in der Heizungsanlage, auf dem Dachboden.**  
Seine App muss seinen Werkzeug-Koffer ersetzen, nicht einen Büroplatz.

---

## Zielgruppe

| Segment | Beschreibung |
|---|---|
| **Primär** | Freiberufliche Energieberater (EEE-zertifiziert, BAFA-Liste) |
| **Sekundär** | Kleine Energieberatungsbüros (2–10 Personen) |
| **Marktgröße** | ~14.000 zugelassene Energieeffizienz-Experten (BAFA-Liste, Stand 2025) |
| **Endkunden** | Immobilieneigentümer, ~80% älter als 40 Jahre, kaufen oder sanieren Wohngebäude |

**Wichtig aus dem Berater-Feedback (April 2026):**  
Die Endkunden sind größtenteils analog. Das Portal richtet sich an den **Berater**, nicht an den Endkunden. Kein Self-Service, kein KI-Chatbot nach außen — der persönliche Kontakt ist der Kernwert des Beraters.

---

## Technologie-Stack

| Ebene | Technologie |
|---|---|
| Frontend | Next.js 16 (App Router), TypeScript, Tailwind CSS v4 |
| Backend / Datenbank | Supabase (PostgreSQL, Row-Level Security, Supabase Auth, Supabase Storage) |
| Deployment |

*[truncated — see source for full prompt]*