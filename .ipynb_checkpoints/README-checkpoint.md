# Airline Passenger Satisfaction – Data Product Case Study
### 1. Overview
This project explores airline passenger satisfaction using an open Kaggle dataset of 120K+ survey responses from an anonymised airline. The goal is to think and act like a Technical Product Owner in an Analytics Centre of Excellence (ACoE): define KPIs, analyse drivers of satisfaction, and translate insights into a product backlog for data and analytics products.

The work is structured as an end-to-end data product case study that could sit inside an airline’s analytics platform or ACoE, similar to Emirates Group’s Analytics Centre of Excellence.

### 2. Business context
Airlines rely on data to understand why passengers are satisfied or dissatisfied and how operational factors like delays and service quality influence loyalty and revenue. A Technical Product Owner in an ACoE must:

- Own data and information products that expose the right KPIs and insights to stakeholders.
- Ensure data from transactional systems and surveys is usable, documented, and trustworthy.
- Prioritise features, BAU improvements, NFRs, and technical debt in backlogs to improve customer experience and operational performance.

This project simulates that role using publicly available airline satisfaction data.

### 3. Dataset
- Source: Kaggle – “Airline Customer Satisfaction” / “Airline Passenger Satisfaction”.
- Size: ≈ 120,000–130,000 rows and 22–25 columns (depending on version).
- Each row: one passenger’s flight with demographics, flight details, service ratings, delays, and overall satisfaction (satisfied vs neutral/dissatisfied).

**Key columns (examples):**
- Satisfaction: overall satisfaction level.
- Customer Type: Loyal vs Disloyal customer.
- Age: passenger age.
- Type of Travel: Business vs Personal.
- Class: Business, Eco, Eco Plus.
- Flight Distance: distance in kilometres.
- Service ratings (1–5): seat comfort, inflight wifi, online booking, on-board service, baggage handling, cleanliness, etc.
- Departure Delay in Minutes, Arrival Delay in Minutes: delay metrics.

### 4. Objectives
From a Technical Product Owner (Data & Analytics) perspective, the project aims to:
1. Design airline-style KPIs for passenger satisfaction and experience across segments (class, travel type, loyalty, delays).
2. Perform exploratory data analysis (EDA) to identify key drivers of satisfaction and dissatisfaction.
3. Build a simple prediction model that classifies whether a passenger is likely to be satisfied, and interpret feature importance.
4. Translate analytics into a product backlog for an internal analytics product (dashboards, data improvements, NFRs, and BAU items).
5. Demonstrate how a Technical Product Owner can work with data to inform roadmap and prioritisation in an ACoE setting.

### 5. Repository structure

```text
.
├── README.md
├── notebooks
│   ├── 00_data_cleaning.ipynb     # from raw → processed CSV
│   ├── 01_eda_kpis.ipynb          # exploratory analysis & KPIs
│   └── 02_modeling_backlog.ipynb  # modeling ideas and experiments
├── data
│   ├── raw
│   │   └── airline_passenger_satisfaction.csv
│   └── processed
│       └── airline_customer_satisfaction_cleaned.csv
├── src
│   └── utils.py                   # optional helpers
└── requirements.txt
```

### 6. Analysis steps
#### 6.1 00_data_cleaning.ipynb
Main steps:
1. Data loading & initial checks
   - Load the Kaggle CSV from `data/raw/`, inspect schema, dtypes, and basic data quality.

2. Cleaning & standardisation
   - Handle missing values (e.g., delays, ratings).
   - Clean and normalise categorical values (e.g., loyal vs disloyal, business vs personal travel).
   - Rename columns to snake_case for easier analysis and modeling.

3. Feature engineering
   - Create derived fields such as delay flags (e.g., `is_dep_delayed`, `is_arr_delayed`), delay buckets, and age/flight distance buckets where helpful.

4. Output
   - Save the cleaned dataset to data/processed/airline_customer_satisfaction_cleaned.csv for downstream notebooks.

#### 6.2 01_eda_kpis.ipynb
This notebook focuses on analytics and storytelling using the processed data.

1. Data loading
   - Load
     `data/processed/airline_customer_satisfaction_cleaned.csv`.

