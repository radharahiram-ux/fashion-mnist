@<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=200&section=header&text=Fashion%20MNIST&fontSize=60&fontColor=fff&animation=twinkling&fontAlignY=35&desc=End-to-End%20Deep%20Learning%20Classifier&descAlignY=60&descSize=20" width="100%"/>

<br/>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)](https://tensorflow.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io)
[![Docker](https://img.shields.io/badge/Docker-Container-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://docker.com)
[![License](https://img.shields.io/badge/License-MIT-22C55E?style=for-the-badge)](LICENSE)

<br/>

> **Build · Train · Deploy** — A production-ready image classifier for 10 fashion categories,  
> wrapped in a Streamlit UI and shipped as a Docker container.

<br/>

[![▶ Watch on YouTube](https://img.shields.io/badge/▶%20Watch%20Step--by--Step%20Guide-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/sb2tm3pu17k)

</div>

---

## 📸 Demo

<div align="center">

| Upload an image | Get instant prediction |
|:---:|:---:|
| ![Upload](https://placehold.co/340x220/1e1e2e/cdd6f4?text=Drag+%26+Drop+Image) | ![Result](https://placehold.co/340x220/1e1e2e/a6e3a1?text=👟+Sneaker+%E2%80%94+98.2%25) |

> *Replace placeholders above with actual screenshots of your running app*

</div>

---

## 🗂 Table of Contents

- [Overview](#-overview)
- [Fashion Categories](#-fashion-categories)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Quick Start](#-quick-start)
- [Docker Deployment](#-docker-deployment)
- [Model Performance](#-model-performance)
- [Tech Stack](#-tech-stack)
- [Video Tutorial](#-video-tutorial)
- [License](#-license)

---

## 🌟 Overview

This project walks through the **complete MLOps lifecycle** — from raw data to a live, containerised web application:

1. 📦 **Data** — Load and preprocess the Fashion MNIST dataset (60 k training / 10 k test images)
2. 🧠 **Model** — Build and train a CNN with TensorFlow / Keras
3. 🖥️ **App** — Wrap the trained model in a Streamlit web interface
4. 🐳 **Deploy** — Package everything in a Docker container for consistent, portable deployment

---

## 👗 Fashion Categories

The model classifies grayscale 28 × 28 images into **10 clothing categories**:

<div align="center">

| Label | Category | Label | Category |
|:---:|:---|:---:|:---|
| `0` | 👕 T-shirt / Top | `5` | 👟 Sandal |
| `1` | 👖 Trouser | `6` | 👔 Shirt |
| `2` | 🧥 Pullover | `7` | 👟 Sneaker |
| `3` | 👗 Dress | `8` | 👜 Bag |
| `4` | 🧣 Coat | `9` | 👢 Ankle Boot |

</div>

---

## 🏗 Architecture

```
Input (28×28 grayscale)
        │
        ▼
┌───────────────────┐
│  Conv2D 32 × 3×3  │  ← ReLU activation
│  MaxPooling 2×2   │
└───────────────────┘
        │
        ▼
┌───────────────────┐
│  Conv2D 64 × 3×3  │  ← ReLU activation
│  MaxPooling 2×2   │
└───────────────────┘
        │
        ▼
┌───────────────────┐
│     Flatten       │
│  Dense 128 ReLU   │
│   Dropout 0.5     │
│  Dense 10 Softmax │  ← 10 class probabilities
└───────────────────┘
```

---

## 📁 Project Structure

```
fashion-mnist-end-to-end/
│
├── 📂 model/
│   ├── train.py            # Model training script
│   ├── evaluate.py         # Evaluation & metrics
│   └── fashion_model.h5    # Saved trained model
│
├── 📂 app/
│   ├── app.py              # Streamlit application
│   └── utils.py            # Preprocessing helpers
│
├── 📂 notebooks/
│   └── exploration.ipynb   # EDA & prototyping
│
├── 🐳 Dockerfile           # Container definition
├── 📋 requirements.txt     # Python dependencies
└── 📖 README.md
```

---

## ⚡ Quick Start

### 1 — Clone the repository

```bash
git clone https://github.com/your-username/fashion-mnist-end-to-end-project.git
cd fashion-mnist-end-to-end-project
```

### 2 — Create a virtual environment

```bash
python -m venv venv

# macOS / Linux
source venv/bin/activate

# Windows
venv\Scripts\activate
```

### 3 — Install dependencies

```bash
pip install -r requirements.txt
```

### 4 — Train the model

```bash
python model/train.py
```

### 5 — Launch the Streamlit app

```bash
streamlit run app/app.py
```

Open your browser at **http://localhost:8501** and start classifying!

---

## 🐳 Docker Deployment

### Build the image

```bash
docker build -t fashion-mnist-app .
```

### Run the container

```bash
docker run -p 8501:8501 fashion-mnist-app
```

### Or pull from Docker Hub *(if published)*

```bash
docker pull your-dockerhub-username/fashion-mnist-app
docker run -p 8501:8501 your-dockerhub-username/fashion-mnist-app
```

Visit **http://localhost:8501** — the app is live inside a fully isolated container. ✅

---

## 📊 Model Performance

<div align="center">

| Metric | Value |
|:---|:---:|
| Training Accuracy | ~92% |
| Validation Accuracy | ~91% |
| Test Accuracy | ~91% |
| Parameters | ~1.2 M |
| Inference Time | < 50 ms |

</div>

> Metrics may vary slightly across runs due to random initialisation. Tune `epochs` and `batch_size` in `train.py` to experiment.

---

## 🛠 Tech Stack

<div align="center">

| Layer | Technology |
|:---|:---|
| Language | Python 3.10+ |
| Deep Learning | TensorFlow 2.x · Keras |
| Data | Fashion MNIST (via `tensorflow.keras.datasets`) |
| Web App | Streamlit |
| Containerisation | Docker |
| Image Processing | NumPy · Pillow |
| Visualisation | Matplotlib · Seaborn |

</div>

---

## 🎬 Video Tutorial

A full step-by-step walkthrough is available on YouTube — covering every phase from data loading to Docker deployment:

<div align="center">

[![Fashion MNIST End-to-End Tutorial](https://img.shields.io/badge/▶%20Watch%20the%20Full%20Tutorial-FF0000?style=for-the-badge&logo=youtube&logoColor=white&labelColor=282828)](https://youtu.be/sb2tm3pu17k)

</div>

Topics covered in the video:

- ✅ Dataset exploration and preprocessing
- ✅ CNN architecture design with Keras
- ✅ Training, evaluation, and saving the model
- ✅ Building the Streamlit prediction interface
- ✅ Writing the Dockerfile and containerising the app
- ✅ Running and testing the container locally

---

## 🤝 Contributing

Contributions are welcome! To get started:

```bash
# Fork the repo, then:
git checkout -b feature/your-feature-name
git commit -m "Add: your feature description"
git push origin feature/your-feature-name
# Open a Pull Request
```

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=120&section=footer" width="100%"/>

**Made with ❤️ for the ML community**

⭐ Star this repo if it helped you — it means a lot!

</div>
