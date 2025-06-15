# Market online sales dashbord
This notebook is designed to prepare and clean datasets before uploading them to Google BigQuery, making them ready for further analysis and dashboard creation in Looker Studio (formerly known as Data Studio).

---

## Project Overview

- Prepare dataset from Kaggle 
- Cleansing and transform data with Python, Pandas
- Export to parquet file
- Upload dataset to Google BigQuery
- Use SQL change data type of date for integer to date
- Connect to Looker Studio for create dashboard

---

## How to Use

 1. Download the code in notebook file or download raw data in data file 
        - If you use python code, Create Colab secret and config Kaggle API for download dataset
        - You can get Kaggle API on your Kaggle Profile.
 
 2. Upload parquet file to Google BigQuery by UI
        - Change column order date data type integer to date, Use below SQL command.

            ```
            CREATE TABLE `your_project.data_set.table` AS
            SELECT
                order_id,
                DATE(TIMESTAMP_MICROS(CAST(order_date / 1000 AS INT64))) AS order_date,
                usd_amount,
                usd_profit,
                quantity,
                total_amount,
                total_profit,
                category,
                sub_category,
                paymentmode,
                customername,
                state,
                city
            FROM `your_project.data_set.table`

            ```
3. Open Looker Studio, connect data in BigQuery and create dashboard

---

## Result dashboard
    ![Dashboard1](images/sales_performance.jpg)
    
    ![Dashboard2](images/Customer_Insight.jpg)

     



