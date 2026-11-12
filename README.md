# patient-readmission-dashboard
# 🏥 Healthcare Readmission Analytics

### 📊 Turning Healthcare Data into Actionable Business Insights

An end-to-end **Data Analytics project** focused on understanding hospital readmission patterns using Python, SQL, and Power BI. This project analyzes historical healthcare data to explore patient demographics, hospital utilization, medication changes, and readmission within 30 days.

![Python](https://img.shields.io/badge/Python-Data%20Analysis-blue?logo=python)
![SQL](https://img.shields.io/badge/SQL-MySQL-orange?logo=mysql)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)
![Project](https://img.shields.io/badge/Project-Data%20Analytics-success)

---

## 🌟 Project Highlights

- 📊 Analyzed **101,766 hospital encounters**.
- 🐍 Used Python and Pandas for data cleaning and exploratory data analysis.
- 🗄️ Used SQL/MySQL for data querying and analysis.
- 📈 Developed a multi-page interactive Power BI dashboard.
- 🧮 Created DAX measures for KPIs and readmission analysis.
- 💡 Identified patterns in hospital stay, emergency visits, and readmission categories.
- 🎯 Presented findings through visualizations and business recommendations.

## 🎯 Business Problem

Hospital readmissions can increase healthcare costs and put additional pressure on hospital resources. Understanding readmission patterns can help identify areas that deserve further investigation.

This project explores the following business questions:

- What is the 30-day readmission rate?
- How do readmission patterns vary across patient demographics?
- How does average hospital stay differ by readmission category?
- Are emergency visits associated with different readmission patterns?
- How do readmission rates vary by medication-change status?
- How do discharge outcomes relate to readmission patterns?

## 📂 Dataset

**Dataset:** Diabetes 130-US Hospitals for Years 1999–2008

**Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/296/diabetes+130-us-hospitals+for+years+1999-2008)

| Dataset Detail | Information |
|---|---|
| 🏥 Hospitals | 130 US hospitals |
| 📅 Period | 1999–2008 |
| 📊 Encounters | 101,766 |
| 📑 Original columns | 50 |
| 🎯 Target | Readmission within 30 days |
| 📌 Categories | `NO`, `>30`, `<30` |

The dataset contains patient encounter information, demographic details, diagnoses, medications, hospital stay, and readmission status.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| 🐍 Python | Data analysis and preparation |
| 🐼 Pandas | Data cleaning and manipulation |
| 🔢 NumPy | Numerical operations |
| 📓 Jupyter Notebook | Exploratory analysis |
| 🗄️ SQL / MySQL | Querying and aggregating data |
| 🔄 Power Query | Data transformation |
| 📊 Power BI | Interactive dashboard development |
| 🧮 DAX | KPI calculations and analytical measures |
| 🐙 GitHub | Version control and documentation |

## 🔄 Project Workflow

**1. Data Understanding 🔍**
- Loaded and explored the dataset.
- Examined columns, data types, and distributions.
- Identified missing values and coded categories.

**2. Data Cleaning 🧹**
- Investigated missing data.
- Prepared fields for analysis.
- Reviewed categorical values and mapping information.
- Prepared the dataset for further analysis.

**3. Exploratory Data Analysis 📈**
- Analyzed readmission categories.
- Explored demographic patterns.
- Compared hospital stays and emergency visits.

**4. SQL Analysis 🗄️**
- Queried healthcare records.
- Used aggregations to summarize data.
- Compared categories to answer business questions.

**5. Power BI Dashboard 📊**
- Created KPI cards and DAX measures.
- Designed charts and slicers.
- Added interactive page navigation.
- Organized insights across four dashboard pages.

**6. Business Insights 💡**
- Interpreted observed readmission patterns.
- Identified areas for further investigation.
- Developed recommendations based on the analysis.

## 📊 Dashboard Overview

### 🏠 Page 1: Healthcare Overview
**KPIs**
- Total Encounters
- Unique Patients
- 30-Day Readmission Rate
- Average Hospital Stay

**Visualizations**
- Encounters by readmission category
- Encounters by age group

### 👥 Page 2: Patient Demographics
**Visualizations**
- Encounters by gender
- Encounters by race
- Gender and race slicers

### 🏨 Page 3: Hospital Utilization & Clinical Insights
**Visualizations**
- Average hospital stay by readmission category
- Average emergency visits by readmission category

### 💊 Page 4: Clinical & Discharge Insights
**Visualizations**
- 30-day readmission rate by medication-change status
- 30-day readmission rate by discharge disposition

The dashboard includes interactive filters, KPI cards, category comparisons, and page navigation to make the analysis easier to explore.

## 📌 Key Findings

### 🏥 Average Hospital Stay

| Readmission Category | Average Stay |
|---|---:|
| No readmission (`NO`) | 4.25 days |
| Readmission after 30 days (`>30`) | 4.50 days |
| Readmission within 30 days (`<30`) | 4.77 days |

**Insight:** Encounters followed by readmission within 30 days had the highest average hospital stay in the current dashboard.

### 🚑 Average Emergency Visits

| Readmission Category | Average Emergency Visits |
|---|---:|
| No readmission (`NO`) | 0.11 |
| Readmission after 30 days (`>30`) | 0.28 |
| Readmission within 30 days (`<30`) | 0.36 |

**Insight:** The `<30` category had the highest average emergency visits among the three categories.

### 🎯 30-Day Readmission Rate

The current analysis reports an approximate **11.16% 30-day readmission rate**, calculated using encounters classified as `<30` divided by all included encounters.

## 💡 Business Recommendations

- 🏥 Review discharge planning and post-discharge follow-up for groups with higher observed readmission rates.
- 🚑 Investigate the relationship between emergency visits and readmission patterns.
- 💊 Compare readmission rates across medication-change categories.
- 📋 Use readable discharge descriptions instead of numeric category IDs.
- 📊 Monitor clearly defined KPIs to support further healthcare data analysis.

These recommendations identify areas for investigation; the analysis does not establish causation.

## 🧮 Key Power BI Measures

### Total Encounters

```dax
Total Encounters =
COUNTROWS('healthcare_readmission_analytics readmissions')
```

### Unique Patients

```dax
Unique Patients =
DISTINCTCOUNT('healthcare_readmission_analytics readmissions'[patient_nbr])
```

### 30-Day Readmission Rate

```dax
30-Day Readmission Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS('healthcare_readmission_analytics readmissions'),
        'healthcare_readmission_analytics readmissions'[readmitted] = "<30"
    ),
    COUNTROWS('healthcare_readmission_analytics readmissions'),
    0
)
```

### Average Hospital Stay

```dax
Average Hospital Stay =
AVERAGE('healthcare_readmission_analytics readmissions'[time_in_hospital])
```

*Note: These measures use the current Power BI table name. Update it if your model uses a different name.*

## 📁 Project Structure

```text
healthcare-readmission-analytics/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   └── 01_exploratory_analysis.ipynb
├── sql/
│   └── analysis_queries.sql
├── powerbi/
│   └── healthcare_readmission_dashboard.pbix
├── images/
│   ├── dashboard_overview.png
│   ├── patient_demographics.png
│   ├── hospital_utilization.png
│   └── clinical_discharge_insights.png
├── requirements.txt
└── README.md
```

*This is a suggested structure. Keep only files and folders that are present in your actual repository.*

## 🚀 How to Run the Project

### Prerequisites
- Python and Jupyter Notebook or VS Code
- Required Python libraries
- MySQL, if running SQL analysis locally
- Power BI Desktop
- Dataset from the UCI Machine Learning Repository

### Python Setup

1. Clone or download the repository.
2. Download the dataset from the source linked above.
3. Place the dataset at the path expected by the notebook.
4. Install dependencies if a `requirements.txt` file is available.
5. Open the Jupyter Notebook and run the cells in order.

```bash
python -m venv .venv
pip install -r requirements.txt
```

### SQL Setup

1. Create the project database in MySQL.
2. Import the prepared dataset into the required table.
3. Update table names and connection settings if needed.
4. Execute the SQL analysis queries.

### Power BI Setup

1. Open the `.pbix` file in Power BI Desktop.
2. Update the data-source path or connection if prompted.
3. Refresh the data.
4. Navigate through the dashboard pages and explore the visualizations.

## ⚠️ Limitations

- The dataset covers 1999–2008 and may not reflect current healthcare practices.
- A patient can have multiple encounters.
- Missing values and coded categories may affect the analysis.
- Readmission rates depend on the measure definition and applied filters.
- Observed associations do not prove causation.
- This project is for educational and portfolio purposes, not clinical decision-making.

## 🔮 Future Improvements

- Add automated data-quality checks.
- Validate Power BI measures against SQL calculations.
- Improve drill-through pages and tooltips.
- Add more analytical SQL queries.
- Include dashboard screenshots and a project walkthrough.
- Explore a validated machine learning model as a future extension.

## 👩‍💻 About Me

**Aastha Shukla**  
🎓 MCA Student | Aspiring Data Analyst

This project demonstrates practical skills in Python, SQL, data cleaning, exploratory data analysis, Power BI, DAX, KPI development, dashboard design, and business insight communication.

---

### ⚕️ Disclaimer

This project uses historical, de-identified data for educational and portfolio purposes only. It should not be used to make clinical decisions or claims about current hospital performance.
