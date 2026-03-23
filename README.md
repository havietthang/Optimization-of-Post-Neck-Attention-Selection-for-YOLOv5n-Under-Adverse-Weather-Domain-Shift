# Optimization of Post-Neck Attention Selection for YOLOv5n Under Adverse-Weather Domain Shift

This repository accompanies our study on improving lightweight object detection under adverse-weather domain shift. It extends our earlier CSoNet 2025 paper, **“Attention-Enhanced YOLO-Nano for Adverse Weather Object Detection,”** by keeping the strongest earlier baseline fixed and systematically comparing different lightweight **post-neck attention modules** under a controlled experimental setup. In this extended version, we enlarge the training and validation data while keeping the **DAWN test set unchanged** for fair comparison across model variants.

## Overview

Object detection models often suffer when they are trained on cleaner or narrower data distributions and then evaluated on images captured in rain, fog, snow, haze, glare, or low visibility. This repository studies whether adding a lightweight attention block **after the neck and before the detection head** can improve robustness without redesigning the full model.

Instead of sweeping many architectures again, this project starts from the strongest configuration found in our earlier experiments:

- **Base detector:** YOLOv5n
- **Neck enhancement:** ResCBAM inserted 4 times in the neck
- **Controlled variable:** one additional post-neck attention module
- **Evaluation setting:** expanded train/validation data, unchanged DAWN test set

The goal is to determine which post-neck attention choice gives the best tradeoff between accuracy, robustness, and model simplicity under adverse-weather domain shift.

## Research Question

**Given a fixed strong lightweight baseline, which post-neck attention module is most effective for adverse-weather object detection?**

The comparison focuses on modules such as:

- SimAM
- CoordAtt
- Triplet Attention
- NAM
- GCBlock

All variants are built on the same baseline so that performance differences can be more confidently attributed to the added post-neck attention module rather than unrelated architectural changes.

## Repository Structure

```text
.
├── README.md
├── dataset_expansion.ipynb
├── train_attention_models.ipynb
└── figures/
