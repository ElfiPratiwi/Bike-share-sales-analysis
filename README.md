# Revenue and Profitability Analysis of Bike Rentals: 2021-2022

## Table of Contents
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Preparation](#data-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Sql Code](#Sql-Code)
- [Results/Findings](#resultsfindings)
- [Recommendations](#recommendations)
  
### project overview
This data analysis project aims to provide insights into the sales performance of a bike rental company for 2021 and 2022. By analyzing various aspects of the rental data, we seek to identify trends, make data-driven decisions, and gain a deeper understanding of the company's performance. 

### Data Sources 
The data source comes from Kaggle (https://www.kaggle.com/datasets/walmalki/toman-bike-share-dataset). The file bike0.csv contains rental data from 2021, and the file bike2.csv contains rental data from 2022. The file cost_table.csv contains rental costs and COGS (Cost of Goods Sold) for each year.

### Tools
1. SQL Server Management Studio (SSMS) - Data preparation and analysis
2. Power BI - Creating dashboard

### Data Preparation
In the initial data preparation we perform :
1. Data loading and inpection
2. Join all the tables and selectthe column we need

### Exploratory Data Analysis
EDA involved exploring the data with answering the manager requirements, such as :
1. Hourly revenue analysis
2. Profit and revenue trends
3. Seasonal revenue
4. Rider demographics

### Data Analysis
```sql
    WITH cte_bike AS (
        SELECT * FROM bike0
        UNION
        SELECT * FROM bike1
    )
    SELECT 
        dteday,
        season,
        weekday,
        a.yr,
        hr,
        rider_type,
        riders,
        price,
        COGS,
        riders * price as revenue,
        (riders * price) - COGS as profit
    FROM cte_bike A
    JOIN cost_table B ON a.yr = b.yr;
```

### Results / Findings
The analysis results are summarised as follow :
1. Hourly Revenue Peaks:
Average revenue per hour peaks during commuting times (morning and evening rush hours).
2. Revenue Trends:
General increasing trend in revenue over the two years.
Noticeable decline in revenue from December to March.
3. Seasonal Revenue:
Summer: Highest revenue season.
Spring: Second highest revenue season.
Fall and winter: Lowest revenue season.
4. Rider Demographics:
Registered riders account for approximately 82% of total riders.
Casual riders make up the remaining 18%.
5. Total Riders:
Total riders over the two-year period: 3 million.
6. Profit Margin:
Consistent profit margin of 45%.

### Recommendation
1. Targeted Marketing and Promotions
Peak Commuting Hours: Since the average revenue peaks during commuting hours, implement targeted marketing campaigns aimed at commuters. Offer special promotions, such as discounted rates or membership benefits, for morning and evening rush hours to further incentivize use during these periods.
Seasonal Promotions: To address the revenue dip from December to March, introduce winter promotions. Offer discounted long-term memberships or bundled deals for the winter season to encourage continued use despite the colder weather. Collaborate with local businesses to provide warm-up spots or complimentary hot beverages for riders.
2. Seasonal Adaptations and Services
Winter Adaptations: Invest in bike adaptations suitable for winter conditions, such as winter tires and heated seats, to make riding more comfortable and safer during the colder months. Additionally, provide safety gear like helmets with built-in lights or reflective gear to ensure rider safety during darker months.
Event-Based Rentals: Organize and promote seasonal events or tours that take advantage of the unique characteristics of each season. For example, offer scenic fall foliage rides, spring bloom tours, or summer evening rides.
3. Expand Registered User Base
Membership Incentives: With registered users accounting for 82% of riders, focus on converting casual riders into registered users. Offer incentives such as loyalty points, discounts on renewals, or exclusive access to new bikes for those who sign up for annual memberships.
Corporate Partnerships: Develop partnerships with local businesses and corporations to offer corporate membership plans. Provide special rates and benefits for companies that encourage their employees to use bike rentals for commuting.
4. Enhance User Experience and Engagement
App and Technology Improvements: Improve the mobile app experience by adding features such as real-time bike availability, route optimization for commuting, and integration with public transport schedules. Introduce gamification elements where users can earn badges or rewards for frequent use.
Community Building: Foster a community among users by organizing meetups, group rides, or social media challenges. This can increase user engagement and loyalty.
5. Revenue Diversification
Advertising and Partnerships: Utilize the bike rental platform for additional revenue streams by partnering with local businesses for advertising opportunities. Bikes and docking stations can serve as advertising spaces.
Merchandise Sales: Sell branded merchandise such as apparel, accessories, and safety gear. Offer these items at rental stations and through the mobile app.
6. Operational Efficiency
Dynamic Pricing Model: Implement a dynamic pricing model that adjusts rates based on demand, weather conditions, and time of day. This can help balance demand and optimize revenue.
Fleet Management: Analyze usage patterns to optimize bike distribution and maintenance schedules. Ensure that bikes are readily available in high-demand areas during peak times and well-maintained to reduce downtime and repair costs.
