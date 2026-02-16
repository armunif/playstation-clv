# Customer Lifetime Value & Next Best Action Framework for PlayStation

An end-to-end data science pipeline that takes raw player behaviour and produces personalised, budget-constrained marketing recommendations for each player.

**[Read the Full Report →](https://armunif.github.io/playstation-clv/report.html)**

---

## What This Project Does

PlayStation's player base spans millions of subscribers across different engagement levels, spending patterns, and subscription tiers. This project builds the analytical infrastructure to answer one question: **what should PlayStation do about each player?**

The pipeline scores every player on three dimensions — churn risk, purchase propensity, and lifetime value — then combines them into a **Next Best Action** recommendation with a specific intervention strategy and budget ceiling.

## Key Results

| Model | Task | AUC | Notes |
|-------|------|-----|-------|
| Churn | Predict PS Plus cancellation | 0.998* | Risk tiers validated against actual churn rates |
| Propensity | Predict paid DLC purchase | 0.86 | Engagement depth is the primary driver |

*\*Churn AUC reflects clean simulated data. With production data, expect 0.78–0.85. See report for discussion.*

**Valhalla Signal**: Players who claimed free DLC purchased paid DLC at a 149% higher rate than non-claimers — validating a "free content as purchase funnel" personalisation strategy.

**NBA Framework**: 5 action categories (Retain Critical → Retain Standard → Upsell → Nurture → Monitor), each with CLV-based budget ceilings.

## Repository Structure

```
├── report.html                          # Business report (start here)
├── 01_data_simulation.ipynb             # PlayStation ecosystem simulation
├── 02_player_360_features.ipynb         # EDA & 47-feature Player 360 table
├── 03_churn_model.ipynb                 # Churn prediction & risk segmentation
├── 04_propensity_model.ipynb            # DLC propensity & Valhalla analysis
├── 05_clv_and_next_best_action.ipynb    # CLV, NBA framework & impact simulation
├── data/                                # Generated datasets
│   ├── players.csv
│   ├── subscriptions.csv
│   ├── sessions.csv
│   ├── purchases.csv
│   ├── trophies.csv
│   ├── games.csv
│   ├── dlc_catalog.csv
│   ├── player360.csv                    # Feature table (5,000 x 47)
│   ├── churn_scores.csv
│   ├── propensity_scores.csv
│   ├── clv_estimates.csv
│   └── nba_final.csv                    # Final player recommendations
└── README.md
```

## Technical Stack

Python 3.10+ · pandas · NumPy · scikit-learn · matplotlib · seaborn

Models: Logistic Regression (baseline) · Gradient Boosting (primary)

## Methodology Notes

This project uses **simulated data** designed to mirror PlayStation's data structures and behavioural patterns. No public dataset exists that captures PS Plus tiers, DLC behaviour, session data, and trophy systems together. The methodology — feature engineering, model evaluation, threshold tuning, CLV estimation, and the NBA decision framework — is fully transferable to real production data.

Key design choices and their rationale are documented throughout the notebooks and in the [full report](https://armunif.github.io/playstation-clv/report.html).

---

Built as a portfolio project for the Data Scientist — CLV & Next Best Action role at PlayStation.
