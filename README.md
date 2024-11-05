# Customer-Segmentation

# Customer Segmentation for a Subscription Service

## Project Summary
This project focuses on analyzing customer data for a subscription service to identify segments and trends. The final deliverable is a Power BI dashboard that presents the analysis of customer behavior, subscription types, cancellations, and renewals.

## Objectives
- Clean, standardize, and normalize data for accurate analysis.
- Analyze customer data to identify subscription patterns and trends in cancellations and renewals.
- Utilize Excel pivot tables and SQL queries to derive insights from the data.
- Create an interactive Power BI dashboard to visualize the findings.

## Instructions and Applications

### Excel
1. Analyze customer data using pivot tables to find subscription patterns.

## Data Preparation

### Data Cleaning and Analysis

#### Excel
1. **Data Cleaning:**
   - **Remove Duplicates**: Use `Remove Duplicates` under the `Data` tab to eliminate any duplicate entries in customer and subscription data.
   - **Handle Missing Values**: For fields with missing values, decide whether to fill, replace, or drop them based on relevance.
   - **Date Formatting**: Standardize all date fields to a consistent format (e.g., `YYYY-MM-DD`) to ensure compatibility across tools.
   
2. **Data Analysis:**
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
   - Result: Returns the total count of customers in each region, indicating where most customers are located.

   -- Most popular subscription type by number of customers
   SELECT SubscriptionType, COUNT(CustomerID) AS TotalCustomers
   FROM CustomerData
   GROUP BY SubscriptionType
   ORDER BY TotalCustomers DESC
   LIMIT 1;
- Result: Provides the subscription type with the highest number of customers, revealing popularity by volume.

   -- Customers who canceled their subscription within 6 months
   SELECT CustomerID
   FROM SubscriptionData
   WHERE DATEDIFF(MONTH, StartDate, EndDate) <= 6 AND Status = 'Canceled';
- Result: Lists customers who canceled within six months, showing which customers might have been disengaged.

   -- Average subscription duration for all customers
   SELECT AVG(DATEDIFF(MONTH, StartDate, EndDate)) AS AverageDuration
   FROM SubscriptionData;
- Result: Returns the average length of subscriptions, offering a baseline for expected customer retention.
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

- Customer Segmentation: Show different customer groups based on behavior.

  Result: Identifies key customer segments such as long-term, new, and high-cancellation groups.

- Cancellations vs. Renewals: Create visualizations to highlight trends.

  Result: Visualizes trends in customer retention, showing the balance between renewals and cancellations.

- Distribution of Subscription Types: Use a pie chart to display this.

  Result: Displays the proportion of each subscription type, giving a quick overview of preferences.

- Subscription Duration Trends: Use line charts to show average duration over time.

  Result: Tracks the average length of subscriptions, indicating changes in customer loyalty over time.

- Interactive Slicers: Add filters by region, subscription type, and status for a dynamic view.

  Result: Allows users to customize views, focusing on specific regions, subscription types, or statuses for deeper insights.

### Subdirectories
- /excel: Store all Excel files and reports.
- /sql: Store SQL scripts for the queries used in this project.
- /powerbi: Store Power BI report files and dashboards.

### Resources
- [Excel Guide](https://support.microsoft.com/excel)
- [SQL Server Documentation](https://docs.microsoft.com/sql/sql-server/)
- [Power BI Documentation](https://docs.microsoft.com/power-bi/)
