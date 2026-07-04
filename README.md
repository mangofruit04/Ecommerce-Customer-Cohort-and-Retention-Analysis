# Ecommerce-Customer-Cohort-and-Retention-Analysis

End-to-end customer cohort retention analysis using PostgreSQL and Power BI to track 12-month user lifecycles, optimize customer lifetime value (LTV), and identify drop-off patterns.

## 🎯 Executive Summary

This project analyzes an e-commerce transactional retail dataset to map out month-over-month user retention across 4,300+ unique customer accounts. By engineering data workflows entirely within PostgreSQL and establishing a server connection to Power BI, I discovered that the business experiences its most critical user drop-off immediately within the first 30 days of acquisition, while also uncovering a highly sticky, seasonal onboarding framework that can be replicated to protect recurring revenue.

## 🛠️ The Tech Stack

* **Database Engine & ETL Process:** PostgreSQL
* **Business Intelligence Dashboard:** Power BI Desktop
* **Server Integration:** PostgreSQL to Power BI Direct Connection

## ⚙️ Data Engineering Steps (What I Did)

### 1. PostgreSQL Transformation & ETL Pipeline
Before creating any charts, I wrote custom SQL queries inside PostgreSQL to handle data cleaning and transform the flat transaction logs into a structured cohort format:
* **Cohort Stamping:** Used `MIN(InvoiceDate) OVER (PARTITION BY CustomerID)` to capture each user's absolute first order month (`cohort_month`).
* **Index Engineering:** Calculated the difference between subsequent order dates and the base signup month to build the rolling tracking timeline (`cohort_index` from 0 to 12).
* **Aggregation:** Grouped the transactions to find the exact distinct count of unique users (`COUNT(DISTINCT CustomerID)`) across every elapsed time bucket.

### 2. Power BI Dashboard Integration
* Connected Power BI Desktop directly to the PostgreSQL server to import the cleaned, pre-calculated summary tables.
* Dropped `cohort_month` into matrix rows, `cohort_index` into matrix columns, and configured conditional background color maps to instantly display customer density patterns.
* Configured full interactive cross-filtering capabilities natively across all charts without needing complex DAX measures.

## 🔍 Key Strategic Insights

* **The Month 1 Churn Cliff:** Across all monthly signups, a severe system leak occurs immediately between Month 0 and Month 1, where more than 50% of acquired users fail to return for a second purchase.
* **The December Quality Peak:** December serves as a massive volume anomaly, bringing in a record 926 unique customers. Rather than a temporary holiday rush, this cohort maintained the most stable retention curve over a 12-month period, keeping over 300+ active buyers returning every single month.

## 🖼️ Finished Business Dashboard

Below is the default visualization canvas displaying the global ecosystem parameters, tracking lines, and the complete customer lifetime lifecycle grid:

![Finished Business Dashboard]https://github.com/mangofruit04/Ecommerce-Customer-Cohort-and-Retention-Analysis/blob/main/Screenshot%202026-07-04%20231419.png

## 💡 Strategic Recommendations

* **Launch Automated Month 1 Re-Engagement:** To stop the immediate 50%+ customer leak, deploy automated post-purchase email triggers, customized secondary-order discount codes, or prompt loyalty reward points to pull users successfully over the Month 1 hurdle.
* **Replicate the December Playbook:** Reverse-engineer the precise bundles, marketing channels, and seasonal campaigns run during December. Re-deploy this exact commercial framework during mid-year promotional milestones (such as summer events or regional festivals) to spark consistent high-retention spikes.

---
*Developed by a Bachelor of Science in Information Technology for portfolio*

### Tags
#DataAnalytics #PowerBI #PostgreSQL #SQL #CohortAnalysis #CustomerRetention #ETL #DataVisualization #BusinessIntelligence #EcommerceAnalytics
