# AI Readiness Score - Measuring Human Skills for the AI Era

An evidence-based analytics system that measures how ready people are to work alongside AI, built as an MSc final project for LEVRA, a UK EdTech company, and delivered as a live interactive dashboard.

> **Note on data:** This project was carried out with real client data under an academic arrangement. No client or learner data is included in this repository. The code runs on a small synthetic sample (`sample_learner_data.csv`) that mirrors the structure of the original files, so the pipeline works end to end without exposing anything confidential.

---

## The problem

As AI takes over more technical and routine work, the skills that decide who succeeds are increasingly human ones: how people think, adapt, and communicate. LEVRA trains these skills through AI-avatar roleplays and had rich data on learner performance, but no single, defensible way to answer the question its clients kept asking: **is this person ready for an AI-driven workplace, and if not, what should they work on?**

## The approach

The project answers that question from two independent directions, then integrates the findings.

**Pipeline A - Quantitative (the AI Readiness Score)**
- Consolidated ~1,000 stacked assessment rows into 160 clean learner records
- Diagnosed and handled 31% missing data (compared four imputation methods; chose Random Forest on a masked-recovery test)
- Selected seven readiness skills from the research literature
- Built a composite score with PCA-derived weights, validated for reliability (Cronbach's alpha = 0.76) and robustness
- Audited fairness across generation, seniority and industry (Kruskal-Wallis)

**Pipeline B - NLP (roleplay transcripts)**
- Quality-filtered 801 sessions down to 468 usable ones
- Applied sentiment analysis (VADER), TF-IDF and topic modelling (NMF)
- Built a predictive model comparing four algorithms across three feature sets

**Integration** - the two pipelines share no common learner IDs, so they were integrated at the level of findings, which makes any agreement between them genuine corroboration rather than an artefact.

## Key results

| Finding | Result |
|---|---|
| Score reliability | Cronbach's alpha = 0.76 |
| Can demographics predict readiness? | No - R squared below 0 (readiness is individual) |
| Can language predict performance? | Yes - R squared approx 0.45 |
| Literature vs data agreement | Selected skills cohere more (0.36) than with others (0.29) |

**Headline:** Who you are does not determine AI readiness. How you communicate does.

## Tech used

`Python` · `pandas` · `scikit-learn` · `Random Forest` · `Ridge regression` · `TF-IDF` · `SHAP` · `VADER` · `Streamlit`

## Repository contents

- `Levra_Pipeline-A.ipynb` - quantitative AI Readiness Score pipeline
- `Levra_Pipeline-B.ipynb` - NLP pipeline on roleplay transcripts
- `sample_learner_data.csv` - synthetic sample data (no client data)
- `dashboard_screenshot.png` - the live Streamlit dashboard

---

*Built as an MSc Business & Data Analytics final project, Ravensbourne University London (2026). Shared for portfolio purposes with all client data removed.*
