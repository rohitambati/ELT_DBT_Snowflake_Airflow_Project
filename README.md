
# ETL Project: Modern Data Transformation and Loading with DBT, Snowflake, and Airflow

## Project Description

In the past, due to the high cost of cloud storage, data was transformed before being loaded. With the decrease in storage costs, we now load data first and transform it as needed. This project demonstrates how to build fact tables and data marts, manage Snowflake Role-Based Access Control (RBAC), and deploy models on Airflow.

## Objectives
- Building fact tables
- Creating data marts
- Managing Snowflake RBAC
- Deploying models on Airflow

## Tools Used
- **DBT**: Data transformation
- **Snowflake**: Data warehousing
- **Airflow**: Orchestration
- **Docker**
- **Python**

## Dataset
- **Snowflake TPCH**: A free dataset provided by Snowflake.

## Steps

### Step 1: Setup Snowflake Environment
Configure and prepare your Snowflake environment for data warehousing.

### Step 2: Configure `dbt_profile.yml`
Set up your DBT profile to connect to the Snowflake environment.

### Step 3: Create Source and Staging Files
Define your source data and staging tables.

### Step 4: Macros
Create reusable SQL snippets using DBT macros.

### Step 5: Transform Models
Develop transformation models to build fact tables and data marts.

### Step 6: Generic and Singular Tests
Implement data quality tests to validate your models.

### Step 7: Deploy on Airflow
Deploy your DBT models using Airflow for orchestration.

## Notes

### Project Structure
- **`dbt.yml`**: This file designates the main project folder and contains information about models, tests, seeds, macros, etc.
- **`DBT_project.yml`**: Specifies where DBT should look for the models.
- **Models Folder**: Contains SQL logic, source datasets, and staging files. It's a good practice to separate staging files using marts folders.
- **Seeds Folder**: For static files that don't change often.
- **Snapshots Folder**: Useful for creating incremental models.

### Tables to Create
- **Staging**: Materialized as a view.
- **Marts**: Materialized as a table.

### Additional Notes
- Install third-party libraries for creating surrogate keys, which are useful in dimensional modeling to connect fact and dimensional tables.
- Staging tables should have a 1-to-1 relationship with source tables.
- Perform necessary transformations on staging tables based on requirements.
- Aggregate data in `line_items` to create fact tables, which store results from business processes.

### Types of Tests
- **Singular Data Test**
- **Generic Data Test**

Refer to the DBT documentation for more details on these tests.

## References
- [DBT Core](https://pypi.org/project/dbt-core/)
- [DBT Profiles Configuration](https://docs.getdbt.com/docs/core/connect-data-platform/profiles.yml)
- [Fact Table Structure](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/fact-table-structure/)
- [DBT Jinja Macros](https://docs.getdbt.com/docs/build/jinja-macros)
- [Astronomer Cosmos](https://github.com/astronomer/astronomer-cosmos)

---

Overview
========

Welcome to Astronomer! This project was generated after you ran 'astro dev init' using the Astronomer CLI. This readme describes the contents of the project, as well as how to run Apache Airflow on your local machine.

Project Contents
================

Your Astro project contains the following files and folders:

- dags: This folder contains the Python files for your Airflow DAGs. By default, this directory includes one example DAG:
    - `example_astronauts`: This DAG shows a simple ETL pipeline example that queries the list of astronauts currently in space from the Open Notify API and prints a statement for each astronaut. The DAG uses the TaskFlow API to define tasks in Python, and dynamic task mapping to dynamically print a statement for each astronaut. For more on how this DAG works, see our [Getting started tutorial](https://docs.astronomer.io/learn/get-started-with-airflow).
- Dockerfile: This file contains a versioned Astro Runtime Docker image that provides a differentiated Airflow experience. If you want to execute other commands or overrides at runtime, specify them here.
- include: This folder contains any additional files that you want to include as part of your project. It is empty by default.
- packages.txt: Install OS-level packages needed for your project by adding them to this file. It is empty by default.
- requirements.txt: Install Python packages needed for your project by adding them to this file. It is empty by default.
- plugins: Add custom or community plugins for your project to this file. It is empty by default.
- airflow_settings.yaml: Use this local-only file to specify Airflow Connections, Variables, and Pools instead of entering them in the Airflow UI as you develop DAGs in this project.

Deploy Your Project Locally
===========================

1. Start Airflow on your local machine by running 'astro dev start'.

This command will spin up 4 Docker containers on your machine, each for a different Airflow component:

- Postgres: Airflow's Metadata Database
- Webserver: The Airflow component responsible for rendering the Airflow UI
- Scheduler: The Airflow component responsible for monitoring and triggering tasks
- Triggerer: The Airflow component responsible for triggering deferred tasks

2. Verify that all 4 Docker containers were created by running 'docker ps'.

Note: Running 'astro dev start' will start your project with the Airflow Webserver exposed at port 8080 and Postgres exposed at port 5432. If you already have either of those ports allocated, you can either [stop your existing Docker containers or change the port](https://docs.astronomer.io/astro/test-and-troubleshoot-locally#ports-are-not-available).

3. Access the Airflow UI for your local Airflow project. To do so, go to http://localhost:8080/ and log in with 'admin' for both your Username and Password.

You should also be able to access your Postgres Database at 'localhost:5432/postgres'.

Deploy Your Project to Astronomer
=================================

If you have an Astronomer account, pushing code to a Deployment on Astronomer is simple. For deploying instructions, refer to Astronomer documentation: https://docs.astronomer.io/cloud/deploy-code/

Contact
=======

The Astronomer CLI is maintained with love by the Astronomer team. To report a bug or suggest a change, reach out to our support.
