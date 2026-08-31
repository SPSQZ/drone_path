# Phase 06: Exploration and Task Allocation

## Goal
Assign areas and tasks to each drone and decide how the swarm covers unknown terrain efficiently.

## Tasks

- [ ] Build exploration map and coverage map
- [ ] Implement frontier-based exploration
- [ ] Add sub-area assignment for each drone
- [ ] Implement coverage planner for terrain segments
- [ ] Add task allocation algorithm:
  - greedy assignment
  - auction-based allocation
  - market-based task assignment
- [ ] Add region priority scoring based on:
  - unknown area size
  - terrain risk
  - likely target value
  - rescue importance
- [ ] Add area reassignment when a drone becomes blocked or low on battery
- [ ] Add dynamic reallocation during storm or communication loss
- [ ] Add map sharing among drones
- [ ] Add coverage completion checks and revisit logic

## Deliverables

- The swarm divides and covers a map without redundant scanning
- Drones can reassign work after route failure or new hazard discovery
- Exploration prioritizes high-value or high-risk terrain

## Exit condition

The swarm can explore a region efficiently and adapt coverage when the situation changes.
