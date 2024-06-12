# Credit_Card_Finance_Analysis

## Problem Statement
- In today's dynamic financial landscape, businesses face the challenge of effectively managing credit card transactions and customer data. Traditional methods of tracking and analysing this information are often time-consuming, prone to errors, and lack real-time insights. As a result, businesses struggle to detect different transaction activities, identify valuable customer segments, and make data-driven decisions to optimize their financial performance.
- In light of these challenges, our organization recognized the necessity for a comprehensive Credit Card Financial Dashboard. This dashboard aims to streamline credit card transaction management, provide actionable insights into customer behaviour, and enhance detection capabilities. By leveraging innovative data analytics and visualization techniques, our dashboard empowers businesses to proactively mitigate risks, improve operational efficiency, and ultimately, safeguard their financial assets and reputation.

## Objective
- To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

## Import data to MySQL database
1. Prepared csv file
2. Created tables in MySQL
3. imported csv file into MySQL
- Connected MySQL database to Power BI, So when will be new data comes we can load it into MySQL Credit Card database and get real time insight in dashboard.

### Created Dashboard using Power BI.

## Dax Queries

#### Using New Column
**AgeGroup =** SWITCH(
TRUE(),
'cust_detail'[customer_age] < 30, "20-30",
'cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'cust_detail'[customer_age] >= 60, "60+",
"unknown"
)

**IncomeGroup =** SWITCH(
TRUE(),
'cust_detail'[income] < 35000, "Low",
'cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'cust_detail'[income] >= 70000, "High",
"unknown"
)

**week_num2 =** WEEKNUM('cc_detail'[week_start_date])

#### Using New Measure
**Revenue =** 'cc_detail'[annual_fees] + 'cc_detail'[total_trans_amt] + 'cc_detail'[interest_earned] - 'cc_detail'[Customer_Acq_Cost]

**Current_week_Reveneue =** CALCULATE(
SUM('cc_detail'[Revenue]),
FILTER(
ALL('cc_detail'),
'cc_detail'[week_num2] = MAX('cc_detail'[week_num2])))
Previous_week_Reveneue = CALCULATE(
SUM('cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'cc_detail'[week_num2] = MAX('cc_detail'[week_num2])-1))

## Useful Insight
### WoW change:
- Revenue increased by 29%.
- Total Transaction Amt & Count increased by 35% & 3.4%.
### Overview YTD:
- Overall revenue is 55.5M.
- Total interest is 8M.
- Total transaction amount is 46M.
- Blue credit card is alone contributing to 83.36% of overall transactions.
- TX, NY & CA is contributing to 68%.
- Male customers are contributing more in revenue 30.5M, where female 25M.
- Age group of 40-50 & 50-60 are contributing to 76.76% of overall transactions.
- Overall Activation rate is 57.5%.
- Overall Delinquent rate is 6.06%.

  ## Conclusion

- In conclusion, the Credit Card Financial Dashboard presented a pivotal advancement in modern financial management. Developed an interactive dashboard using transaction and customer data from a SQL database, to provide real-time insights.

- Through real-time insights into credit card transactions and customer behaviour, businesses can make informed decisions, identify growth opportunities, and mitigate risks effectively.

- Streamlined data processing & analysis to monitor key performance metrics and trends.
As we move forward, it's essential to recognize the transformative potential of data-driven solutions in driving sustainable growth and resilience.




