# Amharic-MMOCR
Custom Amharic OCR using a lightweight MMOCR framework. Highly optimized for CPU-only environments featuring mini-batch configurations, gradient accumulation settings, and complete Ethiopic script token support.


# 🇪🇹 Mini MMOCR for Amharic

A lightweight, CPU-optimized Optical Character Recognition (OCR) pipeline built on OpenMMLab's MMOCR framework, specifically tailored for the Amharic language (Ge'ez/Ethiopic script). 

This project downscales heavy architectures into a "mini" variant designed to run efficiently on commodity CPU hardware without causing system freezes.

---

## ✨ Features

* **Complete Script Support:** Configured dictionary containing the 300+ primary Amharic characters (including punctuation and numbers).
* **CPU-Optimized Pipelines:** Low memory footprint, optimized thread configurations, and micro-batch pipelines to prevent VRAM dependency.
* **End-to-End OCR:** Modular structure featuring lightweight text detection (e.g., DBNet) paired with an efficient text recognizer.

---

## ⚙️ CPU Training & Performance Tweaks

Training deep learning models on a CPU requires careful resource balance. This repository is configured by default with the following hardware protections:

* **Micro-Batching:** Configured with a `batch_size` of `2` or `4` to prevent main memory caching bottlenecks.
* **Gradient Accumulation:** Uses accumulated steps to simulate standard larger batch sizes (`effective_batch_size = 32`) without increasing processing overhead.
* **Thread Capping:** Codebase automatically limits multi-threading workers to prevent 100% system thread locking.

---

## 🚀 Quick Start

### 1. Prerequisites & Installation
Ensure you have Python 3.8+ installed. It is highly recommended to build this inside a clean virtual environment or Conda environment.

```bash
# Clone the repository
git clone [https://github.com/YOUR_USERNAME/amharic-mini-mmocr.git](https://github.com/YOUR_USERNAME/amharic-mini-mmocr.git)
cd amharic-mini-mmocr

# Install OpenMMLab base tools & dependencies
pip install -U openmim
mim install mmengine
mim install "mmcv>=2.0.0"
mim install "mmdet>=3.0.0"

# Install MMOCR editable version
pip install -v -e .
