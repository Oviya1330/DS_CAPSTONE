# Real-Time Sensitive Data Redaction System
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![NLP](https://img.shields.io/badge/NLP-DistilBERT-orange)](https://huggingface.co/distilbert-base-uncased)
[![Computer Vision](https://img.shields.io/badge/Computer%20Vision-OCR%20%2B%20OpenCV-red)]()
<!--[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)-->
> **DS Capstone — Northeastern University**

### Team Members  
- **Oviya Gnanasekar**  
- **Akshaj Nevgi**  
- **Zankhana Mehta**

---

## Project Overview  

### Problem Statement  
Sensitive information such as **PII, secret keys, emails, phone numbers** is often inadvertently shared in screenshots, documents, and images. This poses **privacy and security risks**.  

This project implements a **hybrid redaction system** that detects and masks sensitive text in images using a combination of **OCR, regex, and NLP models**, ensuring **data privacy and compliance**.

### Goal  
To design a **robust redaction pipeline** integrating:  
- OCR for text extraction from images  
- Regex for structured data detection  
- Transformer-based NLP (DistilBERT) for contextual sensitivity detection  
- OpenCV-based blurring for visual redaction  

The system is a **prototype**, with future extension to **video redaction pipelines**.

---

## Repository Structure

| Folder / File | Description |
|----------------|-------------|
| **/prototyping/** | Contains prototype experiments, datasets, notebooks, and images. |
| **/prototyping/pii_dataset/** | Preprocessed dataset splits: train, validation, test. |
| **/prototyping/results/** | Saved DistilBERT model artifacts. |
| **/prototyping/data_merge.ipynb** | Data merging and dataset statistics notebook. |
| **/prototyping/hybrid_detection.ipynb** | EDA, analytics, model training/testing, regex redaction. |
| **/prototyping/ocr_test.ipynb** | OCR implementation using pytesseract with pixel-level extraction. |
| **/prototyping/test1.png** | Example input image with sensitive information. |
| **/prototyping/redacted_output.png** | Example output image with sensitive data blurred. |

---

## Key Features

- **OCR Integration** – Extract text from images using Tesseract  
- **Context-Aware NLP Detection** – DistilBERT fine-tuned to detect sensitive text  
- **Pattern Matching** – Regex for structured sensitive data (emails, API keys, SSNs, credit cards)  
- **Redaction Engine** – Apply Gaussian blur to sensitive regions using OpenCV  
- **Prototype Pipeline** – Works on static images; can be extended to video frames  

---

## Methodology

| Step | Description | Tools |
|------|-------------|-------|
| **Data Merge** | Combined synthetic and external datasets (Faker, templates, WikiText). | Python, Faker, HuggingFace Datasets |
| **OCR Processing** | Extracted visible text and bounding box locations from images. | pytesseract, OpenCV |
| **Pattern Detection** | Detected structured sensitive data using regex rules. | Python Regex |
| **Contextual Detection** | Classified sensitive text using fine-tuned DistilBERT. | Hugging Face Transformers |
| **Redaction** | Applied Gaussian blur to detected bounding boxes in images. | OpenCV |
| **Evaluation** | Verified correct masking of sensitive words; checked label distribution. | Pandas, Scikit-learn |

---

## Experiments & Notebooks

| Notebook / File | Description | Link |
|-----------------|-------------|------|
| **data_merge.ipynb** | Merges datasets and generates final statistics (labels and categories). | [Open Notebook](./prototyping/data_merge.ipynb) |
| **hybrid_detection.ipynb** | Exploratory data analysis, DistilBERT training/testing, regex integration, static image redaction. | [Open Notebook](./prototyping/hybrid_detection.ipynb) |
| **ocr_test.ipynb** | OCR pixel-level extraction prototype to identify sensitive text locations. | [Open Notebook](./prototyping/ocr_test.ipynb) |
| **test1.png** | Example input image containing sensitive information. | [View Image](./prototyping/test1.png) |
| **redacted_output.png** | Redacted output image demonstrating Gaussian blur applied to sensitive data. | [View Image](./prototyping/redacted_output.png) |

---

## Future Work

Extend the pipeline to video redaction by processing individual frames

Improve detection for multi-word secrets or split OCR tokens

Integrate with real-time streaming systems for live redaction

