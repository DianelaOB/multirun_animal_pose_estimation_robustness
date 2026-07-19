# Multi-Run Robustness Evaluation of the Neuromatch U-Net for Animal Pose Estimation

This repository extends the original **Neuromatch Academy Animal Pose Estimation** project by providing a reproducible framework for evaluating the robustness of the U-Net pose estimation model across multiple independent training runs and several common image perturbations.

The original Neuromatch project trains a U-Net to localize 17 anatomical landmarks on grayscale images of fruit flies.

Original project:

[https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html](https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html)

---

# Highlights

This repository extends the original Neuromatch notebook by introducing:

* Multi-run robustness evaluation across five independently trained U-Net models
* Baseline variability analysis
* Robustness evaluation under multiple image perturbations
* Landmark-level robustness analysis
* Automatic generation of quantitative tables, figures, summary CSV files, and a reproducible report
* Exploratory statistical analyses across independent training runs

---

# Project Overview

The original Neuromatch notebook evaluates a single trained model. In this work, I extended the evaluation pipeline to quantify robustness across multiple independently trained models while keeping the original U-Net architecture, optimizer, loss function, and training procedure unchanged.

Each model is trained using a different random seed and evaluated on the same validation dataset under both the original imaging conditions and several synthetic image perturbations. Performance is analyzed using multiple localization metrics, paired comparisons relative to baseline, and landmark-level robustness analyses.

---

# Evaluated Perturbations

The following perturbations are applied **only during evaluation**:

* Mild Gaussian Blur
* Strong Gaussian Blur
* Gaussian Noise
* Brightness Increase
* Contrast Increase
* Central Occlusion

These perturbations modify only the image appearance while preserving the original landmark coordinates.

---

# Evaluation Metrics

The evaluation includes:

* Mean localization error (pixels)
* Median localization error
* PCK@5
* PCK@10
* PCK@20
* Landmark-specific localization error
* Percentage change relative to baseline
* Paired changes relative to baseline
* Exploratory paired statistical analyses

---`
## Notebook Workflow

The notebook follows the complete evaluation pipeline below:

1. Load the original Neuromatch dataset and model.
2. Train five U-Net models using different random seeds while keeping the original training pipeline unchanged.
3. Evaluate each trained model on the original validation images (baseline).
4. Evaluate the same models under six synthetic image perturbations.
5. Compute localization metrics (mean error, median error, PCK@5, PCK@10, landmark-level errors).
6. Perform paired comparisons relative to each model's baseline performance.
7. Generate summary tables, statistical analyses, and publication-ready figures.
8. Export CSV files and automatically generate the final robustness report.

---`
## Repository Outputs

Running the notebook generates:

- Five trained U-Net models
- Run-level performance tables
- Summary statistics across independent runs
- Landmark-level robustness analyses
- Publication-quality figures
- CSV files containing all quantitative results
- An automatically generated HTML and Word report

---`  
# Reproducibility

All experiments were implemented in **Google Colab**.

The evaluation pipeline uses:

* Five fixed random seeds
* A fixed validation split
* Identical training settings across runs
* Deterministic perturbation generation

allowing the complete robustness analysis to be reproduced directly from the notebook.

Running the notebook from top to bottom reproduces the complete analysis, including model training, robustness evaluation, figure generation, CSV exports, and report generation.

---

# Results

The repository automatically generates:

* Trained models
* Performance tables
* Robustness figures
* Statistical summaries
* A complete robustness report

---

# Future Work

The evaluation framework can be readily extended to investigate:

* Perturbation-based data augmentation during training
* Additional perturbation types (e.g., rotations, translations, motion blur)
* Multiple perturbation severity levels
* Alternative pose estimation architectures
* Evaluation on real-world degraded images

---

# Acknowledgments

This work builds upon the original **Animal Pose Estimation** project developed by **Neuromatch Academy**.

Original project:

[https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html](https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html)


