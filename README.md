# UPI Analytics Executive Performance & Risk Intelligence Dashboard

<p align="left">
  <img src="https://img.shields.io/badge/Platform-Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white" alt="Excel Badge" />
  <img src="https://img.shields.io/badge/Architecture-Pivot%20Engine%20%26%20Data%20Modeling-0078D4?style=for-the-badge&logo=microsoftexcel&logoColor=white" alt="Pivot Badge" />
  <img src="https://img.shields.io/badge/Domain-FinTech%20%26%20Payments-0A2540?style=for-the-badge&logo=stripe&logoColor=white" alt="FinTech Badge" />
  <img src="https://img.shields.io/badge/Security-Risk%20%26%20Fraud%20Surveillance-D9381E?style=for-the-badge" alt="Fraud Badge" />
</p>

---

## Executive Summary

The **Unified Payments Interface (UPI) Analytics Dashboard** provides end-to-end transactional visibility, settlement reliability analysis, and fraud surveillance across 5,02,880 digital financial operations totaling ₹44.25 Crores in gross transaction value. Built on enterprise data architecture principles, this reporting framework translates raw telemetry—spanning multi-bank switching nodes, client application endpoints, demographic strata, and merchant networks—into executive decision-making intelligence.

The operational core balances top-line gross merchandise value tracking with granular operational health monitoring, analyzing system success ratios ($91.00\%$), unrecoverable network failure rates ($7.00\%$), settlement latencies ($1.988\%$), and flagged suspicious fraud patterns across $17,089$ transactional payloads.

---

## Dashboard Architecture & Visual Overview

The operational cockpit features a filter-driven control plane interfacing directly with dynamic data presentation layers:

<img width="1109" height="891" alt="70cd370c-1a8d-4f60-ae58-f9cc9bbcb597" src="https://github.com/user-attachments/assets/27797101-5315-44c3-8919-e991a9b61912" />


### Structural Breakdown:
* **Global Slicer Control Plane (Left Lateral Rail):** Real-time multi-attribute filtering across Gender, Transaction Type, Merchant Entity, Merchant Category, Geographic State, Core UPI Application, Age Cohort, Payment Channel Mode, and City Hubs.
* **Top-Level KPI Tier:** Six high-impact operational metrics showing gross volume, capital turnover, incentive cost allocations, infrastructure throughput efficiency, and security alerting thresholds.
* **Temporal & Behavioral Performance Strip (Middle-Tier):** Daily cyclical trends, application distribution ratios, and settlement status breakdowns.
* **Ecosystem & Routing Cluster (Mid-Tier Central):** Bank server load distributions, regional state revenue performance maps, and transaction type breakdown matrices.
* **Temporal Load Matrix (Core Heatmap):** Day-of-week by 24-hour heat indexing showing high-concurrency payment activity.
* **Demographic & Geographic Segmentation (Bottom Tier):** Hourly volume distributions, Age Group cross-tabulated with Client Device OS adoption, and Top 10 Revenue-Producing Metropolitan Markets.

---

## High-Level Key Performance Indicators (KPIs)

| Metric | Recorded Value | Operational Benchmark | Business Context |
| :--- | :--- | :--- | :--- |
| **Gross Processed Transactions** | `5,02,880` | High Concurrency | Absolute count of switched payment requests within the reporting cycle. |
| **Gross Processed Value (INR)** | `₹ 44.25 Cr` | Top-Line Revenue Base | Cumulative capital transferred across P2P, P2M, and utility bill channels. |
| **Total Cashback Disbursed** | `₹ 34.63 L` | Incentive Expense | Acquisition and gamification rebate spend; represents $0.78\%$ of gross volume. |
| **System Success Rate** | `91.00%` | SLA Benchmark ($\ge 90\%$) | Core network stability rate across acquiring banks and payer authentication nodes. |
| **Suspected Fraud Flags** | `17,089` | Risk Threshold ($\le 3.5\%$) | Transactions flagged by real-time risk score thresholds requiring investigation. |
| **Pending / Failed / Refunded Ratios** | `1.99% / 7.00% / 0.01%` | Technical Degradation | Key breakdown of transactions requiring server re-query, auto-reversal, or gateway retry. |

---

## Dataset Schema & Field Definitions

The underlying analytical model integrates 24 raw transaction attributes:

```
Transaction_ID | Transaction_Date | Day | Transaction_Time | Hour | UPI_App
Customer_ID | Age_Group | Gender | State | City | Merchant_Name
Merchant_Category | Transaction_Type | Payment_Mode | Bank_Name | Amount_INR | Cashback_INR
Transaction_Fee_INR | Status | Failure_Reason | Device_OS | Risk_Score | Is_Suspected_Fraud
```

