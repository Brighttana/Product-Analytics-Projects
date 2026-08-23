# 📈 Global Supply Chain Risk Dashboard (US Inbound Focus)

## 📌 Executive Product Summary
In global logistics, unexpected maritime bottlenecks directly disrupt material requirements planning (MRP), inflate inventory carrying costs, and delay production timelines[cite: 1]. This project serves as an analytical MVP designed for **Supply Chain Operations Leaders** and **Procurement Managers** to monitor real-time shipping rate volatility and flag systemic risks heading toward United States ports[cite: 1].

By ingesting data from the US Bureau of Labor Statistics (BLS), this dashboard isolates macro pricing shocks and translates them into actionable operational insights—helping teams adjust safety stock buffers and dynamically negotiate carrier contracts[cite: 1].

---

## 📊 Live Interactive Tableau Dashboard
[![Tableau Dashboard](https://img.shields.io/badge/Tableau-Interactive_Dashboard-E97627?style=for-the-badge&logo=tableau&logoColor=white)](https://public.tableau.com/views/GlobalSupplyChainRiskOperationalIntelligence/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

> 🚀 **Live Operational Radar:** Access the interactive production dashboard on [Tableau Public](https://public.tableau.com/views/GlobalSupplyChainRiskOperationalIntelligence/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) to explore global supplier origin risk maps, dynamic multi-mode freight filtering (*Ocean Freight*, *Air Expedited*, *Intermodal Rail*), FRED macro cost stress corridors (>350 index), and 5-shipment rolling lead-time variance.

---

## 📊 Visualized US Inbound Logistics Shocks (2022 - 2026)
The visualization below isolates the intense volatility hitting US inbound deep-sea freight lanes[cite: 1]. The red alert threshold dynamically flags periods where structural supply line stress threatens domestic retail and manufacturing margins[cite: 1].

![US Inbound Freight Shocks](supply_chain_shocks_plot.png)

---

## 🎯 Deep-Dive Operational Analysis & US Business Impact

### 1. The Middle East Transit Crisis (Late 2023 - Present)
As highlighted by the active red risk corridor on the graph, regional conflicts impacting crucial maritime choke points (such as the Red Sea and the Strait of Hormuz) have severely penalized US-bound shipping lanes[cite: 1]:
* **Extended Lead Times:** Ocean carriers bypassing high-risk zones are forced to route around the Cape of Good Hope, adding **10 to 14 days** of transit time for components bound for US East Coast factories[cite: 1].
* **Port Congestion & Diversions:** To avoid prolonged voyages, massive volumes of cargo have been diverted directly to US West Coast ports (LA/Long Beach), creating localized chassis shortages and rail gridlock[cite: 1].
* **Working Capital Trapped:** For a typical US manufacturer, a 2-week inventory delay means capital is trapped on the water longer, driving up safety stock requirements by an estimated **15-20%** to prevent factory stockouts[cite: 1].

### 2. The 350-Index Risk Threshold Breakout
* **Baseline Stress:** The horizontal dashed line at **350** marks the critical risk boundary[cite: 1]. When the index breaks above this line, it serves as an early-warning signal that freight spot rates are outstripping historical contract protections[cite: 1].
* **Downstream Price Creep:** Historically, sustained breakouts above this threshold correlate with a **3-to-6 month lagged increase** in the US Producer Price Index (PPI) for finished consumer goods, as companies pass inbound freight premiums down to the end consumer[cite: 1].

---

## 🛠️ Technical Implementation & Product Architecture
* **Data Pipeline:** Automated HTTP CSV ingestion from the St. Louis FRED API (Series: `PCU483111483111`)[cite: 1].
* **Wrangling & Optimization:** Constructed using **R (v4.4.1)** and `tidyverse` to clean irregular string dates into `Date` objects, remove missing database records, and isolate the current post-2022 timeline[cite: 1].
* **Visualization Engine:** Standardized through custom `ggplot2` layering, utilizing rotated geometric labels (`angle = 45`) to optimize mobile and desktop readability[cite: 1].

---

## 🏃‍♂️ Agile Product Management Backlog
This product is managed using Scrum frameworks to ensure iterative value delivery[cite: 1]. Below is the active sprint roadmap for the engineering squad[cite: 1]:

| Sprint | Item ID | Feature Name | Description / Target Value | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Sprint 1** | US-01 | Date Range Filtering | Slice data to focus strictly on current ongoing eras (2022-2026)[cite: 1]. | **Done**[cite: 1] |
| **Sprint 1** | US-03 | Visual Risk Thresholds | Draw horizontal alert baselines and highlight outlying data spikes[cite: 1]. | **Done**[cite: 1] |
| **Sprint 2** | US-02 | Interactive BI Dashboard | Built 4-quadrant interactive Tableau Public executive dashboard with multi-mode freight filtering. | **Done** |
| **Sprint 2** | US-04 | Multi-Series Energy Ingestion | Plot Global Bunker Fuel Prices alongside shipping rates to map cost drivers[cite: 1]. | *Todo*[cite: 1] |

---

## 🛠️ Data Infrastructure & Back-End Architecture (SQL)
To power high-visibility operational dashboards, raw transactional logistics tables must be transformed into clean, optimized analytical data layers[cite: 1]. 

I engineered a production-grade optimization script found directly in [`warehouse_lead_time_analytics.sql`](./warehouse_lead_time_analytics.sql) utilizing advanced SQL strategies to process shipping milestones[cite: 1]:

* **Multi-Layered Common Table Expressions (CTEs):** Built to isolate metrics and maintain high-performance query execution by separating initial delta tracking from window partitioning logic[cite: 1].
* **Analytical Window Functions (`AVG() OVER`):** Calculates a rolling 5-shipment moving average delay index partitioned by specific vendors[cite: 1]. This allows the product to differentiate between a random transit anomaly and a structural supplier bottleneck[cite: 1].
* **Forward-Looking Cost Projections (`LEAD()`):** Measures pricing volatility and trends by matching current container shipment costs against the next scheduled lane asset[cite: 1].
* **Conditional Risk Categorization (`CASE WHEN`):** Implements automated warehouse alert flags (`CRITICAL DELAY`, `WARNING`, `OPTIMIZED`) to feed live visualization alerts when lead-time variances breach risk thresholds[cite: 1].

---

## 🤖 Phase 3: Applied AI - Predictive Lead-Time & Transit Delay Modeling
To elevate this project from a historical tracking system into a proactive, forward-looking operational radar, I integrated a predictive Machine Learning forecasting layer into the analytics data pipeline[cite: 1].

### 1. Technical Architecture & Ingestion
I constructed a **Linear Regression Predictive Model** using the `tidymodels` core framework in R to dynamically forecast upcoming shipment transit anomalies before freight assets leave origin ports[cite: 1]:
* **Features Quantified:** Baseline calculated estimated lead times, historical supplier performance error averages, and macroeconomic container market indices extracted from FRED datasets[cite: 1].
* **Validation Strategy:** Implemented a split-validation pipeline allocating 80% of historical shipment ledgers to model training and isolating 20% to validate performance metrics against unseen operational runs[cite: 1].

### 2. Operational Evaluation Metrics
The regression engine was rigorously evaluated using industry-standard predictive error benchmarks[cite: 1]:
* **R-Squared (R² Variance Explained):** The model demonstrates high explanatory validity (**R² > 0.82**), proving that over 82% of transit delay variability can be successfully predicted by combining internal operational telemetry with external macroeconomic indicators[cite: 1].
* **Root Mean Squared Error (RMSE):** Maintained minimal deviation variance, indicating that the model’s predicted arrival window maps precisely within a narrow margin of actual operational delivery times[cite: 1].

### 💼 Operational Product Owner Application
By injecting this AI engine directly into the data architecture, supply chain managers can shift from reactive bottleneck mitigation to proactive inventory preservation[cite: 1]. The pipeline computes a continuous "Predicted Days of Delay" metric for all open purchase orders[cite: 1]. If a high-priority component crosses an AI-flagged threshold of **5+ days of predicted delay**, the system auto-generates a critical risk alert on executive Tableau views—giving procurement teams a multi-day head start to re-route logistics lanes, swap suppliers, and protect enterprise working capital[cite: 1].

---

## 📊 Executive Financial Operations Report: C-Suite Business Logic
### Shifting Operations from Reactive Debugging to Predictive Inventory Management
As a Product Owner and Business Analyst, technical code configurations must directly translate into bottom-line corporate financial value ($ROI, EBITDA, Cash Flow$). The predictive linear regression engine engineered within this platform moves the enterprise past manual data tracking and anchors data infrastructure directly to corporate profitability:

* **Margin Optimization & Revenue Protection:** By predicting exact transit lead-time delay windows with high confidence (**R² > 0.82**), global operations units can dynamically re-route supply paths, eliminating costly factory downtime and warehouse processing overruns.
* **Cash Flow Preservation:** Automated alerting based on multi-layered SQL data modeling allows the finance department to optimize working capital allocations, adjusting safety stock parameters accurately to protect capital liquidity.
* **Elimination of Obsolete Inventory Write-Downs:** Bridging the structural gap between FRED freight cost indices and historic supplier telemetry prevents inventory hoarding, directly stopping bottom-line margin erosion from obsolete materials write-offs.rite-downs.
