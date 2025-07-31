  <a href="https://ai4life.eurobioimaging.eu/open-calls/">
    <img src="https://github.com/ai4life-opencalls/.github/blob/main/AI4Life_banner_giraffe_nodes_OC.png?raw=true" width="70%">
  </a>
</p>

# Project #19: Segmentation of sparse bacteria in human tissue


## Project Overview

This repository contains the code and notebooks for preparing ground truth data for training, training a 3D Stardist model, and then use it on unseen data for **Sparse bacteria segmentation in tissue samples**. 
The project implements deep learning approaches for automated detection and segmentation of bacterial cells in complex tissue environments using 3D microscopy data. 
Developed as part of the [AI4Life project](https://ai4life.eurobioimaging.eu), it uses data provided by Sebastien Herbert from University of Basel in Switzerland.
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
│   ├── 0.1_summary_fov_per_sample_id.ipynb                       # Dataset preparation and splitting
│   ├── 0.2_label_watershed.ipynb                                 # Watershed-based labeling
│   ├── 0.3_normalize_and_crop.ipynb                              # Data preprocessing
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

The workflow was designed to use the available notebooks in the following order:

### 1. Data Preparation (`0.1_summary_fov_per_sample_id.ipynb`)
- Cross-reference of images with sample ID metadata
- Generates a summary of available data per sample ID, including any empty FOVs (Fields of View)
- Allows for informed dataset splitting into training and testing sets by the user

### 2. Label Refinement (`0.2_label_watershed.ipynb`)
- Handling of touching/overlapping bacteria labeled as a single instance
- Application of watershed algorithm for improved instance labeling

### 3. Data Preprocessing (`0.3_normalize_and_crop.ipynb`)
- Image normalization and cropping, needed **only for the training data** due to its large size
- Cropping considers regions with bacteria to balance the ratio of empty background regions and optimize training efficiency
- This step is required to avoid the time consuming processing in the dataloaders during training, this step in not needed for the testing data nor inference as it is integrated in the prediction functions

### 4. Model Training (`StarDist_3D_DL4MicEverywhere_Modified_AI4LifeOC.ipynb`)
- DL4MicEverywhere StarDist 3D model training, validation, and inference
- Custom modifications for large image handling


## 📈 Results

The model provides:
- Segmentation masks for individual bacteria
- Quality metrics and validation reports
- Interactive visualization of results


## 📚 References

- Schmidt, Uwe, et al. "Cell detection with star-convex polygons." International conference on medical image computing and computer-assisted intervention. Cham: Springer International Publishing, 2018.
- Weigert, Martin, et al. "Star-convex polyhedra for 3D object detection and segmentation in microscopy." Proceedings of the IEEE/CVF winter conference on applications of computer vision. 2020.
- Von Chamier, Lucas, et al. "Democratising deep learning for microscopy with ZeroCostDL4Mic." Nature communications 12.1 (2021): 2276.
- Hidalgo-Cenalmor, Iván, et al. "DL4MicEverywhere: deep learning for microscopy made flexible, shareable and reproducible." Nature methods 21.6 (2024): 925-927.

## Acknowledgements
AI4Life has received funding from the European Union’s Horizon Europe research and innovation programme under grant agreement number 101057970. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them.
