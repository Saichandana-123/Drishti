# Drishti

## Adaptive Multi-Weather Preprocessing Framework for Robust Object Detection

---

## Overview

Object detection models such as YOLO achieve strong performance under standard conditions but experience significant degradation in adverse environments such as fog, rain, dust, and low-light scenarios.

This project presents **Drishti**, a unified adaptive preprocessing framework that enhances input images based on environmental conditions before performing object detection.

---

## Problem Statement

In real-world deployments, object detection systems must operate under diverse environmental conditions. However:

* Visibility is reduced in fog and haze
* Illumination is poor in low-light conditions
* Noise and distortion are introduced in rain and dust

Existing approaches either apply fixed preprocessing techniques or train separate models for different conditions, both of which have limitations in adaptability and efficiency.

---

## Proposed Method

The proposed framework introduces a condition-aware pipeline consisting of three stages:

1. **Weather Classification**
   The input image is categorized into one of several environmental conditions.

2. **Condition-Specific Preprocessing**
   Based on the identified condition, an appropriate enhancement method is applied.

3. **Object Detection**
   The processed image is passed to a pretrained YOLO detector.

---

## Pipeline

```
Input Image
     ↓
Weather Classifier
     ↓
[ Fog | Low-Light | Rain/Dust | Normal ]
     ↓
Condition-Specific Preprocessing
     ↓
YOLOv5 / YOLOv8 Detector
     ↓
Detections
```

---

## Novelty

* Introduces explicit condition classification prior to preprocessing
* Applies targeted enhancement instead of generic image processing
* Maintains a single unified pipeline rather than multiple specialized models
* Improves robustness without retraining the detection model

---

## Related Work

* IA-YOLO (AAAI 2022) – Image-adaptive enhancement for object detection
* ERUP-YOLO (WACV 2025) – Unified preprocessing filters
* AIE-YOLO (2024) – Adaptive enhancement modules

---

## Datasets

The following datasets are used for evaluation:

* RTTS – Foggy weather images
* ExDark – Low-light images
* PASCAL VOC – Standard benchmark dataset

---

## Methodology

### Weather Classification

* Lightweight CNN or MobileNetV2
* Classes: Fog, Low-Light, Rain/Dust, Normal

### Preprocessing Techniques

| Condition | Method                                   |
| --------- | ---------------------------------------- |
| Fog       | Dehazing / Contrast Enhancement          |
| Low-Light | Gamma Correction / Brightness Adjustment |
| Rain/Dust | Denoising / Filtering                    |
| Normal    | No preprocessing                         |

### Object Detection

* YOLOv5 / YOLOv8 (pretrained)
* No additional training required

---

## Experiments

The following configurations are evaluated:

* Baseline YOLO (no preprocessing)
* IA-YOLO (reference method)
* Drishti (proposed method)

**Evaluation Metric:**

* Mean Average Precision (mAP)

---

## Results

(To be updated)

---

## Project Structure

```
Drishti/
│── datasets/
│── classifier/
│── preprocessing/
│── detection/
│── results/
│── README.md
```

---

## Setup

```
git clone https://github.com/your-username/Drishti.git
cd Drishti
pip install -r requirements.txt
```

---

## Usage

```
python detect.py --source <image_path>
```

---

## Future Work

* Extension to additional weather conditions such as snow
* Integration of learnable preprocessing modules
* End-to-end optimization with detection feedback

---

## Team

Drishti

---

## Acknowledgements

* IA-YOLO authors
* YOLOv5 / YOLOv8 contributors
* Dataset providers

---
