# Investigation of Microbiome Abundances in Western vs. Non-Western Populations

> Identifying microbial signatures that distinguish Western from Non-Western gut profiles and characterize extreme BMI phenotypes using metagenomic data.

---

## Overview

This project investigates gut microbiome composition across 20 countries using data from the **Human Microbiome Atlas (HMA)** — 3,292 healthy individuals, ~1,990 Metagenomic Species Pangenomes (MSPs). After rigorous preprocessing (CLR transformation, batch and library-size validation), unsupervised ordination (UMAP, t-SNE) and a supervised ML pipeline (Random Forest + L1-regularised Logistic Regression) were applied to identify microbial markers linked to lifestyle and BMI.

---

## Key Findings

**Western vs. Non-Western:** Both classifiers converged on 5 shared markers (ROC-AUC ≈ 0.95):

| Taxon | Enriched in |
|---|---|
| Unclassified *Ruminococcaceae* | Non-Western |
| *[Eubacterium] ramulus* | Non-Western |
| *Anaerostipes hadrus 2* | Western |
| *Anaeromassilibacillus* sp. An250 | Western |
| *Blautia* sp. 2789STDY5834862 | Western |

**BMI extremes (USA cohort):** A label-permutation test confirmed a subtle but valid signal (balanced accuracy 0.570, p = 0.02). Lean individuals (BMI < 22) were enriched in *Bacteroides uniformis* and two *Alistipes* species; obese individuals (BMI > 32) in *Clostridium* sp. CAG:169 and *Blautia* sp. SG772.

---

## Methods

- **Data:** Human Microbiome Atlas — abundance matrix, metadata, metabolic models (GEMs)
- **Preprocessing:** Prevalence filtering, TSS normalisation, CLR transformation, batch/library-size diagnostics
- **Unsupervised:** UMAP and t-SNE on Aitchison distances
- **Supervised:** Random Forest + LASSO Logistic Regression with nested cross-validation (Stratified Group K-Fold by country)
- **Statistics:** Mann–Whitney U test + Cliff's delta for effect size validation
- **Languages:** Python (primary), R (selected steps); all notebooks on [GitHub](https://github.com/dafi03/PA1_repo)

---

## Project Structure

```
├── data/
│   ├── raw/            # Original, unmodified datasets
│   └── processed/      # Cleaned and transformed data
├── notebooks/          # Jupyter notebooks for EDA and analysis
├── Papers/
├── results/            # MSP tables of identified microbes
├── report/
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Team

| Name | Role |
|---|---|
| Ajna Binaki | Student |
| Dario Filippone | Student |

**Supervisor:** Dr. Tugçe Bilgin Sonay  
**Program:** Applied Digital Life Sciences (ADLS) — ZHAW, Wädenswil  
**Submitted:** 21 May 2026

---
