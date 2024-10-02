_Created by [Wesley Armando "WriterMaster-1Click"](https://poe.com/wesleyarmando/)_

---

## Project Introduction: E-commerce KPI Analysis Using DAX in Power BI

### Overview

In the competitive world of e-commerce, understanding key performance indicators (KPIs) is essential for driving business success. My project, "E-commerce KPI Analysis," leverages Power BI and DAX (Data Analysis Expressions) to provide insightful visualizations and analyses that empower stakeholders to make informed decisions. Below, I detail the DAX functions used and their significance in the context of business analytics.

### DAX Functions and Their Purpose

#### 1. BestSellingProductsPerCity

**DAX Code:**

```dax
BestSellingProductsPerCity =  
ADDCOLUMNS( 
    SUMMARIZE( 
        'data', 
        'data'[State], 
        'data'[Category], 
        "TotalSales", SUM('data'[Sales]) 
    ), 
    "Rank",  
    RANKX( 
        FILTER( 
            SUMMARIZE( 
                'data', 
                'data'[State], 
                'data'[Category], 
                "TotalSales", SUM('data'[Sales]) 
            ), 
            'data'[State] = EARLIER('data'[State]) 
        ), 
        [TotalSales],, 
        DESC 
    )
)
```

**Purpose and Significance:**

The `BestSellingProductsPerCity` function identifies the top-selling products in each city by category. By ranking products based on total sales within each state, this function provides a granular view of product performance across different regions. This visualization helps stakeholders understand regional preferences, enabling targeted marketing strategies and inventory management.

#### 2. Top10SellingCategoryTable

**DAX Code:**

```dax
Top10SellingcategoryTable =  
TOPN( 
    10,  
    SUMMARIZE( 
        data,  
        data[Category],  
        "TotalSales", SUM(data[Sales]) 
    ),  
    [TotalSales],  
    DESC 
)
```

**Purpose and Significance:**

The `Top10SellingCategoryTable` function extracts the top 10 selling categories based on total sales. This visualization highlights the most profitable product categories, allowing stakeholders to focus on high-performing areas and optimize product offerings. It provides a clear picture of consumer demand trends, aiding in strategic planning and resource allocation.

#### 3. Top10SellingProductsTable

**DAX Code:**

```dax
Top10SellingProductsTable =  
TOPN( 
    10,  
    SUMMARIZE( 
        data,  
        data[Product],  
        "TotalSales", SUM(data[Sales]) 
    ),  
    [TotalSales],  
    DESC 
)
```

**Purpose and Significance:**

Similar to the category analysis, the `Top10SellingProductsTable` function identifies the top 10 selling products. This visualization offers insights into specific product popularity, helping stakeholders make informed decisions about product promotions, pricing strategies, and inventory levels.

#### 4. TotalProfitByYear

**DAX Code:**

```dax
TotalProfitByYear =  
SUMMARIZE( 
    data, 
    data[Order Date], 
    "Year", YEAR(data[Order Date]), 
    "TotalProfit", SUM(data[Profit]) 
)
```

**Purpose and Significance:**

The `TotalProfitByYear` function aggregates profit data on an annual basis. By visualizing profit trends over time, stakeholders can assess the financial health of the business and identify growth patterns or areas of concern. This analysis supports long-term strategic planning and financial forecasting.

### Conclusion

The DAX functions used in this project provide a comprehensive view of e-commerce performance, offering valuable insights into product sales, regional preferences, and financial trends. By visualizing these KPIs in Power BI, stakeholders can make data-driven decisions that enhance business operations and drive growth. This project demonstrates my ability to harness advanced analytics tools to deliver actionable business intelligence.
