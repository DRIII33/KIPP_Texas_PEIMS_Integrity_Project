### **KIPP Texas PEIMS Integrity Project**

**Role Alignment:** State Reporting Data Specialist, Regional Support and Leadership Department

**Project Goal:** To design, build, and deploy an automated data pipeline and auditing framework to proactively ensure the accuracy and compliance of student attendance and special program data (PEIMS/SAAH) for KIPP Texas Public Schools, specifically targeting Foundation School Program (FSP) funding risk for the Regional Support and Leadership Department.

**Business Context (as of December 2025):** Texas schools are transitioning to **Six-Week Attendance Reporting (HB 2)** for FSP funding. This heightened frequency requires robust, continuous data integrity checks. KIPP Texas, undergoing rapid growth, faces the challenge of identifying and correcting high-stakes reporting errors (e.g., Chronic Absenteeism, Special Education (SPED) Service Shortfalls) before the critical mid-year PEIMS submission.

**Skills Demonstrated & Deliverables:**

| Tool/Language | Deliverable | State Reporting Responsibility |
| :--- | :--- | :--- |
| **Python / Google Colab** | Synthetic Data Generation & ETL Notebook | *Data Extraction & Wrangling;* Creating realistic, auditable datasets that mimic core PEIMS data elements (attendance, SPED status). |
| **SQL / BigQuery** | Optimized Audit Views (`v_Attendance_Audit`, `v_Special_Programs_Compliance`) | *Data Integrity & Auditing;* Developing complex SQL logic to flag compliance breaches (e.g., \>10% chronic absenteeism, SPED minutes deficit) and reduce reporting latency. |
| **Looker Studio** | Data Integrity Dashboard | *Reporting & Insight Generation;* Visualizing high-risk students and campuses for the Regional Support team, prioritizing intervention based on funding impact. |
| **Google Docs/Sheets** | Comprehensive Project Documentation | *Communication & Process Improvement;* Documenting data standards, audit methodologies, and remediation steps for end-users. |

**Key Project Achievements:**

  * Established a **data-driven audit process** that maps directly to the **SAAH** and **TSDS PEIMS** standards.
  * Engineered **optimized BigQuery views** that pre-calculate compliance ratios and error flags, eliminating the need for complex blending/calculations in the visualization layer.
  * Provided an actionable tool for the Regional Support team to **mitigate financial risk** associated with inaccurate state data reporting.

-----

## 📁 GitHub README.md

This file serves as the main entry point for the repository, guiding a reviewer through the project's logic and deliverables.

### **README.md**

# KIPP\_Texas\_PEIMS\_Integrity\_Project

A full-stack data analytics and compliance project designed to proactively audit and ensure the integrity of PEIMS (Public Education Information Management System) data, focusing on Student Attendance Accounting (SAAH) and Special Programs compliance for KIPP Texas Public Schools.

This project simulates the core responsibilities of a **State Reporting Data Specialist** by building a reproducible audit pipeline using Google's cloud ecosystem and open-source data tools.

-----

## 🎯 1. Project Overview & Business Problem

**Business Scenario:** KIPP Texas Public Schools, under the direction of the Regional Support and Leadership Department, needs to prepare for the rigorous new **Six-Week Attendance Reporting (HB 2)** requirements for the 2025-2026 school year. Inaccurate reporting of student attendance codes and special program service documentation (especially for SPED) pose a direct threat to Foundation School Program (FSP) funding.

**The Solution:** This project delivers a **Data Integrity Framework** that automatically detects and visualizes these compliance and funding risks across all KIPP Texas campuses, allowing Regional Support and Leadership to prioritize interventions before final PEIMS submissions.

-----

## 🛠️ 2. Technical Stack

| Tool/Language | Use Case |
| :--- | :--- |
| **Python** (Pandas, NumPy) | Synthetic data generation, initial ETL, and data structure validation. (Executed in Google Colab) |
| **SQL** | Developing optimized, complex audit views (`CREATE OR REPLACE VIEW`) in BigQuery. |
| **Google BigQuery** | Cloud data warehousing, high-performance query execution, and data source for Looker Studio. **Project ID: `driiiportfolio`** |
| **Google Colab** | Hosting and executing the Python notebook for reproducibility and easy sharing. |
| **Looker Studio** | Final data visualization and interactive dashboard creation for leadership reporting. |
| **GitHub** | Version control, documentation, and project organization. |

-----

## 📦 3. Deliverables and File Structure

The repository is structured to guide the user through the data lifecycle, from generation to visualization.

```
KIPP_Texas_PEIMS_Integrity_Project/
├── 0_Documentation/
│   └── 0_Project_Documentation_State_Reporting_Specialist.docx (Full methodology and analysis)
├── 1_Source_Data/
│   └── 1_synthetic_peims_attendance_data.csv (Raw data output from Python)
├── 2_Code_Python/
│   └── 2_Data_Wrangling_PEIMS_Attendance_Colab.ipynb (Colab notebook for data generation/loading)
├── 3_Code_SQL/
│   ├── 3a_SQL_View_v_Attendance_Audit.sql (BigQuery view for Chronic Absenteeism/SAAH flags)
│   └── 3b_SQL_View_v_Special_Programs_Compliance.sql (BigQuery view for SPED service minute shortfall)
├── 4_Deliverables/
│   └── 4_Looker_Studio_Dashboard_Link.txt (Link to the final visualization dashboard)
└── README.md (This file)
```

-----

## ⚙️ 4. Key Components and Audit Logic

### Attendance Audit (3a\_SQL\_View\_v\_Attendance\_Audit.sql)

This view flags two high-stakes compliance risks:

1.  **Chronic Absenteeism Flag:** Identifies students with an attendance rate of **\< 90% (Absenteeism Rate $\ge 10\%$)**, which is a key indicator of state accountability risk and potential FSP funding loss.
2.  **SAAH Code Audit Flag:** Detects non-compliant attendance codes (e.g., using SAAH code '0' (Not in Membership) without proper withdrawal/enrollment status, or misusing 'Z' (Remote Asynchronous) for highly absent students).

### Special Programs Compliance (3b\_SQL\_View\_v\_Special\_Programs\_Compliance.sql)

This view directly supports special population reporting integrity:

1.  **SPED Compliance Ratio:** Calculates the ratio of **Actual Service Minutes to Required Service Minutes**.
2.  **Service Shortfall Flag:** Categorizes students where the ratio is **less than 1.0**, indicating a deficit in services that could result in non-compliance with the student’s Individualized Education Program (IEP) and lead to adverse audit findings.

-----

## 🚀 5. Getting Started

1.  **Data Generation:** Open the `2_Data_Wrangling_PEIMS_Attendance_Colab.ipynb` file in Google Colab, execute the Python script to generate the synthetic data, and export the CSV file (`1_synthetic_peims_attendance_data.csv`).
2.  **Data Loading:** The Python script includes a function to load the generated CSV directly into **BigQuery** under `driiiportfolio.peims_audit.raw_attendance_data` (requires BigQuery API to be enabled).
3.  **Audit View Creation:** Execute the SQL code in `3a_SQL_View_v_Attendance_Audit.sql` and `3b_SQL_View_v_Special_Programs_Compliance.sql` within your BigQuery environment to establish the optimized audit views.
4.  **Reporting:** Connect the two BigQuery views as data sources to Looker Studio to create the final data integrity dashboard.
