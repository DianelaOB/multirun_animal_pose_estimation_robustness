# Multi-Run Robustness Evaluation of Animal Pose Estimation

This repository extends the original **Neuromatch Academy Animal Pose Estimation** notebook.

The original notebook trains and evaluates a single U-Net model to detect 17 anatomical landmarks in grayscale images of fruit flies. In this project, I expanded the evaluation by training the same model five independent times using different random seeds. The objective was to study how consistent the model is across different training runs and how its performance changes when the input images are affected by common perturbations.

The original Neuromatch notebook is available here:

https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html

---

# Repository structure

```text
multirun_animal_pose_estimation_robustness/
├── README.md
├── notebooks/      # Main Colab notebook
├── figures/        # Generated figures
├── results/        # CSV files with evaluation results
├── reports/        # Final report
└── models/         # Saved model weights
```

---

# Project overview

The original training pipeline was kept unchanged, including the U-Net architecture, optimizer, loss function, and training settings. The main difference is that the model is trained five times instead of once.

After training, each model is evaluated on the same validation set under the original images and under several image perturbations. This makes it possible to compare the effect of each perturbation while also measuring the variability between independent training runs.

---

# Image perturbations

The following perturbations are applied during evaluation:

* Mild Gaussian blur
* Strong Gaussian blur
* Gaussian noise
* Increased brightness
* Increased contrast
* Central occlusion

These perturbations only modify the appearance of the images. The landmark coordinates remain unchanged.

---

# Evaluation

For every trained model, the notebook computes:

* Mean localization error
* Median localization error
* PCK@5
* PCK@10
* PCK@20
* Landmark-level localization error

The performance obtained under each perturbation is compared with the baseline performance of the same model. This paired comparison makes it easier to evaluate how much each perturbation affects the predictions.

---

# Running the notebook

The notebook was developed in **Google Colab**.

Running the notebook from beginning to end will:

1. Load the dataset.
2. Train five U-Net models using different random seeds.
3. Evaluate each model on the validation set.
4. Apply all perturbation conditions.
5. Generate figures and CSV files.
6. Create the final report.

The same validation split and training configuration are used for every run so that the results can be compared directly.

---

# Outputs

After running the notebook, the following files are generated:

* trained model weights;
* evaluation tables;
* robustness figures;
* CSV files containing the quantitative results;
* a final report summarizing the study.

---

# Future work

Possible extensions of this project include:

* using perturbation-based data augmentation during training;
* evaluating additional perturbation types, such as rotations or motion blur;
* testing different perturbation strengths;
* comparing other pose estimation architectures.

---

# Original project

This work is based on the **Animal Pose Estimation** notebook developed by **Neuromatch Academy**.

https://deeplearning.neuromatch.io/projects/Neuroscience/pose_estimation.html
