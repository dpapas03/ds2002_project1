# DS 2002 - Project 1 - AdventureWorks Data Warehouse

Author: Dino Papalabrakopoulos    Date: 3/23/2026

## Process Description
I began by selecting the business processes to model. The adventureworks database contained a wealth of transactional information, and, accordingly, I choose to model purchase orders and sales orders. For each fact table, I chose for one row to correspond to one purchase order or one sales order line, as applicable. In terms of dimensional modeling, purchase order modeling required vendor, employee, date, and product data, whereas sales order modeling required employee, date, product, address, ship method, and customer data. 

After extracting corresponding source data from the provided MySQL database, a local file, and a NoSQL database, I removed any columns used to track record updates in the source, created the dimension table precursor data frames through sequential left or inner merges of the transformed source data on appropriate business keys, renamed columns as necessary for specificity, and filtered the data frames to contain only the desired columns in the desired order. Next, I loaded the dimension table precursors to the adventureworks_dw database, assigning appropriate auto incrementing surrogate primary keys.

Following construction of the dimension tables, I extracted source data from the provided MySQL database relevant to both purchase orders and sales orders. Next, I removed any columns used to track record updates in the source, created the fact table precursor data frames through sequential left or inner merges of the transformed source data on appropriate business keys, renamed columns as necessary for specificity, and filtered the data frames to contain only the desired columns in the desired order. Using the dimension tables, I looked up the corresponding surrogate key for each business key in the fact tables and replaced each business key with its corresponding surrogate key. Next, I loaded each fact table precursor to the adventureworks_dw database, assigning appropriate auto incrementing primary keys.


## Code Description
The project utilizes Python3 with the following packages: pandas, sqlalchemy, pymongo, os, json, numpy, datetime, certifi, pymongo.
With the exception of the creation of the initial databases, view materials, and the dim_date dimension, the Project 1 Jupyter notebook contains all the code necessary for the ETL process and any subsequent test SQL queries. Adjusting for connection credentials where indicated, running the cells from top to bottom reproduces the same adventureworks_dw solution. Running the Create_Populate_Dim_Date.sql script on the MySQL server when indicated by the Project 1 notebook creates the dim_date dimension. Running the provided AdventureWorks_MySQL,sql script on the MySQL server prior to running any code in the Project 1 notebook creates the provided adventureworks database. Running the provided AdventureWorks_Queries_MySQL.sql script on the MySQL server creates the table views necessary for the alternate source creation described in the Project 1 notebook. 


## Deployment Strategy
The final warehouse deploys into a relational MySQL database, with dimensions loaded first and fact tables loaded afterward. For this project, the pipeline should be run manually following the numbering and instructions in Project 1.ipynb.
