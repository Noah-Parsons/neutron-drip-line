# What the project found

The write-up the other documents feed into. It is Phase 8 of the plan.

## The question

Take an element and keep adding neutrons. At some point one more neutron falls
straight back out, and that version of the element cannot exist. That edge is the
neutron drip line. It has been reached experimentally only for the lightest elements,
up to about neon. For everything heavier the position comes from formulas, and the
formulas disagree.

This project asked two things: where do the methods say the edge is, and how sure can
anybody be?

## The answer, in one paragraph

The second question turned out to be the whole project. For a mid-mass element, the
honest band on the drip line from the methods used here is about twenty isotopes
wide, and the most accurate of those methods cannot reach the drip line at all
for anything heavier than neon. Along the way, the standard way of quoting
uncertainty on a fitted mass formula was found to understate the real movement of its
constants by seven to ten times, the standard way of estimating how far a method
extrapolates was found to flatter it by about 1.6, and two further obvious error
bars were found to fail by factors of ten in opposite directions. The one
well-calibrated uncertainty found anywhere in the project belongs to the AME
evaluators, not to this project.

## What is not ours

The mass formula is Weizsäcker's, 1935. The local relations are Garvey and Kelson's,
1966. The six published models are other groups' work. The data is the AME's. None of
the physics here is new, and the finding that mass models extrapolate badly toward
the drip line is already established — Erler et al., *Nature* 486, 509 (2012) made
that case with better models than these.

What this project adds is the measurement: pre-registered decisions, blind tests
against data that did not exist when the fits were made, and negative results
reported rather than buried.

## The six findings worth keeping

### 1. The fitted constants drift in one direction, and the error bars do not see it

Across AME 1993, 1995, 2003, 2012, 2016 and 2020, no single step between neighbouring
editions moves a constant by more than 3.2 standard errors. But every step moves
volume, surface, Coulomb and asymmetry the same way, so they accumulate instead of
cancelling: 1993 to 2020 is −9.1σ, −9.6σ, −8.5σ and −6.7σ.

Separating the two possible causes settles it. Refit a fixed set of 1,788 nuclei with
each edition's own values and the constants move 0.1σ in twenty-seven years. Refit
each edition's own set of nuclei with values held at AME2020 and the whole 9σ comes
back. The drift is caused by new nuclei entering the fit, not by old masses being
corrected.

The mechanism is identifiable. Of the 635 nuclei added since 1993, three quarters
scatter evenly around the old formula and do it no harm; the remaining quarter is
missed by +4.27 MeV on average with 80 % the same sign. A minority the formula
cannot describe, all wrong in one direction, drags every constant each time a new
edition appears.

An error bar covering the observed movement would be seven to ten times wider than
the one least squares reports — and that is a floor, because the drift has not
stopped. The quoted error answers "how much would this move if I redrew my sample
from the same population?", and each edition's additions are not a redraw from the
same population. It is not wrong; it answers a question nobody is asking.

This makes a testable prediction: the next AME edition should move all four the same
way again. If it puts the volume term near 15.42 MeV rather than 15.46, the drift
continues. If it reverses, this explanation is wrong.

Worked through in [Phase-5b.md](Phase-5b.md).

### 2. Hold-out testing flattered the method by about 1.6

To find out how fast a method loses accuracy when extrapolating, the standard move is
to hide part of the data and predict it. Done on AME2020, hiding the outer rim,
Garvey–Kelson chains gave 0.27 MeV of error at one step. Run against the real
1993–2020 frontier instead, with each split's hold-out computed on the earlier
edition only, the error was larger in 20 of 22 comparisons and in all five
independent splits, by a median factor of 1.57.

The reason is mechanical: cutting the rim off a finished chart leaves a tidy,
fully-surrounded edge to predict, while a real research frontier is ragged, full of
gaps, and least precisely measured exactly where a prediction has to start.

This is the finding with reach outside nuclear physics, and it is also the one where
the literature already has the general idea — see Meredig et al. (*Mol. Syst. Des.
Eng.*, 2018) on random cross-validation overstating extrapolative performance in
materials discovery, and Roberts et al. (*Ecography*, 2017) on spatially and
temporally structured data. What is unusual here is a real time split rather than
a simulated one: the actual 1993 dataset against thirty years of subsequent
measurement, five times over, because nuclear mass evaluation reissues its dataset
with a date stamp.

Phase 5 initially reported this factor as 2.2 and suggested it grew with the length
of the gap. Phase 5b found the typical value is 1.57 and that the trend with gap
length is not there (r = 0.02 across independent splits) — the apparent trend came
from long splits that overlap the short ones and reuse their data.

The five splits are in [Phase-5b.md](Phase-5b.md).

### 3. Four obvious error bars, and how each one fails

| uncertainty | verdict |
|---|---|
| least-squares covariance on a prediction | contributes 0.18 MeV of a 2.98 MeV band; the rest is model inadequacy |
| propagating a relation's scatter through a chain | exponentially too wide: 710 MeV after twenty steps, 96 % inside 1σ |
| agreement between routes sharing an input | far too narrow: 31 % inside twice the spread |
| spread across weighting choices | too wide and miscentred: covers 36 % of errors |
| **disagreement between independent models** | **usable: 90 % inside half the spread** |
| **the AME evaluators' own stated errors** | **well calibrated: 73 % at 1σ, 100 % at 2σ** |

