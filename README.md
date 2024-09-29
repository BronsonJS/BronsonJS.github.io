# BronsonJS.github.io

# Objective

- What is the key pain point?

  The Head of Customer Retention at the bank needs to understand the factors that lead to the risk of customer churn. They want to use visual insights to identify trends in customer demographics, behaviour, and satisfaction levels to reduce churn rates and improve customer retention strategies.

- What is the ideal solution?

  The ideal solution is to develop an interactive dashboard that visualises customer churn patterns based on key factors such as Geography, Salary, Balance, and Product Usage. The dashboard should provide:

- Churn Rate Overview: A high-level view of the total churn rate to quickly identify the overall scale of customer attrition.
  
- Breakdown of Churned vs. Retained Customers: Visuals that compare churned and retained customers across segments like geographic regions and financial brackets.
  
- Product Usage Insights: Analysis of how the number of products a customer owns influences churn, helping to understand engagement levels.
  
- Clear, Actionable Visuals: Easy-to-understand graphs and charts that highlight key trends and factors contributing to churn, enabling the retention team to quickly target at-risk segments.

This dashboard will empower the customer retention team to proactively address churn by focusing on segments most at risk, ultimately enhancing customer loyalty and improving retention strategies.

## User Story 

As the Head of Customer Retention, I need a visual dashboard to help me understand and analyse customer churn patterns across the bank's customer base.

The dashboard should enable me to:

- View a comprehensive overview of the churn rate, segmented by key customer attributes like Geography, Salary, and Product Usage.
  
- Identify high-risk customer segments most likely to churn, based on financial behaviours and engagement levels with bank products.
  
- Make informed, data-driven decisions to develop targeted retention strategies that focus on retaining customers most at risk of leaving.

# Data Source 

- What data is needed to address the objective?

To effectively address the objective and create meaningful visual insights for customer churn, the dataset should include the following key data points:

- Geography
- Financial Information
- Product Usage
- Churn Status

- The data is sourced from a CSV file on Kaggle. [See here to find it](https://www.kaggle.com/datasets/radheshyamkollipara/bank-customer-churn).

# Stages

![Stages-Diagram](Assets/Images/StagesImage.png)

# Design 

## Dashboard Components Required

- What should the dashboard contain based on the requirements provided?

**1. Churn Rate**  
*Purpose*: Provides a high-level overview of the overall churn rate.  
*Why*: This KPI gives the retention team a quick understanding of how many customers are leaving.

**2. Churn by Country**  
*Purpose*: Compares churn rates across countries.  
*Why*: A bar chart is effective for comparing churn across the three primary countries in the dataset: France, Spain, and Germany.

**3. Churn by Salary**  
*Purpose*: Displays churn distribution across salary brackets.  
*Why*: Customers with different income levels may show varying churn risks, helping target retention efforts by salary range.

**4. Balance vs. Churn**  
*Purpose*: Visualizes how customer account balances influence churn.  
*Why*: Provides insight into whether customers with lower balances are more likely to churn.

**5. Churn by Number of Products**  
*Purpose*: Shows how the number of products a customer holds affects churn rates.  
*Why*: Understanding the relationship between product engagement and churn allows the bank to incentivize customers to use more products.

## Tools

| Tool        | Purpose                                              |
|-------------|------------------------------------------------------|
| Excel       | Exploring the data                                   |
| SQL Server  | Cleaning, Testing, and Analyzing the data            |
| Power BI    | Visualizing the data with interactive dashboards     |
| GitHub      | Hosting the project documentation and version control |

# Development 

- Whats the general approach in creating this solution from start to finish?

 1.	Get the data
 2.	Explore the data in Excel
 3.	Load the data into SQL Server
 4.	Clean the data with SQL
 5.	Test the data with SQL
 6.	Visualize the data in Power BI
 7.	Generate the findings based on the insights
 8.	Report the documentation 
 9.	Publish the data to GitHub Pages

## Data Exploration Notes

- What are your initial observations with this dataset? What’s caught your attention so far?

  1. The dataset includes a variety of columns, including demographic, financial, and behavioural data. This signals that we have a comprehensive dataset to address the churn analysis without needing additional data.
  2. The column names are clear and self-explanatory, with no need for renaming or reformatting, except for minor formatting
  3. The data types seem appropriate, with numerical values where expected and categorical values clearly defined
  4. Some customers have a balance of 0, which could either represent actual zero balances or missing/incorrect data for those accounts. This needs further investigation to determine if these zeros affect churn rates significantly.

## Should we include customers with null or zero balences 

- If Zero Balance Indicates Active Usage: If these customers are still using the bank for other products (e.g., credit cards, loans, or other services), then they should be included in the analysis. Their balance being zero doesn’t necessarily mean they are unengaged.

## Data Cleaning

### Creating a Refined Table with Essential Columns for Churn Analysis

The aim is to refine our dataset to ensure it is structured and ready for analysis.

 - Only relevant columns should be retained.
 - All data types should be appropriate for the contents of each column.

```sql
CREATE TABLE cleaned_customer_churn AS
SELECT 
    Geography,
    EstimatedSalary,
    Balance,
    NumOfProducts,
    Exited
FROM 
    customer_churn;

```

# Testing

- What type of quality and validation checks are you going to create?

## 1. Row Count Check
   
``` sql
/* Row count check */
SELECT COUNT (*) AS total_rows
FROM cleaned_customer_churn
```

## 2. Column Count Check 
``` sql
/* Column count check */
SELECT COUNT(*) AS total_columns
FROM information_schema.columns
WHERE table_name = 'cleaned_customer_churn';
```

