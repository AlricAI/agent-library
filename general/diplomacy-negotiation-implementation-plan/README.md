# DIPLOMACY NEGOTIATION IMPLEMENTATION PLAN

> **Opprettet**: 2025-11-02
**Status**: Planlegging
**Estimert Total Tid**: 8-12 uker

---

## OVERSIKT

Dette dokumentet beskriver den detaljerte imple

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Implementasjonsplan: Interaktivt Forhandlingssystem

**Opprettet**: 2025-11-02
**Status**: Planlegging
**Estimert Total Tid**: 8-12 uker

---

## OVERSIKT

Dette dokumentet beskriver den detaljerte implementasjonsplanen for det nye interaktive forhandlingssystemet inspirert av Civilization. Systemet er delt inn i 5 faser med spesifikke oppgaver for hver fase.

---

## FASE 1: GRUNNLEGGENDE NEGOTIATION ENGINE
**Varighet**: 1-2 uker
**Prioritet**: Kritisk (må være ferdig først)

### Oppgave 1.1: Definer TypeScript-typer
**Fil**: `src/types/negotiation.ts`

**Beskrivelse**: Lag alle nødvendige TypeScript interfaces og types for forhandlingssystemet.

**Typer som skal lages**:
```typescript
- NegotiableItemType (union type)
- NegotiableItem (interface)
- NegotiationState (interface)
- NegotiationRound (interface)
- AIEvaluation (interface)
- CounterOffer (interface)
- LeaderContactState (interface)
- LeaderMood (type)
- VisibleLeaderInfo (interface)
- Agenda (interface)
- AgendaModifier (interface)
- DiplomaticAction (interface)
- AIInitiatedNegotiation (interface)
- NegotiationPurpose (type)
```

**Akseptanskriterier**:
- [ ] Alle typer kompilerer uten feil
- [ ] Typene er godt dokumentert med TSDoc comments
- [ ] Typene eksporteres korrekt fra index

**Estimert Tid**: 4-6 timer

---

### Oppgave 1.2: Implementer negotiationUtils.ts
**Fil**: `src/lib/negotiationUtils.ts`

**Beskrivelse**: Implementer core utility-funksjoner for å håndtere forhandlinger.

**Funksjoner som skal implementeres**:
```typescript
✅ createNegotiation()
✅ addItemToOffer()
✅ addItemToRequest()
✅ removeItem()
✅ calculateItemValue()
✅ calculateTotalValue()
✅ validateNegotiation()
✅ canAffordItems()
✅ applyNegotiationDeal()
```

**Item Value Calculations**:
- **Gold**: Direct value (1:1)
- **Intel**: 3x value of gold
- **Production**: 2x value of gold
- **Alliance**: Base value 1000, modified by relationship
- **Treaty**: Base value 300-800 depending on type
- **Promise**: Base value 200-500 depe

*[truncated — see source for full prompt]*