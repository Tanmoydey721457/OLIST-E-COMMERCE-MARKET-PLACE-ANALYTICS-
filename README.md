Olist Brazilian E-Commerce — Data Analysis Hackathon

Business-focused analysis of marketplace performance, delivery reliability, customer satisfaction, seller performance, product categories, payment behavior, and root causes of low reviews.

📌 Project Overview

This project analyzes the Olist Brazilian E-Commerce Public Dataset, covering approximately 100,000 orders placed between September 2016 and October 2018.

The goal was to move beyond basic descriptive analysis and identify which operational factors are most strongly associated with customer dissatisfaction, then translate those findings into practical recommendations for Olist's operations and customer experience teams.

🎯 Business Problem

Olist leadership needs to understand:

How marketplace performance changed over time

How delivery timing relates to customer satisfaction

Which sellers and regions show performance differences

Which product categories perform better or worse

How payment behavior relates to order value and customer experience

Which factors show the strongest association with low review scores

The analysis is evidence-driven. Associations are reported as associations; the project does not claim causal relationships.

🧠 Analytical Approach

The project follows an end-to-end analytics workflow:

Data Understanding — reviewed the interconnected Olist tables and their relationships.

Data Quality Assessment — checked missing values, duplicates, timestamps, and key identifiers.

Feature Engineering — created purchase-period, delivery-days, delivery-delay, delivery-performance, delay-severity, order-value, category, and low-review features.

Order-Level Integration — aggregated item and payment tables by order_id before joining, keeping the master dataset at one row per order.

Exploratory Analysis — analyzed marketplace trends, delivery, geography, sellers, categories, payment behavior, reviews, and repeat customers.

Root Cause Analysis — compared the relative strength of observed signals associated with low reviews.

Business Intelligence — built an interactive Power BI dashboard with KPIs, trends, delivery analysis, satisfaction analysis, and business insights.

🛠️ Tools & Technologies

Python

Pandas — data manipulation and aggregation

NumPy — numerical operations and feature engineering

Matplotlib — analytical visualizations

Seaborn — exploratory visualization

Power BI — interactive dashboard and business reporting

DAX — KPI and dashboard measures

Jupyter / Google Colab — analysis notebook

GitHub — project versioning and presentation

📊 Dataset

The original Olist dataset contains nine related tables:

Table

Rows

Grain

Orders

99,441

One row per order

Order Items

112,650

One row per item

Order Payments

103,886

One row per payment record

Order Reviews

100,000

One row per review

Customers

99,441

One row per order-level customer record

Products

32,951

One row per product

Sellers

3,095

One row per seller

Geolocation

1,000,163

Multiple readings per ZIP-code prefix

Category Translation

71

Category-name mapping

Dataset period: September 2016 – October 2018.

Source

Brazilian E-Commerce Public Dataset by Olist, originally published on Kaggle:



Please verify the current dataset license and attribution requirements on the source page before redistribution or commercial use.

📁 Repository Structure

Olist-Ecommerce-Data-Analysis/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── Olist_Hackathon_Final_Notebook.ipynb
│
├── data/
│   └── olist_master_for_powerbi.csv
│
└── images/
    ├── dashboard_page2_delivery_satisfaction.png
    └── dashboard_page3_root_cause.png

Included Files

Notebook: complete Python analysis and documented business findings.

Modified CSV: order-level master dataset prepared for Power BI.

Dashboard images: screenshots of the completed dashboard pages available in this project workspace.

The original 9-table workbook is not duplicated in this repository. Use the official public dataset source above if the raw source tables are required.

🔧 Data Preparation

The final Power BI-ready dataset keeps one row per order. Item-level and payment-level data were aggregated by order_id before being joined, preventing multi-item and multi-payment orders from unintentionally multiplying rows.

Key engineered fields include:

purchase_year

purchase_month

purchase_year_month

delivery_days

delivery_delay_days

delivery_performance

delay_bucket

total_items

total_price

total_freight

total_payment

payment_types_used

review_score

low_review

customer_unique_id

customer_state

categories

📈 Power BI Dashboard

Page 1 — Marketplace Overview

Designed to give leadership a quick view of overall marketplace performance.

Key areas:

Total Orders

Delivered Orders

Average Review Score

Total Order Value

Monthly Order Volume

Monthly Revenue

Average Review Score by Month

Order Status Distribution

Page 2 — Delivery & Customer Satisfaction

This page focuses on the strongest observed relationship in the analysis: delivery performance and customer satisfaction.

Key visuals:

Average Delivery Days

Average Delay Days for Late Orders

Late Delivery Rate

Low Review Rate

