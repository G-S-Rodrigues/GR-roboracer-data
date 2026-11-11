# gym-model-std-const-v1

<!-- limits:begin -->

| Limit | Value |
|---|---|
| limit set | gym-model-std-const-v1 |
| vehicle version | f1tenth-gym-limits-v1 |
| optimizer | tum_mintime |
| v_max (m/s) | 20.0 |
| ax cap (m/s^2) | 9.51 |
| brake cap (m/s^2) | = ax (GGV) |
| ay, GGV at v=0 (m/s^2) | 10.289709 |
| mue used | 1.027922 |
| width_opt (m) | 0.8 |
| safety_width (m) | 1.1100 |
| margin (m per side) | 0.4 |
| curvlim (1/m) | 1.348436777 |
| tyre set | gym_fit |
| vehicle file | `config/vehicles/f1tenth_gym_limits.yaml` sha256 `cbfcb3c1143612658e020a67fc70311bc8abe652ad930ace3612eae3b4aa3cd7` |
| ggv.csv sha256 | `06e4a7e780fb3676ccb39123ce21a3c04a610e6396c9714a533843a4d68daed0` |
| ax_max_machines.csv sha256 | `1cf5f7b61a56f439cde3cf503acc1939dff7b4f66841b015f533fb1b35f8da3e` |

<!-- limits:end -->

## Provenance

Simulator: the f1tenth_gym_jax gym (headless). Source: `config/vehicles/f1tenth_gym_limits.yaml` (vehicle_parameter_version f1tenth-gym-limits-v1), every cap pinned to `f1tenth_gym_jax Param` (SIMJAX-1120/1130): a_max 9.51, v_max 20.0 (owner ruling 2026-10-14), s_max 0.4189, sv_max 3.2. Caps: the simulator's own limits, so a raceline asks nothing the simulated car cannot do. Grip: ay = mu*g 10.289709 is a modelling bound (the gym's `st` tyres are linear, `const`), so a profile may be slower than the gym allows, never faster. Name `gym-model-std-const-v1` is owner ruling OD-3 (i) of 2026-11-11: `std` kept although the caps are the gym's own. Renamed from `f1tenth-gym-limits-v1` in D2 (2026-11-11); record regenerated in place, CSV byte-identical.
