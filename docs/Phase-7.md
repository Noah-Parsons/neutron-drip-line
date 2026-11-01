# Phase 7: the drip line as a probability band

Turning everything into a drip line with a probability attached to every isotope
instead of a single line. See D24 and D26 in [Decisions.md](Decisions.md).

## The construction

A nucleus is past the drip line when S2n, the energy needed to remove two neutrons,
goes negative (D4). So for each element, step outward in N, predict S2n, and turn it
into a probability with the uncertainty the blind tests actually measured:

> P(bound) = Φ( S2n predicted / σ )

The line is where that falls through 0.5. The band is where it runs from 0.9 to 0.1.

## The uncertainty on S2n, not on B

A drip line needs the error on a *difference* of two binding energies, and a method
wrong about one nucleus is wrong about its neighbour in the same direction. That has
to be measured, not assumed. Pooling the 2003→2020 and 1995→2003 blind tests:

| method | rms error on B | rms error on S2n |
|---|---|---|
| five-term formula | 3.87 | **1.44** |
| six-term formula | 3.56 | **1.26** |
| Garvey–Kelson chains | 0.85 | **0.69** |

(MeV.) The error on S2n is about a third of the error on B for the formulas. That
is what makes a drip line worth attempting at all — if the uncertainty were the
4–5 MeV of Phase 5, nothing could be said about anything.

By distance past the frontier:

| neutrons out | nuclei | five-term | GK chains |
|---|---|---|---|
| 1 | 83 | 2.12 | 0.52 |
| 2 | 62 | 1.70 | 0.73 |
| 3 | 39 | 1.49 | 0.67 |
| 4+ | 31 | 0.97 | 0.61 |

Flat, or even falling. But four neutrons is the whole of the evidence, and the
drip line is thirty neutrons out. Nothing here says what σ(S2n) does at thirty.

No 1.6 correction from Phase 5b is applied: these are already real blind-test errors,
and that factor corrects a hold-out estimate to reality. Applying it would count the
same correction twice.

## The band

| Z | measured edge | P=0.9 | P=0.5 | P=0.1 | band width | neutrons past the edge |
|---|---|---|---|---|---|---|
| 8 | 18 | 16 | 16 | 18 | 2 | −2 |
| 20 | 36 | 40 | 43 | 46 | 6 | 7 |
| 28 | 45 | 57 | 61 | 66 | 9 | 16 |
| 50 | 85 | 106 | 114 | 123 | 17 | 29 |
| 70 | 108 | 152 | 164 | 178 | 26 | 56 |
| 82 | 133 | 180 | 195 | 211 | 31 | 62 |
| 92 | 148 | 205 | 221 | 240 | 35 | 73 |

(five-term formula.) Over all 88 elements it reaches:

- **band width: median 18 neutrons**, range 2 to 36
- **the line sits 35 neutrons past the measured edge on average**

The six-term formula gives a median width of 14 and the same 34-neutron offset.

Two things follow, and they are the point of the phase.

**The band is wide.** For a mid-mass element the honest statement is "somewhere in a
range of about twenty isotopes", which is not a located drip line by any standard.

**The relations cannot help.** Thirty-five neutrons past the frontier is far beyond
the twelve chained steps where Phase 4 found the relations stop beating the formula.
The most accurate tool in this project — competitive with published models in Phase 6
— cannot reach the drip line for any element heavier than about neon. The band
above is the formula's, alone, which is why it is as wide as it is.

## How much is the choice of formula?

| | neutrons |
|---|---|
| the two formulas disagree by (median) | 2 |
| range of their disagreement | 0 to 8 |
| the statistical band width (median) | 17.5 |

Here the calibrated uncertainty dominates and the model choice does not — the
opposite of Phase 2, where changing the weighting moved the constants by 12 to 16
error bars.

That comparison has to be made carefully, though. Two formulas sharing four of their
five terms and the same fit set is a weak test of model choice, so 2 neutrons is a
floor on it rather than a measurement. Phase 6 found the six published models spread
by 1.53 MeV in mass excess one neutron past the frontier; thirty neutrons out they
will spread considerably more.

## The only place the band can be checked

Three measured nuclei with A ≥ 20 have negative S2n — they are already past the drip
line, and they are the only direct test available.

| nuclide | Z | N | S2n measured | S2n predicted | P(bound) |
|---|---|---|---|---|---|
| B-20 | 5 | 15 | −1.47 | −9.93 | 0.00 |
| B-21 | 5 | 16 | −2.47 | −11.17 | 0.00 |
| O-26 | 8 | 18 | −0.02 | −3.26 | 0.01 |

(MeV.) It calls all three unbound, which is the right answer. But it has them 2
to 9 MeV more unbound than they are, so it is right for the wrong reason, and all
three are light, where the formula's errors happen to point this way.

The other direction: of the 2,292 measured nuclei that are bound, the band calls
29 unbound at P < 0.5 and 19 at P < 0.1 — 1.3 % and 0.8 %.

So a band this wide is rarely wrong about nuclei we already have. It simply cannot
say much about the ones we do not. That is what an honest uncertainty looks like
when the model is not good enough for the question.

## How many nuclei exist?

| formula | P > 0.9 | P > 0.5 | P > 0.1 | spread |
|---|---|---|---|---|
| five-term | 7,132 | 8,086 | 9,041 | **1,909** |
| six-term | 7,320 | 8,148 | 8,988 | **1,668** |

(Z = 8 to 110, neutron-rich side only, so not directly comparable with published
totals, which count the proton-rich side too.)

Erler et al., *Nature* 486, 509 (2012), put the number of bound nuclei near 7,000
with a spread of a few hundred across the published models. The spread here is
about 1,900 — several times wider.

The published models are genuinely better than this formula; Phase 6 measured that
directly, by factors of 8 to 18. So the right reading is not that the field's number
is wrong. It is that a few hundred is the spread of *model agreement*, and Phase 4
showed agreement between methods sharing their inputs is not an error bar, while
Phase 6 showed disagreement between independent ones is a usable one. Which of those
the published spread is depends on how independent those models really are, and this
project cannot settle that.

---

## The conclusion

The drip line cannot be located by the methods in this project, and the useful part
is that it can say by how much, and why:

1. **A band about twenty isotopes wide** for a mid-mass element, from the only
   uncertainty here that has been checked against unseen data.
2. **The accurate method cannot reach it.** The relations are competitive with
   published models for the first ten neutrons past the frontier and the drip line is
   thirty-five out.
3. **Where the answer is known, the band gets it right** — all three measured
   unbound nuclei — but with predicted S2n values 2 to 9 MeV off, so it is not
   evidence the band is trustworthy further out.
4. **A total of 7,100 to 9,000 bound nuclei** on the neutron-rich side of Z = 8–110,
   against a published figure near 7,000 with a spread of a few hundred.

## Loose ends

- The σ(S2n) used here is measured over one to four neutrons past the frontier and
  applied at thirty. That extrapolation is the single largest unverified assumption
  in the phase, and nothing in the AME can test it, because the data to test it with
  has not been taken.
- The six-term line depends on a predicted shell closure at N = 184 and another at
  258 (D24), neither of which has ever been reached experimentally.
