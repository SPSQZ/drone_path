# Phase 01: Foundation and Requirements

## Goal
Define the mission, environment, flight constraints, and swarm rules before building the software.

## Tasks

- [ ] Define mission type:
  - rescue search
  - mountain exploration
  - forest mapping
  - hazard scouting
  - disaster area survey
- [ ] Define operating environment:
  - open mountain ridge
  - canyon
  - forested terrain
  - urban rubble zone
  - GPS-denied area
- [ ] Define swarm size:
  - 3 drones minimum prototype
  - 5 drones for realistic coverage
  - 10 drones for larger missions
- [ ] Define safety envelope:
  - minimum altitude
  - max slope angle
  - max wind exposure
  - max battery drain before return
  - no-go zones
- [ ] Define communication assumptions:
  - full connectivity
  - partial connectivity
  - degraded radio range
  - recovery after outage
- [ ] Define drone hardware baseline:
  - multirotor size
  - battery capacity
  - payload weight
  - onboard computer
  - radio modem
- [ ] Define software constraint:
  - onboard local autonomy required
  - central coordinator optional only for mission control
- [ ] Define mission states:
  - exploration
  - avoidance
  - hold position
  - return to safe zone
  - emergency landing
- [ ] Define failure cases to handle:
  - GPS loss
  - radio drop
  - battery shortage
  - sensor failure
  - leader loss
  - obstacle block

## Deliverables

- Mission requirement document
- Safety policy document
- System assumptions for swarm behavior
- Hardware baseline list

## Exit condition

You must know exactly what the drones are expected to explore, how dangerous the environment is, and how the swarm should behave when it loses a drone, link, or sensor.
