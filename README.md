# Data-Centric Pneumonia Segmentation

A two-stage data-centric learning framework for improving pneumonia segmentation in chest X-ray images through self-supervised learning and hard example mining.

## 📄 Overview

This repository contains the implementation and research materials for **"Improving Pneumonia Segmentation via a Two-Stage Data-Centric Learning Framework"**, presented at the 16th IEEE Symposium on Computer Applications & Industrial Electronics (ISCAIE 2026).

### Key Innovation

Rather than focusing on architectural complexity, this framework prioritizes **data quality and training dynamics** to achieve superior segmentation performance in clinical settings with:

- Limited annotated data
- Noisy labels
- Class imbalance challenges

## 🎯 Core Contributions

1. **Self-Supervised Auto-Labeling (Stage 1)**
   - Contrastive learning models (SimCLR & BYOL) trained on unlabeled CXR images
   - Pseudo-label generation with confidence filtering
   - Significant reduction in annotation noise and improved label consistency

2. **Data-Centric Training with Augmentation & OHEM (Stage 2)**
   - AI-driven augmentation (GAN-based, diffusion-based, CutMix)
   - Online Hard Example Mining (OHEM) prioritizes difficult pneumonia cases
   - Improves robustness without architectural modifications

## 📊 Results & Performance

### Segmentation Performance Comparison

| Method | Model Size (MB) | Cell Nuclei | Fetal Head | Nerve |
|--------|-----------------|---|---|---|
| | | IoU / Dice | IoU / Dice | IoU / Dice |
| U-Net | 32.95 | 86.09 / 91.39 | 95.31 / 97.29 | 68.35 / 79.34 |
| U-Net + SS | 34.22 | 86.14 / 91.63 | 95.37 / 97.33 | 68.90 / 79.73 |
| Wide U-Net | 34.85 | 86.10 / 91.51 | 95.13 / 97.21 | 68.94 / 79.75 |
| U-Net++ | 34.96 | 85.83 / 91.58 | 95.41 / 97.30 | 67.87 / 79.85 |
| Att U-Net | 33.63 | 85.83 / 91.49 | 95.36 / 97.35 | 68.53 / 79.31 |
| **U-Net(R) + SS (Ours)** | **32.89** | **86.58 / 91.84** | **95.48 / 97.41** | **69.14 / 80.14** |

**Key Finding:** Achieved highest performance with the **smallest model size** — demonstrating efficiency without sacrificing accuracy.

### Robustness Under Class Imbalance

The two-stage framework demonstrates superior robustness across varying imbalance ratios and minority class configurations:

- Baseline model shows rapid performance degradation with increasing imbalance
- Undersampling causes significant information loss
- Two-stage training with oversampling maintains stable ROC-AUC scores
- Outperforms conventional approaches by 5-15% in extreme imbalance scenarios

## 🏗️ Framework Architecture

### Stage 1: Self-Supervised Label Refinement
Unlabeled CXR Images
↓
[SimCLR / BYOL]
↓
Feature Representations
↓
Pseudo-Label Generation (Confidence Filtering)
↓
Refined, Noise-Reduced Dataset

### Stage 2: Data-Centric Training
Refined Dataset
↓
[AI-Driven Augmentation: GAN, Diffusion, CutMix]
↓
[Online Hard Example Mining (OHEM)]
↓
Robust Segmentation Model (U-Net)
↓
Clinical-Ready Predictions

## 🚀 Installation

### Prerequisites
- Python 3.8+
- PyTorch 1.9+
- CUDA 11.0+ (optional, for GPU acceleration)

### Setup

```bash
git clone https://github.com/AbdulBari33/data-centric-pneumonia-segmentation.git
cd data-centric-pneumonia-segmentation

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

pip install -r requirements.txt
```

## 📚 Dataset

This work uses the **Chest X-Ray Images (Pneumonia)** dataset from Kaggle:

- **Source:** [Paul Mooney's Chest X-Ray Dataset](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia)
- **Images:** 5,856 labeled CXR images
- **Classes:** Normal vs. Pneumonia
- **Preprocessing:** Normalization and contrast enhancement

## 💻 Usage

### Running the Notebook

```bash
cd notebooks
jupyter notebook pneumonia_segmentation.ipynb
```

The notebook includes:
- Data loading and preprocessing
- Self-supervised learning pipeline
- Segmentation model training
- Evaluation and visualization

## 📈 Visualizations

### Robustness Analysis
The framework demonstrates consistent performance across:
- 2, 5, and 8 minority class scenarios
- Imbalance ratios from 10:1 to 5000:1
- Multiple sampling strategies

### Segmentation Results
High-quality segmentation of pneumonia regions in chest X-rays with:
- Clear boundary detection
- Robust handling of low-contrast areas
- Reliable minority class recognition

## 🔬 Methodology

### Key Techniques

**Self-Supervised Learning:**
- SimCLR: Contrastive learning without labels
- BYOL: Bootstrap Your Own Latent

**Data Augmentation:**
- GAN-based synthesis
- Diffusion-based augmentation
- CutMix spatial augmentation

**Hard Example Mining:**
- Online Hard Example Mining (OHEM)
- Prioritizes difficult pneumonia cases
- Improves sensitivity to ambiguous regions

## 📖 Citation

If you use this work in your research, please cite:

```bibtex
@inproceedings{bari2026pneumonia,
  title={Improving Pneumonia Segmentation via a Two-Stage Data-Centric Learning Framework},
  author={Bari, Abdul and Fatima and Abro, Ghulam E Mustafa},
  booktitle={Proceedings of the 16th IEEE Symposium on Computer Applications & Industrial Electronics (ISCAIE 2026)},
  address={Penang, Malaysia},
  month={April},
  year={2026},
  organization={IEEE}
}
```

## 👥 Authors

- **Abdul Bari** - Lead Researcher, Deloitte Audit and Assurance, UK
  - Email: abdulbarishaikhh@outlook.com
  
- **Fatima Memon** - Co-author, School of Technology, Cardiff Metropolitan University
  - Email: fatimamemon51@outlook.com
  
- **Prof. Ghulam E Mustafa Abro** - Advisor, Research Unit for Robophilosophy & Integrative Social Robotics (RISR), Aarhus University
  - Email: mustafa.abro@ieee.org

## 📄 License

This project is licensed under the MIT License.

## 🔮 Future Work

- Evaluation on real-time and edge-deployment scenarios
- Multi-disease and multi-organ segmentation extensions
- Transformer-based self-supervised models for improved efficiency
- Explainable AI (XAI) integration for clinical interpretability
- Point-of-care clinical applications

## 📞 Contact & Support

For questions, collaborations, or feedback:
- Open an **Issue** on GitHub
- Email: abdulbarishaikhh@outlook.com