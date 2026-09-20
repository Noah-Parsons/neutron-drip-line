# Phase 5: the blind test

**Goal:** fit only to what was known in 2003, predict the nuclei measured since, and
find out how much of the accuracy reported in Phases 2–4 survives contact with data
the models never saw.

**Status:** done.

This is the phase the manual calls the central methodological move. The rules were
fixed in Phase 2, as D8, long before it was run: nothing from after the cutoff may
touch the fit, every weighting variant is reported rather than whichever predicts
best, and no choice may be revised after seeing a test result. D17–D20 add the
detail, written down after the two sets were counted and before any prediction was
made.

---

## The sets

`mass.mas03` from the AMDC, parsed on its own declared format — N, Z and A in the
same columns as AME2020, but the mass excess two columns narrower (D17). Binding
energies use AME2003's own Δ(¹H) and Δ(n), so that not even a mass excess constant
comes from after the cutoff. B/A matches the 2003 file's own column to 0.0005 keV
over all 2,228 measured nuclei. Iron-56 comes out at 8790.32 keV, against 8790.34 in
AME2020; the two editions really do differ by 0.02 keV there.

| | nuclei |
|---|---|
| measured in AME2020 | 2,550 |
| also measured in AME2003 | 2,214 |
| estimated in AME2003 | 301 |
| absent from AME2003 altogether | 35 |
| **fit set** (AME2003 measured, A ≥ 20) | **2,143** |
| **test set** (first measured after 2003, A ≥ 20) | **326** |

Fourteen nuclei went the other way: measured in 2003, and AME2020 no longer calls
them measured. Most carried 2003 uncertainties of 700–1,800 keV. They stay in the fit
set, because somebody fitting in 2003 would have used them; refitting without them
moves no constant by more than 0.081 MeV and changes the test rms from 4.90 to
4.96 MeV.

### Seventeen years of progress is not all outward

| direction | nuclei |
|---|---|
| neutron-rich extension | 182 |
| proton-rich extension | 81 |
| gap fill (inside the 2003 range) | 51 |
| new element (nothing measured in 2003) | 12 |

Only the 182 test extrapolation toward the drip line. They sit 1 to 7 neutrons past
the 2003 edge, and 173 of them within 4.

## Result 1: the formula is 1.65 times worse on nuclei it has not seen

| formula | weighting | fit rms | test rms | test median | neutron-rich | gap fill |
|---|---|---|---|---|---|---|
| five | uniform | 2.98 | **4.90** | 1.72 | 5.96 | 3.49 |
| five | floor 1000 keV | 2.98 | 4.92 | 1.72 | 5.99 | 3.49 |
| five | floor 100 keV | 3.00 | 5.26 | 1.80 | 6.42 | 3.59 |
| five | floor 10 keV | 3.14 | 5.90 | 2.28 | 7.15 | 3.93 |
| five | floor 1 keV | 3.27 | 5.97 | 2.98 | 6.91 | 4.54 |
| six | uniform | 2.16 | 4.70 | 2.59 | 5.73 | 2.93 |
| six | floor 1000 keV | 2.16 | 4.72 | 2.61 | 5.76 | 2.94 |
| six | floor 100 keV | 2.19 | 5.07 | 2.77 | 6.18 | 3.11 |
| six | floor 10 keV | 2.37 | 5.70 | 3.17 | 6.95 | 3.45 |
| six | floor 1 keV | 2.40 | 5.69 | 3.11 | 6.97 | 3.43 |

(rms error in MeV.) **Every six-term number here is not blind** and is labelled so
(D19): the shell term's shape was chosen by looking at AME2020 residuals, which
include these test nuclei. Only its constant was refitted on 2003 data. It is
reported alongside, not as a result.

Reporting a fit residual as though it were a prediction error would have understated
the error by a factor of 1.65. Two details matter more than the ratio:

- **The median error is 1.72 MeV**, well under half the rms. The rms is carried by a
  tail, not by typical behaviour.
- **The mean error is +1.29 MeV**, not zero. The nuclei found since 2003 are
  systematically *more* bound than the 2003 fit predicted. A formula that were merely
  imprecise would miss in both directions equally.

The weighting order is the same as in Phase 2 — uniform and the 1,000 keV floor best,
the 1 keV floor worst — which is at least consistent with D6 having been right for the
right reason.

## Result 2: the constants did not stay inside their error bars

| | a_V | a_S | a_C | a_A | a_P |
|---|---|---|---|---|---|
| AME2003 fit (MeV) | 15.626 | 17.566 | 0.708 | 22.958 | 12.605 |
| its standard error | 0.025 | 0.079 | 0.002 | 0.063 | 0.894 |
| AME2020 fit (MeV) | 15.463 | 17.017 | 0.699 | 22.624 | 12.165 |
| **shift, in 2003 standard errors** | **−6.4** | **−6.9** | **−5.6** | **−5.3** | −0.5 |

