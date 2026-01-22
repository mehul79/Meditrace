# 💊 Drug Name Detection using YOLOv8

An end-to-end **computer vision project** that detects **drug/medicine names from images of medicine packaging** using **YOLOv8**.  
This project focuses on training, evaluating, and running inference on a custom dataset to localize medicine names accurately.

---

## 📌 Project Overview

Medicine packaging often contains critical information such as drug names, which can be difficult to extract automatically due to:
- Varying fonts and layouts  
- Reflections and noise in images  
- Different packaging styles  

This project solves the problem using **object detection**, identifying the region where the **drug name appears** in an image.

---

## 🚀 Features

- 📦 Custom **Drug Name Detection Dataset**
- 🤖 YOLOv8-based object detection model
- 🧠 End-to-end training pipeline
- 🔍 Inference on unseen test images
- 💾 Automatic saving of prediction outputs
- ⚡ Optimized for fast experimentation on Kaggle

---

## 🧠 Tech Stack

- **Python 3**
- **Ultralytics YOLOv8**
- **PyTorch**
- **NumPy & Pandas**
- **Kaggle Notebook Environment**

---

## 📂 Dataset

- Custom labeled dataset for **drug name detection**
- YOLO format annotations
- Dataset configuration defined in `data.yaml`

### Dataset Structure
```
dataset/
├── train/
│   ├── images/
│   └── labels/
├── test/
│   ├── images/
│   └── labels/
└── data.yaml
```

---

## 🏋️ Model Training

The model is trained using **YOLOv8 Nano** for efficient performance.

### Training Configuration
- Image size: `640`
- Epochs: `50`
- Batch size: `32`
- Model: `yolov8n`
- Task: Object Detection

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(
    data="data.yaml",
    imgsz=640,
    epochs=50,
    batch=32,
    name="yolov8n_v1"
)
```

Training outputs (weights, metrics, logs) are stored automatically in:
```
runs/detect/yolov8n_v1/
```

---

## 🔍 Inference & Prediction

Run inference on test images using the trained model:

```bash
yolo task=detect \
     mode=predict \
     model=best.pt \
     source=test/images \
     save=True
```

✔ Bounding boxes are drawn  
✔ Predictions are saved automatically  
✔ Ready for OCR or further processing  

---

## 📊 Results

- Successfully detects drug name regions across varied packaging styles
- Performs well under real-world lighting and orientation conditions
- Can be used as a **preprocessing step for OCR pipelines**

---

## 🧩 Use Cases

- 🏥 Healthcare & pharmacy automation  
- 📱 Medicine scanning mobile applications  
- 💊 Generic medicine recommendation systems  
- 🧾 Prescription and packaging analysis  
- 🇮🇳 Public healthcare cost-reduction platforms (e.g., Jan Aushadhi)

---

## 🔮 Future Improvements

- 🔠 Integrate OCR to extract detected drug names
- 📈 Train on a larger and more diverse dataset
- 🧠 Experiment with larger YOLOv8 variants
- 🌐 Deploy as an API or web application
- 📱 Optimize inference for mobile devices

---

## ▶️ How to Run Locally

```bash
pip install ultralytics
```

```python
from ultralytics import YOLO
model = YOLO("yolov8n.pt")
```

---

## 🤝 Contributing

Contributions are welcome!  
Feel free to open issues, submit pull requests, or suggest improvements.

---

## ✨ Author

**Mehul Gupta**  
AI / ML | Computer Vision | Backend Systems  
Focused on real-world, impact-driven AI solutions
