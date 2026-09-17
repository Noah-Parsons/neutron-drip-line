# Where Does Matter Stop Existing?

**A quantified study of nuclear mass models and the neutron drip line.**

> **New here?** Start with [docs/START_HERE.md](docs/START_HERE.md). Every term
> is explained in [docs/GLOSSARY.md](docs/GLOSSARY.md), and every choice in
> [docs/DECISIONS.md](docs/DECISIONS.md).

## The question, simply

Take an atom and keep adding neutrons to its centre. For a while it holds on to
them. Then, at some point, one more neutron falls back out. That
edge is called the **neutron drip line**. Past it, that version of the element
cannot exist.

Nobody has measured where that edge is for most elements. Scientists have
formulas that predict it, and the formulas disagree.

This project asks two things:

1. Where do the models say the edge is?
2. **How sure can anyone be?**

## What this project is

The mass formula (1935), the Garvey–Kelson relations (1966), the published
models and the data all belong to other people. What this project adds is a
careful test of them: fitting with honest error bars, a blind test on nuclei
measured later, and a drip line given as a probability instead of a single line.

## Data

The measured masses come from the **Atomic Mass Evaluation 2020 (AME2020)**,
free from the IAEA: <https://www-nds.iaea.org/amdc/>. The notebook downloads the
files itself, so they are not stored here.

Cite: Huang et al., *Chinese Physics C* 45, 030002 (2021); Wang et al.,
*Chinese Physics C* 45, 030003 (2021).

## Progress

| Phase | What | Status |
|---|---|---|
| 0 | Check the units: iron-56 comes out at ~8790 keV per nucleon | done |
| 1 | Build the clean dataset, binding energy curve, separation energies | **done**: [docs/PHASE_1.md](docs/PHASE_1.md) |
| 2 | Fit the five-term formula, with its covariance matrix | **done**: [docs/PHASE_2.md](docs/PHASE_2.md) |
| 3 | Leftovers (residuals) and a shell correction | **done**: [docs/PHASE_3.md](docs/PHASE_3.md) |
| 4 | Garvey–Kelson relations | to do |
| 5 | Blind test: fit to AME2003, predict nuclei measured since | to do |
| 6 | Compare the published models on the same test | to do |
| 7 | The drip line as a probability band | to do |
| 8 | Write up | to do |

## Results so far

**The dataset (Phase 1)**
- AME2020 lists 3,558 nuclei. **1,008 are estimates, not measurements**
  (marked `#`), and were removed. **2,550 measured nuclei remain.**
- Binding energies agree with the AME's own values to 0.0001 keV for every
  nucleus.
- Our two-neutron separation energies (S2n) match the AME's published ones for
  **all 2,301 nuclei**, to within 0.001 keV. The same nuclei have values in both.
- The most tightly bound nucleus is **nickel-62** (8794.56 keV per nucleon),
  ahead of iron-58 and iron-56.
- 9 measured nuclei, all light (hydrogen to oxygen), have negative S2n: they
  are already past the drip line.

**The five-term formula (Phase 2)**, fitted to 2,455 nuclei with A ≥ 20:

| constant | MeV |
|---|---|
| volume a_V | 15.46 ± 0.02 |
| surface a_S | 17.02 ± 0.08 |
| Coulomb a_C | 0.699 ± 0.002 |
| asymmetry a_A | 22.62 ± 0.06 |
| pairing a_P | 12.2 ± 0.9 |

- Typical miss: **3.2 MeV**.
- **The error bars are not the whole story.** Changing only how nuclei are
  weighted moves the constants by **12–16 times their error bars**. Several
  equally reasonable choices give different answers, which is also why published
  values disagree.
- Volume and surface are correlated at 0.99, so the full covariance matrix is
  kept for later phases.
- The misses spike at the magic numbers 50, 82 and 126. They are biggest (up to
  27 MeV) for very neutron-rich light nuclei, **right at the drip line**.

**The shell correction (Phase 3)**
- Searching the misses for peaks finds the magic numbers **28, 50, 82 and 126**
  on its own, without being told where to look.
- A sixth term for shell structure (a_sh = −0.506 ± 0.013 MeV) cuts the typical
  miss from **3.24 to 2.56 MeV (21 %)**. It fixes the big shells (50, 82, 126)
  but makes the small ones (20, 28) worse.
- **Far from stability:** with each element's 4 most neutron-rich isotopes
  hidden, the six-term formula predicts them better at every step outward (rms
  4.41 → 3.51 MeV). Both formulas miss more the further out they go.
- The worst misses (boron-21, boron-20, carbon-22, up to 27 MeV) are right at the
  drip line, and the correction doesn't touch them.

## How to run it

Open `drip_line.ipynb` in Google Colab (Runtime → Change runtime type → R) or in
Jupyter with an R kernel, and run all cells from the top, in order. Full steps
are in [docs/START_HERE.md](docs/START_HERE.md).
