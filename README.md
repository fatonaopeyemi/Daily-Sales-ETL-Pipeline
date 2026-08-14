# Daily Sales ETL Pipeline with Machine Learning

## Overview

The Daily Sales ETL Pipeline is an end-to-end Data Engineering and Machine Learning project developed to automate the processing and reporting of supermarket sales transactions from kaggle by Fares Ashraf.
The project addresses the problem of manual and time-consuming sales reporting by implementing an automated Extract, Transform, and Load (ETL) pipeline.
The pipeline extracts raw sales data, cleans and transforms the data, generates daily sales summaries, and stores the processed data in CSV and SQLite formats.

Machine Learning models were also developed to predict sales performance using historical transaction data.

## Problem Statement

Many businesses rely on manually generated daily sales reports. This process can be time-consuming, prone to human error, and inefficient for timely business decision-making.
Automating the reporting process can improve data accuracy, reduce processing time, and provide businesses with structured information for better decision-making.
This project demonstrates how an automated ETL pipeline can simplify daily sales reporting while incorporating Machine Learning for predictive analysis.

## Project Objectives

The objectives of this project are to:

* Design and implement an automated ETL pipeline.
* Extract supermarket transaction data from a CSV dataset.
* Clean and transform raw transactional data.
* Generate meaningful daily sales summaries.
* Store processed data in CSV and SQLite formats.
* Automate the ETL process using a scheduler.
* Develop Machine Learning models for sales prediction.
* Compare Decision Tree and Random Forest models.
* Evaluate model performance.
* Demonstrate a practical Data Engineering and Machine Learning workflow using Python.

## Dataset

The project uses the SuperMarket Analysis dataset obtained from Kaggle.
The dataset contains supermarket transaction records including customer information, product details, transaction dates, quantities sold, payment methods, sales values, and customer ratings.

### Dataset Features

* Invoice ID
* Branch
* City
* Customer Type
* Gender
* Product Line
* Unit Price
* Quantity
* Tax (5%)
* Sales
* Date
* Time
* Payment
* Rating
  
## Technology Stack

* Python
* Pandas
* NumPy
* Scikit-learn
* SQLite
* Matplotlib
* Seaborn
* Google Colab
* Schedule
* Git
* GitHub

## ETL Workflow

The project follows three main ETL stages:

### 1. Extract
The extraction stage reads the raw supermarket sales dataset from a CSV file using Pandas.
The raw dataset is loaded into a Pandas DataFrame for processing.

```python
df = pd.read_csv("SuperMarket Analysis.csv")
```

### 2. Transform
The transformation stage prepares the raw data for reporting and analysis.
The following operations are performed:

* Convert the Date column to datetime format.
* Remove unnecessary whitespace.
* Standardize categorical text fields.
* Create Year, Month, Day, and Weekday features.
* Group transactions by date.
* Calculate daily sales metrics.

The daily sales summary contains:
* Total Daily Sales
* Number of Transactions
* Total Quantity Sold
* Average Daily Sales

### 3. Load
The transformed daily sales data is stored in two formats.

**CSV**

```text
daily_sales_summary.csv
```
The CSV file provides a portable daily sales report that can be opened using spreadsheet applications.

**SQLite**
```text
daily_sales.db
```
The SQLite database stores the processed sales information in a structured database for future querying and analysis.

## ETL Functions

The ETL pipeline was organized into four modular functions:

### extract()
Reads the raw supermarket dataset from the CSV file.

### transform(df)
Cleans, transforms, and aggregates the transaction data.

### load(daily_sales)
Saves the transformed data into CSV and SQLite formats.

### etl_pipeline()
Runs the complete ETL workflow from extraction to loading.

The complete pipeline can be executed using:

```python
etl_pipeline()
```

## Pipeline Scheduling

The Python Schedule library was used to automate the execution of the ETL pipeline.

Example:

```python
schedule.every().day.at("18:00").do(etl_pipeline)
```
This allows the pipeline to run automatically at a predefined time.
In a production environment, the scheduling process could be integrated with tools such as Windows Task Scheduler, Cron, or Apache Airflow.

## Machine Learning

Following the ETL process, Machine Learning models were developed to predict sales values using historical transaction data.
The Machine Learning task was treated as a regression problem because the target variable, Sales, is a continuous numerical value.

### Features
The following features were used:

* Branch
* City
* Customer Type
* Gender
* Product Line
* Unit Price
* Quantity
* Payment

### Target Variable
```text
Sales
```

### Models
Two regression models were implemented:
* Decision Tree Regressor
* Random Forest Regressor

## Model Evaluation
The models were evaluated using:

* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)
* R² Score

### Results
**Decision Tree Regressor**
* MAE: 0.04
* RMSE: 0.25
* R² Score: 0.8890

**Random Forest Regressor**
* MAE: 0.05
* RMSE: 0.28
* R² Score: 0.8634

### Model Interpretation
The Decision Tree Regressor achieved better regression performance than the Random Forest Regressor.
It achieved:
* Lower MAE
* Lower RMSE
* Higher R² Score

Therefore, the Decision Tree was the better-performing regression model on the evaluated dataset.

## Additional Classification Experiment
An additional classification experiment was also performed as part of the project.
Both Decision Tree and Random Forest achieved approximately 96.5% accuracy, with high Precision, Recall, and F1-Score and very few misclassifications.
Confusion matrices were also used to evaluate the classification results.
This classification experiment is separate from the main sales prediction task, which is a regression problem.

## Business Value
The project provides several business benefits:

* Reduces manual sales reporting.
* Improves reporting accuracy.
* Produces consistent daily sales summaries.
* Reduces the time required to process sales data.
* Provides structured historical sales information.
* Supports faster business decision-making.
* Introduces predictive analytics for sales performance.
* Provides a foundation for a scalable data engineering workflow.
  
## Future Enhancements

Potential improvements include:
* Integration with PostgreSQL.
* Integration with AWS S3.
* Development of a Power BI or Tableau dashboard.
* Real-time sales data processing.
* Deployment as a REST API using FastAPI or Flask.
* Hyperparameter tuning.
* Cross-validation.
* Docker containerization.
* Cloud deployment.
* Apache Airflow integration.
* Automated model retraining.

## Conclusion
This project demonstrates the practical implementation of an end-to-end ETL pipeline for automating supermarket sales reporting.
The pipeline extracts raw transaction data, performs data cleaning and transformation, generates daily sales summaries, and stores the processed data in both CSV and SQLite formats.

Machine Learning models were also developed to predict sales values using transaction characteristics.
Based on the evaluation results, the Decision Tree Regressor achieved the best regression performance, recording the lowest MAE and RMSE and the highest R² Score.

Overall, the project demonstrates how Data Engineering and Machine Learning can be combined to automate reporting, improve data accessibility, and support data-driven business decision-making.
