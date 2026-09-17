# Phase 3: what the formula misses, and a shell correction

**Goal:** find the pattern in the five-term formula's mistakes, design a sixth
term to fix it, and check whether that fix **helps or hurts far from stability**,
where the drip line is.

**Status:** done.

The shape of the correction, and the tests used to judge it, were written down
**before** the six-term fit was first run: decisions D9–D11 in
[DECISIONS.md](DECISIONS.md). That stops the results from quietly steering the
choices.

---

## Result 1: the data finds the magic numbers by itself

For every neutron number N, we averaged the formula's misses over all nuclei
with that N, and did the same for every Z. Then we looked for **peaks**: values
higher than everything within a window around them. Nobody told the search where
the magic numbers are.

| window | peaks by N | peaks by Z |
|---|---|---|
| ±4 | 8, 16, **29, 50, 82**, 96, **125**, 153, 159 | 5, **20, 29, 50**, 68, **82**, 107 |
| ±6 | 16, **29, 50, 82**, 96, **125**, 159 | 5, **20, 29, 50, 82**, 107 |
| ±8 | 16, **29, 50, 82, 125**, 159 | 5, **29, 50, 82**, 107 |

**In simple words:** the peaks land on or right next to the known magic numbers
**28, 50, 82 and 126** (for neutrons) and **28, 50 and 82** (for protons). They
appear at every window size. "The model's mistakes told me where the shells are"
is literally true.

**What the other peaks are:**
- **Peaks at the ends** (N = 159, Z = 107, and Z = 5) are edge effects. There's
  nothing past them to be higher than, and the lightest elements are where the
  formula fails worst anyway.
- **N = 16 is interesting.** Experiments have suggested that 16 behaves like a
  magic number in very neutron-rich light nuclei (look up Ozawa et al., 2000).
  Our peak is **consistent with that, but doesn't prove it**. It comes from a few
  light nuclei the formula gets badly wrong for other reasons too.
- **20 is weak.** It appears for protons at small windows only, and never
  clearly for neutrons.

## Result 2: the shell correction

The sixth term (decision D9) is

> a_sh × [f(Z) + f(N)], where f(n) = ν(D − ν)/D

- **ν** is how far n is past the magic number below it.
- **D** is the size of that shell.

So f is **zero at every magic number** and **biggest halfway through a shell**.

**Fitted:** a_sh = **−0.506 ± 0.013 MeV**.

It's negative, as the physics says it should be: nuclei in the middle of a shell
are held **less** tightly than the smooth formula predicts, and nuclei at a full
shell **more** tightly. The fit found the sign on its own.

| | five terms | six terms |
|---|---|---|
| typical miss (rms) | 3.24 MeV | **2.56 MeV** |
| improvement | | **21 %** |

The other five constants barely moved (all by less than 0.25 MeV). The shell
constant is **nearly independent** of them (correlations of 0.10 or less). Unlike
volume and surface, it measures something none of the other terms can see.

## Result 3: which magic numbers it fixed, and which it made worse

Average miss for nuclei sitting **exactly at** each magic number (closer to 0 is
better):

| magic number | nuclei | before (MeV) | after (MeV) | |
|---|---|---|---|---|
| N = 126 | 14 | +5.37 | **−0.06** | ✔ fixed |
| Z = 82 | 38 | +3.62 | **+0.28** | ✔ fixed |
| N = 82 | 24 | +5.48 | +2.86 | ✔ halved |
| Z = 50 | 35 | +4.48 | +2.33 | ✔ halved |
| N = 50 | 21 | +3.57 | +1.71 | ✔ halved |
| N = 28 | 15 | +0.50 | −1.34 | ✘ worse |
| Z = 28 | 22 | −0.35 | −1.47 | ✘ worse |
| N = 20 | 16 | −1.38 | −2.49 | ✘ worse |
| Z = 20 | 21 | −0.72 | −2.04 | ✘ worse |

**In simple words:** it fixes the **big** shells (50, 82, 126) and makes the
**small** ones (20, 28) worse. One constant has to serve every shell. The big
shells dominate the fit, and the small ones get pushed the wrong way.

There's a second side effect. In the middle of the large 82–126 neutron shell
(around N = 100), the correction now overshoots by about +3 MeV. Many nuclei there
are known to be deformed (squashed out of a sphere), which also changes their
binding. This simple term knows nothing about that.

## Result 4: far from stability, it still helps (the key test)

Decision D11: for each of the 91 elements with at least 8 measured isotopes, we
**hid its 4 most neutron-rich isotopes** (364 nuclei in all). Both formulas were
fitted to the rest, then asked to predict the hidden ones.

| hidden isotope | five terms (rms miss) | six terms (rms miss) |
|---|---|---|
| all 364 | 4.41 MeV | **3.51 MeV** |
| most neutron-rich (step 1) | 4.79 | **4.00** |
| step 2 | 4.52 | **3.65** |
| step 3 | 4.21 | **3.24** |
| step 4 | 4.07 | **3.10** |

**The six-term formula predicts better at every step outward.** The result holds
if we hide 2 per element instead (4.49 → 3.63) or 6 (4.28 → 3.40).

By region of the chart:

| elements | five terms | six terms |
|---|---|---|
| Z ≤ 20 | 5.26 | 4.89 |
| Z 21–50 | 4.49 | 3.22 |
| Z 51–82 | 3.17 | 2.65 |
| Z > 82 | 5.47 | 4.20 |

It helps everywhere, but **least for the lightest elements**, which are the ones
whose drip line has actually been measured.

**Two warnings from this test:**
1. **Errors grow outward.** On the nuclei they were fitted to, both formulas miss
   by 2.6–3.2 MeV. On the hidden edge, they miss by 3.5–4.4 MeV, and the furthest
   step out is worst. That's a first taste of Phase 5's "error growth with
   distance".
2. **This isn't the real blind test.** The hidden nuclei are only a few neutrons
   past the rest, and for heavy elements, the most neutron-rich *measured*
   isotopes are still far from the drip line. Phase 5 does it properly.

## Result 5: the worst misses aren't touched

The biggest misses are still very neutron-rich light nuclei. The correction
changes almost nothing there:

| nucleus | before (MeV) | after (MeV) |
|---|---|---|
| boron-21 | +27.4 | +27.7 |
| boron-20 | +25.2 | +25.6 |
| carbon-22 | +20.4 | +20.7 |
| nitrogen-23 | +15.4 | +15.4 |

The formula thinks these nuclei are held far more weakly than they are. It's a
liquid-drop formula, and at around 20 particles, a nucleus is barely a "drop".
**For light elements near the drip line, neither the five-term nor the six-term
formula can be trusted.** Phase 4 (Garvey–Kelson), which works locally rather
than globally, may do better there.

---

## What to carry into later phases

1. **The six-term formula is the better model**, both in the fit and one step
   outward. Carry both forward and compare them in the blind test.
2. **Its known weak spots:** small shells (20, 28), the deformed region around
   N = 100, and light neutron-rich nuclei.
3. **Still to do before presenting:** find and cite a published source that uses
   this valence-particle form of shell correction (see D9).
