# Real-Time Sensitive Data Redaction System
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![NLP](https://img.shields.io/badge/NLP-DistilBERT-orange)](https://huggingface.co/distilbert-base-uncased)
[![Computer Vision](https://img.shields.io/badge/Computer%20Vision-OCR%20%2B%20OpenCV-red)]()

> **DS Capstone — Northeastern University**

### Team Members  
- **Oviya Gnanasekar**  
- **Akshaj Nevgi**  
- **Zankhana Mehta**

---

## Project Overview  

### Problem Statement  
Sensitive information such as **PII, API keys, secret keys, emails, and tokens** is frequently leaked through screenshots, UI demos, configuration tutorials, and video recordings.  
Even a **single frame** in a video can expose a valid credential.

This project implements a **hybrid redaction system** that detects and masks sensitive text from images and videos using:

- **EasyOCR** for robust text extraction  
- **Regex** for well-defined secret patterns  
- **DistilBERT** for contextual classification  
- **OpenCV** for region-level Gaussian blur redaction  

### Goal  
To build a **reliable, real-world redaction pipeline** that maintains high accuracy in noisy UI environments and supports:

- Image redaction  
- Full-frame video redaction  
- Developer-secret and PII detection  
- Contextual sensitivity classification  

---

## Repository Structure

| Folder / File | Description |
|----------------|-------------|
| **/prototyping/** | Contains all datasets, preprocessing scripts, and prototype code. |
| **/prototyping/pii_dataset/** | Final dataset splits (train, validation, test). |
| **/prototyping/results/** | DistilBERT fine-tuned model checkpoints. |
| **/prototyping/data_merge.ipynb** | Data generation and merging logic for text dataset. |
| **/prototyping/hybrid_detection.ipynb** | Full OCR → detection → redaction video/image pipeline. |
| **/prototyping/test1.png** | Example static input. |
| **/prototyping/redacted_output.png** | Example static output. |
| **/prototyping/input_videos/** | **Test videos used for evaluation (real YouTube screen recordings).** |

---

## About the Input Videos Folder (`input_videos/`)

The folder **`prototyping/input_videos/`** contains the **actual test videos** used for evaluating the video redaction pipeline.

These videos are:

- **Real screen recordings** captured from public YouTube tutorials  
- Videos where creators unintentionally exposed **actual API keys**  
- Recorded manually at 1080p to preserve UI clarity  
- Used to evaluate OCR robustness and real-world performance  

This ensures that the system is tested on **authentic, naturally occurring secret exposures**, not synthetic or staged videos.

---

## Key Features

- **EasyOCR-based OCR**  
  Outperforms Tesseract for UI screenshots, rotated text, low contrast, and video frames.

- **Hybrid Detection System**  
  - Regex for structured keys (AWS keys, long secrets, emails)  
  - DistilBERT for contextual classification  
  - GPT-4o-mini used **only for benchmarking**, not for production  

- **Full-Frame Video Redaction**  
  - Processes **every frame** to avoid missing a fast exposure  
  - Frame → OCR → classify → blur → reconstruct  

- **OpenCV Gaussian Blur**  
  Applied only to sensitive bounding boxes for minimal visual distortion.

- **Reproducible Dataset Pipeline**  
  - Synthetic + real PII text samples  
  - Real YouTube-based video frames for evaluation  

---

## Methodology

| Step | Description | Tools |
|------|-------------|-------|
| **Dataset Generation** | Combined real PII (AI4Privacy), synthetic secrets (Faker), and WikiText into an 80k dataset. | Python, Faker, HuggingFace |
| **OCR Processing** | Extracted text + bounding boxes from images and frames. | EasyOCR, OpenCV |
| **Pattern Detection** | Regex for well-defined sensitive patterns. | Python |
| **Contextual Detection** | DistilBERT identifies ambiguous sensitive tokens. | Hugging Face Transformers |
| **Redaction Engine** | Gaussian blur applied to sensitive bounding boxes. | OpenCV |
| **Video Pipeline** | Processes every frame → detects → blurs → reconstructs video. | Python, OpenCV |

---

## Data Generation 

### Text Dataset (80,000 Samples)
Built from:

1. **Real PII (AI4Privacy)**  
2. **Synthetic secrets** (AWS keys, JWT-like tokens, long secrets, corrupted OCR variants)  
3. **WikiText background text** for natural context  

Balanced dataset with an **8k holdout test set**.

### Video Dataset
- Real screen recordings of **YouTube videos** exposing credentials  
- No synthetic or rendered footage  
- Captures natural UI complexity and OCR variation  
- Each frame is processed because secrets may appear **for a single frame**  

---

## Experiments & Notebooks

| Notebook | Description | Link |
|----------|-------------|------|
| **data_merge.ipynb** | Builds dataset from real + synthetic text sources. | [Open](./prototyping/data_merge.ipynb) |
| **hybrid_detection.ipynb** | Full OCR + DistilBERT + Regex + Redaction pipeline. | [Open](./prototyping/hybrid_detection.ipynb) |

---

## Future Work

- Faster polygonal OCR ( PaddleOCR)  
- Real-time video redaction  
- Multi-token secret reconstruction for broken OCR strings  
- DistilBERT quantization for live deployment  


