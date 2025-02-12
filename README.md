# IOWA-liquor-sales
data engineering project on extracting loading transforming and displaying the liquor sales data using GCP, kestra and DBT.

## Overview
This project automates the extraction, transformation, and visualization of Iowa Liquor Sales data. The data is fetched from the **Iowa.gov API** and processed using **Kestra**, an orchestration tool running inside Docker. The extracted data is loaded into a **Google Cloud Storage (GCS) bucket**, transformed in **BigQuery** using **dbt**, and visualized in **Looker Studio**.

## Features
- **Automated Data Extraction**: Scheduled monthly data fetch from the [Iowa Liquor Sales API](https://data.iowa.gov/resource/m3tr-qhgy.json).
- **Orchestration with Kestra**: Manages and automates the data workflow.
- **Data Storage & Transformation**:
  - Raw data stored in **GCS**.
  - Staging table created in **BigQuery**.
  - Data merged into the **liquor_sales** table.
  - **dbt** used to transform and clean data.
- **Dashboard with Looker Studio**: Provides insights into liquor sales trends.

## 📁 Repository Structure
```
📂 Iowaliquorsales-dbt-pipeline
├── 📂 models             # dbt models for data transformation
│   ├── core             # Core transformation models
│   ├── staging          # Staging models
├── 📂 tests             # dbt tests and validations
├── 📂 macros            # dbt macros
├── 📂 seeds             # Seed data (if any)
├── 📂 scripts           # Python scripts for additional processing
├── 📂 kestra            # Kestra YAML workflow files
├── project_dbt.yml      # dbt project configuration
├── README.md            # Project documentation
└── requirements.txt     # Python dependencies
```

## Explore the Repository
- **Kestra Flows**: Defines the workflow for extracting and loading data.
- **dbt Models**: Handles data transformations and schema management in BigQuery.
- **Looker Dashboard**: Connects to BigQuery for interactive data visualization.

## Project Workflow
1. **Data Extraction**:
   - The Kestra workflow fetches monthly liquor sales data from the **Iowa.gov API**.
   - The data is stored in a **Google Cloud Storage bucket**.
2. **Data Loading & Transformation**:
   - A staging table is created in **BigQuery**.
   - Data is merged into the **liquor_sales** table.
   - **dbt** applies transformations and creates an analytical model.
3. **Dashboard & Analysis**:
   - The transformed table is used as a source for **Looker Studio**.
   - The dashboard provides insights into sales trends, popular products, and revenue patterns.

## Technologies Used
### Languages:
- SQL
- Python

### Libraries:
- `requests` (for API calls)
- `pandas` (for data manipulation)
- `google-cloud-storage` (for GCS interactions)
- `dbt-core` (for data transformations)

## Tools
- **Kestra**: Orchestration tool for workflow automation.
- **BigQuery**: Cloud-based data warehouse for storage and transformation.
- **Looker Studio**: Dashboard visualization.
- **Jupyter Notebook**: Interactive data exploration and analysis.
- **GitHub**: Version control and collaboration.

## Prerequisites
- **Python 3.8 or higher**
- **Jupyter Notebook**
- **Google Cloud account** with BigQuery and GCS enabled
- **Docker** (for running Kestra)

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/your-username/iowa-liquor-sales.git
   cd iowa-liquor-sales
   ```
2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
3. Set up Google Cloud credentials:
   ```sh
   export GOOGLE_APPLICATION_CREDENTIALS="path/to/your/service-account.json"
   ```
4. Start Kestra using Docker:
   ```sh
   docker-compose up
   ```
5. Run dbt transformations:
   ```sh
   dbt run
   ```
6. Open Looker Studio and connect it to the BigQuery dataset.

## Looker Dashboard
The final dashboard, hosted in **Looker Studio**, provides interactive visualizations for liquor sales data, including:
- **Sales Trends Over Time**
- **Top-Selling Liquor Categories**
- **Revenue Breakdown by Store & Location**

📊 **[View Liquor sales Dashboard](https://lookerstudio.google.com/reporting/b0691325-01aa-4730-993c-626374417d7b)**


