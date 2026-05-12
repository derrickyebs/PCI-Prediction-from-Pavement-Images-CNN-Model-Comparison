# PCI-Prediction-from-Pavement-Images-CNN-Model-Comparison

 A comparative study of five deep learning architectures to predict Pavement Condition Index (PCI) directly from raw images.

## 📌 Project Overview
Traditional pavement surveys are time-intensive, subjective, and hazardous. This project automates the calculation of the Pavement Condition Index (PCI) by evaluating five distinct Convolutional Neural Network (CNN) architectures. The goal is to develop an AI framework capable of directly predicting a continuous PCI score (0-100) from raw pavement images, effectively turning manual civil engineering surveys into an automated computer vision task.

## 📊 The Dataset
The project utilizes a dataset of **7,704 pavement images**. Since data is sometimes messy,a robust preprocessing pipeline was implemented:
* **Anomaly Removal:** 17 images with impossible negative scores were zeroed out, and 2 corrupted files were skipped programmatically.
* **Class Imbalance Mitigation:** 2,259 images (29.3%) recorded perfect PCI scores of 100. To prevent the model from skewing its predictions, the data was stratified by binning the continuous scores into groups of 10.
* **Data Split:** Models were trained using an **80/10/10** (Train/Validation/Test) split.

## 🧠 Evaluated Architectures (The Models)
To determine the optimal balance between accuracy and computational efficiency, the following models were trained in PyTorch for 30 epochs each:

1. **ResNet50:** The baseline model for general feature extraction.
2. **ResNet50 + CBAM:** A custom implementation injecting a Convolutional Block Attention Module to force the network to focus on pavement distresses and ignore background noise (shadows, bitumen spills).
3. **DenseNet121:** Utilizes dense reuse of features, making it highly effective for extracting the complex, interlocking textures of asphalt.
4. **EfficientNet B0:** Designed to offer high-accuracy predictive power with minimal computational overhead.
5. **MobileNetV3:** A lightweight model evaluated specifically for potential edge-device deployment (e.g., drones, smartphones).

## 🏆 Key Results & Performance
The models test performance were evaluated using Mean Absolute Percenatage Error (MAPE).

| Model | MAPE | 
| :--- | :--- |
| **ResNet50** | 47.86 |
| **ResNet50 + CBAM** | 45.46 |
| **EfficientNet B0** | **45.24** | 
| **DenseNet121** | 43.79 |
| **MobileNetV3** | 52.97 | 

### Core Conclusions:
* **Dense and Efficient architectures** (DenseNet121, EfficientNet B0) delivered the best overall performance.
* **Attention mechanisms (CBAM)** consistently add value by teaching the model *where* to look.
* **Lightweight models** are not as viable for continuous PCI regression due to the complexity of pavement textures.

Any feedback shall be greatly appreciated

email:derrickyebs@gmail.com
