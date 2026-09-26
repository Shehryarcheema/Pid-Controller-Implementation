# PID Controller Implementation — Wall-Following Mobile Robot

A PID-controlled wall-following mobile robot simulated in CoppeliaSim using
the Pioneer P3-DX platform. The robot maintains a fixed distance from the
wall, handles corners and narrow corridors, and follows smoothly without
collisions — demonstrating classical closed-loop control stability on a
mobile robot.

Built as applied robotics coursework (MSc AI, De Montfort University); the
accompanying project write-up is `README- P2952028 (SHEHRYAR).pdf` in this
repo.

## Highlights

- **PID control loop (Kp, Ki, Kd)** implemented in Lua for steering and
  velocity regulation of a differential-drive robot.
- **Left and right wall following** — the robot detects and tracks the
  nearest wall using ultrasonic proximity-sensor feedback.
- **Random reorientation** — if placed randomly, the robot reorients,
  finds the closest wall, and resumes stable wall-following without manual
  intervention.
- **Corner detection and correction** with smooth velocity and steering
  control, tuned to minimize oscillation.
- **Multi-robot extension** — a cooperative scene with multiple robots
  following the wall while avoiding obstacles.

## Scenes

Each task is a self-contained CoppeliaSim scene (`.ttt`):

1. **Task 1 — PID controller with graph** — core PID controller
   implementation with plotted controller response (error / correction
   over time).
2. **Task 2 — PID tuning** — wall-following with random robot placement;
   the PID gains were tuned here for stable, low-oscillation tracking.
3. **Task 3 — custom scene** — an original scene where the robot follows
   the wall precisely and without collision.
4. **Task 4 — cooperative multi-robot** — multiple robots following the
   wall and avoiding obstacles cooperatively (extra task; details per the
   scene itself).

## Tech stack

- **CoppeliaSim** (Edu version) — simulation environment
- **Pioneer P3-DX** mobile robot with ultrasonic proximity sensors
- **Lua** scripting for the embedded control logic
- **PID control** (proportional / integral / derivative terms) for
  closed-loop distance regulation

## Control design

The controller reads the ultrasonic proximity sensors to estimate the
distance to the wall, computes the tracking error against a target
stand-off distance, and applies a PID law to adjust linear and angular
velocity. The integral term removes steady-state offset, the derivative
term damps oscillations, and the tuned gains were validated on the
wall-following and random-placement scenarios before being carried into
the custom and multi-robot scenes.

## Repository structure

```
├── "Task 1- Implementing a PID Controller with Graph-Complete.ttt"                # PID implementation + response graphs
├── "Task 2- PID Tunning Complete (Robot Follow wall and move random).ttt"         # PID tuning / wall-follow / random placement
├── "Task 3. Extra Task Own Create Scene Robot Perfectly Follow.ttt"               # original scene, precise wall-following
├── "Task 4- Extra Multiple Cooperative Robots following wall and avoid obstacle.ttt"  # cooperative multi-robot + obstacle avoidance
├── "README- P2952028 (SHEHRYAR).pdf"                                              # project write-up
└── README.md
```

## Getting started

1. Install **CoppeliaSim (Edu version)** and clone this repository.
2. Open a scene by double-clicking a `.ttt` file (or File → Open scene);
   filenames contain spaces, so quote them in a terminal, e.g.:
   `coppeliaSim "Task 2- PID Tunning Complete (Robot Follow wall and move random).ttt"`.
3. Press **Run simulation** to start the controller; graphs (Task 1) and
   the robot's wall-following behavior are observable in the scene.
4. Tune `Kp`, `Ki`, `Kd` in the embedded Lua script to explore the
   stability/overshoot trade-off in the tuning scene.

## Author

**SHEHRYAR** (P2952028) — MSc AI, De Montfort University.
