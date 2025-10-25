# ✈️ Flight Price Prediction

This project aims to predict flight ticket prices using a machine learning regression model.  
The model is trained on a dataset of flight details and evaluated using a custom metric:  
**1 - RMSLE₁₀ (Root Mean Squared Logarithmic Error, base-10).**

---

## 🛠️ Tech Stack & Libraries

- **Python 3.x**
- **pandas:** For data loading and manipulation  
- **numpy:** For numerical operations and transformations  
- **scikit-learn:** For preprocessing, splitting, and regression models  
- **xgboost:** For gradient boosting-based regression  
- **matplotlib & seaborn:** For visualization  

---

## 🧭 Workflow

### 1. Data Loading & Cleaning
- Load training (`Data_Train.xlsx`) and test (`Test_set.xlsx`) datasets.  
- Handle missing values and drop irrelevant columns.

### 2. Exploratory Data Analysis (EDA)
- Visualized distributions and feature relationships.  
- The target variable **`Price`** was heavily right-skewed.  
- Applied **log transformation (`np.log1p`)** to normalize it.

### 3. Feature Engineering
Converted raw text data into model-ready numerical features:

| Feature | Description |
|----------|--------------|
| `Date_of_Journey`, `Dep_Time`, `Arrival_Time` | Extracted day, month, hour, and minute |
| `Duration` | Converted to total minutes |
| `Total_Stops` | Mapped to integers (e.g., "non-stop" → 0, "1 stop" → 1, etc.) |
| `Airline`, `Source`, `Destination` | One-hot encoded |
| Dropped columns | `Route`, `Additional_Info` |

### 4. Modeling
Two regression models were trained and compared:
1. **Random Forest Regressor**
2. **XGBoost Regressor** (used `early_stopping_rounds` for optimization)

### 5. Evaluation Metric
A **custom metric** was used:
<img width="1095" height="201" alt="Screenshot 2025-10-25 150048" src="https://github.com/user-attachments/assets/985ebf86-fe96-4639-a9f8-37ce1962e0f6" />


✅ **Higher is better** — a score closer to 1 indicates high accuracy.

---

## 📊 Results

- The **XGBoost Regressor** achieved the best performance on validation data.  
- The predictions closely follow the true prices (visualized below).  

><img width="878" height="509" alt="Screenshot 2025-10-25 162401" src="https://github.com/user-attachments/assets/59250e9e-34e5-45c7-a78f-5373dbda1105" />


---

## 🚀 How to Run

```bash
git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name
pip install pandas numpy scikit-learn xgboost matplotlib seaborn openpyxl
python your_script_name.py
