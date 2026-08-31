# CViTLw: A Lightweight Convolutional Neural Network and Vision Transformer Hybrid Architecture for Plant Disease Classification

Official artifact and code repository for the paper **"CViTLw: A Lightweight Convolutional Neural Network and Vision Transformer Hybrid Architecture for Plant Disease Classification"**.

---

## 📌 Repository Structure

```text
CViTLw/
├── CViTLw_Model.ipynb               # Jupyter notebook with complete model definition & parameter analysis
├── paper/
│   └── CViTLw_Wiley.pdf             # Camera-ready manuscript PDF (Wiley USG format)
│
├── checkpoints/                     # Best-fold model weights (.pth) for all 6 evaluation datasets
│   ├── 1_PlantVillage_Full/         # 38 classes, 54k images (Acc: 99.76%) -> CViTLw_fold5_best.pth
│   ├── 2_PVCorn_Subset/             # 4 classes, 3.8k images (Acc: 99.22%) -> CViTLw_fold3_best.pth
│   ├── 3_PlantPathology2020_Ablation/# 4 classes, 6.1k images (Acc: 97.74%) -> Hybrid_none-none-secbam_fold2_best.pth
│   ├── 4_Maize_Mduma2023/           # 3 classes, 18.4k images (Acc: 99.70%) -> CViTLw_fold4_best.pth
│   ├── 5_IIITDMJ_Maize/             # 4 classes, field & drone (Acc: 100.00%) -> CViTLw_fold3_best.pth
│   └── 6_PlantRAW/                  # 35 classes, 16.1k images (Acc: 90.94%) -> CViTLw_best.pth
│
└── logs_and_results/                # Raw training logs & JSON metrics matching paper results
    ├── 1_PlantVillage_Full/         # training.log, comparison_results.json, training_progress.json
    ├── 2_PVCorn_Subset/             # training.log, comparison_results.json, training_progress.json
    ├── 3_PlantPathology2020_Ablation/# ablation_training.log, ablation_kfold_results.json, progress.json
    ├── 4_Maize_Mduma2023/           # training.log, comparison_results.json, training_progress.json
    ├── 5_IIITDMJ_Maize/             # training.log, comparison_results.json, training_progress.json
    └── 6_PlantRAW/                  # training.log, comparison_results.json, training_progress.json
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

## 📊 Overview of the Six Evaluation Datasets & Results

| # | Dataset | Samples | Classes | Setup / Environment | Evaluation Protocol | CViTLw Top Acc | Best Checkpoint |
|:---:|:---|:---:|:---:|:---|:---|:---:|:---|
| **1** | **PlantVillage Full** | 54,305 | 38 | Controlled Laboratory | 5-Fold Stratified CV | **99.76%** | `CViTLw_fold5_best.pth` |
| **2** | **PV-Corn Subset** | 3,852 | 4 | Controlled Laboratory | 5-Fold Stratified CV | **99.22%** | `CViTLw_fold3_best.pth` |
| **3** | **PlantPathology 2020** | 6,192 | 4 | Real-world Field (DSLR) | 5-Fold Ablation CV | **97.74%** | `Hybrid_none-none-secbam_fold2_best.pth` |
| **4** | **Maize Leaf Disease** | 18,402 | 3 | Real-world Field (Smartphone) | 5-Fold Stratified CV | **99.70%** | `CViTLw_fold4_best.pth` |
| **5** | **IIITDMJ Maize** | 816 / 200 | 4 | Field & Aerial Drone | 5-Fold CV + Drone OOD | **100.00%** | `CViTLw_fold3_best.pth` |
| **6** | **PlantRAW (Ours)** | 16,165 | 35 | Multi-source In-the-wild | Standard Split | **90.94%** | `CViTLw_best.pth` |

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

## 📄 Citation

If you find this code or research useful, please cite our paper:

```bibtex
@article{tongle2026cvitlw,
  title={CViTLw: A Lightweight Convolutional Neural Network and Vision Transformer Hybrid Architecture for Plant Disease Classification},
  author={Tong-Le, Thanh-Hai and Le, Minh-Hai and Doan, Thanh-Nghi},
  journal={Journal of Electrical and Computer Engineering},
  year={2026}
}
```
