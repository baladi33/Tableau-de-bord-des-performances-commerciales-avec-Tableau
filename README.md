
# 📊 Commercial Performance Dashboard – Tableau

**Role:** Data Analyst  
**Tools:** Tableau Desktop  
**Dataset:** Commercial data (sales, returns, customers, products, satisfaction)

---

## 📌 Project Overview

This project simulates a real-world business intelligence scenario: a company with large volumes of commercial data across multiple sources (sales, returns, customer satisfaction, product catalog, etc.).  
The goal was to **integrate, model, analyze, and visualize** this data to support strategic commercial decisions.

---

## 🎯 Business Questions Answered

- Which product categories and sub-categories drive the most sales and profit?
- How do sales, returns, and customer satisfaction correlate?
- Where are our geographic strongholds (country/region/city)?
- Which segments underperform and require attention?
- How would a change in profit margin (% increase) impact overall performance?

---

## ⚙️ Key Technical Steps

### 1. Data Import & Modeling
- Connected multiple CSV sources (purchases, returns, evaluations, people)
- Applied **physical joins**:
  - `LEFT JOIN` purchases → evaluations
  - `LEFT JOIN` purchases → returns
  - `INNER JOIN` purchases → people
- Created a **logical relationship** between purchases and evaluations to preserve order-level granularity (e.g., average satisfaction per order)
- Set default formatting: sales (currency), quantity (integer), profit (currency), satisfaction (percentage)

### 2. Hierarchies & Grouping
- **Product hierarchy:** Category → Sub-Category → Product Name
- **Geography hierarchy:** Country → Region → City
- Manual grouping of Sub-Category values for better visual clustering

### 3. Visualizations Built

| Chart Type | Purpose |
|------------|---------|
| Histogram | Sales by Sub-Category (with labels) |
| Histogram | Sales by Segment |
| Drill-down | Quantity by Product hierarchy |
| Scatter/LOD | Satisfaction by Order (using LOD to preserve granularity) |
| Time series | Daily/Monthly/Yearly Sales |
| Map | Sales by Country/Region |
| Bubble chart | Sales by Segment |
| Small multiples | Segment × Region × Sub-Category |
| Dual-axis | Sales vs Quantity |
| Reference lines | Targets per partition |

### 4. Calculated Fields & Parameters

| Field Type | Logic |
|-------------|-------|
| Simple calc | Profit / Sales → Profit margin (%) |
| Conditional calc | Eco-tax: 5% on tech products, **excluded** if product name contains "recycled" |
| Discrete flag | `Total Sales < 1000` → Low sales flag (for conditional formatting/filtering) |
| Dynamic param | `% profit increase` user parameter → Adjusted Profit = Profit × (1 + parameter) |

### 5. Dashboard Final
- Selected most relevant views (sales by geography, satisfaction by order, low sales flag, profit adjuster)
- Added global & contextual filters (Country, Date, Quantity, Segment)
- Applied conditional formatting (red for low sales)
- Ensured readability: titles, legends, axis alignment, color consistency

---

## 📁 Repository Structure

```bash
📦 commercial-dashboard-tableau/
├── data/
│   ├── purchases.csv
│   ├── returns.csv
│   ├── evaluations.csv
│   ├── people.csv
├── dashboard/
│   └── commercial_performance_dashboard.twbx
├── screenshots/
│   ├── dashboard_overview.png
│   ├── profit_adjuster_param.png
│   └── low_sales_flag.png
├── README.md
└── requirements.txt (if any)
```

---

## 🖼️ Dashboard Preview

![Dashboard Overview](./screenshots/dashboard_overview.png)

> *Example of final dashboard with filters, map, satisfaction plot, and profit parameter control*

---

## 🔍 How to Explore the Dashboard

1. **Global filters** (top right): restrict by country, date range, quantity, segment
2. **Profit adjuster slider**: increase profit by X% to simulate margin strategies
3. **Low sales flag**: highlights orders < $1000 for quick risk identification
4. **Satisfaction by order**: identifies dissatisfied orders for root-cause analysis

---

## 📈 Sample Insights

- **Technology** sub-category drives highest sales, but also highest returns
- **Office Supplies** have stable volumes but lower margins
- **Recycled** tech products are eco-tax exempt → competitive pricing opportunity
- **Southern region** shows low satisfaction despite average sales → service quality issue

---

## ✅ What This Project Demonstrates

- Data modeling (joins, relationships, granularity control)
- Hierarchies & grouping for drill-down analysis
- LOD expressions (e.g., satisfaction by order)
- Conditional & parameter-driven calculations
- Dashboard interactivity (filters, parameters, contextual filtering)
- Conditional formatting for operational alerts

---

## 🧠 Lessons Learned

- Logical vs physical joins matter for aggregation level
- Flags (True/False) are powerful for conditional formatting without complex logic
- Parameters make dashboards dynamic for "what-if" analysis
- Reference lines per partition help compare performance against local targets

---

## 🚀 Possible Extensions

- Add forecasting (sales next quarter)
- Integrate returns % as a KPI
- Connect to live database instead of static CSVs

---

# 👨‍💻 Auteur

**Zoubair Baladi**  
**https://www.linkedin.com/in/zoubair-baladi/**
🎓 Master en Systèmes et Télécommunications  
📊 Passionné par le Data Engineering, l’Analyse de Données et la Business Intelligence
## 📬 Connect with Me


*This project was completed as part of a data analyst exercise to simulate real-world commercial intelligence workflows in Tableau.*
