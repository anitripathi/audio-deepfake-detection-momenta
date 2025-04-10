
# 🎤 Audio Deepfake Detection using RawNet2 (ASVspoof 2019)

A deep learning-based solution for detecting audio deepfakes using the **RawNet2** architecture. Trained on the **ASVspoof 2019 Logical Access (LA)** dataset, this project classifies audio clips as either genuine (bonafide) or fake (spoofed).

---

## 🔎 1. Why Audio Deepfake Detection?

With the rapid evolution of AI voice synthesis (like deepfake voice cloning), detecting audio-based spoofing has become critical for protecting biometric authentication systems, online meetings, and voice-activated devices from malicious attacks.

---

## 🎯 2. Why RawNet2?

We explored three models for this project:

1. **RawNet2**
2. **LCNN (Light CNN)**
3. **X-vector + Cosine Scoring**

After evaluating architecture complexity, performance, and adaptability to raw waveform inputs, we selected **RawNet2** as the final model.

### 🔍 2.1 Model Comparison Table

| Model                 | Input Type       | Architecture Type         | Feature Extraction | Accuracy (on LA) | Complexity | Real-Time Capability | Notes                                                                 |
|----------------------|------------------|----------------------------|---------------------|------------------|------------|-----------------------|-----------------------------------------------------------------------|
| **RawNet2**           | Raw Waveform     | CNN + GRU (End-to-End)     | ✅ Learned features | **85–90%**        | Moderate   | ✅ Yes                 | Best performance, real-time ready, no manual preprocessing required   |
| **LCNN (Light CNN)**  | Spectrogram (FFT)| CNN + Max-Feature-Map      | ❌ Manual features  | ~82–85%           | High       | ❌ No                  | Heavy preprocessing and slower inference                              |
| **X-vector + Cosine**| MFCC             | DNN + Cosine Similarity    | ❌ Manual features  | ~78–80%           | Low        | ✅ Yes                 | Simple but less accurate, mainly designed for speaker verification    |

### ✅ 2.2 Why RawNet2 Wins

- **End-to-End Learning**: Processes raw waveform input directly, removing the need for manual feature extraction.
- **Performance**: Outperforms other models in terms of accuracy and adaptability to deepfake variations.
- **Efficiency**: Lightweight and real-time capable, suitable for real-world deployment.
- **Designed for Anti-Spoofing**: RawNet2 was proposed for voice spoof detection challenges and is optimized for such tasks.

---

## 📂 3. Dataset: ASVspoof 2019 (Logical Access)

- **Dataset Link**: [ASVspoof 2019 - Logical Access](https://datashare.ed.ac.uk/handle/10283/3336)
- **Subset Used**: `train`, `dev`, and `eval` under the `LA` folder
- **Formats**: `.flac` audio files + protocol `.txt` files
- ⚠️ **Note**: Due to licensing restrictions, the dataset must be downloaded manually.

---

## 🚀 4. Installation

```bash
git clone https://github.com/anitripathi/audio-deepfake-detection-momenta.git
cd audio-deepfake-detection-momenta

# (Optional) Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

---

## 📈 5. Usage

### 5.1 Train the model

```bash
python train.py
```

### 5.2 Visualize an audio waveform

```bash
python waveform_plot.py
```

### 5.3 Inference (coming soon)

The inference script will allow you to test your own audio samples with the trained RawNet2 model.

---

## 🧠 6. Model Architecture: RawNet2

```
Input: Raw waveform
 └── Conv1D Layers (feature extractor)
     └── Residual Blocks
         └── GRU Layer (temporal encoding)
             └── Fully Connected + Softmax
Output: Bonafide / Spoof
```

- Combines convolutional feature extraction with temporal modeling.
- End-to-end anti-spoofing architecture tailored for biometric ASV systems.

---

## 📊 7. Results

| Metric       | Value     |
|--------------|-----------|
| Accuracy     | ~85–90%   |
| Epochs       | 5         |
| Optimizer    | Adam      |
| Loss         | BCE Loss  |

> Results may vary based on the system and training splits.

---

## 📁 8. Folder Structure

```
audio-deepfake-detection-momenta/
├── models/                  # RawNet2 model definition
├── train.py                 # Model training script
├── visualize.ipynb          # Audio waveform visualization
├── UTILS/                   # Utility functions and dataset loader
├── requirements.txt         # Python dependencies
└── README.md                # Project overview
```

---

## 👥 9. Contributing

Pull requests are welcome! If you find bugs or want to improve the project, feel free to fork and submit PRs.

---

## 👨‍💼 10. Author

**Anivesh Tripathi**  
📧 aniveshtripathi.in@gmail.com  
🔗 [GitHub](https://github.com/anitripathi)

---

## 🌟 11. Acknowledgements

- ASVspoof 2019 Organizing Team  
- RawNet2 Paper by Heo et al.  
- PyTorch and Open-Source ML Community
