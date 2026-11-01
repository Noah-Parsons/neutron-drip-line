# Phase 6: the published models on the same test

**Goal:** score the field's standard mass models on the same blind test, so this
project's methods can be placed against what people actually use.

**Status:** done.

Decisions D25 in [DECISIONS.md](DECISIONS.md).

---

## What could be obtained, and what could not

Six published models, plus the AME evaluators' own extrapolations with their stated
uncertainties, come from the comparison table behind Huang, Audi, Wang, Kondev, Naimi
and Xu, *Scientific Data* **9**, 532 (2022) — figshare collection 5640763, Data set 2.
Every value in that table is a prediction for a nucleus nobody had measured when it
was made, which is what makes this test possible.

The FRDM(2012) table was not obtained from its own source: the Los Alamos page that
hosts it is unreachable from here, and a TLS workaround was declined. The FRDM values
used are the ones the *Scientific Data* paper tabulates. Nothing in this phase
depends on the distinction, but it is recorded.

## The test set

Nuclei measured in AME2020 but not in AME2016 — the 16→20 split of Phase 5b — that
the published table also carries. **51 nuclei**, spread across the chart: 5 with
Z ≤ 20, 16 with Z 21–50, 21 with Z 51–82, 9 above. Small, but every one was an open
question when all seven predictions were made.

## Result 1: the standings

| method | nuclei | rms | median miss | bias | worst |
|---|---|---|---|---|---|
| **AME2016 extrapolation** | 48 | **0.29** | **0.15** | +0.09 | 1.05 |
| **WS4** | 49 | **0.35** | 0.20 | −0.02 | 1.51 |
| **Garvey–Kelson chains** | 40 | **0.53** | 0.19 | +0.04 | 2.11 |
| HFB-21 | 49 | 0.79 | 0.40 | −0.12 | 2.26 |
| Duflo–Zuker | 49 | 0.81 | 0.51 | −0.21 | 2.65 |
| FRDM(2012) | 49 | 0.81 | 0.47 | +0.18 | 2.94 |
| KTUY | 50 | 0.94 | 0.68 | +0.40 | 2.17 |
| INM | 51 | 1.40 | 0.44 | +0.45 | 6.42 |
| five-term formula | 51 | 6.29 | 0.73 | −2.17 | 28.23 |
| six-term formula | 51 | 6.35 | 3.04 | −3.07 | 28.64 |

On the 37 nuclei every method covers:

| method | rms | median miss |
|---|---|---|
| AME2016 extrapolation | **0.17** | **0.11** |
| Garvey–Kelson chains | **0.35** | 0.18 |
| WS4 | 0.36 | 0.16 |
| HFB-21 | 0.70 | 0.37 |
| FRDM(2012) | 0.77 | 0.45 |
| Duflo–Zuker | 0.84 | 0.50 |
| KTUY | 0.89 | 0.68 |
| INM | 0.92 | 0.35 |
| five-term formula | 2.82 | 0.63 |
| six-term formula | 3.07 | 3.01 |

(error in mass excess, MeV.)

Three things worth saying plainly.

**The evaluators' own extrapolations beat every published global model.** They work
locally, from systematic trends around each nucleus, and one step past the frontier
that beats a global model fitted to the whole chart. If you want a mass for a nucleus
just outside the measured region, the AME's `#` value is the best number available.

**The Garvey–Kelson chains are competitive with the best of them.** 0.35 MeV against
WS4's 0.36, HFB-21's 0.70, FRDM(2012)'s 0.77. A parameter-free relation from 1966,
implemented from scratch in a few dozen lines of R, matches a modern global model
just past the frontier. The cost is coverage: silent on 11 of the 51, which the
global models never are.

**The formula this project spent Phases 2 and 3 on is 8 to 18 times worse than
anything published.** That is the honest place to put it.

## Result 2: the six-term formula is worse than the five-term one

