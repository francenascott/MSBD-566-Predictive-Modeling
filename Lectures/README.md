# Lectures

Week-by-week code from class. One folder per lecture, created as the course proceeds:

```
Lectures/
├── Week 01 - Predictive Modeling Framework/
├── Week 02 - Data Understanding and Quality Assessment/
├── Week 03 - Feature Engineering and Representation Learning/
└── ...
```

Each folder holds that session's notebook and, where it helps, a short note on what was covered.
The schedule below is the map; a folder appears once there is something in it.

## Naming

- Folder: `Week NN - Topic`, for example `Week 03 - Feature Engineering and Representation Learning`
- Notebook: `weekNN_topic.ipynb`, for example `week03_feature_engineering.ipynb`
- More than one notebook from a session: add a part suffix, `week03_feature_engineering_part2.ipynb`

## Schedule — Fall 2026

| Week | Date | Topic |
| --- | --- | --- |
| 1 | Aug 11, 2026 | Predictive Modeling Framework |
| 2 | Aug 18, 2026 | Data Understanding & Quality Assessment |
| 3 | Aug 25, 2026 | Feature Engineering & Representation Learning |
| 4 | Sept 1, 2026 | Advanced Regression Modeling |
| 5 | Sept 8, 2026 | Advanced Classification & Decision Analytics |
| 6 | Sept 15, 2026 | Model Validation & Performance Assessment |
| 7 | Sept 22, 2026 | Model Optimization |
| 8 | Sept 29, 2026 | Ensemble Learning |
| 9 | Oct 6, 2026 | Midterm Project Presentation |
| 10 | Oct 13, 2026 | Explainable & Interpretable AI |
| 11 | Oct 20, 2026 | Predictive Modeling for Challenging Data |
| 12 | Oct 27, 2026 | Deep Learning for Predictive Analytics |
| 13 | Nov 3, 2026 | Responsible AI & Translational Predictive Analytics |
| 14 | Nov 10, 2026 | Final Project Presentations |
| 15 | Nov 17, 2026 | Final Project Due |

## Adding a lecture

Through the GitHub web interface — no local Git install needed:

1. Open the `Lectures` folder and choose **Add file → Create new file**.
2. Type the folder and file name in the path box: `Week 03 - Feature Engineering and Representation Learning/week03_feature_engineering.ipynb`.
3. Paste or upload the notebook, then **Commit changes**.

With Git:

```bash
git clone https://github.com/francenascott/MSBD-566-Predictive-Modeling.git
cd MSBD-566-Predictive-Modeling
mkdir "Lectures/Week 03 - Feature Engineering and Representation Learning"
# copy the notebook into that folder
git add .
git commit -m "Add Week 3 lecture notebook"
git push
```
