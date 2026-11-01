# Phase 5b: the same test, on every edition

The Phase 5 blind test, run five more times on every pair of AME editions since
1993, to find out which of its results were properties of the method and which were
accidents of one pair of editions.

Not in the manual's phase list. It exists because Phase 5 produced three claims a
single split could not support, and the AME has been reissued six times since 1993
with every edition dated.

Decisions D21–D23 in [Decisions.md](Decisions.md).

---

## The editions

| edition | rows | measured | estimated | fit set (A ≥ 20) |
|---|---|---|---|---|
| 1993 | 2,650 | 1,911 | 739 | 1,831 |
| 1995 | 2,931 | 1,964 | 967 | 1,882 |
| 2003 | 3,179 | 2,228 | 951 | 2,143 |
| 2012 | 3,353 | 2,438 | 915 | 2,348 |
| 2016 | 3,436 | 2,498 | 938 | 2,404 |
| 2020 | 3,558 | 2,550 | 1,008 | 2,455 |

The column layout changed twice — the mass excess field was widened in 2003 and
again in 2020 — and before 2003 the tabulated binding energy is the total rather
than per nucleon. Each edition's binding energies are built from its own
hydrogen and neutron mass excesses, read out of the same file, so no edition
borrows a constant from another. Checks: the tabulated binding energy is
reproduced to 0.035 keV or better in every edition, and the new general reader
agrees with the hand-built Phase 1 reader on AME2020 to 0.0004 keV.

The older editions come from the AMDC mirror at IMP; the IAEA copy serves 2003,
2016 and 2020 but not 1993, 1995 or 2012.

## The five real splits

| split | gap | fit set | test set | reached by chains | GK rms | GK median | SEMF rms | SEMF on its fit set |
|---|---|---|---|---|---|---|---|---|
| 93→95 | 2 yr | 1,831 | 63 | 27 | 0.42 | 0.27 | 2.81 | 3.04 |
| 95→03 | 8 yr | 1,882 | 286 | 257 | 0.87 | 0.44 | 2.78 | 3.02 |
| 03→12 | 9 yr | 2,143 | 220 | 184 | 0.52 | 0.24 | 4.39 | 2.98 |
| 12→16 | 4 yr | 2,348 | 59 | 48 | 0.36 | 0.18 | 4.73 | 3.12 |
| 16→20 | 4 yr | 2,404 | 73 | 58 | 0.49 | 0.17 | 5.39 | 3.17 |
| 93→03 | 10 yr | 1,831 | 339 | 304 | 0.95 | 0.44 | 2.84 | 3.04 |
| 03→20 | 17 yr | 2,143 | 326 | 269 | 0.86 | 0.30 | 4.90 | 2.98 |
| 93→20 | 27 yr | 1,831 | 635 | 552 | 1.22 | 0.40 | 4.09 | 3.04 |

(MeV. The last three overlap the first five and share their data.)

The Garvey–Kelson relations beat the formula on every split without exception, by
factors of 5 to 13 in the rms. That part of Phase 4 and Phase 5 holds up
everywhere.

## The hold-out is optimistic every time — but by 1.6, not 2

For each split, compare what a hold-out on the earlier edition predicted the
error would be against what it turned out to be, at matched chain length. That is
the honest version: it is what somebody standing in 1993, or 2003, could actually
have computed. Phase 5 compared against a hold-out on AME2020, the finished chart,
which nobody in 2003 could have done.

| split | gap | rounds compared | geometric mean optimism | independent |
|---|---|---|---|---|
| 93→95 | 2 yr | 1 | 1.57 | yes |
| 12→16 | 4 yr | 1 | 1.25 | yes |
| 16→20 | 4 yr | 1 | 1.57 | yes |
| 95→03 | 8 yr | 4 | 1.79 | yes |
| 03→12 | 9 yr | 3 | 1.30 | yes |
| 93→03 | 10 yr | 4 | 1.35 | no |
| 03→20 | 17 yr | 4 | 2.04 | no |
| 93→20 | 27 yr | 4 | 2.24 | no |

