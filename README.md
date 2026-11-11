# GR-roboracer-data

Licence: GPL-3.0 (`LICENSE`); the Spielberg data derives from a GPL-3.0 work, see `NOTICE.md`.

Data for GR-roboracer and its TUM fork (`GR-roboracer-global_racetrajectory_optimization`), kept out
of both code repos and pinned by SHA as a submodule (`third_party/GR-roboracer-data`).

Layout (adjust only with a note here):

- `tracks/<Map>/`: one folder per track. `<Map>` is the scenario's `environment.map` with its case kept
  (`Spielberg`, `Porto`); a scenario's `map_directory` is this `tracks/` folder (the gym and the launch find
  the ground truth as `<map_directory>/<Map>/<Map>.yaml`). A raceline record's `track:` field stays the
  lower-case track-file stem (`spielberg`); only the folder is keyed by the map name.
  - `<Map>.yaml` + `<Map>.png|.pgm`: the simulator's own map, the ground truth. `NOTICE.md`, `README.md`.
    Spielberg also has `<Map>_centerline.csv` and `<Map>_raceline.csv` (importer output).
  - `maps/<method>/`: maps this stack built of the track, one folder per method: `slam_toolbox/res_NNNN/`
    (NNNN is the cell size in millimetres: 0.050 m is `res_0050`), `mola/`, later `far_lio/`. Every map folder
    holds at least one PNG and a `README.md` (simulator, odometry, resolution, accuracy vs ground truth,
    command, date, GR-roboracer commit).
  - `racelines/<optimizer>/<limit set>/`: `raceline.csv`, `raceline.yaml` (the record), `limits.md` (the
    limits it was optimized under) and, for `tum_mintime`, `reference.csv`. No simulator name appears in a
    path above the limit-set folder.
- `fixtures/tum-fork/...`: inputs, goldens and solver states the fork's tests read.

## fixtures/tum-fork/spielberg-gym-0.40

Spielberg, the gym vehicle, margin 0.40, tyre B, scale 0.98, h (`stepsize_reg`) 0.5. All files were
produced in GR-roboracer's scratch harness `.scratch/part8b-harness/p8b-step1/` (GR-roboracer
`a61e5fa` checked out; the harness is not under git) and copied here byte for byte on 2026-10-24.

