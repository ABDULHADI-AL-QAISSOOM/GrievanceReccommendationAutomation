

# Staff Evaluation Grievance Analysis Tool

**Designed π Hadi**

## 1. Overview

The **Staff Evaluation Grievance Analysis** tool is a web-based dashboard designed to assist HR analysts in objectively reviewing staff performance scores. By uploading raw evaluation data, the tool performs statistical comparisons against peers to determine if an employee’s score is consistent with the department's grading pattern or if it warrants reconsideration.

## 2. Data Privacy & Security

* **Client-Side Processing:** This tool runs entirely in the browser. No data is uploaded to any external server or cloud.
* **Confidentiality:** The Excel files selected remain on the local machine, ensuring full data privacy and compliance with internal data handling policies.

## 3. How It Works

The tool requires three standard Excel files (exported from the Annual Performance System - APS) corresponding to staff categories:

1. **Staff Professional**
2. **Staff Support**
3. **Staff Chief**

Once loaded, the user enters a specific **KFUPM ID**. The system then isolates that employee and performs a deep-dive analysis based on the logic detailed below.

---

## 4. The Analytical Logic

The core power of this tool lies in how it contextualizes a single employee's score against their peers. It does not look at the score in a vacuum; it uses **comparative analytics**.

### A. Peer Grouping (The Baseline)

The system automatically filters the dataset to create a "Peer Group."

* **Logic:** An employee is *only* compared against others who share the **Same Department** and the **Same Staff Category** (e.g., Professional vs. Professional).
* **Why:** This ensures fairness. Comparing a "Support" staff member in HR to a "Professional" in IT would yield inaccurate results due to different job complexities and grading curves.

### B. Inconsistency Flagging (The "Red Flag" System)

The tool scans the peer group to find logical contradictions between the **Overall Score (1–5)** and the **Total Calculation (0–100)**.

An employee is flagged as **"Inconsistent"** if:

1. **Similar Total, Lower Score:** A peer has a Total (100) within **±2 points** of the employee but received a *higher* Overall Score.
2. **Lower Total, Higher Score:** A peer has a Total (100) significantly lower (more than 2 points difference) but still received a *higher* Overall Score.

### C. Statistical Variation Check (Standard Deviation)

The tool checks if grading within the department is consistent.

* **Logic:** It groups all employees who received the *same score* (e.g., all employees who got a "3").
* **Calculation:** It calculates the **Standard Deviation (σ)** of their Total (100) values.
* **Threshold:** If the standard deviation is **≥ 10**, the group is flagged as **"High Variation."**
* **Meaning:** High variation means the manager is giving the same rating (e.g., "3") to employees with vastly different performance totals (e.g., one has 60/100, another has 90/100), indicating subjective or irregular grading.

### D. Distribution Outlier Check

This checks if the specific employee fits into the statistical "Normal Range" of their score group.

* **Logic:** `Mean (Average) ± 1 Standard Deviation`.
* **Application:** If the employee's Total (100) falls outside this range compared to others who got the same score, they are considered an outlier (e.g., they have the highest total among everyone who got a "3", yet they didn't get a "4").

---

## 5. The Recommendation Engine

The tool generates an automated recommendation text based on a strict set of rules.

### Case 1: "No Changes Recommended"

The system recommends maintaining the current score **ONLY IF** all the following conditions are met:

1. **Normal Department Trend:** The department average is between 2.0 and 3.0.
2. **Aligned Score:** The employee’s score is within ±1 point of the department average.
3. **No Inconsistencies:** The employee was not flagged in the peer comparison (Section 4B).
4. **Within Distribution:** The employee fits statistically within their score group (Section 4D).

### Case 2: "Reconsideration Recommended"

If **ANY** of the above conditions fail, the system recommends reconsidering the score. It dynamically generates a justification text citing the specific reasons:

* *"Several peers with lower Total (100) received higher overall scores..."*
* *"The employee’s Total (100) falls significantly outside the distribution..."*
* *"Significant variation was observed within score groups..."*
* *"The department’s average rating indicates irregular scoring patterns..."*

---

## 6. Visualization & Reporting

* **Histograms & Scatter Plots:** Visual aids are generated to show where the employee sits compared to the department curve.
* **Export to PDF:** The tool generates a clean, high-resolution PDF report including all charts, tables, and the automated recommendation, ready for signature and filing.

---

**Technical Stack:** HTML5, CSS3 (Inter Font), JavaScript (ES6), SheetJS (Excel Parsing), Chart.js (Visualization).

**License:** Internal Use Only.
**( designed π Hadi )**
