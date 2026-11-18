# MSBD 566 — Predictive Modeling and Analytics

**Francena Scott**
Meharry Medical College · School of Applied Computational Sciences · Fall 2026

This repository is my semester-long coding portfolio for **MSBD 566: Predictive Modeling and
Analytics**. It holds the notebooks I submit for the course assignments and the code I write
during lecture, organized so that each new week becomes a new folder rather than a new pile of
files.

Every notebook here is committed **already executed** — the tables, numbers and figures in the
file are the ones produced by a top-to-bottom run, not typed in by hand. Each assignment folder
has its own `README.md` describing what the notebook contains and how to re-run it.

## Portfolio map

| Folder | Contents |
| --- | --- |
| [`Assignment 1/`](Assignment%201/) | **From a prepared dataset to a defensible baseline.** Diabetes 30-day readmission (UCI #296). Problem framing, two data-decision analyses, a design memo, and two baseline models — L2-regularized logistic regression vs. random forest — compared on a patient-grouped holdout. |
| [`Assignment 2/`](Assignment%202/) | **Validation, tuning and honest evaluation.** Parkinson's disease classification from voice (UCI #470). Leakage from record-level splitting, grouped cross-validation, regularization paths, nested tuning, and one final test-set estimate. |
| [`Lectures/`](Lectures/) | Week-by-week lecture notebooks, added as the course proceeds. |
| [`data/`](data/) | The small dataset that keeps Assignment 2 runnable, plus notes on the large files that are deliberately not committed. |

## Assignments

| # | Focus | Notebook |
| --- | --- | --- |
| 1 | From a prepared dataset to a defensible baseline | [`MSBD566_Scott_Francena_Assignment1.ipynb`](Assignment%201/MSBD566_Scott_Francena_Assignment1.ipynb) |
| 2 | Validation, tuning and honest evaluation | [`MSBD566_Scott_Francena_Assignment2.ipynb`](Assignment%202/MSBD566_Scott_Francena_Assignment2.ipynb) |

Both notebooks are self-contained reports: the written analysis (problem framing, data
decisions, design memo, evaluation, reflection) is in markdown cells, and the modeling code sits
in code cells directly beneath the discussion it supports.

## Running a notebook

```bash
python -m venv .venv
.venv\Scripts\activate        # Windows
pip install -r requirements.txt
jupyter lab
```

Open the notebook and run **Kernel → Restart & Run All**. Python 3.12, pandas, NumPy,
scikit-learn and Matplotlib; no internet access is required once the data is in place.

- **Assignment 1** reads the six prepared CSVs from `Assignment 1/data/`. Those files are derived
  artifacts, not source data, and are not committed — the scaled training matrix alone is about
  190 MB. [`Assignment 1/README.md`](Assignment%201/README.md) lists the files and explains how
  they were produced.
- **Assignment 2** reads `data/rarout/pd_speech_features.csv`, which is committed.
- Neither notebook re-splits the data, and neither touches the test set before its evaluation
  section.

## Data

The datasets are public and come from the UCI Machine Learning Repository. Provenance, licenses
and the reason the large files are excluded are documented in [`data/README.md`](data/README.md).
