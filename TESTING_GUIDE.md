# Software-Only Drone Testing Guide

## Overview

This autonomous drone swarm system is **100% software-based** and can be fully tested, validated, and evaluated without any physical hardware. The testing framework provides complete scenario-based evaluation capabilities.

---

## Quick Start: Running Tests

### 1. Run All Tests
```bash
cd c:\Users\shara\OneDrive\Documents\drone_path
python -m pytest -q tests/
```

Result: **65+ tests** covering all 17 phases validating:
- Simulation core functionality
- Drone state management
- Environment representation
- Path planning and validation
- Sensor simulation
- Mapping and terrain understanding
- Path selection and decision making
- Autonomous exploration
- Rescue intelligence
- Multi-drone coordination
- Formation control
- Collision avoidance
- Storm and weather resilience
- Failure simulation and recovery
- Evaluation and metrics collection

### 2. Run Specific Phase Tests
```bash
# Test simulation
python -m pytest tests/test_phase2_simulation.py -v

# Test exploration
python -m pytest tests/test_phase10_exploration.py -v

# Test swarm coordination
python -m pytest tests/test_phase12_swarm.py -v

# Test resilience
python -m pytest tests/test_phase15_resilience.py -v

# Test intelligent formation
python -m pytest tests/test_intelligent_formation.py -v
```

### 3. Run Evaluation Tests
```bash
python -m pytest tests/test_phase17_evaluation.py -v
```

---

## Testing Scenarios

### Built-in Scenario Templates

The system includes pre-built scenario templates that you can use to test different mission types:

```python
from evaluation.scenario_runner import ScenarioBuilder, ScenarioRunner

# Create a scenario runner
runner = ScenarioRunner()

# Use pre-built scenarios
scenarios = [
    ScenarioBuilder.single_drone_navigation(),
    ScenarioBuilder.obstacle_course(),
    ScenarioBuilder.multi_drone_exploration(num_drones=3),
    ScenarioBuilder.search_and_rescue(),
    ScenarioBuilder.storm_resilience(),
    ScenarioBuilder.communication_failure(),
    ScenarioBuilder.formation_test(formation_type="wedge"),
]

# Run all scenarios
for scenario in scenarios:
    result = runner.run_scenario(scenario)
    print(f"Scenario: {scenario['name']}")
    print(f"Result: {result}")
```

### Scenario Types Available

#### 1. **Single Drone Navigation**
Tests basic path planning and navigation without obstacles.
- Start: (0, 0)
- Goal: (40, 40)
- Validates: Path generation, trajectory following, state updates

#### 2. **Obstacle Course**
Tests obstacle avoidance and complex path planning.
- Multiple static obstacles
- No-go zones
- Validates: Collision detection, validation, candidate filtering

#### 3. **Multi-Drone Exploration**
Tests coordinated exploration with multiple drones.
- 2–10 drones
- Large exploration area
- Validates: Frontier detection, coverage tracking, coordination

#### 4. **Search & Rescue**
Tests target detection and investigation behavior.
- Multiple targets with confidence levels
- Terrain difficulty
- Validates: Target detection, priority ranking, investigation planning

#### 5. **Storm Resilience**
Tests adaptive behavior during adverse weather.
- Wind and gusts
- Visibility degradation
- Validates: Speed reduction, formation contraction, emergency hold

#### 6. **Communication Failure**
Tests autonomous operation when links fail.
- Packet loss simulation
- Link outages
- Validates: Local autonomy, fallback behavior, recovery

#### 7. **Formation Control**
Tests multi-drone formation maintenance and switching.
- Line, wedge, arc, diamond formations
- Path waypoints
- Validates: Formation offsets, collision avoidance, spacing adaptation

---

## Creating Custom Scenarios

### Manual Scenario Creation

```python
from evaluation.scenario_runner import ScenarioRunner

runner = ScenarioRunner()

# Define a custom scenario
custom_scenario = {
    "name": "my_custom_mission",
    "num_drones": 4,
    "world_size": (80, 80),
    "start_position": (5, 5),
    "goal_position": (75, 75),
    "obstacles": [
        {"x": 20, "y": 20, "radius": 5},
        {"x": 50, "y": 40, "radius": 4},
        {"x": 65, "y": 60, "radius": 3},
    ],
    "no_go_zones": [
        (10, 10, 15, 15),
        (60, 60, 70, 70),
    ],
    "weather": {
        "wind_speed": 8.0,
        "visibility": 0.7,
    },
    "formation": "wedge",
    "expected_completion_time": 30.0,
}

# Run scenario
result = runner.run_scenario(custom_scenario)
print(result)
```

### Scenario Configuration Options

