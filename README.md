# PNID_OCR_Training_Using_GELAN-E_And_Paddle_Text_Recognition

# OCR Custom Model Training Project  
This project implements a **robust end-to-end OCR pipeline** combining **YOLOv9-gelan-e** for **text detection** and **PaddleOCR (PPOCR)** for **text recognition**.  
It is designed to handle **large-scale images**, apply **custom augmentations**, and build fully **trainable datasets** for both detection and recognition.  

---

## Project Overview  

- **Detection Model:** YOLOv9-gelan-e (GPL-3.0 License)  
- **Recognition Model:** PaddleOCR (PPOCR)  
- **Core Features:**  
  - Smart image preprocessing (cropping from 8000×9000 → 1792×1792)  
  - Automated dataset verification and label transformations  
  - Augmentation strategies for robustness (rotation, color, blur, noise)  
  - End-to-end dataset preparation for detection & recognition  
  - Training pipelines for both YOLOv9 and PPOCR  

---

## Step-by-Step Execution  

### 1. Image Preprocessing  
- Cropping large images into **1792×1792 patches** for YOLOv9 compatibility.  
- Automated script (`Preparing_Dataset.ipynb`) skips already-processed images.  

### 2. Dataset Verification & Label Preprocessing  
- Dataset consistency checks for detection & recognition.  
- **90° rotation augmentation** with bounding box adjustments.  
- Optional augmentations (color distortion, Gaussian blur, noise).  

### 3. Object Detection Model Training (YOLOv9)  
<pre>
'''
- Dataset format:  
    detection_dataset/
    ├── train/
    │ ├── images/
    │ └── labels/
    ├── val/
    │ ├── images/
    │ └── labels/
    └── data.yaml
'''
</pre>

- Training parameters:  
- Batch size: **1**  
- Image size: **1792**  
- Model: **YOLOv9-gelan-e**  

### 4. 🔹 Text Recognition Model Training (PaddleOCR)  
- Dataset format:  
<pre>
'''
recognition_dataset/
├── train_images/
├── valid_images/
├── train.txt
└── valid.txt
'''
</pre>

- `train.txt` example:  

train_images/img_1.jpg Hello
train_images/img_2.jpg World

- Custom YAML config for PaddleOCR to define architecture, optimizer, and dataset paths.  
---

## 📂 Label Formats  

**Detection (YOLO format):**  
class_id x_center y_center width height
- Normalized values between 0 and 1.  

**Recognition (PaddleOCR format):**  


---

## 🏆 Results  

✨ Below are some results from detection + recognition on custom datasets.  

📌 *Replace with actual images after training*  

![Result 1](results/result1.png)  
![Result 2](results/result2.png)  
![Result 3](results/result3.png)  

---

## ✅ Conclusion  

This project successfully implements a **custom OCR training pipeline** with:  
- 📌 Smart cropping and preprocessing  
- 📌 Rotation-based label augmentation  
- 📌 YOLOv9 detection + PaddleOCR recognition  
- 📌 Fully open-source & reproducible (GPL-3.0)  

---

## 🔗 References  
- [YOLOv9 Official Repo](https://github.com/WongKinYiu/yolov9)  
- [PaddleOCR Official Repo](https://github.com/PaddlePaddle/PaddleOCR)  

---