# Data

The repository keeps notebooks, not raw data. The one dataset small enough to commit is the
Parkinson's file, because leaving it out would make Assignment 2 fail on the first run.

| Dataset | Used by | Location | Committed? |
| --- | --- | --- | --- |
| Diabetes 130-US Hospitals for Years 1999–2008 (UCI #296) | Assignment 1 | `Assignment 1/data/` | No — the derived matrices total about 260 MB and the scaled training matrix alone is 188 MB, over GitHub's per-file limit |
| Parkinson's Disease Classification (UCI #470) | Assignment 2 | `data/rarout/pd_speech_features.csv` | Yes — 5 MB, CC BY 4.0 |

## Assignment 1 — diabetes readmission

The notebook starts from six model-ready files produced by the Week 2–3 Data Preparation step:
`X_train.csv`, `X_test.csv`, `X_train_scaled.csv`, `X_test_scaled.csv`, `y_train.csv`,
`y_test.csv`, plus `groups_train.csv` / `groups_test.csv` (patient IDs) and
`prep_manifest.json`. They are omitted here because they are derived artifacts — a one-hot
encoded, scaled copy of the raw table — and because the largest of them cannot be pushed to
GitHub at all.

To reproduce: download
[Diabetes 130-US Hospitals](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008)
(UCI #296, `diabetic_data.csv` plus `IDS_mapping.csv`), run the Week 2–3 preparation notebook to
write the six files into `Assignment 1/data/`, then run the assignment notebook. The split
recorded in the manifest is a patient-grouped, stratified 80/20 holdout with zero patient
overlap: 79,473 training encounters from 56,036 patients, 19,867 test encounters from 13,951
patients, 11.39% positive in both.

## Assignment 2 — Parkinson's disease classification

`data/rarout/pd_speech_features.csv` is the UCI Parkinson's Disease Classification dataset
(Sakar et al., 2019), 756 sustained-vowel recordings from 252 subjects, licensed CC BY 4.0. The
inner archive from UCI is a `.rar`; the CSV inside it is committed here unchanged.

Source: [UCI dataset #470](https://archive.ics.uci.edu/dataset/470/parkinson+s+disease+classification).
