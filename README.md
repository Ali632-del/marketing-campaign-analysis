# 📊 Marketing Campaign Performance Analysis

An end-to-end Data Analytics project focused on evaluating marketing campaign performance across multiple digital platforms.

This project demonstrates the complete analytics workflow, including:

* Data Cleaning & Preparation
* Exploratory Data Analysis (EDA)
* KPI Engineering
* Platform Performance Evaluation
* Trend Analysis
* Statistical Testing
* Data Visualization
* Business Insights & Recommendations

The objective is to transform raw marketing campaign data into actionable insights that support data-driven marketing decisions.

---

# 🚀 Project Highlights

✅ Data Cleaning & Validation

✅ Exploratory Data Analysis (EDA)

✅ KPI Calculation Framework

✅ Platform Performance Ranking

✅ Trend Analysis

✅ Statistical Testing

✅ Business Insights Generation

✅ Publication-Quality Visualizations

---

# 📂 Project Structure

```text
Marketing-Campaign-Performance-Analysis/
│
├── marketing_analysis.ipynb
│
├── cleaned_marketing_campaigns.csv
│
├── charts/
│   ├── 01_conversions_by_platform.png
│   ├── 02_cost_by_platform.png
│   ├── 03_conversion_rate_by_platform.png
│   ├── 04_cpa_cpc_by_platform.png
│   ├── 05_performance_score_ranking.png
│   ├── 06_monthly_trends.png
│   ├── 07_top10_campaigns_conversions.png
│   ├── 08_duration_vs_conversions.png
│   └── 09_correlation_heatmap.png
│
├── requirements.txt
└── README.md
```

---

# 📈 Key Performance Indicators (KPIs)

The project evaluates campaign effectiveness using industry-standard marketing metrics.

### Conversion Rate (CR)

Measures the percentage of clicks that resulted in conversions.

CR = Conversions / Clicks

**Business Importance:**

* Evaluates campaign effectiveness.
* Indicates audience engagement quality.
* Higher values suggest better targeting and messaging.

---

### Cost Per Click (CPC)

Measures the average advertising cost required to generate one click.

CPC = Cost / Clicks

**Business Importance:**

* Assesses traffic acquisition efficiency.
* Supports advertising budget optimization.
* Lower values indicate more cost-effective campaigns.

---

### Cost Per Acquisition (CPA)

Measures the average cost required to generate one conversion.

CPA = Cost / Conversions

**Business Importance:**

* One of the most critical profitability metrics.
* Directly reflects campaign efficiency.
* Lower values indicate stronger return on investment.

---

### Conversion Efficiency

Measures how effectively campaign spending generates conversions.

Conversion Efficiency = Conversions / Cost

**Business Importance:**

* Evaluates marketing spend productivity.
* Helps identify high-performing platforms.
* Supports budget allocation decisions.

---

# 🧹 Data Preparation & Cleaning

To ensure reliable analysis, the dataset was cleaned and validated through:

* Duplicate removal
* Missing value handling
* Platform name standardization
* Data type conversion
* Date validation
* KPI feature engineering
* Campaign duration calculation

Additional engineered features:

* Conversion_Rate
* CPC
* CPA
* Conversion_Efficiency
* Campaign_Duration_Days
* Duration_Group
* Start_YearMonth

---

# 📊 Analytics Performed

### Campaign Analysis

* Total Campaigns
* Total Clicks
* Total Conversions
* Total Marketing Cost

### Platform Analysis

* Platform comparison
* Conversion performance evaluation
* Cost efficiency assessment
* KPI benchmarking

### Trend Analysis

* Monthly conversion trends
* Monthly cost trends
* Campaign activity patterns

### Statistical Analysis

A Kruskal-Wallis statistical test was performed to determine whether conversion rates differ significantly across marketing platforms.

---

# 🏆 Platform Performance Ranking

A custom scoring model was developed to rank marketing platforms.

Performance Score:

```text
0.40 × Conversion Rate
+ 0.30 × Total Conversions
+ 0.20 × Conversion Efficiency
- 0.10 × CPA
```

This score balances:

* Effectiveness
* Efficiency
* Conversion Volume
* Cost Performance

allowing a comprehensive comparison between platforms.

---

# 📉 Visualizations

The notebook generates multiple visualizations to support analysis and decision-making:

* Conversions by Platform
* Cost by Platform
* Conversion Rate by Platform
* CPA & CPC Comparison
* Platform Performance Ranking
* Monthly Trends
* Top Performing Campaigns
* Campaign Duration Analysis
* Correlation Heatmap

---

# ▶️ Run Notebook

Open:

```text
marketing_analysis.ipynb
```

Run all notebook cells sequentially to:

1. Clean and prepare the dataset
2. Generate KPIs
3. Perform exploratory data analysis
4. Create visualizations
5. Evaluate platform performance
6. Extract business insights

The notebook contains the complete workflow from raw data processing to final business recommendations.

---

# 📸 Project Screenshots

Add screenshots here after exporting your charts.

### Platform Performance Analysis

<img width="1918" height="1018" alt="image" src="https://github.com/user-attachments/assets/24e3f79c-6e51-45b4-aaa9-7b8a32d031cf" />


### Trend Analysis

<img width="1918" height="1020" alt="image" src="https://github.com/user-attachments/assets/13ee0aa0-6d10-4aa2-880d-b9155ed8574e" />


### KPI Dashboard View

<img width="1898" height="916" alt="image" src="https://github.com/user-attachments/assets/9383372c-2ff9-4f26-9b90-83d7fd3ed12b" />


---

# 🛠️ Tech Stack

| Technology       | Purpose                          |
| ---------------- | -------------------------------- |
| Python           | Core Development                 |
| Pandas           | Data Cleaning & Analysis         |
| NumPy            | Numerical Computation            |
| Matplotlib       | Data Visualization               |
| Seaborn          | Statistical Visualization        |
| SciPy            | Statistical Analysis             |
| Jupyter Notebook | Interactive Analysis Environment |

---

# 📌 Business Value

This project demonstrates how marketing campaign data can be transformed into actionable business insights through analytics and visualization.

Key skills demonstrated:

* Data Cleaning
* Exploratory Data Analysis
* KPI Design
* Statistical Analysis
* Business Intelligence
* Data Visualization
* Insight Generation

The project reflects real-world analytical workflows commonly used by Data Analysts, Business Analysts, and Marketing Analysts.