**Four of the five moved by more than five of their own standard errors.** Those error
bars had already been inflated by χ²/dof — a correction of a factor of hundreds — and
they are still far too small to cover what seventeen years of data actually changed.
D7 flagged this as its own suspected weakness. It was right.

This is the strongest single result in the project so far, and it answers the
project's question directly. A published constant of the mass formula, quoted with a
least-squares error bar, does not mean what it appears to mean.

## Result 3: the band on a prediction is right in the middle and wrong in the tail

The band declared in D20 is the constants' covariance carried through the design row,
plus the fit's own scatter.

| | mean band | rms error | inside 1σ | inside 2σ |
|---|---|---|---|---|
| five terms, uniform | 2.98 | 4.90 | **64 %** | **83 %** |
| six terms, uniform (not blind) | 2.16 | 4.70 | 41 % | 76 % |

A 1σ band should hold about 68 %, a 2σ band about 95 %. The five-term band gets the
middle of the distribution almost exactly right and **badly misses the tail**: 17 %
of the test nuclei — 57 of 326 — fall outside two standard deviations, missing by 6 to
30 MeV. Those are not unlucky draws from the quoted band. They are nuclei the formula
does not describe at all.

Two things follow.

**The covariance matrix is nearly irrelevant to predicting a mass.** It contributes
0.18 MeV of that 2.98 MeV band; the rest is the fit's own scatter. The careful
covariance work of Phase 2 matters for quoting the constants and for nothing else
here.

**The spread across weightings is not an error bar.** Its median is 2.28 MeV, wider
than the median error, and it still covers only 36 % of the errors — because the five
weightings mostly disagree in the same direction at once rather than bracketing the
truth.

## Result 4: where the errors are

Neutron-rich extensions, by distance past the 2003 edge:

| steps out | nuclei | five terms | six terms | mean signed, five |
|---|---|---|---|---|
| 1 | 66 | 5.30 | 4.78 | +1.93 |
| 2 | 50 | 5.83 | 5.49 | +1.59 |
| 3 | 36 | 6.36 | 6.33 | +1.59 |
| 4 | 21 | 7.88 | 7.95 | +0.64 |
| 5 | 6 | 2.91 | 3.72 | −0.92 |
| 6 | 2 | 4.84 | 5.31 | −3.67 |
| 7 | 1 | 7.03 | 6.94 | −7.03 |

(rms in MeV.) The error climbs from 5.3 to 7.9 MeV over the first four steps, which
covers 173 of the 182. The last three rows are 6, 2 and 1 nuclei and carry no weight.
The signed error tells a second story: it starts at +1.9 MeV and falls through zero,
so close to the edge the formula under-binds and further out it over-binds.

By region and direction, five terms, uniform (rms, MeV):

| region | neutron-rich | proton-rich | gap fill | new element |
|---|---|---|---|---|
| Z ≤ 20 | **13.79** (21) | 1.54 (1) | — | — |
| Z 21–50 | 3.78 (69) | 3.18 (36) | 5.59 (13) | — |
| Z 51–82 | 2.58 (58) | 4.65 (15) | 2.37 (23) | — |
| Z > 82 | 5.68 (34) | 1.42 (29) | 2.37 (15) | 0.56 (12) |

The light neutron-rich corner is where it collapses, and that is precisely where the
drip line has actually been reached experimentally.

## Result 5: the Garvey–Kelson relations, blind

Chained outward from everything AME2003 had measured, and asked about the same 326
nuclei.

| | reached | rms | median | mean |
|---|---|---|---|---|
| Garvey–Kelson chains | 269 of 326 | **0.86** | **0.30** | −0.02 |
| five-term formula, same 269 | 269 | 4.37 | 1.89 | — |

(MeV.) **Better by a factor of five in the rms and six in the median**, with a mean
error of −0.02 MeV, so no systematic drift outward. By region the gap is widest where
the formula is worst:

| region | relations | formula | nuclei |
|---|---|---|---|
| Z ≤ 20 | 1.96 | 9.72 | 19 |
| Z 21–50 | 1.00 | 3.80 | 111 |
| Z 51–82 | 0.36 | 2.56 | 85 |
| Z > 82 | **0.24** | 4.67 | 54 |

And by direction:

| direction | nuclei | relations, median | relations, rms | formula, rms |
|---|---|---|---|---|
| gap fill | 42 | 0.10 | 0.31 | 3.79 |
| neutron-rich extension | 166 | 0.32 | 0.86 | 4.98 |
| proton-rich extension | 61 | 0.40 | 1.08 | 2.60 |

