# IndoTraffic Dataset

**A Large-Scale Multi-City Dataset for Indonesian Mixed Traffic Detection**

> **The Majority Class Paradox in Urban Traffic Detection: Lessons from the IndoTraffic Dataset**
> Putu Eka Suartawan¹, Dewa Made Priyantha Wedagama², Putu Alit Suthanaya³, I Made Suraharta¹, Putu Diva Ariesthana Sadri¹, Aswin Badarudin A.¹
> ¹Bali Land Transportation Polytechnic, ²³Udayana University

---

## 📋 Overview

IndoTraffic is a publicly accessible dataset designed for vehicle detection in Indonesian urban mixed traffic environments. The dataset addresses critical gaps in existing traffic datasets by providing:

- **9,078 high-resolution images** with comprehensive annotations
- **Multi-city coverage**: Denpasar, Yogyakarta, and Jabodetabek
- **Temporal diversity**: 24-hour coverage including peak hours, midday, evening, and night
- **Environmental variability**: Clear, overcast, and rainy weather conditions
- **6 vehicle classes** reflecting real Indonesian traffic distribution

### Key Features

✅ **Real-world class distribution** (motorcycle-dominant traffic)
✅ **High-quality annotations** in YOLO format
✅ **Multiple cities** coverage for diverse traffic patterns
✅ **Open license** (CC BY 4.0) for research and commercial applications

---

## 🚗 Dataset Classes

| Class | Description | Indonesian Name |
|-------|-------------|-----------------|
| Bus | Public transportation buses | Bus |
| Mobil Penumpang | Passenger cars | Mobil Penumpang |
| Pejalan Kaki | Pedestrians | Pejalan Kaki |
| Sepeda Motor | Motorcycles (majority class) | Sepeda Motor |
| Truck | Cargo trucks | Truck |
| Unmotorized | Non-motorized vehicles | Kendaraan Tidak Bermotor |

---

## 📥 Dataset Download and Structure

### Option 1: GitHub Repository (Documentation & Config)
This repository contains the documentation and configuration files. The full dataset with images and labels is available separately.

### Option 2: Complete Dataset (Available)
📁 **Download the complete dataset here**:
[🔗 IndoTraffic Dataset - Google Drive](https://drive.google.com/drive/folders/1arD3geb3A8kQcyp5WXzTWn21AdumD5It?usp=sharing)

The Google Drive folder contains:
- All training, validation, and test images
- YOLO format annotation files (.txt)
- Pre-trained model weights (optional)

> **Note**: The dataset is shared for academic and research purposes under CC BY 4.0 license.

### Repository Structure

```
indotraffic-dataset/
├── train/
│   ├── images/          # Training images (download from Google Drive)
│   └── labels/          # YOLO format annotations (.txt) (download from Google Drive)
├── val/
│   ├── images/          # Validation images (download from Google Drive)
│   └── labels/          # YOLO format annotations (.txt) (download from Google Drive)
├── test/
│   ├── images/          # Test images (download from Google Drive)
│   └── labels/          # YOLO format annotations (.txt) (download from Google Drive)
├── data.yaml            # Dataset configuration
├── requirements.txt     # Dependencies
├── CITATION.cff        # Citation information
├── LICENSE             # CC BY 4.0 License
└── README.md            # This file
```

### Dataset Size Information
- **Training Images**: ~6,355 images
- **Validation Images**: ~1,816 images
- **Test Images**: ~907 images
- **Total Estimated Size**: ~2-3 GB (including images)

---

## 🛠️ Installation

### Requirements

- Python 3.8+
- CUDA 11.0+ (for GPU training)

### Setup

```bash
# Step 1: Clone this repository
git clone https://github.com/ekasuartawan82/indotraffic-dataset.git
cd indotraffic-dataset

# Step 2: Download the complete dataset from Google Drive
# Link: https://drive.google.com/drive/folders/1arD3geb3A8kQcyp5WXzTWn21AdumD5It?usp=sharing
# Extract and place the folders in this directory:
# indotraffic-dataset/
# ├── train/
# │   ├── images/
# │   └── labels/
# ├── val/
# │   ├── images/
# │   └── labels/
# └── test/
#     ├── images/
#     └── labels/

# Step 3: Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Step 4: Install dependencies
pip install -r requirements.txt
```

---

## 🚀 Quick Start

### 1. Dataset Configuration

The dataset configuration is in `data.yaml`:

```yaml
train: train/images
val: val/images
test: test/images

nc: 6
names: ['Bus', 'Mobil Penumpang', 'Pejalan Kaki', 'Sepeda Motor', 'Truck', 'Unmotorized']
```

### 2. Training with YOLOv8

```bash
from ultralytics import YOLO

# Load a model
model = YOLO('yolov8n.pt')  # load a pretrained model

# Train the model
results = model.train(data='data.yaml', epochs=100, imgsz=640)
```

### 3. Inference

```bash
from ultralytics import YOLO

# Load the trained model
model = YOLO('best.pt')

# Run inference
results = model('path/to/image.jpg')
```

---

## 📊 Dataset Statistics

- **Total Images**: 9,078
- **Training Set**: ~6,355 images (70%)
- **Validation Set**: ~1,816 images (20%)
- **Test Set**: ~907 images (10%)
- **Classes**: 6 vehicle types
- **Annotation Format**: YOLO

---

## 📝 Citation

If you use this dataset in your research, please cite:

```bibtex
@article{suartawan2024indotraffic,
  title={The Majority Class Paradox in Urban Traffic Detection: Lessons from the IndoTraffic Dataset},
  author={Suartawan, Putu Eka and Wedagama, Dewa Made Priyantha and Suthanaya, Putu Alit and Suraharta, I Made and Sadri, Putu Diva Ariesthana and Badarudin, Aswin},
  journal={International Journal of Artificial Intelligence},
  year={2024},
  publisher={IAES}
}
```

---

## 📄 License

This dataset is released under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to:
- **Share** — copy and redistribute the material
- **Adapt** — remix, transform, and build upon the material for any purpose, even commercially

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made

---

## 📧 Contact

**Corresponding Author:** Putu Eka Suartawan
**Email:** putu.eka@poltradabali.ac.id
**Institution:** Bali Land Transportation Polytechnic

---

## 🙏 Acknowledgments

- Area Traffic Control System (ATCS) operators in Denpasar, Yogyakarta, and Jabodetabek
- Indonesian transportation authorities for data access
- Research team at Bali Land Transportation Polytechnic and Udayana University

---

**Last Updated:** November 2024
**Version:** 1.0
**Repository:** https://github.com/ekasuartawan82/indotraffic-dataset