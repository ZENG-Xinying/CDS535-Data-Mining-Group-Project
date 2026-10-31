# ZHANG Jiaming — Model Evaluation & Cross-Dataset Comparison

CDS535 Data Mining Group Project · Weka · Mushroom & Ionosphere

## My role

I served as the **evaluation lead**. While other members prepared the datasets and
built the classifiers, I was responsible for evaluating every model under one consistent
design, comparing the four classifiers across the two datasets, and running the
statistical significance tests.

## What I did

1. Applied one consistent evaluation design to all classifiers:
   **10-fold stratified cross-validation** and an independent **66%/34% split** (seed = 1).
2. Compared four classifiers — **J48, RandomForest, Logistic, SMO** — on Mushroom and
   Ionosphere using accuracy, precision, recall, F1, ROC-AUC and Kappa.
3. Checked the leakage-control setup: data-driven preprocessing (standardization and
   feature selection) is fitted **inside each fold**, never on the full dataset.
4. Ran the Weka Experimenter **paired corrected t-test** (two-tailed, 0.05) to decide
   which observed differences are statistically significant.
5. Wrote the cross-dataset comparison and the personal report and slides.

## Key results

- **Mushroom:** all four classifiers reach 100% accuracy and AUC 1.00, so the result is
  reported as a **tie**, not a ranking.
- **Ionosphere:** RandomForest has the highest accuracy (92.88%) and AUC (0.98).
  The accuracy differences are **not significant** (0/2/0), but RandomForest's ROC-AUC is
  **significantly higher** than J48 (1/1/0).
- Adding feature selection or increasing the number of trees produced **no stable
  improvement**.

## Repository structure

| Folder | Contents |
|---|---|
| `01_summary` | `D_eval_summary.csv` — full per-run metrics for every classifier, protocol and dataset |
| `02_experimenter` | Weka Experimenter config (`exp_setup.exp`), the class-last Mushroom input, and the new-version results (`new1.arff`) |
| `03_figures` | Accuracy/AUC comparison chart, significance-test screenshot and dataset loading screenshots |
| `04_personal` | Personal slides `D.pptx` and the personal report `D_Report.docx` |

## How to reproduce

- Open `02_experimenter/exp_setup.exp` in the Weka Experimenter to inspect the exact
  classifiers, datasets and test options.
- `02_experimenter/new1.arff` stores the per-run output produced by that setup.
- `01_summary/D_eval_summary.csv` provides the readable, consolidated metrics.
