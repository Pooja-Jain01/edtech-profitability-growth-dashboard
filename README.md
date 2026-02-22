# 📊 EdTech Profitability & Growth Dashboard

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Made with DAX](https://img.shields.io/badge/DAX-0078D4?logo=microsoft&logoColor=white)](https://docs.microsoft.com/en-us/dax/)

> An interactive Power BI dashboard analyzing **₹3.04B revenue, ₹636M net profit, and 25.2% margin** across 9 EdTech courses, helping identify profitability drivers and optimize marketing ROI from 10,000+ transactions.

---

## 🎯 Project Overview

This project delivers a comprehensive business intelligence solution for an EdTech company, analyzing course-level profitability, marketing efficiency, and growth trends. The dashboard enables data-driven decisions on pricing, marketing budget allocation, and course scaling strategies.

### Key Metrics at a Glance

| Metric | Value |
|--------|-------|
| **Total Revenue** | ₹3.04 Billion |
| **Net Profit** | ₹636.09 Million |
| **Profit Margin** | 25.2% |
| **Total Enrollments** | 243,603 students |
| **Marketing ROI** | 3.2x |
| **Data Period** | Jan 2023 - Dec 2024 |

---

## 🚀 Key Features

✅ **Profitability Analysis** - Course-level profit breakdown with margin percentages  
✅ **Marketing Performance** - ROI tracking and cost per enrollment metrics  
✅ **Conversion Funnel** - Lead to enrollment tracking across all courses  
✅ **Interactive Filters** - Dynamic slicing by date, category, and course  
✅ **Trend Analysis** - Revenue and profit patterns over 24 months  

---

## 📈 Business Problem

### The Challenge
Management struggled to identify which courses were **genuinely profitable** versus those generating high revenue but consuming disproportionate resources.

**Pain Points:**
- ❌ High-volume courses with thin margins draining operational capacity
- ❌ Marketing budget allocated without ROI visibility
- ❌ No clear view of cost per enrollment or conversion rates
- ❌ Inability to prioritize scalable, high-margin opportunities

### The Solution
A Power BI dashboard that:
- ✅ Calculates true profitability across all cost dimensions
- ✅ Tracks marketing ROI and customer acquisition costs
- ✅ Visualizes the complete conversion funnel
- ✅ Enables evidence-based marketing optimization

---

## 💡 Key Insights

### 🏆 Top Findings

1. **Profitability Concentration**
   - Top 3 courses generate **68% of total profit** with only 33% of enrollments
   - **Data Analytics** alone drives ₹214M profit (33.6% of total)

2. **Marketing Efficiency**
   - Average cost per enrollment: **₹1,074**
   - **SQL Bootcamp** delivers best ROI at **4.2x**
   - **Brand Strategy** shows lowest ROI at **1.1x** - requires optimization

3. **Growth Trajectory**
   - Q4 2024 revenue **up 23%** vs Q4 2023
   - Enrollment conversion improved from **5.8% to 6.4%** YoY
   - Clear seasonality: **Jan-Feb peak enrollment periods**

4. **Course Performance Tiers**

**High-Margin Champions** (Scale These):
- Performance Marketing: **31.4% margin**
- SQL Bootcamp: **28.9% margin**
- Data Analytics: **27.3% margin**

**Volume Giants** (Optimize Pricing):
- Digital Marketing: **18.2% margin**, highest enrollment
- Financial Modeling: **19.1% margin**, high volume

**Underperformers** (Review Strategy):
- Brand Strategy: **12.1% margin**
- Corporate Finance: **14.5% margin**

---

## 🛠️ Tools & Technologies

- **Microsoft Excel** - Data exploration and structuring
- **Power Query (M)** - ETL and data transformation
- **Power BI Desktop** - Dashboard development
- **DAX** - Business logic and calculated measures
- **Data Modeling** - Star schema design

---

## 📊 Dashboard Components

### KPI Cards
- Total Revenue, Net Profit, Profit Margin %
- Marketing ROI, Total Enrollments

### Visualizations
- **Line Chart** - Revenue & profit trends over time
- **Bar Chart** - Top 5 courses by profitability
- **Funnel Chart** - Lead to enrollment conversion
- **Table** - Detailed course performance metrics
- **Column Chart** - Profit comparison across all courses

### Interactive Features
- Date range slicer
- Course category filter
- Cross-filtering across all visuals


## Dashboard Preview

![Dashboard](dashboard_screenshots.png)
![KPI View](KPI%20Dashboard%20Screenshot.png)

---

## 📂 Repository Structure

```
edtech-profitability-growth-dashboard/
│
├── EdTech_Messy_Raw_Data_10k.csv                    # Raw dataset (10K records)
├── Ed-tech-Profitability_and_performance_dashboard.pbit  # Power BI template
├── LICENSE                                           # MIT License
└── README.md                                         # This file
```

---

## 🚀 How to Use

### Prerequisites
- **Power BI Desktop** (Free): [Download here](https://powerbi.microsoft.com/desktop/)
- Windows 10/11 or Power BI Service account

### Steps

1. **Download Files**
   ```
   - Clone this repository or download ZIP
   - Extract all files to a folder
   ```

2. **Open Dashboard**
   ```
   - Open Power BI Desktop
   - File → Open → Browse
   - Select "Ed-tech-Profitability_and_performance_dashboard.pbit"
   ```

3. **Connect Data** (if prompted)
   ```
   - Point to "EdTech_Messy_Raw_Data_10k.csv"
   - Click "Load"
   ```

4. **Explore Dashboard**
   ```
   - Use slicers to filter by date and category
   - Click on visuals to cross-filter
   - Hover for detailed tooltips
   ```

5. **Refresh Data** (optional)
   ```
   - Replace CSV with your own data (same format)
   - Home ribbon → Refresh
   ```

---

## 📊 Data Overview

### Dataset Specifications
- **Records:** 9,999 transactions
- **Period:** January 2023 - December 2024
- **Courses:** 9 unique courses
- **Categories:** Data, Finance, Marketing

### Fields
| Field | Description | Type |
|-------|-------------|------|
| Date | Transaction date | Date |
| Course Category | Course domain | Text |
| Course Name | Specific course | Text |
| Course Price | Price in ₹ | Number |
| Instructor Cost | Instructor payment | Number |
| Refund Amount | Refunds issued | Number |
| Leads_Clean | Marketing leads | Number |
| Enrollments_clean | Actual enrollments | Number |
| Marketing_spend | Marketing cost | Number |

### Data Quality Notes
⚠️ **Transparency:** The original dataset contained significant missing values:
- 75.6% missing lead data
- 74.6% missing marketing spend
- 66.7% missing instructor costs
- 50.6% missing enrollment data

**Handling Approach:**
- Used category averages for imputation where appropriate
- Flagged imputed records for transparency
- Analysis based on ~50% complete data
- Results may underestimate true metrics

---

## 📈 Key DAX Measures

### Net Profit
```dax
Net Profit = 
SUM(Clean_EdTech_Fact[Revenue]) - 
SUM(Clean_EdTech_Fact[Total Cost])
```

### Net Profit Margin %
```dax
Net Profit Margin % = 
DIVIDE(
    [Net Profit],
    SUM(Clean_EdTech_Fact[Revenue]),
    0
) * 100
```

### ROI on Marketing
```dax
ROI on Marketing = 
DIVIDE(
    [Net Profit],
    SUM(Clean_EdTech_Fact[Marketing_spend]),
    0
)
```

### Cost per Enrollment
```dax
Cost per Enrollment = 
DIVIDE(
    SUM(Clean_EdTech_Fact[Marketing_spend]),
    SUM(Clean_EdTech_Fact[Enrollments_clean]),
    0
)
```

### Conversion Rate %
```dax
Conversion Rate % = 
DIVIDE(
    SUM(Clean_EdTech_Fact[Enrollments_clean]),
    SUM(Clean_EdTech_Fact[Leads_Clean]),
    0
) * 100
```

---

## 💼 Business Recommendations

Based on the analysis, here are actionable recommendations:

### 1. **Scale High-Margin Courses**
- Increase marketing budget for Performance Marketing, SQL Bootcamp, and Data Analytics
- These deliver **30%+ margins** with strong demand

### 2. **Optimize Volume Courses**
- Digital Marketing and Financial Modeling have high enrollment but lower margins
- Consider price increases or cost reduction strategies
- Target margin improvement from **18% to 25%**

### 3. **Review Underperformers**
- Brand Strategy and Corporate Finance show **<15% margins**
- Options: Restructure pricing, reduce costs, or discontinue
- Reallocate resources to profitable courses

### 4. **Marketing Budget Reallocation**
- Shift budget from low-ROI courses (Brand Strategy: 1.1x) to high-ROI courses (SQL Bootcamp: 4.2x)
- Target overall ROI improvement from **3.2x to 4.0x**

### 5. **Conversion Rate Optimization**
- Current rate: **6.4%** - industry average is 8-10%
- Improve lead qualification and nurturing processes
- A/B test landing pages and email campaigns

---

## 🎓 Skills Demonstrated

**Data Analysis:**
- Data cleaning and transformation
- Handling missing data
- Statistical analysis
- Profitability modeling

**Business Intelligence:**
- Dashboard design and UX
- KPI definition
- Data storytelling
- Visual analytics

**Technical Skills:**
- Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query (M language)
- Data modeling (star schema)

**Business Acumen:**
- EdTech domain knowledge
- Marketing funnel analysis
- Unit economics (CAC, LTV)
- Strategic recommendations

---

## 📝 Methodology

### 1. Data Preparation
- Imported raw CSV with 9,999 records
- Handled missing values using domain-appropriate strategies
- Created calculated columns for revenue and costs
- Validated data quality and flagged issues

### 2. Data Modeling
- Designed star schema with fact and dimension tables
- Created date dimension for time intelligence
- Established relationships for proper filtering

### 3. Measure Development
- Built 10+ DAX measures for KPIs
- Implemented profit, margin, and ROI calculations
- Created conversion rate and cost metrics

### 4. Visualization
- Designed single-page dashboard for clarity
- Used appropriate chart types for each insight
- Applied consistent color scheme and formatting
- Added interactive slicers and filters

### 5. Testing & Validation
- Verified calculations against raw data
- Tested all interactive features
- Ensured cross-filtering works correctly

---

## 🔮 Future Enhancements

Potential improvements for this project:

- [ ] **Multi-page dashboard** with Executive, Profitability, and Marketing views
- [ ] **Predictive analytics** - Enrollment forecasting using historical trends
- [ ] **Customer segmentation** - Cluster analysis of student behavior
- [ ] **What-if analysis** - Dynamic pricing scenario modeling
- [ ] **Automated refresh** - Connect to live data source
- [ ] **Mobile optimization** - Responsive layout for tablets/phones
- [ ] **Advanced DAX** - YoY growth, moving averages, Pareto analysis

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👤 About Me

**Pooja Jain** - Data Analyst passionate about transforming data into actionable business insights.

### Connect With Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/poojajain54/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white)](https://github.com/Pooja-Jain01)
[![Email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:pjpoojajain54@example.com)

I'm interested in:
- 📊 Data Analytics & Business Intelligence roles
- 💼 Freelance dashboard projects
- 🤝 Collaborations on data visualization
- 📚 Knowledge sharing & mentorship

---

## 🙏 Acknowledgments

- Power BI community for best practices and inspiration
- EdTech industry reports for business context validation
- Open-source contributors for data visualization examples

---

## ⭐ Show Your Support

If you found this project helpful:
- ⭐ **Star this repository**
- 🔀 **Fork it** for your own analysis
- 📢 **Share it** on LinkedIn
- 💬 **Provide feedback** via Issues

---

<div align="center">

**Built with ❤️ using Power BI**

*Last updated: February 2026*

</div>
