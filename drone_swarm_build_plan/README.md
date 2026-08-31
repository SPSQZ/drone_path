# Drone Swarm Exploration Build Plan

This folder contains the execution sequence for building a resilient swarm drone system for mountain exploration, rescue scouting, and harsh terrain missions.

## Scope

This roadmap is focused on software architecture, autonomy logic, planning, coordination, and resilience. It assumes the flight controller and sensors are already available or can be integrated later.

## Recommended order

1. [01_foundation_and_requirements.md](01_foundation_and_requirements.md)
2. [02_single_drone_autonomy.md](02_single_drone_autonomy.md)
3. [03_mapping_and_terrain_understanding.md](03_mapping_and_terrain_understanding.md)
4. [04_swarm_network_and_localization.md](04_swarm_network_and_localization.md)
5. [05_formation_control_and_collision_avoidance.md](05_formation_control_and_collision_avoidance.md)
6. [06_exploration_and_task_allocation.md](06_exploration_and_task_allocation.md)
7. [07_storm_and_terrain_resilience.md](07_storm_and_terrain_resilience.md)
8. [08_simulation_and_validation.md](08_simulation_and_validation.md)
9. [09_real_world_deployment.md](09_real_world_deployment.md)
10. [10_software_only_task_list.md](10_software_only_task_list.md)

## Build principle

Build one drone first, then make two drones coordinate, then build a swarm. Do not start with full swarm autonomy.

## Target behaviors

- survey rough terrain without a fixed target
- maintain safe spacing in formation
- avoid terrain and drone collisions
- continue even with partial communication loss
- adapt formation for mountains, storms, and obstacles
- share discovered information with the swarm
- recover from failures and rejoin when possible

## Final software-only task list

The concise implementation sequence is in [10_software_only_task_list.md](10_software_only_task_list.md).
