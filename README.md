# CS435/471 – Linear Regression on Student Performance

> A minimal, reproducible regression mini‑project for CS435/471 that predicts students’ final scores using **Linear Regression** on the *Student Performance* dataset. Built to match course guidelines: simple processing, one core model, clear metrics, and clean code in a single notebook.

## 📁 Project Files
- `StudentPerformance_LinearRegression (2) (1).ipynb` – the complete Colab‑friendly notebook with code, comments, and section headers.

---

## 🎯 Objective
- Train a **Linear Regression** model to predict the target `total_score`.
- Keep the pipeline simple and transparent (per assignment requirements).
- Report clear validation and test metrics.

---

## 📊 Dataset
- **Source:** Kaggle – *Student Performance Dataset*  
  https://www.kaggle.com/datasets/nabeelqureshitiii/student-performance-dataset
- **Expected target column:** `total_score`
- **Assumption:** All feature columns are either numeric or will be one‑hot encoded by the notebook.

> If your CSV has different column names, update `TARGET_COL` inside the notebook.

---

## 🧹 Data Preparation (as implemented in the notebook)
1. Upload CSV in Colab using `google.colab.files.upload()`.
2. Median imputation for **numeric** columns.
3. One‑hot encoding for **non‑numeric** columns (`pd.get_dummies(..., drop_first=True)`).
4. Remove exact **duplicate** rows.
5. Define features/target:  
   ```python
   TARGET_COL = "total_score"
   X = df.drop(columns=[TARGET_COL])
   y = df[TARGET_COL]
   ```

---

## 🔀 Train/Validation/Test Split
- Hold‑out strategy: **60% train / 20% validation / 20% test** via two steps:
  ```python
  X_train, X_temp, y_train, y_temp = train_test_split(X, y, test_size=0.4, random_state=42)
  X_val, X_test, y_val, y_test   = train_test_split(X_temp, y_temp, test_size=0.5, random_state=42)
  ```

---

## 🧠 Model
- **Algorithm:** `sklearn.linear_model.LinearRegression`
- **Why Linear Regression?** Matches course requirement to use a simple, interpretable baseline and report coefficients for feature influence.

---

## 📈 Evaluation
The notebook prints metrics for both **validation** and **test** sets:
- **MAE** – Mean Absolute Error
- **MSE** – Mean Squared Error
- **RMSE** – Root Mean Squared Error
- **R²** – Coefficient of Determination

It also includes:
- A scatter plot of **Actual vs Predicted** on the test set.
- A coefficient table (sorted) to highlight most influential features.

> Exact numbers depend on your CSV and preprocessing outcome.

---

## ▶️ How to Run (Google Colab)
1. Open the notebook in Colab.
2. Run section **“Import Required Libraries”**.
3. In section **“Upload Dataset”**, a file picker appears. Choose your CSV (e.g., `student_performance.csv`).  
   The notebook will confirm with: `Dataset loaded successfully! Shape: (...)`.
4. Run all cells in order.
5. Review printed metrics, the coefficient table, and the final **Actual vs Predicted** plot.

---

## ▶️ How to Run Locally (Optional)
1. Create and activate a virtual environment (Python 3.9+ recommended).
2. Install requirements:
   ```bash
   pip install -U pandas numpy matplotlib scikit-learn
   ```
3. Replace the Colab upload cell with:
   ```python
   import pandas as pd
   df = pd.read_csv("student_performance.csv")
   ```
4. Run cells sequentially in Jupyter Notebook/Lab or VS Code.

---

## 📑 Notebook Outline
- **1) Import Required Libraries**  
- **2) Upload Dataset (Colab)**  
- **3) Basic Preprocessing (impute/encode/drop duplicates)**  
- **4) Define Target & Features**  
- **5) Train/Validation/Test Split (60/20/20)**  
- **6) Train Linear Regression**  
- **7) Validation Metrics**  
- **8) Final Model (Train+Val) & Test Metrics**  
- **9) Coefficients & Top Features**  
- **10) Visualization — Actual vs Predicted**

---

## ✅ Deliverables Checklist
- [x] Uses a **public dataset** (linked above).
- [x] **Linear Regression** only (no scaling pipeline required).
- [x] **60/20/20** split with a separate test set.
- [x] Clear **metrics** and **plot**.
- [x] Coefficient‑based **feature influence**.

---

## 👩‍🏫 Team
- Joud Fahad Alharbi — 431201479  
- **Aleen Alqwaifel — 431201500**  
- Bushra Ali Alhusyani — 421201987  
- Reema Alfehaid — 431201292  
- Kadi Alaowimer — 411214150

---

## 📜 License
This project is for educational use in CS435/471. If you plan to reuse or publish beyond coursework, please include proper credit and verify the dataset’s original license on Kaggle.
