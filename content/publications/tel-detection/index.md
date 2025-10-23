---
title: "Diffusion-Transformer Hybrid Framework for Dataset Construction in Deep Learning-Based TEL Detection from Satellite Imagery"
authors:
  - admin
  - Soomin Kwon
  - Seongil Jo
  - Jaeoh Kim
date: 2025-10-01
publishDate: 2025-10-01
draft: false
publication_types:
  - article
publication: "Submitted to *ISPRS Journal of Photogrammetry and Remote Sensing*"
publication_short: "Under Review (JPRS)"
abstract: "Automated identification of transporter-erector-launchers (TELs) in satellite imagery is a critical task for strategic surveillance, yet it remains hindered by extreme data sparsity and the operational complexity of camouflaged military assets. To overcome these challenges, this study proposes a three-stage synthetic data generation framework that integrates semantic-preserving diffusion-based augmentation, context-aware object insertion, and transformer-based image inpainting. Experimental results demonstrate that the proposed framework outperforms conventional GAN-based approaches, achieving a 38% reduction in Frechet Inception Distance and producing visually coherent datasets suitable for training deep learning-based detection models."
summary: "미사일 객체 탐지 데이터셋 증강 Diffusion과 Transformer를 결합한 이미지 증강 3단계 프레임워크"
tags:
  - Generative AI
  - Diffusion Model
  - Transformer
  - Satellite Imagery
image:
  preview_only: true
---

---
### Method Overview

This study proposes a three-stage synthetic data generation framework for TEL detection in satellite imagery.

<figure style="margin: 2rem 0;">
  <img src="tel_overview.png" alt="Overview of Generation Pipeline" style="width: 100%; border-radius: 8px;">
  <figcaption style="text-align: center; color: #6b7280; font-size: 0.9rem; margin-top: 0.5rem; font-style: italic;">
    Figure 1. Overview of the proposed generation pipeline for TEL detection dataset
  </figcaption>
</figure>

---
**Stage 1: TEL Dataset Augmentation**

The first stage employs a conditional diffusion model to augment existing TEL instances while preserving structural fidelity and introducing variation in camouflage patterns.

<figure style="margin: 2rem 0;">
  <img src="step1.jpg" alt="TEL Augmentation Process" style="width: 100%; border-radius: 8px;">
  <figcaption style="text-align: center; color: #6b7280; font-size: 0.9rem; margin-top: 0.5rem; font-style: italic;">
    Figure 2. TEL dataset augmentation process using diffusion-based semantic preservation
  </figcaption>
</figure>

---
**Stage 2: Context-Aware Object Insertion**

Augmented TEL objects are strategically inserted into realistic satellite backgrounds identified through open-source intelligence, including tunnel entrances, mountainous regions, and airfield aprons.

<figure style="margin: 2rem 0;">
  <img src="step2.png" alt="Object Insertion" style="width: 60%; display: block; margin: 0 auto; border-radius: 8px;">
  
  <figcaption style="text-align: center; color: #6b7280; font-size: 0.9rem; margin-top: 0.5rem; font-style: italic;">
    Figure 3. Context-aware TEL object insertion into satellite imagery backgrounds
  </figcaption>
</figure>

---
**Stage 3: Transformer-Based Inpainting**

The final stage applies a transformer-based inpainting model to eliminate boundary artifacts and ensure spatial and spectral continuity around inserted objects.

<figure style="margin: 2rem 0;">
  <img src="step3.png" alt="Inpainting Process" style="width: 100%; border-radius: 8px;">
  <figcaption style="text-align: center; color: #6b7280; font-size: 0.9rem; margin-top: 0.5rem; font-style: italic;">
    Figure 4. Inpainting process of missing areas using transformer-based model
  </figcaption>
</figure>

---
**Results**

The proposed framework achieves a 38% reduction in Fréchet Inception Distance compared to conventional GAN-based approaches, demonstrating superior quality in synthetic dataset generation.

<figure style="margin: 2rem 0;">
  <img src="featured.png" alt="Augmentation Results" style="width: 100%; border-radius: 8px;">
  <figcaption style="text-align: center; color: #6b7280; font-size: 0.9rem; margin-top: 0.5rem; font-style: italic;">
    Figure 5. Augmentation Results
  </figcaption>
</figure>

---
**Key Contributions**

- **Three-stage synthetic data generation framework** integrating diffusion models, context-aware insertion, and transformer-based inpainting
- **Semantic-preserving augmentation** that maintains structural fidelity while introducing realistic variations
- **Context-aware background selection** using open-source intelligence for realistic placement
- **Significant performance improvement** over existing GAN-based methods