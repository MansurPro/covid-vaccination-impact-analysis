# 🌍 Global COVID-19 Vaccination Impact Analysis
### Databricks • Python • Pandas • Apache Spark

![Databricks](https://img.shields.io/badge/Databricks-Cloud%20Analytics-red)
![Python](https://img.shields.io/badge/Python-3.10-blue)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-Big%20Data-orange)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellow)
![License](https://img.shields.io/badge/License-MIT-green)

---

# 📌 Project Overview

This project investigates whether **COVID-19 vaccination rates are associated with fewer infections and lower mortality across continents**.

Using global pandemic data from **Our World in Data**, the project applies **data cleaning, aggregation, statistical analysis, and visualization techniques** within a **Databricks cloud environment**.

The goal is to understand how vaccination campaigns correlate with:

- 📉 COVID-19 case rates
- ☠️ excess mortality
- 💰 economic conditions (GDP PPP)

> **Research Question:**  
> Are higher COVID-19 vaccination rates associated with fewer cases and reduced excess mortality? :contentReference[oaicite:0]{index=0}

---

# 🧠 Data Pipeline

The project follows a typical **data analytics workflow**.

```text
Raw Global COVID Data
        │
        ▼
Data Cleaning & Filtering
        │
        ▼
Feature Engineering
(month, year columns)
        │
        ▼
Aggregation by Continent
        │
        ▼
Statistical Analysis
(correlation + descriptive statistics)
        │
        ▼
Visualization
(bar charts)
        │
        ▼
Insights & Interpretation
````

---

# 📊 Dataset

Primary dataset:

```
OWID_COVID19_data_4_Project5-1-1.csv
```

Source:

Our World in Data
[https://ourworldindata.org/covid-vaccinations](https://ourworldindata.org/covid-vaccinations)

The dataset contains global information including:

| Feature                      | Description                       |
| ---------------------------- | --------------------------------- |
| location                     | Country or region                 |
| continent                    | Geographic continent              |
| date                         | Daily observation                 |
| people_fully_vaccinated_phun | % fully vaccinated                |
| new_cases_pmil               | New cases per million             |
| excess_mortality             | Mortality above expected baseline |
| gdp_per_capita               | GDP PPP per capita                |

---

# 🧹 Data Preparation

Steps performed during preprocessing:

### Filtering invalid records

Removed rows where:

* vaccination rate ≤ 0
* new cases ≤ 0
* missing key variables

### Time filtering

Analysis restricted to:

```
September 2021
October 2021
```

This period represents a stage where vaccination programs were well established globally.

---

# ⚙️ Feature Engineering

Two additional features were created from the `date` column:

```python
df['month'] = df['date'].dt.month
df['year'] = df['date'].dt.year
```

This allowed aggregation and comparison between months.

---

# 📈 Aggregated Analysis

Data was grouped by:

```
continent
month
```

Metrics computed:

| Metric                          | Meaning               |
| ------------------------------- | --------------------- |
| average_people_fully_vaccinated | vaccination rate      |
| average_new_cases               | new cases per million |
| average_excess_mortality        | mortality indicator   |

---

# 📊 Visualization

Two main bar charts were created:

### Vaccination Rate by Continent

Shows how vaccination coverage differed across continents in September and October 2021.

### New Cases per Million

Displays the relative spread of COVID-19 during the same period.

Example chart structure:

```
Europe          ███████ Sept
                ████████ Oct

North America   ██████ Sept
                ███████ Oct
```

Charts were generated using **Databricks visualization tools**.

---

# 🔬 Statistical Analysis

Correlation between vaccination rate and case numbers:

```
Correlation = 0.4899
```

Interpretation:

* Indicates **moderate positive correlation**
* Higher vaccination regions also reported more cases

Important:

**Correlation ≠ causation**

Possible reasons:

* higher testing rates
* better reporting systems
* population mobility
* timing of outbreaks

---

# 💰 Data Enrichment

Several countries had missing GDP values.

Missing GDP (PPP) was manually added from:

* World Bank
* Wikipedia
* IMF

Countries filled:

```
Cuba
Liechtenstein
Monaco
Somalia
Syria
Taiwan
```

---

# 📊 Descriptive Statistics

Summary statistics generated:

| Variable              | Mean | Std Dev | Observations |
| --------------------- | ---- | ------- | ------------ |
| Vaccination Rate      | ✔    | ✔       | ✔            |
| GDP per Capita        | ✔    | ✔       | ✔            |
| New Cases per Million | ✔    | ✔       | ✔            |
| Excess Mortality      | ✔    | ✔       | ✔            |

These statistics provide a general overview of the dataset.

---

# 📌 Key Insights

Main findings from the analysis:

• Higher vaccination rates were **not strongly associated with fewer reported cases**
• A **moderate positive correlation (0.49)** was observed
• Differences in **testing capacity and reporting systems** likely influenced results
• Vaccination may still reduce **severe outcomes and mortality**, which requires further analysis

---

# ⚙️ Technologies Used

| Technology               | Purpose                  |
| ------------------------ | ------------------------ |
| Databricks               | Cloud analytics platform |
| Python                   | Data processing          |
| Pandas                   | Data manipulation        |
| Apache Spark             | Distributed processing   |
| Databricks Visualization | Interactive plotting     |

---

# 📂 Repository Structure

```
global-covid-vaccination-analysis
│
├── data
│   └── OWID_COVID19_data_4_Project5.csv
│
├── notebooks
│   └── covid_analysis.dbc
│
├── screenshots
│   └── charts
│
├── results
│   └── analysis_summary.doc
│
└── README.md
```

---

# 🚀 Running the Project

1️⃣ Create a **Databricks workspace**

2️⃣ Upload dataset

3️⃣ Import notebook

```
covid_analysis.dbc
```

4️⃣ Run cells sequentially

---

# 📚 References

Our World in Data
[https://ourworldindata.org/covid-vaccinations](https://ourworldindata.org/covid-vaccinations)

World Bank Data
[https://data.worldbank.org](https://data.worldbank.org)

Wikipedia
[https://wikipedia.org](https://wikipedia.org)

IMF Data
[https://imf.org](https://imf.org)

---

# 👨‍💻 Author

Cloud Computing Data Analytics Project
University Coursework