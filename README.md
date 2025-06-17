# Multimodal-Image-Fusion-for-Brain-Tumor-Detection-using-Deep-Learning
# Multimodal Image Fusion for Brain Tumor Detection Using Deep Learning

## Overview

This project implements an automated medical image analysis pipeline that utilizes multimodal image fusion to enhance brain tumor detection. By combining **Computed Tomography (CT)** and **Magnetic Resonance Imaging (MRI)** scans, the system leverages the complementary strengths of structural and functional imaging for improved diagnostic accuracy.

The methodology integrates **image registration**, **deep learning-based fusion using transfer learning**, and **segmentation techniques** to detect brain tumors with greater clarity and precision.

---

## Objectives

- To align (register) multimodal medical images into a common spatial framework.
- To perform image fusion that combines CT and MRI scans for enriched visual information.
- To apply deep learning (VGG-19) and wavelet transforms to generate a fused image.
- To segment tumor regions using morphological algorithms for improved visualization and analysis.
- To provide accessible interfaces via a Flask-based web GUI and a desktop application.

---

## Technologies and Frameworks

- **Programming Language:** Python  
- **Deep Learning:** TensorFlow / Keras (VGG-19 Transfer Learning)  
- **Image Processing:** OpenCV, Discrete Wavelet Transform (DWT), Watershed Algorithm  
- **Visualization:** Matplotlib  
- **User Interfaces:** Flask (Web), Tkinter (Desktop)  
- **Development Environment:** Jupyter Notebooks, Python Scripts  

---

## Functional Workflow

### 1. Image Registration

Aligns MRI and CT images by transforming them into a common coordinate space. A landmark-based registration method is employed, where reference points are selected manually to align the two modalities.

- **Output:** `mri_registered.jpg`

> *Execute:*  
> - Notebook: `Image Registration Process.ipynb`  
> - Flask: `python app.py`

---

### 2. Image Fusion

Utilizes **VGG-19**, a pre-trained convolutional neural network, to guide the fusion process. Both images are converted to the YCbCr color space, and **Discrete Wavelet Transform (DWT)** is applied. Fusion is performed on each set of wavelet coefficients, followed by inverse DWT to generate the final fused image.

- **Output:** `fusion.jpg`

> *Execute:*  
> - Notebook: `Transfer_Learning.ipynb`  
> - Flask: `python app.py`

---

### 3. Tumor Segmentation

Applies the **Watershed Segmentation Algorithm** to detect and isolate tumor regions within the fused image. This method uses morphological operations and marker-based object detection for accurate segmentation.

- **Output:** `segmented.jpg`

> *Execute:*  
> - Notebook: `Image Segmentation.ipynb`  
> - Flask: `python app.py`

---

### 4. Desktop Application

A standalone desktop interface built using **Tkinter** integrates the full pipeline, allowing users to register, fuse, and segment medical images without a browser.

> *Execute:*  
> ```bash
> python desktop_app.py
> ```

---

## Dataset

This project can be tested using publicly available medical imaging datasets:

- **BraTS (Brain Tumor Segmentation Challenge)**  
  [https://www.med.upenn.edu/cbica/brats2020/](https://www.med.upenn.edu/cbica/brats2020/)

Alternatively, CT and MRI brain images from open-source medical databases can be used.

---

## Project Structure

├── app.py # Web GUI using Flask
├── desktop_app.py # Desktop GUI using Tkinter
├── python scripts/
│ ├── Image Registration Process.ipynb
│ ├── Transfer_Learning.ipynb
│ └── Image Segmentation.ipynb
├── static/
│ ├── mri_registered.jpg
│ ├── fusion.jpg
│ └── segmented.jpg
├── data/
│ ├── CT/
│ └── MRI/
└── README.md

---

## Results

- Enhanced detection of tumor boundaries and regions through multimodal fusion.
- Improved clarity and contrast over single-modality imaging.
- Accurate segmentation using classical morphological algorithms.

Quantitative evaluation and performance metrics (e.g., PSNR, SSIM, Dice Coefficient) can be added based on the specific dataset used.

---

## Installation and Usage

### Prerequisites

- Python ≥ 3.8  
- Required libraries: `numpy`, `opencv-python`, `matplotlib`, `tensorflow`, `flask`, `tkinter`, etc.

### Setup Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/multimodal-image-fusion-brain-tumor.git
   cd multimodal-image-fusion-brain-tumor

2. Install dependencies:
    pip install -r requirements.txt
3. Launch the Flask GUI:
     python app.py
4.Or, launch the Desktop App:
  python desktop_app.py
