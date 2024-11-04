# Customer-Segmentation
Customer Segmentation for a Subscription Service
# Customer Segmentation for a Subscription Service

## Project Summary
This project focuses on analyzing customer data for a subscription service to identify segments and trends. The final deliverable is a Power BI dashboard that presents the analysis of customer behavior, subscription types, cancellations, and renewals.

## Objectives
- Analyze customer data to track subscription patterns and identify key trends.
- Produce insights using Excel pivot tables and SQL queries.
- Create a Power BI dashboard for visual analysis.

## Instructions

### Excel
1. Analyze customer data using pivot tables to find subscription patterns.
1. **Data Analysis:**
   - Data cleaning:
   - Removal of  duplicate data
   - Removal of empty/null data 
   - Use **Pivot Tables** to analyze customer data and find subscription patterns.
2. Calculate the average subscription duration and identify the most popular subscription types.
   - Use the following **formulas**:
     - **Average Subscription Duration:**  
       `=AVERAGE(duration_range)`
     - **Most Popular Subscription Types:**  
       Use `=MODE(subscription_type_range)` or count occurrences with `=COUNTIF()`.
     - **Total Revenue by Subscription Type:**  
       `=SUMIF(subscription_type_range, type_cell, revenue_range)`
3. Create any other interesting reports based on your findings.
   ## **Additional Reports:**
   - Create a report detailing customer cancellations and renewals.
   - Generate a report comparing average subscription duration by type.

### SQL
1. Load the dataset into your SQL Server environment.
2. Write queries to extract insights:
   - Total number of customers from each region.
   - Most popular subscription type by number of customers.
   - Customers who canceled their subscription within 6 months.
   - Average subscription duration for all customers.
   - Customers with subscriptions longer than 12 months.
   - Total revenue by subscription type.
   - Top 3 regions by subscription cancellations.
   - Total number of active and canceled subscriptions.
 ```sql
   -- Total number of customers from each region
   SELECT Region, COUNT(CustomerID) AS TotalCustomers
   FROM CustomerData
   GROUP BY Region;

   -- Most popular subscription type by number of customers
   SELECT SubscriptionType, COUNT(CustomerID) AS TotalCustomers
   FROM CustomerData
   GROUP BY SubscriptionType
   ORDER BY TotalCustomers DESC
   LIMIT 1;

   -- Customers who canceled their subscription within 6 months
   SELECT CustomerID
   FROM SubscriptionData
   WHERE DATEDIFF(MONTH, StartDate, EndDate) <= 6 AND Status = 'Canceled';

   -- Average subscription duration for all customers
   SELECT AVG(DATEDIFF(MONTH, StartDate, EndDate)) AS AverageDuration
   FROM SubscriptionData;

   -- Customers with subscriptions longer than 12 months
   SELECT CustomerID
   FROM SubscriptionData
   WHERE DATEDIFF(MONTH, StartDate, EndDate) > 12;

   -- Total revenue by subscription type
   SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
   FROM SubscriptionData
   GROUP BY SubscriptionType;

   -- Top 3 regions by subscription cancellations
   SELECT Region, COUNT(CustomerID) AS Cancellations
   FROM CustomerData
   WHERE Status = 'Canceled'
   GROUP BY Region
   ORDER BY Cancellations DESC
   LIMIT 3;

   -- Total number of active and canceled subscriptions
   SELECT Status, COUNT(CustomerID) AS TotalSubscriptions
   FROM SubscriptionData
   GROUP BY Status;
```
## Power BI

### Dashboard Overview
- Include a Customer Segmentation section to show different customer groups based on behavior.
- Create visualizations for Cancellations vs. Renewals to highlight trends.
- Use a pie chart to display the distribution of subscription types.
- Incorporate line charts for average subscription duration trends over time.
- Add interactive slicers for filtering by region, subscription type, and status.

### Subdirectories
- /excel: Store all Excel files and reports.
- /sql: Store SQL scripts for the queries used in this project.
- /powerbi: Store Power BI report files and dashboards.

### Resources
- [Excel Guide](https://support.microsoft.com/excel)
- [SQL Server Documentation](https://docs.microsoft.com/sql/sql-server/)
- [Power BI Documentation](https://docs.microsoft.com/power-bi/)
