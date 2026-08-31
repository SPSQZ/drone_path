# Phase 02: Single Drone Autonomy

## Goal
Build one drone that can fly, localize itself, avoid simple obstacles, and stay safe before adding swarm logic.

## Tasks

- [ ] Set up flight stack:
  - PX4 or ArduPilot
  - MAVLink communication
  - flight mode management
- [ ] Implement state estimation:
  - IMU fusion
  - GPS/RTK integration
  - altimeter and heading
  - basic localization output
- [ ] Add waypoint navigation:
  - takeoff
  - fly to goal
  - hold position
  - land
- [ ] Add local altitude and heading control
- [ ] Integrate obstacle detection:
  - LiDAR or depth camera
  - near-field obstacle warning
- [ ] Add emergency behavior:
  - stop and hover
  - avoid obstacle
  - return to safe point
  - emergency landing
- [ ] Add battery monitoring and low-power logic
- [ ] Add watchdog for sensor faults and flight states
- [ ] Validate in simulation with simple terrain
- [ ] Validate on real flight in open environment

## Deliverables

- One drone can fly stable autonomous missions
- One drone can stop and recover from obstacle risk
- One drone can land or return safely under low battery

## Exit condition

You have a stable single drone baseline before adding any swarm features.
