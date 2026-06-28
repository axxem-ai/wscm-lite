# WSCM-Lite

**A Practitioner-Ready Implementation of the Weak Signal Cultivation Model**

WSCM-Lite is a lookup-table simplification of the full Weak Signal Cultivation Model (WSCM). It is designed for organizations that need to start tracking frontline risk signals immediately using nothing more than a spreadsheet — no exponential functions, no free parameters, no specialized software.

## WSCM vs. WSCM-Lite

The **full WSCM** is a 15-equation, 15-parameter mathematical framework for weak signal tracking published as a peer-reviewed arXiv paper:

> Codourey, M. & Gonzalez, E. A. (2026). The weak signal cultivation model: A human-centric framework for frontline risk detection, signal tracking, and proactive organizational resilience. *arXiv preprint* [arXiv:2604.01495](https://arxiv.org/abs/2604.01495).

The full WSCM includes consensus momentum, reversal amplifiers, continuous exponential recency weights, and other mechanisms designed for software-based deployment. It is the authoritative mathematical specification.

**WSCM-Lite** is a reduced-friction deployment tier that replaces the full model's exponential functions with a 4-row lookup table whose weights match the full WSCM's continuous recency and decay functions to within 0.01 per step. Because it drops the full model's momentum and reversal dynamics, WSCM-Lite is deliberately more conservative — escalating and de-escalating a session or two later rather than reproducing the full trajectory exactly. It trades second-order dynamics (momentum, reversal detection) for immediate usability in Excel or Google Sheets. Everything in this repository describes the WSCM-Lite mathematics only.

WSCM-Lite is documented in its own companion paper:

> Codourey, M. & Gonzalez, E. A. (2026). WSCM-Lite: A practitioner-ready implementation of the Weak Signal Cultivation Model. *arXiv preprint* [arXiv:2604.05381](https://arxiv.org/abs/2604.05381).

## What's in This Repository

| File | Description |
|------|-------------|
| `WSCM_Lite_Step_by_Step_Mathematics.pdf` | Complete WSCM-Lite mathematical specification in plain language. Seven steps, six constants, one lookup table. |
| `WSCM_Lite_Gas_Fumes_26_Sessions.pdf` | Detailed 26-session worked example tracing a gas fumes signal from initial detection through emergency response and near-retirement. Every session includes field observations, assessor scores, step-by-step calculations, and team decisions. |
| `WSCM_Lite_Simulator_v0.1.xlsx` | Excel simulator pre-loaded with the Gas Fumes example. Enter NRS scores and the model computes position, distance, SMS escalation, and Session Severity Index automatically. |

The companion paper ([arXiv:2604.05381](https://arxiv.org/abs/2604.05381)) provides the full derivation, validation against the parent WSCM, and sensitivity analysis.

## Quick Start

1. Open `WSCM_Lite_Simulator_v0.1.xlsx`
2. Go to the **Config** sheet and set your session cadence (Weekly, Biweekly, or Monthly)
3. Go to the **Signal Tracker** sheet and enter session data: Day, number of assessors, NRS scores (0–4), and occurrences
4. Computed columns auto-calculate: position (x', y'), distance (d), SMS status, SSI, and region
5. The **SSI Chart** sheet shows severity over time

For multiple signals, duplicate the Signal Tracker sheet.

## The WSCM-Lite Model in Brief

WSCM-Lite tracks risk signals on a 10×10 coordinate field divided into four regions:

- **Question Marks** (x<5, y<5) — emerging, unclear signals
- **Lit Fuses** (x≥5, y<5) — high intensity, low growth potential
- **Sleeping Cats** (x<5, y≥5) — low intensity, high growth potential
- **Owls** (x≥5, y≥5) — high on both axes, active management required

At each cultivation session, assessors score the signal on two 0–4 scales (Risk Intensity and Risk Growth Potential). The model updates the signal's position using recency-weighted averaging with committee scaling and passive y-decay. If the signal's distance from the origin exceeds 7.07, it is escalated to the formal Safety Management System.

Eight formulas. Six hardcoded constants. Zero free parameters.

For the full mathematical foundation — including consensus momentum, reversal amplifiers, and continuous recency weighting — refer to the [WSCM arXiv paper](https://arxiv.org/abs/2604.01495).

## License

This work is licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) (Creative Commons Attribution-NonCommercial 4.0 International).

You are free to share and adapt this material for non-commercial purposes with appropriate attribution. For commercial licensing inquiries, contact the authors.

Copyright © 2026 Maurice Codourey and Emmanuel A. Gonzalez.
