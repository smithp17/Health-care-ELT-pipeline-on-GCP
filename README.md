# Airflow DAG: Load and Transform CSV Data from GCS to BigQuery

This repository contains an Apache Airflow DAG that automates the process of loading a CSV file from Google Cloud Storage (GCS) into BigQuery, creating country-specific tables, and generating views with filtered data for reporting purposes.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Dependencies](#dependencies)
- [DAG Structure](#dag-structure)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Execution](#execution)
- [License](#license)

## Overview

The DAG automates the following tasks:
1. Checks for the existence of a CSV file in a specified GCS bucket.
2. Loads the CSV file into a staging table in BigQuery.
3. Creates country-specific tables based on the data in the staging table.
4. Generates views with filtered and transformed data for reporting.

## Features

- GCS-to-BigQuery integration for seamless data loading.
- Automated creation of country-specific tables and views.
- Modular and scalable DAG structure.
- Utilizes Airflow operators for efficient task management.

## Dependencies

This project requires the following Airflow providers:
- `apache-airflow-providers-google`
- `google-cloud-bigquery`
- `google-cloud-storage`

## DAG Structure

The DAG `load_and_transform_view` is structured as follows:
1. **Task: Check File Exists**  
   Verifies if the `global_health_data.csv` file exists in the GCS bucket.

2. **Task: Load CSV to BigQuery**  
   Loads the CSV file into the `staging_rawdata` dataset in BigQuery.

3. **Task: Create Country-Specific Tables**  
   Creates tables for countries (e.g., USA, India, Germany) in the `transform_dataset` dataset.

4. **Task: Create Reporting Views**  
   Creates views for each country-specific table with selected fields and filters in the `reporting_dataset` dataset.

5. **Task: Success**  
   Final task indicating successful completion of the DAG.

## Getting Started

1. **Clone the Repository**  
   ```bash
   git clone <repository-url>
   cd <repository-directory>
