# 🛍️ Customer Shopping Behavior Analysis

An end-to-end data analytics project: raw data → cleaning in **Python** → business analysis in **PostgreSQL** → interactive **Power BI** dashboard → report and stakeholder presentation.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Alister44/customer_trends_data_analysis/blob/main/customer_behavior_analysis.ipynb)

![Power BI Dashboard](images/dashboard.png)

---

## 📌 Business Problem

A retail company wants to better understand its customers' shopping behavior in order to improve sales, customer satisfaction and long-term loyalty. Management is especially interested in which factors — discounts, reviews, shipping, subscriptions, demographics — drive spending and repeat purchases.

**Central question:** *How can the company use customer shopping data to identify trends, improve customer engagement and optimize marketing and product strategies?*

Full brief: [Business Problem Document.pdf](Business%20Problem%20%20Document.pdf)

---

## 🗂️ Dataset

- **Source:** [Customer Shopping Trends Dataset (Kaggle)](ADD-LINK-HERE)
- **Size:** 3,900 transactions, 18 columns
- **Key fields:** age, gender, item purchased, category, purchase amount (USD), location, season, review rating, subscription status, shipping type, discount applied, previous purchases, payment method, purchase frequency

---

## 🛠️ Tools & Technologies

| Stage | Tools |
|---|---|
| Data cleaning & feature engineering | Python (pandas), Jupyter Notebook / Google Colab |
| Database & analysis | PostgreSQL, SQLAlchemy, SQL (CTEs, subqueries, `CASE`, window functions) |
| Visualization | Power BI |
| Reporting | PDF report, PowerPoint presentation (built with Gamma) |

---

## 🔄 Workflow

1. **Exploratory analysis** — reviewed data types, distributions and summary statistics.
2. **Data cleaning**
   - Filled 37 missing `review_rating` values with the **median rating per category** (not the global median), to keep category-level differences intact.
   - Converted column names to `snake_case`.
   - Removed the redundant `promo_code_used` column after verifying it was identical to `discount_applied`.
3. **Feature engineering**
   - `age_group` — Young Adult (18–25), Adult (26–40), Middle-aged (41–55), Senior (56+).
   - `purchase_frequency_days` — converted text frequencies (Weekly, Quarterly, …) into numeric days.
4. **Database load** — wrote the cleaned dataset to PostgreSQL with SQLAlchemy.
5. **SQL analysis** — 10 business questions covering revenue, segments, discounts, products and shipping ([sql_queries.sql](sql_queries.sql)).
6. **Dashboard** — built an interactive Power BI dashboard on top of the database.
7. **Reporting** — summarized findings and recommendations in a report and a presentation.

---

## ❓ Business Questions Answered (SQL)

| # | Question | SQL techniques |
|---|---|---|
| 1 | Revenue by gender | `GROUP BY`, `SUM` |
| 2 | Customers who used a discount but still spent above average | subquery |
| 3 | Top 5 products by average review rating | aggregation, `ORDER BY`, `LIMIT` |
| 4 | Average spend: Standard vs. Express shipping | filtering, `AVG` |
| 5 | Do subscribers spend more? | aggregation |
| 6 | Top 5 products by share of discounted purchases | conditional aggregation (`CASE`) |
| 7 | Customer segmentation: New / Returning / Loyal | CTE, `CASE` |
| 8 | Top 3 products within each category | CTE, `ROW_NUMBER() OVER (PARTITION BY …)` |
| 9 | Are repeat buyers more likely to subscribe? | filtering, aggregation |
| 10 | Revenue contribution by age group | aggregation |

---

## 💡 Key Findings

- **Total revenue:** $233,081 from 3,900 purchases; average order value **$59.76**.
- **Clothing drives the business:** 45% of revenue ($104K), followed by Accessories ($74K). Outerwear contributes only $18.5K.
- **Gender:** men generate 68% of revenue ($158K vs. $75K), but average spend per purchase is almost identical (~$60). The gap comes from the **number of customers**, not from higher spending.
- **Subscriptions don't raise order value:** subscribers spend $59.49 on average vs. $59.87 for non-subscribers. Only 27% of customers are subscribed.
- **Discounts don't lower order value noticeably:** $59.28 with a discount vs. $60.13 without.
- **Shipping:** Express customers spend slightly more than Standard ($60.48 vs. $58.46).
- **Loyalty:** 80% of customers are *Loyal* (10+ previous purchases); only 83 customers are *New*.
- **Age:** revenue is evenly split between Adult, Middle-aged and Senior groups (~$65–67K each); Young Adults (18–25) bring in about half as much ($35K).
- **Highest-rated products:** Gloves (3.86), Sandals (3.84), Boots (3.82).

> Many differences between groups are small (1–3%). The data shows that customer behavior is very uniform across segments — this is itself a useful finding for targeting decisions.

---

## 📈 Business Recommendations

1. **Rethink the subscription offer.** Subscribers currently don't spend more per purchase — add exclusive benefits (early access, free Express shipping) that give a real reason to subscribe and buy more.
2. **Grow the Young Adult segment.** It brings in half the revenue of other age groups — test targeted campaigns and products for 18–25-year-olds.
3. **Use discounts confidently but selectively.** Discounts don't reduce order value, so they can be used to win new customers, where the base is very small.
4. **Strengthen weak categories.** Outerwear and Footwear lag far behind Clothing — consider bundles with best-selling clothing items.
5. **Promote highly rated products** (Gloves, Sandals, Boots) in marketing and on product pages.

---

## 📁 Project Files

| File | Description |
|---|---|
| [customer_behavior_analysis.ipynb](customer_behavior_analysis.ipynb) | Data cleaning, feature engineering, load to PostgreSQL |
| [sql_queries.sql](sql_queries.sql) | 10 business-focused SQL queries |
| [customer_behavior_dashboard.pbix](customer_behavior_dashboard.pbix) | Power BI dashboard |
| [Customer Shopping Behavior Report.pdf](Customer%20Shopping%20Behavior%20Report.pdf) | Written report with findings and recommendations |
| [Customer-behavior_project_presentation.pptx](Customer-behavior_project_presentation.pptx) | Stakeholder presentation |
| [customer_shopping_behavior.csv](customer_shopping_behavior.csv) | Raw dataset |
| [Business Problem Document.pdf](Business%20Problem%20%20Document.pdf) | Project brief |

---

## ▶️ How to Run

**Option 1 — no setup:** click the *Open in Colab* badge above and run the notebook (the dataset loads directly from this repository).

**Option 2 — locally:**

```bash
git clone https://github.com/Alister44/customer_trends_data_analysis.git
cd customer_trends_data_analysis
pip install -r requirements.txt
jupyter notebook customer_behavior_analysis.ipynb
```

To reproduce the SQL part:
1. Create a PostgreSQL database and set your credentials in the notebook (use an environment variable for the password, e.g. `os.getenv("DB_PASSWORD")`).
2. Run the notebook cell that loads the data into the `customer` table.
3. Run `sql_queries.sql` in pgAdmin or DBeaver.
4. Open `customer_behavior_dashboard.pbix` in Power BI Desktop and refresh the connection.

---

## 👤 Author

**Alisa Kotenko** — Junior Data Analyst
