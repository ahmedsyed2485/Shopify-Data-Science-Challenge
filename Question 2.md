# Shopify-Data-Science-Challenge

### My analysis code and question answers are in the notebook above
### The SQL answers are below

#### 
Question 1: 
#####
SELECT Count(DISTINCT(O.OrderID))
FROM ORDERS O
INNER JOIN SHIPPERS S ON o.shipperID = S.ShipperID
WHERE ShipperName = 'Speedy Express'


54 orders were shipped by Speedy Express in total
####
Question 2:
#####
SELECT LastName, MAX(COUNT_ORDERS)
FROM 
(
SELECT E.EmployeeID, LastName, COUNT(OrderID) AS COUNT_ORDERS
FROM EMPLOYEES E INNER JOIN ORDERS O ON E.EmployeeID = O.EmployeeID
GROUP BY E.EmployeeID) t
 
Peacock is the last name of the employee with the most orders
####
Question 3:
#####
SELECT PRODUCT, MAX(SUM_Q) as
FROM 
(SELECT P.PRODUCTNAME AS PRODUCT, C.COUNTRY, SUM(OD.QUANTITY) as SUM_Q
FROM CUSTOMERS C INNER JOIN ORDERS O ON C.CuStomerID = O.CustomerID
INNER JOIN ORDERDETAILS OD ON O.ORDERID = OD.ORDERID
INNER JOIN PRODUCTS P ON OD.PRODUCTID = P.PRODUCTID
WHERE country = 'Germany'
GROUP BY P.PRODUCTNAME) t

Boston Crab Meat was ordered by customers the most in Germany
