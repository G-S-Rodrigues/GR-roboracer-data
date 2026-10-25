# GR-roboracer-data

Licence: GPL-3.0 (`LICENSE`); the Spielberg data derives from a GPL-3.0 work, see `NOTICE.md`.

Data for GR-roboracer and its TUM fork (`GR-roboracer-global_racetrajectory_optimization`), kept out
of both code repos and pinned by SHA as a submodule (`third_party/GR-roboracer-data`).

Layout (adjust only with a note here):

- `tracks/<Track>/maps/...` and `tracks/<Track>/racelines/<vehicle-version>/...`: the tracks, their
  SLAM maps and racelines. Not populated yet.
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
