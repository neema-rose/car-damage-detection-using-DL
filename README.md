# 🚗 Car Damage Detection using Deep Learning

An AI-powered system that automatically detects and classifies vehicle damage from images using computer vision and deep learning.

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://car-damage-detection-using-dl.streamlit.app/)
[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-ResNet50-red.svg)](https://pytorch.org/)

**🔗 [Try the Live Application](https://car-damage-detection-using-dl.streamlit.app)**

---

## 📋 Table of Contents

- [Overview](https://github.com/neema-rose/car-damage-detection-using-DL/edit/main/README.md#-overview)
- [Problem Statement](https://github.com/neema-rose/car-damage-detection-using-DL/edit/main/README.md#-problem-statement)
- [Solution](https://github.com/neema-rose/car-damage-detection-using-DL/edit/main/README.md#-solution)
- [How It Works](https://github.com/neema-rose/car-damage-detection-using-DL/edit/main/README.md#%EF%B8%8F-how-it-works)
- [Technical Implementation](https://github.com/neema-rose/car-damage-detection-using-DL/edit/main/README.md#-technical-implementation)
- [Model Performance](https://github.com/neema-rose/car-damage-detection-using-DL/edit/main/README.md#-model-performance)
- [Installation & Usage](https://github.com/neema-rose/car-damage-detection-using-DL/edit/main/README.md#-installation--usage)
- [Skills Demonstrated](https://github.com/neema-rose/car-damage-detection-using-DL/edit/main/README.md#-skills-demonstrated)

---

## 🖼️ Application Screenshots
![Prediction Result-1](screenshots/prediction_result.png)
## 🎯 Overview

This project automates vehicle damage inspection using a deep learning model. It analyzes car images and classifies damage into 6 categories:

| Area | Condition |
|------|-----------|
| Front | Normal |
| Front | Breakage |
| Front | Crushed |
| Rear | Normal |
| Rear | Breakage |
| Rear | Crushed |

**Built for:** VROOM Cars (car resale company) as a Proof of Concept to evaluate AI-based inspection systems.

---

## 🔍 Problem Statement

Manual vehicle inspection is:
- ⏱️ Time-consuming and costly
- 🎲 Inconsistent (depends on human judgment)
- 📈 Not scalable for high-volume operations

**Goal:** Build an AI system with **≥75% accuracy** to automate damage classification and assist manual inspections.

---

## ✅ Solution

A complete end-to-end pipeline consisting of:

1. **Deep Learning Model** - ResNet-50 CNN with transfer learning
2. **Web Application** - Streamlit interface for easy interaction
3. **Image Processing** - Automated preprocessing pipeline
4. **Real-time Inference** - Instant damage predictions

**Key Achievement:** Successfully met the 75% accuracy threshold.

---

## 🛠️ How It Works

```
User Upload → Image Preprocessing → Best Model (ResNet-50) → Prediction → Display Result
```

**Step-by-step process:**

1. User uploads a car image through the web interface
2. Image is resized to 224×224 and normalized
3. ResNet-50 CNN analyzes visual features
4. Model outputs probability for each damage class
5. Highest probability class is displayed as the result

---

## 🧬 Technical Implementation

### Models Experimented

I built and compared **4 different approaches** to find the best solution:

| Approach | Description | Purpose |
|----------|-------------|---------|
| **1. Custom CNN** | Built from scratch | Baseline model to understand the problem |
| **2. CNN with Regularization** | Custom CNN + Dropout & L2 | Prevent overfitting, improve generalization |
| **3. Transfer Learning - EfficientNet** | Pretrained EfficientNet | Leverage efficient architecture |
| **4. Transfer Learning - ResNet-50** | Pretrained ResNet-50 | **Final selected model** ✅ |

### Why Multiple Models?

I experimented with different architectures to:
- Compare custom vs pretrained approaches
- Test different regularization strategies
- Find the optimal balance between accuracy and efficiency
- Validate that transfer learning outperforms custom models for limited datasets

### Final Model Architecture (ResNet-50)

- **Base Model:** ResNet-50 (pretrained on ImageNet)
- **Approach:** Transfer Learning
- **Customization:**
  - Froze early layers (kept general visual knowledge)
  - Unfroze final block (layer4) for fine-tuning
  - Replaced output layer with 6-class classifier

**Why ResNet-50 Won?**
After comparing all models, ResNet-50 with transfer learning provided the best accuracy. The pretrained model reuses knowledge about edges, shapes, and textures from ImageNet, then specializes in car damage patterns through fine-tuning.

### Image Preprocessing

All images undergo standardized preprocessing:
```python
- Convert to RGB
- Resize to 224 × 224
- Convert to PyTorch tensor
- Normalize using ImageNet statistics
```

### Training Process

- **Loss Function:** Cross-entropy
- **Optimization:** Backpropagation on unfrozen layers only
- **Validation:** Continuous monitoring to prevent overfitting
- **Hyperparameters Tuned:**
  - Learning rate
  - Batch size
  - Number of epochs
  - Dropout rate

### Deployment

- **Model Weights:** Saved as `saved_model.pth`
- **Framework:** Streamlit for web interface
- **Hosting:** Streamlit Cloud
- **Inference:** Real-time predictions on uploaded images

---

## 📊 Model Performance

✅ **Achieved >75% accuracy** on validation data

The model successfully:
- Distinguishes between front and rear damage
- Classifies damage severity (normal, breakage, crushed)
- Generalizes to unseen vehicle images

---

## 💻 Installation & Usage

### Prerequisites
```bash
Python 3.8+
PyTorch
Streamlit
PIL (Python Imaging Library)
torch
torchvision
gdown
```

### Local Setup
```bash
# Clone the repository
git clone <https://github.com/neema-rose/car-damage-detection-using-DL>
cd car-damage-detection

# Install dependencies
pip install -r requirements.txt

# Run the Streamlit app
streamlit run app.py
```

### Using the Application

1. Open the web interface
2. Upload a car image (front or rear view)
3. Wait for processing (~2-3 seconds)
4. View the damage classification result

---

## 🎓 Skills Demonstrated

This project showcases:
- Deep Learning & Transfer Learning
- Computer Vision & CNN Architecture
- Hyperparameter Tuning & Model Optimization
- Image Preprocessing & Data Pipeline
- ML Model Deployment & Web Development
- Building Production-Ready AI Systems
---

**⭐ If you find this project useful, please consider giving it a star!**
**Made with ❤️ and Python**
