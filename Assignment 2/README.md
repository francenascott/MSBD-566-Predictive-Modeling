# Assignment 2 — Validation, Tuning and Honest Evaluation

**MSBD 566 — Predictive Modeling and Analytics** · Francena Scott

A classifier that detects Parkinson's disease from sustained-vowel recordings, built around the
idea that the goal is not the highest AUC but a number you can trust. Each part shows a course
concept in code and then explains what the output means.

## What is here

| File | What it is |
| --- | --- |
| `MSBD566_Scott_Francena_Assignment2.ipynb` | The submitted notebook: Parts 1–6, Q1–Q14, executed with all outputs and figures saved. |
| `../data/rarout/pd_speech_features.csv` | The dataset (5 MB), committed at the repository root so the notebook runs out of the box. |

## Data

UCI Parkinson's Disease Classification (Sakar et al., 2019; CC BY 4.0): 756 sustained-vowel
recordings from 252 subjects — 188 with Parkinson's disease, 64 healthy, three recordings per
subject. 752 acoustic features plus `subject id`, `gender` and `class` (1 = Parkinson's,
0 = healthy).

The notebook reads the CSV with `header=1` and looks for it, in order, at:

- `data/rarout/pd_speech_features.csv` — when Jupyter is started from the repository root
- `../data/rarout/pd_speech_features.csv` — when started from this folder
- `~/Downloads/pd_speech_features.csv` — last resort

To rebuild the file from scratch: download `parkinson+s+disease+classification.zip` from
[UCI dataset #470](https://archive.ics.uci.edu/dataset/470/parkinson+s+disease+classification),
extract the inner `.rar`, and keep `pd_speech_features.csv`.

## Reproducing

Run **Kernel → Restart & Run All**. A full run takes about three minutes and regenerates every
number and figure. Requirements: Python 3.12, pandas, NumPy, scikit-learn, Matplotlib. The
notebook is single-threaded throughout (`n_jobs=None`) and needs no internet access.

Wall-clock timings printed in Part 5 vary from run to run on a shared machine; every AUC, score
and count is deterministic under `random_state=42`, which is why the written answers quote scores
exactly and timings approximately.

## What the notebook does

- **Part 1** separates the unit of observation (a recording) from the unit of independence (a
  subject) and describes the feature set.
- **Part 2** compares `StratifiedKFold` with `StratifiedGroupKFold` — the same two models, four
  AUCs — and quantifies how much of the "performance" a record-level split invents.
- **Part 3** demonstrates leakage inside a pipeline, including the pure-noise experiment that
  shows what a model should score when there is nothing to learn.
- **Part 4** reads the regularization path and the learning curve to separate bias from
  variance.
- **Part 5** contrasts the naive best cross-validated score with a nested estimate, so model
  selection is scored honestly.
- **Part 6** fixes a decision threshold, compares `class_weight` with thresholding, and reports
  the final test-set estimate with its uncertainty.
