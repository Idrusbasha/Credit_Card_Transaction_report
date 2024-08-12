# Credit_Card_Transaction_report
## Project Objective 
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.
## Import data to SQL database
1. Prepare csv file
2. Create tables in SQL
3. import csv file into SQL

## Project Insights- Week 53 (31st Dec)
### WoW change:
1. Revenue increased by 28.8%,
2. Total Transaction Amt & Count increased by 35% & 12%
3. Customer count increased by 13%
### Overview YTD:
1. Overall revenue is 57M
2. Total interest is 8M
3. Total transaction amount is 46M
4. Male customers are contributing more in revenue 31M, female 26M
5. Blue & Silver credit card are contributing to 93% of overall transactions
6. TX, NY & CA is contributing to 68%
7. Overall Activation rate is 57.5%
8. Overall Delinquent rate is 6.06%**

## DAX Queries
1. AgeGroup = SWITCH(  TRUE(), 'public cust_detail'[customer_age] < 30, "20-30", 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",  'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",  'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",  'public cust_detail'[customer_age] >= 60, "60+", "unknown" )

2. IncomeGroup = SWITCH( TRUE(), 'public cust_detail'[income] < 35000, "Low",'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med", 'public cust_detail'[income] >= 70000, "High", "unknown")

3. week_number = WEEKNUM('public cc_detail'[week_start_date])

4. Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

5. Current_week_Reveneue = CALCULATE( SUM('public cc_detail'[Revenue]), FILTER( ALL('public cc_detail'), 'public cc_detail'[week_number] = MAX('public cc_detail'[week_number])))

6. Previous_week_Reveneue = CALCULATE( SUM('public cc_detail'[Revenue]), FILTER( ALL('public cc_detail'), 'public cc_detail'[week_number] = MAX('public cc_detail'[week_number])-1))

