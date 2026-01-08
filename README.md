
# Recycling Image Classifier (CNN)

This project implements a Convolutional Neural Network (CNN) for classifying images of waste into recycling categories using transfer learning with **ResNet50**. The goal is to accurately identify common waste types to support recycling and waste-sorting applications.

## Dataset

The project uses the **Garbage Dataset Classification** dataset from Kaggle:

https://www.kaggle.com/datasets/zlatan599/garbage-dataset-classification

### Classes
The dataset contains six classes:
- cardboard
- glass
- metal
- paper
- plastic
- trash

The dataset directory is expected to follow the original Kaggle structure:
```
Garbage_Dataset_Classification/
├── images/
│   ├── cardboard/
│   ├── glass/
│   ├── metal/
│   ├── paper/
│   ├── plastic/
│   └── trash/
└── metadata.csv
```

## Project Overview

- Transfer learning using **ResNet50 pretrained on ImageNet**
- Two-phase training strategy:
  - **Phase 1:** Train a custom classification head with the backbone frozen
  - **Phase 2:** Fine-tune the last layers of ResNet50
- Data augmentation for robustness
- Evaluation using accuracy, Top-2 accuracy, confusion matrix, and classification report
- Models saved in modern `.keras` format

## Environment Setup

### Python Version
- Python **3.10** is recommended

### Install Dependencies
Create a virtual environment and install requirements:
```bash
pip install -r requirements.txt
```

### Dataset Path
Set the dataset directory as an environment variable:
```bash
export DATASET_DIR=/path/to/Garbage_Dataset_Classification
```
On Windows (PowerShell):
```powershell
setx DATASET_DIR "C:\path\to\Garbage_Dataset_Classification"
```

## Training Procedure

1. Load and preprocess images
2. Stratified train/validation/test split
3. Apply data augmentation
4. Train Phase 1 (frozen backbone)
5. Train Phase 2 (fine-tuning last ResNet layers)
6. Evaluate on test set
7. Save trained models

## Results

Final test performance:
- **Accuracy:** ~93%
- **Top-2 Accuracy:** ~98%

The confusion matrix and classification report show strong performance across all classes, with minimal confusion between visually similar materials.

## Saved Models

Models are saved in the `models/` directory:
- `base_modelv1.keras` – after Phase 1 training
- `final_modelv1.keras` – after fine-tuning

## License

This project is for educational and research purposes. Dataset rights belong to the original Kaggle contributor.
