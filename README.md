# 🌿 Plant Disease Recognition & Classification System

An end-to-end Deep Learning project designed to accurately identify and classify **38 different classes** of plant diseases and healthy crop leaves using a Convolutional Neural Network (CNN) built with **TensorFlow** and **Keras**.

---

## 📌 Context & Motivation

Plant diseases pose a significant threat to global food security, agricultural yield, and farmers' livelihoods. Traditional manual inspection of crops by experts is often labor-intensive, expensive, and impractical for large-scale farming.

This project implements a computer vision solution using deep learning to automate early disease diagnosis from leaf images. By accurately recognizing infection symptoms at an early stage, farmers can take prompt, targeted action to protect crops and minimize pesticide overuse.

---

## 📊 Dataset Information

This project uses the **New Plant Diseases Dataset** available on Kaggle:

* 🔗 **Dataset Link:** [New Plant Diseases Dataset on Kaggle](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset)
* **Total Images:** ~87,000+ RGB leaf photographs
* **Classes:** 38 distinct categories (healthy vs. diseased across 14 crop species)
* **Dataset Splits:**
  * `train/`: 70,295 images used for model training
  * `valid/`: 17,572 images used for model validation and fine-tuning
  * `test/`: Unseen test images for real-world verification

### Supported Crops & Diseases
The 38 classes cover diseases affecting:
* **Apple:** Apple Scab, Black Rot, Cedar Apple Rust, Healthy
* **Blueberry:** Healthy
* **Cherry (including sour):** Powdery Mildew, Healthy
* **Corn (Maize):** Cercospora Leaf Spot (Gray Leaf Spot), Common Rust, Northern Leaf Blight, Healthy
* **Grape:** Black Rot, Esca (Black Measles), Leaf Blight (Isariopsis Leaf Spot), Healthy
* **Orange:** Huanglongbing (Citrus Greening)
* **Peach:** Bacterial Spot, Healthy
* **Pepper (Bell):** Bacterial Spot, Healthy
* **Potato:** Early Blight, Late Blight, Healthy
* **Raspberry:** Healthy
* **Soybean:** Healthy
* **Squash:** Powdery Mildew
* **Strawberry:** Leaf Scorch, Healthy
* **Tomato:** Bacterial Spot, Early Blight, Late Blight, Leaf Mold, Septoria Leaf Spot, Two-Spotted Spider Mite, Target Spot, Yellow Leaf Curl Virus, Mosaic Virus, Healthy

---

## 🧠 Model Architecture & Training

* **Framework:** TensorFlow 2.10 / Keras
* **Hardware Acceleration:** NVIDIA GeForce RTX 3050 Laptop GPU (CUDA 11.8 & cuDNN 8.9)
* **Input Resolution:** `(128, 128, 3)` RGB images
* **Network Type:** Custom Deep Convolutional Neural Network (CNN)
  * Feature extraction using multiple `Conv2D` layers (ReLU, `padding="same"`) paired with `MaxPool2D`
  * Fully connected classifier (`Dense` layers) with `Dropout` for regularization
  * Output layer: `Dense(38, activation='softmax')`
* **Optimization & Loss:**
  * Optimizer: `Adam`
  * Loss Function: `categorical_crossentropy`
  * Metrics: `accuracy`

---

## 📈 Performance & Results

After 10 training epochs, the model achieved outstanding classification performance:

* **Training Accuracy:** ~96.7%
* **Validation Accuracy:** **~96.0%** (evaluated across all 17,572 validation images)
* **Macro & Weighted F1-Scores:** **0.96**

Detailed per-class precision, recall, and F1-score breakdown can be found in [`classification_report.json`](classification_report.json).

---

## 📁 Repository Structure

```text
├── train_plant_diesease.ipynb    # Main Jupyter Notebook for model building & training
├── requirements.txt             # Python dependencies
├── classification_report.json   # Full scikit-learn classification metrics per class
├── .gitignore                   # Ignored files (dataset directories, model weights, venvs)
└── README.md                    # Project documentation & dataset guide
```

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/varshi495/version-2.git
cd version-2
```

### 2. Set Up Virtual Environment (Python 3.10)
```bash
python -m venv .venv

# On Windows (PowerShell)
.\.venv\Scripts\Activate.ps1

# On Linux / macOS
source .venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Download and Place Dataset
1. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset).
2. Extract the archive into the project root so the folder structure looks like:
   ```text
   version-2/
   ├── train/
   ├── valid/
   └── test/
   ```
*(Note: These dataset folders are automatically ignored by Git to keep the repository lightweight).*

### 5. Run the Notebook
Open [`train_plant_diesease.ipynb`](train_plant_diesease.ipynb) in Jupyter Notebook or VS Code, select the `.venv` kernel, and run all cells.
