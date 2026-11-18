# Assignment 1 — From a Prepared Dataset to a Defensible Baseline

**MSBD 566 — Predictive Modeling and Analytics** · Francena Scott

The notebook is both the code and the report: Parts A–C and F are written analysis in markdown,
Parts D–E are executed code with the evaluation written up beside it.

## What is here

| File | What it is |
| --- | --- |
| `MSBD566_Scott_Francena_Assignment1.ipynb` | The submitted notebook: Parts A–F, executed with all outputs and figures saved. |
| `data/` | Not committed — the six prepared CSVs are derived artifacts and total about 260 MB. See below. |

## The data files

The notebook starts from the six model-ready files produced by the Week 2–3 Data Preparation
step, and never re-splits them:

| File | Contents |
| --- | --- |
| `X_train.csv`, `X_test.csv` | Unscaled model matrices, 121 features. |
| `X_train_scaled.csv`, `X_test_scaled.csv` | The same matrices after `StandardScaler`, fit on the training rows only. |
| `y_train.csv`, `y_test.csv` | Binary target: 1 = readmitted within 30 days, 0 = otherwise. |

Two companion files — `groups_train.csv`, `groups_test.csv` — carry the patient IDs so the
notebook can prove the split has zero patient overlap.

The split recorded in `data/prep_manifest.json`:

| | Train | Test |
| --- | --- | --- |
| Encounters | 79,473 | 19,867 |
| Patients | 56,036 | 13,951 |
| Positive rate (30-day readmission) | 11.39% | 11.39% |

Starting from 101,766 raw encounters, 2,423 death/hospice discharges and 3 `Unknown/Invalid`
gender rows were removed, leaving 99,340 modelled encounters; seven constant columns and three
columns with ≥40% missing (`weight`, `payer_code`, `medical_specialty`) were dropped.

**Why `data/` is not in the repository.** `X_train_scaled.csv` is about 188 MB on its own, over
GitHub's 100 MB per-file limit, and every file in the folder is reproducible from the raw UCI
extract. To re-run the notebook, drop the six CSVs (and the two `groups_*.csv` files) into
`Assignment 1/data/`; the loader finds them whether Jupyter is started from the repository root
or from this folder.

Source: [Diabetes 130-US Hospitals for Years 1999–2008](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008),
UCI Machine Learning Repository (dataset #296).

## Reproducing

1. Put the prepared CSVs in `Assignment 1/data/` as described above.
2. Open the notebook and run **Kernel → Restart & Run All**. A full run takes about three
   minutes and regenerates every number and figure.
3. Requirements: Python 3.12, pandas, NumPy, scikit-learn, Matplotlib. No internet access is
   needed once the data is in place.

## What the notebook does

- **Part A** frames the decision: which discharged patients a transitional-care program should
  enroll, and what a measurable success criterion looks like.
- **Part B** analyzes two preparation decisions — the patient-grouped split and the ICD-9
  chapter grouping — including the specific ways each could hurt performance or fairness.
- **Part C** is the design memo, written before any model is fit: the two model families, the
  metrics (ROC-AUC, PR-AUC, precision/recall/F1 at a threshold, precision at 10% capacity, Brier
  score), and the overfitting guard.
- **Part D** implements L2-regularized logistic regression and a random forest on the same
  split, and prints their test-set predictions.
- **Part E** reports and compares the metrics, chooses the operating threshold on out-of-fold
  training predictions only, bootstraps a confidence interval for the AUC difference, and
  recommends one model.
- **Part F** reflects on what more time or data would change.