Delivery Performance vs Customer Satisfaction

Delay Severity vs Low Review Rate

State-level delivery/satisfaction comparisons

Satisfaction by Payment Type



Page 3 — Root Cause & Business Insights

This page summarizes the most important customer-experience findings.

Key KPIs and visuals:

Low Review Rate

Average Review Score

Repeat Customers

Customer Satisfaction Distribution

Satisfaction by Payment Type

Key Business Insights



🔎 Key Insights

1. Delivery reliability is the strongest observed signal

Late orders show substantially worse customer satisfaction than on-time orders. The root-cause analysis reports 54.56% low reviews for late orders versus 9.46% for on-time orders.

2. Delay severity matters

Low-review rates increase sharply as delivery delays become more severe. The analysis reports a rise from about 10.52% for on-time orders to 78%+ for orders delayed by 8 or more days.

3. Seller performance is a secondary operational priority

Seller performance varies meaningfully. In the analytical seller-risk segmentation, high-risk sellers show substantially higher late-delivery and low-review rates than low-risk sellers.

4. Product categories also vary

Several categories show elevated low-review rates. However, category-level signals are weaker than the delivery-related signals.

5. Freight cost is a weaker signal

Review scores remain relatively stable across freight-to-price groups, suggesting freight cost is not the primary explanation for customer dissatisfaction in this analysis.

6. Payment behavior is more related to order value than satisfaction

Payment type and installment patterns show limited differences in review satisfaction, although payment behavior provides useful information about order value.

7. Review text supports the quantitative findings

Among 15,093 low-score reviews, 11,408 contain written messages. Exploratory keyword analysis identifies themes involving delivery, product quality, refunds/returns, missing or incomplete orders, and seller/support issues.

8. Repeat customers are a valuable segment

Repeat customers are a relatively small group but have higher average spending than one-time customers, while average review scores are similar.

🎯 Business Recommendations

Priority 1 — Improve Delivery Reliability

Make delivery reliability a core operational KPI and prioritize reducing late deliveries.

Priority 2 — Monitor Severe Delivery Delays

Create operational alerts for orders approaching or exceeding estimated delivery dates, with stronger intervention for severe delays.

Priority 3 — Monitor Seller Performance

Build seller performance scorecards using delivery delay rate, review score, and low-review rate to identify sellers requiring targeted support or performance review.

Priority 4 — Investigate Regional Performance

Focus operational investigation on regions with consistently high late-delivery rates and evaluate carrier coverage, routes, and fulfillment capacity.

Priority 5 — Investigate Underperforming Categories

Combine category, seller, and delivery analysis to identify whether specific product groups require different fulfillment or quality processes.

Secondary — Monitor Freight & Maintain Payment Flexibility

Freight cost should remain an efficiency metric, but not the primary customer-satisfaction intervention. Dominant payment methods and installment options should continue to be supported.

🧩 Root Cause Matrix

Factor

Evidence Strength

Business Role

Delivery Reliability

Very Strong

Primary

Delivery Delay Severity

Very Strong

Primary

Seller Performance

Strong

Secondary

Product Category

Moderate

Secondary

Freight Cost

Weak

Weak / Secondary

Payment Behavior

Weak

Limited

⚠️ Limitations

The analysis identifies associations and does not establish causality.

Delivery timestamps contain missing values, particularly for orders that were not delivered.

Small seller and category groups can produce unstable comparisons, so minimum-volume filters were used for detailed analysis.

Geographic analysis is performed at customer-state level and does not capture every local logistics difference.

Review scores do not capture every aspect of customer experience.

Review keyword matching is exploratory and is not a definitive complaint classifier.

▶️ How to Use This Repository

1. Open the notebook

Open:

notebooks/Olist_Hackathon_Final_Notebook.ipynb

It can be run in Google Colab or Jupyter Notebook.

2. Use the Power BI-ready data

Import:

data/olist_master_for_powerbi.csv

into Power BI Desktop.

3. Explore the dashboard

Use the three dashboard pages to move from marketplace overview → delivery/customer satisfaction → root cause and business insights.

🏁 Conclusion

The analysis indicates that delivery performance is the strongest observed factor associated with customer dissatisfaction. Both late-delivery frequency and delay severity show strong relationships with low review scores, while seller performance and product category provide additional but weaker signals.

The main operational opportunity is therefore to improve delivery reliability, detect severe delays earlier, and use seller and regional monitoring to target operational support where the data shows the strongest signals.

Project: Olist Brazilian E-Commerce — Data Analysis Hackathon
Focus: Data Analytics • Customer Experience • Operations • Business Intelligence
