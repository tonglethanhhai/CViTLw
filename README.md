# CViTLw: A Lightweight Convolutional Neural Network and Vision Transformer Hybrid Architecture for Plant Disease Classification

Official artifact and code repository for the paper **"CViTLw: A Lightweight Convolutional Neural Network and Vision Transformer Hybrid Architecture for Plant Disease Classification"**.

---

## 📌 Repository Structure

```text
CViTLw/
├── CViTLw_Model.ipynb          # Jupyter notebook with complete model definition & parameter analysis
├── paper/
│   └── CViTLw_Wiley.pdf        # Manuscript PDF (Wiley format)
├── checkpoints/                # Best-fold model weights (.pth) for each dataset
│   ├── PlantVillage_Full/      # 38 classes (Acc: 99.76%)
│   │   └── CViTLw_fold5_best.pth
│   ├── IIITDMJ_Maize/          # 4 classes (Acc: 100.00%)
│   │   └── CViTLw_fold3_best.pth
│   └── PlantRAW/               # Complex field dataset (Acc: 90.94%)
│       └── CViTLw_best.pth
└── logs_and_results/           # Raw training logs & JSON metrics matching paper results
    ├── PlantVillage_Full/      # training.log, comparison_results.json, training_progress.json
    ├── IIITDMJ_Maize/          # training.log, comparison_results.json, training_progress.json
    ├── PlantRAW/               # training.log, comparison_results.json, training_progress.json
    └── Ablation_PlantPathology2020/ # 5-fold cross-validation ablation logs & results
```

---

## 🔬 Model Overview

- **Model Name**: CViTLw (Convolutional Vision Transformer Lightweight)
- **CNN Branch**: MobileNetV2 `features[:8]` (random init) $\rightarrow$ 32 channels
- **ViT Branch**: Lightweight Transformer Encoder (4 layers, 4 heads, $D=48$, random init)
- **Fusion Block**: Inverted Residual (expand=6, stride=2) + Sequential Attention (SE $\rightarrow$ CBAM)
- **Total Parameters**: **334,008 (0.334 M)**
- **Computational Cost**: **143.54 MFLOPs**
- **Inference Latency**: **~5.0 ms / image** (NVIDIA RTX 5070 Ti)

---

## 🚀 Quick Start & Model Inspection

To inspect the model architecture, layer parameters, tensor shapes, FLOPs, and latency:

1. Clone this repository:
   ```bash
   git clone <REPO_URL>
   cd CViTLw
   ```

2. Open and run the Jupyter notebook:
   ```bash
   jupyter notebook CViTLw_Model.ipynb
   ```

### Requirements
- Python >= 3.9
- PyTorch >= 2.0
- torchvision
- numpy

---

## 📊 Summary of Experimental Results

| Dataset | Classes | Split / Validation | CViTLw Accuracy | Params (M) |
|:---|:---:|:---:|:---:|:---:|
| **PlantVillage (Full)** | 38 | 5-Fold CV | **99.76%** | 0.334 |
| **IIITDMJ Maize** | 4 | 5-Fold CV | **99.39% ± 1.8% (Peak: 100%)** | 0.334 |
| **PlantRAW (Field)** | 10 | Standard Split | **90.94%** | 0.334 |

---

## 📄 Citation

If you find this code or research useful, please cite our paper:

```bibtex
@article{tongle2026cvitlw,
  title={CViTLw: A Lightweight Convolutional Neural Network and Vision Transformer Hybrid Architecture for Plant Disease Classification},
  author={Tong-Le, Thanh-Hai and Le, Minh-Hai and Doan, Thanh-Nghi},
  journal={Wiley},
  year={2026}
}
```
