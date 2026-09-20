# Phase 4: the Garvey–Kelson relations

**Goal:** test a second, completely different prediction method — local relations
between neighbouring nuclei instead of one global formula — and find out how far
outward it can be trusted.

**Status:** done.

The choices for this phase are D12–D16 in [DECISIONS.md](DECISIONS.md), written
down before the chaining test was run.

---

## What the relations are

Pick six nuclei sitting close together on the chart, add their binding energies
with alternating signs, and the total comes out at almost exactly zero. Garvey
and Kelson found this in 1966. It works because the parts of the nuclear mass
that change smoothly — the bulk, the surface, the electrical repulsion — cancel
between the six terms, leaving only local structure behind.

The six nuclei fit inside a 3×3 patch of the chart: three neighbouring elements,
three neighbouring neutron numbers.

## Result 1: the relations found from the data, not copied

There are only six ways to pick three cells with a plus sign and three with a
minus from that 3×3 patch, using each row and each column once on each side. All
six were tried on every patch where all six masses are measured:

| plus | minus | patches | rms | median miss |
|---|---|---|---|---|
| 021 | 102 | 2,057 | 486 keV | **109 keV** |
| 120 | 201 | 1,916 | 599 keV | **116 keV** |
| 102 | 210 | 1,926 | 2,209 keV | 1,059 keV |
| 021 | 210 | 1,930 | 2,253 keV | 1,071 keV |
| 012 | 120 | 2,004 | 2,293 keV | 1,064 keV |
| 012 | 201 | 2,000 | 2,327 keV | 1,059 keV |

Two of the six cancel. The other four are ten times worse, and they are the
useful control: they show what an arrangement that does *not* cancel the smooth
part of the mass looks like, which is what a mistyped index would give.

The two that work are the pair Garvey and Kelson published. `120/201` is the
**transverse** relation; writing the published form out term by term and
comparing gives agreement to 2×10⁻¹⁰ keV, so the indices are right. `021/102` is
the **longitudinal** one.

**Why those two:** both cancel any mass that can be written as a function of Z
plus a function of N plus a function of A. The transverse does it exactly — the Z
values, the N values and the A values on the plus side are the same three numbers
as on the minus side. The longitudinal matches the A values' first two moments
rather than the values themselves, so a smooth dependence on A survives only at
third order. The other four cancel nothing beyond the terms linear in Z and N.

A useful consequence of that cancellation: masses, mass excesses and binding
energies all give the same answer, because they differ only by terms linear in Z,
N and A. Checked to 7×10⁻¹⁰ keV.

## Result 2: how accurate they are

Over every patch with all six masses measured:

| | patches | rms | median miss | 90th percentile | worst |
|---|---|---|---|---|---|
| transverse | 1,916 | 599 keV | 116 keV | 451 keV | 9,499 keV |
| longitudinal | 2,057 | 486 keV | 109 keV | 412 keV | 7,922 keV |
| transverse, A ≥ 20 | 1,848 | 347 keV | 112 keV | 378 keV | 2,876 keV |
| longitudinal, A ≥ 20 | 1,979 | 244 keV | 104 keV | 353 keV | 1,684 keV |

For comparison, the six-term formula of Phase 3 misses by 2,564 keV rms on the
nuclei it was fitted to. **In the median the relations are about twenty times
more accurate.**

Two things to be careful about.

**The rms is five times the median.** The distribution has a heavy tail. A
handful of very light nuclei (lithium-5, helium-5, boron-9) miss by 5–9 MeV.
Below A = 20 the relations are barely better than the global formula. Quoting
"about 100 keV" without saying it is a median would be misleading.

**Accuracy depends strongly on where you are.** It has to be read inside a mass
band, because the relations are much better in heavy nuclei, and any measure of
"distance from the edge" is confounded with mass:

| region | 0–5 from edge | 6–10 | 11–20 | >20 |
|---|---|---|---|---|
| Z ≤ 20 | 1,542 / 1,428 | 1,655 / 1,407 | 1,564 / 1,062 | — |
| Z 21–50 | 251 / 207 | 243 / 253 | 439 / 233 | 460 / 215 |
| Z 51–82 | 142 / 127 | 179 / 166 | 146 / 142 | 198 / 194 |
| Z > 82 | 107 / 85 | 141 / 152 | 124 / 100 | 89 / 72 |

