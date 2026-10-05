# 📊 Deloitte Data Analytics Virtual Experience (Forage)

## 📖 Project Overview
This repository contains my deliverables and findings from the **Deloitte Data Analytics Virtual Experience Program** hosted on Forage. The simulation involved stepping into the role of a Deloitte analyst to solve two critical business challenges for a global manufacturing client, Daikibo: operational downtime optimization and forensic pay equity analysis.

## 🛠️ Tools & Technologies
*   **Tableau:** Data visualization and interactive dashboard creation.
*   **Microsoft Excel:** Logical data classification and forensic analysis.
*   **JSON:** Telemetry data format.

---

## 📁 Task 1: Telemetry Data Analysis (Tableau)

### The Problem
Daikibo, a global manufacturing company, was experiencing significant operational downtime across its factories. The objective was to analyze telemetry data to identify where the downtime was most severe and which specific machines were causing it.

### Methodology
1.  **Data Ingestion:** Imported the raw `daikibo-telemetry-data.json` file into Tableau.
2.  **Calculated Field:** Engineered a custom calculated metric named `Unhealthy` to quantify downtime. Based on the reporting interval, each "unhealthy" status represented 10 minutes of potential downtime.
    *   *Formula used:* `IF [Status] = "unhealthy" THEN 10 ELSE 0 END`
3.  **Dashboard Construction:** Built a dual-chart interactive dashboard:
    *   **Top Chart:** Down Time per Factory (Bar chart).
    *   **Bottom Chart:** Down Time per Device Type (Bar chart).
4.  **Filtering:** Configured the Factory chart as a filter. Clicking a specific factory filters the bottom chart to show device-specific downtime for *that location only*.

### Key Findings
*   **Highest Risk Factory:** **Daikibo Factory Seiko** exhibited the highest operational downtime (480 minutes).
*   **Root Cause:** At the Daikibo Seiko facility, the **LaserWelder** was identified as the single point of failure, accounting for 100% of the recorded downtime (480 minutes). All other devices at this location reported zero downtime.

*(Placeholder: Insert your Tableau Dashboard screenshot here)*
`![Daikibo Dashboard](path-to-your-image.png)`

---

## 📁 Task 2: Forensic Technology Investigation (Excel)

### The Problem
The company required forensic support to investigate internal complaints regarding gender pay inequality across various factory locations and job roles.

### Methodology
Using the provided `Equality Table.xlsx`, I created a new column (`Equality class`) to systematically categorize employee compensation based on their `Equality Score` (ranging from -100 to +100, where 0 is ideal).

I utilized nested logical `IF` and `OR` statements in Excel to classify the scores into three distinct categories:
*   **Fair:** Scores between -10 and 10.
*   **Unfair:** Scores between -10 and -20, OR between 10 and 20.
*   **Highly Discriminative:** Scores less than -20 OR greater than 20.

*   *Excel Formula used:*
    ```excel
    =IF(OR(C2<-20, C2>20), "Highly Discriminative", IF(OR(C2<-10, C2>10), "Unfair", "Fair"))
