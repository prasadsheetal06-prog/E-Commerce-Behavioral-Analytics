# 📊 E-Commerce Behavioral Pipeline & Conversion Analysis
### *Full-Stack Product Analytics: Identifying Intent & Recovering Revenue*

## 📌 Project Overview
This project transforms raw user interaction data into a strategic roadmap for conversion optimization. By integrating **Python-driven behavioral segmentation** with **SQL-based financial attribution**, I mapped the user journey of 2,500+ global sessions to identify high-value behaviors and pinpoint where revenue "leaks" from the funnel.

---

## 🚀 Phase 1: Behavioral Analytics & Feature Engineering (Python)

**Objective:** Cleanse raw session data and engineer "Intelligent Features" that quantify user intent.

* **From Noisy Data to Insights:** The raw dataset contained high-variance metrics like absolute click counts and erratic session durations. I neutralized this noise by creating the **Intent Score (Cart-to-View Ratio)**, which measures the efficiency of a user's path to purchase rather than just their time spent browsing.
* **Intelligent Features:** * `cart_to_view_ratio`: Distinguishes "Surgical Buyers" from "Window Shoppers."
    * `session_velocity`: Average time spent per page to identify engagement depth.

### Visualizing Interaction Patterns
![Correlation Heatmap](image_9bdb8b.png)
**Interpreting the Heatmap:**
* The high correlation (**0.73**) between `purchased` and `order_value_usd` validates the data integrity for revenue analysis.
* The low correlation between `pages_viewed` and `purchased` (**0.07**) was a key finding—proving that "more browsing" does not necessarily equal "more buying," shifting the focus toward session quality over quantity.

![Distribution of Pages](image_9bdbc3.png)
**Engagement Frequency:** The distribution reveals a peak at 5–6 pages per session. Users exceeding this "saturation point" without adding to cart are flagged as "Stuck" in the UI, representing a friction point rather than high interest.

---

## 📈 Phase 2: User Segmentation & Multivariate Analysis

I utilized **K-Means Clustering** to segment the population into three distinct archetypes based on behavior rather than just demographics.

| Segment | Label | % of Traffic | Key Characteristic | Strategic Action |
| :--- | :--- | :--- | :--- | :--- |
| **Segment 1** | **The VIPs** | ~15% | High Intent Score, 100% Conversion | Loyalty & Retention |
| **Segment 0** | **The Potential** | ~51% | Moderate engagement, 5.18% Conversion | Personalization & Nudging |
| **Segment 2** | **Window Shoppers**| ~34% | Max Time on Site, 0% Conversion | UI/UX Friction Audit |

![Pairplot of Segments](Screenshot%20(784).jpg)
**Pairplot Interpretation:** This visualization confirms that Segment 1 (blue clusters) occupies the high-intent/high-purchase space with minimal time wastage, while Segment 2 (orange clusters) shows high "Time on Site" but fails to cross the "Added to Cart" threshold, highlighting a major conversion leak.

---

## 🛠️ Phase 3: Strategic SQL Infrastructure & ETL

**Objective:** Build a "Golden Record" database to allow stakeholders to query behavioral segments in real-time.

* **ETL Pipeline:** I developed a structured extraction process to move ML-generated labels into a **MySQL Relational Schema**. This involved data type optimization (e.g., converting floats to decimal for financial precision) and ensuring referential integrity across session IDs.

![MySQL Schema and Describe](image_9bdbe7.png)
**Schema Design:** The `sessions` table serves as the primary source of truth, integrating `customer_segment` and `predicted_session_value` directly into the relational environment for BI tool consumption.

### Advanced SQL Metrics & Attribution
![Revenue Ranking Query](Revenue%20rank%20by%20country%20and%20device%202.png)
**Revenue Attribution:** Using **Window Functions** (`SUM OVER`), I calculated the `pct_contribution_to_revenue`. This allows the Analytics Head to see that specific country-device combinations (e.g., Country 3 on Device 0) are driving the lion's share of sales.

![Traffic Source Analysis](Comparing%20behavior%20across%20traffic%20sources%202.png)
**Funnel Leakage Analysis:** This query calculates the **Leakage Rate**—the percentage of users who add to cart but do not purchase. By ordering by `leakage_rate DESC`, I identified that certain traffic sources have a **-110% inefficiency**, indicating a critical drop-off in the checkout pipeline.

---

## 🔍 Executive Summary & Insights

* **For the Analytics Head:** Engagement time is a "vanity metric" in this dataset. The **Intent Score** is a 12x better predictor of conversion, suggesting a shift in KPI focus from *Time on Site* to *Cart-to-View efficiency*.
* **For the Stakeholders:** **Segment 2 (Window Shoppers)** represents a massive revenue recovery opportunity. Despite being 34% of our traffic, they produce $0 revenue. Implementing "Exit-Intent" discounts or "Saved Cart" reminders for this group could reclaim significant lost GMV.
* **For HR/Product Managers:** This project demonstrates a full-cycle ability to handle raw data, apply machine learning for segmentation, and deploy SQL infrastructure for business reporting.

---

## 🛠️ Technical Stack
* **Product Analytics:** Python (Pandas, Scikit-Learn), Feature Engineering, Behavioral Segmentation.
* **Data Infrastructure:** SQL (MySQL), ETL Pipeline Design, Relational Schema Architecture.
* **Advanced SQL:** Window Functions, CTEs, Ranking, Funnel Analysis.
* **Visualization:** Seaborn, Matplotlib, MySQL Workbench Reporting.