**The phenomenon replicates.** The hold-out underestimated the real error in 20 of
22 round-level comparisons and in all five independent splits.

**The size is 1.6, not 2.** The five independent splits run 1.25 to 1.79, median
1.57. The 2.2 reported in Phase 5 came from one long split and is the top of the
range, not the typical value.

**The trend with gap length is not there.** The long splits do look worse, which is
what suggested a trend. But they are built out of the short ones — 93→20 contains
all five — so they are the same data counted again. Across the five independent
splits the correlation of optimism with gap length is 0.02. With five points
there is no evidence either way, and the apparent trend was an artefact of
overlapping data.

So the correction Phase 5 recommended for Phase 7 — double the Phase 4 curve — is
roughly right but on the pessimistic side. A factor of 1.6 is better supported.

## The blind-test penalty is not a property of the formula

| split | gap | nuclei | fit rms | test rms | penalty | bias |
|---|---|---|---|---|---|---|
| 93→95 | 2 yr | 63 | 3.04 | 2.81 | **0.92** | +1.11 |
| 95→03 | 8 yr | 286 | 3.02 | 2.78 | **0.92** | +0.92 |
| 03→12 | 9 yr | 220 | 2.98 | 4.39 | 1.48 | +0.91 |
| 12→16 | 4 yr | 59 | 3.12 | 4.73 | 1.51 | +2.06 |
| 16→20 | 4 yr | 73 | 3.17 | 5.39 | 1.70 | +1.52 |

(MeV.) This claim does not survive. On both pre-2003 splits the penalty is below
one: the formula predicted the newly measured nuclei *better* than it fitted the
nuclei it was built from. From 2003 onward it climbs to 1.48, 1.51, 1.70.

"The formula is 1.65 times worse out of sample" is therefore a fact about where
experiments went after 2003, not a fact about the formula. In the 1990s new
measurements mostly filled in near stability and flattered it. Since then they have
pushed outward into the region where it fails.

What *is* steady across all eight splits is the sign of the bias: between +0.9
and +2.1 MeV every time. Newly measured nuclei are consistently more bound than the
formula of the day predicted. That turns out to matter more than the penalty ratio.

## The constants drift, and Phase 5 understated it

| edition | a_V | a_S | a_C | a_A | a_P |
|---|---|---|---|---|---|
| 1993 | 15.713 | 17.836 | 0.715 | 23.076 | 11.739 |
| 1995 | 15.699 | 17.792 | 0.714 | 23.062 | 11.777 |
| 2003 | 15.626 | 17.566 | 0.708 | 22.958 | 12.605 |
| 2012 | 15.553 | 17.309 | 0.704 | 22.860 | 12.409 |
| 2016 | 15.507 | 17.155 | 0.701 | 22.737 | 12.264 |
| 2020 | 15.463 | 17.017 | 0.699 | 22.624 | 12.165 |

Step-to-step shifts, in standard errors of the earlier fit:

| step | a_V | a_S | a_C | a_A | a_P |
|---|---|---|---|---|---|
| 93→95 | −0.5 | −0.5 | −0.6 | −0.2 | 0.0 |
| 95→03 | −2.7 | −2.7 | −2.9 | −1.5 | +0.9 |
| 03→12 | −2.9 | −3.2 | −2.5 | −1.6 | −0.2 |
| 12→16 | −1.9 | −2.0 | −1.6 | −2.0 | −0.2 |
| 16→20 | −1.8 | −1.8 | −1.6 | −1.9 | −0.1 |
| **93→20** | **−9.1** | **−9.6** | **−8.5** | **−6.7** | +0.4 |

**No single step is alarming.** The largest is 3.2σ and only 1 of 25 comparisons
exceeds 3σ. Anyone checking one edition against the next would have found nothing
to report.

