# Start here

This guide assumes you know nothing about this project, nuclear physics or R.
Words you might not know are explained in [GLOSSARY.md](GLOSSARY.md).

---

## 1. The project in two minutes

Every atom has a tiny centre called the **nucleus**, made of **protons** and
**neutrons**.

Take an element, say oxygen, and imagine adding neutrons to its nucleus one at a
time. For a while the nucleus holds on to them. It becomes a heavier version
(an **isotope**) of oxygen. Then at some point, one more neutron just falls
straight back out. The nucleus can't hold it.

That edge is the **neutron drip line**. Past it, that version of the element
**cannot exist**.

Here's the problem: **nobody has measured where that edge is for most
elements.** Experiments have reached it only for the lightest ones, up to about
neon (element 10). For everything heavier, we rely on formulas that predict it,
and the formulas disagree.

This project asks:

1. Where do the formulas say the edge is?
2. **How sure can anyone be?**

The second question is the real one.

## 2. How the answer is built

Think of it as a staircase. Each step stands on the one below.

| Phase | In plain words |
|---|---|
| 0 | Check we're reading the data correctly, using one nucleus (iron-56) |
| 1 | Build a clean table of every nucleus that has actually been measured |
| 2 | Fit a famous 1935 formula to that table, **with honest error bars** |
| 3 | Study what the formula gets wrong, and add a correction |
| 4 | Try a completely different method (Garvey–Kelson) |
| 5 | **Blind test:** fit to old data (2003), then predict nuclei measured since |
| 6 | Put the professional models through the same blind test |
| 7 | Turn it all into a drip line **with a probability for every isotope** |
| 8 | Write it up |

Done so far: **Phases 0, 1, 2 and 3.** See [PHASE_1.md](PHASE_1.md),
[PHASE_2.md](PHASE_2.md) and [PHASE_3.md](PHASE_3.md).

## 3. What this project is not

The formula (1935), the Garvey–Kelson method (1966), the published models and
the data all belong to other people. What this project adds is a **careful,
honest test** of them. Every choice is written down in
[DECISIONS.md](DECISIONS.md).

---

## 4. Run it yourself

All the work is in one file, **`drip_line.ipynb`**. It's a notebook: a document
mixing explanations with small blocks of code you run one at a time. The code is
written in **R**, a free language for statistics.

The notebook downloads the data it needs by itself (about 1 MB, from the
International Atomic Energy Agency).

### Option A: Google Colab (easiest, nothing to install)

1. Go to <https://colab.research.google.com/>.
2. **File → Upload notebook** and pick `drip_line.ipynb`.
3. **Runtime → Change runtime type → R**, then Save.
4. **Runtime → Run all.**

### Option B: on your own computer

1. Install **R** from <https://cran.r-project.org/>.
2. Install **Python** from <https://www.python.org/>, then in a terminal:
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
| `docs/START_HERE.md` | this guide |
| `docs/GLOSSARY.md` | every term, explained simply |
| `docs/PHASE_1.md` | building and checking the dataset |
| `docs/PHASE_2.md` | fitting the formula, and what it taught us |
| `docs/PHASE_3.md` | finding the magic numbers, and the shell correction |
| `docs/DECISIONS.md` | every choice made, and why |

The data files (`*.mas20.txt`) are **not** stored in the repository. The
notebook downloads them.