The pattern is consistent. Agreement between methods that share their inputs is
worthless, and sharing can be subtle — routes through the same predicted neighbour,
or five weightings of the same fit set. Disagreement between genuinely independent
methods is informative. Of the things this project computed itself, nothing was well
calibrated; the two that were belong to other people.

The split-by-split table is in [Phase-5b.md](Phase-5b.md).

### 4. The 1966 relations are competitive with modern global models

Garvey–Kelson relations, found by enumerating all six arrangements of six nuclei in a
3×3 patch rather than copying indices, and verified against the published equations to
7×10⁻¹⁰ keV. Chained outward from AME2016 onto the 51 nuclei first measured after it:

| | rms | median |
|---|---|---|
| AME2016 evaluators' extrapolation | 0.17 | 0.11 |
| **Garvey–Kelson chains** | **0.35** | **0.18** |
| WS4 | 0.36 | 0.16 |
| HFB-21 | 0.70 | 0.37 |
| FRDM(2012) | 0.77 | 0.45 |
| five-term formula | 2.82 | 0.63 |

(MeV, on the 37 nuclei every method covers.) A parameter-free relation from 1966, in
a few dozen lines of R, matching a modern global model one step past the frontier.
The cost is coverage: the chains are silent on 11 of the 51, and on 17 % of the
2003→2020 test set, because a chain needs five measured neighbours to start from.

The accuracy decays as (chained steps)^1.37, not as the square root — chained
errors are not independent, since a prediction inherits its neighbours' mistakes and
they push the same way. The global formula overtakes the chains at about twelve
chained steps.

See [Phase-4.md](Phase-4.md), [Phase-6.md](Phase-6.md).

### 5. The evaluators beat the models

The AME's own `#` extrapolations — the numbers anybody actually looks up — came first
on every measure, ahead of all six published global models. They work locally, from
systematic trends around each nucleus, and one step past the frontier that beats a
global fit to the whole chart. Their stated uncertainties were also the only
well-calibrated ones in the project.

See [Phase-6.md](Phase-6.md).

### 6. The blind-test penalty is not a property of a model

Phase 5 found the five-term formula 1.65 times worse on nuclei it had not seen. Run
on all five splits, the penalty is 0.92 on both pre-2003 splits — the formula
predicted the newly measured nuclei *better* than it fitted its own set — and climbs
to 1.48, 1.51, 1.70 from 2003 on.

So "N times worse out of sample" describes where the new data landed, not the model.
In the 1990s new measurements filled in near stability and flattered the formula;
since then they have pushed outward into the region where it fails. The one thing
steady across all eight splits is the sign of the bias: +0.9 to +2.1 MeV every
time, newly measured nuclei always more bound than predicted. That sign is what drives
finding 1.

See [Phase-5b.md](Phase-5b.md).

## Where the project contradicted itself, and which way it went

Reported because the corrections are the most useful part of the record.

| claim | where it came from | how it ended |
|---|---|---|
| the shell correction helps far from stability | Phase 3, AME2020 hold-out: rms 4.41 → 3.51 | **wrong.** Phase 6: the six-term formula is worse than the five-term on real unseen data, median 3.01 against 0.63 |
| the formula is 1.65× worse out of sample | Phase 5, one split | **not general.** Pre-2003 splits give 0.92 |
| constants moved 5–7σ | Phase 5, 2003 vs 2020 | **understated.** Single steps are 2–3σ; the accumulation over six editions is 9σ, and the cause is identifiable |
| hold-outs are optimistic by a factor of 2, growing with the gap | Phase 5 | **half right.** Optimistic always, by 1.57; no trend with gap length |
| route agreement could be an error bar | Phase 4, correlation 0.89 with the real error | **wrong.** Correlation was scale, not calibration: 31 % coverage |

The pattern in all five: a test run on complete data agreed with the claim, and a
test run against data that did not exist yet did not.

## Limits

- **σ(S2n) is measured one to four neutrons past the frontier and applied at thirty.**
  That extrapolation is the largest unverified assumption in Phase 7, and no existing
  data can test it.
- **Phase 6 rests on 51 nuclei**, and the models in it were fitted at different dates.
  WS4 is both the best of the six and the most recently fitted, and that confound
  cannot be removed with one test set.
- **The six-term formula is not blind** anywhere in Phases 5 to 7: its shell term was
  shaped on AME2020 residuals. Labelled throughout.
- **Five independent splits is not many.** The drift in finding 1 rests on six
  editions, and the monotonicity test is close to one test at 1 in 16, not four
  independent ones, because the constants are correlated at 0.87 to 0.99.
- **Nothing here is a new fact about nuclei.**

## If the project continued

The lever is finding 2, not the drip line. It is the result that applies outside
nuclear physics, and the obvious next step is more time splits in other fields whose
reference datasets are reissued with dates — not more work on the drip line, where
the field's own models are already better than anything here by a factor of eight.

Finding 1 has a cheap test attached: wait for the next AME edition and check the sign.