3.07 against 2.82 in rms, and **3.01 against 0.63 in the median** — the shell
correction nearly quintuples the typical error on this test set.

Phase 3 asked exactly this question, with the far-from-stability test of D11, and
answered yes on an AME2020 hold-out: rms 4.41 → 3.51 MeV. Phase 5 found it slightly
better on rms (4.70 against 4.90) but already worse in the median (2.59 against 1.72).
Here it is clearly worse on both.

Taken with Phase 5b, the reading is that the shell term helps where it was designed
and hurts when extrapolated, and the AME2020 hold-out that justified it was the wrong
test — the same lesson as Phase 5b's Result 1, arrived at independently.

## Result 3: whose error bars hold

The AME publishes an uncertainty with every extrapolated value, and 48 of these
nuclei have one.

| | value |
|---|---|
| mean stated error | 0.27 MeV |
| rms actual error | 0.29 MeV |
| inside 1 stated error | **73 %** (68 % expected) |
| inside 2 stated errors | **100 %** (95 % expected) |
| actual / stated, median | 0.70 |
| actual / stated, 90th percentile | 1.29 |

**These are the only well-calibrated error bars in this project, and they are not
ours.** Slightly conservative in the middle, and the tail holds too. Phase 5 found
this project's own bands held 64 % at 1σ and 83 % at 2σ.

## Result 4: disagreement between models is a usable error bar

| | value |
|---|---|
| the six models averaged, rms | 1.04 MeV |
| the six models averaged, median miss | 0.28 MeV |
| median spread between the six | 1.53 MeV |
| error inside half the spread | **90 %** |
| error inside the full spread | **94 %** |

Averaging the six gives a better median than any one of them. And half the spread
between them covers 90 % of the errors — the one uncertainty anywhere in this project
that is neither far too wide nor far too narrow. It is not a calculated uncertainty at
all; it is six groups disagreeing.

That is worth holding next to Phase 4, where agreement between two relations sharing
an input was shown to be worthless as an error bar. Disagreement between genuinely
independent methods is informative; disagreement between methods that share their
inputs is not.

## Result 5: by region

| region | nuclei | AME2016 | WS4 | GK chains | FRDM12 | HFB21 | five-term |
|---|---|---|---|---|---|---|---|
| Z ≤ 20 | 5 | 0.68 | 1.03 | 1.37 | 1.88 | 1.40 | 17.44 |
| Z 21–50 | 16 | 0.28 | 0.32 | **0.20** | 0.93 | 1.02 | 4.54 |
| Z 51–82 | 21 | **0.15** | 0.21 | 0.23 | 0.51 | 0.48 | 2.54 |
| Z > 82 | 9 | **0.13** | 0.20 | 0.28 | 0.50 | 0.58 | 1.96 |

(rms, MeV.) Everything is worst in the light neutron-rich corner, which is where the
drip line has actually been reached. The chains are the best method in the
mid-mass region.

## The publication-date problem, stated

Every model here was published before AME2020, so every test nucleus was unmeasured
when it was fitted. But they were fitted at different times:

| model | vintage |
|---|---|
| Duflo–Zuker | 1995 parameters |
| KTUY | 2005 |
| HFB-21 | AME2003-era data |
| FRDM(2012) | published 2016, adjusted to AME2003 |
| WS4 | 2014, fitted to AME2012 |
| INM | 2000s |
| AME2016 extrapolation | 2016 |

**WS4 is the best of the six and the most recently fitted; the AME2016 extrapolation
is the best of all and the most recent of all.** That ordering is a confound this test
set cannot remove — it would take a test set postdating all of them equally, which
does not exist. It is reported rather than argued away.

---

## What Phase 6 gives the rest of the project

1. A place for this project's methods in the real standings: the chains among the
   best, the formula far behind.
2. One well-calibrated uncertainty to point at — the AME's own.
3. Model disagreement validated as a rough error bar at 90 % coverage.
4. A direct contradiction of Phase 3's conclusion about the shell correction.
