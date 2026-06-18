 # Traffic Volume Prediction System Using Machine Learning

An end-to-end Machine Learning regression project developed during my internship at **ITSOLERA Pvt. Ltd.** This system forecasts hourly urban traffic volume using historical traffic, time-based features, and environmental data to help optimize traffic management and reduce congestion.

##  Project Overview
Urban traffic congestion significantly impacts transportation efficiency and economic productivity. This project implements and evaluates multiple regression models—including Linear Regression, Support Vector Regression (SVR), Decision Trees, Random Forest, and XGBoost—to accurately predict traffic volume using features like weather conditions and holiday schedules.

##  Tools and Technologies
* **Programming Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, XGBoost
* **Development Environment:** VS Code, Jupyter Notebook
* **Model Serialization:** Pickle

---

## 📊 Dataset Description
The system utilizes the **Metro Interstate Traffic Volume dataset** containing **48,204 entries** and 9 initial features:
* `holiday`: Categorical indicator of national holidays (handled missing data)
* `temp`: Temperature in Kelvin
* `rain_1h`: Rain amount in mm that occurred in the hour
* `snow_1h`: Snow amount in mm that occurred in the hour
* `clouds_all`: Percentage of cloud cover
* `weather_main`: Short textual description of the current weather
* `weather_description`: Detailed textual description of the weather (dropped during preprocessing)
* `date_time`: Date and hour of data collection
* `traffic_volume` (**Target Variable**): Hourly traffic volume

---

##  Methodology & Pipeline

### 1. Data Preprocessing & Cleaning
* Addressed missing values inside the `holiday` column.
* Dropped unnecessary categorical columns like `weather_description`.
* Applied `LabelEncoder` to encode categorical text features into numerical values.
* Split the dataset into an **80% training set** and a **20% testing set** (Train shape: `38,563`, Test shape: `9,641`).

### 2. Feature Engineering
* Extracted time components (`hour`, `day`, `month`, `day_of_week`) from the `date_time` column.
* Generated a custom `is_weekend` binary indicator feature to capture weekend traffic trends.

### 3. Model Development & Evaluation
Five distinct machine learning regression models were trained and compared using metrics like $R^2$ Score, Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE).

---

## Performance & Results

Ensemble-based techniques significantly outperformed traditional linear models. While the standalone Decision Tree heavily overfit the training data, **Random Forest** achieved the best overall balance and predictive accuracy.

| Model Name | Training $R^2$ | Test $R^2$ | MAE | RMSE | Performance Status |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Linear Regression** | 0.187 | 0.185 | High | High | Underfit |
| **SVR** | 0.006 | 0.005 | Very High | Very High | Poor |
| **Decision Tree** | 1.000 | 0.941 | Low | Low | Overfit |
| **Random Forest** | **0.995** | **0.965** | **208.94** | **371.13** | **Best Model** |
| **XGBoost** | 0.0976 | 0.958 | Low | Low | Good |
Prediction.git)
cd Traffic-Volume-Prediction
