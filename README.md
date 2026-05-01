# Energy Consumption Analysis Dashboard (Aws + Snowflake + Tableau)

## Dashboard link : 
https://public.tableau.com/app/profile/phani.naidu.kondapalli/viz/Energyconsumptionanalysis/Dashboard

## Dashboard Preview : 
![dash](https://github.com/user-attachments/assets/e648dab7-be08-4870-bd82-c5253a84f238)

(Insert your dashboard screenshot here)

## Problem Statement : 

This dashboard analyzes global household energy consumption patterns across regions, income levels, and energy sources.

It helps stakeholders understand:

How energy usage varies across different regions and countries
The impact of income levels on energy consumption
Adoption trends of renewable energy sources
Cost savings associated with different energy sources

The goal is to provide insights for energy planning, sustainability strategies, and policy decisions.

## Dataset Description :

The dataset consists of 1,000 records representing household-level energy consumption.

Key Columns:
- Household_ID – Unique household identifier
- Region / Country – Geographic classification
- Energy_Source – Type of energy (Solar, Wind, Hydro, etc.)
- Monthly_Usage_kWh – Energy consumption
- Income_Level – Low, Middle, High
- Household_Size – Number of people
- Urban_Rural – Location type
- Adoption_Year – Year of energy source adoption
- Subsidy_Received – Government support indicator
- Cost_Savings_USD – Savings from energy usage

## Data Source & Data Preparation :

Data stored in AWS S3 bucket
Integrated with Snowflake Data Warehouse
Cloud Setup:
Created S3 bucket for data storage
Configured IAM roles & permissions
Connected AWS S3 with Snowflake
Created:
Database
Warehouse
Tables
Loaded dataset into Snowflake
Data Transformation (SQL in Snowflake):

![aws](https://github.com/user-attachments/assets/f9d0bfe1-275f-4092-a95d-d940663183ee)



1. Adjusted Energy Consumption based on Income Level:

update energy_consumption
set monthly_usage_kwh = monthly_usage_kwh * 1.1
where income_level = 'Low';

update energy_consumption
set monthly_usage_kwh = monthly_usage_kwh * 1.2
where income_level = 'Middle';

update energy_consumption
set monthly_usage_kwh = monthly_usage_kwh * 1.2
where income_level = 'High';




2. Adjusted Cost Savings:
update energy_consumption
set cost_savings_usd = 
case 
    when income_level = 'Low' then 0.9 * cost_savings_usd
    when income_level = 'Middle' then 0.8 * cost_savings_usd
    when income_level = 'High' then 0.7 * cost_savings_usd
end;


![snowflae](https://github.com/user-attachments/assets/d45ca133-b333-4d18-bb56-1c92141ce962)


3. Tableau Data Connection
Connected Tableau Desktop → Snowflake
Authenticated using server credentials
Imported dataset into Tableau
Verified:
Data types
Column structure





## Steps Followed : 
- Connected Tableau to Snowflake data warehouse
- Validated dataset structure and data types
- Created visualizations:
  - KPI Cards (Total Usage, Households, Income Levels)
  - Bar Charts (KWH by Region, CSU by Region)
  - Map Visuals (Country-level distribution)
  - Pie Charts (Energy Source distribution)
- Applied filters and formatting
- Designed dashboard layout for clarity and storytelling


## Key Insights : 

- Energy Usage by Region:
Asia and Africa show the highest energy consumption (~41K KWH)
North America has comparatively lower consumption (~20K KWH)

![region](https://github.com/user-attachments/assets/d19e5dbc-4507-40ea-b9e0-451dd57081a3)

- Energy Source Distribution :
Wind energy dominates total usage
Followed by:
Hydro
Solar
Biomass
Geothermal
Indicates a strong inclination toward renewable energy sources

![source](https://github.com/user-attachments/assets/38bd6c02-281a-4eb4-911e-6a18b109d34f)

-  Income Level Impact
Middle-income households form the largest segment
Energy consumption increases with income level adjustments
Cost savings decrease proportionally for higher income groups

![income](https://github.com/user-attachments/assets/d6c178eb-35a0-45b1-91dc-75051d720e10)

- Geographic Insights
Countries like India, Argentina, and New Zealand show varying consumption patterns
Regional differences highlight diverse energy adoption trends

- Cost Savings Analysis
Lower income groups retain higher percentage savings
Higher income groups show reduced relative savings, possibly due to higher consumption patterns


## Tools & Technologies Used
- Tableau Desktop – Data visualization & dashboard creation
- Snowflake – Cloud data warehouse
- AWS S3 – Data storage
- SQL – Data transformation and updates
- AWS IAM – Access and role management

## Conclusion :

This dashboard provides a comprehensive overview of energy consumption patterns across different regions, income levels, and energy sources.

It enables stakeholders to:

- Identify high-consumption regions
- Understand the role of income in energy usage
- Evaluate renewable energy adoption
- Make data-driven sustainability decisions
