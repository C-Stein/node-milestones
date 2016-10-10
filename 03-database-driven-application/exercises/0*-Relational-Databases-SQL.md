#### Talking to a Database

###### SQL Statements
 * SQL keywords are written in CAPS
 * Basic Structure of a SQL statement:
	`SELECT ______   
	FROM ______
	JOIN ______ ON ______
	WHERE ______`

* Example:  `SELECT * FROM employees WHERE name LIKE ‘b%’`
   * LIKE means “matches a pattern” and % means “starts with” (wildcard).

* Example 2: `SELECT products.id, products.name FROM order_details JOIN products ON  order_details.product_id = products.id WHERE order_details.order_id = 10250`



#### Joins
* http://blog.codinghorror.com/a-visual-explanation-of-sql-joins/
* With a join, you must specify how the table is joined using ON. Otherwise, you will get all the combinations possible of one table row matched with another table row.
  * **Inner Join** matches one table with another table row for row. If one row doesn’t have its pair on another table, it will be excluded. It will only show matching row pairs.
  * **Outer Join** matches two tables row for row but includes rows that are not paired up, aka rows that have a pair with a null in the other table.

#### Other Resources
* http://tutorials.jumpstartlab.com/topics/fundamental_sql.html
