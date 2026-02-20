---
title: "Data Internship in zjts"
excerpt: "
**Job Content:**

- Cuisine Popularity Analysis and Heat-driven Dataset Construction for Dish Name Recognition
Designed and implemented a data-centric pipeline to enhance multi-modal dish name generation models.
Scraped regional dish popularity and TGI (Target Group Index) data from ByteDance's analytics portal to identify high-frequency dishes for targeted data augmentation, based on observed performance gains with ≥50 training examples per dish.
Automatically retrieved representative dish images and constructed a structured training dataset.
Built a curated 500-sample benchmark test set and developed a two-layer evaluation framework combining exact-match metrics and semantic scoring using LLMs (GPT-4, Gemini, Claude), enabling quantitative analysis of iterative SFT (Supervised Fine-tuning) performance for models like Qwen-VL.
Delivered structured outputs and visualizations to support downstream personalization and recommendation scenarios.

- Multi-Stage Fine-Tuning Pipeline for Multi-modal Dish Name Recognition (SFT → DPO → GRPO)
Designed and implemented a scalable training pipeline for Qwen2.5-VL series (3B/7B/72B) to enhance multi-modal dish name recognition.

    - Conducted Supervised Fine-tuning (SFT) using Gemini-labeled high-quality food datasets, integrating LoRA and SwanLab for efficient training and tracking.

    - Applied Direct Preference Optimization (DPO) based on LLaMA-Factory, using structured positive-negative pairs to improve user-preferred outputs.

    - Deployed Group Relative Policy Optimization (GRPO) via EasyR1 to further align recognition accuracy with semantic reward functions.

    - Built a progressive dataset evolution strategy combining crawled images, Gemini instruction data, and balanced samples.

    - Implemented full evaluation and visualization pipeline using SwanLab, tracking loss, LR schedule, GPU usage, and token statistics.

<br/><img src='/images/efficient_frontier.png'>
"
collection: projects
---