### Data Dictionary

| Column Name | Data Type | Analytical Classification | Business Context & Logical Usage |
| :--- | :--- | :--- | :--- |
| `Transaction_ID` | String / Alphanumeric | Dimension (Primary Key) | Unique alphanumeric reference hash identifying the individual transaction payload. |
| `Transaction_Date` | Date (`YYYY-MM-DD`) | Temporal Dimension | Gregorian settlement date applied for longitudinal day-on-day trending. |
| `Day` | Text | Temporal Dimension | Day of the week (Monday through Sunday) utilized in cyclical load modeling. |
| `Transaction_Time` | Time (`hh:mm:ss`) | Temporal Dimension | Clock timestamp marking the exact arrival time at the payment switch interface. |
| `Hour` | Integer / Formatted String | Temporal Cohort | 24-hour normalized block (`00` through `23`) driving diurnal velocity analysis. |
| `UPI_App` | Categorical String | Ecosystem Entity | Client application initiating payment (PhonePe, Google Pay, Paytm, BHIM, etc.). |
| `Customer_ID` | String / Alphanumeric | User Dimension | Unique persistent customer entity token to monitor customer lifetime usage patterns. |
| `Age_Group` | Categorical Bracket | Demographic Dimension | Demographic strata (`18-24`, `25-34`, `35-44`, `45-54`, `55+`) for adoption tracking. |
| `Gender` | Categorical String | Demographic Dimension | User demographic identity (`Male`, `Female`, `Other`) for market penetration audits. |
| `State` | Geographic String | Regional Dimension | First-tier administrative territory in India governing regional performance. |
| `City` | Geographic String | Localized Dimension | Metropolitan or urban commercial hub where transaction was initiated. |
| `Merchant_Name` | String | Commercial Entity | Receiving commercial merchant, aggregator, or enterprise receiver account. |
| `Merchant_Category` | Categorical String | Vertical Segment | Industry classification code (e.g., Entertainment, Fuel, Utilities, Dining). |
| `Transaction_Type` | Categorical String | Protocol Classification | Payment rail flow: `P2M`, `P2P`, `Bill Payment`, `Online Shopping`, `Recharge`. |
| `Payment_Mode` | Categorical String | Interface Modality | Routing channel: `QR Scan`, `UPI ID`, `Mobile Number`, `Bank Account Intent`. |
| `Bank_Name` | Categorical String | Infrastructure Entity | Remitter or beneficiary core banking system provider processing the balance transfer. |
| `Amount_INR` | Numeric (Decimal) | Financial Measure | Gross monetary value transferred per transaction in Indian Rupees. |
| `Cashback_INR` | Numeric (Decimal) | Financial Measure | Direct promotional credit paid out to the user account post-completion. |
| `Transaction_Fee_INR`| Numeric (Decimal) | Financial Measure | Aggregator network fee or interchange charged per clearing event. |
| `Status` | Categorical String | Operational State | Execution status code: `Success`, `Failed`, `Pending`, `Refunded`. |
| `Failure_Reason` | Categorical String | Diagnostic Flag | Bank server timeouts, insufficient balances, security lockouts, network drop. |
| `Device_OS` | Categorical String | Client Telemetry | Client device architecture (`Android` vs. `iOS`) capturing platform split. |
| `Risk_Score` | Numeric (Normalized) | Algorithmic Output | Heuristic security rating measuring behavioral deviations and network risk. |
| `Is_Suspected_Fraud`| Boolean (`0`/`1`) | Risk Measure | Binary classification triggered when risk criteria or blacklists are breached. |

---

## Detailed Chart & Visual Component Analysis

### 1. Transaction Volume & Amount Over Time (Daily Velocity)
* **Visual Structure:** Dual-tone temporal area-line chart plotting calendar day progression against processed INR values.
* **Observed Pattern:** High initial volatility stabilizing into cyclical mid-month surges, with peak transaction volume registering around major national settlement and salary disbursement days ($₹ 1.82\text{ Cr}$ daily peaks).
* **Business Takeaway:** Cash-flow liquidity and bank API rate-limits must be dynamically provisioned to handle $\sim 40\%$ load spikes during salary and billing cycles (1st to 7th, and 28th to 31st of each month).

### 2. Market Share Distribution by Client UPI Applications
* **Visual Structure:** 3D Exploded Donut/Pie distribution detailing application origin share.
* **Observed Metrics:**
  * **PhonePe:** $49.8\%$ (Dominant core payment hub)
  * **Google Pay:** $21.3\%$ (Strong second-tier market penetration)
  * **Paytm:** $14.3\%$ (Steady commercial footprint)
  * **Amazon Pay:** $4.9\%$
  * **BHIM:** $3.8\%$
  * **CredPay:** $3.0\%$
  * **WhatsApp Pay:** $2.9\%$
