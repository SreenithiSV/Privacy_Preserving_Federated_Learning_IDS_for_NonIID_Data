# Privacy-Preserving Heterogeneous Federated Learning Intrusion Detection System for Non-IID Data

This project implements a **privacy-preserving heterogeneous federated learning framework** for **network intrusion detection**. The system enables multiple clients to collaboratively train deep learning models while keeping their local data private. Instead of sharing raw data or model parameters, the framework exchanges **encrypted model outputs (logits)** and performs **secure aggregation using homomorphic encryption**. This approach supports collaboration across heterogeneous client architectures while preserving data confidentiality.

## Overview

Modern network infrastructures generate large volumes of distributed traffic data across IoT devices, enterprise systems, and critical infrastructures. Centralized training of intrusion detection models is often impractical due to **privacy concerns, regulatory restrictions, and scalability challenges**. Federated learning addresses this problem by enabling collaborative model training without transferring raw data.

However, conventional federated learning systems face two major challenges:

- **Data heterogeneity** – Network traffic data across organizations are highly non-IID.
- **Model heterogeneity** – Clients may use different neural network architectures depending on computational constraints.

This project proposes a framework that addresses these challenges through **secure logit aggregation and cross-model knowledge distillation**.

## Key Features

- Privacy-preserving federated learning
- Support for heterogeneous client models
- Homomorphic encryption using **CKKS**
- Differential privacy through clipping and noise injection
- Knowledge distillation for cross-model collaboration
- Weighted aggregation for improved robustness
- Ensemble-based global evaluation

## Framework Architecture

The system follows a **client-server federated learning workflow**:

1. Each client trains a local deep learning model on private data.
2. Clients compute representative **logits on a shared input dataset**.
3. Logits are protected using **differential privacy mechanisms**.
4. The logits are encrypted using **CKKS homomorphic encryption**.
5. The server performs **secure aggregation on encrypted logits**.
6. Clients decrypt the aggregated logits and perform **knowledge distillation** to update their models.

This process repeats across multiple federated learning rounds, enabling collaborative learning without exposing sensitive information.

## Client Model Diversity

To simulate realistic decentralized environments, each client uses a different neural network architecture. Example architectures include:

- Multi-Layer Perceptron (MLP)
- Residual MLP
- Bidirectional GRU
- Attention-based tabular neural network
- 1D Convolutional Neural Network

Supporting heterogeneous models allows the system to operate effectively in environments where devices have different computational resources and deployment requirements.

## Privacy Mechanisms

### Homomorphic Encryption
The framework uses **CKKS homomorphic encryption**, implemented using the TenSEAL library. Client logits are encrypted before transmission, allowing the server to aggregate them without accessing plaintext values.

### Differential Privacy
To further protect client information, the system applies:

- Gradient clipping
- Gaussian noise injection

These mechanisms prevent sensitive information leakage from client updates.

## Training Process

The training pipeline follows a **round-based federated learning strategy**:

1. Local client training
2. Logit generation on shared inputs
3. Differential privacy protection
4. Homomorphic encryption
5. Secure server aggregation
6. Knowledge distillation updates
7. Iterative federated rounds

This design enables collaboration among heterogeneous models without requiring parameter sharing.

## Evaluation

Model performance is evaluated using:

- Accuracy
- Weighted F1-score
- Client-wise validation metrics
- Global ensemble predictions

An **ensemble of all client models** is used for final evaluation to improve generalization and detection performance.

## Requirements

The project requires the following Python libraries:

- PyTorch
- NumPy
- Pandas
- Scikit-learn
- TenSEAL
- Matplotlib
- Seaborn
