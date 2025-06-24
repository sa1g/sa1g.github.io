---
title: Advanced Computer Vision - MobileCLIP
description: Case study on MobileCLIP, a lightweight CLIP model for mobile devices, focusing on architecture, training, and dataset creation.
slug: acv
date: 2025-02-20 01:00:00+0000
# image: cover.jpg
categories:
  - uni_projects
tags:
  - AI
  - CLIP
  - CV
weight: 1 # You can add weight to some posts to override the default sorting (date descending)
---

[Project Repo](https://github.com/sa1g/advanced-cv)

Made in collaboration with [Emanuele](https://github.com/IlPoiana)

This is not strictly a project, but rather a case study on how MobileCLIP was developed, focusing on understanding the architecture, training and dataset creation, and the overall process of building a lightweight CLIP model for mobile devices. Possible improvements were proposed.

<p align="center">
<a href="https://github.com/sa1g/advanced-cv/blob/main/MobileClip_presentation.pdf"><img src="image.png" width="250"/></a>
</p>
<p align="center">
Click to download presentation
</p>

### Training

- **TinyCLIP distillation of MobileCLIP**
  - Reduce the model parameter number, while keeping most of the original accuracy using TinyCLIP.
- **Improving synthetic captions**
  - Regenerate captions if they are too similar in the reinforced dataset.
- **Sigmoid self-attention**
  - Substitute softmax with sigmoid self-attention in the self-attention layers.

### Inference

- **PuMer adaptation to MobileCLIP**
  - PuMer adopts token pruning **(TIP)** and merging **(MAM)** in ViLT architecture to improve latency without compromising model performance.
  - MobileCLIP differs from ViLT from a structural perspective, but modality aware merging (MAM) still could lead to small latency improvements.
- **Token Ranking Pruning**
  - Patch Ranking original purpose was to **prune image patches** in tranformer based CLIP models **through a predictor** to reduce the number of tokens processed through the image and text encoder.
  - Adapting this technique to the MobileCLIP text encoder could result in similar improvements to the paper implementation.
- **Dynamic Input Resolution**
  - Adjust input resolution on a per-sample basis: low-resolution inference for simpler images, high-resolution for more complex ones.