* **Business Takeaway:** Market duopoly remains entrenched: PhonePe and Google Pay collectively manage $71.1\%$ of transaction origins. Merchant routing infrastructure must maintain dedicated high-bandwidth gateway pipes specifically optimized for PhonePe and Google Pay switch protocols.

### 3. Gateway Settlement Status & Network Reliability
* **Visual Structure:** Slice-distribution donut chart segmenting execution outcomes.
* **Observed Distribution:**
  * **Success:** $91.05\%$
  * **Failed:** $6.95\%$
  * **Pending:** $2.01\%$
  * **Refunded:** $0.04\%$
* **Business Takeaway:** The $6.95\%$ hard failure rate and $2.01\%$ lingering pending rate account for approximately $₹ 3.96\text{ Cr}$ in stalled or lost transaction volume. Automated server timeouts, NPCI clearing latency, and insufficient fund errors require predictive routing to failover bank gateways.

### 4. Core Banking Partner Performance Distribution
* **Visual Structure:** Horizontal ranked bar chart indexing monetary throughput across clearing banks.
* **Observed Performance:**
  * **HDFC Bank:** $₹ 58,923,758$ ($\sim ₹ 5.89\text{ Cr}$)
  * **State Bank of India (SBI):** $₹ 58,374,952$ ($\sim ₹ 5.84\text{ Cr}$)
  * **Kotak Mahindra Bank:** $₹ 55,810,254$ ($\sim ₹ 5.58\text{ Cr}$)
  * **Canara Bank:** $₹ 55,161,837$ ($\sim ₹ 5.52\text{ Cr}$)
  * **ICICI Bank:** $₹ 55,083,265$ ($\sim ₹ 5.51\text{ Cr}$)
  * **Axis Bank:** $₹ 54,929,186$ ($\sim ₹ 5.49\text{ Cr}$)
  * **Bank of Baroda:** $₹ 53,145,382$ ($\sim ₹ 5.31\text{ Cr}$)
  * **Punjab National Bank (PNB):** $₹ 51,054,000$ ($\sim ₹ 5.11\text{ Cr}$)
* **Business Takeaway:** Transaction loads are balanced across top private and public entities, with HDFC and SBI processing the highest volume. Downstream integrations must establish dynamic circuit-breakers to reroute traffic automatically if SBI or HDFC core banking systems slow down.

### 5. Transaction Value by Flow Classification (Transaction Type)
* **Visual Structure:** Horizontal category bar chart quantifying transaction types.
* **Observed Segmentation:**
  * **P2M (Person-to-Merchant):** $₹ 18.88\text{ Cr}$ (Highest category)
  * **P2P (Person-to-Person):** $₹ 8.77\text{ Cr}$
  * **Bill Payment:** $₹ 6.17\text{ Cr}$
  * **Online Shopping:** $₹ 3.83\text{ Cr}$
  * **Mobile / DTH Recharge:** $₹ 3.54\text{ Cr}$
  * **Subscription Services:** $₹ 1.79\text{ Cr}$
  * **Wallet Transfer:** $₹ 1.28\text{ Cr}$
* **Business Takeaway:** Over $42.6\%$ of monetary volume is driven by offline and online commercial merchant points (`P2M`), outpacing individual transfers (`P2P`). This highlights an acceleration in commercial transaction acceptance over personal money movement.

### 6. Temporal Load Heatmap: Transaction Amount by Hour and Day
* **Visual Structure:** Matrix heatmap mapping 7 Days (`Sunday` to `Saturday`) against 24 Hours (`00` to `23`).
* **Observed Thermal Patterns:**
  * **Dormant Window (`00:00` to `07:00`):** Characterized by low activity across all days.
  * **Ramping Phase (`08:00` to `11:00`):** Steady increase in commercial and utility traffic.
  * **Peak Traffic Band (`12:00` to `15:00` and `18:00` to `21:00`):** Deep green clusters indicating high transaction density corresponding to lunch hours, retail purchasing, and evening leisure spending.
* **Business Takeaway:** Scheduled database batch runs, bank recon jobs, and structural system maintenance must be restricted to the low-traffic window between `02:00` and `05:00` to protect core payment uptime during high-value evening windows.

### 7. Demographic Cross-Tabulation: Age Cohort vs. Device OS
* **Visual Structure:** Grouped column visual cross-referencing age brackets against client operating systems (`Android` vs. `iOS`).
* **Observed Distribution:**
  * The `25-34` age demographic forms the core revenue-generating cohort ($₹ 13.81\text{ Cr}$ Android, $₹ 3.05\text{ Cr}$ iOS), followed by the `35-44` bracket ($₹ 9.13\text{ Cr}$ Android, $₹ 2.00\text{ Cr}$ iOS).
  * Android users account for approximately $81.9\%$ of total monetary value, while iOS represents $18.1\%$.
