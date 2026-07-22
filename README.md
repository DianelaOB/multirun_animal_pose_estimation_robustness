# Multi-Run Quantitative Robustness Analysis of the Neuromatch Animal Pose Estimator

This repository contains my individual extension of the original **Neuromatch Academy Animal Pose Estimation** project.

Rather than modifying the original U-Net architecture, I focused on extending the evaluation framework to study **how robust the trained model is when confronted with common image perturbations**. The main goal of this work was to distinguish variability introduced by stochastic model training from performance degradation caused by changes in the input images.

The original Neuromatch Academy notebook trains a single U-Net model and evaluates its performance on a fruit fly dataset containing 17 annotated anatomical landmarks. In this project, I kept the original model and training pipeline unchanged, but redesigned the evaluation procedure to perform a systematic quantitative robustness analysis across multiple independently trained models.

Original Neuromatch project:

https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html

---

# Motivation

Neural networks are inherently stochastic. Even when the architecture, hyperparameters, and training data remain identical, different random initializations can produce models with slightly different performance.

Because of this variability, conclusions based on a single trained model may not accurately represent the robustness of the method.

To better characterize model behavior, I trained the same U-Net architecture multiple times using different random seeds and evaluated each trained model under identical perturbation conditions.

The objective was not to improve the original Neuromatch model, but to develop a reproducible framework for measuring robustness quantitatively.

---

# Experimental Design

Several design decisions were intentionally made before implementing the robustness framework.

- The original Neuromatch U-Net architecture was kept unchanged.
- The optimizer, loss function, number of epochs, and training configuration were preserved.
- Five independent models were trained using different random seeds.
- The same validation dataset was used throughout all experiments.
- Image perturbations were applied only during evaluation.
- Every perturbation was compared with the corresponding baseline result from the same trained model.

These decisions allowed perturbation effects to be evaluated while minimizing confounding factors introduced by differences in training or evaluation.

---

# Repository Structure

```
multirun_animal_pose_estimation_robustness/

├── README.md
├── notebooks/
├── figures/
├── reports/
├── results/
├── models/
```

---

# Robustness Evaluation

Each independently trained model was evaluated under the original validation images together with several controlled perturbations.

The evaluated perturbations include:

- Mild Gaussian Blur
- Strong Gaussian Blur
- Gaussian Noise
- Brightness increase
- Contrast increase
- Central Occlusion

The landmark annotations remained unchanged throughout all perturbation experiments so that performance differences could be attributed only to changes in the input images.

---

# Quantitative Evaluation

For every independent training run, the following metrics were computed:

- Mean localization error
- Median localization error
- Standard deviation
- PCK@5
- PCK@10
- Landmark-level localization error
- Paired changes relative to baseline
- Summary statistics across runs

Instead of comparing different trained models directly, every perturbation was compared with the baseline performance obtained from the same model. This paired evaluation reduces the influence of differences caused by random initialization and provides a clearer estimate of the effect of each perturbation.

---

# Main Contributions

Compared with the original Neuromatch notebook, this repository adds:

- multiple independent training runs
- quantitative robustness evaluation
- paired baseline comparisons
- landmark-level robustness analysis
- exploratory statistical analyses
- automatic generation of figures
- automatic generation of quantitative reports
- CSV summaries for every experiment

---

# Running the Notebook

The project was developed in Google Colab.

Running the notebook from beginning to end will:

1. Load the dataset.
2. Train five independent U-Net models.
3. Evaluate baseline performance.
4. Apply every perturbation.
5. Compute quantitative robustness metrics.
6. Generate figures.
7. Export CSV tables.
8. Produce the final report.

Because all runs use the same validation split and training configuration, the resulting metrics can be compared directly across models.

---

# Outputs

The notebook automatically generates:

- trained model weights
- quantitative evaluation tables
- robustness figures
- CSV result files
- summary statistics
- final report

---

# Limitations

This work evaluates robustness using a single fruit fly dataset and one perturbation intensity for each evaluated condition.

Although five independent training runs provide a more reliable estimate of robustness than a single run, they do not completely characterize the variability of all possible trained models.

The statistical analyses included in this repository should therefore be interpreted as exploratory.

---

# Future Work

Possible extensions include:

- perturbation-based data augmentation during training
- rotations and translations
- multiple perturbation severity levels
- motion blur
- additional animal pose estimation datasets
- comparison with alternative pose estimation architectures

---

# Acknowledgements

This work extends the educational Animal Pose Estimation project developed for **Neuromatch Academy Deep Learning**.

The original notebook and dataset were provided by Neuromatch Academy.
