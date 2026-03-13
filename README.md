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

