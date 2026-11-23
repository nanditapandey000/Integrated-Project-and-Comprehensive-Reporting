# Integrated-Project-and-Comprehensive-Reporting

# Week 6 — Integrated Capstone Project

**Project:** Predicting LendingClub Loan Defaults — A Complete Data Science Pipeline
**Focus:** Integration of all six weeks into one comprehensive, reproducible project
**Dataset:** LendingClub LoanStats3a (42,535 loans, 2007–2011)
**Report date:** November 2026

---

## 1. Objective

Week 6 is the capstone: integrate every skill developed over the previous five weeks
into a single, coherent data-science project that addresses a real-world problem
through systematic analysis and clear documentation. The deliverable is a complete
project that goes through the full pipeline — data collection and cleaning, exploratory
analysis, statistical modeling, machine learning, and data visualization — and stands
as a professional example of reproducible data science.

The capstone does not introduce new models or new data. It synthesizes the findings
of Weeks 1–5 into a unified narrative, documents the trade-offs, and discusses the
implications for a hypothetical lender or investor.

---

## 2. Deliverables

### Main report

| File | Location | Purpose |
|------|----------|---------|
| **Week6_Integrated_Capstone_Project.pdf** | `download/` | 16-page capstone report (cover + body, bronze/gold palette) |

### Supporting files (from Weeks 1–5, all included)

| File | Location | Week | Purpose |
|------|----------|------|---------|
| `cleaned_dataset.csv` | `download/` | W1 | Final cleaned dataset (42,535 × 55) |
| `week1_data_cleaning.ipynb` | `download/` | W1 | Cleaning notebook |
| `week2_eda.ipynb` | `download/` | W2 | EDA notebook |
| `Week3_Statistical_Modeling_Report.pdf` | `download/` | W3 | Statistical analysis report |
| `week3_statistical_modeling.ipynb` | `download/` | W3 | Statistical modeling notebook |
| `Week4_ML_Model_Development_Report.pdf` | `download/` | W4 | Machine learning report |
| `week4_ml_model_development.ipynb` | `download/` | W4 | ML pipeline notebook |
| `Week5_Data_Visualization_Report.pdf` | `download/` | W5 | Visualization portfolio report |
| `week5_visualization_portfolio.ipynb` | `download/` | W5 | Visualization notebook |
| **`week6_integrated_capstone.ipynb`** | `download/` | W6 | Integrated capstone notebook (single entry point) |
| `best_model.joblib` | `data/` | W4 | Serialized champion model |
| 10 week-3 figures | `data/week3_figures/` | W3 | Statistical diagnostic plots |
| 6 week-4 figures | `data/week4_figures/` | W4 | ML evaluation plots |
| 10 week-5 figures | `data/week5_figures/` | W5 | Annotated visualization portfolio |
| 1 capstone synthesis figure | `data/week6_figures/` | W6 | Four-panel synthesis dashboard |

### README files (documentation layer)

| File | Purpose |
|------|---------|
| **README_Week3.md** | Documents the Week 3 statistical-modeling deliverable |
| **README_Week4.md** | Documents the Week 4 machine-learning deliverable |
| **README_Week5.md** | Documents the Week 5 visualization-portfolio deliverable |
| **README_Week6.md** | This file — master integration guide |

---

## 3. The Project

### The problem

> **Will a given LendingClub loan default?**

A binary classification problem with a 15.12% positive rate (6,431 defaults out of
42,535 loans). Accurate default prediction matters operationally: LendingClub's
business model depends on pricing risk correctly into the interest rate, and investors
need to construct portfolios that balance yield against loss.

### The pipeline

