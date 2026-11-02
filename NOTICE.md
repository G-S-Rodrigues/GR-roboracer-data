# Notice

## Licence

This repository is distributed under the **GNU General Public License v3.0** (`LICENSE`). The
Spielberg track data below derives from a GPL-3.0 work, so the data that derives from it carries
that licence.

## Spielberg — provenance (carried over from GR-roboracer)

Everything under `tracks/Spielberg/` (maps, racelines) is covered by this section.

Derived from `f1tenth/f1tenth_racetracks` at
`866fe657f0bbe245f90a5042bc6eec0b0489d4c3` (`Spielberg/Spielberg_centerline.csv`,
`Spielberg/Spielberg_raceline.csv`), licensed **GPL-3.0**.

In GR-roboracer, `config/tracks/spielberg.yaml` is produced by `tools/import_f1tenth_racetrack.py`
from that revision. The files under `fixtures/tum-fork/spielberg-gym-0.40/` derive from that track:
`track.csv` is its TUM-format track, `seed/gym-0.4.csv` is a min-curv line optimised on it, and
`W1a/`, `S1c/` and `x0_seed.*` are solver inputs and outputs on it.

The same upstream revision is referenced, not copied, by GR-roboracer as the submodule
`third_party/f1tenth_racetracks`.

## Porto — provenance

`tracks/Porto/maps/Porto/` is the official AutoDRIVE map, copied byte for byte from
`AutoDRIVE-Ecosystem/AutoDRIVE-RoboRacer-Racetracks` at `cf3cf1e5d37489f4768c8041706e53977e4d6bc7`,
directory `Legacy Tracks/Porto Track/`, licensed **BSD-2-Clause**. This is a separate licence from the
repository's GPL-3.0; the upstream notice is kept here and in `tracks/Porto/maps/Porto/NOTICE.md`.

```
BSD 2-Clause License

Copyright (c) 2025, AutoDRIVE

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```
