# Spielberg dense survey grid, slam_toolbox, 0.020 m

A sibling of `../res_0050/` made with non-default mapper settings; no launch selects it. Kept beside the committed grid: algorithms and data are added, never replaced.

Picture: `Spielberg.png`.

- Simulator: f1tenth_gym_jax
- Odometry: ground truth (`/ground_truth/odom`), scan matching and loop closure off
- Resolution: 0.020 m per cell
- Accuracy vs ground truth: nearest occupied cell per wall point, left/right: max 0.066/0.069 m, p95 0.046, median 0.017 (full figures in the yaml header)
- Command: `./scripts/map_track.sh config/scenarios/spielberg_survey.yaml <stem>` (seed 42, 1x, slam_toolbox async mapper, scan matching off, `config/localization/slam_toolbox_survey.yaml`) with overrides that are not committed defaults: slam_toolbox resolution 0.020, minimum_travel_distance 0.02, minimum_travel_heading 0.02, controller maximum_speed 1.5 m/s, a scenario copy with max_steps 100000 (2 laps); the yaml header holds the rest
- Date: 2026-10-23
- GR-roboracer commit: main `cfbf844`
