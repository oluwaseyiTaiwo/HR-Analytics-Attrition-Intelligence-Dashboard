# HR Analytics & Attrition Intelligence Dashboard

This repository presents a **comprehensive, enterprise-grade HR analytics solution** developed in Power BI, leveraging advanced DAX, robust data modeling, and dynamic visuals. The project addresses real-world challenges in employee attrition, performance evaluation, diversity equity & inclusion (DEI), and strategic workforce planning.

> This is more than a dashboard — it's an end-to-end analytical system that demonstrates the kind of impactful, data-driven storytelling that Fortune 500 HR departments rely on.

---

## 🚀 Project Overview

The dashboard enables organizations to:

* **Analyze attrition patterns** across departments, job roles, age groups, and ethnicities
* **Track and predict performance review cycles**
* **Visualize hiring trends and employee engagement metrics**
* **Support DEI and compensation equity analysis**

### Built-in Capabilities

* **Multi-dimensional analysis** using a fully normalized star schema
* **Live performance review monitoring** with custom calendar logic
* **Temporal intelligence** with dynamic date filtering and custom fiscal calendar support
* **Drill-down interactivity** from department-level summaries to individual employee records

---

## 🎓 Key Features & Contributions

### ✅ Data Engineering & Modeling

* Imported and transformed raw HR datasets: employees, performance ratings, and satisfaction surveys
* Created a **custom date dimension (`DimDate`)** with 25+ attributes including fiscal month, week range, and quarter start/end logic using advanced DAX
* Established **one-to-many relationships** between dimension and fact tables with proper cardinality and active/inactive paths
* Created **clean, filterable** dimension tables for Education, Rating Levels, and Satisfaction Levels
* Standardized date formats, removed nulls, and ensured **one-to-many relationships** for proper modeling
* Integrated and cleaned **multi-source HR datasets** (employee profiles, satisfaction reviews, performance ratings)

### 🧩 Data Modeling

* Built a **robust star schema** connecting dimensions like `DimDate`, `RatingLevel`, and `SatisfiedLevel` to fact tables
* Developed **cross-table relationships** using inactive/active relationship toggling via `USERELATIONSHIP`
* Created a **custom `DimDate` table** using DAX with extended attributes (fiscal quarters, week spans, year-month keys)

### ⚖️ Advanced DAX Logic

Defined over **15+ sophisticated measures** including:

```dax
ActiveEmployee = SUM('Employee -Dim'[Active/NotActive])
AttritionRate = [InActiveEmployee] / [TotalEmployee]
AttritionRate Date = [InactiveEmployeesDate] / [TotalEmployeeDate]
InActiveEmployee = [TotalEmployee] - [ActiveEmployee]
TotalEmployee = DISTINCTCOUNT('Employee -Dim'[EmployeeID])
TotalEmployeeDate = CALCULATE([TotalEmployee], USERELATIONSHIP('Employee -Dim'[HireDate], DimDate[Date]))
InactiveEmployeesDate = CALCULATE([InActiveEmployee], USERELATIONSHIP('Employee -Dim'[HireDate], DimDate[Date]))
Next Review Date = VAR review = IF(MAX('PerformanceRating - Fact'[ReviewDate]) = BLANK(), Max('Employee -Dim'[HireDate]), MAX('PerformanceRating - Fact'[ReviewDate])) RETURN review + 365
```

* Leveraged **`USERELATIONSHIP()`** to simulate date-aware calculations for hire and review timelines
* Predicted next performance review dates and filled missing data for insightful completeness

### 🌐 Data Visualization & Storytelling

Used Power BI’s capabilities to produce a **compelling executive-level dashboard**, including:

* KPI cards (Total Employees, Attrition Rate, Active Employees)
* Tree maps for employee distribution by department and job role
* Stacked column charts for hiring vs attrition by year
* Line and area charts for attrition trend analysis
* Diversity-focused visuals: attrition by ethnicity, salary by ethnic group, gender/age breakdowns
* Interactive filters and employee-level drill-through functionality

---

## 🎓 Technical Stack

* **Power BI Desktop** for modeling, visuals, and UX
* **DAX** for measure creation, logic and advanced time-intelligence and conditional KPIs
* **Data modeling** Dimensional modeling using a star schema
* **Custom date table** with full fiscal/calendar flexibility
* **Relational modeling** with dimension/fact integrity
* Clean UI/UX principles for navigation and executive storytelling

---

## 🎯 Key Business Impact

* Identified high-risk attrition segments by department, age, travel status and job role
* Revealed demographic gaps in satisfaction and compensation
* Supported diversity initiatives by visualizing ethnic and gender distribution
* Enabled proactive review management through predictive insights
* Delivered enterprise-ready visuals for HR leadership and executive teams
* Highlighted **underrepresented demographics** in hiring vs. attrition
* Surface **performance management trends**, dissatisfaction spikes, and review delays
* Created a **boardroom-ready report** with both macro and micro-level views

---

## 📈 Visual Reporting & Dashboarding

* **Executive Summary Cards** (Total Employees, Active, Inactive, Attrition %)
* **Attrition Trend Visuals** by year, role, department, business travel
* **Demographic Breakdown** by age, gender, marital status, and ethnicity
* **Salary & Satisfaction Analysis** by ethnic group and department
* **Performance Review Tracker** with manager vs. self-rating comparisons and future review date prediction
* Used diverse visuals: bar charts, line graphs, treemaps, stacked columns, shaded area visuals, and custom KPIs

### 📷 Screenshot Locations

Screenshots will be included in the `/screenshots` folder:

* `overview_dashboard.png`: High-level summary with attrition and department-level KPIs
![Data Model](screenshots/overview.png.png)
* `demographic_view.png`: Breakdown of employee demographics by age, ethnicity, gender, and salary
![Data Model](screenshots/DemoGraphic.png.png)
* `performance_tracker.png`: Tracker for individual employee ratings and satisfaction over time
![Data Model](screenshots/Performance%20Tracker.png.png)
* `attrition_insights.png`: Detailed attrition trends by business travel, role, and department
![Data Model](screenshots/Attrition%20Rate.png.png)
* `data_model_schema.png`: Power BI relationship diagram (model view)
![Data Model](screenshots/Model.png.png)

Each screenshot highlights key design choices and interaction flows built into the report.

---

## 🧭 Dynamic Interactions

* **Drill-through and slicers** for department, attrition status, and employee selection
* **USERELATIONSHIP DAX logic** to activate specific date filters for context-sensitive KPIs
* Cross-filtering enabled between visuals for seamless story exploration

---

## 📄 Sample Use Cases

* Who are our highest-performing departments with lowest attrition?
* Are younger employees leaving at a faster rate?
* What is the average satisfaction level by gender or marital status?
* Which job roles have the longest tenure vs. highest turnover?

---

## 📁 Project Files

* `HR_Employee_Attrition.pbix`: Main Power BI report
* `DAX_Measures.txt`: Raw definitions of all custom measures used
* `DimDate DAX.txt`: Full custom DAX code used to build the advanced date dimension
* `screenshots/`: Folder containing all Power BI dashboard views and model diagram

---

> ⚡ **This project demonstrates deep technical fluency in Power BI and an ability to think like a data product owner—not just an analyst.** It bridges analytics, storytelling, and executive alignment to deliver true business value.
