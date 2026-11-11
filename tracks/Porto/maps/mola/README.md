# Porto MOLA-LO map

MOLA-LO's map of Porto built by one mapping lap in the AutoDRIVE sim: `Porto.mm`, provenance `Porto.yaml`, grid `Porto_grid.{yaml,png}`. The provenance yaml is the generated file, unedited; its `command:` names the `.scratch-out` stem the run used.

Picture: `Porto_grid.png`.

- Simulator: AutoDRIVE (the competition sim image)
- Odometry: `/odom`, loop closure off, seed 42. Launch wheelspin makes `/odom` read about 1.8x the truth in the first second, and MOLA anchors on it
- Resolution: grid 0.05 m per cell
- Accuracy vs ground truth: against the official `Porto.pgm` (`map_to_wall`, 1712 wall cells), at the provenance `T_map_mola`: median 0.206 m, p95 0.696 m, max 0.825 m; after a best-fit alignment: median 0.045 m, p95 0.116 m, max 0.196 m (the difference is `T`: a 0.75 m / 1.19 deg launch-slip offset). One lap, 17.85 s, 0 collisions
- Command: `scripts/autodrive_qualify.sh --case mola_map --sim container`
- Date: 2026-11-11
- GR-roboracer commit: `3a084e0` (branch `1v-fix-b`)