The cost is coverage: **57 of the 326 cannot be reached at all**, including all
twelve new-element nuclei, 20 proton-rich extensions, 16 neutron-rich extensions and
9 gap fills. A chain needs five measured neighbours to start from, and the formula
will always return something.

## Result 6: Phase 4's calibration was optimistic by a factor of two

Phase 4 measured the cost of each chained step on hold-outs cut from AME2020. This is
the first time that curve meets data it was not built from.

| chained steps | nuclei | rms here | Phase 4 hold-out | optimistic by | power law |
|---|---|---|---|---|---|
| 1 | 118 | 0.60 | 0.27 | **2.2** | 0.13 |
| 2 | 70 | 0.91 | 0.39 | **2.3** | 0.34 |
| 3 | 39 | 1.23 | 0.57 | **2.2** | 0.59 |
| 4 | 25 | 1.11 | 0.69 | 1.6 | 0.88 |
| 5 | 12 | 0.76 | 0.75 | 1.0 | 1.19 |

(MeV. Rounds 6 and 7 hold 4 nuclei and 1.) **A steady factor of about two over the
first three rounds**, which is where 84 % of these nuclei sit.

This is a result about hold-out testing in general, not about these relations. Cutting
the outer rim off a finished chart leaves a tidy, fully-surrounded edge to predict.
The real 2003 frontier was ragged, full of gaps, and least precisely measured exactly
where the chains had to start. A hold-out drawn from complete data flattered the
method by a factor of two.

Used as a 1σ band, the Phase 4 curve holds 51 % rather than 68 %. **Doubling it gives
68 %.** So Phase 7 carries twice the Phase 4 curve — a correction this phase earned
rather than assumed.

## Result 7: the worst misses, and what the relations do with them

| nuclide | direction | formula | relations | rounds |
|---|---|---|---|---|
| B-21 | neutron-rich | 30.2 | unreachable | — |
| B-20 | neutron-rich | 27.8 | unreachable | — |
| C-22 | neutron-rich | 22.7 | unreachable | — |
| N-23 | neutron-rich | 17.4 | **−0.87** | 1 |
| O-26 | neutron-rich | 16.0 | **−0.39** | 2 |
| O-25 | neutron-rich | 15.7 | **−0.57** | 1 |
| Sn-101 | gap fill | 12.0 | **−0.42** | 1 |
| F-29 | neutron-rich | 11.9 | 1.19 | 2 |
| F-28 | neutron-rich | 11.2 | 1.03 | 1 |
| Mg-37 | neutron-rich | 10.8 | **−0.06** | 3 |
| Na-34 | neutron-rich | 10.7 | −1.73 | 2 |
| Sn-135 | neutron-rich | 10.6 | 0.19 | 2 |

(error in MeV.) Every one of the worst twelve is in the light neutron-rich corner.
Where the relations reach at all they are wrong by under a MeV on nuclei the formula
misses by fifteen. The three they cannot reach are the three worst of the lot.

## Result 8: both together

| | rms | median |error| |
|---|---|---|
| chain where possible, formula otherwise | **2.98** | **0.37** |
| five-term formula alone | 4.90 | 1.72 |
| six-term formula alone (not blind) | 4.70 | 2.59 |

(MeV, over all 326.) The median falls by a factor of five. The rms barely moves,
because the 57 nuclei the relations cannot reach include the very worst: boron-21 and
boron-20 are unreachable and the formula misses them by 30 MeV, and two nuclei at
30 MeV dominate any sum of squares no matter how well the other 324 are done.

That gap between the median and the rms is the honest summary of the whole project so
far. The typical prediction is good and the worst ones are catastrophic, and they are
catastrophic in the one corner of the chart that matters for the drip line.

---

## What Phase 5 gives the rest of the project

1. A measured blind-test penalty for the mass formula: 1.65× on rms, with a +1.29 MeV
   bias toward under-binding.
2. Proof that the fitted constants' error bars are too small by a factor of at least
   five, even after χ²/dof scaling.
3. A prediction band that is calibrated in the middle and fails in the tail, with 17 %
   of nuclei outside 2σ.
4. The relations confirmed on real unseen data at 0.86 MeV rms, five times better than
   the formula, but silent on 17 % of the questions.
5. A factor-of-two correction to the Phase 4 uncertainty curve, which Phase 7 must
   carry.

## Still to do

- Phase 6 puts the published models (FRDM2012, HFB, Duflo–Zuker, WS4) through this
  same test set. The publication-date problem has to be handled explicitly: a model
  published after 2003 may have been fitted to some of these 326 nuclei, and one
  published after 2020 to all of them.
- The AME2003 uncertainties are used for the weighting floors but the test set is
  scored against AME2020 central values, which have their own uncertainties. Those are
  a few keV against errors of MeV, so it does not matter here, and it is recorded in
  case a later phase needs a tighter comparison.
