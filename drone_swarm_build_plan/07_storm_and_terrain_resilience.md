# Phase 07: Storm and Terrain Resilience

## Goal
Make the swarm adapt to bad weather, exposed ridges, rough terrain, and degraded conditions without losing the mission.

## Tasks

- [ ] Add weather risk estimation:
  - wind
  - gust intensity
  - visibility drop
  - dust or smoke
- [ ] Add terrain risk model:
  - slope
  - narrow pass risk
  - cliff risk
  - debris zones
- [ ] Add safe-route scoring based on risk and uncertainty
- [ ] Implement formation contraction in high wind or low visibility
- [ ] Implement route rerouting around bad weather cells
- [ ] Add low-altitude or sheltered-corridor preference logic
- [ ] Add storm-safe return-to-base or return-to-safe-zone behavior
- [ ] Add priority drift policy when mission risk increases
- [ ] Add dynamic speed limitation under rough conditions
- [ ] Add emergency hold behavior for severe weather

## Deliverables

- Swarm changes formation and route based on environment risk
- Storm or mountain conditions do not cause uncontrolled flight or collision
- Drones prefer safe fallback behavior when conditions worsen

## Exit condition

The swarm is robust under wind, poor visibility, and harsh terrain.
