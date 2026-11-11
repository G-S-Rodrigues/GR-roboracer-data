# gym-nominal-std-const-v1

<!-- limits:begin -->

| Limit | Value |
|---|---|
| limit set | gym-nominal-std-const-v1 |
| vehicle version | f1tenth-default-v1 |
| optimizer | tum_mincurv_iqp |
| v_max (m/s) | 3.0 |
| ax cap (m/s^2) | 2 |
| brake cap (m/s^2) | = ax (GGV) |
| ay, GGV at v=0 (m/s^2) | 10.289709 |
| mue used | n/a |
| width_opt (m) | 0.8 |
| safety_width (m) | 0.9000 |
| margin (m per side) | 0.3 |
| curvlim (1/m) | 1.281191572 |
| tyre set | n/a |
| vehicle file | `config/vehicles/f1tenth_default.yaml` sha256 `1a7be711f78a22811b46ed3367983dd977b2cf86ec06a0a2f7779aa462be7eed` |
| ggv.csv sha256 | `0ecbace704e9c30cfef04a08f6d43e8c99e4c85ad135ba0bd7b2497ed6d5c5c9` |
| ax_max_machines.csv sha256 | `0f17ea3c0efd599026ef7bebb1fd3325da39cf81689f8f7ad3bf473449b1bbd8` |

<!-- limits:end -->

## Provenance

Simulator: the f1tenth_gym_jax gym (headless). Source: `config/vehicles/f1tenth_default.yaml` (vehicle_parameter_version f1tenth-default-v1) with its GGV and ax_max_machines tables. Caps: v_max 3.0, ax 2.0 and steering 0.4 carry no provenance comment in the file; they are nominal, hand-chosen caps, not the gym's own limits. Grip: ay 10.289709 flat is the gym's mu*g from `ggv.csv:2-3`, a single mu (`const`); it is the gym's model value while the caps are nominal. Tier `std` = the standard 3.0 / 2.0 cap tier. Renamed from `f1tenth-default-v1` in D2 (2026-11-11); record regenerated in place, CSV byte-identical.
