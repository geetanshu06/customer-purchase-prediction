# Customer Purchase Prediction  
## Capstone Project – Initial Report & Exploratory Data Analysis (EDA)

---

## 📌 Research Question

Can a customer’s historical purchase behavior be used to predict whether they will make a purchase within the next 30 days?

---

## 📊 Dataset

This project uses the **Online Retail Dataset** from the UCI Machine Learning Repository.

The dataset contains transactional e-commerce data including:

- Invoice number  
- Product description  
- Quantity purchased  
- Unit price  
- Customer ID  
- Transaction timestamp  

For reproducibility, the dataset was downloaded and stored locally in the `/data` directory.

---

## 🧹 Data Cleaning & Preparation

The following preprocessing steps were performed:

- Removed rows with missing Customer IDs  
- Removed duplicate transactions  
- Removed negative quantities and return transactions  
- Converted date columns to proper datetime format  
- Created a new feature: **TotalPrice = Quantity × UnitPrice**  
- Aggregated transaction data at the customer level  
- Engineered a binary target variable:
  - `1` → Customer purchased within the last 30 days  
  - `0` → Customer did not purchase within the last 30 days  

Outlier analysis was conducted using boxplots and IQR-based inspection.

---

## 📈 Exploratory Data Analysis (EDA)

EDA was conducted to understand customer purchasing patterns, identify skewness and outliers, examine feature relationships, and evaluate class balance before modeling.

Key visualizations include:

- Transactions vs Total Spending (scatter plot)  
- Distribution of Total Customer Spending (log-scaled histogram)  
- Target variable distribution  
- Correlation heatmap  
- Outlier boxplots  

### Key Insights

- Total customer spending is highly right-skewed, with a small number of high-value customers.
- Customers with higher transaction frequency tend to generate higher total revenue.
- Transaction count and total spending show strong positive correlation.
- The target variable is relatively balanced, making accuracy an appropriate primary metric.

A logarithmic scale was applied to the spending distribution to properly visualize wide-ranging spending magnitudes.

---

## 🤖 Modeling Approach

This project follows a structured machine learning workflow starting from a baseline model and progressively improving performance.

### Baseline Model
A **Dummy Classifier** was first used to establish a baseline. It predicts the majority class and helps validate whether the problem is meaningful.

### Initial Model
A **Logistic Regression** model was implemented as the first real model due to its simplicity and interpretability.

### Features Used
- Total Transactions  
- Total Quantity  
- Total Spending  

### Problem Framing

The task is structured as a **binary classification problem**:

Predict whether a customer will make a purchase within the next 30 days based on historical purchasing behavior.

### Features Used

- Total Transactions  
- Total Quantity  
- Total Spending  

---

## 📊 Model Evaluation

> **Note:** Model performance metrics may vary slightly due to random train-test splits.

### Evaluation Metric

**Accuracy** was selected as the primary evaluation metric because:

- The target classes are relatively balanced.
- Accuracy provides a clear measure of overall predictive correctness.

Additional metrics including **Precision, Recall, and F1-score** were computed to ensure balanced performance across both classes.

### Interpretation

Accuracy represents the proportion of customers correctly classified as either likely or not likely to purchase in the next 30 days.

The confusion matrix was analyzed to understand false positives and false negatives and assess classification performance across both classes.

---
## ⚖️ Handling Class Imbalance

Although the dataset is moderately balanced (~66% vs 34%), multiple techniques were applied to improve minority class prediction:
- **Class Weights (Balanced Logistic Regression)**  
  Adjusted model to give higher importance to minority class

- **SMOTE (Synthetic Minority Oversampling Technique)**  
  Generated synthetic samples to balance the dataset

These approaches significantly improved recall and F1-score.
## 📊 Model Comparison

Multiple models were evaluated to compare performance:

| Model                | F1 Score |
|---------------------|----------|
| Dummy Classifier    | 0.00     |
| Logistic Regression | 0.45     |
| Balanced Logistic   | 0.54     |
| SMOTE Logistic      | 0.53     |
| Tuned Logistic      | 0.45     |
| Random Forest       | 0.45     |
| Gradient Boosting   | 0.47     |


## ⚙️ Hyperparameter Tuning

Grid Search was used to optimize Logistic Regression parameters:

- Regularization strength (`C`)
- Solver type

However, tuning did not significantly improve performance, indicating that the model is already well-regularized for this dataset.

### Key Takeaways

- Dummy classifier confirms the problem is non-trivial  
- Logistic Regression performs well as a baseline  
- Handling class imbalance significantly improves performance  
- Tree-based models did not outperform linear models in this case  

## 🎯 Threshold Tuning

Instead of using the default probability threshold (0.5), multiple thresholds were tested to optimize F1-score.

| Threshold | F1 Score |
|----------|----------|
| 0.2      | 0.48     |
| 0.3      | 0.49     |
| 0.4      | 0.56 ⭐   |
| 0.5      | 0.53     |
| 0.6      | 0.46     |

### Insight

- Optimal threshold = **0.4**
- Lowering threshold improved recall and overall F1-score
- This is critical for business use cases where missing potential customers is costly


## 🚀 Final Model

The final selected model is:

👉 **Balanced Logistic Regression + Threshold = 0.4**

### Why this model?

- Handles class imbalance effectively  
- Provides best F1-score (~0.56)  
- Improves recall (captures more potential customers)  
- Simple, interpretable, and production-friendly  



## 💼 Business Relevance

Predicting short-term customer purchase behavior enables businesses to:

- Target high-probability customers with promotions  
- Improve marketing efficiency  
- Increase customer retention  
- Support short-term revenue forecasting  

Threshold tuning further enhances business impact by prioritizing high-recall predictions, ensuring more potential customers are targeted.

---

## 📁 Repository Structure

<pre><code>customer-purchase-prediction/  
│  
├── data/  
│   └── Online_Retail.xlsx  
│  
├── notebooks/  
│   └── customer_purchase_prediction.ipynb  
│  
├── images/  
│   ├── transactions_vs_spending.png  
│   ├── spending_distribution.png  
│   ├── target_balance.png  
│   ├── correlation_heatmap.png  
│   ├── outlier_boxplot.png  
│   └── confusion_matrix.png  
│  
└── README.md  
</code></pre>
---

🔗 Access the Notebook

You can view or run the full analysis here:  
➡️ notebooks/customer_purchase_prediction.ipynb


⚙️ How to Run This Project

🔹 Option 1: Google Colab
1. Open the notebook directly from GitHub in Colab:
https://colab.research.google.com/github/geetanshu06/customer-purchase-prediction/blob/main/notebook/customer_purchase_prediction.ipynb
2. Run all cells — the notebook automatically reads from the `data/` folder and saves plots to `images/`.



## 🧑‍💻 Author

<pre><code>Name: Geetanshu Aggarwal  
Project: Customer Purchase Prediction  
Environment: Google Colab + GitHub  
Date: Feb 2026  
</code></pre>