* **Business Takeaway:** Product feature roadmaps, SDK updates, and in-app checkout optimizations should prioritize Android performance, while high-ticket luxury promotions and subscription services should be focused on the higher average order value (AOV) typical of the iOS demographic.

### 8. Geographic Concentration: State and Top 10 Cities
* **Visual Structure:** Geographical choropleth map alongside a sorted bar chart of the top 10 municipal hubs.
* **Observed Metrics:**
  * **Top Performing States:** Maharashtra ($₹ 4.54\text{ Cr}$), Karnataka ($₹ 4.51\text{ Cr}$), Delhi ($₹ 4.48\text{ Cr}$), Rajasthan ($₹ 4.42\text{ Cr}$), Uttar Pradesh ($₹ 4.41\text{ Cr}$).
  * **Top Municipalities:** Kolkata ($₹ 14.69\text{ Cr}$), Hyderabad ($₹ 14.69\text{ Cr}$), Howrah ($₹ 14.71\text{ Cr}$), Durgapur ($₹ 14.29\text{ Cr}$), Bengaluru ($₹ 11.32\text{ Cr}$), Ahmedabad ($₹ 11.01\text{ Cr}$).
* **Business Takeaway:** High revenue concentration across key manufacturing and IT corridors underscores the need for regionalized edge-caching nodes in eastern, western, and southern data centers to maintain low gateway latency.

---

## Business Case Study: Strategic Queries & Solutions

### Query 1: Payment Success Optimization
* **Business Problem:** The dashboard records a $7.00\%$ failure rate and a $1.988\%$ pending status rate, impacting approximately $₹ 3.96\text{ Cr}$ in transactions and creating customer friction.
* **Analytical Finding:** Correlating failures against bank routing shows that core public sector banking servers experience elevated latency between 18:00 and 21:00, leading to NPCI network timeout codes.
* **Actionable Solution:** 
  1. Implement client-side smart dynamic routing that monitors bank API response health every 30 seconds.
  2. If an issuing bank's success rate falls below $85\%$, proactively prompt users during the checkout phase to select an alternate bank account or use a secondary balance rail.

### Query 2: Marketing ROI & Cashback Allocation Strategy
* **Business Problem:** Cashback disbursements totaled $₹ 34.63\text{ Lakhs}$, representing an operational expense line item that requires clear return on investment.
* **Analytical Finding:** The `25-34` age cohort generates $38.08\%$ of total transaction value ($₹ 16.85\text{ Cr}$) with higher retention rates, whereas the `55+` cohort generates only $4.98\%$ ($₹ 2.20\text{ Cr}$) despite receiving equivalent per-transaction cashback rates.
* **Actionable Solution:**
  1. Restructure incentive distribution: Reduce blanket transaction cashbacks by $50\%$ for routine utility payments.
  2. Reallocate these marketing funds into gamified cashback rewards for high-margin `P2M` retail transactions and merchant subscriptions focused on the high-velocity `18-24` and `25-34` demographics.

### Query 3: Real-Time Fraud Mitigation & Risk Profiling
* **Business Problem:** $17,089$ transactions were flagged as suspected fraud, representing roughly $3.4\%$ of total traffic.
* **Analytical Finding:** High-risk scores are heavily concentrated in rapid succession P2P wallet transfers occurring during late-night hours (`01:00` to `04:00`) on newly bound SIM devices.
* **Actionable Solution:**
  1. Implement automated step-up authentication (biometric confirmation or app-bound OTP challenges) for any transaction exceeding $₹ 2,000$ initiated between `00:00` and `05:00`.
  2. Enforce a mandatory 2-hour velocity ceiling ($₹ 5,000$ aggregate cap) for devices undergoing a new UPI registration or SIM-swap event within the previous 24 hours.

---

## Technical Project Setup & Requirements

1. **Software Platform:** Microsoft Excel 2016, 2019, 2021, or Microsoft 365.
2. **Data Structure:** Single interconnected workbook leveraging structured Table references, multi-layer Pivot Caches, and dynamic reporting ranges.
3. **Display Configuration:** Optimized for standard widescreen landscape monitors ($1920 \times 1080$ resolution) with Gridlines disabled under the View tab for presentation mode.

---

<div align="center">
  <p><b>Developed by Sourish Dey</b></p>
  <p>Payments Infrastructure & Financial Data Analytics</p>
</div>
