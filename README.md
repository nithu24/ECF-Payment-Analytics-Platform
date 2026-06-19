# 💼 ECF Payment Analytics Platform

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)
![DAX](https://img.shields.io/badge/DAX-20%2B%20Measures-blue)
![Domain](https://img.shields.io/badge/Domain-Corporate%20Finance-orange)
![Regions](https://img.shields.io/badge/Coverage-7%20Regions-red)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

> **A 10-page enterprise Power BI platform for Employee Claims & Finance (ECF) payment analytics — providing operational visibility into claims processing, reimbursement efficiency, financial risk, and stakeholder decision-making across 7 global regions.**
https://app.powerbi.com/links/h_CISIwi8a?ctid=56c1d497-700b-49cf-8f8d-3dd6b20d522f&pbi_source=linkShare
---

## 🎯 Business Objectives

This dashboard was built to give every stakeholder — employees, managers, and finance leadership — the exact view they need:

- ✅ Monitor claims processing efficiency
- ✅ Identify pending financial exposure
- ✅ Enable employee self-service analytics
- ✅ Support operational root-cause analysis

---

## 📊 Dataset Overview

| Metric | Value |
|--------|-------|
| **Total Claims** | 345 |
| **Total Amount** | $724K |
| **Employees** | 50 |
| **Regions** | 7 |
| **Expense Categories** | 5 |
| **% Processed** | 90.3% |
| **Pending Amount** | $70K |
| **Avg Processing Days** | 10 |

---

## 📁 Dashboard Structure — Multi-Stakeholder Design

This is the core architectural feature of the project — **one dataset, three purpose-built views**, each tailored to a different stakeholder's decision-making needs.

| # | Page | Audience | Business Question Answered |
|---|------|----------|---------------------------|
| 1 | **Home** | Everyone | What is this platform and how do I navigate it? |
| 2 | **Executive Summary** | Leadership | How is overall claims processing performing? |
| 3 | **Employee View** | Individual Employees | What's the status of *my* claims? |
| 4 | **Stakeholders View** | Finance Managers | Where is company-wide financial exposure concentrated? |
| 5 | **Operational Intelligence** | Operations & Finance | Where are the bottlenecks, anomalies, and intervention points? |
| 6 | **Insights / Recommendations** | Leadership | What should we do now? |
| 7 | **TT_Country** *(tooltip)* | — | Hover detail for country-level visuals |
| 8 | **Claim Investigation** *(drill-through)* | Finance | Full claim-level detail for a selected country |
| 9 | **TT_Employee_Category** *(tooltip)* | — | Hover detail for employee/category visuals |
| 10 | **TT_Stakeholder_MD** *(tooltip)* | — | Hover detail for manager-level visuals |

---

## 🔥 Key Pages — Deep Dive

### 📈 Executive Summary
- KPI cards: Total Claims, Total Amount, Processed Amount, Pending Amount, % Processed, Avg Processing Days
- Monthly Claims & Spend Performance combo chart
- Country Performance Overview — Sweden ($326K), Italy ($170K), France ($113K)
- Processing Health donut: 90.33% Processed vs 9.67% Under Process
- AI-Generated Business Insights panel with dynamic text summaries

### 👤 Employee View — Personalized Self-Service
- Employee selector slicer — each employee sees **only their own** claims
- Personal KPIs: My Claims, My Amount, My Approved, My Pending, My Approval Rate
- My Claims Journey funnel: Processed vs Under Process
- Claims Requiring Attention table — personal pending claims
- **AI-Generated Insights** — dynamically generated text per employee (e.g. *"Paid accounted for 64.15% of Total Amount. Team Lunch had $11,450 Total Amount..."*)
- Total Amount by Payment Mode donut

### 🏢 Stakeholders View — Finance & Management
- Expense Concentration by Top 10 Employee — heatmap-style tiles
- Geographic Spend Distribution — horizontal bar chart by country
- **Top Risk Contributors** — employees with highest pending amounts
- Pending Claims Requiring Finance Action — filterable detail table
- AI-Generated Insights highlighting outliers (e.g. Business Travel claims 206% higher than Team Lunch)

### 🔍 Operational Intelligence — Root Cause Analysis
- **Decomposition Tree**: drills from Pending Amount ($70,034) → Country → Employee → Expense Category → Payment Mode
- Revealed Sweden as highest queue-risk contributor ($28,496)
- Claims Processing Flow (bridge-style chart): Processed (313) → Under Process (32) → Total (345)
- Key findings panel:
  - ⚠️ Sweden contributes highest queue exposure
  - 📈 Business Travel claims dominate exceptions
  - 💳 Payroll drives reimbursement concentration
  - 👤 A small group of employees contributes a significant share of queue risk

### 🎯 Strategic Recommendations
A dedicated decision page with **Key Findings → Recommended Actions → Future Scope**:

| Key Finding | Recommended Action |
|-------------|---------------------|
| 90.3% of claims processed successfully | Focus immediate review on high-value pending claims |
| Highest pending exposure concentrated in Sweden | Track top pending contributors weekly for proactive follow-up |
| Business Travel is highest spending category | Standardize approval and reimbursement workflows across countries |
| Small group of employees drives pending value | Introduce automated alerts for SLA-approaching claims |
| Bank Transfer is most frequent reimbursement channel | Improve employee self-service visibility for claim tracking |

**Future Scope:**
- Implement role-based access control for secure employee-level reporting
- Integrate live ERP/finance system feeds for real-time claim monitoring
- Apply predictive analytics to flag high-risk-of-delay claims
- Automate exception-based notifications for non-compliant claims

---

## ⚙️ Technical Implementation

### Advanced Power BI Features Used

| Feature | Purpose |
|---------|---------|
| **Drill-through** | Country-level → full Claim Investigation detail page |
| **Custom Tooltip Pages (×3)** | Rich hover detail without leaving the main page |
| **Decomposition Tree** | Interactive multi-level root cause analysis |
| **AI-Generated Insights Text** | Dynamic DAX-driven narrative summaries |
| **Slicer-driven personalization** | Employee View filters to selected individual |

### DAX Measures Built

```dax
% Processed =
DIVIDE(
    CALCULATE(COUNTROWS(ECF), ECF[Status] = "Paid"),
    COUNTROWS(ECF)
)

Pending Amount =
CALCULATE(
    SUM(ECF[Amount]),
    ECF[Status] IN {"Under Process", "Under Review"}
)

Pending Count =
CALCULATE(
    COUNTROWS(ECF),
    ECF[Status] IN {"Under Process", "Under Review"}
)

Avg Processing Days =
AVERAGE(ECF[ProcessingDays])
```

### Data Model
- Tables: Date Table, ECF Table (fact), Measure Table
- Clean star-schema-style structure supporting all drill-through and tooltip pages
- Composite filtering used in drill-through (Country, Employee Category, Stakeholder/MD)

---

## 💡 Key Business Findings

1. **$70K Financial Exposure** — 9.67% of total claims remain pending, representing real cash liability
2. **Geographic Concentration Risk** — Sweden alone accounts for ~41% of pending exposure
3. **Category Risk** — Business Travel dominates both spend and exceptions
4. **Employee Concentration** — A small group of employees drives a disproportionate share of pending value
5. **Processing Time** — 10-day average processing exceeds typical 5–7 day industry benchmark

---

## 🛠️ Tools & Technologies

| Category | Tools |
|----------|-------|
| BI Platform | Power BI Desktop |
| Calculations | DAX (20+ measures) |
| Navigation | Drill-through, Custom Tooltip Pages |
| Advanced Visuals | Decomposition Tree, AI Insight Text Cards |
| Data Modeling | Date Table, Fact Table, Measure Table |

---

## 🔮 Future Enhancements

- **Row-Level Security (RLS)** — restrict each manager to their own department/region's claims
- **Live ERP integration** (SAP, Oracle) for real-time claim status feeds
- **Predictive delay-risk model** — flag claims likely to breach SLA before they do
- **Automated SLA alerting** — notify finance team proactively on aging claims
- **Cross-report drill-through** to a dedicated HR/Payroll report

---

## 👩‍💻 Author

**Nithu Anna Ninan**
- 🔗 LinkedIn: [linkedin.com/in/nithu-ninan](https://linkedin.com/in/nithu-ninan)
- 📧 Email: nithuanna24@gmail.com
- 🐙 GitHub: [github.com/nithu-ninan](https://github.com/nithu-ninan)

---

## ⭐ If you found this project useful, please give it a star!

---

*Built with Power BI · DAX | Domain: Corporate Finance — Employee Claims & Reimbursement | Coverage: 7 Regions*
