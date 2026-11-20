# CommerceLens:Revenue-Customer-Analytics

**An End-to-End Retail Data Analytics Project | Python · MySQL · Power BI**

An end-to-end data analytics project focused on understanding customer purchasing patterns, revenue distribution, product performance, discount usage, and customer loyalty. This project transforms raw retail shopping data into actionable business insights using Python for data preparation, MySQL for business analysis, and Power BI for interactive visualization.

---

## 1. Business Problem

Retail businesses generate large amounts of customer and purchase data, but raw data alone does not explain customer behavior or support effective business decisions.

A retail company wants to understand:

- Which customer segments contribute the most to revenue?
- Which products and categories perform best?
- Are customers who use discounts spending more?
- How does purchasing behavior differ between subscribers and non-subscribers?
- Which products receive the highest customer ratings?
- How do shipping preferences relate to purchase amounts?
- Which customer groups demonstrate repeat-purchase behavior?

Without structured analysis, it becomes difficult for business teams to identify purchasing trends, evaluate marketing strategies, understand customer loyalty, and make informed product decisions.

### Business Objective

The objective of this project is to analyze customer shopping data and convert it into meaningful business insights that can help a retail business:

1. Understand customer purchasing patterns.
2. Identify high-performing products and categories.
3. Evaluate discount usage and subscription behavior.
4. Analyze customer segments and repeat-purchase patterns.
5. Support data-driven marketing and customer engagement strategies.

---

## 2. Project Solution

To address the business problem, I developed an end-to-end analytics workflow consisting of three major stages:

| Stage | Technology | Responsibility |
|---|---|---|
| Data Preparation | Python, Pandas, NumPy | Data inspection, cleaning, transformation, and feature engineering |
| Business Analysis | MySQL | Business queries, aggregations, customer segmentation, and product analysis |
| Data Visualization | Power BI, DAX | Interactive dashboards, KPIs, and business performance analysis |

**Workflow:**

```text
        Raw Customer Shopping Dataset
                    |
                    v
           Python & Pandas
       Data Cleaning and EDA
                    |
                    v
          Feature Engineering
       Missing Value Treatment
                    |
                    v
               MySQL
        Business Analysis Queries
                    |
                    v
              Power BI
       Interactive Dashboard
                    |
                    v
          Business Insights
        and Recommendations
```

---

## 3. Dataset Overview

The project uses a customer shopping behavior dataset containing **3,900 records and 18 columns**.

The dataset includes customer demographics, product information, purchase amounts, ratings, discounts, subscription status, shipping preferences, and purchase frequency.

### Dataset Attributes

| Column | Description |
|---|---|
| customer_id | Unique customer identifier |
| age | Customer age |
| gender | Customer gender |
| item_purchased | Product purchased |
| category | Product category |
| purchase_amount | Purchase amount in USD |
| location | Customer location |
| size | Purchased product size |
| color | Product color |
| season | Shopping season |
| review_rating | Customer product rating |
| subscription_status | Subscription status |
| shipping_type | Selected shipping method |
| discount_applied | Whether a discount was applied |
| promo_code_used | Whether a promotional code was used |
| previous_purchases | Number of previous purchases |
| payment_method | Payment method |
| frequency_of_purchases | Purchase frequency category |

**Dataset size:** 3,900 rows × 18 columns.

**Missing values:** 37 missing values were identified in the `review_rating` column.

---

## 4. Data Cleaning and Preparation — Python

Python and Pandas were used to inspect, clean, and prepare the dataset for further analysis.

### Key Activities

**1. Data Inspection**
- Loaded the CSV dataset using Pandas.
- Inspected the dataset structure using `df.info()`.
- Analyzed descriptive statistics using `df.describe()`.
- Checked missing values and duplicate records.

**2. Missing Value Treatment**
- Identified 37 missing values in `review_rating`.
- Imputed missing ratings using the median rating of the corresponding product category.

Category-wise median imputation was selected to preserve differences in rating distributions across product categories.

**3. Column Standardization**
- Converted column names into lowercase snake_case.
- Renamed columns for consistency and easier SQL integration.

**4. Feature Engineering**
- Created `age_group` by grouping customers based on age.
- Created `purchase_frequency_days` by mapping purchase frequency categories to approximate day intervals.

**5. Data Consistency Check**
- Checked the relationship between `discount_applied` and `promo_code_used`.
- Removed `promo_code_used` after verifying redundancy.

**6. Database Integration**
- Connected Python to MySQL using SQLAlchemy.
- Loaded the cleaned DataFrame into a MySQL database for business analysis.

---

## 5. Business Analysis — MySQL

