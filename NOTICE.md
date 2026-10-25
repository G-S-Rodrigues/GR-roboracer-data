# Notice

## Licence

This repository is distributed under the **GNU General Public License v3.0** (`LICENSE`). The
Spielberg track data below derives from a GPL-3.0 work, so the data that derives from it carries
that licence.

## Spielberg — provenance (carried over from GR-roboracer)

Derived from `f1tenth/f1tenth_racetracks` at
`866fe657f0bbe245f90a5042bc6eec0b0489d4c3` (`Spielberg/Spielberg_centerline.csv`,
`Spielberg/Spielberg_raceline.csv`), licensed **GPL-3.0**.

In GR-roboracer, `config/tracks/spielberg.yaml` is produced by `tools/import_f1tenth_racetrack.py`
from that revision. The files under `fixtures/tum-fork/spielberg-gym-0.40/` derive from that track:
`track.csv` is its TUM-format track, `seed/gym-0.4.csv` is a min-curv line optimised on it, and
`W1a/`, `S1c/` and `x0_seed.*` are solver inputs and outputs on it.

The same upstream revision is referenced, not copied, by GR-roboracer as the submodule
`third_party/f1tenth_racetracks`.
