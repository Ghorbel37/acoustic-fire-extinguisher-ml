# 🔥 Fire Extinguisher Prediction using Sound Waves

A machine learning project that predicts whether a fire can be extinguished using sound waves based on various parameters such as fuel type, distance, frequency, decibel level, and airflow.

## 📋 Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Features](#features)
- [Models](#models)
- [Results](#results)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)

## 🔍 Overview

This project analyzes the effect of sound waves on extinguishing flames from different fuels. The experiments were conducted using a sound wave fire extinguishing system that includes powerful subwoofers, amplifiers, an anemometer for measuring airflow, a decibel meter for sound intensity, and an infrared thermometer for temperature measurement.

The goal is to use machine learning algorithms to establish the best possible classifications for predicting fire extinction based on acoustic parameters.

## 📊 Dataset

**Acoustic Extinguisher Fire Dataset**

**Dataset Source**: [Kaggle - Acoustic Extinguisher Fire Dataset](https://www.kaggle.com/datasets/muratkokludataset/acoustic-extinguisher-fire-dataset)

- **Total observations**: 17,442 tests
- **Features**: 6 attributes
- **Target variable**: STATUS/CLASS (0 = not extinguished, 1 = extinguished)
- **Class distribution**: Nearly balanced (8,759 non-extinct, 8,683 extinct)

### Dataset Features

| Feature | Description | Values/Range |
|---------|-------------|--------------|
| **SIZE** | Container size (cm) or LPG throttle setting | 7, 12, 14, 16, 20 cm (liquids); 0=half, 1=full (LPG) |
| **FUEL** | Type of fuel used | Gasoline, Kerosene, Thinner, LPG |
| **DISTANCE** | Distance from sound source (cm) | 10 - 190 cm |
| **DESIBEL** | Sound intensity (dB) | 72 - 113 dB |
| **AIRFLOW** | Air flow generated (m/s) | 0 - 17 m/s |
| **FREQUENCY** | Sound frequency (Hz) | 1 - 75 Hz (54 different frequencies) |

## 🎯 Features

### 1. Comprehensive Model Comparison
The project evaluates 9 different machine learning models:
- Naive Bayes Classifier
- K-Nearest Neighbors (KNN)
- Decision Tree Classifier
- Random Forest Classifier
- Gradient Boosting Classifier
- XGBoost (Extreme Gradient Boosting)
- Perceptron
- Logistic Regression
- Support Vector Machine (SVM)
- K-Means (unsupervised)

### 2. Interactive GUI Application
A user-friendly Tkinter interface that allows users to:
- Input fire parameters (fuel type, size, distance, etc.)
- Get real-time predictions on fire extinction probability
- Visualize results instantly

## 📈 Models

### Model Performance Comparison

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| **XGBoost** | **97.76%** | **97.77%** | **97.76%** | **97.76%** |
| Decision Tree | 96.36% | 96.36% | 96.36% | 96.36% |
| Random Forest | 95.79% | 95.79% | 95.79% | 95.79% |
| Gradient Boosting | 94.44% | 94.45% | 94.44% | 94.44% |
| SVM | 93.35% | 93.35% | 93.35% | 93.35% |
| KNN | 92.95% | 92.95% | 92.95% | 92.95% |
| Logistic Regression | 89.28% | 89.29% | 89.28% | 89.28% |
| Perceptron | 88.82% | 88.88% | 88.82% | 88.81% |
| Naive Bayes | 86.93% | 87.08% | 86.93% | 86.90% |

### Hyperparameter Optimization
- **KNN**: GridSearchCV used to find optimal k=7 neighbors
- **Decision Tree**: Best criterion = entropy
- **Random Forest**: Optimal n_estimators=150, criterion=entropy
- **SVM**: Best parameters C=1000.0, kernel=rbf

### Feature Importance (XGBoost)
The most important features for prediction according to XGBoost analysis are included in the first notebook with visualizations.

## 🎨 Results

### Key Findings
1. **Best Model**: XGBoost achieves the highest accuracy of **97.76%**
2. **Top 3 Models**: XGBoost, Decision Tree, and Random Forest all exceed 95% accuracy
3. **Class Balance**: Dataset is well-balanced, avoiding bias issues
4. **No Missing Data**: Complete dataset with no null values or duplicates

### Visualizations
The project includes:
- Confusion matrices for all models
- Feature importance plots
- Performance comparison charts
- PCA visualizations for K-Means clustering (2D and 3D)
- Count plots and correlation heatmaps

## 🚀 Installation

### Prerequisites
```bash
Python 3.7+
```

### Required Libraries
```bash
pip install -r requirements.txt
```

### For Tkinter GUI (usually pre-installed with Python)
```bash
# On Linux (if needed)
sudo apt-get install python3-tk

# On macOS (usually included)
brew install python-tk
```

## 💻 Usage

### 1. Model Training and Comparison
Run the comprehensive analysis notebook:
```bash
jupyter notebook Fire_Extinguisher_Predictor_GridSearch.ipynb
```

This notebook will:
- Load and explore the dataset
- Preprocess the data
- Train multiple models with hyperparameter tuning
- Compare model performances
- Save the best model as `pipeline.pkl`

### 2. GUI Application
Run the Tkinter application notebook:
```bash
jupyter notebook Fire_Extinguisher_Predictor_With_Tkinter.ipynb
```

Or execute the final cell to launch the interactive prediction interface where you can:
1. Select fuel type (Gasoline, Kerosene, Thinner, or LPG)
2. Enter container size or LPG throttle setting
3. Input distance, decibel level, airflow, and frequency
4. Click "Predict" to see if the fire will be extinguished

### 3. Using the Saved Model
```python
import pickle
import pandas as pd

# Load the trained model
with open('pipeline.pkl', 'rb') as f:
    model = pickle.load(f)

# Make predictions
# Format: [SIZE, FUEL, DISTANCE, DESIBEL, AIRFLOW, FREQUENCY]
sample_data = [[7, 0, 50, 95, 5.5, 30]]
prediction = model.predict(sample_data)

print("Fire will be extinguished:", prediction[0] == 1)
```

## 📁 Project Structure

```
.
├── Fire_Extinguisher_Predictor_GridSearch.ipynb    # Comprehensive model comparison
├── Fire_Extinguisher_Predictor_With_Tkinter.ipynb  # Pipeline + GUI application
├── pipeline.pkl                                      # Saved trained model
├── Acoustic_Extinguisher_Fire_Dataset.xlsx          # Dataset file
├── .gitignore                                        # Git ignore file
└── README.md                                         # This file
```

## 🛠️ Technologies Used

- **Python 3.x**: Core programming language
- **Pandas & NumPy**: Data manipulation and numerical operations
- **Scikit-learn**: Machine learning models and preprocessing
- **XGBoost**: Gradient boosting framework
- **Matplotlib & Seaborn**: Data visualization
- **Tkinter**: GUI development
- **Jupyter Notebook**: Interactive development environment
- **Pickle**: Model serialization

## 📝 Methodology

### 1. Data Preprocessing
- Encoding categorical variable (FUEL): Gasoline=0, Thinner=1, Kerosene=2, LPG=3
- Mapping SIZE values to actual dimensions in cm
- Train-test split: 80% training, 20% testing

### 2. Model Training
- GridSearchCV for hyperparameter optimization
- 5-fold cross-validation
- Multiple evaluation metrics (Accuracy, Precision, Recall, F1-Score)

### 3. Model Evaluation
- Confusion matrices for all models
- Performance comparison using multiple metrics
- Feature importance analysis

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file.

## 🤝 Contributing

This is an academic project. If you have suggestions or find issues, feel free to open an issue or submit a pull request.

## 📧 Contact

For questions or feedback regarding this project, please contact me.

---

**Note**: Make sure the dataset file `Acoustic_Extinguisher_Fire_Dataset.xlsx` or `Acoustic_Extinguisher_Fire_Dataset.csv` is in the same directory as the notebooks before running them.