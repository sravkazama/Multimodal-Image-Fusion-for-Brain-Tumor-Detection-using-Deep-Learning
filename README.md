# Multimodal Medical Image Fusion for Brain Tumor Detection

This project uses **deep learning** and **image processing** to help detect brain tumors more effectively by combining CT and MRI scans. The idea is to create a single, clearer image that gives doctors better information than either scan alone.

---

## Why Multimodal Imaging?

Medical images like **CT** (shows structure) and **MRI** (shows soft tissue) give different types of information. Combining them — known as **image fusion** — helps doctors get a more complete view of the brain. This can help detect tumors earlier and more accurately.

---

## Project Workflow

We follow a 3-step process:

1. **Image Registration** – Align MRI and CT images into one coordinate system.
2. **Image Fusion** – Merge both images using deep learning and wavelet transform.
3. **Image Segmentation** – Highlight the tumor area using the watershed algorithm.

---

## 1. Image Registration

Align MRI to CT using landmark-based registration. You choose matching points in both images, and the system adjusts the MRI to match the CT.

### How to Run:
- **Notebook:** `python scripts/Image Registration Process.ipynb`
- **Flask GUI:** Run `python app.py` and upload your CT and MRI images. The result is saved as `static/mri_registered.jpg`.

---

## 2. Image Fusion

We use **VGG-19**, a pre-trained neural network, to guide fusion. Before that, both images are converted to **YCbCr** color space and **wavelet transform** is applied.

### Steps:
- Decompose both images using DWT (Discrete Wavelet Transform).
- Use VGG-19 to fuse components.
- Apply inverse wavelet transform to generate the fused image.

### How to Run:
- **Notebook:** `python scripts/Transfer_Learning.ipynb`
- **Flask GUI:** Run `python app.py`. Fused image will be saved as `static/fusion.jpg`.

---

## 3. Image Segmentation

We apply the **Watershed Algorithm** to detect and separate the tumor region from the fused image. It uses seed points (manual or automatic) to grow segmented regions.

### How to Run:
- **Notebook:** `python scripts/Image Segmentation.ipynb`
- **Flask GUI:** Run `python app.py`. Segmented image will be saved as `static/segmented.jpg`.

---

## Desktop App

Prefer a desktop interface? This project is also available as a standalone [Tkinter-based Desktop Application](https://github.com/beccaboo-31/Multimodal-Image-Fusion-Desktop-App/).

---

## Requirements

- Python 3.8+
- Libraries: `opencv-python`, `numpy`, `matplotlib`, `tensorflow`, `flask`, `tkinter`, etc.
- Install all dependencies:
  ```bash
  pip install -r requirements.txt