2. KPI definition
   Example KPIs:
   - Overall satisfaction rate.
   - Satisfaction by customer type, travel type, and class.
   - Satisfaction vs departure / arrival delay buckets.
   - Average service ratings for satisfied vs dissatisfied passengers.
   
   These KPIs are treated as core metrics for an airline passenger experience analytics product.

3. Exploratory Data Analysis

   - Segmentation:
     - Satisfaction by class, type of travel, and loyalty status.
   
   - Service quality:
     - Comparison of rating distributions (seat comfort, wifi, online booking, baggage handling, on-board service, cleanliness, etc.) between satisfied and dissatisfied passengers.

   - Delay impact:
     - Relationship between delay metrics and satisfaction, and the marginal impact of increasing delay buckets.

4. Key insights (business narrative)

   - Summaries written in product language (e.g., “Business travellers in Economy are particularly sensitive to departure delays and online booking experience.”).
   - Explicit linking of insights to potential product decisions and operational improvements.

#### 6.3 02_modeling_backlog.ipynb
This notebook collects modeling ideas and experiments from a TPO lens.

1. Feature engineering & preprocessing
   - Work off the processed dataset to encode categorical variables, scale or transform numerical variables where appropriate, and split into train/test sets.

2. Baseline model
   - Train a simple classification model (e.g., logistic regression or a tree-based model) to predict Satisfaction.
   - Evaluate using metrics such as accuracy, precision/recall, and confusion matrix.

3. Feature importance & interpretation
   - Extract feature importances or model coefficients.
   - Interpret which features most influence satisfaction (e.g., online boarding, inflight wifi, seat comfort, delays).

4. Model limitations
   - Briefly discuss assumptions, potential data issues (e.g., survey bias, missing delay values), and how a TPO would address them via backlog items and NFRs.

### 7. Product & backlog implications (TPO lens)
This section ties analytics back to product management responsibilities similar to the Emirates Technical Product Owner – Platforms role.

#### 7.1 Example epics and user stories
- Passenger communication & delay management
  - “As a frequent business traveller, I want timely and transparent notifications when delays exceed 30 minutes so that I can adjust my plans and maintain trust in the airline.”

- Digital experience improvements
  - “As an economy passenger, I want a smoother online booking and boarding experience so that I can complete my journey with fewer frustrations.”

- Experience for loyal customers
  - “As a loyal customer, I want consistent service quality across flights so that I feel rewarded for my loyalty and remain satisfied.”

#### 7.2 BAU, NFRs, and technical debt
- BAU analytics: ongoing monitoring of satisfaction KPIs by segment and service area, with quarterly reviews of top drivers.
- NFRs: data freshness, data quality metrics for delay and service-rating fields, performance of dashboards and query layers.
- Technical debt: improving inconsistent or missing delay data, standardising rating scales, and enriching the dataset with additional operational fields.

#### 7.3 Data product & documentation
- Proposed artefacts for an ACoE-style data product:
  - KPI dictionary for satisfaction metrics.
  - Business metadata (entity definitions, relationships, KPI ownership) and user guides for analytics consumers, aligning with enterprise data and analytics guidelines.

### 8. How this maps to a Technical Product Owner role
This project is designed to demonstrate:
- Ownership of data and information products: clear KPIs, dashboards and analytical views focused on passenger satisfaction and operations.
- Backlog management: translating insights into features, BAU, NFRs, and technical debt items for analytics and customer experience platforms.
- Collaboration with data & engineering teams: defining data requirements, quality improvements, and modeling outcomes that support decision-making.
- Analytics mindset: using EDA and simple models to quantify impact, prioritise work, and measure success through metrics.

### 9. How to run this project
1. Clone the repository.
2. Download the Kaggle dataset and place it under
   data/raw/airline_passenger_satisfaction.csv.

3. Create a virtual environment and install dependencies:


```bash
pip install -r requirements.txt
```

Launch Jupyter and run the notebooks in order:

```bash
jupyter lab
```

Recommended order:
1. `notebooks/00_data_cleaning.ipynb` – generate the processed CSV.
2. `notebooks/01_eda_kpis.ipynb` – perform EDA and derive insights.
3. `notebooks/02_modeling_backlog.ipynb` – experiment with models and capture backlog ideas.