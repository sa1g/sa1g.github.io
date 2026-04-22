---
title: Advanced Topics of Machine Learning and Optimization
description: Learn missing concepts in Concept Bottleneck Models with RLHF-style feedback.
slug: atmlo
date: 2026-04-10 01:00:00+0000
categories:
  - uni_projects
tags:
  - AI
  - Interpretable AI
  - CBM
  - RL
  - RLHF
weight: 1
---

[Project Repo](https://github.com/sa1g/atmlo)

# Improving Concept Bottleneck Models with RLHF-style Feedback

This project investigates how to improve Concept Bottleneck Models (CBMs) with RLHF-style feedback in a human-in-the-loop setting. Using the CUB-200-2011 bird dataset (112 visual concepts), the work starts from deliberately weakened CBMs created by removing important concepts and reducing training data, then trains a Human Decision Model (HDM) to simulate downstream human feedback. The core contribution is an RLHF-inspired fine-tuning pipeline, including custom concept-quality rewards (CAC/CAHC) and a PPO-based optimization setup, to recover missing concept quality and improve final predictions. Experiments show that the approach is feasible: RLHF can improve degraded models (up to about +17% in some settings), though it still trails standard supervised fine-tuning and remains roughly 10% below a fully trained baseline in harder cases. The study also finds that heuristic reward signals are more useful than similarity metrics like cosine/EMD in this context, and that some CUB concepts appear redundant for downstream classification.

More details can be found in the report linked below.

<div align="center" style="display: flex; justify-content: center; gap: 40px; flex-wrap: wrap;">

  <div>
    <a href="https://github.com/sa1g/atmlo/blob/master/report/report.pdf">
      <img src="https://raw.githubusercontent.com/sa1g/atmlo/refs/heads/master/report/thumb.png" width="250"/>
    </a>
    <p align="center">Click to download the report</p>
  </div>
</div>

## Reproducibility
The code is in `/src`. To reproduce the results in the report you'll need fast hardware and a lot of patience, if you have a slurm cluster use job-arrays (an example is present in the repo). Most experiments are setup in `/src/common/experiment_configs.py`, to select one of them simply run: `python main.py -pc <experiment-name>`. Multiple arguments are available to customize the training, see `python main.py -h` for details. The code is structured to allow easy addition of new experiments, reward functions, and training setups.

The code won't be refactored even if it needs it. Currently configs for supervised training, fine-tuning of both CBM and HDM, and RLHF-style training are all mixed together, this makes everything a bit confusing, but it works. This happened because I was aiming to quickly test different ideas and setups, and I didn't want to spend time refactoring the code.

The coolest thing over the code, except for the _custom_ PPO behavior is how the supervised training cycle is written to avoid needing to rewrite it for the different training stages (CBM, HDM, and fine-tuning). Most of the same logic is kept in the same place, simply by using basic inheritance and a bit of abstraction. 



## Ack
If you are reading this well...have fun! - Sa1g
