# Calculating Minimum Sales Prospecting Date using DAX
This repository provides a solution for calculating the minimum sales prospecting date using the DAX (Data Analysis Expressions) language.

## Introduction
Hello, GitHub community!

Today, I would like to share a business problem with you where a measure in DAX can be extremely helpful. In this project, we will discuss how to calculate the minimum date for sales prospecting using the DAX language.

## Business Problem
Imagine that you work for a company that specializes in customer prospecting and selling products or services. The success of your sales depends on an efficient prospecting strategy, where the date of the first approach or contact with a potential customer is a crucial factor.

To optimize this process, you need to identify the earliest date when each customer was first approached. This information allows you to evaluate the performance of your prospecting team, determine the average time required to convert a potential customer into an effective customer, and make strategic decisions based on this data.


## Solution: Using DAX Measure
This is where the DAX measure becomes useful. By using the formula mentioned below, you can calculate the minimum prospecting date for each customer:

Measure Description
Measure Name: Min_Date
The Min_Date measure calculates the minimum date for prospecting (FIRST_DATE) for each unique combination of company (COMPANY_ID) and year (YEAR) in the SALE_PROSPECTING table.

### DAX Formula

```dax
Min_Date = 
MINX(
    FILTER(
        'SALE_PROSPECTING',
        'SALE_PROSPECTING'[COMPANY_ID] = EARLIER('SALE_PROSPECTING'[COMPANY_ID]) &&
        'SALE_PROSPECTING'[YEAR] = EARLIER('PRIMEIRO RELACIONAMENTO'[YEAR])
    ),
    'SALE_PROSPECTING'[FIRST_DATE]
) 
```
# Measure Description

## Measure Name: Min_Date

The Min_Date measure calculates the minimum date for prospecting (FIRST_DATE) for each unique combination of company (COMPANY_ID) and year (YEAR) in the SALE_PROSPECTING table.

In the above formula, replace 'SALE_PROSPECTING' with the actual name of your table containing the sales prospecting data. Ensure that the column names 'COMPANY_ID', 'YEAR', and 'FIRST_DATE' match the corresponding column names in your table.

## Solution and Results

The solution leverages the DAX measure Min_Date to determine the minimum prospecting date for each unique combination of company and year in the sales prospecting data.

### Data Set like this: 

| COMPANY_ID | YEAR | FIRST_DATE | MIN_DATE   |
|------------|------|------------|------------|
|     1      | 2021 |  2021-01-01| 2021-01-01 |
|     1      | 2021 |  2021-02-15| 2021-01-01 |
|     1      | 2022 |  2022-03-10| 2022-03-10 |
|     2      | 2021 |  2021-06-20| 2021-06-20 |
|     2      | 2022 |  2022-08-05| 2022-08-05 |

# By implementing this measure in your Power BI, you can:

- Evaluate the earliest date at which each company was first approached for prospecting.
- Gain insights into the timing and effectiveness of your sales prospecting efforts.
- Analyze trends and patterns in the minimum prospecting dates by company and year.
- Make data-driven decisions and strategize your sales efforts based on this information.
- The results can be visualized using various Power BI visualizations, such as tables, charts, or timelines, to showcase the minimum prospecting dates for each company and year combination.

Feel free to incorporate the provided Min_Date measure and adapt it to your specific sales prospecting data and visualization needs in order to enhance your sales analysis and decision-making process.

###### Enjoy exploring and utilizing this measure to optimize your sales prospecting activities!
