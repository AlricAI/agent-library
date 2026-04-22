# Phase 3 4

> Denne fasen varer i fire uker og bygger videre på fundamentet fra fase 1 og 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Fase 3 – Utvidelser og balanse

Denne fasen varer i fire uker og bygger videre på fundamentet fra fase 1 og 2. Fokus ligger på å åpne opp kooperativ spillopplevelse, innføre moralske og politiske variabler, samt levere audiovisuelle tilbakemeldinger som forsterker simulasjonen.

## Kooperativ modus

- **Synkroniseringsmekanismer:**
  - Etabler WebSocket-kanal `co-op-sync` for deling av turdata, kartoppdateringer og hendelseslogg i sanntid.
  - Implementer låsestrategier i klientstate ("optimistic lock" pr. region) slik at to spillere ikke overstyrer samme ressursmodul.
  - Legg inn "turn heartbeat"-meldinger hver 5. sekund for å oppdage bortfall og trigge reconnect.
- **Delte ressurser:**
  - Opprett ressursfond for drivstoff, forsyninger og luftstøtte som begge spillere kan disponere, med kvoter basert på rolle (strateg vs. taktiker).
  - Innfør felles "command queue" hvor planlagte handlinger må bekreftes av begge parter for å utføres i felt.
- **UI-indikatorer:**
  - Statuspanel for spillerroller med synlig ressursbalanse og buff/debuff-effekter.
  - Overlegg med ikonografi som viser hvilke områder som er låst av medspillerens pågående ordre.
  - Notifikasjoner i høyre kolonne som oppsummerer synk-suksess, ventende bekreftelser og konflikter.

## Moralsystem og politiske hendelser

- **Event-generator:**
  - Modul `moraleEventService` som trekker scenarier fra datasett basert på frontlinje-status, sivile tap og internasjonalt press.
  - Scheduler som injiserer hendelser hvert 3.–5. trekk, med sannsynlighetsvekting per region.
- **Påvirkning på gameplayvariabler:**
  - Moralsk indeks pr. region justerer produksjon, rekruttering og motstandsvilje.
  - Politisk støtte påvirker ressursdrop og diplomatiske buffere (f.eks. forsinkelse i fiendens opptrapping).
  - Negative hendelser kan trigge "policy choice"-dialoger der spillerne må velge kompromiss med ulike konsekvenser.
- **Analyse & logging:**
  - Lag dashboard-panel som viser moraltrend og politisk temperatur o

*[truncated — see source for full prompt]*