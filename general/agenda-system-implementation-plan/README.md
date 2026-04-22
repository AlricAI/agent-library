# AGENDA SYSTEM IMPLEMENTATION PLAN

> **Opprettet**: 2025-11-02
**Status**: Implementation Ready
**Estimert Total Tid**: 1-2 uker

---

## OVERSIKT

Dette dokumentet beskriver den detaljer

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Implementasjonsplan: Agenda-System for AI Leder-Personligheter

**Opprettet**: 2025-11-02
**Status**: Implementation Ready
**Estimert Total Tid**: 1-2 uker

---

## OVERSIKT

Dette dokumentet beskriver den detaljerte implementasjonsplanen for Phase 4 av diplomati-systemet: Agenda-System for Unique Leader Personalities. Systemet vil gi hver AI leder:
- 1 Primary Agenda (alltid synlig)
- 1 Hidden Agenda (avsløres over tid)
- Unique personlighet som påvirker alle diplomatiske beslutninger

**Status av Eksisterende Implementasjon**:
- ✅ `src/lib/agendaDefinitions.ts` - 8 primary + 8 hidden agendas definert
- ✅ `src/lib/agendaSystem.ts` - Core functionality implementert
- ✅ `src/types/negotiation.ts` - Agenda types definert
- ⏳ Integration med game initialization - IKKE GJORT
- ⏳ Integration med AI evaluation - IKKE GJORT
- ⏳ Integration med turn processing - IKKE GJORT
- ⏳ UI components - IKKE GJORT
- ⏳ Testing - IKKE GJORT

---

## OPPGAVER

### Oppgave 4.1: Integrer Agenda Assignment ved Game Start

**Fil**: `src/pages/Index.tsx` eller equivalent game initialization
**Varighet**: 0.5-1 dag

**Beskrivelse**: Kalle `initializeNationAgendas()` når spillet starter for å gi alle AI nations agendaer.

**Implementasjon**:

```typescript
import { initializeNationAgendas } from '@/lib/agendaSystem';

// I game initialization (finn existing nation setup code)
// Etter at nations er opprettet, men før spillet starter:

const nationsWithAgendas = initializeNationAgendas(
  nations,
  playerNationId,
  seededRng  // Bruk seeded RNG for reproducibility
);

setNations(nationsWithAgendas);

// Log for debugging
log('=== LEADER AGENDAS ===');
nationsWithAgendas.forEach(nation => {
  if (nation.id !== playerNationId) {
    const primary = nation.agendas?.find(a => a.type === 'primary');
    const hidden = nation.agendas?.find(a => a.type === 'hidden');
    log(`${nation.name}:`);
    log(`  Primary: ${primary?.name}`);
    log(`  Hidden: ${hidden?.name} (not revealed)`);
  }
});
```


*[truncated — see source for full prompt]*