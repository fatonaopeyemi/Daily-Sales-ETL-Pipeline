
ETL pipeline for transforming daily supermarket sales data into  systematic useful business report.

**Daily Sales ETL Pipeline with Machine Learning**

Overview
The Daily Sales ETL Pipeline is an end-to-end data engineering and machine learning project developed to automate the processing of supermarket sales transactions. The project addresses the challenge of manual and time-consuming sales reporting by implementing an automated Extract, Transform, and Load (ETL) pipeline that generates daily sales summaries and stores the processed data in multiple formats for reporting and analysis.

In addition to the ETL process, machine learning models were developed to analyze sales patterns and predict sales performance using historical transaction data.

**Problem Statement**
Many businesses rely on manually generated daily sales reports, which are often inefficient, prone to human error, and unsuitable for timely business decision-making. Automating the reporting process improves data quality, reduces processing time, and enables managers to make faster, data-driven decisions.

This project demonstrates how an automated ETL pipeline can simplify daily sales reporting while incorporating predictive analytics to support business intelligence.

**Project Objectives**
The objectives of this project are to:

Design and implement an automated ETL pipeline for daily sales reporting.
Extract supermarket transaction data from a CSV dataset.
Clean, validate, and transform raw transactional data into meaningful daily summaries.
Store processed data in both CSV and SQLite database formats.
Develop machine learning models for sales prediction.
Evaluate and compare the performance of Decision Tree and Random Forest algorithms.
Demonstrate a practical data engineering workflow using Python.
Dataset Description
This project uses the SuperMarket Analysis dataset obtained from Kaggle.

The dataset contains transactional records collected from supermarket branches and includes customer information, product details, payment methods, transaction dates, quantities sold, and sales values.

Dataset Features
Invoice ID
Branch
City
Customer Type
Gender
Product Line
Unit Price
Quantity
Tax (5%)
Sales
Date
Time
Payment Method
Rating
Technology Stack
Category	Technology
Programming Language	Python
Data Processing	Pandas, NumPy
Machine Learning	Scikit-learn
Database	SQLite
Development Environment	Jupyter Notebook / Google Colab
Scheduling	Schedule Library
Project Architecture
                Raw CSV Dataset
                       │
                       ▼
                 Extract Stage
             (Read CSV with Pandas)
                       │
                       ▼
               Transform Stage
      • Data Cleaning
      • Date Conversion
      • Text Standardization
      • Daily Sales Aggregation
                       │
                       ▼
                  Load Stage
        ┌─────────────────────────┐
        │                         │
        ▼                         ▼
CSV Report                SQLite Database
        │                         │
        └──────────────┬──────────┘
                       ▼
          Machine Learning Models
       • Decision Tree Regressor
       • Random Forest Regressor
                       │
                       ▼
             Model Evaluation
ETL Workflow
1. Extract
The extraction stage reads the raw supermarket sales dataset from a CSV file using the Pandas library.

Output:

Raw transaction DataFrame
2. Transform
The transformation stage prepares the dataset for analysis by performing the following operations:

Converted the Date column into datetime format.

Standardized categorical text fields.

Removed unnecessary whitespace.

Generated a daily sales summary by grouping transactions according to date.

Calculated key business metrics including:

Total Daily Sales
Number of Transactions
Total Quantity Sold
Average Daily Sales
The transformed data provides a concise representation of daily business performance.

3. Load
The transformed daily sales summary is exported into two different storage formats:

CSV Output
daily_sales_summary.csv
Provides a portable report that can easily be opened using spreadsheet software.

SQLite Database
daily_sales.db
Stores the processed data in a relational database for future querying and analytical applications.

ETL Functions
To improve code readability, maintainability, and reusability, the ETL process was organized into four modular functions:

Function	Description
extract()	Reads the raw dataset from the CSV file.
transform(df)	Cleans, transforms, and summarizes the data.
load(daily_sales)	Saves the transformed data into CSV and SQLite.
etl_pipeline()	Executes the complete ETL workflow from extraction to loading.
Pipeline Scheduling
To support automation, the ETL pipeline was configured using the Python Schedule library.

This enables the pipeline to execute automatically at predefined times without manual intervention. In a production environment, the scheduler can be integrated with operating system schedulers such as Windows Task Scheduler or Cron.

**Machine Learning**
Following the ETL process, predictive models were developed to estimate sales using historical transaction data.

Features
Branch
City
Customer Type
Gender
Product Line
Unit Price
Quantity
Payment Method
Target Variable
Sales
Machine Learning Models
Two regression algorithms were implemented:

Decision Tree Regressor
Random Forest Regressor
These models were trained to predict sales values based on transaction characteristics.

Model Evaluation
The predictive models were evaluated using standard regression performance metrics.

Metric	Decision Tree	Random Forest
Mean Absolute Error (MAE)	0.04	0.05
Root Mean Squared Error (RMSE)	0.25	0.28
R² Score	0.8890	0.8634
Interpretation
The Decision Tree model achieved:

Lower Mean Absolute Error
Lower Root Mean Squared Error
Higher R² Score
These results indicate that the Decision Tree provided slightly more accurate predictions than the Random Forest model on the available dataset.

Classification Evaluation
As part of the comparative analysis, classification experiments were also performed.

Both Decision Tree and Random Forest achieved:

Accuracy: 96.5%
High Precision
High Recall
High F1-Score
Very few misclassifications according to the Confusion Matrix
This demonstrates that both algorithms were highly effective in classification tasks, although the Decision Tree produced superior performance when evaluated as a regression model.

Project Structure
Daily-Sales-ETL-Pipeline/
│
├── Daily_Sales_ETL.ipynb
├── SuperMarket Analysis.csv
├── daily_sales_summary.csv
├── daily_sales.db
├── README.md
├── requirements.txt
└── images/
How to Run the Project
Clone the repository.

Install the required dependencies.

pip install -r requirements.txt
Open the notebook using Jupyter Notebook or Google Colab.

Execute all notebook cells sequentially.

Run the ETL pipeline.

etl_pipeline()
Review the generated CSV report and SQLite database.

Train and evaluate the machine learning models.

Business Value
The developed ETL pipeline provides several business benefits:

Eliminates manual sales reporting.
Improves reporting accuracy.
Produces consistent daily sales summaries.
Enables faster business decision-making.
Supports predictive analytics for sales forecasting.
Demonstrates a scalable workflow for data engineering projects.
Future Enhancements
Potential improvements include:

Integration with cloud storage and cloud databases.
Development of an interactive dashboard using Power BI or Tableau.
Real-time streaming of sales transactions.
Deployment as a REST API using Flask or FastAPI.
Hyperparameter tuning to further improve model performance.
Containerization using Docker for production deployment.
Conclusion
This project successfully demonstrates the implementation of a complete Extract, Transform, Load (ETL) pipeline for automating daily supermarket sales reporting. The pipeline extracts raw transactional data, performs data cleaning and aggregation, and loads the processed information into both CSV and SQLite formats for reporting and future analysis.

To extend the analytical capabilities of the pipeline, Decision Tree and Random Forest regression models were developed to predict sales from transaction characteristics. Model evaluation showed that the Decision Tree Regressor achieved the best overall performance, recording the lowest prediction errors and the highest R² score among the evaluated models.

Overall, the project highlights the practical integration of data engineering and machine learning techniques to automate reporting, improve data accessibility, and support informed business decision-making.
