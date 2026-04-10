# 🛍️ Customer Behavior Analysis

> An end-to-end data analytics project covering data cleaning, feature engineering, SQL querying, and Power BI visualization on a retail customer shopping dataset.

---

## 📌 Project Overview

This project analyzes retail customer shopping behavior across **3,900 customers** and **4 product categories** (Clothing, Accessories, Footwear, Outerwear). The pipeline moves from raw CSV data through Python preprocessing, PostgreSQL storage, structured SQL analysis, and finally an interactive Power BI dashboard.

---

## 📊 Dashboard Preview

![Customer Behavior Dashboard](dashboard.png)

| KPI | Value |
|-----|-------|
| 👥 Total Customers | 3,900 |
| ⭐ Avg Review Rating | 3.75 / 5 |
| 💵 Avg Purchase Amount | $59.76 |

---

## 🗂️ Project Structure

```
customer-behavior-analysis/
│
├── 📄 customer_shopping_behavior.csv   # Raw dataset
├── 🐍 analysis.py                      # Data cleaning & feature engineering
├── 🗃️ queries.sql                      # 10 SQL business queries
├── 📊 dashboard.pbix                   # Power BI dashboard file
├── 📋 dashboard.png                    # Dashboard screenshot
└── 📝 README.md
```

---

## 🛠️ Tech Stack

| Layer | Tool |
|-------|------|
| Data Wrangling | Python (Pandas) |
| Database | PostgreSQL |
| ORM / Connector | SQLAlchemy + psycopg2 |
| SQL Client | pgAdmin |
| Visualization | Microsoft Power BI |

---

## ⚙️ Setup & Usage

### 1. Clone the repository
```bash
git clone https://github.com/your-username/customer-behavior-analysis.git
cd customer-behavior-analysis
```

### 2. Install Python dependencies
```bash
pip install pandas sqlalchemy psycopg2-binary
```

### 3. Run the data pipeline
```bash
python analysis.py
```

### 4. Configure PostgreSQL connection
Inside `analysis.py`, update your credentials:
```python
username = "postgres"
password = "your_password"
host     = "localhost"
port     = "5432"
database = "customer_behavior"
```

### 5. Run SQL queries
Open `queries.sql` in pgAdmin or any PostgreSQL client and execute the queries against the `customer` table.

### 6. View the dashboard
Open `dashboard.pbix` in **Microsoft Power BI Desktop**.

---

## 🧹 Data Cleaning Steps

- **Null imputation** — `review_rating` filled with category-level median
- **Column normalization** — Lowercase names, underscores replacing spaces
- **Duplicate removal** — `promo_code_used` dropped (100% identical to `discount_applied`)

## 🔧 Feature Engineering

| Feature | Method | Values |
|---------|--------|--------|
| `age_group` | Quartile binning (`pd.qcut`) | Young Adult, Adult, Middle-aged, Senior |
| `purchase_frequency_days` | Label mapping | 7, 14, 30, 90, 365 |

---

## 🔍 SQL Queries (10 Business Questions)

| # | Question | SQL Concept |
|---|----------|-------------|
| Q1 | Revenue by gender | `GROUP BY`, `SUM` |
| Q2 | High-value discount users | Subquery, scalar aggregation |
| Q3 | Top 5 highest-rated products | `AVG`, `ROUND`, `ORDER BY` |
| Q4 | Standard vs Express shipping spend | Filtered `GROUP BY` |
| Q5 | Subscriber vs non-subscriber spend | Multi-metric aggregation |
| Q6 | Top 5 products by discount rate | `CASE WHEN`, conditional aggregation |
| Q7 | Customer segmentation (New / Returning / Loyal) | CTE, `CASE WHEN` |
| Q8 | Top 3 products per category | Window function (`ROW_NUMBER`, `PARTITION BY`) |
| Q9 | Repeat buyers & subscription tendency | Filtered aggregation |
| Q10 | Revenue by age group | `GROUP BY` on engineered column |

---

## 💡 Key Findings

- 📌 **Male customers** generate **2.1×** more revenue than female customers ($157,890 vs $75,191)
- 📌 **Young Adults** are the top revenue-generating age group at **$62,143**
- 📌 **80% of customers** are classified as Loyal (11+ purchases) — strong retention, weak acquisition
- 📌 **Gloves** are the highest-rated product with an average rating of **3.86**
- 📌 **Hat** has the highest discount usage at **50%** — potential margin erosion risk
- 📌 Subscribers spend nearly the same as non-subscribers (~$59.70 avg) — subscription benefits need restructuring

---

## 📈 Power BI Dashboard Features

- **Donut Chart** — Customer split by subscription status (73% No / 27% Yes)
- **Bar Charts** — Sales & Revenue by Category
- **Horizontal Bars** — Revenue & Sales by Age Group
- **Slicers** — Filter by Gender, Category, Subscription Status, Shipping Type

---

## 📄 License

This project is for educational and portfolio purposes.

---

> Made with 🐍 Python · 🐘 PostgreSQL · 📊 Power BI