```
Raw LoanStats3a (42,551 × 74)
    │
    ▼  Week 1 — Data Cleaning
Cleaned dataset (42,535 × 55, 0 nulls in modeling features)
    │
    ▼  Week 2 — Exploratory Data Analysis
EDA stats + figures; default rate, distributions, correlations
    │
    ▼  Week 3 — Statistical Modeling
5 hypotheses tested; baseline logistic regression (23 features);
OLS decomposition of interest rate
    │
    ▼  Week 4 — Machine Learning
4 models compared (LogReg, RF, XGBoost, LightGBM);
champion = Logistic Regression (ROC-AUC 0.697, PR-AUC 0.288)
    │
    ▼  Week 5 — Data Visualization
10-figure narrative portfolio; storyboard arc from growth to interactions
    │
    ▼  Week 6 — Integration (this report)
Comprehensive capstone synthesizing all findings
```

---

## 4. Headline Findings

### Finding 1 — Loan grade dominates default prediction

Default rates rise monotonically from **6.0% (grade A) to 33.8% (grade G)** — a 5.5×
spread. Grade alone explains ~93% of the variance in the assigned interest rate. No
other feature comes close. (Week 3, Figure 3; Week 5, Figures 3 and 8.)

### Finding 2 — The simplest model wins

A tuned logistic regression achieves **ROC-AUC = 0.697, PR-AUC = 0.288**,
outperforming Random Forest, XGBoost, and LightGBM on the metric we optimized for
(PR-AUC). The reason: the dominant predictive feature (grade) is monotonic in the
target, and linear models capture monotonic relationships efficiently. (Week 4.)

### Finding 3 — Risk compounds at intersections

The riskiest cell in the purpose × grade matrix — **small_business loans in grade G —
defaults at 50%**, far above either dimension in isolation. This is exactly the kind
of interaction that tree-based models are designed to exploit, and the fact that they
did not decisively win tells us the interaction, while real, is small relative to the
main grade effect. (Week 5, Figure 10.)

### Finding 4 — The predictive ceiling is real

No model in our search exceeds PR-AUC ≈ 0.29. Single continuous features (DTI,
loan-to-income, interest rate) overlap heavily between paid and defaulted loans. The
signal is distributed across many features, and the grade aggregates them — but no
single feature separates defaulters from non-defaulters. (Week 5, Figures 7, 9.)

---

## 5. Capstone Report Structure (16 pages)

| Page | Section |
|------|---------|
| 1 | Cover (bronze/gold, 6-stage pipeline diagram + 5 KPI stats) |
| 2 | Table of contents (auto-generated) |
| 3 | 1. Executive Summary |
| 4 | 2. Introduction and Problem Definition |
| 5 | 3. Methodology (pipeline overview table) |
| 6 | 3. Methodology (continued — preprocessing, stats, ML, viz) |
| 7 | 4. Analysis and Results — the grade signal (Figures 4.1, 4.2) |
| 8 | 4.2 Statistical hypothesis testing (Table 4.1) |
| 9 | 4.3 ML model comparison (Table 4.2, Figure 4.3) |
| 10 | 4.4 Feature importance (Figure 4.4) |
| 11 | 4.5 The interaction effect (Figure 4.5) |
| 12 | 4.6 Why the predictive ceiling is real (Figure 4.6) |
| 13 | 5. Discussion — implications for lender and investor |
| 14 | 5.3 Limitations |
| 15 | 5.4 Suggestions for further work |
| 16 | 6. Conclusion |

---

## 5.1 Capstone Notebook

The companion [**week6_integrated_capstone.ipynb**](week6_integrated_capstone.ipynb)
is the single entry point for reviewing the integrated analysis. Rather than re-running
every model from scratch (those live in the weekly notebooks), it **integrates** the six
phases into one runnable narrative.

**Structure (24 cells: 13 markdown + 11 code):**

| Section | Content |
|---------|---------|
| 1. Environment setup | Palette, fonts, seeds |
| 2. Phase 1 — Data cleaning (recap) | Load cleaned dataset, derive `is_default` |
| 3. Phase 2 — EDA (recap) | Grade ladder (the dominant signal) |
| 4. Phase 3 — Statistical modeling (recap) | H2 (grade vs rate), H5 (purpose interaction) |
| 5. Phase 4 — Machine learning (recap) | Load saved Week-4 metrics, model comparison |
| 6. Phase 5 — Visualization (recap) | DTI overlap + risk matrix |
| 7. Phase 6 — Capstone synthesis | Four-panel synthesis dashboard |
| 8. Conclusion | Four headline findings + one-sentence summary |

