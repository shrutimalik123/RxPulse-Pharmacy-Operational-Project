# RxPulse: Pharmacy Operational Audit Dashboard 💊 📊

### **Executive Summary**
This project bridges **Clinical Pharmacy Operations** with **Data Analytics**. Using Power BI, I analyzed synthetic pharmacy workflow data (500 records) to identify bottlenecks in patient wait times, track revenue loss from claim rejections, and optimize staffing models based on peak-hour traffic.

The dashboard moves beyond simple reporting to provide **prescriptive analytics**—allowing managers to simulate "What-If" scenarios to reduce patient wait times.

---

## 🚀 Key Features & Insights

### 1. Staffing Optimization (Time Intelligence)
**The Problem:** Unpredictable patient influx leads to understaffing and long queues.
**The Solution:**
* Created a **Peak Hour Heatmap** using Power BI Matrix visuals and Conditional Formatting.
* **Insight:** Identified that **2:00 PM (14:00)** is the highest traffic hour, requiring an overlap of shift schedules.

### 2. Root Cause Analysis (AI Visuals)
**The Problem:** Average wait times were skewing high, but the cause was unclear.
**The Solution:**
* Implemented the **AI Decomposition Tree** to automatically break down wait times by `Status`, `Drug Class`, and `Pharmacist`.
* **Insight:** The bottleneck was not staff performance, but **"Pending Prior Authorizations"** for Pain Management prescriptions (Avg 39 mins vs. 15 mins baseline).

### 3. Performance Quadrants (Scatter Plot)
**The Problem:** Difficulty distinguishing between high-speed staff and those handling complex cases.
**The Solution:**
* Built a **Quadrant Scatter Plot** comparing *Script Volume* vs. *Average Wait Time*.
* **Insight:** Differentiated "High Volume/Low Wait" star performers from staff needing support with complex insurance rejections.

### 4. Financial Impact Analysis
**The Problem:** Rejected claims were not being quantified in terms of lost revenue.
**The Solution:**
* Calculated **Revenue at Risk** using DAX filter contexts.
* **Metric:** Identified **$800** in potential immediate revenue loss due to preventable claim rejections.

### 5. Scenario Planning (Parameters)
**The Problem:** Management needed to know the impact of efficiency improvements before committing resources.
**The Solution:**
* Built a dynamic **What-If Parameter** (0-50% improvement slider).
* Allows users to slide a toggle and instantly see how a 10% reduction in processing time would impact overall patient throughput.

---

## 🛠 Technical Stack

* **Tool:** Microsoft Power BI Desktop
* **ETL:** Power Query (Data cleaning, type casting, custom conditional columns)
* **Language:** DAX (Data Analysis Expressions) for calculated measures
* **Modeling:** Star Schema logic (Data separated into Fact and Dimension concepts)

### Key DAX Formulas Used

**Revenue at Risk:**
```dax
Revenue at Risk =
CALCULATE(
    SUM('Pharmacy_Data'[Copay]),
    'Pharmacy_Data'[Status] = "Rejected"
)
