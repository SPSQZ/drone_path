# Phase 05: Formation Control and Collision Avoidance

## Goal
Keep the swarm in a safe geometric pattern while avoiding collisions with each other, terrain, and obstacles.

## Tasks

- [ ] Define formation shapes:
  - line
  - arc
  - curve
  - wedge
  - diamond
  - dynamic adaptive formation
- [ ] Choose formation control method:
  - leader-follower
  - virtual leader
  - consensus-based control
  - distributed formation control
- [ ] Define collision safety distance between drones
- [ ] Add formation maintenance using relative offsets
- [ ] Add vehicle-to-vehicle collision avoidance
- [ ] Add obstacle-aware formation adaptation
- [ ] Add dynamic switching between formation shapes
- [ ] Implement slope-aware formation change in mountains
- [ ] Stress test formation under tight terrain and turns
- [ ] Add emergency separation if drones get too close

## Deliverables

- Swarm can maintain arc and curve formations in rough terrain
- Drones do not collide during turns, obstacle avoidance, or replanning
- Formation changes automatically based on terrain and risk

## Exit condition

The swarm can fly as a coordinated group while preserving minimum safe separation.