**Verified:** executes end-to-end in <30 seconds with 0 errors, renders 5 inline figures,
and saves `data/week6_figures/capstone_synthesis.png` (the four-panel synthesis dashboard).

> **Reproducibility.** Upload `cleaned_dataset.csv` to the working directory and Run All.
> Optional: the Week-4 model comparison loads `week4_stats.json` if available (shipped in
> `data/`). Like the other weekly notebooks, it ships as a clean template (no outputs) —
> Run All to populate.

---

## 6. Quality Checks Passed

- `pdf.py font.check` — all fonts embedded, 0 issues.
- `pdf.py toc.check` — TOC populated, 0 errors.
- `pdf_qa.py` — **11/11 passed, 0 errors**. Page size consistent (595.3 × 841.9 pt).
- All 6 embedded figures placed on correct pages, within margins.
- No leftover placeholders (XXX, TODO, NaN, 【, undefined).
- All bullet characters render correctly (no `(cid:127)` artifacts).
- Cover validated (0 overlaps, 0 zone overflows).

---

## 7. Reproducibility

The entire project is reproducible from the raw CSV. The execution order:

```bash
# Week 1 — Data cleaning
python3 -I scripts/week1_cleaning.py           # produces download/cleaned_dataset.csv

# Week 2 — EDA
python3 -I scripts/week2_eda.py                # produces data/eda_stats.json + eda_figures/

# Week 3 — Statistical modeling
python3 -I scripts/week3_modeling.py           # produces data/week3_stats.json + week3_figures/
python3 -I scripts/build_week3_body.py         # produces scripts/body_week3.pdf

# Week 4 — Machine learning
python3 -I scripts/week4_ml_pipeline.py        # produces data/week4_stats.json + best_model.joblib
python3 -I scripts/week4_feature_importance.py  # produces feature-importance figure
python3 -I scripts/build_week4_body.py         # produces scripts/body_week4.pdf

# Week 5 — Visualization
python3 -I scripts/week5_visualizations.py    # produces data/week5_stats.json + week5_figures/
python3 -I scripts/build_week5_body.py         # produces scripts/body_week5.pdf

# Week 6 — Capstone integration
python3 -I scripts/build_week6_notebook.py      # produces download/week6_integrated_capstone.ipynb
python3 -I scripts/build_week6_body.py         # produces scripts/body_week6.pdf
```

Each week's cover + body are merged into the final PDF in `download/`. The
notebooks in `download/` can be run independently in Colab by uploading
`cleaned_dataset.csv` to the working directory.

### Environment

- **Python 3.12**, pandas 2.2, scikit-learn 1.5, matplotlib 3.9, seaborn 0.13.
- Optional: `xgboost`, `lightgbm`, `optuna` for the Week-4 model comparison.
- `squarify` for the Week-5 treemap.
- ReportLab for all PDF generation.
- Fonts: FreeSerif (body), Playfair Display + Inter (covers), NotoSerifSC (bullet
  glyphs and CJK fallback).

---

## 8. Codebase Organization

