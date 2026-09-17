# Decisions log

Every choice that could change a result goes here: what was chosen, why, and
what else was tried. A careful reader should never have to guess.

Newest at the bottom.

---

### D1. Remove every estimated value (Phase 1)

**Chose:** drop every nucleus whose mass excess, or its uncertainty, contains a
`#`. That removed 1,008 of 3,558.
**Why:** estimates are the AME team's guesses, not measurements. Fitting to them
means fitting to another model. It would also poison the blind test.

### D2. Work in keV throughout (Phase 1)

**Chose:** keep all energies in keV, as in the data files. Constants are divided
by 1000 only when printed.
**Why:** mixing keV and MeV creates errors of exactly 1000× that are easy to
miss.

### D3. Use hydrogen-atom and free-neutron mass excesses (Phase 1)

**Chose:** Δ(¹H) = 7288.971064 keV and Δ(n) = 8071.31806 keV. These are the
AME2020 values, typed in with a few fewer digits than the file lists.
**Why:** the tables list whole-atom masses. Using the hydrogen atom makes the
electrons cancel.
**Checked:** B/A agrees with the AME's own column to 0.0001 keV for every
nucleus.

### D4. S2n is the main drip line test (Phase 1)

**Chose:** S2n rather than Sn.
**Why:** pairing makes Sn zigzag between even and odd neutron numbers. S2n steps
by two and avoids that. Places where the two disagree will be reported
separately.

### D5. Fit only nuclei with A ≥ 20 (Phase 2)

**Chose:** 2,455 nuclei with A ≥ 20; 95 lighter ones left out.
**Why:** the liquid-drop picture behind the formula barely applies to very small
nuclei. The cutoff of 20 is the one the project manual suggests. It was chosen
before fitting.
**Also tried:** all nuclei (except the free neutron and hydrogen-1). Constants
moved by about 9 error bars, and the typical miss rose from 3.2 to 3.7 MeV. See
[PHASE_2.md](PHASE_2.md), Result 5.

### D6. Main fit uses uniform weighting; four floors reported alongside (Phase 2)

**Chose:** uniform weighting as the reference fit. Inverse-variance weighting
with floors of 1, 10, 100 and 1000 keV is reported next to it.
**Why:** the formula misses by about 3,000 keV and measurements are good to
about 6 keV. So nearly all the scatter comes from the formula, not the
measurements, and every nucleus's miss is roughly the same size whatever its
measurement error. Uniform weighting says exactly that. No one floor can be
justified, so all four are shown.
**Consequence:** the spread across weightings (12–16 error bars) is reported as
a real part of the uncertainty.

### D7. Scale weighted covariance by χ²/dof (Phase 2)

**Chose:** report C = (XᵀWX)⁻¹ × χ²/dof, not the raw (XᵀWX)⁻¹. For uniform
weighting this is the usual s²(XᵀX)⁻¹.
**Why:** the raw version assumes the formula misses only by measurement error,
which is false by a factor of hundreds (χ²/dof = 875 to 1,781,000). Without
scaling, the error bars would be up to 1,000× too small.
**Known limit:** the residuals are not random (they spike at magic numbers), so
even the scaled error bars are probably too small. Phase 5 tests this directly.

### D8. The blind test must not borrow from these AME2020 fits (for Phase 5)

**Rule:** Phase 5 fits to AME2003 and tests on nuclei first measured after 2003.
The A ≥ 20 cutoff and the weighting choices were settled while looking at AME2020
fits, which include those later nuclei. To stop that from leaking into the test:
- Phase 5 uses the **same fixed cutoff (A ≥ 20)** and reports **every weighting
  variant**, not whichever one predicts best.
- No new choice (a different cutoff, a new floor, dropping outliers) may be made
  after seeing any Phase 5 test result. If one turns out to be needed, it is
  reported as a separate, clearly labelled extra analysis.
