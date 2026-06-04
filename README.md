# Hardware-Aware Nussbaum-PID Controller on the Niryo NED3 Pro

Companion code repository for the manuscript:

> **Hardware-Aware Experimental Assessment of a Nussbaum-Function PID Controller on a Low-Cost Manipulator Joint Using Optuna-Guided Tuning**
> Danial Zafaranchizadeh Moghaddam, Abolfazl Zaraki — University of Hertfordshire, 2026.

This repo collects the **reproducibility material** that backs the claims of the paper:

- the publication figures used in the article (`figures/`),
- the publication tables (`tables/`),
- the Python scripts that regenerate every figure from raw closed-loop CSV logs (`scripts/`).

The manuscript text, LaTeX source, and the published PDF are **not** distributed here. The article, its DOI, and a direct PDF link are available from the project landing page:

**Project page:** <https://danielz.co.uk/projects/hardware-aware-nussbaum-pid/>

If you use the code, the figure-generation scripts, or the experimental methodology, please cite the manuscript above and link back to the project page.

---

## Repository layout

```
.
├── figures/    Publication figures (PDF / PNG / SVG, exact versions used in the paper)
├── tables/     Publication tables (selected metrics, parameter set, Optuna campaigns)
├── scripts/    Reproducible figure-generation Python scripts
│   ├── README.md
│   ├── build_main_results_figures.py
│   ├── build_envelope_figures.py
│   └── build_control_architecture_diagram.py
├── data/       Raw closed-loop CSV logs, per-run metrics (CSV+JSON),
│   │          Optuna trial archives, controller source code, run commands
│   ├── README.md
│   ├── best_results/{raw,metrics,plots}/
│   ├── optuna_trials/
│   ├── envelope_step_bandwidth/
│   ├── controller_code/
│   └── run_commands/
├── LICENSE
└── README.md   This file
```

---

## Scripts

All scripts are run from the project root and write into `figures/` and `tables/`.

| Script | Produces |
|--------|----------|
| `scripts/build_main_results_figures.py` | Headline-run tracking summary, baseline vs. enhanced comparison, critical-region zoom, cycle close-up, Optuna progress and trade-off dashboards, variant ablation, hardware platform figure, graphical abstract. |
| `scripts/build_envelope_figures.py` | Multi-amplitude / multi-frequency sinusoidal envelope figures (10°/0.05 Hz headline, 10°/0.5 Hz, 40°/0.05 Hz, 40°/0.5 Hz), real-hardware step responses (15° and 40°), and the bandwidth-limit probes (10°/1.5 Hz, 10°/3 Hz). |
| `scripts/build_control_architecture_diagram.py` | Reproducible matplotlib version of the hardware-aware Nussbaum-PID closed-loop block diagram. |

Dependencies:

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install numpy pandas matplotlib pymupdf pillow
python3 scripts/build_envelope_figures.py
python3 scripts/build_main_results_figures.py
python3 scripts/build_control_architecture_diagram.py
```

The raw closed-loop CSV logs, per-run metric tables (CSV + JSON), Optuna trial archives, controller source code, and run commands that the scripts consume are all released under `data/` (see `data/README.md`). The PDF / PNG / SVG figures already committed to `figures/` are the exact versions used in the published article and require no re-build.

---

## Hardware experiments

All real-hardware runs were executed on a **Niryo NED3 Pro** manipulator, driving **Dynamixel ID 6 (Niryo J5)** in raw current mode (Mode 0).

Validated envelope:

- Sinusoid: 10° and 40° amplitudes, 0.05 Hz and 0.5 Hz frequencies, locked-centre around 140°, 300 s validation.
- Step: 15° and 40° down-steps from the 140° operating centre.
- Bandwidth probes (out-of-envelope, characterized but not claimed as in-envelope tracking): 10°/1.5 Hz, 10°/3 Hz, 40°/1.0 Hz, 40°/1.5 Hz.

---

## License

The code and figure-generation scripts in this repository are released under the **MIT License** (see `LICENSE`). The publication figures themselves are © the authors; please cite the paper if you reuse them in your own work.

---

## Contact

- Danial Zafaranchizadeh Moghaddam — `danial.za@outlook.com`
- Abolfazl Zaraki — `a.zaraki@herts.ac.uk`

---

## Code access note

This public repository keeps the project page, file names, figures, tables, and README descriptions visible for manuscript context. The Python implementation bodies have been removed from the public copy.

For access to the implementation code, reviewer material, or collaboration details, please email:

- Danial Zafaranchizadeh Moghaddam — `danial.za@outlook.com`
- Abolfazl Zaraki — `a.zaraki@herts.ac.uk`

Please include your affiliation, intended use, and whether the request is for review, reproduction, or collaboration.
