# Hotel-Daily-Room-Rate-Booking-Cancellation-Prediction

![Harvard_University_logo svg](https://github.com/user-attachments/assets/d105e69f-937f-4ef6-92ca-9915220d0660)

![Harvard-Extension-School](https://github.com/user-attachments/assets/b0f3123f-4f08-45a3-9639-f605e511406e)

## **STAT E-109	Introduction to Statistical Modeling**

## Authors: **Dai-Phuong Ngo (Liam)**, **Brandon Henley**

## Professor: **Bharatendra Rai, PhD**

Professor of Decision and Information Sciences, Charlton College of Business, University of Massachusetts Dartmouth

Here’s a structured `README.md` outline for your GitHub project **Hotel Daily Room Rate & Booking Cancellation Prediction**, with tailored content for each section based on your PDF:

---

## Project Overview

Predicting daily hotel room rates (ADR) and booking cancellations (CNC) is crucial for revenue optimization in the hospitality industry. This project applies advanced regression and classification models—including linear regression, ensemble methods, and neural networks—on real-world hotel booking data from Kaggle to deliver actionable insights for hotel revenue managers.

---

## Objectives

* **ADR Prediction**: Forecast daily room rates using features such as season, customer type, and booking behavior.
* **Cancellation Forecasting**: Predict the probability of a booking being canceled based on lead time, past behavior, and special requests.
* **Model Comparison**: Evaluate traditional and modern ML models (e.g., LinR, XGBoost, Neural Networks) to identify the best performers.
* **Revenue Strategy Insight**: Inform pricing strategies and overbooking policies to maximize profit and reduce cancellations.

---

## Dataset

* **Source**: [Hotel Booking Demand dataset on Kaggle](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand)
* **Variables**: Lead time, arrival dates, guest counts, room type, market segment, country, booking changes, special requests, etc.
* **Target Variables**:

  * `adr`: Average Daily Rate (continuous)
  * `is_canceled`: Booking canceled (binary)

---

## Methodology

### Data Preprocessing

* Removed invalid records (ADR ≤ 0, lead time ≤ 0, ADR > \$500)
* Handled missing values using mode imputation
* Engineered features:

  * Booking seasons (Winter, Spring, Summer, Fall)
  * Total room nights and average length of stay (ALOS)
  * Transformed categorical features into binary indicators

### Feature Engineering

* Aggregated records to better reflect room usage per night
* Introduced derived metrics such as `rooms_sold` and `ALOS`
* Created binary flags for channel type, country origin, and seasons

### Model Development

| Task               | Models Used                                                 | Evaluation Metrics                   |
| ------------------ | ----------------------------------------------------------- | ------------------------------------ |
| ADR Regression     | Linear Regression, Random Forest, XGBoost, Neural Network   | R², RMSE                             |
| CNC Classification | Logistic Regression, Random Forest, XGBoost, Neural Network | Accuracy, Precision, Recall, F1, AUC |

* Applied 5-fold cross-validation with grid search for RF and XGBoost
* Neural Network designed with dual-heads: regression and classification

---

## Results

### Average Daily Rate (ADR) Prediction

* **Best Model**: Neural Network and XGBoost Regressor (lowest RMSE)
* **Key Features**: `checkin_season_summer`, room types, number of guests

### Cancellation Prediction

* **Best Model**: XGBoost Classifier (highest Recall and AUC)
* **Key Features**: `deposit_type_non_refundable`, `previous_cancellations`, `customer_type_transient`, `booking_changes`

> The neural network model showed robust performance across both tasks without overfitting, confirming the hypothesis about its superior learning capacity.

---

## Visuals and Diagnostics

* VIF analysis to reduce multicollinearity
* Diagnostic plots for residual normality and homoscedasticity
* Feature importance charts for XGBoost models
* ROC curves for classification comparison

---

## Insights & Recommendations

* **Dynamic Pricing**: Use seasonal and customer-type indicators to adjust ADR.
* **Cancellation Strategy**: Leverage predictors to manage overbooking and deposit policies.
* **Adopt Advanced Models**: Ensemble methods and NNs offer better performance over traditional approaches.

---

## Limitations

* The dataset lacks aggregated financial metrics (RevPAR, TRevPAR) so I developed them through Alteryx based on my domain knowledge of hospitality management.
* Time-based dependencies (e.g., temporal autocorrelation) were not modeled as Time Series Forecasting and Inference were not under my scope for my project.
* Assumed observation independence over time.

---

## Future Work

* Incorporate time series modeling (e.g., LSTM) for temporal dependencies
* Include external signals like competitor pricing or local events
* Optimize model deployment for real-time booking systems

---

## Appendix

* **Model training scripts** (PyTorch, scikit-learn, XGBoost)
* **Hyperparameter tuning** via GridSearchCV
* **Data Dictionary**: Detailed explanation of all dataset features
* **Full VIF and diagnostics plots** (see `/notebooks/eda/`)

---

