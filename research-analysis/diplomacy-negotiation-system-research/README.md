# DIPLOMACY NEGOTIATION SYSTEM RESEARCH

> **Dato**: 2025-11-02
**Formål**: Forbedre diplomati-systemet med interaktive forhandlinger inspirert av Civilization

---

## 1. CIVILIZATION 6 DIPLOM

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Forskning: Interaktivt Forhandlingssystem for Diplomati

**Dato**: 2025-11-02
**Formål**: Forbedre diplomati-systemet med interaktive forhandlinger inspirert av Civilization

---

## 1. CIVILIZATION 6 DIPLOMATI-SYSTEM - ANALYSE

### 1.1 Nøkkelfunksjoner fra Civilization 6

#### AI Leder-Personligheter og Agendaer
- **Personlige Agendaer**: Hver leder har en unik agenda som alltid er den samme
  - Eks: Gandhi hater sivilisasjoner som bruker atomvåpen
  - Eks: Gilgamesh elsker allierte og vil beskytte dem
- **Skjulte Agendaer**: Tilfeldig tildelt, endres fra spill til spill
  - Gir variasjon og gjør AI mindre forutsigbar
- **Agendaer påvirker alle diplomatiske beslutninger**

#### Forhold og Scoring-System
- **Akkumulerende Score**: Alle handlinger de siste 30-50 runder teller
- **Terskelverdier for Diplomati**:
  - Score < -5: Risiko for denonsering
  - Score > -4: Unngår denonsering
- **Modifikatorer**:
  - Delegasjoner: Koster 25 gull, gir bonus til forhold
  - Ambassader: Gir bedre forhold og mer informasjon
  - Handelsavtaler: Forbedrer forhold over tid
  - Krigshandlinger: Kraftig negativ effekt

#### Synlighetssystem
1. **Første Kontakt**: Minimal informasjon
2. **Delegasjon Sendt**: Kan se noen agendaer
3. **Ambassade**: Full informasjon om agendaer og preferanser

#### Forhandlingssystem
- **Multi-item Forhandlinger**: Kan tilby/kreve flere ting samtidig
  - Gull, ressurser, byer, avtaler
- **Gjensidighet**: AI evaluerer om handelen er rettferdig
- **Historikk Påvirker**: Tidligere brudd på avtaler gjør AI mindre tilbøyelig

#### Grievance-System
- **Automatiske Grievances**: Genereres av aggressive handlinger
  - Kriger uten årsak: Stor grievance
  - Spionasje oppdaget: Mindre grievance
- **Tidsbasert Nedgang**: Grievances reduseres over tid
- **Påvirker Krigsoppslutning**: Legitimerer krig

---

## 2. EKSISTERENDE SYSTEM I VECTOR WAR GAMES

### 2.1 Nåværende Styrker

#### Omfattende 3-Fase System
Spillet har allerede et sofistikert diplomati-system:

**Fa

*[truncated — see source for full prompt]*