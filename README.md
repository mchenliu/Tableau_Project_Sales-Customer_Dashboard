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

- **Sales Dashboard:** Reveals KPIs, sales & profit trends analysis and product subcategory comparison.
- **Customers Dashboard:** Draws attention to KPIS, customer trends, customers engagement analysis and presents the top ten customers by proft.


In this project, I developed two robust interactive dashboards (**Sales** and **Customers**) designed to enhance decision-making through detailed analyses of key performance indicators (KPIs) related to sales performance and customer engagement. These tools are crafted for stakeholders looking to deepen their understanding of market dynamics and customer behaviors.

- **Sales Dashboard:** This dashboard provides an overview of sales and profit trends, alongside a detailed comparison of product subcategories. It is engineered to highlight critical sales KPIs, offering insights into both overall performance and granular product-level trends.

- **Customers Dashboard:** Focused on driving customer-centric strategies, this dashboard offers a nuanced look at customer engagement metrics and trends. It features an analysis of top ten customers by profit, enabling targeted marketing and customer relationship management.

- **Key Features:** Interactive elements allow users to explore data across different time frames and dimensions. Dynamic filters to drill down into specific products, categories, or customer segments.

The project was completed as part of Baraa Salkini's course on [Udemy](https://www.udemy.com/course/the-tableau-ultimate-course-from-zero-to-hero).  

:mag: Check out my HR dashboard on [Tableau Public](https://public.tableau.com/app/profile/mei.liu4813/viz/SalesCustomersDashboardsDataWithBaraa/CustomersDashboard).
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
- Connected the dataset to Tableau. Identified the `Orders` tabls is a fact table while the `Customers`, `Location` and `Products` tables are dimention tables.
- Built data model started with the **fact** table `Orders`.  

| Primary Key | Foreign Key|
|-------------|------------|
| Customers.Customer ID | Orders.Customer ID |
| Location.Postal Code | Orders.Postal Code |
| Products.Product ID | Orders.Product ID|  

*Connection diagran*  
![Data_model](/Sales%20Dashboard%20Materials/Images/Connect_data.png)
- Conducted an initial inspection to verify data quality and ensure accurate data type mapping.
- Explored the data using Tableau worksheets to understand relationships and potential insights.
## :three: Build Charts
- **:white_check_mark: Chart Selection:** Analyzed user requirements to select the most effective chart types for presenting data.
- **:gear: Created Parameter:** As per user requirement to have the flexibity of selecting any desired year.  

*Parameter created with input validation*
![Parameter](/Sales%20Dashboard%20Materials/Images/Parameter.png)
- **:1234: Calculated fields** developed to enhance chart functionality:  

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
- **:chart_with_upwards_trend: BAN + Line Chart:** Ideal for presenting KPIs at a glance. I combined BANs with dual axis line charts to show KPIs of sales, profit, quantity sold, number of customers, sales per customer and orders. trends for all these indexes over time. Both highest and lowest figures are highlighted in the chart.
  *BAN & line chart for total sales*
![BAN](/Sales%20Dashboard%20Materials/Images/Total_Sales_BAN.png)  
  *BAN & line chart for total sales per customer*
![Sales_per_customer_BAN](/Sales%20Dashboard%20Materials/Images/Total_Sales_Per_Customer.png)  
- **:bar_chart: Bar-in-bar chart:** Excellent for comparing a subgroup with its large group. 
  ![Bar_in_bar_chart](/Sales%20Dashboard%20Materials/Images/Bar_in_bar_chart.png)
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
