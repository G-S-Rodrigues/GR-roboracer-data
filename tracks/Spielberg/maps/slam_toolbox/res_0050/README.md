# Spielberg survey grid, slam_toolbox, 0.05 m

The grid amcl localizes on (`pose_source:=amcl`). A survey, not an autonomous SLAM result: the car drives on ground truth while slam_toolbox lays `/scan` at the exact poses.

Picture: `Spielberg.png`.

- Simulator: f1tenth_gym_jax (GR-roboracer's headless gym)
- Odometry: ground truth (`/ground_truth/odom`), scan matching and loop closure off
- Resolution: 0.05 m per cell
- Accuracy vs ground truth: identity residual against the ground-truth walls: median 0.043 m, p95 0.094 m (measured 2026-10-14 against the pre-part-2.1 gym PNG; against the current PNG RACELINE-1120 measures the extracted bounds at about 0.09 m); the yaml header holds the full figures
- Command: `./scripts/map_track.sh config/scenarios/spielberg_survey.yaml <stem>` (seed 42, 1x, slam_toolbox async mapper, scan matching off, `config/localization/slam_toolbox_survey.yaml`)
- Date: 2026-10-14 (header of `Spielberg.yaml`; a regeneration differs, the async mapper picks its own scans)
- GR-roboracer commit: not recorded in the yaml header (pre-D1 `config/scenarios/maps/Spielberg/slam/`)
