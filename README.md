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


## Results and Performance

We conducted extensive experiments to compare the impact of Data Augmentation and Model Architecture.

### Key Findings:


## Authors

* **Afonso Tomas de Magalhaes Mateus** (202204126)
* **Diogo Soares de Albergaria Oliveira** (202108325)

## References

This work is based on state-of-the-art research in PV fault detection:
* *Ramadan, E.A., et al.* (2024). "An innovative transformer neural network for fault detection and classification for photovoltaic modules". Energy Conversion and Management.
* *Le, M., et al.* (2023). "Thermal inspection of photovoltaic modules with deep convolutional neural networks on edge devices in AUV". Measurement.

---

**Note:** This project was developed for academic purposes.
