# 📊 EdTech Profitability & Growth Dashboard

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?logo=powerbi&logoColor=black) ![DAX](https://img.shields.io/badge/DAX-Measures-blue) ![License: MIT](https://img.shields.io/badge/License-MIT-green)

An interactive Power BI dashboard analysing **₹3B revenue, ₹636M net profit (25.2% margin)** across 9 EdTech courses, covering course-level profitability, marketing efficiency and the lead-to-enrollment funnel from ~10K transactions (Jan 2023 – Dec 2024).

![Dashboard](Dashboard%20Screenshot.png)

## 🎯 Business Question
Which courses actually drive profit, and is marketing spend being used efficiently? The dashboard gives a single view of course-level profit and margin, cost per lead / enrollment, and marketing ROI so pricing and budget decisions can be prioritised.

## 📂 Data Source
- Public **Kaggle** dataset: ~9,999 transactions, 9 courses, 4 categories: Data, Finance, Marketing, General/Foundation.
- The business scenario in this project is illustrative; the analysis is a portfolio exercise on a public dataset, not on a real company's internal data.

## 📈 Headline Metrics (from the dashboard)
| Metric | Value |
|---|---|
| Revenue | ₹3B |
| Net Profit | ₹636.4M |
| Net Profit Margin | 25.2% |
| Marketing Spend | ₹1.03B |
| Marketing ROI (revenue-based) | 146% (ROAS 2.46x) |
| Enrollments | ~294K |
| Leads | ~998K |
| Cost per Lead / Enrollment | ~₹1,030 / ~₹3,490 |

> Marketing ROI = (Revenue − Marketing Spend) ÷ Marketing Spend. It is revenue-based, so it ignores instructor cost and refunds. For comparison, net profit is ~₹0.62 per ₹1 of marketing spend.

## 💡 Key Insights
1. **Profit is concentrated, and driven mainly by scale.** The top 3 courses (Digital Marketing, Equity Research, SQL Bootcamp) generate **~48.5% of net profit**; the top 4 generate ~62%.
2. **Margins are tightly clustered (20.5%–27.8%)**, so differences in profit come mostly from revenue volume rather than margin.
3. **Digital Marketing leads on both revenue (₹431M) and profit (₹118M)** at a 27.4% margin.
4. **Lowest margins:** Financial Modeling (20.5%), Brand Strategy (21.9%) and Equity Research (23.1%). Equity Research is high-revenue but below-average margin, so it is a pricing/cost candidate.
5. **Highest margins:** Power BI Mastery (27.8%), Corporate Finance (27.6%) and Digital Marketing (27.4%).

| Course | Revenue (₹M) | Net Profit (₹M) | Margin |
|---|---|---|---|
| Digital Marketing | 431.3 | 118.2 | 27.4% |
| Equity Research | 413.6 | 95.4 | 23.1% |
| SQL Bootcamp | 376.4 | 95.0 | 25.2% |
| Data Analytics | 344.2 | 87.2 | 25.3% |
| Corporate Finance | 208.5 | 57.5 | 27.6% |
| Power BI Mastery | 192.7 | 53.5 | 27.8% |
| Performance Marketing | 192.3 | 50.7 | 26.4% |
| Brand Strategy | 189.9 | 41.6 | 21.9% |
| Financial Modeling | 181.4 | 37.3 | 20.5% |

## ✅ Recommendations
- **Protect and grow the top profit drivers with healthy margins** (Digital Marketing, SQL Bootcamp, Data Analytics): together ~₹300M profit (~47% of total) at 25-27% margins.
- **Review pricing/cost for Equity Research**, which has high revenue but only 23.1% margin; every +1 pt of margin is ~₹4M profit.
- **Investigate Financial Modeling and Brand Strategy** (lowest margins, lowest profit) before allocating more marketing budget to them.
- **Add course-level ROI** (see Future Enhancements) before reallocating marketing budget.

## ⚠️ Data Quality & Limitations
The raw data was intentionally messy. Missing values before cleaning:
- Leads: 75.6% · Marketing spend: 74.6% · Instructor cost: 66.7% · Enrollments: 50.6%

**Handling:** category-average imputation, with imputed records flagged.

**What this means for the results:**
- Metrics that depend on imputed fields (marketing ROI, cost per lead / enrollment, **conversion rate of 29.45%**) should be treated as indicative, not exact. Conversion rate is likely inflated by imputing leads and enrollments independently.
- Revenue is the most reliable figure. Net profit and margin also depend on cost fields that were partly imputed (e.g., instructor cost, 66.7% missing), so treat them as estimates; the sensitivity check in Future Enhancements is needed to confirm that the course ranking holds.

## 🛠️ Tools & Technologies
Excel (exploration) · Power Query / M (ETL) · Power BI Desktop · DAX · Star-schema data modelling

## 📊 Dashboard Components
- **KPI cards:** Net Profit Margin %, Net Profit, Enrollment, Revenue, Conversion Rate %, ROI on Marketing %
- **Pareto chart:** Net profit and cumulative profit % by course
- **Line chart:** Profit by year, quarter and month
- **Table:** Revenue, net profit and margin % by course (conditional formatting)
- **Column chart:** Cost per lead and cost per enrollment by course category
- **Revenue by course** chart

## 📈 Key DAX Measures
```dax
Net Profit = SUM(Clean_EdTech_Fact[Revenue]) - SUM(Clean_EdTech_Fact[Total Cost])

Net Profit Margin % =
DIVIDE([Net Profit], SUM(Clean_EdTech_Fact[Revenue]), 0) * 100

ROI on Marketing =
DIVIDE(
    SUM(Clean_EdTech_Fact[Revenue]) - SUM(Clean_EdTech_Fact[Marketing_spend]),
    SUM(Clean_EdTech_Fact[Marketing_spend])
)

Cost per Enrollment =
DIVIDE(SUM(Clean_EdTech_Fact[Marketing_spend]), SUM(Clean_EdTech_Fact[Enrollments_clean]), 0)

Conversion Rate % =
DIVIDE(SUM(Clean_EdTech_Fact[Enrollments_clean]), SUM(Clean_EdTech_Fact[Leads_Clean]), 0) * 100
```

## 📝 Methodology
1. **Prepare:** imported raw CSV, profiled missing values, imputed and flagged records in Power Query.
2. **Model:** star schema with a fact table and dimension tables (including a date dimension).
3. **Measure:** built 10+ DAX measures for profit, margin, ROI, cost and conversion metrics.
4. **Visualise:** single-page dashboard with slicers and cross-filtering.
5. **Validate:** cross-checked KPI totals against the course-level table (e.g., total revenue ₹3B → 25.2% margin on ₹636.4M profit).

## 🔮 Future Enhancements
- [ ] **Course-level marketing ROI** table and visual
- [ ] **Sensitivity check:** recompute key metrics on non-imputed rows only and compare with the full results
- [ ] Pareto / profit-share analysis of enrollments vs profit
- [ ] Multi-page layout (Executive, Profitability, Marketing)
- [ ] YoY growth and moving averages in DAX

## 📂 Repository Structure
```
├── EdTech_Messy_Raw_Data_10k.csv
├── Ed-tech-Profitability and performance dashboard.pbit
├── Dashboard Screenshot.png
├── KPI Dashboard Screenshot.png
├── screenshots/
├── LICENSE
└── README.md
```

## 🚀 How to Use
1. Clone the repo or download the ZIP.
2. Open the `.pbit` template in Power BI Desktop (free).
3. Point the data source to `EdTech_Messy_Raw_Data_10k.csv` when prompted and click **Load**.

## 👤 About
**Pooja Jain**: PGDM (Finance & Business Analytics) student building a profile for data analytics roles.
[LinkedIn](https://linkedin.com/in/poojajain54) · [GitHub](https://github.com/Pooja-Jain01)

## 📄 License
MIT License. See [LICENSE](LICENSE).
