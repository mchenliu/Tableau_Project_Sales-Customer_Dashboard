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
🔍 Check out my HR dashboard on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/SalesCustomersDashboardsDataWithBaraa/CustomersDashboard).
## Tools Used
**:art: Tableau:** A powerful tool for creating data visualizations and business intelligence dashboards, enabling insightful analysis and reporting.  
**:pencil2: draw.io:** Used to sketch the container structures for dashboard design.
**:computer: Visual Studio Code:** A lightweight, versatile code editor. I utilized Visual Studio Code to edit project scripts and manage images, ensuring seamless integration and synchronization with GitHub for version control and collaboration.  
**:octopus: Git & Github:** My go-to for version control and tracking my project progress.
# Steps to Build Dashboards
## :one: Define User Requirements
- :dart: Identify Target Audience:
- :moneybag: Sales
- :credit_card: Customers
## :two: Build Data Source
- Connected the dataset to Tableau. Identified the `Orders` tabls is a fact table while the `Customers`, `Location` and `Products` tables are all dimention tables.
- Built data model starting with `Orders` table.  

| Orders   |  
![Data_model](/Sales%20Dashboard%20Materials/Images/Connect_data.png)
- Conducted an initial inspection to verify data quality and ensure accurate data type mapping.
- Explored the data using Tableau worksheets to understand relationships and potential insights.
## :three: Build Charts
- :white_check_mark: Chart Selection: Analyzed user requirements to select the most effective chart types for presenting data.
- :gear: Parameter Created:  
![Parameter](/Sales%20Dashboard%20Materials/Images/Parameter.png)
- :1234: Calculated fields developed to enhance chart functionality:  

| Field Name |Formula   |                                                            
|------------|----------|
| Order Date (Years) | `YEAR([Order Date])`|
| Current Year Sales | `IF YEAR([Order Date]) = [Select Year]` <br> `THEN [Sales]` <br> `END`|
| %  Difference in Sales |  `(SUM([Current Year  Sales]) - SUM([Previous Sales]))` <br> `/ SUM([Previous Sales])`|
| Find Min & Max Sales | `IF SUM([Current Year Sales]) =` <br> `WINDOW_MAX (SUM([Current Year Sales]))` <br> `THEN SUM([Current Year  Sales])` <br> `ELSEIF` <br> `SUM([Current Year Sales]) =` <br> `WINDOW_MIN(SUM ([Current Year Sales]))` <br> `THEN SUM([Current Year  Sales])` <br> `END`|
| Find Sales Below or <br> Above Average | `IF SUM([Current Year Sales]) >` <br> `WINDOW_AVG (SUM([Current Year Sales])` <br> `THEN 'Above'` <br> `ELSE 'Below'` <br> `END` |
| Num of Orders <br> Per Customer| `IF YEAR([Order Date]) = [Select Year]` <br> `THEN [Customer ID]` <br> `END`  
___
**:abacus: Charts Used**
Each chart type was selected for its ability to effectively communicate specific insights:  
- **:chart_with_upwards_trend: BAN + Line Chart:** Ideal for presenting KPIs at a glance. I combined BANs with line charts to show KPIs of sales, profit, quantity sold, number of customers, sales per customer and orders. trends for all these indexes over time.  
![BAN](/Sales%20Dashboard%20Materials/Images/Total_Sales_BAN.png)  
![Sales_per_customer_BAN](/Sales%20Dashboard%20Materials/Images/Total_Sales_Per_Customer.png)  
- **:bar_chart: Bar in bar chart:**
  ![Bar_in_bar_chart](/Sales%20Dashboard%20Materials/Images/Bar_in_bar.png)  
- **:chart_with_upwards_trend: Stepped Line Chart:**  
  ![Stepped_line_chart](/Sales%20Dashboard%20Materials/Images/Step_line_chart.png)
- **:bar_chart: Histogram:**  
  ![Histogram](/Sales%20Dashboard%20Materials/Images/Histogram.png)  
- **:clipboard: Table:**  
  ![Customer_filter](/Sales%20Dashboard%20Materials/Images/Top_10_customer_filter.png)
  ![Table](/Sales%20Dashboard%20Materials/Images/Top_customer_table.png)  

## :four: Dashboard Build  
**Sales Dashboard**  
**:bricks: Structure:**
**:paintbrush: Design and Build:**
![Sketch1](/Sales%20Dashboard%20Materials/Images/Sketch1.png)    
![Sketch2](/Sales%20Dashboard%20Materials/Images/Sketch2.png)  

**Customers Dashboard**  
**:bricks: Structure:**  
**:paintbrush: Design and Build:**
# Conclusion
:mag: Explore the full dashboards on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/SalesCustomersDashboardsDataWithBaraa/CustomersDashboard).
