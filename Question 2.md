# Shopify-Data-Science-Challenge

### My analysis code and question answers are in the notebook above
### The SQL answers are below

#### 
Question 1: 
#####
SELECT 
COUNT(ShipperID)
FROM Orders
WHERE ShipperID == 1;

54 orders were shipped by Speedy Express in total
####
Question 2:
#####
SELECT c.CustomerName, COUNT(*) AS Count
FROM Orders AS o, Customers AS c
WHERE o.CustomerID = c.CustomerID
GROUP BY o.CustomerID
ORDER BY Count DESC
LIMIT 1;
 
Handel is the last name of the employee with the most orders
####
Question 3:
#####
SELECT p.ProductName, SUM(Quantity) AS Total
FROM Orders AS o, OrderDetails AS ord, Customers AS c, Products AS p
WHERE c.Country = "Germany" AND ord.OrderID = o.OrderID AND ord.ProductID = p.ProductID AND c.CustomerID = o.CustomerID
GROUP BY p.ProductID
ORDER BY Total DESC
LIMIT 1;
Boston Crab Meat was ordered by customers the most in Germany
