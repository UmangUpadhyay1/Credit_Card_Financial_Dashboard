# Credit Card Financial Report
![Credit card financial report](https://github.com/UmangUpadhyay1/Credit_Card_Financial_Dashboard/blob/main/image.png)

## 📦 SQL Script: Create Tables & Import Data from CSV Files

![Credit Card DB Schema](https://github.com/UmangUpadhyay1/Credit_Card_Financial_Dashboard/blob/main/ER_DIAG.png)

```sql
-- 0. Create a database 
CREATE DATABASE ccdb;

-- 1. Create cc_detail table
CREATE TABLE cc_detail (
    Client_Num INT,
    Card_Category VARCHAR(20),
    Annual_Fees INT,
    Activation_30_Days INT,
    Customer_Acq_Cost INT,
    Week_Start_Date DATE,
    Week_Num VARCHAR(20),
    Qtr VARCHAR(10),
    current_year INT,
    Credit_Limit DECIMAL(10,2),
    Total_Revolving_Bal INT,
    Total_Trans_Amt INT,
    Total_Trans_Ct INT,
    Avg_Utilization_Ratio DECIMAL(10,3),
    Use_Chip VARCHAR(10),
    Exp_Type VARCHAR(50),
    Interest_Earned DECIMAL(10,3),
    Delinquent_Acc VARCHAR(5)
);

-- 2. Create cust_detail table
CREATE TABLE cust_detail (
    Client_Num INT,
    Customer_Age INT,
    Gender VARCHAR(5),
    Dependent_Count INT,
    Education_Level VARCHAR(50),
    Marital_Status VARCHAR(20),
    State_cd VARCHAR(50),
    Zipcode VARCHAR(20),
    Car_Owner VARCHAR(5),
    House_Owner VARCHAR(5),
    Personal_Loan VARCHAR(5),
    Contact VARCHAR(50),
    Customer_Job VARCHAR(50),
    Income INT,
    Cust_Satisfaction_Score INT
);

-- 3. Import CSV data into SQL tables (update file paths accordingly)

-- Copy data into cc_detail table
COPY cc_detail
FROM 'D:\\credit_card.csv' 
DELIMITER ',' 
CSV HEADER;

-- Copy data into cust_detail table
COPY cust_detail
FROM 'D:\\customer.csv' 
DELIMITER ',' 
CSV HEADER;

-- ⚠️ Common error note:
-- ERROR:  date/time field value out of range: "0"
-- HINT:  Perhaps you need a different "datestyle" setting.

-- ✅ Suggested fix:
-- Check the date format in your CSV (e.g., YYYY-MM-DD), or
-- Set the datestyle explicitly:
SET datestyle TO 'ISO, DMY';

-- 4. Import additional data (Week 53)

-- cc_detail additional data
COPY cc_detail
FROM 'D:\\cc_add.csv' 
DELIMITER ',' 
CSV HEADER;

-- cust_detail additional data
COPY cust_detail
FROM 'D:\\cust_add.csv' 
DELIMITER ',' 
CSV HEADER;
```

