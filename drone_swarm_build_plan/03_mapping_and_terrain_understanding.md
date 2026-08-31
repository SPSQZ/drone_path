# Phase 03: Mapping and Terrain Understanding

## Goal
Give each drone a local map of terrain, obstacles, and risky areas so it can decide where it can fly safely.

## Tasks

- [ ] Integrate sensor streams:
  - IMU
  - LiDAR or depth camera
  - RGB camera
  - GPS
  - altimeter
- [ ] Build occupancy map
- [ ] Build elevation map or terrain height map
- [ ] Build traversability map:
  - slope cost
  - roughness cost
  - obstacle height cost
  - vegetation or debris cost
- [ ] Estimate risk per map cell
- [ ] Detect no-go zones:
  - cliffs
  - steep landslides
  - narrow ravines
  - blocked routes
- [ ] Generate local safe corridor route
- [ ] Implement local path planner using map info
- [ ] Add map update loop with new observations
- [ ] Add uncertainty map for uncertain terrain

## Deliverables

- Safe-path map for each drone
- Terrain risk scoring engine
- Local route generation around obstacles and steep areas

## Exit condition

The drone can tell which areas are safe, risky, or unknown, and can plan around rough terrain.
