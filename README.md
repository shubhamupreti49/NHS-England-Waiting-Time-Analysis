# NHS-England-Waiting-Time-Analysis
The NHS is failing despite record hiring. Integrating workforce and outcome data in R, this project exposes a critical "Efficiency Paradox." London, despite having the highest staffing density, suffers the worst wait times. The findings prove the crisis is structural: more resources alone cannot fix a broken process.
# The Efficiency Gap: A Forensic Analysis of the NHS Crisis

**Author:** Shubham Upreti  
**Date:** December 2025  
**Tech Stack:** R (Tidyverse, Janitor, Lubridate, GGplot2)

## 🚨 The Executive Summary
The UK National Health Service (NHS) is facing a historic collapse. Since 2020, the patient waiting list has tripled, leaving over **7 million people** stranded in a queue defined by chronic pain and delayed diagnoses.

This project interrogates a critical economic assumption: **Does increasing the workforce automatically reduce waiting times?**

Using longitudinal workforce data and regional patient outcomes, this analysis exposes a **"Resource-Performance Gap."** The findings destroy the narrative that the crisis is purely a lack of funding—proving instead that it is a failure of structure.

---

## 📉 Key Findings

### 1. The London Paradox (Resource != Performance)
Conventional wisdom suggests that more doctors equal faster care. My analysis proves the opposite in London.
* **Input:** London possesses the **highest staffing density** in the NHS (76 FTE per 1,000 patients).
* **Output:** Yet, it delivers the **worst performance**, with **42.5%** of patients waiting beyond the 18-week crisis threshold.
* **Conclusion:** High resource intensity has decoupled from operational throughput.

### 2. The Efficiency Frontier
Conversely, the **North East & Yorkshire** region demonstrates "Lean Performance." Despite operating with **19% fewer staff** (64 FTE per 1,000 patients) than London, they achieve significantly better patient throughput.

### 3. The Administrative Creep
A longitudinal stream graph analysis (2010–2025) reveals that while workforce numbers have risen, a significant portion of this growth correlates with **administrative expansion** rather than direct clinical capacity.

---

## 🛠️ Methodology & Technical Approach

This analysis integrates three distinct datasets comprising over **260,000 records**.

### 1. Advanced Data Wrangling (The "Granularity Mismatch")
A major technical hurdle was the mismatch between **Workforce Data** (Regional level) and **Patient Outcomes** (Provider level).
* **Solution:** I engineered a custom **Regex (Regular Expression)** pipeline to map hundreds of inconsistent local provider names (e.g., specific hospital trusts) to the 7 standardized NHS Regions.
* **Pivoting:** Transformed "wide" outcome data (100+ columns of wait buckets) into a "long" tidy format for granular distribution analysis.

### 2. Visualization Strategy
* **The Crisis Curve:** `geom_area` to visualize the post-2020 structural break.
* **Efficiency Quadrants:** A scatterplot using `geom_vline` and `geom_hline` to partition regions into "Lean Performers" vs. "Resource Paradox" clusters.
* **Workforce Composition:** A stream graph to track the ratio of clinical vs. non-clinical staff over 15 years.

---

## 📂 Data Structure

| File Name | Description | Dimensions |
| :--- | :--- | :--- |
| `NHS_cleaned.csv` | Longitudinal referral timeseries (2007-2025) | 240 x 45 |
| `RTT_NHS_March.csv` | Regional wait-time snapshot (March 2025) | 185k x 121 |
| `NHS_Workforce_Statistics.csv` | Full-Time Equivalent (FTE) staffing numbers | 82k x 7 |

---

## 📊 Visuals
Make sure to check out the animated plots that i generated in R studio using gganimate.

---

## ⚖️ Ethical Considerations
**The Ecological Fallacy:** This analysis relies on regional averages. While statistically necessary for macro-analysis, it risks masking the "long tail" of acute suffering faced by individual patients. A region labeled "efficient" may still contain thousands of patients in chronic pain.

## 🤖 AI Use Statement
This project utilizes a **Hybrid Intelligence** approach.
* **Human:** Hypothesis generation, statistical logic, narrative framing, and final code validation.
* **AI (Gemini):** Used to generate complex Regex patterns for provider-to-region mapping and to refine `ggplot2` aesthetic themes. All code was manually debugged and verified.

---

## 🚀 How to Run
1. Clone this repo.
2. Open `NHS_Efficiency.Rproj`.
3. Run `final_analysis.qmd` to render the full report.
