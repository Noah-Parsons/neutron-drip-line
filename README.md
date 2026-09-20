# Where Does Matter Stop Existing?

**A quantified study of nuclear mass models and the neutron drip line.**

> **New here?** Start with [docs/START_HERE.md](docs/START_HERE.md). Every term
> is explained in [docs/GLOSSARY.md](docs/GLOSSARY.md), and every choice in
> [docs/DECISIONS.md](docs/DECISIONS.md).

## The question

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

The measured masses come from the **Atomic Mass Evaluation**, free from the IAEA:
<https://www-nds.iaea.org/amdc/>. The notebook downloads the files itself, so they
are not stored here. The **2020** edition supplies the measurements; the **2003**
edition supplies the blind test of Phase 5.

Cite: Huang et al., *Chinese Physics C* 45, 030002 (2021); Wang et al.,
*Chinese Physics C* 45, 030003 (2021). For AME2003: Audi, Wapstra and Thibault,
*Nuclear Physics A* 729, 337 (2003).

## Progress

| Phase | What | Status |
|---|---|---|
| 0 | Check the units: iron-56 comes out at ~8790 keV per nucleon | done |
| 1 | Build the clean dataset, binding energy curve, separation energies | **done**: [docs/PHASE_1.md](docs/PHASE_1.md) |
| 2 | Fit the five-term formula, with its covariance matrix | **done**: [docs/PHASE_2.md](docs/PHASE_2.md) |
| 3 | Leftovers (residuals) and a shell correction | **done**: [docs/PHASE_3.md](docs/PHASE_3.md) |
| 4 | Garvey–Kelson relations | **done**: [docs/PHASE_4.md](docs/PHASE_4.md) |
| 5 | Blind test: fit to AME2003, predict nuclei measured since | **done**: [docs/PHASE_5.md](docs/PHASE_5.md) |
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

**The Garvey–Kelson relations (Phase 4)**
- Of the six ways to arrange six nuclei in a 3×3 patch of the chart, exactly
  **two** cancel: the transverse and longitudinal relations. The other four are ten
  times worse, so a mistyped index would have been obvious. The published
  transverse form is reproduced to 2×10⁻¹⁰ keV.
- Where all six masses are measured, the median miss is **109–116 keV against
  2,564 keV for the six-term formula** — about twenty times better. The rms is five
  times the median, though: the tail is heavy, and below A = 20 the relations are
  barely better than the formula.
- **Predicting the hidden neutron-rich edge** (the Phase 3 hold-out): 0.58 MeV rms
  against 3.51 MeV for the six-term formula. At one step out, 0.90 against 4.02.
- **The cost of each step outward is measured:** rms ≈ 0.13 MeV × steps^1.37. The
  exponent is not 0.5, because chained errors are not independent — a prediction
  inherits its neighbours' mistakes.
- **They stop winning at about twelve chained steps**, where the six-term formula
  overtakes them. For most heavy elements the drip line is further out than that.
- 17 of 364 hidden nuclei **cannot be reached at all**. The global formula always
  returns something; the relations sometimes return nothing.
- Two obvious error bars on a chained prediction both fail: propagating the
  relation's scatter is exponentially too wide (96 % inside 1σ, 710 MeV by twenty
  steps), and the disagreement between routes is far too narrow (31 % inside twice
  the spread) because routes sharing a predicted neighbour inherit its error.

**The blind test (Phase 5)** — fit to AME2003, predict the 326 nuclei measured since
- **The formula is 1.65 times worse on nuclei it has not seen**: 2.98 MeV rms on the
  2,143 it was fitted to, 4.90 MeV on the 326 it was not. The median error is
  1.72 MeV, so the rms is carried by a tail. The mean error is **+1.29 MeV** — the
  new nuclei are systematically *more* bound than predicted.
- **Four of the five constants moved by more than five of their own 2003 standard
  errors** between the editions (volume 6.4σ, surface 6.9σ). Those error bars were
  already inflated by χ²/dof and are still far too small. This is the clearest answer
  the project has to "how sure can anyone be?".
- **The prediction band is right in the middle and wrong in the tail:** 64 % inside
  1σ against the 68 % it should hold, but only 83 % inside 2σ against 95 %. 17 % of
  the test nuclei miss by 6 to 30 MeV. The covariance matrix contributes 0.18 MeV of
  the 2.98 MeV band; the rest is the formula's own inadequacy.
- **The Garvey–Kelson relations, blind: 0.86 MeV rms and 0.30 MeV median**, against
  4.37 and 1.89 for the formula on the same nuclei — five times better, unbiased, and
  0.24 MeV against 4.67 for Z > 82. But they cannot reach 57 of the 326 at all.
- **Phase 4's uncertainty curve was optimistic by a steady factor of two.** Hiding the
  outer rim of a finished chart is easier than the real, ragged frontier of 2003.
  Doubling the curve makes it honest, so Phase 7 carries twice it.
- The worst twelve misses are all light and neutron-rich — boron-21 at 30 MeV — which
  is the one corner of the chart where the drip line has actually been reached.

## How to run it

Open `drip_line.ipynb` in Google Colab (Runtime → Change runtime type → R) or in
Jupyter with an R kernel, and run all cells from the top, in order. Full steps
are in [docs/START_HERE.md](docs/START_HERE.md).
