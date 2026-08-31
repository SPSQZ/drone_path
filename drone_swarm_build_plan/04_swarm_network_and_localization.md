# Phase 04: Swarm Network and Localization

## Goal
Let multiple drones know where each other is, share data, and keep working when communication is partial or weak.

## Tasks

- [ ] Set up inter-drone communication network
  - mesh or ad hoc radio link
  - neighbor discovery
  - heartbeat and status packet
- [ ] Define swarm message types:
  - position
  - velocity
  - heading
  - battery health
  - mission state
  - hazard report
  - map update
- [ ] Add relative localization:
  - UWB if needed
  - visual relative detection
  - range-based estimation
- [ ] Build neighbor tracking system
- [ ] Add drone state broadcast to swarm
- [ ] Add message loss handling
- [ ] Handle partial connectivity and disconnected nodes
- [ ] Implement local autonomy mode when the drone loses swarm link
- [ ] Add network reconnection logic and rejoin strategy
- [ ] Add a shared map update pipeline

## Deliverables

- Drone-to-drone communication working
- Neighbor tracking and health awareness in place
- Drones can continue local missions even if network is degraded

## Exit condition

The swarm has communication and awareness, but still behaves safely even when some drones become isolated.
