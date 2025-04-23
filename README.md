# 🌿 Plant Disease Classification Using Convolutional Neural Networks

## 📁 Project Overview
This project aims to classify plant diseases using deep learning, specifically Convolutional Neural Networks (CNNs), applied to a large image dataset of leaves showing various symptoms. The model can automatically detect the type of plant and whether it is healthy or suffering from a specific disease.

---

## 📊 Dataset Description

**Source**: [New Plant Diseases Dataset (Augmented)](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset)

**Structure**:
- The dataset contains **over 87,000 images** spread across **38 categories**.
- Each category is stored in a folder named using the pattern:

- For example:
- `Apple___Apple_scab`
- `Corn_(maize)___Common_rust`
- `Grape___healthy`

**Classes**:
- Each image belongs to a combination of a **plant type** (e.g., Apple, Corn) and a **disease type** (e.g., Black_rot, healthy).
- The challenge includes parsing these labels and potentially handling them as **multi-label classification** tasks.

---

## ⚠️ Challenges

1. **Label Structure**  
 The dataset uses combined class names (`Plant___Disease`), requiring custom preprocessing to separate plant type and disease type.

2. **Data Imbalance**  
 Some classes (e.g., healthy leaves) are overrepresented, which may bias the model if not handled properly.

3. **Overfitting Risk**  
 Due to the relatively small number of unique visual features for some diseases, there's a risk of overfitting.

4. **Real-World Variation**  
 Augmented data does not always reflect true environmental variability in field conditions.

---

## 🧠 Methodology

- **Framework**: TensorFlow & Keras
- **Model**: Custom Convolutional Neural Network (CNN)
- **Preprocessing**:
- Normalized pixel values
- Resized images to `256x256`
- Extracted plant and disease labels from directory structure
- **Data Loading**:
- Used `tf.data.Dataset` with `cache()` and `prefetch()` for efficient training
- Applied `data augmentation` (random flips, rotations) to improve generalization
- **Training**:
- Used `EarlyStopping` and `ModelCheckpoint` callbacks
- Optimized with `Adam` optimizer and `categorical_crossentropy` loss

---

## 📈 Results

- **Accuracy Achieved**: ~**98.5%** on validation set
- **Loss**: < 0.05 after convergence
- **Training Time**: ~12 minutes (using GPU)
- **Observations**:
- Model performs exceptionally well on clear, high-resolution samples.
- Slightly lower confidence on visually similar disease categories (e.g., `Apple___Apple_scab` vs. `Apple___Cedar_apple_rust`).

---

## 📌 Future Improvements

- Experiment with **transfer learning** (e.g., MobileNetV2, EfficientNet)
- Implement **multi-output classification** to predict plant and disease as separate targets
- Add **explainability tools** (e.g., Grad-CAM) to visualize what the model is focusing on
- Address class imbalance using **class weights** or **oversampling**

---

## 🧪 Example Prediction

> Input: Image of a corn leaf with yellowing spots  
> **Prediction**:  
> - Plant: Corn  
> - Disease: Cercospora Leaf Spot  
> - Confidence: 97.3%

---

## 🤝 Acknowledgements

- Kaggle dataset by **Vipin Kumar**
- TensorFlow documentation and community
- Academic literature on plant pathology and deep learning

---

*This project demonstrates the power of deep learning in automating disease detection in crops, with potential applications in precision agriculture and food security.*
