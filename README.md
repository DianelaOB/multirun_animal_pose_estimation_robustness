# Multi-Run Quantitative Robustness Analysis of the Neuromatch Animal Pose Estimator

This repository contains the work developed for my **Neuromatch Academy Deep Learning** project on evaluating the robustness of a U-Net-based animal pose estimator.

The project builds upon the official **Neuromatch Academy Animal Pose Estimation** notebook, which implements a U-Net model (Ronneberger et al., 2015) for localizing seventeen anatomical landmarks in *Drosophila melanogaster* images. Working in **Google Colab**, I extended the original notebook by adding new Markdown and code cells to perform repeated training runs, robustness experiments, quantitative analyses, statistical summaries, and automated report generation while preserving the original training pipeline.

**Neuromatch Academy resources**

- Project page: https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html
- Original notebook: https://colab.research.google.com/github/NeuromatchAcademy/course-content-dl/blob/main/projects/Neuroscience/pose_estimation.ipynb

# Motivation

Deep neural networks are influenced by stochastic processes such as parameter initialization and optimization. Consequently, independently trained models may exhibit different performance even when the architecture, hyperparameters, and dataset remain unchanged (Henderson et al., 2018; Åkesson et al., 2024).

To account for this variability, the model was trained five times using different random seeds. Robustness was then evaluated by comparing each trained model under identical perturbation conditions.

# Repository Overview
```
multirun_animal_pose_estimation_robustness/

├── README.md          # Project overview and documentation.
├── notebooks/         # Google Colab notebook containing the complete study.
├── models/            # Saved U-Net checkpoints.
├── results/           # Quantitative CSV files and summary statistics.
├── figures/           # Generated figures.
└── reports/           # Final report.
```
Running the notebook from beginning to end automatically:

- downloads and prepares the original Neuromatch dataset;
- installs any additional packages required for the extended analyses when needed;
- trains five independent U-Net models;
- evaluates baseline and perturbed conditions;
- computes quantitative robustness metrics and landmark-level analyses;
- generates robustness figures, CSV files, and statistical summaries;
- exports the trained model checkpoints, the final Word report, and a ZIP archive containing all generated outputs.

# Acknowledgements

This work was completed as part of the **Neuromatch Academy Deep Learning** program, July 2026.

I gratefully acknowledge Neuromatch Academy for providing the original notebook, dataset, training and educational materials on which this project is based.
