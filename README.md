# 🌾 SmartFarm - Crop Recommendation System

## 📊 Project Overview

This project implements a **machine learning-based crop recommendation system** to assist farmers in making informed decisions based on environmental and soil conditions. It predicts the most suitable crop to cultivate using key parameters like **Nitrogen (N)**, **Phosphorus (P)**, **Potassium (K)**, **Temperature**, **Humidity**, and **Rainfall**.

> ✅ Final Model: **Naive Bayes**
>  
> 🎯 Accuracy Achieved: **95%**

---

## 📁 Dataset

- **Dataset Name**: `Crop_recommendation.csv`  
- **Source**: [Kaggle - Crop Recommendation Dataset](https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset?resource=download)  
- **Records**: 2200  
- **Features**:
  - `N`: Nitrogen content in soil
  - `P`: Phosphorous content in soil
  - `K`: Potassium content in soil
  - `temperature`: in °C
  - `humidity`: in %
  - `ph`: soil pH value
  - `rainfall`: in mm
  - `label`: Target crop (22 unique crops)

---

## 🧪 Project Workflow

### 1. 📥 Data Preprocessing
- Handled missing values (if any)
- Performed **train-test split** (70-30)
- Applied **feature scaling** using `StandardScaler`

### 2. 📈 Visualizations
- **Histograms**: To study feature distribution
- **Correlation Heatmap**: To detect feature relationships
- **Scatter Plot & Pairplot**: To analyze relationships between features and target labels

### 3. 🧬 Feature Selection
- Dropped: `rainfall`, `ph` (low variance & correlation)
- Retained:
  - `N`, `P`, `K`, `temperature`, `humidity`

### 4. 🤖 Model Development

#### Models Tested:
- Logistic Regression (Accuracy: 91%)
- Decision Tree (Accuracy: 94%)
- **Naive Bayes** (✅ Selected - Accuracy: **95%**)

#### Why Naive Bayes?
- Excellent for **multi-class classification**
- Simple, interpretable, and fast
- High precision, recall, and F1-score
- Robust to overfitting

### 5. 🧪 Evaluation Metrics
- **Confusion Matrix**
- **Accuracy**
- **Precision, Recall, F1-Score** (weighted)

---

## 🌱 Interactive Crop Prediction

An interactive system allows users to enter values for environmental features to get a crop recommendation.

```python
# Sample code snippet:
user_input = []
for feature in features:
    value = input(f"{feature}: ")
    if value:
        user_input.append(float(value))
    else:
        user_input.append(feature_means[feature])

predicted_crop = classifier_tree.predict(np.array(user_input).reshape(1, -1))
