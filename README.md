# 📊 E-Commerce Behavioral Pipeline & Conversion Analysis
**An End-to-End Data Science & SQL Project**

## 📌 Project Overview
This project bridges the gap between raw web behavior and actionable business strategy. Using a dataset of **2,500+ global e-commerce sessions**, I developed a full-stack analytics pipeline. By applying the **Scientific Method**—forming hypotheses about user intent and testing them through Machine Learning—I identified high-value segments and quantified "leakage" in the conversion funnel.

---

## 🚀 Phase 1: Behavioral Data Science (Python)
**Objective:** Transform raw, noisy session data into "Intelligent Features."

* **Scientific Approach:** Applied variable control to isolate "Time on Site" as the primary driver of purchase intent.
* **Feature Engineering:** Engineered a custom `cart_to_view_ratio` (Intent Score) to distinguish between casual browsing and high-intent shopping.
* **Machine Learning:**
    * **Random Forest:** Identified feature importance, revealing that engagement time (88.6% importance) outweighs page count.
    * **K-Means Clustering:** Segmented the population into 3 distinct behavioral archetypes:
        * **Segment 1 (The VIPs):** High-efficiency buyers; 100% conversion rate in refined testing.
        * **Segment 0 (The Potential):** Middle-funnel users with a 5.18% conversion rate.
        * **Segment 2 (Window Shoppers):** High engagement (7.4 min avg) but 0% conversion—the primary revenue recovery target.



---

## 📈 Phase 2: Strategic Infrastructure & BI (SQL)
**Objective:** Migrate ML-refined data into a relational environment for financial reporting.

* **ETL Pipeline:** Migrated the "Golden Record" from Python to a MySQL relational schema.
* **Funnel Analytics:** Utilized **CTEs** to map the transition from `Session -> Add-to-Cart -> Purchase`.
* **Revenue Attribution:** Implemented **Window Functions** (`SUM OVER` and `RANK`) to calculate the exact percentage of global revenue contributed by each ML-generated segment.



---

## 🔍 Key Strategic Insights
* **The Conversion Leak:** Segment 2 represents 34% of total traffic. Despite spending the most time on-site, they have a **0% conversion rate**, suggesting a critical UI/UX friction point in the checkout process.
* **Efficiency Metric:** Segment 1 users are "Surgical Buyers"—they spend less time but have the highest Intent Score (0.087).
* **Revenue Opportunity:** Targeting Segment 2 with "Exit-Intent" triggers could potentially recover significant lost revenue currently stalled in abandoned carts.

---

## 🧪 The "Science" in the Data
Coming from a **BSc (BCGbt)** background, I approached this project as a controlled experiment:
* **Observation:** Browsing patterns varied wildly across regions.
* **Hypothesis:** Higher engagement time correlates with intent, but only up to a "saturation point."
* **Experimentation:** Used Feature Scaling and Clustering to validate that "time-on-site" is a stronger predictor of sales than "number of pages viewed."
* **Conclusion:** Conversion is a multi-variant problem requiring both behavioral science (Python) and structural analysis (SQL).

---

## 🛠️ Technical Stack
* **Languages:** Python (Pandas, Scikit-Learn), SQL (MySQL)
* **Models:** Random Forest, K-Means Clustering
* **Techniques:** ETL Pipelines, Feature Engineering, Window Functions, CTEs, Data Visualization (Seaborn/Matplotlib)

---
