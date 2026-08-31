# Mission Specification

## Mission type

Autonomous exploration and rescue-support drone system for rough and unknown terrain.

## Goal

The drone should explore unknown terrain, build a local understanding of the environment, choose safe flight paths, and continue exploring even when the environment is uncertain or partially blocked.

## Primary constraints

- no fixed destination required
- must operate in rough terrain
- must avoid obstacles and risky slopes
- must remain safe under uncertain sensor and map conditions
- must support fallback behavior if the route becomes blocked

## Safety limits

- minimum altitude threshold
- maximum slope angle allowed
- minimum clearance from terrain and obstacles
- maximum battery drain before return-to-safe-zone
- maximum acceptable risk before switching to fallback behavior

## Mission states

- explore
- inspect
- avoid_obstacle
- hold_position
- retreat
- return_to_safe_zone
- emergency_landing

## Failure states

- sensor degradation
- GPS loss
- blocked path
- low battery
- communication loss
- unexpected obstacle
- unsafe terrain risk

## Software scope for current phase

This phase focuses only on:
- mission definition
- system boundaries
- software architecture
- simulation foundations
- project structure

It does not yet focus on:
- full swarm communication
- multi-drone formation control
- real hardware integration