```python
scenario = {
    # Required
    "name": "scenario_name",
    "num_drones": 1,
    "world_size": (width, height),
    
    # Navigation
    "start_position": (x, y),
    "goal_position": (x, y),
    
    # Environment
    "obstacles": [
        {"x": x, "y": y, "radius": r},
        ...
    ],
    "no_go_zones": [
        (x_min, y_min, x_max, y_max),
        ...
    ],
    
    # Mission
    "mission_type": "exploration|rescue|patrol|transport",
    
    # Weather
    "weather": {
        "wind_speed": 0.0,
        "storm_intensity": 0.0,
        "visibility": 1.0,
    },
    
    # Formation
    "formation": "line|wedge|arc|diamond",
    
    # Constraints
    "expected_completion_time": 30.0,
    "target_coverage": 0.90,
}
```

---

## Metrics & Evaluation

### Collecting Metrics

```python
from evaluation.metrics_collector import MetricsCollector

collector = MetricsCollector()

# Record drone positions
for time_step in range(100):
    x = time_step * 0.5
    y = time_step * 0.5
    collector.record_position(drone_id=1, x=x, y=y, z=0)

# Track exploration
for x in range(50):
    for y in range(50):
        collector.mark_cell_visited(x, y)

# Record battery usage
for time_step in range(100):
    battery = 100 - (time_step * 0.5)
    collector.record_battery_usage(drone_id=1, battery_percent=battery)

# Get metrics
print(f"Total distance: {collector.get_total_distance(drone_id=1):.2f}")
print(f"Coverage: {collector.get_coverage_percentage():.2f}%")
print(f"Average speed: {collector.get_average_speed(drone_id=1):.2f}")
print(f"Battery efficiency: {collector.get_battery_efficiency(drone_id=1):.2f}")
print(f"Collisions: {collector.get_collision_rate()}")
```

### Generating Reports

```python
from evaluation.evaluation_framework import EvaluationFramework

framework = EvaluationFramework()

test_results = {
    "single_drone_nav": {"success": True, "time": 12.0, "energy": 18},
    "obstacle_course": {"success": True, "time": 15.0, "energy": 22},
    "exploration": {"success": True, "time": 45.0, "energy": 60},
}

report = framework.generate_report(test_results)
print(report)

# Compare results
comparison = framework.compare_results([
    {"time": 15.0, "energy": 30},
    {"time": 10.0, "energy": 25},
])
print(f"Best: {comparison['best']}")
print(f"Average time: {comparison['average']['time']}")
```

---

## Component Testing

### Test Individual Systems

#### Simulation
```python
from simulation.world import World

world = World(width=50, height=50)
print(f"In bounds (25, 25): {world.in_bounds(25, 25)}")
print(f"In bounds (60, 60): {world.in_bounds(60, 60)}")
```

#### Path Planning
```python
from planner.generator import PathGenerator
from planner.validator import validate_trajectory

generator = PathGenerator()
trajectory = generator.generate_straight((0, 0), (10, 10), altitude=5.0)

print(f"Trajectory: {trajectory.name}")
print(f"Points: {trajectory.points}")
```

#### Formation Control
```python
from swarm.intelligent_formation import IntelligentFormationPlanner

planner = IntelligentFormationPlanner(num_drones=4)

mission_context = {
    "mission_type": "exploration",
    "energy_available": 80.0,
    "terrain_difficulty": 0.3,
    "wind_speed": 5.0,
    "num_obstacles": 2,
}

formation = planner.select_formation(mission_context)
print(f"Selected formation: {formation['type']}")
print(f"Offsets: {formation['offsets']}")
```

#### Resilience
```python
from resilience.weather_simulator import WeatherSimulator
from resilience.failure_simulator import FailureSimulator

# Weather simulation
weather = WeatherSimulator()
weather.set_storm_intensity(0.7)
wind = weather.generate_wind_gust()
print(f"Wind speed: {wind['speed']:.2f} m/s")
print(f"Visibility: {weather.get_visibility():.2f}")

# Failure simulation
failures = FailureSimulator()
failures.inject_failure("gps_loss", drone_id=1, duration=10)
print(f"Active failures: {failures.get_active_failures(drone_id=1)}")
```

---

## Integration Testing

### Full Mission Simulation

```python
from evaluation.scenario_runner import ScenarioBuilder, ScenarioRunner
from evaluation.metrics_collector import MetricsCollector
from evaluation.evaluation_framework import EvaluationFramework

# Setup
runner = ScenarioRunner()
collector = MetricsCollector()
framework = EvaluationFramework()

# Create scenario
scenario = ScenarioBuilder.multi_drone_exploration(num_drones=3)

# Run scenario
result = runner.run_scenario(scenario)

# Collect metrics
for i in range(100):
    collector.record_position(drone_id=1, x=i*0.5, y=i*0.5)
    collector.record_battery_usage(drone_id=1, battery_percent=100-i*0.5)

# Generate report
metrics = {
    "distance": collector.get_total_distance(1),
    "coverage": collector.get_coverage_percentage(),
    "battery_efficiency": collector.get_battery_efficiency(1),
    "time": 100,
}

report = framework.generate_report({"scenario": metrics})
print(report)
```

