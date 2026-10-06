# Customer Shopping Behavior Analysis

A full end-to-end data analysis project: from raw data to an interactive Power BI dashboard and a stakeholder-ready presentation.

---

## 📌 Overview

This project analyzes customer shopping behavior to uncover purchasing patterns, demographic trends, and factors that influence spending. It demonstrates a complete data analytics workflow — from data cleaning in Python to SQL-based business analysis and a final Power BI dashboard — reflecting a realistic, end-to-end analyst task.

**Key questions explored:**
- Which customer segments spend the most, and why?
- How do discounts affect purchase amount?
- Which products receive the highest customer satisfaction?
- How does shipping type impact average spending?

---

## 🗂️ Dataset

- **Source:** Customer shopping behavior dataset ([link to source / Kaggle / GitHub repo])
- **Size:** ~3,900 records, 18 columns
- **Key fields:** Customer ID, Age, Gender, Item Purchased, Category, Purchase Amount, Location, Review Rating, Subscription Status, Shipping Type, Discount Applied, Promo Code Used, Previous Purchases, Payment Method, Frequency of Purchases

---

## 🛠️ Tools & Technologies

| Category | Tools |
|---|---|
| Data Processing | Python (pandas, NumPy) |
| Environment | Jupyter Notebook |
| Database | PostgreSQL / MySQL / SQL Server |
| Querying | SQL (joins, aggregations, subqueries, window functions) |
| Visualization | Power BI |
| Presentation | PowerPoint (built with Gamma) |

---

## 🔄 Project Workflow

1. **Data Loading** — Imported the raw dataset into Python using pandas.
2. **Exploratory Data Analysis (EDA)** — Reviewed data types, distributions, and summary statistics to understand the dataset before cleaning.
3. **Data Cleaning** — Checked and handled missing values, removed duplicates, standardized column names and data types.
4. **Database Integration** — Loaded the cleaned dataset into a SQL database (PostgreSQL/MySQL/SQL Server) using SQLAlchemy.
5. **SQL Analysis** — Wrote and executed business-focused SQL queries to answer key questions (top products, discount impact, customer segments, shipping comparisons, etc.).
6. **Dashboard Development** — Built an interactive Power BI dashboard connected directly to the database to visualize key metrics and trends.
7. **Reporting & Presentation** — Summarized insights in a written report and created a stakeholder-ready presentation using Gamma.

---

## 📊 Dashboard

The Power BI dashboard provides an interactive view of:
- Overall sales and purchase amount trends
- Customer demographics (age, gender, location)
- Category and product performance
- Discount and promo code impact on spending
- Shipping type and subscription status breakdown

📎 *[Add dashboard screenshot or link here]*

---

## 💡 Key Findings

- [Insight 1 — e.g., "Customers who used a discount still spent X% above average"]
- [Insight 2 — e.g., "Top 5 products by average review rating are..."]
- [Insight 3 — e.g., "Express shipping customers spend more on average than Standard shipping"]
- [Insight 4 — add your own data-driven conclusion]

*(Replace with the actual results from your SQL queries and dashboard.)*

---

## ▶️ How to Run This Project

### 1. Clone the repository
```bash
git clone https://github.com/your-username/customer-shopping-behavior-analysis.git
cd customer-shopping-behavior-analysis
```

### 2. Set up the environment
```bash
pip install pandas sqlalchemy psycopg2-binary jupyter
```

### 3. Run the Jupyter Notebook
```bash
jupyter notebook
```
Open `customer_behavior_analysis.ipynb` and run the cells in order to load, clean, and export the data.

### 4. Load data into your database
Update the database credentials in the notebook, then run the cell that executes:
```python
df.to_sql("customer", engine, if_exists="replace", index=False)
```

### 5. Run the SQL queries
Open the `queries.sql` file in pgAdmin / DBeaver / SQL Server Management Studio and execute the queries against the `customer` table.

### 6. Open the dashboard
Open `dashboard.pbix` in Power BI Desktop and refresh the data connection to your local database.

---

## 📁 Project Structure

```
customer-shopping-behavior-analysis/
├── data/
│   └── customer_shopping_behavior.csv
├── notebooks/
│   └── customer_behavior_analysis.ipynb
├── sql/
│   └── queries.sql
├── dashboard/
│   └── dashboard.pbix
├── report/
│   └── analysis_report.pdf
└── README.md
```

---

## 👤 Author

**[Your Name]**
Junior Data Analyst
📧 [your email] | 🔗 [LinkedIn] | 💻 [GitHub]
