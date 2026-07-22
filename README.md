# Multi-Run Quantitative Robustness Analysis of the Neuromatch Animal Pose Estimator

This repository contains the work developed for my **Neuromatch Academy Deep Learning** project.

The study investigates how the U-Net-based animal pose estimator provided in the official **Neuromatch Academy Animal Pose Estimation** project responds to controlled changes in image appearance and visibility. The evaluated conditions include mild and strong Gaussian blur, Gaussian noise, brightness and contrast changes, and central occlusion.

Rather than evaluating a single trained model, I trained five independently initialized U-Net models using random seeds `11`, `22`, `33`, `44`, and `55`. This design allows variability introduced during training to be considered separately from performance changes associated with the image perturbations.

This work builds upon the official **Neuromatch Academy Animal Pose Estimation** notebook, which downloads and prepares the fruit fly dataset, represents seventeen anatomical landmarks as heatmaps, trains a single U-Net model based on the architecture proposed by Ronneberger et al. (2015), and evaluates landmark localization using Euclidean error.

Using the original notebook in Google Colab, I added new Markdown and code cells to train multiple independent models, apply deterministic perturbations during evaluation, perform quantitative and landmark-level analyses, run exploratory paired statistical tests, and generate figures, CSV files, model checkpoints, and a Word report while preserving the original model and training workflow.

The objective was not to modify the original U-Net model, but to extend its evaluation through a reproducible multi-run robustness analysis.

## Neuromatch Academy Resources

- **Project page:** https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html
- **Original notebook:** https://colab.research.google.com/github/NeuromatchAcademy/course-content-dl/blob/main/projects/Neuroscience/pose_estimation.ipynb

---

# Motivation

Changes in image quality or visibility can affect the predictions of computer-vision models. Evaluating a model under blur, noise, illumination changes, and occlusion provides information about its behavior beyond performance on unmodified validation images (Geirhos et al., 2020).

Deep neural-network training is also affected by sources of randomness such as parameter initialization and stochastic optimization. As a result, independently trained models may achieve different performance even when they use the same architecture, hyperparameters, and dataset (Henderson et al., 2018; Åkesson et al., 2024).

To account for this variability, I evaluated the same perturbation conditions across five independently trained models while keeping the train-validation split fixed.

Throughout this project, **robustness** refers to the ability of a trained model to maintain landmark-localization accuracy under an image perturbation relative to its own baseline performance.

---

# Quantitative Evaluation

Each model is evaluated on the same fixed validation subset under the baseline condition and six deterministic perturbation conditions:

- Mild Gaussian Blur: kernel size `5`, σ = `1.0`.
- Strong Gaussian Blur: kernel size `9`, σ = `2.0`.
- Gaussian Noise: σ = `0.10`.
- Brightness: factor `1.30`.
- Contrast: factor `1.40`.
- Central Occlusion: a centered mask covering 40% of the image height and width.

The landmark annotations remain unchanged because the perturbations modify only image appearance or visibility.

The notebook computes:

- Mean and median landmark-localization error.
- PCK@5, PCK@10, and PCK@20.
- Landmark-level mean error and PCK@5.
- Absolute and relative changes from each model's baseline.
- Mean and standard deviation across the five runs.
- The proportion of runs in which each perturbation increased error.
- Exploratory paired t-tests and one-sided Wilcoxon signed-rank tests.

Because only five paired runs are available, the statistical tests are treated as exploratory.

---

# Repository Overview

```text
multirun_animal_pose_estimation_robustness/

├── README.md          # Project documentation.
├── notebooks/         # Google Colab notebook containing the complete workflow.
├── models/            # Saved U-Net checkpoints.
├── results/           # Quantitative CSV files and summary statistics.
├── figures/           # Quantitative and qualitative robustness figures.
└── reports/           # Final Word report
```
---

# Running the notebook from beginning to end:

- Downloads and prepares the original Neuromatch dataset.
- Installs additional packages when required.
- Creates one fixed training-validation split.
- Trains five U-Net models using seeds 11, 22, 33, 44, and 55.
- Evaluates every model under baseline and perturbation conditions.
- Exports run-level, landmark-level, paired, statistical, and summary CSV files.
- Generates quantitative and qualitative figures.
- Saves the five trained model checkpoints.
- Creates the final Word report and supporting downloadable outputs.

---

# Acknowledgements

This work was completed as part of the Neuromatch Academy Deep Learning program (July 2026).

I gratefully acknowledge Neuromatch Academy for providing the lectures, educational materials, original notebook, dataset workflow, and model implementation that served as the foundation for this project.
