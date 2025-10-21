# 🏀 Sports Classifier: Reliable Deployment

This project provides an end-to-end deep learning solution for classifying various sports images (e.g., Badminton, Cricket, Swimming). The model was trained using the **FastAI** library on a ResNet-34 architecture and deployed as a Gradio application on Hugging Face Spaces.

## ⚙️ Model and Technical Stack

| Component | Detail | Badge |
| :--- | :--- | :--- |
| **Model Architecture** | ResNet-34 (Transfer Learning) | [![Model](https://img.shields.io/badge/Model-ResNet34-blue?style=for-the-badge)](https://pytorch.org/hub/pytorch_vision_resnet/) |
| **Deep Learning** | FastAI | [![FastAI](https://img.shields.io/badge/FastAI-5935A9?style=for-the-badge&logo=fastai&logoColor=white)](https://www.fast.ai/) |
| **Runtime Language** | Python 3.11 | [![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/) |
| **Interface** | Gradio | [![Gradio](https://img.shields.io/badge/Gradio-425A82?style=for-the-badge&logo=gradio&logoColor=white)](https://www.gradio.app/) |

---

## 📦 Project Structure and Setup

To run this application successfully, the current working directory of the Space requires the following minimal and essential files.

| File Name | Purpose | Notes |
| :--- | :--- | :--- |
| **`app.py`** | **Core Application** | Defines the Gradio interface and the `predict` function. |
| **`model.pkl`** | **Trained Model Weights** | The exported FastAI `Learner` object (uploaded via Git LFS). |
| **`requirements.txt`** | **Dependencies** | **Crucial** for environment setup, locking library versions. |
| **`README.md`** | **Space Configuration** | Sets the Python runtime (`python_version: 3.11`) and provides documentation. |
| **Example Images** | `badminton.jpg`, `cricket.jpg`, `swimming.jpg` | Used to populate the Gradio example panel. |

### Required Dependencies (`requirements.txt`)

The successful deployment required strictly locking versions due to cross-environment serialization issues:

```text
fastai==2.7.12
torch<2.2
torchvision<0.16
numpy<2.0 
gradio
cloudpickle 
fasttransform 
💡 Key Deployment Challenges & Solution
The stability of this deployment was achieved by addressing core version conflicts that are common when exporting models from newer Kaggle environments to standard Hugging Face Runtimes.

The Primary Problem (Fixed):

Symptom: TypeError: code expected at most 16 arguments, got 18

Cause: The Python bytecode inside the model.pkl was saved using a newer Python version (e.g., 3.11) and was incompatible with the default Space runtime (Python 3.10).

Solution: Forcing the runtime version to Python 3.11 via the README.md configuration.

Hidden Dependencies (Fixed):

Symptom: ModuleNotFoundError: No module named 'fasttransform'

Solution: All custom modules referenced by the model pickle (like fasttransform and cloudpickle) are explicitly included in requirements.txt.

📜 License
This project is licensed under the MIT License.
