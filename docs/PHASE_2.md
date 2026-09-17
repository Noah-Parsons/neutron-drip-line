# Phase 2: fitting the five-term formula

**Goal:** find the five constants of the 1935 mass formula from the measured
data, **with honest error bars**, including how the constants are tied to each
other.

**Status:** done.

---

## The formula, simply

The formula estimates the binding energy B of any nucleus from just Z and A. It
has five parts:

| term | story | effect |
|---|---|---|
| **volume**, a_V × A | every particle is held by its neighbours | adds binding |
| **surface**, a_S × A^(2/3) | particles on the outside have fewer neighbours | takes away |
| **Coulomb**, a_C × Z(Z−1)/A^(1/3) | protons push each other apart | takes away |
| **asymmetry**, a_A × (A−2Z)²/A | nuclei prefer equal protons and neutrons | takes away |
| **pairing**, ± a_P / √A | even numbers pair up nicely | adds or takes away |

The five letters a_V … a_P are unknown. Fitting finds them.

## Why the fit is easy

For each nucleus, the thing each constant is multiplied by (A, A^(2/3), …) can be
calculated **before** fitting. So the formula is just

> B = a_V·x₁ + a_S·x₂ + a_C·x₃ + a_A·x₄ + a_P·x₅

which is ordinary **linear regression** with five columns and no intercept. The
notebook builds the five columns (the **design matrix**), then solves it with a
few matrix steps. As a check, it also solves with R's built-in `lm()`. The two
agree to 0.0000002 keV.

**Which nuclei:** the 2,455 measured nuclei with A ≥ 20. The 95 lighter ones are
left out, because the "liquid drop" idea barely applies to a nucleus of a dozen
particles. (See [DECISIONS.md](DECISIONS.md).)

---

## Result 1: the constants

Uniform weighting (every nucleus counts equally), A ≥ 20:

| constant | value (MeV) | error bar (MeV) | published range (MeV) |
|---|---|---|---|
| a_V (volume) | 15.46 | ± 0.02 | 15.5 – 15.8 |
| a_S (surface) | 17.02 | ± 0.08 | 16.8 – 18.3 |
| a_C (Coulomb) | 0.699 | ± 0.002 | 0.70 – 0.72 |
| a_A (asymmetry) | 22.62 | ± 0.06 | 23.0 – 23.7 |
| a_P (pairing) | 12.2 | ± 0.9 | 11 – 12 |

**Typical miss (rms residual): 3.2 MeV.** That's the formula's accuracy.

Four of the five fall just outside the published ranges. Result 3 below shows
why that is not a mistake.

## Result 2: the constants are tangled together

The correlation matrix, where 1 means "always move together":

| | a_V | a_S | a_C | a_A | a_P |
|---|---|---|---|---|---|
| a_V | 1 | **0.99** | **0.98** | 0.90 | 0.04 |
| a_S | | 1 | 0.96 | 0.88 | 0.04 |
| a_C | | | 1 | 0.87 | 0.04 |
| a_A | | | | 1 | 0.03 |
| a_P | | | | | 1 |

Volume and surface are correlated at **0.99**. If the fit nudges a_V up, it nudges
a_S up almost exactly in step, because the two terms are fighting over the same
overall size of the nucleus.

**Why this matters:** in Phase 7, the drip line depends on combinations of these
constants. Treating them as independent would give error bars that are badly
wrong. That's why the whole covariance matrix is kept, not just the five error
bars.

(Pairing is nearly independent of the rest. It only cares whether numbers are
even or odd, which the other terms don't see.)

## Result 3: the weighting choice moves the constants by 12–16 error bars

This is the most important thing Phase 2 found.

There's no correct floor, so we tried four different weightings:

| weighting | χ²/dof | a_V | a_S | a_C | a_A | a_P |
|---|---|---|---|---|---|---|
| uniform | – | 15.46 | 17.02 | 0.699 | 22.62 | 12.17 |
| floor 1 keV | 1,781,000 | 15.84 | 18.26 | 0.726 | 23.02 | 10.58 |
| floor 10 keV | 65,270 | 15.81 | 18.13 | 0.721 | 23.39 | 11.62 |
| floor 100 keV | 875 | 15.64 | 17.58 | 0.710 | 23.04 | 11.85 |
| floor 1000 keV | 10.5 | 15.46 | 17.02 | 0.699 | 22.62 | 12.17 |

(The 1000 keV floor gives exactly the uniform answer. Every measured uncertainty
is below 1000 keV, the largest being 838, so every nucleus gets the same weight.)

**How far did the constants move, compared with their own error bars?**

| | a_V | a_S | a_C | a_A | a_P |
|---|---|---|---|---|---|
| biggest shift (MeV) | 0.38 | 1.24 | 0.027 | 0.76 | 1.58 |
| error bar (MeV) | 0.024 | 0.076 | 0.0017 | 0.059 | 0.91 |
| **shift ÷ error bar** | **15.6** | **16.4** | **16.2** | **12.9** | 1.7 |

The error bars say a_S is known to ±0.08 MeV. But just
changing *how you weight the nuclei*, a choice with no single right answer, moves
it by 1.24 MeV. **The error bars understate the real uncertainty by more than ten
times.**

This also explains why published values disagree: different authors made
different reasonable choices. With a 100 keV floor, all five constants land inside
the published ranges; with uniform weighting, four don't.

## Result 4: raw error bars are wildly too small

For weighted fits, the textbook formula C = (XᵀWX)⁻¹ assumes the formula misses
each nucleus only by its **measurement** error. But measurements are good to
about 6 keV (the median), while the formula misses by about 3,000 keV.

χ²/dof shows the mismatch. It should be about 1; it is 875 to 1.8 million. So
the raw error bars come out far too small:

| floor | raw error bar on a_S | corrected error bar on a_S |
|---|---|---|
| 1 keV | 0.00005 MeV | 0.063 MeV |
| 100 keV | 0.0026 MeV | 0.076 MeV |

The **corrected** error bars multiply C by χ²/dof, so the scatter the formula
really has is counted. Those are the ones reported. Even they are probably too
small: they assume the misses are random noise, and Result 5 shows they are not.
**Phase 5 (the blind test) will check whether they are honest.**

## Result 5: the cutoff matters too

Refitting with **all** nuclei, not just A ≥ 20, moves a_V, a_S, a_C and a_A by
about **9 error bars** each. Including the smallest nuclei raises the typical
miss from 3.2 to 3.7 MeV.

## Result 6: a first look at what the formula misses

Plotting the residuals (measured minus predicted) against neutron number
**does not** give a flat band of random scatter. It gives clear **spikes at N = 50,
82 and 126**, three of the magic numbers. Nuclei there are held together more
tightly than the formula knows. That's Phase 3.

The biggest misses of all are **very neutron-rich light nuclei**: boron-21
(+27 MeV), boron-20 (+25), carbon-22 (+20), nitrogen-23 (+15) and oxygen-26
(+14). The formula says they should be far **less** bound than they really are.
These nuclei sit **right at the drip line**. So the formula is at its worst
exactly where this project needs it most. Phase 3 has to find out whether a
correction fixes that or makes it worse.

---

## What to carry into later phases

1. **The fitted constants and the full covariance matrix** (uniform, A ≥ 20) are
   the starting model.
2. **Report every weighting variant, not just one.** The spread between them is
   a real part of the uncertainty (Result 3).
3. **The blind test must use choices fixed in advance.** See
   [DECISIONS.md](DECISIONS.md).
