# Figure-generation scripts

Reproducible scripts that build every figure in the manuscript.
Run any script from the project root, e.g.

```bash
python3 scripts/build_envelope_figures.py
python3 scripts/build_control_architecture_diagram.py
```

| Script | Produces |
|--------|----------|
| `build_main_results_figures.py` | Headline results, baseline-vs-enhanced, critical zoom, cycle close-up, Optuna progress/trade-off dashboards, variant ablation, hardware photos, graphical abstract. Reads from the upstream Optuna archive bundle referenced by `PKG`. |
| `build_envelope_figures.py` | Multi-amplitude / multi-frequency sinusoidal envelope (10°/0.05 Hz headline, 10°/0.5 Hz, 40°/0.05 Hz, 40°/0.5 Hz), step responses (15° and 40°), and bandwidth-limit probes (10°/1.5 Hz, 10°/3 Hz). |
| `build_control_architecture_diagram.py` | Matplotlib reference build of the hardware-aware Nussbaum-PID closed-loop block diagram. The submission uses an externally produced version of the same diagram (`figures/fig_block_diagram.pdf`); this script is preserved as a reproducible fall-back. |

All scripts write to `../figures/` and `../tables/` of the project root.

---

## Code access note

This public repository keeps the script names and README descriptions visible for manuscript context. The Python implementation bodies have been removed from the public copy.

For access to the implementation code, reviewer material, or collaboration details, please email:

- Danial Zafaranchizadeh Moghaddam — `danial.za@outlook.com`
- Abolfazl Zaraki — `a.zaraki@herts.ac.uk`

Please include your affiliation, intended use, and whether the request is for review, reproduction, or collaboration.
