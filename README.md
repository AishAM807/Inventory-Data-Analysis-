# Inventory Data Analysis 

### Dashboard Link : 

### Data Source: MySQL & SQL Server

## Problem Statement
Organizations often struggle to maintain optimal inventory levels due to a lack of real-time visibility into stock movement, product demand, and supplier performance. Inefficient inventory management can lead to overstocking, stockouts, increased holding costs, and delayed order fulfillment.

The objective of this project is to analyze inventory data and build an interactive Power BI dashboard that provides insights into stock availability, product performance, supplier efficiency, and inventory turnover. The dashboard will help stakeholders monitor key metrics such as total inventory value, stock levels by category, reorder status, sales trends, and supplier delivery performance.

### Steps followed

- Step 1: Successfully imported the Test Environment dataset and Product Details dataset into SQL Server to prepare the data for analysis and transformation, as shown below.

<img width="715" height="621" alt="Image" src="https://github.com/user-attachments/assets/9ee216c4-6460-4d1f-b63d-1a02dc47b242" />

<img width="1088" height="707" alt="Image" src="https://github.com/user-attachments/assets/2f4e7ef2-38a6-4302-8ef8-4196906b7b35" />



- Step 2: As shown below, both datasets were successfully imported into SQL Server and are ready for further analysis.


<img width="725" height="561" alt="Image" src="https://github.com/user-attachments/assets/aeff9aab-b8b6-4f42-a263-142f8b2d0406" />

<img width="532" height="544" alt="Image" src="https://github.com/user-attachments/assets/cd536e1c-c48b-497c-90d4-f95112c8c3d6" />

- Step 3: Since both tables share the common column Product_ID, it was used as the joining key to merge the datasets. A new table named New_Table was created by applying a LEFT JOIN to combine the Inventory dataset and Product dataset.


<img width="1178" height="589" alt="Image" src="https://github.com/user-attachments/assets/b28d2d72-5c0f-420b-8d67-d63b122e1e3d" />



- Step 4:The data was imported into Power BI Desktop, and the Power Query Editor was used to adjust and correct the data types of the columns.

- Step 5: Customized the canvas background and adjusted the wallpaper background to improve the overall layout

- Step 6: A DAX measure was created to calculate the distinct number of dates in the dataset.

		Total_Distinct_dates = DISTINCTCOUNT('Inventory Data'[Order_Date_DD_MM_YYYY].[Date])

- Step 7: Applied the SUM DAX function to compute the total product demand and total product availability.

		Total_demand = SUM('Inventory Data'[Demand])

		Total_availability = SUM('Inventory Data'[Availability])

- Step 8: Developed additional DAX measures to determine the average demand per day, average availability per day, and total product shortage for improved inventory analysis.
		Average Deamnd Per Day = DIVIDE([Total_demand], [Total_Distinct_dates])
		
		Average Availability per Day = DIVIDE([Total_availability], [Total_Distinct_dates])

		Total Supply Sortage = [Total_demand] - [Total_availability]



- Step 9: Implemented the filter pane in the report, allowing users to dynamically filter values based on product name and date.

- Step 10: Created the first report page in Power BI to provide an interactive overview of inventory metrics, displaying KPIs for key values and using the filter pane to enable dynamic filtering by product name and date, enhancing report usability.


