[README.md](https://github.com/user-attachments/files/29393243/README.md)
# 📊 Customer Churn & LTV Predictor

> A machine learning web app that predicts whether a customer will churn — and how much they'll spend in their lifetime.  
> Built end-to-end in 4 days as part of my public ML learning journey.

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![Streamlit](https://img.shields.io/badge/Streamlit-Deployed-red?style=flat-square&logo=streamlit)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?style=flat-square&logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Live-brightgreen?style=flat-square)

---

## 🚀 What It Does

Enter a customer's details into the web app and get back two AI-powered predictions instantly:

| Output | Example |
|--------|---------|
| 💰 Predicted Lifetime Value (LTV) | `$762.98` |
| 🟢 Churn Risk Status | `Satisfied → Will Renew` |
| 🟡 Neutral Risk | `On the fence → Send a discount!` |
| 🔴 High Risk | `Unsatisfied → Will Churn` |

---

## 🖥️ Live Demo

![App Screenshot](screenshot.png)

> The app takes customer inputs, runs them through two trained ML models, and returns real predictions with business-ready recommendations.

---

## 📌 Input Features

| Feature | Type | Description |
|--------|------|-------------|
| Age | Numeric | Customer age |
| Gender | Categorical | Male / Female |
| City | Categorical | New York, LA, Chicago, Miami, SF, Houston |
| Membership Tier | Categorical | Bronze / Silver / Gold |
| Items Purchased | Numeric | Total items bought |
| Average Rating | Numeric (1.0–5.0) | Customer satisfaction rating |
| Days Since Last Purchase | Numeric | Recency of activity |
| Discount Applied | Categorical | Yes / No |

---

## 🤖 Models Used

### 1. Linear Regression — LTV Prediction
- Predicts the **continuous dollar value** a customer will spend over their lifetime
- Output is inverse-transformed from scaled space back to real dollars

### 2. Logistic Regression — Churn Classification
- Predicts one of **3 classes**: Satisfied (2), Neutral (1), Unsatisfied (0)
- Uses the LTV prediction as one of its input features — the two models work together

---

## 🔧 Full ML Pipeline

```
Raw Data
   │
   ▼
1. EDA (Exploratory Data Analysis)
   └── Understand distributions, correlations, outliers
   │
   ▼
2. Data Cleaning
   └── Handle missing values, fix dtypes, remove duplicates
   │
   ▼
3. Preprocessing & Feature Engineering
   └── Label Encoding (Gender, Membership, Discount)
   └── One-Hot Encoding (City → 6 binary columns)
   │
   ▼
4. Feature Scaling
   └── StandardScaler on: Age, Total Spend, Items Purchased,
       Average Rating, Days Since Last Purchase
   │
   ▼
5. Model Training
   └── Linear Regression  → predicts LTV
   └── Logistic Regression → predicts Churn class
   │
   ▼
6. Model Evaluation
   └── Regression: R² Score, MAE
   └── Classification: Accuracy, Precision, Recall
   │
   ▼
7. Deployment
   └── Streamlit web app with live predictions
```

---

## 📚 Algorithms I Studied (Day 4 of ML Journey)

| Algorithm | Type | What it does |
|-----------|------|-------------|
| **Logistic Regression** | Classification | Predicts Yes/No using a sigmoid curve |
| **Naive Bayes** | Classification | Probability-based, assumes feature independence |
| **KNN** | Classification | Classifies by finding K nearest data points |
| **Decision Tree** | Classification | IF-THEN rule-based splitting |
| **SVM** | Classification | Finds the sharpest boundary between classes |
| **Linear Regression** | Regression | Predicts a continuous number |

---

## 🗂️ Project Structure

```
customer-churn-ltv-predictor/
│
├── app.py                  # Streamlit web app (main file)
├── log_model.pkl           # Trained Logistic Regression model
├── lin_model.pkl           # Trained Linear Regression model
├── scaler.pkl              # Fitted StandardScaler
├── train_models.ipynb      # Full training notebook (EDA → Model)
├── requirements.txt        # Dependencies
└── README.md               # You are here
```

---

## ⚙️ How to Run Locally

```bash
# 1. Clone the repo
git clone https://github.com/yourusername/customer-churn-ltv-predictor.git
cd customer-churn-ltv-predictor

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the app
streamlit run app.py
```

---

## 📦 Requirements

```
streamlit
scikit-learn
pandas
numpy
joblib
```

---

## 💡 Key Learning — X_train vs Y_train

The biggest confusion I had starting out:

```python
X_train = df[['Age', 'Gender', 'Items Purchased', ...]]  # Features — what the model LEARNS FROM
y_train = df['Satisfaction Level']                        # Target  — what the model PREDICTS
```

Once this clicked, the entire ML pipeline made sense.

---

## 📈 What's Next

- [ ] Add KNN, Naive Bayes, SVM, and Decision Tree models to the app
- [ ] Build a full 6-model "Customer Risk Profile" dashboard
- [ ] Add model accuracy metrics to the UI
- [ ] Deploy on Streamlit Cloud with public URL

---

