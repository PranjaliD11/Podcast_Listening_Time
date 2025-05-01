#  Podcast Listening Time Prediction

This project focuses on predicting podcast **listening time (in minutes)** using genre and other categorical metadata. It explores multiple preprocessing techniques and machine learning models to minimize RMSE (Root Mean Squared Error) on unseen test data.

---

## Dataset Overview

- **Train Data**: 750,000 rows  
- **Test Data**: 250,000 rows  
- **Target Variable**: `episode_listening_time` (in minutes)  
- Features include episode genre, duration, and other categorical information.

---

##  Exploratory Data Analysis (EDA)

Before modeling, extensive EDA was conducted:
- Identified missing values in `episode_length_minutes`
- Analyzed distributions across genres and listening patterns
- Examined correlations and categorical feature distributions

---

## Data Cleaning & Imputation

- Instead of using a global mean for missing `episode_length_minutes`, the **median value per genre** was used.
- This genre-wise imputation significantly improved RMSE compared to a general mean imputation.

---

## Feature Engineering & Encoding

Different encoding strategies were tested for categorical features:
- **Label Encoding**
- **One-Hot Encoding**
- **Mapping techniques**

---

## 🤖 Model Experiments

Three primary models were evaluated:

### CatBoost (without encoding)
- Used raw categorical features, leveraging CatBoost's inbuilt handling.
- **Result**: Poor generalization and high RMSE — model underperformed on test data.

### CatBoost (with encoded features)
- Trained on pre-encoded categorical data.
- **Result**: Best RMSE on train set, but overfitted and failed to generalize on test data.
- **Test RMSE**: `20.25`

### XGBoost 
- Performed better than CatBoost after tuning.
- **Test RMSE**: `20.200`

### LightGBM
- Initial test RMSE: `20.20998`

---

##  Model Tuning & Improvements

Applied the following techniques to improve performance:
- **Cross-validation**
- **Hyperparameter tuning**
- **Capping outliers** in episode listening time

>  **Final RMSE on unseen data: `13.07`**

---

## 📌 Key Takeaways

- Genre-wise median imputation significantly boosted model accuracy.
- Encoding categorical features for CatBoost led to better results than using raw categories.
- XGBoost outperformed both CatBoost and LightGBM after tuning and handling outliers.




