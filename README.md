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

## 🤖 Baseline Model

A **Logistic Regression** model was implemented as the baseline classification model.

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

## 💼 Business Relevance

Predicting short-term customer purchase behavior enables businesses to:

- Target high-probability customers with promotions  
- Improve marketing efficiency  
- Increase customer retention  
- Support short-term revenue forecasting  

Even a baseline predictive model provides valuable insights for data-driven decision-making.

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

## 🧑‍💻 Author

<pre><code>Name: Geetanshu Aggarwal  
Project: Customer Purchase Prediction  
Environment: Google Colab + GitHub  
Date: Feb 2026  
</code></pre>