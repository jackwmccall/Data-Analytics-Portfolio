# -Mini SQL Case Study- Pharmaceutical Drug Spending by Country

For the following mini case study I will be looking at a dataset provided from the Organisation for Economic Cooperation and Development (OECD). This specific dataset covers pharmaceutical drug spending by country including information such as total spent per year, percent makeup of GDP, and USD spent per capita.

***

### 1. How many distinct countries exist in the dataset?

````sql
SELECT COUNT(DISTINCT Location) AS Total_Countries
FROM Spending;
````

**Answer:**

<kbd><img src="https://github.com/user-attachments/assets/b3c72d64-32de-46f2-8345-ebba5f698bf6" width="141" />

There are 44 distinct countries in the dataset. 

***

### 2. Which 3 countries spent the highest amount of $/Capita in 2019?

````sql
SELECT Location, USD_CAP
FROM spending
WHERE TIME = 2019
ORDER BY USD_CAP DESC
LIMIT 3;
````

**Answer:**

<kbd><img src="https://github.com/user-attachments/assets/dd9bbe95-d6c2-46bb-bd60-e5eda2995bcc" width="180" />

The top 3 countries in pharmaceutical drug expenditures/capita in 2019 were the United States, Japan, and Germany.

***

### 3. From 1990 to 2021 how much did the United States spent on pharmaceutical drugs?

````sql
SELECT SUM(TOTAL_SPEND)
FROM SPENDING
WHERE TIME BETWEEN '1990' AND '2021' AND Location = "USA";
````

<kbd><img src="https://github.com/user-attachments/assets/1f978798-3b92-409a-b825-541f16e413ef" width="141" />

From 1990-2021 the United States spent over 7 trillion USD on pharmaceutical drugs. 

***

### 4. Rank the top 5 countries by their average pharmaceutical drug expenditures as a percentage of GDP from 2010 to 2015.

````sql
SELECT location,
AVG(PC_GDP) AS avg_pc_gdp,
RANK() OVER (ORDER BY AVG(PC_GDP) DESC) AS Country_Rank
FROM spending
WHERE time BETWEEN 2010 and 2015
GROUP BY location
ORDER BY Country_Rank
LIMIT 5;
````

**Answer:**

<kbd><img src="https://github.com/user-attachments/assets/b12949be-654c-4f75-ae96-59321f6fc2c8" width="260" />

In terms of percentage of GDP, the countries with the highest averages from 2010 to 2015 are Bulgaria, Greece, Hungary, the United States, and Japan.

***

### 5. Take the 5 countries from the previous question and calculate a year by year rolling cumulative total of their combined pharmaceutical drug expenditures from 2010 to 2015.

````sql
WITH individual_yearly_expenditures AS
(
SELECT 
    location,
    time,
    total_spend
FROM spending
WHERE time BETWEEN 2010 and 2015 AND location IN ('BGR', 'GRC', 'HUN', 'USA', 'JPN')
)
SELECT  
    time,
    SUM(total_spend) AS combined_yearly_expenditures,
    SUM(SUM(total_spend)) OVER(ORDER BY time ASC ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS rolling_cumulative_total
FROM individual_yearly_expenditures
GROUP BY time
ORDER BY time ASC;
````

**Answer:**

<kbd><img src="https://github.com/user-attachments/assets/ddb213ce-c7ba-4945-81e4-f4f8cc82556c" width="380" />

From 2010 to 2015 Bulgaria, Greece, Hungary, the United States, and Japan combined spent a total of over 2.5 trillion USD on pharmaceutical drugs. We can then follow up with the below query to determine the United States share of that spending.

````sql
SELECT SUM(total_spend)
FROM spending
WHERE location = 'USA' AND time BETWEEN 2010 AND 2015;
````

From the above query we find out that the United States spent just over 1.9 trillion alone from 2010 to 2015 and thus made up just under 75% of the total expenditures of pharmaceutical drugs from the previous listed 5 countries.

Note: The dataset did not include data from Bulgaria from 2010 or 2011 which resulted in skewed results. 
