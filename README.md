# Data Analytics Project in Microsoft Power BI Using Excel and CSV

[Follow me on LinkedIn](https://www.linkedin.com/in/abhishekmishra3/)

[Github Page Link](https://abhishekmishra8.github.io/Power-BI-Project-Bank-Domain/)

Project Report and Dashboard Sreenshot shown below:

<img src="Images Folder/Power Bi Report Dashboard.JPG" width="400" height="250" /> &nbsp;&nbsp; <img src="Images Folder/Power Bi Service Dashboard.JPG" width="400" height="250" />




## key Learning are as follow:-

1. Loaded Files from Excel Worksheet, Excel CSV  
Distinct v/s Unique  
Data Set : 1 2 3 3 4 4  
Distinct Value : 4  
Unique Value : 2  

2. Power Query : Transform Data are done in Power Query.  
- All trasformation data are recorded in APPLIED STEPS section like remove add column & rows etc.
- M Code : Whatever the changes made on data, those action are done by M code Language in Backend.

3. Create MasterDate Table with Date Format
- `DateMaster = CALENDAR(FIRSTDATE(Bank_Churn[Bank DOJ]), LASTDATE(Bank_Churn[Bank DOJ]))`
- `Year = YEAR(DateMaster[Date])`
- `Month = FORMAT(DateMaster[Date], "MMM")`

4. Data Modeling in Power Pivot : Dealing with the cardinality between the tables.  
Creating Relationship between the tables. Fact Tables & Dimension Tables.
- One to One Relationship & One to Many Relationship
- Star Schema : All the Dimension tables are connected to the main Fact table.
- Snowflake schema : Dimension tables may or maybe indirectly connected to the main Fact table through another Dimension table.
- Galaxy Schema or Bridge Schema : Multiple Fact tables and Dimension tables involves.  
<img src="Images Folder/Data Model in Power Pivot.JPG" width="550" height="350" />

5. Created Seperate Table for Measure.  
`Total Customers = COUNT(Bank_Churn[CustomerId])`
`Active Customers = CALCULATE(COUNT(Bank_Churn[IsActiveMember]), ActiveCustomer[ActiveID]=1)`
`Inactive Customers = CALCULATE(COUNT(Bank_Churn[IsActiveMember]), ActiveCustomer[ActiveID]=0)`
`Credit Card Holders = CALCULATE(COUNT(Bank_Churn[CustomerId]), CreditCard[Category]="Credit card holder")`
`Non Credit Card Holders = CALCULATE(COUNT(Bank_Churn[CustomerId]), CreditCard[Category]="Non Credit card holder")`
`Exit Customer = CALCULATE([Total Customers], ExitCustomer[ExitCategory]="Exit")`
`Retain Customers = CALCULATE([Total Customers], ExitCustomer[ExitCategory]="Retain")`

6. Displayed all Measures in Card Visual.

7. Created Slicer to filter the Visual data by Year, Month, Location, Gender

8. Created Column for Customers with Credit Score remark.  
`Credit Type = SWITCH(TRUE(), Bank_Churn[CreditScore]>=800 && Bank_Churn[CreditScore]<=850,"Excellent",
Bank_Churn[CreditScore]>=740 && Bank_Churn[CreditScore]<=799, "Very Good",
Bank_Churn[CreditScore]>=670 && Bank_Churn[CreditScore]<=739,"Good",
Bank_Churn[CreditScore]>=580&&Bank_Churn[CreditScore]<=699,"Fair",
Bank_Churn[CreditScore]>=300&&Bank_Churn[CreditScore]<=579,"Poor")`

9. Clustered Column Chart visual.
Active & Inactive members. Year and Month Wise. With some formatting.
Note : Drill Up, Drill Down Concept.

10. Time Intelligence Functions. How to get previous months Exit customers.New Measure created.  
`Previous Month Exit Customers = CALCULATE([Exit Customer],PREVIOUSMONTH(DateMaster[Date]))`

11. Line Chart. It shows Month wise Exit Customer and Secondary Y axis as Previous month Exit Customer.

12. Donut Chart to show in percentage. Exit Customer by Gender Category.

13. Bar Chart Exit Customer by Credit Type data.

14. Go to Insert > Q&A > Ask questions like Exit Customer by Category in Pie Chart. It will provide the ready output.

15. Try Smart Narative tool to get summary of any visual reports

16. Create new Measurement to get Churn percentage of customers.
`Churn % = 
var EC = [Exit Customer]
var TC = [Total Customers]
var ChurnPercentage = DIVIDE(EC,TC)
return ChurnPercentage`

17. Create Matrix visual table to showcase the Churn percentage report.

18. Create Button to Navigate in next page of dashboard.

19. RLS ( Row Level Security ): 
-Moedeling -> Manage Roles -> Create 
-RoleName -> Tables (Geography) -> Add Filters -> Geography Location.
-After creating RLS you can click View As roles to select the filter.

20. Now in Power BI service create Workspaces.
-My Work space is for internal purpose only you can see the report.
-Workspace is to share across larger audience.
- Give Access to Group Member by Manage access button.
- Access role Admin, Member, Contributor, Viewer

21. Now Publish the darsboard report from Desktop PowerBI to Power Bi Services
- Home -> Publish -> Select Workspace -> Submit.

22. Add Members to Security :
- More option in Dataset -> Security -> People or Group who belong to this role.
- This is Static RLS. Dataset -> Schedule Refresh ->

23. Refresh the Data : 
- On Demand Refresh in Desktop Power BI. Home -> Refresh.
- Schedule Refresh in Power BI Service. Gateways are required if the data is On Premise or in local machine.
- If the data is in cloud then no need Gateway connection.
- Install Gateway in PowerBi Service : Settings -> Manage Connections & Gateway -> click to Learn More About. Follow the page instruction.
- After installation done Add to Gateway and Map to the connection.
- Now schedule the Refresh with Frequency and Time.  
<img src="Images Folder/Gateway Connection in Power BI Service.png" width="450" height="350" /> &nbsp;&nbsp; <img src="Images Folder/Schedule Refresh in Power BI Service.JPG" width="450" height="350" />

24. Create New Dashboard in Power BI Service and Pin the visuals from Report.
- Report is ynamic and Dashboard is Static. It is single page data story. We cannot add/Pin Slicers to Dashboard.

25. Subscribe to Dashboard : To send report by email.  
<img src="Images Folder/Subscibe to Dashboard.JPG" width="450" height="350" />

26. Manage Alter/Data Alert : To receive alert email of data change in report.

27. Create App  
<img src="Images Folder/App1 Create App in Power BI Service.JPG" width="350" height="350" /> &nbsp;&nbsp; <img src="Images Folder/App2 Create App Add Content.JPG" width="350" height="350" /> &nbsp;&nbsp; <img src="Images Folder/App3 Power BI App Published.JPG" width="350" height="350" />


Thanks to KSR Datavizon.

[Reference Youtube Video Click Here](https://www.youtube.com/watch?v=aXNhtcQ4nEU)  
