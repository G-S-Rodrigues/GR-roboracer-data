# Spielberg MOLA-LO map

MOLA-LO's own map (`Spielberg.mm`, the simplemap) from one mapping lap, its provenance (`Spielberg.yaml`: `T_map_mola`, hashes, versions) and the 2D grid derived from it (`Spielberg_grid.{yaml,png}`, 0.05 m).

Picture: `Spielberg_grid.png`.

- Simulator: f1tenth_gym_jax, `config/scenarios/spielberg_1080.yaml` (1080-beam lidar)
- Odometry: `/odom` (dead reckoning), loop closure off, seed 7
- Resolution: grid 0.05 m per cell
- Accuracy vs ground truth: not measured here; SIM-3530/SIM-5520 score it against the ground truth in GR-roboracer (`racing_evaluation.map_accuracy`, `map_to_wall`)
- Command: `./scripts/mola_map_track.sh config/scenarios/spielberg_1080.yaml <stem> 7` (the yaml's `command:` names the pre-D2 path)
- Date: not recorded in the yaml (committed to this repo 2026-11-02, moved from GR-roboracer `config/`)
- GR-roboracer commit: not recorded in the yaml
