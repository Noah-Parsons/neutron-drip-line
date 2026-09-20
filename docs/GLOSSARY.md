# Glossary

Every term used in this project. Alphabetical.

---

**A (mass number):** the total count of protons plus neutrons in a nucleus.
Iron-56 has A = 56.

**AME (Atomic Mass Evaluation):** the official collection of measured nuclear
masses, used by every professional group. This project uses the 2020 edition,
**AME2020**. Earlier editions (2003, 2012, 2016) make the blind test possible.

**Asymmetry term:** the part of the formula that penalises a nucleus for having
unequal numbers of protons and neutrons. It matters most near the drip line,
where nuclei have far more neutrons than protons.

**Binding energy (B):** the energy you'd need to pull a nucleus completely
apart into separate protons and neutrons. Bigger means more tightly held
together.

**Binding energy per nucleon (B/A):** binding energy divided by the number of
particles. It lets you compare a small nucleus fairly with a big one. It's about
8 MeV for most nuclei.

**Blind test:** fitting a model using only old data, then checking how well it
predicts data it never saw. It is the only way to tell a model that
*understands* nuclei from one that has just *memorised* the table.

**χ²/dof (chi-squared per degree of freedom):** a single number saying how well
a fit matches the data **compared with the error bars**. About 1 means "misses
by exactly as much as the measurement errors". Much bigger than 1 means the
model is missing something real.

**Correlation:** how much two fitted numbers move together. 1 means perfectly
together, 0 means independently.

**Coulomb term:** the part of the formula for protons pushing each other apart
(they're all positively charged). It uses Z(Z−1), not Z², because a proton
doesn't push itself.

**Covariance matrix:** a table holding the error bar of every fitted constant
**and** how each pair of constants is tied together. Without it, error bars on
predictions come out far too small.

**Design matrix (X):** a table with one row per nucleus and one column per
constant in the formula. Each entry is the number that constant gets multiplied
by for that nucleus.

**Drip line (neutron drip line):** the edge of existence. For each element, it's
the heaviest isotope that can still hold on to its neutrons.

**Estimated value (extrapolated value):** a number in the AME that is **not** a
measurement. It is a guess made by the AME team, marked with `#`. This project
throws all of them out.

**Floor (weighting floor):** a minimum error bar. Any nucleus measured more
precisely than the floor is treated as if its error were the floor, so no single
ultra-precise measurement can dominate the fit.

**Isotope:** versions of the same element with different numbers of neutrons.
Carbon-12 and carbon-14 are isotopes of carbon.

**keV, MeV:** units of energy. 1 MeV = 1000 keV. The data files use keV, so the
project works in keV throughout.

**Least squares:** the standard way to fit a formula to data. It picks the
constants that make the squared misses, added up, as small as possible.

**Liquid drop model:** the idea behind the formula. It treats a nucleus like a
drop of liquid, where each particle only feels its immediate neighbours.

**Magic numbers:** 2, 8, 20, 28, 50, 82, 126. Nuclei with exactly these numbers
of protons or neutrons are held together more tightly than the formula predicts.
It's like a completely filled shell of electrons, but inside the nucleus.

**Mass excess (Δ):** what the data tables actually list. It's the nucleus's mass
minus A atomic mass units, written as an energy. Binding energy is computed from
it.

**N:** the number of neutrons.

**Nucleon:** a proton or a neutron.

**Nuclide:** one specific nucleus, fixed by both its proton count and its
neutron count.

**Pairing term:** the part of the formula that rewards even numbers of protons
and neutrons (particles like to pair up). It has three cases: even-even gets a
bonus, odd-odd gets a penalty, and odd A gets nothing.

**Residual:** measured minus predicted. It's how much the formula missed by, for
one nucleus.

**rms (root-mean-square):** a typical size of the residuals. Square them all,
average, then square-root.

**S2n (two-neutron separation energy):** the energy needed to remove the last
two neutrons. **Positive: the nucleus holds them. Negative: it can't, so it's
past the drip line.**

**Sn (one-neutron separation energy):** the same, for one neutron.

**Semi-empirical mass formula (SEMF):** the five-term formula from 1935 for the
binding energy of any nucleus. "Semi-empirical" means its shape comes from
physics but its five constants come from fitting data.

**Standard error:** the error bar on a fitted constant.

**Surface term:** the part of the formula for particles on the outside of the
nucleus, which have fewer neighbours and so are held less tightly.

**Volume term:** the biggest part of the formula. Every particle adds roughly
the same binding.

**Weighting:** deciding how much each nucleus counts in the fit. **Uniform**
weighting: all equal. **Inverse-variance** weighting: precisely measured nuclei
count more.

**Z (atomic number):** the number of protons. It decides which element it is.
Iron always has Z = 26.

---

*Added in Phase 3:*

**Deformed nucleus:** a nucleus squashed or stretched out of a sphere, often
halfway between two magic numbers. The simple formulas here assume a sphere.

**Hidden set (held-out set):** nuclei deliberately kept out of a fit so the
formula can be tested on them afterwards.

**Shell (nuclear shell):** a group of energy levels protons or neutrons fill up,
like electron shells in chemistry. A magic number is a full shell.

**Shell correction:** an extra term added to the formula to account for shells.
In this project: a_sh × [f(Z) + f(N)], zero at magic numbers and largest
mid-shell.

**Valence particles:** the protons or neutrons past the last full shell.

---

*Added in Phase 4:*

**Chaining:** using a prediction as an input to the next prediction. It is how
the local relations reach nuclei that have no measured neighbours, and it is why
their errors grow with every step outward.

**Garvey–Kelson relation:** a rule saying that six particular nuclei, close
together on the chart, have binding energies that cancel out to nearly zero when
added with alternating signs. Two arrangements work: the **transverse** and the
**longitudinal** relation. Published by Garvey and Kelson in 1966.

**Global model:** a single formula fitted to the whole chart at once, like the
five- and six-term formulas here. The opposite of a **local relation**.

**Local relation:** a rule that only involves nuclei sitting next to each other.
It says nothing about the chart as a whole, and it is far more accurate where it
applies.

**Power law:** a relationship of the form y = a × x^b. The error of a chained
prediction follows one, with b = 1.37.

**Route:** one way of reaching an unknown nucleus with a relation — which of the
two relations, and which of its six cells is the unknown. Twelve in total.

**Unreachable nucleus:** one that no relation can predict, because it does not
have five measured neighbours in any of the twelve arrangements.

---

*Added in Phase 5:*

**AME2003:** the 2003 edition of the Atomic Mass Evaluation. Standing in for
"what was known then", it makes the blind test possible.

**Bias (systematic error):** a miss that leans one way. If a formula's errors
average out to zero it is unbiased, whatever their size; if they average +1.3 MeV
it is getting something wrong in one direction.

**Blind (of a result):** obtained without the answers having been visible at any
point, including while choosing the method. A result can be blind in its numbers
and not blind in its shape, which is why the six-term formula is labelled as not
blind in Phase 5.

**Coverage:** the fraction of predictions that actually land inside their stated
error bars. A 1σ band should cover about 68 %, a 2σ band about 95 %. Coverage is
how you find out whether an error bar means anything.

**Gap fill:** a nucleus measured later that sits *inside* the range already
measured, rather than beyond its edge. Easier than extrapolating, and counted
separately for that reason.

**Test set:** the nuclei kept out of the fit and used to score it. Here: the 326
measured in AME2020 but not in AME2003.

**Tail (of a distribution):** the rare large values. A method can have a good
median and a terrible tail, and for the drip line the tail is what matters.