(rms in keV, transverse / longitudinal, by how far the patch sits inside that
element's measured range.) Within a band the accuracy is roughly flat — it does
not get worse as you approach the neutron-rich edge of measured territory. The
strong pattern is with mass, not with distance.

## Result 3: predicting outward

If five of the six masses are known, the relation gives the sixth. Feed each
prediction back in and it runs outward step by step. Twelve routes can reach any
one nucleus: two relations, and six choices of which cell in the patch is the
unknown.

Tested on the Phase 3 hold-out (D11): hide the 4 most neutron-rich isotopes of
every element with at least 8 measured, and predict them.

| steps out | nuclei | relations | five terms | six terms |
|---|---|---|---|---|
| 1 | 77 | **0.90** | 4.79 | 4.02 |
| 2 | 88 | **0.65** | 4.54 | 3.68 |
| 3 | 91 | **0.37** | 4.21 | 3.24 |
| 4 | 91 | **0.25** | 4.07 | 3.10 |
| all | 347 | **0.58** | 4.39 | 3.51 |

(rms error in binding energy, MeV.) At the hidden edge the relations beat the
six-term formula by a factor of four, and by twelve at four steps in. This is the
clearest result of the phase.

**17 of the 364 hidden nuclei cannot be reached at all.** Chaining needs five
measured neighbours to start from. The global formula always returns an answer,
even a bad one; the relations sometimes return nothing. Those 17 are reported,
not filled in from the formula (D14).

## Result 4: how fast the error grows

Repeating the hold-out at depths of 4, 8, 12, 16 and 20 hidden isotopes and
pooling gives enough nuclei at each chain length to measure the growth. The x
axis is the number of chained rounds, not the distance from the edge: a nucleus
two isotopes out can still take five rounds to reach if the route has to go round
an unmeasured gap, and it is the chaining that costs the accuracy.

| chained steps | nuclei | median miss | relations | six terms |
|---|---|---|---|---|
| 1 | 316 | 0.10 | **0.27** | 2.54 |
| 2 | 331 | 0.14 | **0.39** | 2.59 |
| 4 | 340 | 0.27 | **0.69** | 2.91 |
| 6 | 276 | 0.44 | **1.01** | 2.87 |
| 8 | 260 | 0.71 | **1.71** | 3.10 |
| 10 | 202 | 1.04 | **2.54** | 3.17 |
| 12 | 176 | 1.44 | 3.55 | **3.49** |
| 14 | 119 | 1.68 | 5.00 | **3.80** |
| 16 | 101 | 2.32 | 7.25 | **4.19** |
| 20 | 41 | 1.59 | 14.11 | **5.00** |

(rms error in MeV; the winner in bold.) Fitted as a power law,

> rms ≈ **0.13 MeV × (chained steps)^1.37**

**The exponent is 1.37, not 0.5.** A random walk of independent errors would give
0.5. It is steeper because the errors are not independent: a prediction is built
out of its neighbours, and when those neighbours were themselves predicted their
errors come along with them and push the same way.

The fit is a summary, not a law. It is pulled by the long end of the range, so it
over-predicts the first step (0.13 against 0.27 MeV measured) and under-predicts
the last few. The table is the result; the power law is shorthand for it.

## Result 5: where the relations stop winning

The six-term formula first overtakes them at **twelve chained steps** (3.55
against 3.49 MeV), and is clearly ahead after that.

This is a hard limit on the method and it matters for Phase 7. For most heavy
elements the drip line is tens of neutrons past the last measured isotope, which
is well past where the relations' advantage runs out. They are the better tool
for the first ten steps or so into unmeasured territory and the worse tool beyond
that.

## Result 6: two error bars that don't work

Two obvious ways to put an uncertainty on a chained prediction. Both fail, in
opposite directions.

**Propagate the relation's own scatter.** Each round adds the relation's scatter
plus the variance of any input that was itself predicted, which multiplies the
variance by roughly five per round. The band grows exponentially while the real
error grows as a power of the chain length:

| chained steps | propagated 1σ | actual rms | fraction inside 1σ |
|---|---|---|---|
| 1 | 0.36 | 0.27 | 0.90 |
| 4 | 1.15 | 0.69 | 0.93 |
| 8 | 5.18 | 1.71 | 0.98 |
| 12 | 24.77 | 3.55 | 1.00 |
| 20 | 709.76 | 14.11 | 1.00 |

A 1σ band should hold about 68 % of them. This one holds 96 % overall, and by
twenty steps it is 700 MeV wide — wider than the binding energy of a light
nucleus, and useless.

**Use the disagreement between routes.** For the 1,694 nuclei reached more than
one way, compare the spread between routes with the actual error. Twice the
spread holds only 31 % of them overall, and 6–12 % beyond ten rounds. Routes that
pass through the same already-predicted neighbour inherit its error, so they
agree with each other while all being wrong together. Agreement between methods
that share an input is not evidence.

What is left is the measured curve itself. The hold-out gives an honest error bar
as a function of chain length, and that is what Phase 7 will use. Its limit is
that it is one average over the whole chart, and the region table in Result 2
shows the scatter around it is large.

## Result 7: the two relations separately

| | reached, of 364 | rms | median miss |
|---|---|---|---|
| transverse alone | 333 | 0.57 | 0.22 |
| longitudinal alone | 259 | 0.77 | 0.18 |
| both | 347 | 0.58 | 0.20 |

(MeV.) The transverse relation reaches far more nuclei because its footprint sits
better against a ragged neutron-rich edge. The longitudinal one has the smaller
median error. Using both reaches 347, more than either alone, but the rms of the
combination is no better than the transverse alone — averaging the two fills in
gaps rather than improving accuracy.

Having more than one route matters a great deal:

| | nuclei | rms | median miss |
|---|---|---|---|
| reached one way only | 2,216 | 3.98 | 0.68 |
| reached two or more ways | 1,697 | 2.61 | 0.32 |

(MeV, pooled over all hold-out depths.) The single-route predictions are the ones
out on a thin filament with nothing to cross-check them, and they are twice as
bad.

---

## What Phase 4 gives the rest of the project

1. A second prediction method, independent of the mass formula, that is about
   twenty times more accurate close to measured nuclei.
2. A measured cost per step outward: rms ≈ 0.13 MeV × steps^1.37.
3. A crossover at about twelve chained steps, after which the global formula is
   the better tool.
4. Two failed error bars, with the numbers, which is why Phase 7 will use the
   empirical curve instead of propagating anything.

## Still to do

- The relations were verified against the published transverse form. The
  longitudinal form was found by enumeration and named by its footprint; check
  the sign convention against Garvey, Gerace, Jaffe, Talmi and Kelson, *Reviews
  of Modern Physics* **41** (1969) before presenting.
- The chaining test uses AME2020 only, so every "prediction" is of a nucleus
  somebody has already measured. The real extrapolation test is Phase 5.
