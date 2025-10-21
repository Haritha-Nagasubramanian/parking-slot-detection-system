# Parking Slot Detection System

## 1. Abstract
Parking in crowded cities has become increasingly frustrating due to the unavailability of real-time parking slot information. This project presents a deep learning-based image classification system that identifies and classifies parking slots as **"Occupied"** or **"Free"** in a single static parking lot image.  

The system was built entirely from scratch using a **Convolutional Neural Network (CNN)**, without relying on pretrained models or video streams. After exploring multiple approaches such as automated contour detection and slot extraction via Google image datasets, we settled on a reliable method involving **manually annotated slot positions** and a CNN trained on full-frame labeled parking lot images.  

Our system achieved high accuracy and successfully marked over 200 slots, making it a promising solution for scenarios where consistent parking layout images are available.

---

## 2. Problem Statement

### Project Overview: Smarter Parking with Simple Images
Parking in busy urban areas can be a headache—both for drivers searching for spots and for managers trying to optimize space. While many high-tech solutions rely on live video feeds, this project tackles the problem differently:  

> Determine parking availability just from a single snapshot of a parking lot.

### The Goal
We’re developing a lightweight, efficient system that can:  
- Identify parking slots in a static image (no video required).  
- Classify each spot as **free** or **occupied** quickly and accurately.  
- Run on limited resources, making it accessible for smaller lots or budget-conscious setups.  

### Why It Matters
Not every parking lot needs (or can afford) complex camera systems. By using simple images, we can provide **real-time insights** without heavy infrastructure. Examples:  
- A shopping mall monitoring spots with occasional snapshots.  
- A small business optimizing its private lot.  
- City planners analyzing parking trends from periodic photos.  

This approach keeps things **simple, cost-effective, and scalable**, helping more places manage parking smarter.

---

## 3. Methodology

The project was carried out in stages:

### Initial Attempts
- **Automatic Contour Detection:** Used thresholding and edge detection to identify parking slots. Failed due to misaligned crops and poor accuracy.  
- **Google Image Dataset:** Tried using images from Google with auto-cropping, but classification quality was low.  

### Final Approach
- **Manual Slot Annotation:** Defined precise coordinates for each parking slot in the image.  
- **Data Collection:** Labeled full-frame images manually as "Free" or "Occupied".  
- **CNN Training:** Trained a deep learning model using data augmentation to generalize better.  
- **Classification:** Applied the trained model to cropped slots based on manual annotations.  

This approach provided the best balance of accuracy and control.

---

## 4. Tools and Technologies Used
- **Python**: Core programming language.  
- **OpenCV**: Image processing, thresholding, and visualization.  
- **TensorFlow / Keras**: Building and training the CNN.  
- **NumPy**: Numerical operations.  
- **SciPy**: Scientific and technical computing.  
- **Matplotlib**: Visualizing training metrics.  

---

## 5. Dataset Preparation & Preprocessing
- Organized a custom dataset into two classes:  
  - `Free/`  
  - `Occupied/`  
- Used full-frame parking lot images labeled manually.  
- Applied data augmentation techniques: rotation, flips, brightness adjustment, to improve generalization.  

---

## 6. Model Architecture
- **Input:** 64x64 RGB images  
- **Layers:**  
  - Conv2D → ReLU → MaxPooling  
  - Conv2D → ReLU → MaxPooling  
  - Flatten → Dense → Dropout → Dense (Sigmoid)  
- **Loss Function:** Binary Crossentropy  
- **Optimizer:** Adam  

---