| File | Source run dir (under `p8b-step1/`) | What it is |
|---|---|---|
| `seed/gym-0.4.csv` | `mc_040/gym-0.4.csv` | the min-curv line (`s;x;y;psi;kappa;v;a_x`, open loop) the S1 seed is built from; produced by the part-8b `mc_040` min-curv chain, see `mc_040/result.json` |
| `track.csv` | `D/W1a-gym-from-defaultRB/track.csv` (identical to `SEED/S1c/track.csv`) | TUM track `x_m,y_m,w_tr_right_m,w_tr_left_m` |
| `inputs/racecar_f110.ini` | `D/W1a-gym-from-defaultRB/inputs/` (identical to S1c's) | the min-time ini (gym vehicle) |
| `inputs/veh_dyn_info/{ggv,ax_max_machines}.csv` | same | TUM vehicle tables (GR-roboracer `config/vehicles/f1tenth_gym_limits`) |
| `W1a/frame.npz`, `W1a/states.csv` | `D/W1a-gym-from-defaultRB/` | W1a: warm start from R-B at mu_init 1e-2; Optimal, 722 iterations, lap_est 32.32678506 s; frame (`r`, `nv`) and states (col 5 = n) for the closure test TUMFORK-1020 |
| `W1a/result.json`, `W1a/params.json` | same | the harness's record of W1a |
| `S1c/{w0,lam_x0,lam_g0}.csv` | `SEED/S1c/export/` | the converged seeded state: S1c = `P8B_SEED=1 P8B_SEED_MU=1e-3`, threads 3, `SEED/s.sh`'s `solve3.py` arguments; Optimal, 1715 iterations, lap_est 32.32678506 s. Its `states.csv` is byte-identical to W1a's |
| `S1c/result.json`, `S1c/params.json` | `SEED/S1c/` | the harness's record |
| `x0_seed.csv` | `STEP1/` (the fork's Step 1; dumped by the harness before the solve, `%.17g`, byte-identical over 3 runs) | the seeded initial guess `w0` (16301 values) the fork's `build_seed_x0` must reproduce (TUMFORK-1030) |
| `x0_seed.frame.txt` | same | its frame inputs: `N=679`, `h`, `Lc`, the seed path, `size` |

The exact S1c command was not recorded when it ran; the reconstruction above is the only route that
could have produced it (`SEED/run_tum_w.py`), and it is re-run by the fork's Step 1 before it is
relied on.

## sha256

```
ad88de3fdf751a16519af25569a01710571ce93b6e56f8a1b962bbdad1ecfb01  ./S1c/lam_g0.csv
22c8541b02969a2af777fcb0a5327db28c0b87042ca35cf38467ef929785376b  ./S1c/lam_x0.csv
1966499f336a9d0747c3daef4ede31c11b47eddb3f7b4e9d1b2737f74b2d5c17  ./S1c/params.json
88f5b02a4204e827e14426195c51e01e210b4fff63f9e34d0753f05ee30deb63  ./S1c/result.json
84068c8937a08fbe19bf4f0ae82119e1e7ef7d03d2cbcee4c73b222308e14a4a  ./S1c/w0.csv
10dafdb6d5b58d0679f80292669ce9917649de81d0c4447da8e95840d48a6a6d  ./W1a/frame.npz
1966499f336a9d0747c3daef4ede31c11b47eddb3f7b4e9d1b2737f74b2d5c17  ./W1a/params.json
50e9176f249dbfe0504541f2cf3aad3bb900fa667a53cb86968bd98028d3abb7  ./W1a/result.json
acb9c569b1ee71135ad524d5a16424ba48e10bea2ba8ca967e60f10a45152849  ./W1a/states.csv
748d7d531bd1e38f3a90bc5e1478972476c659b62d1dae161cebd93372314736  ./inputs/racecar_f110.ini
1cf5f7b61a56f439cde3cf503acc1939dff7b4f66841b015f533fb1b35f8da3e  ./inputs/veh_dyn_info/ax_max_machines.csv
06e4a7e780fb3676ccb39123ce21a3c04a610e6396c9714a533843a4d68daed0  ./inputs/veh_dyn_info/ggv.csv
8d19be0441dccfd969e1d898f2adb486efba237bd4a004282b7197d39811655b  ./seed/gym-0.4.csv
959ec8868937567f55fcc47495acacba216fb44f2fca23a3d83b3bdde7a8f8f0  ./track.csv
3713016346fe5ce7b326d40d253f81b0f73d25e05eba1cbc21635119ba062544  ./x0_seed.csv
7c8b58933b0cba11eac347d5df1103f347bf7710d3f1e90999dd7d4f029e6948  ./x0_seed.frame.txt
```

## Limit sets

A raceline folder is named for the limits it was optimized under:
`<sim>-<source>-<caps>-<grip>[-<qualifier>]-v<N>`.

| Part | Values | Meaning |
|---|---|---|
| `sim` | `gym`, `autodrive`, `car` | the vehicle model's world |
| `source` | `nominal`, `model`, `identified`, `tuned` | where the numbers come from: chosen by hand, the simulator's own parameters, measured, or tuned on track |
| `caps` | `std`, `fast`, `full`, ... | which speed and acceleration caps (`std` the 3.0 m/s / 2.0 m/s^2 tier, `fast` the 4.5 / 4.0 tier, `full` the simulator's unrestricted limits) |
| `grip` | `peak`, `sliding`, `const`, `pNN` | the lateral-acceleration basis: peak, sliding, a constant, or a percentile |
| `qualifier` | optional | e.g. `gymfit`, the tyre set |
| `vN` | `v1`, ... | a changed limit gets a new `vN`; a folder is never edited in place |

The name is matched to a vehicle file by the record's `vehicle_version` and `vehicle.path`
(`limits.md` says which); no vehicle file carries the name.

| Limit set | Vehicle file (GR-roboracer `config/vehicles/`) | `vehicle_version` |
|---|---|---|
| `gym-nominal-std-const-v1` | `f1tenth_default.yaml` | `f1tenth-default-v1` |
| `gym-model-std-const-v1` | `f1tenth_gym_limits.yaml` | `f1tenth-gym-limits-v1` |
| `autodrive-nominal-fast-const-gymfit-v1` | `autodrive_roboracer_fast.yaml` | `autodrive-roboracer-fast-v1` |

## tracks/

Path history: before GR-roboracer's D2 change the layout was `tracks/<Map>/maps/<Map>/` (ground truth, `slam/`,
`slam_0025/`, `slam_0020/`, `mola/`) and `tracks/<Map>/racelines/<vehicle-version>/<optimizer>.csv`; the
list below gives each moved file's current path. Before GR-roboracer's D1 change (see GR-roboracer ADR 0009),
`tracks/<Map>/maps/<Map>/` was `config/scenarios/maps/<Map>/` and `tracks/<Map>/racelines/` was
`config/racelines/<track>/`. Some map files still carry header comments that cite the old paths; they
are the command as run, and the records pin their SHA256, so they are left unedited.

Spielberg's regeneration root for `sim.track_importer` (see `tracks/Spielberg/NOTICE.md`)
is `tracks` (`--maps-root`): it rewrites `tracks/Spielberg/Spielberg.*` byte for byte.

sha256 of the moved files, byte for byte as they were in GR-roboracer `config/` (the raceline `.yaml`
records are excluded: they were regenerated with new path strings, and every raceline `.csv` below is
byte-identical to its predecessor):

```
199bdc2c972364ddd2aacdf2e483a1994c3db1828f80289791646775a1495f08  tracks/Porto/NOTICE.md
404a72551715fbf48ebcbd5b3b4093fcdf62934fb815898b144a017fe2c02efe  tracks/Porto/Porto.pgm
b78d687bae1758fdd62070b6da30c77a817bb102926630d973503035584d4d0d  tracks/Porto/Porto.yaml
5dc9485b45d91f023047b75129be840a0678f11bc15776e7dbf9ec92032565a1  tracks/Spielberg/NOTICE.md
c3e2a362ce5faa5180317a7d5812be4c7e3ae22bb5c8b0d3f688f99fb6081cbb  tracks/Spielberg/Spielberg.png
b0367d0b806d46fd58588213e50b726150772dfea1d4c43bf243b3691117bffc  tracks/Spielberg/Spielberg.yaml
5b1962efc479dc28f2960390ebf20cf753ba2bc60fcaf76f13b61bdd51311cda  tracks/Spielberg/Spielberg_centerline.csv
214ffcdb0d35acdeaeb1eea5d795a0913e158349cd364b674cd56bcf10637d60  tracks/Spielberg/Spielberg_raceline.csv
5b4ec525f900ddc715ffdd8671f1a53f3a95e53efb24459fce3c8f3e5b66414a  tracks/Spielberg/maps/mola/Spielberg.mm
e308eea70a24baa79c8f60844c5b5556c2b2c5c06e409ca33f88e35dd44402e0  tracks/Spielberg/maps/mola/Spielberg.yaml
c89d8afa6e4d06a3939000944fa3a6b73d6e6e142ef023fcd1ca49991190fbca  tracks/Spielberg/maps/mola/Spielberg_grid.png
250bdf4ae6dc5d138b5f88d1e62c8c22066115e76cc158dd127f675cb07ba0c6  tracks/Spielberg/maps/mola/Spielberg_grid.yaml
0344b011a2a0211b0e8c38ffc11d679b0dec437d6c6241019b1fcb70e0567145  tracks/Spielberg/maps/slam_toolbox/res_0050/Spielberg.png
be4cc60b62e68db90b029ff9172590e06fc57d7b62c67cc30ec9215031b40b5c  tracks/Spielberg/maps/slam_toolbox/res_0050/Spielberg.yaml
aa95588572749ad0556abe32e8a216f0694e4b27542020f50e7c3f1d84da2e7c  tracks/Spielberg/maps/slam_toolbox/res_0020/Spielberg.png
92b64cec807419d9b681289e56dc963a9d3d0f8ca7564fa9916dd4cfbebd3d67  tracks/Spielberg/maps/slam_toolbox/res_0020/Spielberg.yaml
b679f6600383014588e8d9ac8a6e99ee07cea3ea324dee51ed1feeb49af29f24  tracks/Spielberg/maps/slam_toolbox/res_0025/Spielberg.png
9897b12b28d9e3fbda4d475ec083bebd3997005f248872e9216148c27d9e58db  tracks/Spielberg/maps/slam_toolbox/res_0025/Spielberg.yaml
135faf4b08a7f6dcc475823d34b1572d09e669ade7108b5d68da7f8f5b8f195a  tracks/Spielberg/racelines/tum_mintime/gym-nominal-std-const-v1/reference.csv
e7bbdaaa7e4fe1ec60cbb9a8e3fb045899ab7402de69cc4f7a43c008958385ee  tracks/Spielberg/racelines/tum_mincurv_iqp/gym-nominal-std-const-v1/raceline.csv
22e9218a9749d6e499fe2a79b2786e52849158b940d0ff1b03d096ab47504e9e  tracks/Spielberg/racelines/tum_mintime/gym-nominal-std-const-v1/raceline.csv
8d19be0441dccfd969e1d898f2adb486efba237bd4a004282b7197d39811655b  tracks/Spielberg/racelines/tum_mintime/gym-model-std-const-v1/reference.csv
501ce6d327984de82f5ab6212dc97da4b554f5b91221733d11998218cad5e8c6  tracks/Spielberg/racelines/tum_mincurv_iqp/gym-model-std-const-v1/raceline.csv
e68d5ca3b08d35af103a42606fe176d64639e2dbce3794713994511f29286905  tracks/Spielberg/racelines/tum_mintime/gym-model-std-const-v1/raceline.csv
```

### tracks/Porto/maps/slam_toolbox/res_0050

Provenance, scores and commands: `tracks/Porto/maps/slam_toolbox/res_0050/README.md`. `tracks/Porto/NOTICE.md`
changed after the D1 move (it now names `slam/`), so its line in the list above records the moved bytes, not the current
ones. `sha256sum` from the repo root:

```
29818599cc8d1dff4c4a28340b35b956dc0643f1e823cbf6ef5d8ccf4282ac22  tracks/Porto/maps/slam_toolbox/res_0050/Porto.png
1abace1797b9fa54d760cc4a3f3e04b07156460a467ae006e0fae5434ef70d64  tracks/Porto/maps/slam_toolbox/res_0050/Porto.yaml
```

### tracks/Porto/maps/mola

Provenance, scores and commands: `tracks/Porto/maps/mola/README.md`. `sha256sum` from the repo root:

```
7adc2eebc1e8c7cac7f55a42a5f7e14d05d0aef8a5fa4f7fb009e4f60a3daaac  tracks/Porto/maps/mola/Porto.mm
e64564a05e46ce2c74606c319ebf860d96459a3160ca7eddb3a53b034c0b4524  tracks/Porto/maps/mola/Porto.yaml
45fa9436b73cfb0706f88ce44166e443b9d795233b0cd4641271ca8f75df8503  tracks/Porto/maps/mola/Porto_grid.png
bc428479c57fe5837af0f657ae067269f5e28e7ddedd21d24bf23c9bde862969  tracks/Porto/maps/mola/Porto_grid.yaml
```
