# E-Commerce Customer Churn Analysis

## Objective
This project focuses on analyzing customer churn patterns in the e-commerce domain to provide actionable insights for targeted retention strategies. The goal is to uncover factors leading to customer churn and suggest improvements to mitigate churn rates.

## Project Overview
In this project, I worked with an e-commerce sales dataset to identify patterns and drivers of customer churn. The analysis provided insights into the effects of complaints, gender, payment modes, app usability, and warehouse proximity on churn. I used MySQL to clean and analyze the data, uncovering critical metrics that can guide retention strategies.

### Key Features:
- **Data Source**: E-commerce sales dataset (sourced from Kaggle)
- **Tools Used**: MySQL
- **Focus Areas**: Churn patterns, customer behavior analysis, complaint handling, payment modes, and app experience

---

## Data Preparation
- **Table Creation**: Utilized **DDL commands** to create necessary tables and imported the dataset using the **Table Data Import Wizard** in MySQL.
- **Handling NULL Values**:
  - In the `warehouse_to_home_distance` attribute, I identified NULL values. 
  - To handle these, I first checked for outliers since using mean to fill NULL values could skew the results if outliers were present.
  
### Outlier Detection and Removal:
1. **Inter-Quartile Range (IQR)**:
   - Applied the IQR method using the `PERCENTILE_CONT` function in MySQL to calculate Q1 and Q3.
   - Calculated the **IQR** by subtracting Q1 from Q3 and derived lower and upper bounds.
   - Filtered out outliers using the **WHERE** clause to remove values that exceeded these limits.

2. **Z-Score Method**:
   - Verified the IQR results using the **Z-Score** method.
   - Calculated the Z-Score by taking the difference between the mean and the `distance`, dividing it by the standard deviation.
   - Filtered out any values that exceeded a Z-Score of ±3 to cross-check for outliers.

---

## Data Analysis

### 1. Basic Queries
- **Total Customers**: Queried the total number of customers and segmented them into **active** and **churned** groups.
- **Cashback and Coupons**: Analyzed how many cashback offers and coupons were used by churned customers.
- **Complaint Analysis**: Investigated the relationship between customer complaints and churn rates.

### 2. Key Insights

#### Complaints and Churn
- **Complaints & Churn**: I found that **over 60% of customers churned** after raising a complaint, indicating issues with the technical support team’s grievance handling.
- **Male Churn Rate**: Male customers showed a higher churn rate after filing complaints compared to female customers, particularly those using the mobile app for placing orders.

#### Mobile App Usability
- **Male Customers**: Discovered that **male customers using the mobile app** for placing orders had a significantly higher churn rate. This points to potential issues with the app’s interface or targeted advertising.
  
#### Warehouse Proximity and Delivery Issues
- **Warehouse to Home Distance**: Customers living more than **15 km** away from the warehouse, especially in **Tier 3 cities**, had a high churn rate. 
- **Gender-Neutral Churn**: Both **male and female customers** experienced higher churn when living far from the warehouse, indicating potential issues with the delivery team.
  
#### Payment Mode and Churn
- **Debit Card Payments**: Customers who paid with **debit cards** had the highest churn rate. This may suggest issues such as **payment failures**, **late refunds**, or a lack of support for multiple debit card types.

#### Tenure and Churn
- **Tenure Analysis**: Customers with a **tenure greater than 2 years** were churning at an alarming rate. This serves as a **red flag** for long-term customer retention, indicating that even loyal customers are leaving.

---

## Conclusion
To effectively reduce churn, the e-commerce company should:
1. **Improve technical support**: Focus on providing better solutions to customer complaints to prevent post-complaint churn.
2. **Enhance the mobile app experience**: Address gender-neutral usability issues in the app, particularly for male customers.
3. **Optimize delivery services**: Improve delivery efficiency for customers living far from warehouses, especially in Tier 3 cities.
4. **Address payment mode issues**: Investigate and resolve potential issues with debit card payments, such as server errors or delayed refunds.
5. **Focus on long-term customers**: Develop strategies to retain customers with over 2 years of tenure, as they represent a crucial part of the customer base.

---

## Key MySQL Queries & Techniques:
- **Data Cleaning**: Used IQR and Z-Score methods to remove outliers.
- **Querying**: 
  - Basic queries for customer segmentation (active vs. churned).
  - Analyzed relationships between complaints, gender, and churn.
  - Investigated payment modes, warehouse proximity, and tenure.
