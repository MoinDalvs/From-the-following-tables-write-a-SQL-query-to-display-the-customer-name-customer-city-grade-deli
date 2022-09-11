# SQL_Query
Assignment 3: From the following tables write a SQL query to display the customer_name, customer city, grade, deliveryagent. deliver yagent city. The result should be ordered by ascending on customer_id. customer table: customer_id|customer_name | city | grade | deliver yagent_id 3002|NickRimando |New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002 3008 | Julian Green [London | 300 | 5002 3004 | Fabian Johnson | Paris | 300 | 5006 3009 | Geoff Cameron | Berlin {| 100 | 5003 3003 | Jozy Altidor {Moscow | 200 | 5007 3001 | Brad Guzan | London | | 5005 deliveryagent table deliveryagent_id| name | city | commission 5001 | James Hoag | New York | 0.15 5002 | Nail Knite | Paris | 013 5005 | Pit Alex [London | 0.1 5006 | Mc Lyon | Paris | 0.44 5007| Paul Adam | Rome | 0.13

## Solution
show databases;
create database assignment;
show databases;
use assignment;
create table customer(
	customer_id INT PRIMARY KEY, 
    customer_name VARCHAR(20),
    city VARCHAR(10),
    grade INT,
    deliveryagent_id INT);

DESCRIBE customer;

create table deliveryagent(
	deliveryagent_id INT PRIMARY KEY,
    name VARCHAR(20),
    city VARCHAR(10),
    commission float);
    
DESCRIBE deliveryagent;

-- CUSTOMER DETAILS
INSERT INTO customer
VALUES(3002, 'Nick Rimando', 'New York', 100, 5001),
	(3007, 'Brad Davis', 'New York', 200, 5001),
	(3005, 'Graham Zusi', 'Calfornia', 200, 5002),
	(3008, 'Julian Green', 'London', 300, 5002),
	(3004, 'Fabian Johnson', 'Paris', 300, 5006),
	(3009, 'Geoff Cemeron', 'Berlin', 100, 5003),
	(3003, 'Jozy Altidor', 'Moscow', 200, 5007),
	(3001, 'Brad Guzan', 'London', Null, 5005);
    
SELECT * FROM customer;

INSERT INTO deliveryagent
VALUES(5001, 'James Hoog', 'New York', 0.15),
	(5002, 'Nail Knite', 'Paris', 0.13),
    (5005, 'Pit Alex', 'London', 0.11),
    (5006, 'Mc Lyon', 'Paris', 0.14),
    (5007, 'Paul Adam', 'Rome', 0.13);
    
select * from deliveryagent;

SELECT c.customer_id as 'Customer Id',
 c.customer_name as 'Customer Name',
 c.city as 'Customer City', 
 c.grade as 'Grade',
 d.name as 'Delivery Agent',
 d.city as 'Delivery Agent City'
FROM customer c
JOIN deliveryagent d
USING (deliveryagent_id);
