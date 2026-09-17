# Phases 0 and 1: building and checking the dataset

**Goal:** a clean table of every nucleus that has **actually been measured**,
with its binding energy and separation energies, checked against the official
numbers.

**Status:** done.

---

## Step 1: get the data

The notebook downloads `mass_1.mas20.txt`, the AME2020 mass table. It's a plain
text file, but with no commas. Each value sits at **fixed character positions**
on the line, as listed in the file's header.

| characters | contents |
|---|---|
| 5–9 | N (neutrons) |
| 10–14 | Z (protons) |
| 15–19 | A (total) |
| 29–42 | mass excess, keV |
| 43–54 | its uncertainty, keV |
| 55–67 | the AME's own binding energy per nucleon (used only for checking) |

## Step 2: throw out the guesses

Some numbers in the file are **not measurements**. The AME team estimated them,
and marked them with `#`. If we kept them, we would be fitting our formula to
someone else's formula, not to nature.

| | count |
|---|---|
| nuclei in the file | 3,558 |
| **estimates, removed** | **1,008** |
| **measured, kept** | **2,550** |

## Step 3: binding energy

From the mass excess Δ, the binding energy is

> B = Z × 7288.971 keV + N × 8071.318 keV − Δ

The two numbers are the mass excess of a hydrogen atom and of a free neutron.
We use **hydrogen atom** rather than a bare proton because the tables list
whole-atom masses, including electrons. Each hydrogen atom brings one electron,
so the electrons cancel out.

## Step 4: check it (Phase 0)

**Iron-56, by hand:** 8790.356 keV per nucleon. The manual expects about 8790.
✔

**Every nucleus:** our B/A minus the AME's own B/A is at most **0.0001 keV**,
for all 2,550 nuclei. The small difference is just rounding. **No nucleus is
off by even 1 keV.** ✔

This single check proves the parsing, the units and the signs are all right.

## Step 5: the binding energy curve

Plotting B/A against A gives the famous curve: a steep rise, a peak, then a slow
decline.

The top three nuclei:

| nucleus | B/A (keV) |
|---|---|
| **nickel-62** | **8794.556** |
| iron-58 | 8792.253 |
| iron-56 | 8790.356 |

**Nickel-62 is the most tightly bound nucleus**, not iron-56 as often said. It
is iron-56 that has the lowest mass *per nucleon*, which is a slightly different
measure, and that's where the popular claim comes from.

## Step 6: separation energies

- **Sn** = B(this nucleus) − B(one fewer neutron)
- **S2n** = B(this nucleus) − B(two fewer neutrons)

Both need the neighbour to have been measured too, so not every nucleus gets
one:

| | count |
|---|---|
| Sn computable | 2,393 of 2,550 |
| S2n computable | 2,301 of 2,550 |

## Step 7: the cross-check

The AME team publish their own S2n values in a second file, `rct1.mas20.txt`. We
read it and lined it up nucleus by nucleus with ours.

| | result |
|---|---|
| measured S2n in the AME file | 2,301 |
| nuclei where we have S2n but the AME doesn't, or the other way round | **0** |
| largest difference between our S2n and theirs | **0.001 keV** |

**Same nuclei, same numbers.** That confirms the neighbour lookup and the
subtraction, not just the binding energies. (The 0.001 keV is rounding: their
file prints four decimal places.)

We didn't separately check Sn, which is listed in a third file, `rct2`. Sn uses
the same binding energies and the same kind of lookup, both confirmed above.

## Step 8: nuclei already past the drip line

Nine measured nuclei have **negative S2n**. They can't hold their last two
neutrons; they exist for an instant as short-lived resonances.

| nucleus | Z | N | S2n (keV) |
|---|---|---|---|
| hydrogen-5 | 1 | 4 | −1800 |
| hydrogen-6 | 1 | 5 | −1112 |
| helium-10 | 2 | 8 | −1445 |
| lithium-13 | 3 | 10 | −110 |
| beryllium-15 | 4 | 11 | −24 |
| beryllium-16 | 4 | 12 | −1350 |
| boron-20 | 5 | 15 | −1466 |
| boron-21 | 5 | 16 | −2470 |
| oxygen-26 | 8 | 18 | −18 |

All of them are light, up to oxygen (Z = 8). This fits with the drip line having
been reached experimentally only for the lightest elements.
