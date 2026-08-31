drone_autonomy/
│
├── state.py
├── environment.py
├── terrain.py
├── obstacles.py
│
├── sensors/
│   ├── imu.py
│   ├── gps.py
│   ├── lidar.py
│   ├── depth.py
│   ├── camera.py
│   └── sensor_fusion.py
│
├── mapping/
│   ├── occupancy.py
│   ├── elevation.py
│   ├── traversability.py
│   ├── risk.py
│   └── uncertainty.py
│
├── paths/
│   ├── primitives.py
│   ├── straight.py
│   ├── curve.py
│   ├── climb.py
│   ├── descend.py
│   └── turn.py
│
├── planner/
│   ├── generator.py
│   ├── validator.py
│   ├── astar.py
│   ├── local_planner.py
│   └── cost_function.py
│
├── exploration/
│   ├── frontier.py
│   ├── coverage.py
│   ├── target_search.py
│   └── priority.py
│
├── swarm/
│   ├── communication.py
│   ├── neighbors.py
│   ├── map_sharing.py
│   ├── task_allocation.py
│   └── formation.py
│
├── resilience/
│   ├── weather.py
│   ├── failures.py
│   └── fallback.py
│
├── simulation/
│   ├── world.py
│   ├── physics.py
│   ├── scenarios.py
│   └── visualization.py
│
└── tests/
    ├── planner/
    ├── exploration/
    ├── swarm/
    └── resilience/