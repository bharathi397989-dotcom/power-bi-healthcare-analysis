# Healthcare Analytics Dashboard | Power BI

## Project Overview

This project focuses on analyzing healthcare data using Microsoft Power BI. The interactive dashboard provides insights into hospital appointments, admissions, patient demographics, billing performance, and doctor performance.

The objective is to transform healthcare data into meaningful insights that support hospital management in making data-driven decisions.

## Tools and Technologies
- **Power BI Desktop** – Data visualization and reporting
- **Power Query** – Data cleaning and transformation
- **DAX** – Calculated measures and KPIs
- **Data Modeling** – Snowflake Schema
- **Row-Level Security (RLS)** – Region-based data access

## Data Model

The project uses a Snowflake Schema consisting of fact tables, dimension tables, and supporting dimension tables.

### Fact Tables
- FACT_APPOINTMENTS
- FACT_ADMISSIONS
- FACT_BILLING

### Dimension Tables
- DIM_PATIENT
- DIM_DOCTOR
- DIM_TREATMENT
- DIM_DATE

### Supporting Dimension Tables
- DIM_DEPARTMENT
- DIM_SPECIALIZATION
- DIM_LOCATION

## Key Performance Indicators (KPIs)

The report includes the following metrics:

- Total Billing Amount
- Total Appointments
- Completed Appointments
- Total Admissions
- Distinct Patients
- Previous Year Billing
- Year-over-Year (YoY) Revenue Growth
- Year-to-Date (YTD) Billing
- Month-to-Date (MTD) Billing
- Doctor Performance Ranking

## DAX Measures

### Total Billing Amount
```dax
Total Billing Amount =
SUM(FACT_BILLING[TOTAL_AMOUNT])
```

### Previous Year Billing
```dax
Previous Year Billing =
CALCULATE(
    [Total Billing Amount],
    SAMEPERIODLASTYEAR(DIM_DATE[FULL_DATE])
)
```

### YoY Growth Percentage
```dax
YoY Growth % =
DIVIDE(
    [Total Billing Amount] - [Previous Year Billing],
    [Previous Year Billing],
    0
)
```

### Completed Appointments
```dax
Completed Appointments =
CALCULATE(
    COUNTROWS(FACT_APPOINTMENTS),
    FACT_APPOINTMENTS[STATUS] = "Completed"
)
```

### Distinct Patients
```dax
Distinct Patients =
DISTINCTCOUNT(FACT_APPOINTMENTS[PATIENT_ID])
```

### Doctor Ranking
```dax
Doctor Rank =
RANKX(
    ALL(DIM_DOCTOR[DOCTOR_NAME]),
    [Total Appointments],
    ,
    DESC,
    DENSE
)
```

## Dashboard Features

### 1. Interactive Healthcare Dashboard
- Appointment and admission analysis
- Billing and revenue trends
- Patient demographics
- Department-wise healthcare performance
- Doctor performance analysis

### 2. Financial Analysis
- Total billing amount
- Previous year comparison
- Year-over-year revenue growth
- YTD and MTD calculations

### 3. Dynamic KPI Selection
Implemented a dynamic KPI selector using:

- SELECTEDVALUE()
- SWITCH()
- Calculated table

Users can select different KPIs such as Revenue, Appointments, Admissions, and Patients to view the corresponding metrics.

### 4. Row-Level Security (RLS)
Implemented region-based Row-Level Security to restrict data visibility based on regional access rules.

## Dashboard Preview

Add screenshots of the completed Power BI report pages below.


### Patient Dashboard
![Patient Dashboard](patient%20dashboard.PNG)

### Doctor Dashboard
![Doctor Dashboard](doctor%20dashboard.PNG)

### Insurance Dashboard
![Insurance Dashboard](insurance%20dashboard.PNG)

## Project Workflow

1. Imported healthcare datasets into Power BI.
2. Cleaned and transformed data using Power Query.
3. Created relationships between fact and dimension tables.
4. Designed the snowflake data model.
5. Created DAX measures for healthcare and financial KPIs.
6. Developed interactive report pages.
7. Implemented dynamic KPI selection.
8. Configured region-based Row-Level Security.
9. Validated results and finalized the dashboard.

## Key Outcomes

- Developed an interactive Power BI report for healthcare performance monitoring.
- Integrated appointments, admissions, billing, and patient information into a structured data model.
- Implemented time-intelligence calculations for revenue comparisons.
- Enabled dynamic KPI selection for interactive analysis.
- Applied region-based security to control data access.

## Project Objective

To demonstrate practical skills in data modeling, Power Query, DAX, interactive dashboard development, and data security through an end-to-end healthcare analytics project.

## Author

**Divya Bharati**

Aspiring Junior Data Analyst

[GitHub Profile](https://github.com/bharathi397989-dotcom)
