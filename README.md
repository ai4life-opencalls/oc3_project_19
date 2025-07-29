# Project #19: Segmentation of sparse bacteria in human tissue



## Project Overview

This repository contains the code and notebooks for preparing ground truth data for training, training a 3D Stardist model, and then use it on unseen data for **Sparse bacteria segmentation in tissue samples**. 
The project implements deep learning approaches for automated detection and segmentation of bacterial cells in complex tissue environments using 3D microscopy data. 
Developed as part of the [AI4Life project](https://ai4life.eurobioimaging.eu), it uses data provided by ***.
All images used in this tutorial are licensed under **CC-BY**. If any of the instructions are not working, please [open an issue]


## 🎯 Objective

The main goal is to develop robust AI models for:
- Automated segmentation of *Staphylococcus aureus* bacteria in tissue samples
- 3D cell detection and counting in microscopy images
- Quality control and validation of segmentation results

## 📁 Repository Structure

```
AI4LIfe_OC_StaphInTissue/
├── notebooks/
│   ├── 0_dataset_split_train_test.ipynb                          # Dataset preparation and splitting
│   ├── 0.1_Label_watershed.ipynb                                 # Watershed-based labeling
│   ├── 0.2_train_dataset_normalize_crop.ipynb                    # Data preprocessing
│   ├── StarDist_3D_DL4MicEverywhere_Modified_AI4LifeOC.ipynb     # Main StarDist 3D notebook for training and inference
│   └── data_identifier.csv                                       # Dataset metadata
├── env_requirements.txt                                          # Python dependencies
├── LICENSE                                                       # MIT License
└── README.md                                                     # This file
```

## 🚀 Getting Started

### Prerequisites

- CUDA-compatible GPU (recommended for training)
- Sufficient RAM for 3D image processing
- [DL4MicEverywhere](https://github.com/HenriquesLab/DL4MicEverywhere)

### Installation

1. Follow the [DL4MicEverywhere](https://github.com/HenriquesLab/DL4MicEverywhere) installation instructions and load the Stardist 3D ZeroCostDL4Mic environment.

2. In the Jupyter notebook interface, clone this repository:
```bash
git clone https://github.com/ai4life-opencalls/****.git
```

## 📊 Workflow

The project follows a structured workflow for bacterial segmentation:

### 1. Data Preparation (`0_dataset_split_train_test.ipynb`)
- Cross-reference of images with metadata
- Generate summary of available data
- Allows for informed dataset splitting into training and testing sets by the user

### 2. Label Refinement (`0.1_Label_watershed.ipynb`)
- Handling of touching/overlapping bacteria labeled together
- Application of watershed algorithm for improved instance labeling

### 3. Data Preprocessing (`0.2_train_dataset_normalize_crop.ipynb`)
- Image normalization and cropping
- Preparation of training dataset for StarDist 3D model
- Reduction of empty background regions to optimize training efficiency

### 4. Model Training (`StarDist_3D_DL4MicEverywhere_Modified_AI4LifeOC.ipynb`)
- StarDist 3D model implementation
- Custom modifications for large image handling
- Training and validation procedures
- Model evaluation and quality control

## 🔬 Methodology

The project utilizes **StarDist 3D**, a state-of-the-art deep learning approach for:
- Star-convex object detection in 3D microscopy images
- Accurate segmentation of spherical bacterial cells
- Instance segmentation for overlapping objects

### Key Features:
- **3D segmentation**: Full volumetric processing of microscopy stacks
- **Quality control**: Comprehensive validation metrics (IoU, precision, recall)
- **Visualization**: Interactive tools for result inspection
- **Scalability**: Tiled processing for large images

## 📈 Results

The model provides:
- Segmentation masks for individual bacteria
- Quality metrics and validation reports
- Interactive visualization of results

## 🛠️ Usage

### Training a New Model

1. If multiple image sets have the same source prepare a metadata file like `data_identifier.csv`
2. Run the data preparation notebooks in sequence:
   ```
   notebooks/0_dataset_split_train_test.ipynb
   notebooks/0.1_Label_watershed.ipynb
   notebooks/0.2_train_dataset_normalize_crop.ipynb
   ```
3. Train the StarDist model:
   ```
   notebooks/StarDist_3D_DL4MicEverywhere_Modified_AI4LifeOC.ipynb
   ```

### Inference on New Data

Use the trained model section in the main notebook to process new images.

## 📚 References

- Schmidt, U., et al. "Cell detection with star-convex polygons." MICCAI 2018.
- Weigert, M., et al. "Star-convex polyhedra for 3d object detection and segmentation in microscopy." WACV 2020.
- von Chamier, L., et al. "Democratising deep learning for microscopy with ZeroCostDL4Mic." Nature Communications 2021.

## Acknowledgements
AI4Life has received funding from the European Union’s Horizon Europe research and innovation programme under grant agreement number 101057970. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them.