**All five steps go the same way, for four of the five constants.** That is why they
accumulate. Five steps of about 2σ in one direction come to 9σ; five random steps of
2σ would have come to about 4.5. Under a coin flip a given constant has a 1 in 16
chance of moving one way five times running. The four are correlated at 0.87 to
0.99, so this is close to one test rather than four — but it is one test at 1 in 16,
on a pattern nobody went looking for.

The pairing term is the exception throughout. It is so poorly determined (±0.9 MeV
on a value near 12) that its quoted error already covers everything it does.

## The drift comes from new nuclei, not corrected ones

Two things changed between editions: the set of nuclei grew, and some masses already
in the table were revised. Separate them.

- **A — fixed set of nuclei, each edition's own values.** Fit only the 1,788 nuclei
  with A ≥ 20 measured in all six editions.
- **B — growing set, fixed values.** Fit each edition's own set, but take every mass
  from AME2020.

Movement from 1993 to 2020, in 1993 standard errors:

| | a_V | a_S | a_C | a_A |
|---|---|---|---|---|
| A: values only | 0.1 | 0.0 | 0.1 | 0.1 |
| B: nuclei only | **8.9** | **9.4** | **8.3** | **6.3** |
| both (the real thing) | 9.1 | 9.6 | 8.5 | 6.7 |

**The entire drift is B.** Re-measuring nuclei already in the table moves the
constants by a tenth of a standard error over twenty-seven years. Adding new nuclei
moves them by nine. This is not the AME correcting old mistakes; the old numbers
were fine.

## The mechanism

Of the 635 nuclei added to the A ≥ 20 fit set between 1993 and 2020, the 1993
formula misses them by 4.09 MeV rms against 3.04 MeV on its own fit set, with a mean
miss of +1.24 MeV. Splitting them at the upper quartile of |miss|:

| | mean miss | same sign |
|---|---|---|
| worst quarter | **+4.27 MeV** | **80 %** |
| the other three quarters | +0.23 MeV | 50 % |

Three quarters of the new nuclei scatter evenly around the old formula and do it no
harm. The remaining quarter is missed by 4 MeV on average, and 80 % of those misses
are the same sign. A minority of nuclei the formula cannot describe, all wrong in
one direction, drags every constant the same way each time a new edition appears.

| | a_V | a_S | a_C | a_A |
|---|---|---|---|---|
| spread across the six editions (MeV) | 0.249 | 0.820 | 0.017 | 0.452 |
| typical quoted error (MeV) | 0.025 | 0.080 | 0.002 | 0.063 |
| **ratio** | **9.8** | **10.3** | **9.5** | **7.2** |

An error bar that covered the movement would have to be seven to ten times wider
than the one least squares reports — and that is a floor, not an estimate, because
the drift has not stopped.

---

## What this changes

The quoted error bar on a fitted constant answers one question: how much would this
move if I redrew my sample from the same population? The nuclei added at each
edition are not a redraw from the same population. They are systematically harder
for the formula and missed in one direction. So the error bar is not wrong about the
question it answers — it is answering a question nobody is asking.

That is the project's headline, stated more carefully than Phase 5 managed, and with
five independent replications instead of one split.

**It also makes a prediction, which is rare for this project.** The next AME edition
should move all four constants the same way again. If AME2024 or AME2028 puts the
volume term near 15.42 MeV rather than 15.46, the drift is continuing. If it
reverses, this explanation is wrong.

## Corrections this phase makes to Phase 5

| Phase 5 said | Phase 5b finds |
|---|---|
| the formula is 1.65× worse out of sample | true for 2003→2020 only; the pre-2003 splits give 0.92 |
| constants moved 5–7σ | true over three editions; single steps are 2–3σ, and the accumulation is what matters |
| the hold-out was optimistic by a factor of 2 | optimistic always, but by 1.57 on independent splits |
| (implied) the optimism grows with the gap | no evidence; r = 0.02 across independent splits |
