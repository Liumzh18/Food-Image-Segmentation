# YOLOv8 Food Image Instance Segmentation
A lightweight food image segmentation solution based on YOLOv8n-seg, supporting automated dataset processing, model training, evaluation, inference and one-click deployment.

## Project Overview
This project focuses on **pixel-level instance segmentation** for food images as a typical computer vision task. It provides a full pipeline including automatic environment setup, dataset loading & validation, mask format conversion, model training, performance evaluation, result visualization and model packaging. The solution balances accuracy and inference speed, which can be directly applied to smart catering, dietary analysis and other visual scenarios.

## Core Features
1. Automatically detect and install project dependencies, supporting auto-switch between GPU and CPU
2. One-click loading and validation of the UECFOODPIXCOMPLETE dataset with sample preview
3. Auto-convert dataset masks to the standard YOLOv8 segmentation format
4. Train lightweight YOLOv8n-seg model with transfer learning
5. Automatic model evaluation with metric calculation and training curve visualization
6. One-click model packaging for fast deployment without extra environment configuration

## Environment Setup
The project supports automatic dependency installation. Just run the main code, and it will install all required packages:
- Required libraries: datasets, transformers, torch, pillow, ultralytics, opencv-python, pyyaml
- Hardware support: NVIDIA GPU (CUDA) / CPU compatible

## Usage Steps
### 1. Environment & Dataset Initialization
Run the environment setup script to install dependencies, check hardware, and download/validate the dataset.
Sample preview images will be saved automatically.

### 2. Dataset Format Conversion
Convert raw dataset masks to standard YOLOv8 format.
The system automatically creates directories, extracts contours, normalizes coordinates, and generates `dataset.yaml`.

### 3. Model Training
Load pre-trained YOLOv8n-seg weights and start training automatically.
The best model weights `best.pt` will be saved after training.

### 4. Model Evaluation
Test model performance on the validation set with standard computer vision metrics.
Training loss curves, mAP curves and prediction visualization results are generated automatically.

### 5. Inference & Deployment
Load the trained model for real-time food image segmentation.
Use one-click packaging to export a complete deployable model package.

## Project Structure
```
Project Root/
├── data/                     # Dataset and sample preview images
├── UECFoodPix_YOLOv8/        # YOLOv8 formatted dataset
│   ├── images/               # Training/validation images
│   ├── labels/               # Segmentation labels
│   └── dataset.yaml          # Dataset configuration
├── runs/                     # Training logs, evaluation results and visualization plots
├── model_packages/           # Packaged model files
│   ├── models/               # Model weights
│   ├── configs/              # Configuration files
│   ├── training_results/     # Training outputs and metrics
│   └── README.md             # Model usage documentation
└── Core Scripts              # Environment setup, data processing, training, evaluation, packaging
```

## Key Parameters
- Model: YOLOv8n-seg (lightweight instance segmentation)
- Input size: 640×640
- Training epochs: 100
- Batch size: 16
- Key metrics: mask mAP@50=0.9492, mAP@50-95=0.8409
- Inference speed: 6–7 ms per image

## Notes
1. A stable network connection is required for first-run dataset downloading
2. Small invalid regions are filtered during format conversion to improve training quality
3. Local image input is supported for inference, with segmentation masks and bounding boxes as output
4. The packaged model can be deployed directly without reconfiguring the environment