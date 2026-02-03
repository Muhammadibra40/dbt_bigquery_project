# dbt BigQuery Project

This repository contains a **dbt (Data Build Tool)** project configured to run SQL transformations in **BigQuery**.  
It follows dbt’s recommended structure for organizing models, configurations, and tests. :contentReference[oaicite:0]{index=0}

---

## About

This project is built as a core dbt transformation pipeline. It includes:
- Modular SQL models
- dbt configurations and definitions
- Version control via Git
- BigQuery as the data warehouse

It helps transform raw data into analytics-ready datasets.

---

## Project Structure

```

├── models/
│   └── sales_analytics/        # dbt transformation models
├── snapshots/                  # Historical snapshot definitions
├── tests/                     # dbt tests
├── macros/                    # Custom dbt macros
├── dbt_project.yml           # Project configuration
├── profiles.yml (local)      # Connection settings (not committed)
├── .gitignore
└── README.md

````

This structure aligns with dbt’s best practices for organizing code and models. :contentReference[oaicite:1]{index=1}

---

## How to Get Started

### 1. Install dbt
Install dbt and the BigQuery adapter:

```bash
pip install dbt-core dbt-bigquery
````

---

### 2. Authenticate with BigQuery

Set up your authentication, commonly via:

```bash
gcloud auth application-default login
```

Then configure `profiles.yml` with your GCP project and dataset. ([dbt Developer Hub][1])

---

### 3. Run dbt Commands

```bash
dbt debug      # Verify your connection
dbt run        # Build models
dbt test       # Run tests
dbt docs generate
dbt docs serve
```

---

## Conventions

* Use `{{ ref('model_name') }}` to reference models — this builds dependency graphs. ([B EYE][2])
* Structure models into layers (e.g., staging → intermediate → marts) for maintainability. ([Hevo Data][3])
* Document your models and columns using YAML for auto-generated docs.

---

## Generate Documentation

To generate HTML docs for your project:

```bash
dbt docs generate
dbt docs serve
```

This creates a local web interface showing lineage and schema details. ([dbt Developer Hub][1])

---

## Why dbt + BigQuery?

dbt enables you to write modular SQL, track dependencies, add tests, and version-control analytics transformations.
BigQuery serves as the high-performance data warehouse where dbt runs queries. ([datadoghq.com][4])

---
