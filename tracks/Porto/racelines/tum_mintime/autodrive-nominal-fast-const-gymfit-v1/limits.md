# autodrive-nominal-fast-const-gymfit-v1

<!-- limits:begin -->

| Limit | Value |
|---|---|
| limit set | autodrive-nominal-fast-const-gymfit-v1 |
| vehicle version | autodrive-roboracer-fast-v1 |
| optimizer | tum_mintime |
| v_max (m/s) | 4.5 |
| ax cap (m/s^2) | 4 |
| brake cap (m/s^2) | = ax (GGV) |
| ay, GGV at v=0 (m/s^2) | 9.810000 |
| mue used | 0.98 |
| width_opt (m) | 0.8 |
| safety_width (m) | 1.0700 |
| margin (m per side) | 0.4 |
| curvlim (1/m) | 1.781950314 |
| tyre set | gym_fit |
| vehicle file | `config/vehicles/autodrive_roboracer_fast.yaml` sha256 `04af38e0515fb8d06ee2611e5594d0c18cb1addce34d8f65613bded3f6157c05` |
| ggv.csv sha256 | `51783356985fd5f5643343be4723abb63d4c22c1c225c3d61190867110484260` |
| ax_max_machines.csv sha256 | `782dd9010ec88600d42342507717858e5c67a27a36f1afbd840b066e108138fd` |

<!-- limits:end -->

## Provenance

Simulator: AutoDRIVE (roboracer), Porto. Source: `config/vehicles/autodrive_roboracer_fast.yaml` (vehicle_parameter_version autodrive-roboracer-fast-v1; sha256 04af38e0... after ruling #33), geometry from the competition sim image (wheelbase 0.324). Caps: speed 4.5 and acceleration 4.0, owner ruling 2026-11-08 (file lines 14-16) for the fast min-time lap; top speed is not measured on Porto. Grip: ay 9.81 is prefab mu 1.0, not measured (`ggv.csv:2-6`), so `const`; tyre set gym_fit (byte-identical to the gym's). The 200 ms stale-timeout edit (A7-Q4) is not an optimizer input, so the set stays -v1. Renamed from `autodrive-roboracer-fast-v1` in D2 (2026-11-11); record regenerated in place, CSV byte-identical.
