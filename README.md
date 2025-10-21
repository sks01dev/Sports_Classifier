# 🏀 Sports Classification Model: End-to-End Deployment

[![Hugging Face Space](https://img.shields.io/badge/Hugging%20Face-Space-blue)](https://huggingface.co/spaces/sks01dev/Sports_Classifier)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-black)](https://www.google.com/search?q=https://github.com/your-username/your-repo-name)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE.md)

This repository contains a **high-accuracy image classification model** capable of recognizing various sports activities such as **Badminton, Cricket, Swimming**, and more. The project emphasizes **MLOps best practices**, resolving cross-version serialization issues during deployment from a Kaggle kernel to a cloud runtime.

---

## ⚙️ Technical Stack & Architecture

The application is built on a modern, open-source stack with specific version constraints for stability.

| Component | Details | Reference |
|-----------|---------|-----------|
| **Model Architecture** | ResNet-34 (Transfer Learning) | [PyTorch ResNet](https://pytorch.org/hub/pytorch_vision_resnet/) |
| **Deep Learning Framework** | FastAI | [fast.ai](https://www.fast.ai/) |
| **Runtime Language** | Python 3.11 | [Python](https://www.python.org/) |
| **Inference Framework** | PyTorch | [PyTorch](https://pytorch.org/) |
| **Web Interface** | Gradio | [Gradio](https://www.gradio.app/) |

---

## 📦 Repository Contents

The repository is organized for **easy reproduction and deployment**.

| File/Folder | Purpose | Notes |
|-------------|---------|-------|
| `app.py` | **Inference Endpoint** | Initializes Gradio UI and loads the trained model. |
| `model.pkl` | **Trained Model Weights** | FastAI `Learner` object (stored via Git LFS). |
| `requirements.txt` | **Dependency Manifest** | Ensures stable environment by locking versions. |
| `README.md` | **Project Documentation** | Configures Hugging Face Space runtime. |
| `model-deployment.ipynb` | **Training Notebook** | Kaggle notebook with full data preparation & training pipeline. |
| `Example Images` | `.jpg` files | Sample inputs for testing the Gradio interface. |

---

## 💡 MLOps Solution Highlights

The main challenge was **environment incompatibility** between Kaggle (Python 3.11) and Hugging Face Spaces (Python 3.10 by default). This caused:

| Challenge | Error Message | Solution Implemented |
|-----------|---------------|--------------------|
| **Python Bytecode Incompatibility** | `TypeError: code expected at most 16 arguments, got 18` | Locked Space runtime to Python 3.11 via `README.md` configuration. |
| **Dependency Conflicts** | `ModuleNotFoundError: fasttransform` | Strict version pinning: FastAI `2.7.12`, `numpy<2.0`, ensured all dependencies (`fasttransform`, `cloudpickle`) are in `requirements.txt`. |

✅ This ensures **robust, stable deployment**, independent of environment changes.

---

## 🛠️ Local Reproduction

Follow these steps to run the application locally:

1. **Clone the repository:**

```bash
git clone --depth 1 --branch main [YOUR GITHUB REPO URL]
cd [YOUR GITHUB REPO NAME]
git lfs pull  # Download model.pkl
````

2. **Install dependencies:**

```bash
pip install -r requirements.txt
```

3. **Run the application:**

```bash
python app.py
```

The Gradio interface will launch in your default browser, ready to classify sports images.

---

## 📜 License

This project is licensed under the **MIT License**.

```text
MIT License

Copyright (c) 2025 Shivam Kumar Swarnkar

---

> Crafted with ❤️ for **reproducible, production-ready AI deployments**.

