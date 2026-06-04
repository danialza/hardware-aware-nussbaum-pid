# Final Run Commands

These commands are written for the robot host, where the controller script is located at:

```text
/home/niryo/paper_ctrl_ws/src/ned_ros/niryo_robot_hardware_stack/niryo_robot_paper_controller/scripts/nussbaum_pid_mode0_direct_dxl.py
```

## Best 300 s Joint-6 Nussbaum Paper-Plus Run

This is the best validated 300 s configuration from the current work. The saved dataset in this package is:

```text
03_best_results/raw/nuss_break_c12a_300.csv
```

```bash
python3 /home/niryo/paper_ctrl_ws/src/ned_ros/niryo_robot_hardware_stack/niryo_robot_paper_controller/scripts/nussbaum_pid_mode0_direct_dxl.py \
  --device /dev/ttyAMA0 \
  --baudrate 1000000 \
  --dxl-id 6 \
  --duration 300 \
  --csv /tmp/nuss_break_c12a_300.csv \
  --rate 24 \
  --amplitude-deg 10.0 \
  --frequency-hz 0.05 \
  --reference-shape sine \
  --sine-center-mode lock \
  --soft-start-sec 6.0 \
  --gamma-link 1.1824623105 \
  --k-delta 0.1336345470 \
  --zeta0 0.8856929670 \
  --zeta-leak 0.0237735451 \
  --zeta-soft 0.9891853160 \
  --tail-kd 0.0606430796 \
  --tail-err-thresh-deg 1.5 \
  --tail-err-full-deg 4.0 \
  --fric-coulomb 0.0089323247 \
  --fric-vel-scale 1.2725305725 \
  --alpha 7.1072835468 \
  --gamma-adapt 8.7187500403 \
  --sigma-mod 0.2460708825 \
  --rbf-nodes 11 \
  --rbf-width 1.4631904539 \
  --rbf-center-min -3.2 \
  --rbf-center-max 3.2 \
  --max-control 0.0632 \
  --control-output-scale 1.0 \
  --torque-to-current 210 \
  --current-bias-raw -0.1296542137 \
  --command-sign -1 \
  --max-current-raw 39 \
  --max-current-slew 10.1211443054 \
  --current-limit-raw 0 \
  --predict-horizon-sec 0.0056165844 \
  --qd-lpf-alpha 0.1383932134 \
  --max-abs-e-dot 1.0 \
  --integral-limit 1.6504936083 \
  --q-abs-guard-deg 35 \
  --start-center-deg 140 \
  --start-center-wait-sec 3.0 \
  --start-center-tol-deg 1.0 \
  --start-center-hold-sec 0.2 \
  --start-center-max-travel-deg 80 \
  --default-mode 3 \
  --no-restore-mode
```

## Paper-Pure vs Paper-Plus Reproducibility Script

The script copied into this package is:

```text
05_all_nussbaum_outputs/nussbaum_pub_20260409/run_best_joint6_pure_plus.sh
```

It runs the original zeta law and the zeta-leak paper-plus version for direct comparison.

## Previous CNNPID Step-Disturbance Reference

This is not the final Nussbaum controller. It is included as the prior article/controller reference because it was used to compare engineering patterns and real-motor safety structure.

```bash
python3 /home/niryo/paper_ctrl_ws/src/ned_ros/niryo_robot_hardware_stack/niryo_robot_paper_controller/scripts/paper_cnnpid_mode0_direct_dxl_step_disturb.py \
  --device /dev/ttyAMA0 \
  --baudrate 1000000 \
  --dxl-id 6 \
  --duration 34 \
  --csv /tmp/step_seq_pm40_bestscore_with_zero.csv \
  --rate 40 \
  --amplitude-deg 10 \
  --frequency-hz 0.51675 \
  --reference-shape sine \
  --sine-center-mode lock \
  --precenter-before-trial \
  --precenter-target-deg 140 \
  --precenter-wait-sec 3.0 \
  --precenter-tol-deg 1.0 \
  --precenter-max-travel-deg 180 \
  --abort-on-precenter-fail \
  --soft-start-sec 0.0 \
  --kappa0 2.5639459954 \
  --kd 0.0364554730 \
  --alpha 0.015 \
  --gamma 4.8 \
  --sigma-leakage 0.03 \
  --sigma 10 \
  --rbf-width 6.0 \
  --rbf-center-min -2.5 \
  --rbf-center-max 2.5 \
  --kb 0.08 \
  --constraint-c 3.0 \
  --max-torque-nm 0.1473755225 \
  --tau-output-scale 1.0 \
  --tau-vff-gain 0.0 \
  --torque-to-current 210 \
  --current-bias-raw -1.0715708803 \
  --command-sign 1 \
  --max-current-raw 40 \
  --current-limit-raw 0 \
  --predict-horizon-sec 0.0 \
  --qd-lpf-alpha 0.06 \
  --max-abs-e-dot 3.0 \
  --integral-limit 0.4021932031 \
  --blf-guard-ratio 0.95 \
  --blf-epsilon 0.02 \
  --q-abs-guard-deg 75 \
  --default-mode 3 \
  --no-restore-mode \
  --step-start-sec 0.5 \
  --step-shape step \
  --step-sequence-deg "40,0,-40,0,40,0,-40,0" \
  --step-segment-sec 4 \
  --disturbance-placement mid_move \
  --mid-disturbance-offset-sec 0
```