MySQL was used to answer business-oriented questions through SQL queries and aggregations.

The analysis focused on revenue performance, customer behavior, product ratings, discounts, subscription patterns, and customer loyalty.

### SQL Concepts Applied

- SELECT, WHERE, ORDER BY, LIMIT
- Aggregate Functions: SUM(), AVG(), COUNT(), MIN(), MAX()
- GROUP BY and HAVING
- CASE WHEN statements
- Subqueries
- Common Table Expressions (CTEs)
- Window Functions

### Business Questions Solved

| # | Business Question | Analytical Objective |
|---|---|---|
| 1 | Revenue by Gender | Compare revenue generated by male and female customers |
| 2 | Discount & Spending Analysis | Identify discount users whose spending is at or above the overall average |
| 3 | Product Rating Analysis | Identify the top 5 products based on average review rating |
| 4 | Shipping Analysis | Compare average purchase amounts for Standard and Express shipping |
| 5 | Subscription Analysis | Compare customer counts, average spending, and revenue between subscribers and non-subscribers |
| 6 | Discount Dependency Analysis | Identify the top 5 products with the highest percentage of discounted purchases |
| 7 | Customer Segmentation | Classify customers into New, Returning, and Loyal segments based on previous purchases |
| 8 | Product Popularity Analysis | Identify the top 3 most purchased products within each category |
| 9 | Repeat Buyer Analysis | Compare subscription status among customers with more than 5 previous purchases |
| 10 | Age Group Revenue Analysis | Compare total revenue across customer age groups |

### Customer Segmentation Logic

Customers were classified using the following project-defined conditions:

| Previous Purchases | Customer Segment |
|---|---|
| 1 | New |
| 2–10 | Returning |
| More than 10 | Loyal |

This segmentation provides a way to compare purchasing behavior across customer groups.

---

## 6. Power BI Dashboard

Power BI was used to transform the analytical results into an interactive dashboard for business users.

The dashboard is organized around executive performance monitoring and detailed customer/product analysis.

### Dashboard — Executive Overview

Key performance indicators:

- Total Revenue
- Purchase Records
- Average Purchase Amount
- Average Review Rating

Visualizations:

- Revenue by Product Category
- Revenue by Gender
- Revenue by Age Group
- Subscription Distribution
- Top 10 Products by Revenue

Interactive slicers:

- Gender
- Category
- Season
- Subscription Status
- Payment Method


## 7. Tools and Technologies

| Technology | Purpose |
|---|---|
| Python | Data analysis and preprocessing |
| Pandas | Data cleaning and manipulation |
| NumPy | Numerical operations |
| Jupyter Notebook | Exploratory analysis and documentation |
| MySQL | Relational database and business queries |
| SQLAlchemy | Python–MySQL integration |
| Power BI | Interactive dashboard and reporting |
| DAX | Measures and dynamic calculations |
| Git & GitHub | Version control and project documentation |

---


## 8. Limitations and Future Improvements

### Current Limitations

- The dataset does not provide transaction dates, so genuine monthly, quarterly, or yearly revenue trends cannot be analyzed.
- Cost and profit information is unavailable; therefore, revenue should not be interpreted as profit.
- The analysis identifies associations and patterns, not causal relationships.
- Purchase-frequency day values are approximate mappings of categorical frequency labels.
- Customer segments are based on project-defined previous-purchase thresholds.

### Future Enhancements

- Introduce transaction-level historical data for time-series analysis.
- Develop customer lifetime value (CLV) metrics using richer customer history.
- Perform RFM (Recency, Frequency, Monetary) customer segmentation when suitable transaction data is available.
- Build predictive models for customer churn and purchase behavior.
- Evaluate discount effectiveness using controlled experiments.
- Develop automated data refresh and reporting pipelines.

---

## 9. Project Deliverables

- Python notebook for data inspection, cleaning, feature engineering, and database integration.
- MySQL scripts for business analysis.
- Interactive Power BI dashboard.
- Business findings and actionable recommendations.
- GitHub documentation and reproducible project workflow.

---

## 10. Conclusion

This project demonstrates an end-to-end data analytics workflow that combines Python, MySQL, and Power BI to transform raw customer shopping data into business-oriented insights.

Through data cleaning, SQL-based business analysis, and interactive visualization, the project explores revenue distribution, customer segments, product performance, discount usage, subscription patterns, and purchasing behavior.

The final objective is to support better retail decision-making through data-driven analysis of customer behavior and business performance.

---

**Author:** Vagisha Bhavsar  
**Domain:** Retail Analytics | Business Intelligence | Data Analytics  
**Technologies:** Python · Pandas · MySQL · SQL · Power BI · DAX

