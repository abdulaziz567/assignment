---

## 🚀 Live Demo

👉 https://huggingface.co/spaces/jawadix/saferoad-ai

---

title: Smart Traffic AI - Seatbelt Compliance Monitoring
emoji: 🚘
colorFrom: orange
colorTo: red
sdk: streamlit
sdk_version: "1.35.0"
app_file: app.py
pinned: false
license: mit
------------

# 🚘 Smart Traffic AI - Seatbelt Compliance Monitoring & Plate Recognition

A computer vision based traffic surveillance solution designed to improve road safety by automatically identifying seatbelt violations and recording vehicle information.

### Key Capabilities

* Detects drivers wearing and not wearing seatbelts using **YOLOv8**
* Flags seatbelt violations in real-time
* Locates the closest vehicle license plate
* Reads plate numbers through **Tesseract OCR**
* Saves violation records into **PostgreSQL**
* Provides an interactive **Streamlit** dashboard for monitoring

---

## 🎯 Project Overview

This project focuses on developing an intelligent road monitoring system capable of detecting drivers, determining seatbelt usage status, identifying traffic violations, recognizing vehicle license plates, extracting text information through OCR, storing records in a database, and presenting results through a web-based interface.

---

## 🔍 Processing Flow

```text
Image / Video Input
        ↓
YOLOv8 Seatbelt Detection Model
        ↓
Driver Classification
   ├── Seatbelt Detected
   └── Seatbelt Missing
        ↓
Violation Identification
        ↓
License Plate Detection
        ↓
Nearest Plate Association
        ↓
Plate Cropping & OCR
        ↓
Text Extraction
        ↓
PostgreSQL Storage
        ↓
Streamlit Dashboard Visualization
```

---

## 📂 Repository Layout

```text
saferoad-ai/
│
├── app.py
├── line_crossing.py
├── requirements.txt
├── README.md
│
├── models/
│   ├── __init__.py
│   └── detector.py
│
├── db/
│   ├── __init__.py
│   └── database.py
│
└── train/
    ├── __init__.py
    └── train_models.py
```

---

## 🚀 Getting Started

### Install Required Packages

```bash
pip install -r requirements.txt
```

### Install Tesseract OCR

Ubuntu / Debian:

```bash
sudo apt install tesseract-ocr
```

macOS:

```bash
brew install tesseract
```

Windows:

Download and install the official Tesseract package for Windows.

---

### Model Training

#### Seatbelt Detection

```bash
python train/train_models.py \
--task seatbelt \
--api_key YOUR_API_KEY \
--epochs 50 \
--imgsz 640
```

#### License Plate Detection

```bash
python train/train_models.py \
--task plate \
--api_key YOUR_API_KEY \
--epochs 50 \
--imgsz 640
```

After training, move the generated weight files into the models directory.

---

### Launch Application

```bash
streamlit run app.py
```

---

## 📊 Training Datasets

| Dataset                       | Purpose                        |
| ----------------------------- | ------------------------------ |
| Seat Belt Detection Dataset   | Driver Seatbelt Classification |
| Vehicle License Plate Dataset | License Plate Localization     |

---

## 🗄 Database Structure

The system records:

* Plate Number
* Violation Category
* Detection Confidence
* Timestamp
* Source Image Name
* Video Frame Information

All records are stored inside PostgreSQL and can also be exported as CSV files when required.

---

## 🖥 Dashboard Modules

| Module                | Function                                               |
| --------------------- | ------------------------------------------------------ |
| Image Analysis        | Detect violations from uploaded images                 |
| Video Analysis        | Process uploaded videos frame-by-frame                 |
| Violation Records     | Review and export stored results                       |
| Line Crossing Monitor | Trigger inspections based on virtual boundary crossing |

---

## 🛠 Technologies Used

| Area                | Technology          |
| ------------------- | ------------------- |
| Detection Model     | YOLOv8              |
| OCR Engine          | Tesseract OCR       |
| Backend Database    | PostgreSQL          |
| User Interface      | Streamlit           |
| Deployment Platform | Hugging Face Spaces |
| Image Processing    | OpenCV & Pillow     |

---

## 📌 Additional Information

* The application can operate in demonstration mode when trained model files are unavailable.
* For full functionality, place trained YOLO weight files inside the `models/` directory.
* Model availability is verified automatically during application startup.
* Generated violations can be viewed, filtered, and exported directly from the dashboard.
