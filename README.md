# Table of Contents
- [Table of Contents](#table-of-contents)
- [Sales \& Customers Dashboard | Sales](#sales--customers-dashboard--sales)
- [Sales \& Customers Dashboard | Customers](#sales--customers-dashboard--customers)
- [Introduction](#introduction)
  - [Tools Used](#tools-used)
- [Steps to Build Dashboards](#steps-to-build-dashboards)
  - [:one: Define User Requirements](#one-define-user-requirements)
  - [:two: Build Data Source](#two-build-data-source)
  - [:three: Build Charts](#three-build-charts)
  - [:four: Dashboard Build](#four-dashboard-build)
- [Conclusion](#conclusion)

# Sales & Customers Dashboard | Sales  
![Sales Dashboard](/Sales%20Dashboard%20Materials/Images/Sales%20Dashboard.gif)  
# Sales & Customers Dashboard | Customers
![Customer Dashboard](/Sales%20Dashboard%20Materials/Images/Customers%20Dashboard.gif)  

# Introduction  
:mega: I built two interactive dashboards (**Sales** and **Customers**) in this project providing a comprehensive overview of key performance indicators (KPIs) related sales performance and customer engagement. 

The project was completed as part of Baraa Salkini's course on [Udemy](https://www.udemy.com/course/the-tableau-ultimate-course-from-zero-to-hero).  

:mag: Check out my HR dashboard on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/SalesCustomersDashboardsDataWithBaraa/CustomersDashboard).
## Tools Used
**:art: Tableau:** A powerful tool for creating data visualizations and business intelligence dashboards, enabling insightful analysis and reporting.  
**:pencil2: draw.io:** Used to sketch the container structures for dashboard design.
**:computer: Visual Studio Code:** A lightweight, versatile code editor. I utilized Visual Studio Code to edit project scripts and manage images, ensuring seamless integration and synchronization with GitHub for version control and collaboration.  
**:octopus: Git & Github:** My go-to for version control and tracking my project progress.
# Steps to Build Dashboards
## :one: Define User Requirements
- **:dart: Identify Target Audience:** The dashboard is tailored for sales managers and executives, focusing on:
  - KPI Overview and Trends: Monitor key performance indicators and their changes over time.
  - Interactivity and Flexibility: Users can switch between dashboards, view data for selected years, and apply filters related to product information and location. 
- **:moneybag: Sales:**
- **:credit_card: Customers:**
## :two: Build Data Source
- **Data Connection:** Linked the dataset to Tableau. The `Orders` table functions as a fact table, while `Customers`, `Location`, and `Products` tables serve as dimension tables.
- **Data Model Construction:**
    - Initiated with the `Orders` fact table.
    - Key Relationships:
      `Customers.Customer ID` ↔ `Orders.Customer ID`
      `Location.Postal Code` ↔ `Orders.Postal Code`
      `Products.Product ID` ↔ `Orders.Product ID`

*Data model diagran*  
![Data_model](/Sales%20Dashboard%20Materials/Images/Connect_data.png)
- **Data Exploration:**
    - Verified data quality and correct data type mapping.
    - Utilized Tableau worksheets to explore data relationships and gather potential insights.
## :three: Build Charts
- **:white_check_mark: Chart Selection:** Analyzed user requirements to select the most effective chart types for presenting data.
- **:gear: Created Parameter:** Implemented a parameter to allow year selection, ensuring data accuracy for users with input validation.

*Parameter created with input validation*  
![Parameter](/Sales%20Dashboard%20Materials/Images/Parameter.png)
- **:1234: Calculated fields** developed to enhance chart functionality including:  

| Field Name |Formula   |                                                            
|------------|----------|
| Order Date (Years) | `YEAR([Order Date])`|
| Current Year Sales | `IF YEAR([Order Date]) = [Select Year]` <br> `THEN [Sales]` <br> `END`|
| %  Difference in Sales |  `(SUM([Current Year  Sales]) - SUM([Previous Sales]))` <br> `/ SUM([Previous Sales])`|
| Find Min & Max Sales | `IF SUM([Current Year Sales]) =` <br> `WINDOW_MAX (SUM([Current Year Sales]))` <br> `THEN SUM([Current Year  Sales])` <br> `ELSEIF` <br> `SUM([Current Year Sales]) =` <br> `WINDOW_MIN(SUM ([Current Year Sales]))` <br> `THEN SUM([Current Year  Sales])` <br> `END`|
| Find Sales Below or <br> Above Average | `IF SUM([Current Year Sales]) >` <br> `WINDOW_AVG (SUM([Current Year Sales])` <br> `THEN 'Above'` <br> `ELSE 'Below'` <br> `END` |
| Number of Orders <br> Per Customer| `IF YEAR([Order Date]) = [Select Year]` <br> `THEN [Customer ID]` <br> `END`  
___
**:abacus: Charts Used**  
Each chart type was selected for its ability to effectively communicate specific insights:  
- **:chart_with_upwards_trend: BAN + Line Chart:** Ideal for presenting KPIs at a glance. I combines BANs with dual-axis line charts for a dynamic representation of sales, profit, and customer trends.
  *BAN & line chart for total profit*
![BAN](/Sales%20Dashboard%20Materials/Images/Total_profit.png)
  *BAN & line chart for total sales per customer*
![Sales_per_customer_BAN](/Sales%20Dashboard%20Materials/Images/Total_Sales_Per_Customer.png)  
- **:bar_chart: Bar-in-bar chart:** Excellent for comparing a subgroup with its large group. 
  ![Bar_in_bar_chart](/Sales%20Dashboard%20Materials/Images/Bar_in_bar_chart.png)
- **:chart_with_upwards_trend: Stepped Line Chart:**  
  ![Stepped_line_chart](/Sales%20Dashboard%20Materials/Images/Step_line_chart.png)
- **:bar_chart: Histogram:** Suitable for detailed data distribution insights.
  ![Histogram](/Sales%20Dashboard%20Materials/Images/Histogram.png)  
- **:clipboard: Table:**  
  ![Customer_filter](/Sales%20Dashboard%20Materials/Images/Top_10_customer_filter.png)
  ![Table](/Sales%20Dashboard%20Materials/Images/Top_customer_table.png)  

## :four: Dashboard Build  
**Sales Dashboard**  

**:bricks: Structure:**  
- Title: Included logo, title and a floating filter bar.
- Legends: 
- KPIs: Sales, profit and quantity.
- Charts: 
  - Sales & Profit by Subcategory
  - Sales & Profit Trends
  
**:paintbrush: Design and Build:**  
- Planned and sketched the layout in draw.io, defining container structures for clarity.
- Integrated charts into the Sales Dashboard.
- Refined the dashboard's design, including colors, text styles, and inner/outer padding for a clean and professional look.
- Added the logo and buttons to the title bar for a cohesive and branded design.
- Converted the buttons to floating and added to the floating filter.
- Fine tuned the settings of the floating filter.
- Performed thorough testing.  
  
*Define different objects in the sketch*  
![Sketch1](/Sales%20Dashboard%20Materials/Images/Sketch1.png)  
*Sales Dashboard sketch*  
![Sketch2](/Sales%20Dashboard%20Materials/Images/Sketch2.png)  

**Customers Dashboard**  
The structure is nearly identical to Sales Dashboard. Therefor I used the same sketch and took same building stpes to construct this dashboard.  

# Conclusion
:mag: Explore the full dashboards on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/SalesCustomersDashboardsDataWithBaraa/CustomersDashboard).