---

## Automated Test Suite

### Run Complete Test Suite

```bash
# Run all tests with verbose output
python -m pytest tests/ -v

# Run all tests and generate coverage
python -m pytest tests/ --cov=. --cov-report=html

# Run tests by marker
python -m pytest tests/ -m "not slow"

# Run specific test file
python -m pytest tests/test_phase10_exploration.py -v

# Run with detailed output
python -m pytest tests/ -vv --tb=short
```

### Creating Custom Test Files

```python
# tests/test_my_scenario.py
import pytest
from evaluation.scenario_runner import ScenarioBuilder, ScenarioRunner

def test_exploration_coverage():
    runner = ScenarioRunner()
    scenario = ScenarioBuilder.multi_drone_exploration(num_drones=3)
    
    result = runner.run_scenario(scenario)
    
    assert result["success"] is True
    assert result["completion"] >= 50.0

def test_rescue_mission():
    runner = ScenarioRunner()
    scenario = ScenarioBuilder.search_and_rescue()
    
    result = runner.run_scenario(scenario)
    
    assert result is not None
    assert "obstacles_avoided" in result
```

---

## Performance Benchmarking

### Benchmark Different Configurations

```python
from evaluation.scenario_runner import ScenarioBuilder, ScenarioRunner
from evaluation.evaluation_framework import EvaluationFramework

framework = EvaluationFramework()
runner = ScenarioRunner()

# Benchmark different drone counts
results = {}
for num_drones in [1, 2, 3, 4]:
    scenario = ScenarioBuilder.multi_drone_exploration(num_drones)
    result = runner.run_scenario(scenario)
    results[f"drones_{num_drones}"] = result

# Compare
comparison = framework.compare_results([
    results["drones_1"],
    results["drones_2"],
    results["drones_3"],
])

print(comparison)
```

### Benchmark Different Formations

```python
# Test different formations
for formation in ["line", "wedge", "arc", "diamond"]:
    scenario = ScenarioBuilder.formation_test(formation_type=formation)
    result = runner.run_scenario(scenario)
    
    framework.benchmark_scenario(
        f"formation_{formation}",
        result
    )

# Retrieve and compare
line_bench = framework.get_benchmark("formation_line")
wedge_bench = framework.get_benchmark("formation_wedge")
```

---

## Continuous Integration Testing

### Automated Test Workflow

```bash
# Install dependencies
pip install pytest pytest-cov

# Run full test suite
pytest tests/ --cov=. --cov-report=term-missing

# Run tests on code changes
pytest tests/ -v --tb=short

# Run tests with specific markers
pytest tests/ -m "phase17"
```

---

## Validation Checklist

### Before Deployment/Production

- [ ] All 65+ unit tests pass
- [ ] All scenario tests succeed
- [ ] Formation control validated for all types
- [ ] Collision avoidance verified in multi-drone scenarios
- [ ] Resilience tested with failure scenarios
- [ ] Coverage metrics meet targets (>85%)
- [ ] Battery efficiency acceptable (>0.5 distance/battery%)
- [ ] Communication failure recovery verified
- [ ] Storm adaptation tested at multiple intensities
- [ ] Multi-drone coordination synchronized

---

## Quick Reference Commands

```bash
# Run all tests
pytest tests/ -q

# Run with coverage report
pytest tests/ --cov=. --cov-report=html

# Run specific phase
pytest tests/test_phase10_exploration.py -v

# Run specific test
pytest tests/test_phase10_exploration.py::test_frontier_detector_identifies_unknown_regions -v

# Run in watch mode (requires pytest-watch)
ptw tests/

# Generate JUnit XML for CI/CD
pytest tests/ --junit-xml=test-results.xml

# Run tests in parallel (requires pytest-xdist)
pytest tests/ -n auto

# Profile test execution time
pytest tests/ --durations=10
```

---

## Troubleshooting

### Common Issues

**Import errors:**
```bash
# Ensure you're in the project directory
cd c:\Users\shara\OneDrive\Documents\drone_path

# Install dependencies
pip install -r requirements.txt
```

**Test failures:**
```bash
# Run with verbose output to see detailed errors
pytest tests/ -vv --tb=long
```

**Performance issues:**
```bash
# Check which tests are slowest
pytest tests/ --durations=10
```

---

## Next Steps

1. **Modify scenarios** to match your specific use cases
2. **Add custom metrics** to evaluate performance criteria
3. **Extend test cases** for edge cases and stress testing
4. **Integrate with CI/CD** pipeline for automated testing
5. **Benchmark against baseline** metrics for regression detection

All components are testable, measurable, and validatable **without any physical hardware**.
