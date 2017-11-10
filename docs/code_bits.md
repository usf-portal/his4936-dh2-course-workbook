# Code Bits

---

## Week 8

### Select Statement - A Basic Statement

Below is an example showing the basic syntax of a SELECT statement.

```sql
-- This is a SQL comment, any line starting with -- is ignored.
-- You can use this feature to leave notes for yourselves and others.
-- Good programmers use comments not only to help themselves remember
-- when they come back to their code later, but also so that any other coder
-- can quickly understand what is going on without having to painstackingly
-- read every line.

SELECT
	some_table.some_column AS 'Some Column',
	some_table.some_other_column AS 'Some Other Column'
FROM some_db.some_table AS some_table
	JOIN some_db.optional_table AS optional_table
		USING (matching_id_columns)
-- Optional: you may use WHERE to filter rows. You may use multiple conditions with 'AND' or 'OR' (no quotes)
WHERE optional_table.optional_column != 'Some Value'
-- Optional: you may use GROUP BY on one more more columns to perform aggregate calcualtions (e.g. average student grades by major)
GROUP BY optional_table.optional_id
-- Optional: you may use ORDER BY to sort by one or more columns, you may specific ASC (ascending) or DESC (descending)
ORDER BY some_table.some_column ASC;
```

---

### View - Product Orders
Views are like pseudo-tables, which brings togetaher data columns that are often spread across a number of different tables. In our sample database, we want all the information about every product in every order. To do this, we need to join together three tables, the products themselves, the orders in which they appear, and finally the details table which specifies the details about quantity etc. of each product for each order. We also want to limit our search only to items that are currently in stock


```sql
SELECT
	-- On each line below, we first specify the column supplying the values, and then rename the column inside 'Quotes'
	-- This is the same as writing orders.orderNumber AS 'Order Number'... we just drop the AS
	orders.orderNumber 'Order Number',
    orders.orderDate 'Date Ordered',
    orders.requiredDate 'Date Required',
    orders.shippedDate 'Date Shipped',
    orders.status 'Status',
    products.productName 'Name',
    details.quantityOrdered 'Quantity',
    details.priceEach 'Price Each',
    products.quantityInStock 'In Stock',
    products.productDescription 'Description',
    details.quantityOrdered * details.priceEach 'Total Cost'
-- Start with the 'details' table, since it is the 'hinge' which connects the orders and products tables together
FROM classicmodels.orderdetails details
	JOIN classicmodels.orders orders
		-- Both tables use orderNumber as the column name, so you can use the USING keyword
		USING (orderNumber)
	JOIN classicmodels.products products
		USING (productCode)
WHERE products.quantityInStock > 0
ORDER BY details.priceEach DESC;
```

---

### Views - Product Analysis

Views not only bring columns together from different tables, they can also perform calculations on them. To perform an aggregate statement, you start by joining the tables you desire as normal, then use the GROUP BY clause with whichever column you want to group by (you can give more than one) then, use aggregate functions (like SUM) against columns you wanted calculated. Note: if you use GROUP BY, you will be forced to used aggregate functions on any columns where values are different between rows of the same group (e.g. you must use an aggregate function quantityOrdered column below, because).

```sql
-- In this example, we want to find out information about each product in our database...
-- we would like to know whether products tend to be purchased in bulk or not.
-- To do this we want to know
-- 1.) How many of each product was ordered?
-- 2.) Over how many orders was it spread?
-- 3.) When it was ordered, on average, how many items were ordered?


SELECT
	-- We grouped by productCode below, so each row will start with its product code
	products.productCode 'Product Code',
	-- Since productName will not vary for each product code, we also do not need to perform aggregate functions
    products.productName 'Product Name',
	-- Quantity ordered will be different, as there will be many different orders within each productCode group
	-- so, we must perform some aggregate function, in this case, we want to know the total across orders, so we use SUM
    SUM(details.quantityOrdered) 'Quantity Ordered',
	-- We also want to know how many different orders were involved. Since each order has its own unique ID, we can use that
	-- with the COUNT function, which will add to a tally each time it finds a new orderNumber relating to each product
	-- though it shouldn't be a problem, we ensure that no orders are double counted by adding the keyword
	-- 'DISTINCT'

    COUNT(DISTINCT orders.orderNumber) 'Total Orders Containing',
    SUM(details.quantityOrdered) / COUNT(orders.orderNumber) 'Avg. Quantity Per Order'
-- Although we are asking about products, the values we want to calculate are in the order details table, so we start there
FROM classicmodels.orderdetails details
	-- We also want info about the orders themselves
	JOIN classicmodels.orders orders
		USING (orderNumber)
	-- We also want information about the products themselves, so we join that one last
	JOIN classicmodels.products products
		USING (productCode)
-- We don't really need a WHERE statement to filter rows, so none appears here
-- Finally, the rows are grouped here.
GROUP BY products.productCode
ORDER BY products.productCode ASC;
```

---

## Week 10

### Ubuntu commands

```bash
# use sudo (superuser do) to execute a command with admin priviledges (will will then be asked your password)
sudo some_command

# apt-get is Ubuntu's system package manager, just type apt-get to get a list of sub-commands and help
apt-get

# update will refresh system's available packages and versions, you should run this before installing new packages or upgrading old ones
sudo apt-get update

# upgrade will download newer versions of all your current packages
sudo apt-get upgrade

# use -y if you don't want to be asked to confirm each package
sudo apt-get upgrade -y

# use install to get a new package (you can also use the -y flag to bypass confirmation)
sudo apt-get install some-package

# use to install Python 3 and development libraries
sudo apt-get install python3 python3-pip python3-venv
sudo apt-get install build-essential libssl-dev libffi-dev python-dev

# use to install nodejs
sudo apt-get install build-essential
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
```

--

## Week 10 Continued

```sql
SELECT
	employees.employeeNumber,
    employees.lastName,
    employees.firstName,
    employees.extension,
    employees.email,
    employees.officeCode,
    employeeBosses.bossName,
    employees.jobTitle
FROM classicmodels.employees AS employees
	JOIN
	(
		SELECT
			employees.employeeNumber,
			CONCAT(bosses.firstName, " ", bosses.lastName) AS bossName
		FROM classicmodels.employees AS employees
			JOIN classicmodels.employees AS bosses
				ON employees.reportsTo = bosses.employeeNumber
	) AS employeeBosses
    ON employees.employeeNumber = employeeBosses.employeeNumber
```

TODO: Add building queries in tableau

---

## Week 11

```sql
SELECT
	studio.idStudio AS `Studio ID`,
    studio.country AS `Country`,
    studio.`production/Distribution` AS `Production / Distribution`,
    movie.relDate AS `Release Date`,
    movie.bOffice AS `Box Office`,
    movie.subGenre AS `Sub Genre`,
    wars.name as `War`,
    wars.dates AS `Dates`,
    wars.outcome AS `Outcome`
FROM usf_mlosasso.Studio AS studio
	INNER JOIN usf_mlosasso.MovieStudio AS movie_studio
		ON studio.idStudio = movie_studio.Studio_idStudio
    INNER JOIN usf_mlosasso.Movie AS movie
		ON movie_studio.Movie_idTitle = movie.idTitle
    INNER JOIN usf_mlosasso.MovieWarsDepicted AS war_in_movie
		ON movie.idTitle = war_in_movie.Movie_idTitle
    INNER JOIN usf_mlosasso.Wars AS wars
		ON war_in_movie.Wars_idWars = wars.idWars
	
```
