# Porto survey grid, slam_toolbox, 0.05 m

Porto's grid for `pose_source:=amcl`, built by this stack in the AutoDRIVE sim (not upstream's). A survey: slam_toolbox lays `/scan` at the exact poses with scan matching off.

Picture: `Porto.png`.

- Simulator: AutoDRIVE (the competition sim image)
- Odometry: ground truth (`config/localization/slam_toolbox_survey_truth.yaml`)
- Resolution: 0.05 m per cell
- Accuracy vs ground truth: against the official `Porto.pgm` (`map_to_wall`, 2239 wall cells): median 0.0501 m, p95 0.1229 m, max 0.195 m; survey lap 14.08 s, 0 collisions, no stale-input latch
- Command: `scripts/autodrive_qualify.sh --domain 64 --case survey --sim container`
- Date: 2026-11-11
- GR-roboracer commit: `0c423b6` (branch `1v-fix-b`)
