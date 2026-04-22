# AGENDA SYSTEM RESEARCH

> **Dato**: 2025-11-02
**Formål**: Implementere unique leder-personligheter gjennom et agenda-system inspirert av Civilization

---

## 1. CIVILIZATION 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Forskning: Agenda-System for AI Leder-Personligheter

**Dato**: 2025-11-02
**Formål**: Implementere unique leder-personligheter gjennom et agenda-system inspirert av Civilization

---

## 1. CIVILIZATION 6 AGENDA-SYSTEM - ANALYSE

### 1.1 Hvordan Civilization's Agenda-System Fungerer

#### To Typer Agendaer

**1. Leader Agenda (Primary)**:
- Hver leder har én unik agenda som alltid er den samme
- Synlig for spilleren fra første møte
- Eksempler:
  - Gandhi: "Peacekeeper" - Hater land som bruker atomvåpen
  - Gilgamesh: "Enkidu's Ally" - Elsker allierte, blir venn for livet
  - Alexander: "To the World's End" - Vil kontrollere alle bystater
  - Montezuma: "Gift for the Tlatoani" - Verdsetter luksusvarer

**2. Hidden Agenda**:
- Hver leder får én tilfeldig agenda fra en pool
- Endres fra spill til spill (gir replay value)
- Ikke synlig fra start - må oppdages over tid
- Eksempler:
  - "Exploiter": Respekterer land med mange ressurser
  - "Nuke Happy": Liker land som har atomvåpen
  - "Money Grubber": Verdsetter store gullreserver
  - "Standing Army": Respekterer sterke militærmakter

#### Agenda-Mekanikker

**Synlighets-System**:
1. **Første Kontakt**: Kun leader agenda synlig
2. **Etter Delegasjon Sendt**: Hidden agenda kan oppdages
3. **Etter Ambassade Etablert**: Hidden agenda garantert avslørt
4. **Alternativt**: Over tid med god relationship (20-30 turns)

**Påvirkning på AI-Beslutninger**:
- Agendaer gir +/- modifiers til relationship
- Påvirker alle diplomatiske beslutninger
- AI vil kommentere når agenda blir krenket/respektert
- Kan være årsak til krig eller fredelig samarbeid

**Eksempel - Gandhi's "Peacekeeper"**:
```
IF player uses nuclear weapons:
  - Relationship: -30 (permanent penalty)
  - Will denounce player
  - Extremely unlikely to ally
  - May declare war if relationship drops low enough

IF player has no nukes AND promotes peace:
  - Relationship: +10 (bonus)
  - More likely to accept alliances
  - Will support player in World Congress
```

###

*[truncated — see source for full prompt]*