# 🛍️ Customer Shopping Behavior Analysis
### End-to-End Data Analytics Project | Python · MS SQL Server · Power BI

---

## 📌 Project Overview

This project performs a complete, industry-standard data analytics workflow on a retail customer shopping dataset containing **3,900 transactions** across multiple product categories.

The objective is to answer a core business question:

> *"How can a retail company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?"*

The project covers the full analytics pipeline — from raw data cleaning in Python, structured querying in SQL, to an interactive dashboard in Power BI.

---

## 🗂️ Project Structure

```
📁 customer-behavior-analysis/
├── Customer_Shopping_Behavior_Analysis.ipynb   # Python EDA & data loading
├── customer_behavior_sql_queries.sql           # SQL business queries (10 questions)
├── customer_behavior_dashboard.pbix            # Power BI interactive dashboard
├── customer_shopping_behavior.csv              # Raw dataset (3,900 rows)
├── Business_Problem__Document.pdf              # Business problem statement
└── README.md
```

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (Pandas, SQLAlchemy, Matplotlib, Seaborn) | Data cleaning, EDA, DB connection |
| MS SQL Server + SSMS | Data storage & SQL analysis |
| Power BI Desktop | Interactive dashboard & visualization |
| Jupyter Notebook | Python development environment |

---

## 📊 Dataset Summary

- **Rows:** 3,900 customer transactions
- **Columns:** 18 features
- **Key Features:**
  - Customer demographics: Age, Gender, Location, Subscription Status
  - Purchase details: Item, Category, Purchase Amount, Season, Size, Color
  - Behavior signals: Discount Applied, Previous Purchases, Frequency, Review Rating, Shipping Type
- **Data issue handled:** 37 missing values in `Review Rating` — imputed using category-level median

---

## 🔬 Phase 1 — Data Preparation & EDA (Python)

Performed in `Customer_Shopping_Behavior_Analysis.ipynb`:

- Loaded and explored the raw CSV using `pandas`
- Checked data types, null values, and summary statistics
- **Imputed** missing `review_rating` values using the median rating per product category
- **Renamed** all columns to snake_case for consistency
- **Feature Engineering:**
  - Created `age_group` column by binning customer ages (Young Adult / Adult / Middle-aged / Senior)
  - Created `purchase_frequency_days` from frequency-of-purchase strings
- **Dropped** `promo_code_used` after confirming it was redundant with `discount_applied`
- **Loaded** the cleaned DataFrame into MS SQL Server using `SQLAlchemy` (Windows Authentication)

---

## 🗄️ Phase 2 — Data Analysis (MS SQL Server)

Ran 10 business queries in `customer_behavior_sql_queries.sql` to extract actionable insights:

| # | Business Question | Key Finding |
|---|---|---|
| 1 | Revenue by Gender | Male customers generated ~2x more revenue ($157,890 vs $75,191) |
| 2 | High-spending discount users | 839 customers used discounts but still spent above average |
| 3 | Top 5 products by rating | Gloves (3.86), Sandals (3.84), Boots (3.82) led ratings |
| 4 | Standard vs Express shipping spend | Express users spend slightly more ($60.48 vs $58.46 avg) |
| 5 | Subscriber vs non-subscriber revenue | Non-subscribers generate more total revenue despite similar avg spend |
| 6 | Most discount-dependent products | Hat (50%), Sneakers (49.66%), Coat (49.07%) |
| 7 | Customer segmentation | 3,116 Loyal / 701 Returning / 83 New customers |
| 8 | Top 3 products per category | Blouse & Pants lead Clothing; Jewelry leads Accessories |
| 9 | Repeat buyers & subscriptions | Most repeat buyers (2,518) are non-subscribers — retention opportunity |
| 10 | Revenue by age group | Young Adults contribute most revenue ($62,143) |

**SQL concepts used:** GROUP BY, Subqueries, CTEs, Window Functions (ROW_NUMBER, PARTITION BY), CASE WHEN, ROUND, aggregate functions

---

## 📈 Phase 3 — Dashboard (Power BI)

Connected Power BI to MS SQL Server and built an interactive dashboard with:

- **KPI Cards:** Total Customers (3.9K), Avg Purchase Amount ($59.76), Avg Review Rating (3.75)
- **Donut Chart:** Subscription status breakdown (Yes 27% / No 73%)
- **Bar Charts:** Revenue and Sales by Category, Revenue and Sales by Age Group
- **Slicers:** Filter by Subscription Status, Gender, Category, Shipping Type
https://github.com/Ankit-Dubey10/Customer-Shopping-Behavior-Analysis/blob/main/dashboard.png
---

## 💡 Business Recommendations

Based on the analysis, the following strategic actions are recommended:

1. **Boost Subscriptions** — Only 27% of customers subscribe. Promoting exclusive subscriber benefits could significantly increase retention and revenue.
2. **Loyalty Programs** — With 3,116 loyal customers already, a structured rewards program could further reduce churn.
3. **Review Discount Policy** — Products like Hat and Sneakers have ~50% discount rates; margins need review to ensure profitability.
4. **Target Young Adults** — Highest revenue-contributing segment; focus digital marketing here.
5. **Promote Top-Rated Products** — Gloves, Sandals, and Boots have strong ratings and should be highlighted in campaigns.
6. **Express Shipping Upsell** — Express shipping users spend slightly more; promoting it could lift average order value.

---
