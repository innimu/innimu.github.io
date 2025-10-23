---
title: "Hierarchical and Robust Bayesian Meta-Models for Estimating Cadmium Dose-Response Curves"
authors:
  - admin
  - Inyoung Beak
  - Jeongseon Kim
  - Jaeoh Kim
  - Seongil Jo
date: 2025-09-01
publishDate: 2025-10-01
draft: false
publication_types:
  - article
publication: "Submitted to *Statistical Methods in Medical Research*"
publication_short: "Under Review (SMMR)"
abstract: "Cadmium is a toxic heavy metal that accumulates in human tissues and poses long-term health risks, particularly nephrotoxicity. Benchmark dose (BMD) modeling provides a scientific basis for establishing health-based guidance values; however, conventional dose-response models often fail to address heterogeneity and outliers across studies. This study conducts a Bayesian meta-analysis of 48 studies and 250 exposure groups published between 1983 and 2022, focusing on the relationship between urinary cadmium (UCd) and urinary β2-microglobulin (β2MG), a biomarker of early renal dysfunction. We propose a robust hierarchical Bayesian framework based on a Hierarchical Mixture of Experts (HME) model with a piecewise linear structure and Student's t-distribution to capture latent subgroup structure and improve robustness against outliers. Compared with standard models, the HME-PL model achieved superior performance in terms of Deviance Information Criterion (DIC) and Normalized Root Mean Squared Error (NRMSE). Age- and sex-specific BMD and BMDL estimates indicate that older adults, particularly females, exhibit greater sensitivity to cadmium exposure. These findings highlight the importance of incorporating heterogeneity in dose-response assessment and provide a practical methodological contribution for deriving regulatory reference points in toxicological risk assessment."
summary: "베이지안 메타분석<br> 카드뮴 위험 기준치 추정을 위한 강건한 HME-PL 모형 사용"
tags:
  - bayesian  
  - Risk Assessment
featured: true
image:
  preview_only: true
---

## Data Overview

**Exploratory Data Analysis**

We compiled data from 48 independent studies published between 1983 and 2022, encompassing 250 exposure groups. The dataset exhibits clear nonlinear associations between urinary cadmium (UCd) and β2-microglobulin (β2MG) concentrations, with notable differences across age and sex subgroups.

<figure style="margin: 2rem 0;">
  <img src="image.png" alt="Data Distribution" style="width: 100%; border-radius: 8px; display: block; margin: 0 auto;">
  <figcaption style="text-align: center; color: #6b7280; font-size: 0.9rem; margin-top: 0.5rem; font-style: italic;">
    Figure 2. UCd and β2MG distributions by sex and age
  </figcaption>
</figure>

---
## Method
**Standard Piecewise Linear Model Performance**

Conventional piecewise linear (PL) models were fitted under both Normal and Student's t-distribution assumptions. While both models captured the general trend, they exhibited limitations in handling heterogeneity and outliers, particularly evident in the post-breakpoint slope estimation.

<figure style="margin: 2rem 0;">
  <img src="image-1.png" alt="Standard PL Model" style="width: 70%; border-radius: 8px; display: block; margin: 0 auto;">
  <figcaption style="text-align: center; color: #6b7280; font-size: 0.9rem; margin-top: 0.5rem; font-style: italic;">
    Figure 1. Standard-PL model under Normal and Student's t assumptions
  </figcaption>
</figure>

---
**Proposed Model: HME-PL with Robust Distribution**

To address the limitations of standard models, we developed a Hierarchical Mixture of Experts (HME) framework that identifies latent subgroup structures within the data. The model assigns observations to either a "mainstream" component (Component 1, blue) or an "atypical" component (Component 2, green) using a gating network based on age.

The Student's t-distribution assumption further enhances robustness by downweighting extreme observations, resulting in more stable parameter estimates and improved model fit.

<figure style="margin: 2rem 0;">
  <img src="image-2.png" alt="HME-PL Model" style="width: 70%; border-radius: 8px; display: block; margin: 0 auto; ">
  <figcaption style="text-align: center; color: #6b7280; font-size: 0.9rem; margin-top: 0.5rem; font-style: italic;">
    Figure 3. HME-PL model with two latent components
  </figcaption>
</figure>

---

## Model Performance Comparison

**HME-PL vs Standard-PL**

| Model Type | Distribution | DIC | NRMSE |
|------------|-------------|-----|-------|
| **Standard-PL** | Normal | 1093.0 | 1.000 |
| **Standard-PL** | Student's t | 815.9 | 0.899 |
| **HME-PL** | Normal | 809.0 | 1.000 |
| **HME-PL** | Student's t | **520.4** | **0.854** |

The HME-PL model with Student's t-distribution achieved a **52% reduction in DIC** compared to the standard Normal model, demonstrating superior model fit and robustness.

---

## Benchmark Dose Estimates

**Age- and Sex-Specific BMD and BMDL**

Based on the optimal HME-PL model with Student's t-distribution, we derived benchmark doses (BMD) and their lower confidence bounds (BMDL) for different demographic subgroups using a clinical cut-off of 1000 µg/g creatinine.

| Subgroup | BMD₅ (BMDL₅) | BMD₁₀ (BMDL₁₀) |
|----------|--------------|----------------|
| **Male, age < 50** | 7.30 (6.89) | 7.91 (7.53) |
| **Male, age ≥ 50** | 7.08 (6.69) | 7.61 (7.16) |
| **Female, age < 50** | 7.27 (6.69) | 7.87 (7.54) |
| **Female, age ≥ 50** | **7.05 (6.68)** | **7.57 (7.23)** |

Older females consistently exhibited the **lowest BMD and BMDL values**, indicating greater sensitivity to cadmium-induced nephrotoxicity. These findings support the need for age- and sex-specific regulatory guidelines.

---

**Key Contributions**

- **Hierarchical Mixture of Experts (HME)** framework to capture latent heterogeneity across studies
- **Student's t-distribution** for robustness against outliers and heavy-tailed noise
- **Age- and sex-specific BMD estimates** for tailored risk assessment
- **52% reduction in DIC** compared to standard models, demonstrating superior performance