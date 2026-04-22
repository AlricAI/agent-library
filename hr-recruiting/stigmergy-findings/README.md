# Stigmergy Findings

> **Date:** January 3, 2026  
**Experiment:** Emergent pathfinding through pheromone-based stigmergy  
**Live demo:** https://kochi.to/amber/stigmergy.h

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Stigmergy Experiment: Full Findings

**Date:** January 3, 2026  
**Experiment:** Emergent pathfinding through pheromone-based stigmergy  
**Live demo:** https://kochi.to/amber/stigmergy.html

## Expected Behavior

The simulation should demonstrate **stigmergy** — indirect coordination through environmental modification. Here's what should happen:

### Phase 1: Chaotic Exploration (0-50 generations)
- 100 agents spawn at the nest (brown circle)
- Each agent has no memory, no communication with other agents
- Agents move using a simple rule:
  - If no food: move toward nearest food source (2 green circles)
  - If carrying food: move toward nest
  - Movement biased by: pheromone strength (50%) + direction to goal + randomness (20%)
- Initially, pheromones are scattered everywhere as agents explore randomly
- Efficiency should be LOW (10-30%) because pheromones are diffuse

### Phase 2: Reinforcement (50-200 generations)
- Shorter paths get traversed more frequently (agents complete round trips faster)
- More frequent traversal = stronger pheromone deposits
- Stronger pheromones attract more agents (positive feedback loop)
- Longer/inefficient paths see less traffic, pheromones evaporate (0.995 rate per frame)
- Efficiency should RISE (30-60%) as trails converge on shorter routes

### Phase 3: Stabilization (200+ generations)
- The system reaches equilibrium
- Clear, bright pheromone trails emerge between nest and both food sources
- Most agents follow these trails (high convergence %)
- Efficiency should plateau (55-70%)
- System demonstrates **emergent optimization** without any agent knowing the optimal path

### Key Metrics

1. **Path Efficiency**: % of pheromones on optimal paths (straight lines ±3 cells to food sources) vs scattered elsewhere
2. **Convergence**: % of cells with very low pheromone (< 0.1) — high convergence = trails are focused, not diffuse
3. **Generation**: Time steps elapsed
4. **Active Agents**: Should stay at 100 throughout

## Code Review



*[truncated — see source for full prompt]*