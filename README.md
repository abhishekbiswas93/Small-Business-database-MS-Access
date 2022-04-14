# Small-Business-database-MS-Access
Small Business database MS Access
# RETAIL & CLOTHING DATABASE

Abhishek Biswas |  April 27, 2021


## SQL QUERRY

a)	Search required records for your business (4 queries)

b)	Search results from multiple tables (Assuming this has joins - 3 queries )


## QL Query to figure out the Name of employees managed by Michael ManagerID - 1

Query Name - SQL_3_a_SelfJoin :


 SELECT 

	E.Employee_LastName, E.Employee_FirstName, E.ManagerID AS Supervisior_Employee_ID, EE.Employee_FirstName AS SupervisorName
    
FROM 

	Employee AS E, Employee AS EE
  
WHERE 

	E.ManagerID = EE.Employee_ID
  
AND

	E.ManagerID = 1;


------------------

## SQL Query to find Customer name, phone number along with the price and Product that they have purchased sorted by price.

Query Name - SQL_3_B_CustomersWithHighestSpend:

SELECT

	C.Customer_FirstName AS NAME, C.Customer_Phone AS PhoneNo, Product, Price

FROM 

    Customer AS C 

INNER JOIN 

    (SELECT P.Product_Description AS Product, P.Product_Price AS Price, O.Customer_ID 

FROM 
 
    Product AS P INNER JOIN 
	
    NewOrder AS O 

ON 

    P.Product_ID = O.Prod_ID)  AS Z 

ON 
	
    C.Customer_ID = Z.Customer_ID

ORDER BY 
	
    Price DESC;

-------------------
## SQL Query to Find Customer Details and Shipping address whose delivery is still pending

Query Name - SQL_3_C_NameAdressOfPendingOrders

SELECT
	C.Customer_FirstName & C.Customer_LastName AS Name, S.Shipment_Destination AS DeliveryLocation
FROM
	
    Customer AS C 
INNER JOIN 
	
    Shipment AS S 
ON
	
    C.Customer_ID = S.Customer_ID
WHERE
	
    C.Customer_ID IN 
	  (SELECT 
		Customer_ID 
		FROM NewOrder
		WHERE Order_Status = 'Pending');


## SCHEMA DIAGRAM OR ACCESS RELATIONSHIP

:point_down:

![image](https://user-images.githubusercontent.com/28976558/163290023-9801d6f9-feb1-46a8-ac39-97ef0cda14e3.png)



------------------

## TASK LIST
•	Database Implementation and Data Ingestion

•	Creating Access Table Relation

•	Query Creation – (Part A of query section)

•	Database Implementation and Data Ingestion

•	Creating Access Table Relation

•	Query Creation – (Part C of query section)

•	Query Creation – (Part B of query section)

•	Access Table Relationship and Schema Diagram

•	Creating User Document
