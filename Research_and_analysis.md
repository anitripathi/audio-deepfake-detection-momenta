# **Deepfake Model Research & Analysis**

## **Overview**

This document provides a comparative analysis of several models used for detecting audio deepfakes. It evaluates their strengths, limitations, and real-world applicability using the ASVspoof 2019 Logical Access (LA) dataset, aiming to identify the most effective solution for the project.

---

## **1\. Background**

The rise of audio deepfakes has been accelerated by advancements in text-to-speech (TTS) and voice conversion (VC) technologies. As these synthetic voices become more convincing, there is a growing need for dependable detection systems. Researchers have explored various models and strategies to address this challenge.

---

## **2\. Reviewed Models**

Three key models were chosen for comparison based on their widespread use, prior performance, and compatibility with the dataset.

### **2.1 RawNet2**

* **Input**: Raw audio waveform

* **Feature Handling**: End-to-end processing, no manual feature extraction required

* **Architecture**: Residual CNN blocks, GRU encoder, and fully connected layers

* **Strengths**: High accuracy, low error rate, and real-time readiness

### **2.2 LCNN (Light Convolutional Neural Network)**

* **Input**: Spectrogram images

* **Feature Handling**: Requires spectrogram extraction as a preprocessing step

* **Architecture**: Deep convolutional layers with max-feature map activations

* **Strengths**: Performs well under controlled conditions, easily interpretable

* **Limitations**: Less suitable for real-time implementation

### **2.3 X-vector \+ Cosine Similarity Scoring**

* **Input**: MFCC features

* **Feature Handling**: Preprocessed embeddings used for classification

* **Architecture**: Time-delay neural networks (TDNN)

* **Strengths**: Lightweight and efficient

* **Limitations**: Reduced accuracy in more complex spoofing scenarios

---

## **3\. Performance Comparison**

| Model | Feature Type | Accuracy (Dev Set) | Real-Time Suitable | Notes |
| ----- | ----- | ----- | ----- | ----- |
| RawNet2 | End-to-End | \~90% | Yes | Well-balanced performance |
| LCNN | Spectrogram | \~87% | No | Resource-intensive |
| X-vector \+ Cosine Scoring | MFCC | \~83% | Yes | Fast but less accurate |

---

## **4\. Distinction from Existing Projects**

Conventional approaches often depend on MFCCs or spectrograms, which involve significant preprocessing and are not ideal for real-time usage.

Our approach differs in that:

* It minimizes preprocessing by directly analyzing raw audio.

* RawNet2 is optimized for real-world scenarios and scalability.

* Performance is validated on a demanding benchmark (ASVspoof 2019 LA), ensuring its applicability.

---

## **5\. Conclusion**

RawNet2 emerged as the most effective model for our goals, offering a balanced combination of accuracy, speed, and ease of deployment. This makes it a strong candidate for real-world anti-spoofing systems.

Future exploration will focus on integrating transformer-based models and applying domain adaptation techniques to improve robustness across datasets.

