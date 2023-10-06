### 1.YuliaRYN_Portfolio
### 1.2. YuliaRYN_SQL_homework
***
### использовались таблицы сайта: https://www.w3schools.com/sql
***
### Задание 1
Для последнего заказа покажите customer's name, product name и employee's name. Используйте JOIN нескольких таблиц.

Решение :
SELECT 
  CustomerName, 
  LastName, 
  FirstName, 
  ProductName 
FROM 
  (
    SELECT 
      * 
    FROM 
      Orders 
    ORDER BY 
      OrderId DESC 
    LIMIT 
      1
  ) AS LastOrder 
  JOIN Customers ON LastOrder.CustomerID = Customers.CustomerID 
  JOIN Employees ON LastOrder.EmployeeID = Employees.EmployeeID 
  JOIN OrderDetails ON LastOrder.OrderID = OrderDetails.OrderID 
  JOIN Products ON OrderDetails.ProductID = Products.ProductID;




### Задание 2 
Создать запрос, показывающий все заказы клиентов из Испании.

Решение:
SELECT 
  * 
FROM 
  Orders 
WHERE 
  CustomerID IN (
    SELECT 
      CustomerID 
    FROM 
      Customers 
    WHERE 
      Country = 'Spain'
  )