```
my-project/
├── download/                      # ← All deliverables the user sees
│   ├── cleaned_dataset.csv         #    Week 1 final dataset
│   ├── week1_data_cleaning.ipynb   #    Week 1 notebook
│   ├── week2_eda.ipynb             #    Week 2 notebook
│   ├── Week3_Statistical_Modeling_Report.pdf
│   ├── week3_statistical_modeling.ipynb
│   ├── Week4_ML_Model_Development_Report.pdf
│   ├── week4_ml_model_development.ipynb
│   ├── Week5_Data_Visualization_Report.pdf
│   ├── week5_visualization_portfolio.ipynb
│   ├── Week6_Integrated_Capstone_Project.pdf   # ← capstone report
│   ├── week6_integrated_capstone.ipynb          # ← capstone notebook (single entry point)
│   ├── README_Week3.md
│   ├── README_Week4.md
│   ├── README_Week5.md
│   └── README_Week6.md             # ← this file
├── data/                           # ← Generated artifacts (stats, figures, model)
│   ├── LoanStats3a.csv             #    Raw source (Week 1 input)
│   ├── cleaned_dataset.csv         #    Week 1 output (symlinked to download/)
│   ├── stats.json / eda_stats.json #    Week 1/2 machine-readable stats
│   ├── week3_stats.json
│   ├── week4_stats.json
│   ├── week5_stats.json
│   ├── best_model.joblib           #    Week 4 champion model
│   ├── eda_figures/                #    Week 2 EDA figures
│   ├── week3_figures/              #    Week 3 statistical figures (10)
│   ├── week4_figures/              #    Week 4 ML figures (6)
│   ├── week5_figures/              #    Week 5 viz portfolio (10)
│   └── week6_figures/              #    Week 6 capstone synthesis (1)
└── scripts/                        # ← All generation scripts (recoverable artifacts)
    ├── week1_cleaning.py
    ├── week2_eda.py
    ├── week3_modeling.py
    ├── week4_ml_pipeline.py
    ├── week4_feature_importance.py
    ├── week5_visualizations.py
    ├── build_week3_body.py / week3_cover.html / week3_cover.pdf
    ├── build_week3_notebook.py
    ├── build_week4_body.py / week4_cover.html / week4_cover.pdf
    ├── build_week4_notebook.py
    ├── build_week5_body.py / week5_cover.html / week5_cover.pdf
    ├── build_week5_notebook.py
    ├── build_week6_body.py / week6_cover.html / week6_cover.pdf
    ├── build_week6_notebook.py
    └── body_week{3,4,5,6}.pdf      #    Pre-merge body PDFs
```

---

## 9. Limitations and Further Work

### Limitations

- **Vintage limitation.** The dataset spans 2007–2011, capturing the financial crisis
  but not the post-2014 era with its changed underwriting standards.
- **Random split, not time split.** We used a stratified random split rather than a
  time-based split (train on 2007–2010, test on 2011).
- **No post-origination features.** We use only origination-time attributes. Payment
  behavior in the first 3–6 months would likely add substantial lift.
- **Class imbalance handling.** We tuned for PR-AUC but did not apply SMOTE or
  class-weighting.
- **US-centric.** The geography and regulatory context are US-specific.


---

## 10. Project Narrative — The Loop Closes

The six weeks form a closed analytical loop:

- **Week 3** asked *which features matter* and found grade dominates.
- **Week 4** asked *how well can we predict* and found a logistic regression captures
  the signal as well as any tree ensemble.
- **Week 5** asked *what does it mean* and explained visually why the predictive ceiling
  is real (overlapping DTI distributions) and why the interaction effects are small
  (the risk matrix's hottest cell is 50%, not 80%).

**Week 6** integrates these answers into a single narrative. The grade signal that
dominates the Week-4 model was first surfaced in Week 3's hypothesis tests, quantified
in Week 5's correlation matrix, and explained operationally in Week 5's interest-rate
violin plot. The predictive ceiling that bounds the Week-4 models is explained visually
in Week 5's DTI distribution. The narrative closes the loop.

> **The project in one sentence:** Using 42,535 LendingClub loans, we showed that the
> platform's assigned loan grade is the dominant predictor of default (5.5× spread
> A→G), that a simple logistic regression captures this signal as well as any tree
> ensemble (ROC-AUC 0.697), and that residual risk concentrates at identifiable
> intersections — small_business loans in low grades, borrowers in Nevada and the
> Southeast, and borrowers with high loan-to-income ratios.
