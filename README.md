# 🧠 Real-Time Sensitive Data Redaction System
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![NLP](https://img.shields.io/badge/NLP-DistilBERT-orange)](https://huggingface.co/distilbert-base-uncased)
[![Computer Vision](https://img.shields.io/badge/Computer%20Vision-OCR%20%2B%20OpenCV-red)]()
<!--[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)-->
> **DS5500 Data Science Capstone — Northeastern University**

### 👩‍💻 Team Members  
- **Oviya Gnanasekar**  
- **Akshaj Nevgi**  
- **Zankhana Mehta**

---
## 📘 Project Overview  

### 🎯 Problem Statement  
Over **78% of remote workers** have accidentally shared sensitive information (like passwords, API keys or emails) during screen sharing, leading to severe data breaches.  

This project proposes an **AI-driven real-time redaction system** that automatically detects and masks sensitive data from live screens, documents and videos ensuring **data privacy and compliance** in everyday digital communication.

### 💡 Goal  
To design a **multi-modal redaction pipeline** integrating:
- OCR for text extraction  
- Regex for structured pattern detection  
- Transformer-based NLP for contextual sensitivity detection  
- Real-time OpenCV masking for visual redaction  
All under **<5s latency** per frame.

---
## 🧩 Repository Structure

| Folder / File | Description |
|----------------|-------------|
| **/prototyping/** | Phase 1: Prototype experiments combining OCR, regex and NLP layers. |

---
## 🔍 Key Features

-  **OCR Integration** – Text extraction using Tesseract + EasyOCR  
-  **Context-Aware NLP Detection** – Transformer-based DistilBERT classifier  
-  **Pattern Matching** – Regex for structured data (emails, phone numbers, AWS keys)  
-  **Redaction Engine** – OpenCV-based masking and blurring  
-  **Real-Time Pipeline** – Multi-threaded optimization for <5s latency  
-  **Cross-Platform Ready** – Python + FastAPI backend (future Electron-based UI)

---
## 🧠 Methodology

| Step | Description | Tools |
|------|--------------|-------|
| **Data Collection** | Collected real and synthetic screen captures; annotated using CVAT/Label Studio. | Faker, HuggingFace, WikiText |
| **OCR Processing** | Extracted visible text from screenshots and frames. | Tesseract |
| **Pattern Detection** | Used regex rules for structured entities (e.g., SSNs, AWS keys, emails). | Python Regex |
| **Contextual Detection** | Detected unstructured sensitive text using fine-tuned DistilBERT. | Hugging Face Transformers |
| **Redaction** | Masked or blurred detected areas dynamically. | OpenCV |
| **Evaluation** | Measured precision, recall, and latency for real-time targets. | Scikit-learn |

---
## 🧪 Experiments

| Notebook | Description |
|-----------|-------------|
| **p1.ipynb** | Baseline OCR + Regex prototype demonstrating static image redaction. |
| **p2.ipynb** | Hybrid OCR + NLP contextual detection using DistilBERT classifier. |
| **aws_key_detector/** | Specialized detection for AWS-style access/secret keys. |
| **redacted_output.png** | Demonstrates successful masking of sensitive data. |

---
