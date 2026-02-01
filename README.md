# Accelerated Photocatalytic C-C Coupling via Interpretable Deep Learning

This repository contains the official implementation of the paper: **"ACCELERATED PHOTOCATALYTIC C-C COUPLING VIA INTERPRETABLE DEEP LEARNING: SINGLE-CRYSTAL PEROVSKITE CATALYST DESIGN USING FIRST-PRINCIPLES CALCULATIONS"**.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Data Description](#data-description)
- [Model Architecture](#model-architecture)
- [Results and Performance](#results-and-performance)
- [Installation](#installation)
- [Usage](#usage)
- [Citation](#citation)

---

## Project Overview
Photocatalytic C-C coupling reactions are essential for sustainable chemical synthesis. This research utilizes a computational approach, leveraging first-principles calculations to evaluate 158 single-crystal perovskite materials. By integrating a multi-head-attention mechanism with a ResNet architecture, we provide a robust tool for predicting bandgap values, which are critical for catalyst efficiency.

## Key Features
* **Deep Learning Integration**: Combines ResNet's residual learning with Multi-head Self-Attention for feature weighing.
* **Interpretable AI**: Focuses on 10 key physical and chemical descriptors selected from a pool of 38 features.
* **High Performance**: Outperforms traditional methods like Random Forest, MLP, and PCA in bandgap prediction tasks.

## Data Description
The dataset consists of 158 single-crystal perovskite materials. Feature selection was performed using Pearson correlation analysis to identify the most impactful descriptors.

### Selected Descriptors
1.  **Transition Metal Parameter** ($\eta$)
2.  **Group-A / Group-B** (Element groupings)
3.  **Pettifor Number**
4.  **$\chi M-B$ / $\chi P-B$** (Electronegativity)
5.  **$E_a-A$** (Activation Energy)
6.  **$C_B$** (Bonding Parameter)
7.  **$K_B$** (Bulk Modulus)
8.  **$R_a-B$** (Atomic Radii)

![figure1](docs/images/figure1.png)
*Figure 1: Heatmap of Pearson correlation analysis for feature selection.*

## Model Architecture
The model utilizes a **10-layer ResNet** backbone enhanced with a **Multi-head Attention** layer to capture complex inter-dependencies between the input descriptors.

![figure2](docs/images/figure2.png)
*Figure 2: Schematic of the Multi-head-Attention enhanced ResNet architecture.*

## Results and Performance
Our model demonstrates superior stability and predictive power compared to traditional regression and machine learning techniques.

| Model | Training $R^2$ | Test $R^2$ |
| :--- | :---: | :---: |
| **Proposed ResNet-Attention** | **0.819** | **0.803** |
| Random Forest | 0.946 | 0.581 |
| MLP (Multilayer Perceptron) | 0.792 | -66.437 |
| K-means | 0.583 | 0.031 |
| PCA | 0.439 | -0.10 |

![figure3](docs/images/figure3.png)
*Figure 3: Predicted vs. Actual bandgap values for the test set.*

## Installation

1.  **Clone the repository**:
    ```bash
    git clone [https://github.com/username/project-name.git](https://github.com/username/project-name.git)
    cd project-name
    ```

2.  **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

## Usage

### Training
To train the model from scratch using the provided dataset:
```bash
python train.py --data data/perovskite_data.csv --epochs 100
```

### Prediction
To use a pre-trained model for bandgap prediction:
```bash
python predict.py --input sample_descriptors.json
```

### Citation

If you use this code or the findings in your research, please cite:

```bibtex
@article{hao2025accelerated,
  title={Accelerated Photocatalytic C-C Coupling via Interpretable Deep Learning: Single-Crystal Perovskite Catalyst Design Using First-Principles Calculations},
  author={Hao, Yuze and Duo, Lan},
  journal={ICLR 2025},
  year={2025}
}
```
