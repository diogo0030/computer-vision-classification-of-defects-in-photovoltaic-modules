# Classification of Defects in Photovoltaic Modules

This project implements a Deep Learning pipeline for the automatic detection and classification of anomalies in thermal images of photovoltaic (PV) modules. Developed as part of the Computer Vision course (Assignment 2) at FEUP (2025/2026), it aims to automate the inspection process of solar farms by identifying defects such as hotspots, cracking, or vegetation to maintain energy efficiency and prolong equipment lifespan.

The solution leverages Convolutional Neural Networks (CNNs) and Transfer Learning, utilizing the Raptor Maps Infrared Solar Modules dataset (20,000 images).

### Grade: ??

---

## Overview

Thermal inspection is a critical non-invasive technique for assessing the health of PV modules. Manual analysis of thousands of infrared images is time-consuming and error-prone. This project automates this process using Convolutional Neural Networks.

We developed and compared three AI models to classify thermal images:
1.  **Binary Classification:** Anomaly vs. No-Anomaly.
2.  **11-Class Classification:** Detailed classification of specific defects (e.g., Cell, Hot-Spot, Diode).
3.  **12-Class Classification:** The full range of 11 anomaly types plus the "No-Anomaly" class.

## Features and Methodology

Our approach focuses on robust data preparation to handle the specific challenges of thermal imagery (low contrast) and dataset imbalance.

### 1. Preprocessing Pipeline
* **Unsharp Masking:** Applied a sharpening filter (Radius=2, Amount=150%) to enhance the thermal edges of defects, making subtle anomalies like *Cracking* more visible to the network.
* **Resolution:** All images were resized to **128x128** (upscaled from the original low resolution) to preserve spatial details.
* **Stratified Split:** Data divided into 80% Train, 10% Validation, and 10% Test before augmentation to prevent data leakage.

### 2. Hybrid Data Augmentation
We implemented a two-stage augmentation strategy to solve class imbalance and overfitting:
* **Offline Augmentation (Balancing):** Used to physically generate new images for minority classes (e.g., *Diode-Multi*, *Soiling*) before training. We targeted **3000 images per class** using aggressive transformations (flips, rotations) to eliminate statistical bias.
* **Online Augmentation (Generalization):** Applied dynamic transformations during training (Random Affine, Color Jitter, Random Flips) to ensure the model never sees the exact same image twice, increasing robustness.

### 3. Model Architectures
* **Custom CNN:** A lightweight Convolutional Neural Network built from scratch with 4 convolutional blocks, Batch Normalization, and Dropout.
* **ResNet18 (Transfer Learning):** Adaptation of the pre-trained ResNet18 architecture. The first layer was modified to accept 1-channel grayscale inputs, leveraging features learned from ImageNet to improve performance on the complex 11-class task.

---

## Results and Performance

We conducted extensive experiments to compare the impact of Data Augmentation and Model Architecture.

### Key Findings:

* **Impact of Balancing:** The **Offline Augmentation** strategy was crucial. Without it, models achieved high accuracy by simply predicting the majority classes (*Cell*, *Vegetation*) while failing to detect critical rare defects (*Diode*, *Hot-Spot-Multi*). Balancing the classes to 3000 samples equalized the F1-Scores across categories.
* **Architecture Comparison:**
    * In **Binary Classification**, the **Custom CNN** proved highly efficient, achieving competitive results (~72% Accuracy) with significantly fewer parameters than pre-trained models.
    * In **Multi-Class Classification (11/12 classes)**, the **ResNet18** outperformed the Custom CNN. The complexity of distinguishing between visually similar defects (e.g., *Hot-Spot* vs. *Cell*) benefited from the deeper architecture and transfer learning.
* **Visual Enhancement:** The use of **Unsharp Masking** improved the convergence rate of the models by emphasizing the boundaries of thermal anomalies, which are often blurry in raw infrared images.

---


## Authors

* **Afonso Tomas de Magalhaes Mateus** (202204126)
* **Diogo Soares de Albergaria Oliveira** (202108325)

## References

This work is based on state-of-the-art research in PV fault detection:
* *Ramadan, E.A., et al.* (2024). "An innovative transformer neural network for fault detection and classification for photovoltaic modules". Energy Conversion and Management.
* *Le, M., et al.* (2023). "Thermal inspection of photovoltaic modules with deep convolutional neural networks on edge devices in AUV". Measurement.

---

**Note:** This project was developed for academic purposes.
