# Data: raw closed-loop logs, metrics, Optuna trials, controller code

Reproducibility data backing every figure, table, and Appendix item of the manuscript.

## Layout

```
data/
├── best_results/                     Headline 10°/0.05 Hz / 300 s campaign
│   ├── raw/                          Closed-loop CSV logs (one row per control sample)
│   ├── metrics/                      Per-run metric tables (CSV + JSON) and the cross-run summary
│   └── plots/                        Source SVGs preserved for the appendix figures
├── optuna_trials/                    Headline Optuna campaigns (79-trial archive + sub-passes)
├── envelope_step_bandwidth/          Multi-envelope, step, and bandwidth-probe runs
├── run_commands/                     Verbatim shell commands used for the final runs
└── controller_code/                  Controller-code file names; Python bodies are not public
```

## Headline run (Table 4, Figure for 10°/0.05 Hz)

- `best_results/raw/nuss_break_c12a_300.csv` — 300 s headline `break-c12a-300`
- `best_results/metrics/break-c12a-300_metrics.{csv,json}`
- `best_results/raw/nussbaum_compare_pure_300.csv` — direct baseline reference
- `best_results/metrics/paper-pure_metrics.{csv,json}`
- `best_results/metrics/metrics_comparison_summary.csv` — all variants together

## Failed / intermediate archive (Table A1)

- `best_results/metrics/paper-pure_metrics.*` + `best_results/plots/paper-pure_overview.svg`
- `best_results/metrics/bestnow-fric-slewboost-300_metrics.*`
- `best_results/metrics/stage1-best300_metrics.*`
- `best_results/metrics/tryc-slew16-300_metrics.*`
- `best_results/metrics/tryd-robust-300_metrics.*`
- additional intermediate runs (`fric-t1-300`, `rebaseline-300`, `trya/tryb`, `plus-baseline`, `plus-tuned`) released for completeness.

## Optuna campaigns (Table 6)

Headline 79-trial archive and supporting sub-passes:

- `optuna_trials/nussbaum_plus_optuna_20260409_{trials.csv, best.json, summary.md}`
- `optuna_trials/nuss_optuna_break_baseline_{trials.csv, best.json}`
- `optuna_trials/nussbaum_optuna_fric_p95_{trials.csv, summary.json}`
- `optuna_trials/nussbaum_optuna_tailp95_{trials.csv, best.json}`
- `optuna_trials/nussbaum_optuna_tailp95_v2_{trials.csv, best.json}`

## Multi-envelope, step, bandwidth-limit (Section 4.3, 4.4, Appendix A.2)

- `envelope_step_bandwidth/nussbaum_sine_05hz_amp10_optuna_v2_trial13_full.csv` — 10°/0.5 Hz
- `envelope_step_bandwidth/nussbaum_sine_005hz_amp40_stability_test1_300s.csv` — 40°/0.05 Hz 300 s
- `envelope_step_bandwidth/nussbaum_sine_05hz_amp40_optuna_v2_trial25_full.csv` — 40°/0.5 Hz short-run
- `envelope_step_bandwidth/nussbaum_step15_tailclean_best_single.csv` — 15° step
- `envelope_step_bandwidth/nussbaum_step40_best_single.csv` — 40° step (source: `*_source_for_step40.csv`)
- `envelope_step_bandwidth/nussbaum_step_settle120_trials.csv` — step Optuna trials
- `envelope_step_bandwidth/nussbaum_sine_15hz_amp10_optuna_v5_{trial0_full.csv, trials.csv}` — 10°/1.5 Hz bandwidth probe
- `envelope_step_bandwidth/nussbaum_sine_3hz_{sanity.csv, struct_*.csv, hard_*.csv, refine_trials.csv}` — 10°/3 Hz bandwidth probe + supporting passes
- `envelope_step_bandwidth/PRIORITY_EVIDENCE_MANIFEST.csv` + `priority_metrics_check.csv` — provenance and metric checks

## Controller code

The following controller-code files are listed for manuscript context. Their Python implementation bodies are not included in the public copy. For full code access, please email Danial Zafaranchizadeh Moghaddam or Abolfazl Zaraki.

- `controller_code/nussbaum_pid_mode0_direct_dxl.py` — direct-Dynamixel real-time runner used for every reported real-hardware trial.
- `controller_code/nussbaum_direct_autotune_optuna.py` — wrapping Optuna driver that produced the archive in `optuna_trials/`.
- `controller_code/paper_cnnpid_mode0_direct_dxl_step_disturb.py` — step + disturbance variant of the runner.
- `controller_code/paper_formulas_nussbaum_pid.py` — standalone implementation of the source-paper equations used for cross-checks.

## Run commands

- `run_commands/final_run_commands.md` — verbatim shell commands used to capture the final closed-loop logs above.

## CSV schema

All raw closed-loop CSVs share the same columns:

```
t, q_ref_rad, q_meas_rad, qd_ref_rad_s, qd_meas_rad_s,
e_rad, e_dot_rad_s, e_int, psi, psi_dot,
kappa_delta, nussbaum_n, zeta, zeta_dot,
u_cmd, u_aux, u_robust, u_fric, tail_activation, max_control_eff,
current_from_u_raw, goal_current_raw, slew_boost,
max_current_slew_eff_raw_s, present_current_raw, psi_hat_norm
```

(Step CSVs append `q_ref_base_rad, qdd_ref_rad_s2, disturb_*` columns.)

## License

See top-level `LICENSE` (MIT for code/data; figures © authors).

---

## Full code access

This public repository keeps the data layout, file names, and README descriptions visible for manuscript context. Python implementation bodies are not included in the public copy.

For full code access, reviewer material, or collaboration details, please email:

- Danial Zafaranchizadeh Moghaddam — `danial.za@outlook.com`
- Abolfazl Zaraki — `a.zaraki@herts.ac.uk`

Please include your affiliation, intended use, and whether the request is for review, reproduction, or collaboration.
