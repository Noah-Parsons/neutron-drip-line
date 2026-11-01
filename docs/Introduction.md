# Start here

This guide assumes you know nothing about this project, nuclear physics, or R.
Definitions are provided in [Glossary.md](Glossary.md).

---

## 1. The project

Every atom has a tiny centre called the nucleus, made of protons and
**neutrons**.

Take an element, say oxygen, and imagine adding neutrons to its nucleus one at a
time. For a while the nucleus holds on to them. It becomes a heavier version
(an isotope) of oxygen. Then at some point, one more neutron falls
straight back out. The nucleus can't hold it.

That edge is the neutron drip line. Past it, that version of the element
**cannot exist**.

The problem: nobody has measured where that edge is for most
elements. Experiments have reached it only for the lightest ones, up to about
neon (element 10). For everything heavier, we rely on formulas that predict it,
and the formulas disagree.

This project asks:

1. Where do the formulas say the edge is?
2. **How sure can anyone be?**

## 2. Project Phases

| Phase | In plain words |
|---|---|
| 0 | Check we're reading the data correctly, using one nucleus (iron-56) |
| 1 | Build a clean table of every nucleus that has actually been measured |
| 2 | Fit a famous 1935 formula to that table, **with honest error bars** |
| 3 | Study what the formula gets wrong, and add a correction |
| 4 | Try a completely different method (Garvey–Kelson) |
| 5 | **Blind test:** fit to old data (2003), then predict nuclei measured since |
| 5b | The same blind test again, on every AME edition since 1993 |
| 6 | Put the professional models through the same blind test |
| 7 | Turn it all into a drip line **with a probability for every isotope** |
| 8 | Write it up |

All of them are done, plus a Phase 5b that was not in the original plan. The results
are in [Findings.md](Findings.md); each phase has its own document, listed below.

## 3. What this project is not

The formula (1935), the Garvey–Kelson method (1966), the published models and
the data all belong to other people. What this project adds is a careful,
honest test of them. Every choice is written down in
[Decisions.md](Decisions.md).

---

## 4. Running it 

All the work is in one file, `drip_line.ipynb`. It's a notebook: a document
mixing explanations with small blocks of code you run one at a time. The code is
written in R, a free language for statistics.

The notebook downloads the data it needs by itself (about 1 MB, from the
International Atomic Energy Agency).

### Option A: Google Colab (easiest, nothing to install)

1. Go to <https://colab.research.google.com/>.
2. **File → Upload notebook** and pick `drip_line.ipynb`.
3. **Runtime → Change runtime type → R**, then Save.
4. **Runtime → Run all.**

### Option B: on your own computer

1. Install R from <https://cran.r-project.org/>.
2. Install Python from <https://www.python.org/>, then in a terminal:
   ```bash
   pip install jupyter
   ```
3. Open R and type these two lines. They connect R to Jupyter:
   ```r
   install.packages("IRkernel")
   IRkernel::installspec()
   ```
4. In a terminal, go to the project folder and start Jupyter:
   ```bash
   jupyter notebook drip_line.ipynb
   ```
5. **Kernel → Restart & Run All.**

### The one rule

**Run the cells from the top, in order.** Later cells use results from earlier
ones. If you run a cell on its own after restarting, you'll get errors like
`object of type 'closure' is not subsettable`. That just means R has forgotten
the table `df`. Run everything from the top again.

---

## 5. What's in the repository

| File | What it is |
|---|---|
| `drip_line.ipynb` | all the code and results |
| `README.md` | the summary |
| `docs/Introduction.md` | this guide |
| `docs/Glossary.md` | every term, explained simply |
| `docs/Phase-1.md` | building and checking the dataset |
| `docs/Phase-2.md` | fitting the formula, and what it taught us |
| `docs/Phase-3.md` | finding the magic numbers, and the shell correction |
| `docs/Phase-4.md` | the local relations, and how far outward they can be trusted |
| `docs/Phase-5.md` | the blind test: predicting nuclei measured after 2003 |
| `docs/Phase-5b.md` | the same test repeated on every AME edition since 1993 |
| `docs/Phase-6.md` | the published models put through the same test |
| `docs/Phase-7.md` | the drip line, as a band with a probability |
| `docs/Findings.md` | **what the project found** — start here for the results |
| `docs/Decisions.md` | every choice made, and why |

The data files are not stored in the repository. The notebook downloads every AME
edition it needs, from 1993 to 2020.
