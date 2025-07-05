# Retail-Profitability-Analysis-and-Forecasting

> This repository provides code and documentation for analyzing and forecasting retail profitability using transaction data. You’ll identify key profit drivers, visualize relationships, and build a predictive model for future performance.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Dataset](#dataset)
3. [Environment Setup](#environment-setup)
4. [Analysis Workflow](#analysis-workflow)
5. [Key Findings](#key-findings)
6. [Forecasting Approach](#forecasting-approach)
7. [Business Implications](#business-implications)
8. [How to Run](#how-to-run)
9. [Dependencies](#dependencies)
10. [Authors](#authors)
11. [License](#license)

---

## Project Overview

In this project, we:

* Clean and preprocess transaction data
* Subset relevant features (Sales, Quantity, Discount, Category, etc.)
* Perform exploratory data analysis and visualizations
* Compute a correlation heatmap to assess linear relationships
* Develop a simple regression-based forecasting model
* Derive business insights and recommendations

## Dataset

The dataset contains anonymized retail transactions with the following columns:

| Column   | Description                                               |
| -------- | --------------------------------------------------------- |
| Order ID | Unique identifier for each transaction                    |
| Product  | Item sold                                                 |
| Category | Product category (Furniture, Office Supplies, Technology) |
| Sales    | Revenue per transaction                                   |
| Quantity | Units sold                                                |
| Discount | Discount rate applied                                     |
| Profit   | Profit per transaction                                    |

> **Note:** Negative profit values (losses) were removed before analysis.

## Environment Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/retail-profit-forecast.git
   cd retail-profit-forecast
   ```

2. **Create a virtual environment (optional)**

   ```bash
   python -m venv venv
   source venv/bin/activate   # macOS/Linux
   venv\\Scripts\\activate  # Windows
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

## Analysis Workflow

1. **Data Cleaning**: Remove negative profits and standardize formats.
2. **Subsetting**: Select `Sales`, `Quantity`, `Discount`, `Category`, and `Profit`.
3. **Aggregation**: Group by `Category` to compute total sales, quantity, and profit.
4. **Visualization**: Create bar charts for distributions and a heatmap for correlations.
5. **Modeling**: Fit a linear regression of Profit on Sales and Discount.
6. **Forecasting**: Use regression coefficients to project future profit given sales and discount scenarios.

## Key Findings

* **Sales** is the strongest driver of profit (Profit ↔ Sales correlation ≈ 0.97).
* **Quantity** has a positive but weaker relationship with profit.
* **Discount** negatively impacts profit margins.
* Raw category codes show minimal linear effect—recommend segment-specific modeling.

## Forecasting Approach

We built a regression model:

```text
Profit_t = α + β₁·Sales_t + β₂·Discount_t + ε_t
```

* **β₁** positive and significant → sales growth directly boosts profit.
* **β₂** negative → deeper discounts reduce profits.

> **Reliability:** Extend the model with category dummies, validate out-of-sample (R² ≥ 0.8, MAPE < 10%), and perform residual diagnostics before deployment.

## Business Implications

1. **Focus on revenue quality**: Increase average order value rather than just unit counts.
2. **Optimize discounts**: Implement targeted promotions to protect margins.
3. **Segment forecasting**: Model profit by product line for more accurate planning.
4. **Scenario analysis**: Evaluate trade-offs between sales growth and discount depth.

## How to Run

* **Launch Jupyter Notebook**

  ```bash
  jupyter notebook "Retail Profitability Analysis and Forecasting.ipynb"
  ```

* **Convert to HTML**

  ```bash
  jupyter nbconvert --to html "Retail Profitability Analysis and Forecasting.ipynb"
  ```

## Dependencies

* Python 3.8+
* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn

Install all dependencies with:

```bash
pip install -r requirements.txt
```
