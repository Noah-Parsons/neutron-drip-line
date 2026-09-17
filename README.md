# Where Does Matter Stop Existing?

**A quantified study of nuclear mass models and the neutron drip line.**

## The question, simply

Take an atom and keep adding neutrons to its centre. For a while it holds on to
them. Then, at some point, one more neutron just falls straight back out. That
edge is called the **neutron drip line**. Past it, that version of the element
cannot exist.

Nobody has measured where that edge is for most elements. Scientists have
formulas that predict it, and the formulas disagree.

This project asks two things:

1. Where do the models say the edge is?
2. **How sure can anyone be?**

## What this project is, and is not

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
| 1 | Build the clean dataset, binding energy curve, separation energies | mostly done (cross-check against `rct1` left) |
| 2 | Fit the five-term formula, with its covariance matrix | to do |
| 3 | Leftovers (residuals) and a shell correction | to do |
| 4 | Garvey–Kelson relations | to do |
| 5 | Blind test: fit to AME2003, predict nuclei measured since | to do |
| 6 | Compare the published models on the same test | to do |
| 7 | The drip line as a probability band | to do |
| 8 | Write up | to do |

### Results so far

- AME2020 has 3,558 nuclei. **1,008 are estimates, not measurements**
  (marked `#`), and were removed. **2,550 measured nuclei remain.**
- Binding energies computed from mass excess match the AME's own values to
  within 0.0002 keV for every nucleus.
- The most tightly bound nucleus is **nickel-62** (8794.56 keV per nucleon),
  just ahead of iron-56 (8790.36 keV).
- Two-neutron separation energy can be computed for 2,301 nuclei; 9 of them
  are negative.

## How to run it

Open `drip_line.ipynb` in Jupyter with an R kernel and run all cells from the
top, in order.
