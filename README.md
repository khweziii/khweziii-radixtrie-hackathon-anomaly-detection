
# RadixTrie Hackathon: Time Series Anomaly Detection
[![python](https://img.shields.io/badge/Python-3.9-3776AB.svg?style=flat&logo=python&logoColor=white)](https://www.python.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 🚀 Project Overview
This repository contains my submission for the RadixTrie hackathon, focused on time series anomaly detection. The challenge was to identify unusual patterns or values in time-ordered data, a critical task for automatically monitoring the health of thousands of databases. My solution leverages a deep learning approach to learn the "normal" behavior of the time series and then flag any significant deviations.

## 🔧  Model and Methodology
For this problem, I chose an **LSTM Autoencoder**. This type of model is particularly well-suited for time series data because:

**LSTM (Long Short-Term Memory) Network**: LSTMs are a type of recurrent neural network (RNN) that can learn and remember patterns over long sequences of data, making them excellent for capturing the complex, time-dependent nature of the chaotic systems used in the synthetic data.

**Autoencoder**: The autoencoder is trained to compress the time series data into a lower-dimensional representation (the "latent space") and then reconstruct it back to its original form.

The core idea for anomaly detection is that the model is trained exclusively on normal data. When it is presented with an anomalous data point, it will struggle to reconstruct it accurately because it has not learned that pattern. The difference between the original data and the reconstructed data is the reconstruction error, which serves as our anomaly score. Any data point with a reconstruction error above a set threshold is classified as an anomaly.

#### ⚙️  Model Parameters
My final model was configured with the following parameters:

- Batch Size: 32
- Epochs: 10
- Window Size: 10
- Latent Dimension: 8
- Learning Rate: 0.001

## 🏗️ Anomaly Detection Process

The process for detecting anomalies using this model is as follows:

- The LSTM Autoencoder is trained on the provided train_files  (containing only normal data).

- After training, the model's performance is evaluated by its reconstruction error on the normal data. A threshold is then set, typically based on a statistical measure like the 95th or 99th percentile of the reconstruction errors.

- The model is then applied to the test_files. For each time series in the test set, the reconstruction error is calculated.

- Any data point where the reconstruction error exceeds the predefined threshold is flagged as an anomaly.

### 🚀 Quick Start
1. **Clone the repository**
   ```bash
   git clone <repository-url>
   ```
2. **Set up virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
## 🌟 Acknowledgments
- RadixTrie
- Deep Learning IndabaX South Africa 2025