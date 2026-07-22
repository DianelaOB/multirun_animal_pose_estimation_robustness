# Multi-Run Quantitative Robustness Analysis of the Neuromatch Animal Pose Estimator

This repository documents my individual extension of the official **Neuromatch Academy Animal Pose Estimation** project.

The original Neuromatch notebook trains and evaluates a U-Net model for landmark localization in *Drosophila melanogaster* images using the architecture proposed by Ronneberger et al. (2015). This project extends the original notebook by evaluating model robustness across multiple independent training runs under controlled image perturbations while preserving the original training pipeline.

**Original Neuromatch Academy project**

https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html

# Motivation

Deep neural networks are influenced by stochastic processes such as parameter initialization and optimization. Consequently, independently trained models may exhibit different performance even when the architecture, hyperparameters, and dataset remain unchanged (Henderson et al., 2018; Åkesson et al., 2024).

To account for this variability, the model was trained five times using different random seeds. Robustness was then evaluated by comparing each trained model under identical perturbation conditions.

# Repository Organization

This project was developed in **Google Colab** by extending the official **Neuromatch Academy Animal Pose Estimation** notebook https://colab.research.google.com/github/NeuromatchAcademy/course-content-dl/blob/main/projects/Neuroscience/pose_estimation.ipynb
It provides the dataset download procedure, model implementation, visualization utilities, and training pipeline. During the project, additional Markdown and code cells were incorporated to implement repeated training runs, robustness experiments, quantitative analyses, statistical summaries, and automated report generation.

Running the notebook from beginning to end automatically:

- downloads and prepares the original Neuromatch dataset;
- installs any additional packages required for the extended analyses when needed;
- trains five independent U-Net models;
- evaluates baseline and perturbed conditions;
- computes quantitative robustness metrics and landmark-level analyses;
- generates robustness figures, CSV files, and statistical summaries;
- exports the trained model checkpoints, the final Word report, and a ZIP archive containing all generated outputs.

```
multirun_animal_pose_estimation_robustness/

├── README.md          # Project overview and documentation.
├── notebooks/         # Google Colab notebook containing the complete study.
├── models/            # Saved U-Net checkpoints.
├── results/           # Quantitative CSV files and summary statistics.
├── figures/           # Generated figures.
└── reports/           # Final report.
```

 # Acknowledgements

This work was developed during **Neuromatch Academy Deep Learning**.

The original notebook, dataset, and training pipeline were provided by Neuromatch Academy. This repository documents the additional robustness experiments and quantitative analyses developed during the project.
