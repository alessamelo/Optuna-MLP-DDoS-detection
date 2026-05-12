<div align="center">

# Multi-Objective Optimization of DDoS Detection using Optuna and Neural Networks

### Cybersecurity Network Traffic Analysis Project

**Developed by:**  
Daniel Troya  
Alessa Melo  

**Supervised by:**  
Juan Pablo Astudillo

</div>

---

# Project Overview

This project focuses on the development and optimization of a deep learning model for cybersecurity network traffic classification, specifically targeting the detection of Distributed Denial of Service (DDoS) and flooding attacks.

The main objective of this research is to analyze the trade-off between:

- Maximizing the F1-score
- Minimizing prediction time

To achieve this, a multi-objective hyperparameter optimization study was conducted using **Optuna**.

---

# Study Configuration

The Optuna study was configured with the following parameters:

```python
RANDOM_STATE = 42
N_TRIALS = 100
N_RUNS_TIMING = 10

# Hidden layer size range
HIDDEN_SIZE_MIN = 32
HIDDEN_SIZE_MAX = 256

# Number of hidden layers
NUM_LAYERS_MIN = 1
NUM_LAYERS_MAX = 5

# Learning rate range
LR_MIN = 1e-5
LR_MAX = 1e-2

# Batch size options
BATCH_SIZES = [32, 64, 128]

# Optimization directions
DIRECTIONS = ["maximize", "minimize"]
```

---

# Optimization Objectives

This project implements a multi-objective optimization problem in which the neural network architecture is optimized according to two conflicting goals:

| Objective | Description |
|---|---|
| Maximize F1-score | Improve attack detection performance |
| Minimize prediction time | Reduce inference latency for real-time systems |

This methodology allows the identification of models that achieve a balance between classification performance and computational efficiency.

---

# Dataset Description

The project uses the following dataset:

## Cybersecurity Network Traffic Dataset: Baseline

This dataset contains network traffic records used for cybersecurity analysis, specifically focused on detecting:

- Distributed Denial of Service (DDoS) attacks
- Reflection attacks
- Amplification attacks
- Flooding attacks

Each CSV file corresponds to a specific attack type or normal network behavior.

---

# Available Dataset Files

| File | Description |
|---|---|
| `DrDoS_DNS.csv` | DNS amplification Distributed Reflection Denial of Service attack traffic |
| `DrDoS_LDAP.csv` | LDAP reflection DDoS attack traffic |
| `DrDoS_MSSQL.csv` | MSSQL reflection DDoS attack traffic |
| `DrDoS_NetBIOS.csv` | NetBIOS reflection DDoS attack traffic |
| `DrDoS_NTP.csv` | NTP amplification attack traffic |
| `DrDoS_SNMP.csv` | SNMP reflection DDoS attack traffic |
| `DrDoS_SSDP.csv` | SSDP reflection DDoS attack traffic |
| `DrDoS_UDP.csv` | UDP flood distributed denial of service traffic |
| `Syn.csv` | SYN flood attack traffic |

---

# Dataset Selection

Due to computational limitations, only a subset of the dataset was selected for training and experimentation.

The selected datasets were:

- `DNS.csv`
- `LDAP.csv`
- `NTP.csv`
- `Syn.csv`

These datasets were selected because they represent some of the most common and relevant reflection and amplification attack scenarios in modern cybersecurity environments.

---

# Reflection and Amplification Attacks

In reflection-based DDoS attacks:

1. The attacker sends requests using a spoofed IP address.
2. The spoofed address corresponds to the victim.
3. Legitimate servers respond to the victim instead of the attacker.
4. Massive traffic overwhelms the target system.

Protocols such as DNS, LDAP, and NTP are commonly abused because their responses are significantly larger than the original requests, amplifying attack traffic.

---

# Data Processing Pipeline

The dataset preprocessing pipeline consisted of multiple stages designed to improve model performance and prevent data leakage.

---

## 1. Initial Dataset Cleaning

The original dataset was cleaned to:

- Remove invalid values
- Handle corrupted records
- Eliminate unnecessary features
- Standardize data consistency

---

## 2. Train-Test Split

After preprocessing, the dataset was divided into:

- Training set
- Testing set

The testing set remained untouched during training to ensure realistic evaluation results.

---

## 3. Training Data Balancing

The training set contained class imbalance due to the natural distribution of network traffic records.

To address this issue, undersampling techniques were applied in order to artificially balance the classes.

This process reduced the dominance of majority classes and improved learning stability during training.

---

## 4. Secondary Split (Train / Validation)

After balancing, the modified training dataset was split again into:

- Training set
- Validation set

The validation set was used during Optuna optimization and neural network training.

---

## 5. Final Evaluation

After training and optimization, the final evaluation was performed using the original untouched testing dataset.

This methodology ensures realistic performance measurements and prevents evaluation bias.

---

# Neural Network Architecture

The neural network architecture was dynamically generated during the Optuna optimization process.

The following hyperparameters were explored:

| Hyperparameter | Range |
|---|---|
| Hidden layer size | 32 → 256 |
| Number of hidden layers | 1 → 5 |
| Learning rate | 1e-5 → 1e-2 |
| Batch size | 32, 64, 128 |

This allowed Optuna to search for architectures that achieved the best trade-off between classification quality and inference speed.

---

# Evaluation Metrics

The primary evaluation metric was:

## F1-score

F1-score was selected because cybersecurity datasets are often highly imbalanced.

This metric combines:

- Precision
- Recall

into a single value that better reflects attack detection performance.

---

# Inference Time Analysis

In addition to classification performance, this project also evaluates:

- Prediction latency
- Computational efficiency
- Real-time applicability

Prediction time was measured multiple times:

```python
N_RUNS_TIMING = 10
```

The average inference time was then used as the second optimization objective.

---

# Optuna Multi-Objective Optimization

Optuna was used to generate and evaluate multiple neural network configurations.

The study explored:

- Different architectures
- Different learning rates
- Different batch sizes

while simultaneously optimizing:

```python
DIRECTIONS = ["maximize", "minimize"]
```

Meaning:

- Maximize F1-score
- Minimize prediction time

The result is a Pareto front containing models with different trade-offs between speed and classification performance.

---

# Expected Results

The project aims to obtain:

- High-performance DDoS detection models
- Reduced prediction latency
- Efficient real-time inference
- Balanced neural network architectures

This type of optimization is highly relevant for modern intrusion detection systems where both accuracy and response speed are critical.

---

# Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| PyTorch / TensorFlow | Neural network implementation |
| Optuna | Hyperparameter optimization |
| Pandas | Data manipulation |
| NumPy | Numerical computation |
| Scikit-learn | Metrics and preprocessing |

---

# Conclusion

This project demonstrates the application of:

- Multi-objective optimization
- Deep learning
- Cybersecurity traffic analysis

for the detection of DDoS attacks using neural networks.

By combining Optuna optimization with careful dataset preprocessing and balanced training strategies, the project seeks to develop models that are both accurate and computationally efficient for real-world cybersecurity environments.

---

<div align="center">

### Developed by Daniel Troya and Alessa Melo  
### Supervised by Juan Pablo Astudillo

</div>
