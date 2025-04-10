# 🎤 Audio Deepfake Detection using RawNet2 (ASVspoof 2019)

A deep learning-based solution for detecting audio deepfakes using the **RawNet2** architecture. Trained on the **ASVspoof 2019 Logical Access (LA)** dataset, this project classifies audio clips as either genuine (bonafide) or fake (spoofed).

---

## 🔎 Why Audio Deepfake Detection?
With the rapid evolution of AI voice synthesis (like deepfake voice cloning), detecting audio-based spoofing has become critical for protecting biometric authentication systems, online meetings, and voice-activated devices from malicious attacks.

---

## 🎯 Why RawNet2?

We explored three models for this project:

1. **RawNet2**
2. **LCNN (Light CNN)**
3. **X-vector + Cosine Scoring**

After evaluating architecture complexity, performance, and adaptability to raw waveform inputs, we selected **RawNet2** for the following reasons:

### ✔ RawNet2 Advantages
- **Raw audio input**: Works directly with waveform input, eliminating hand-crafted feature extraction (e.g., MFCC).
- **End-to-end learning**: Learns the most relevant features for spoof detection via CNN + GRU.
- **Superior performance**: Benchmarked with state-of-the-art results on the ASVspoof 2019 dataset.
- **Real-time ready**: Lightweight and faster inference compared to LCNN.

> ⚡ RawNet2 is specifically designed for anti-spoofing and has been tested against various voice synthesis and voice conversion attacks.

---

## 🔹 Dataset: ASVspoof 2019 (Logical Access)

- **Dataset Link**: [ASVspoof 2019 - Logical Access](https://datashare.ed.ac.uk/handle/10283/3336)
- **Subset used**: `train`, `dev`, and `eval` under `LA` folder
- **Formats**: .flac audio + protocol files (.txt)
- **Note**: Due to licensing, we do not host the dataset. You must download it manually.

---

## 🚀 Installation

```bash
git clone https://github.com/anitripathi/audio-deepfake-detection-momenta.git
cd audio-deepfake-detection-momenta

# (Optional) Virtual environment
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Install requirements
pip install -r requirements.txt
```

---

## 📈 Usage

### 1. Train the model
```bash
python train.py
```

### 2. Visualize audio waveform
```bash
python waveform_plot.py
```

### 3. Inference (coming soon)
Inference script will allow you to test your own audio samples with the trained RawNet2 model.

---

## 📊 Model Architecture: RawNet2

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

## 📊 Results

| Metric       | Value     |
|--------------|-----------|
| Accuracy     | ~85-90%   |
| Epochs       | 5         |
| Optimizer    | Adam      |
| Loss         | BCE Loss  |

> Final results may vary slightly depending on the training split and hardware.

---

## 📂 Folder Structure

```
audio-deepfake-detection-momenta/
├── models/                          # RawNet2 model definition
├── train.py                        # Model training script
├── UTILS/                         # include the dataset traing 
├── requirements.txt
└── README.md
```

---

## 👥 Contributing

Pull requests are welcome! If you find bugs or have feature suggestions, feel free to open an issue.

---

---

## 👨‍💼 Author

**Anivesh Tripathi**  
📧 aniveshtripathi.in@gmail.com  
🔗 [GitHub](https://github.com/anitripathi)

---

## 🌟 Acknowledgements

- ASVspoof 2019 Organizing Team
- RawNet2 Paper by Heo et al.
- PyTorch Community


