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

<img width="1258" height="498" alt="Image" src="https://github.com/user-attachments/assets/4244a6d6-f961-46c2-b74c-73bb6e7a9977" />

- Step 11: Created a new calculated column to evaluate profit or loss by analyzing the difference between product demand and availability.
- Step 12: Created DAX measures to calculate total profit and loss by comparing availability and demand. When the difference (availability minus demand) is positive, it is classified as profit; when negative, it is classified as a loss.

		Total Profit = SUMX(FILTER('Inventory Data', 'Inventory Data'[Profit/Loss] > 0), 'Inventory Data'[Profit/Loss] * 'Inventory Data'[Unit_Price])
		
		Total Loss = SUMX(FILTER('Inventory Data', 'Inventory Data'[Profit/Loss] < 0), 'Inventory Data'[Profit/Loss] * 'Inventory Data'[Unit_Price]) * -1		

- Step 13: Created a measure to calculate the average daily loss by dividing total loss by the total number of days.

		Average Loss per Day = DIVIDE([Total Loss], [Total_Distinct_dates])

- Step 14: Included Product Name and Order Date fields in the filter pane for better data filtering.

<img width="1105" height="502" alt="Image" src="https://github.com/user-attachments/assets/8adfa6be-4274-4c6a-8af7-9b420769bc1f" />

- Step 15: Set up a new SQL Server database named PROD and successfully imported the production and product datasets for further analysis.

<img width="936" height="591" alt="Image" src="https://github.com/user-attachments/assets/f8e13f9f-7516-43fa-ac45-f13507228f9b" />
  
- Step 16: Applied a WHERE clause to validate the quality of the Order Date column, as shown below.

<img width="836" height="422" alt="Image" src="https://github.com/user-attachments/assets/018550e8-4f58-48e2-a8de-b397e49a9398" />

### Important Note: "The test dataset has a relatively low volume of records, whereas the production dataset is significantly larger. Hence, the production dataset will be loaded into SQL Server for data cleaning processes, followed by replacing the test dataset with the production dataset.”

- Step 15: Set up a new SQL Server database named PROD and successfully imported the production and product datasets for further analysis.

- Step 16: Applied a WHERE clause to validate the quality of the Order Date column, as shown below.
  
- Step 17: Performed data cleaning in SQL by applying the UPDATE statement to modify product IDs and ensure data consistency.
- 
<img width="976" height="315" alt="Image" src="https://github.com/user-attachments/assets/1f815873-a042-4f45-b94a-764790970a24" />

- Step 18: Constructed a new table named new_table by leveraging a LEFT JOIN to integrate data from the production and products datasets using the common column product_id.
- 
<img width="1082" height="463" alt="Image" src="https://github.com/user-attachments/assets/0f463549-ad4a-42ac-bbe8-e4dd837ddb4e" />

- Step 19: Transferred data from the test environment to the production environment using Power BI Desktop.

- Step 20: Implemented the following procedure to change the data source within the system.

<img width="308" height="249" alt="Image" src="https://github.com/user-attachments/assets/7c3429f0-bec3-4838-b268-8657232e07a5" />
<img width="801" height="609" alt="Image" src="https://github.com/user-attachments/assets/58745b1a-eb73-44af-b2be-d6776491829d" />
<img width="869" height="614" alt="Image" src="https://github.com/user-attachments/assets/ce539bdd-42ff-4f18-9cc5-85993ba7913c" />

### “Performed data source migration from SQL Server to MySQL to support data processing and analysis.”

- Step 21: The production dataset was successfully imported into MySQL, as illustrated below.
- 
 <img width="897" height="626" alt="Image" src="https://github.com/user-attachments/assets/cdb89a6b-24e8-4c41-95f3-138b979a0d0a" />

- Step 22: Data preparation in MySQL involved using the UPDATE statement to modify production ID values. A similar process was implemented in SQL Server.
- 
  <img width="729" height="523" alt="Image" src="https://github.com/user-attachments/assets/c3f36762-fb62-4f61-b6be-3a5533d7ccaa" />
  
- Step 23: Also imported the product dataset into MySQL.

<img width="710" height="550" alt="Image" src="https://github.com/user-attachments/assets/4e56046a-7fa3-4b3d-80f8-34bae169abce" />

- Step 24: Constructed new_table by performing a join between the production and product datasets on the common field, product_id, and applied the same methodology in SQL Server.

<img width="636" height="394" alt="Image" src="https://github.com/user-attachments/assets/30f0aec0-8c2f-44c0-a061-fa1b2bb385ad" />

<img width="797" height="371" alt="Image" src="https://github.com/user-attachments/assets/ddcbfe1b-930d-4ffa-ad84-372d6352dc92" />

- Step 25: Changed the data source using the data source settings, and then applied transformations in the Advanced Editor within Power Query to migrate the report from SQL Server to MySQL.

<img width="800" height="612" alt="Image" src="https://github.com/user-attachments/assets/22e24a2a-ffa8-44cb-ba59-a7711cd6dcae" />
<img width="704" height="483" alt="Image" src="https://github.com/user-attachments/assets/d9ebb910-22e3-4f4d-976e-2bc1469458cf" />
<img width="1190" height="608" alt="Image" src="https://github.com/user-attachments/assets/ac412b3c-1668-4f36-bd90-5df5aa285d98" />

- Step 26: Published the report to the Power BI Service.

# 📊Insights

A two-page report was created on Power BI Desktop & it was then published to Power BI Service.

The following inferences can be drawn from the dashboard;

### [1] Loss vs Profit Gap:
- Total Loss (8M) is significantly higher than Total Profit (301K).
- Loss is approximately 26.6 times greater than profit.
### [2] Net Impact:
- Net result = 301K – 8M = -7.699M
- This indicates an overall net loss of ~7.7M.
### [3] Daily Loss Perspective:
- With an average daily loss of 2.97K, the business is consistently losing money each day.
### [4] Profit Contribution:
- Profit represents only about 3.76% of total loss, showing low recovery against losses.
### [5] Performance Indicator:
- The large gap suggests inefficiencies in operations, demand-supply mismatch, or high wastage.

