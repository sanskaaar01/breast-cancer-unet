
---

# 🧠 Breast Tumor Segmentation using U-Net......

Deep learning–based semantic segmentation of breast ultrasound images using an enhanced U-Net architecture.

This project focuses on **pixel-level tumor localization**, providing clinically meaningful output beyond simple image classification.

---

## 📌 Overview

Breast cancer is one of the most prevalent cancers worldwide. Ultrasound imaging is widely used for early detection due to its safety and accessibility.

The objective of this project is to build a deep learning model capable of accurately segmenting tumor regions from breast ultrasound images.

Unlike classification models that only predict presence or absence of cancer, this implementation performs **semantic segmentation**, identifying the exact tumor boundaries at the pixel level.

---

## 🗂 Dataset

**Breast Ultrasound Images Dataset (BUSI)**

* ~780 ultrasound images (benign, malignant, normal)
* 647 images used for segmentation (benign + malignant)
* Binary ground-truth masks provided
* Images resized to 128×128 (grayscale)

📎 Dataset Source: Kaggle – Breast Ultrasound Images Dataset

> ⚠ The dataset is not included in this repository.
> Download it from Kaggle and place it inside:
>
> ```
> data/Dataset_BUSI_with_GT/
> ```

---

## 🏗 Model Architecture

The model implements an improved U-Net architecture with:

* Encoder–decoder structure with skip connections
* Batch Normalization for stable training
* Dropout for regularization
* Combined Binary Crossentropy + Dice Loss
* Adam optimizer (learning rate = 1e-4)
* EarlyStopping and ReduceLROnPlateau callbacks

The network performs binary pixel classification to generate tumor segmentation masks.

---

## 📊 Evaluation Metrics

The model was evaluated using segmentation-specific metrics rather than simple accuracy.

### Dice Coefficient

Measures the overlap between predicted and ground-truth tumor masks.

```
Dice = (2 × TP) / (2 × TP + FP + FN)
```

### Intersection over Union (IoU)

Measures how well the predicted tumor region matches the actual tumor region.

```
IoU = TP / (TP + FP + FN)
```

### Why Not Pixel Accuracy?

Pixel accuracy is not emphasized because background pixels dominate medical images, making accuracy misleading for segmentation tasks.

---

## 📈 Results

| Metric           | Score                       |
| ---------------- | --------------------------- |
| Dice Coefficient | ~0.55                       |
| IoU              | ~0.45                       |
| Pixel Accuracy   | High but not representative |

The model demonstrates moderate tumor localization performance given the limited dataset size.

---

## 📉 Training Analysis

* Mild overfitting observed due to limited dataset size
* Learning rate scheduling improved convergence stability
* Validation Dice stabilized between 0.48–0.55
* Combined BCE + Dice loss improved segmentation consistency

Training curves and sample predictions are available in the `outputs/` folder.

---

## 📂 Project Structure

```
breast-cancer-unet/
│
├── models/
│   └── unet_breast_cancer_model.h5
│
├── notebooks/
│   └── 01_unet_training.ipynb
│
├── outputs/
│   ├── training_curves.png
│   └── prediction_samples.png
│
├── README.md
└── requirements.txt
```

---

## 🛠 Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/breast-cancer-unet.git
cd breast-cancer-unet
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## ▶ How to Run

1. Download the dataset from Kaggle.
2. Place it inside:

   ```
   data/Dataset_BUSI_with_GT/
   ```
3. Open:

   ```
   notebooks/01_unet_training.ipynb
   ```
4. Run all cells from top to bottom.

---

## ⚠ Limitations

* Small dataset (~647 images)
* Class imbalance between tumor and background
* No external validation dataset
* Not clinically validated
* Intended for research and educational purposes only

This model is **not suitable for real-world medical diagnosis**.

---

## 🚀 Future Improvements

* Implement Attention U-Net
* Use pretrained encoder (ResNet-based U-Net)
* Apply stronger augmentation techniques
* Perform k-fold cross-validation
* Train on larger multi-institution datasets
* Conduct clinical validation studies

---

## 🛠 Technologies Used

* Python
* TensorFlow / Keras
* NumPy
* OpenCV
* Matplotlib
* scikit-learn

---

## 👤 Author

**Sanskar Bhosle**
Data Science & Machine Learning Enthusiast

---

# 💡 Key Highlights

* Applied deep learning for medical image segmentation
* Used appropriate evaluation metrics for imbalanced data
* Built a reproducible ML pipeline
* Demonstrated structured model evaluation and analysis

---

