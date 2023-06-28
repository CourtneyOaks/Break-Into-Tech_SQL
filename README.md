# BreakIntoTech_SQL

##### Welcome to my SQL portfolio from the Break Into Tech certification program! This code repository contains examples of SQL I've written toward the completion of this course. Feel free to take a look and reach out if you have any questions.

Challenge:
We've created a database to track student grades, with their name, number grade, and what percent of activities they've completed. 
n this first step, select all of the rows, and display the name, number_grade, and percent_completed, which you can compute by multiplying and rounding the fraction_completed column.
SELECT name,
	number_grade, 
	ROUND(fraction_completed*100) AS percent_completed
FROM student_grades;

-- Create a query which will show how many students have earned which letter_grade. 
-- You can output the letter_grade by using CASE with the number_grade column, outputting 'A' for grades > 90, 'B' for grades > 80, 'C' for grades > 70, and 'F' otherwise. Then you can use COUNT with GROUP BY to show the number of students with each of those grades.
SELECT COUNT(*), 
	CASE
		WHEN number_grade > 90 THEN 'A'
		WHEN number_grade > 80 THEN 'B'
		WHEN number_grade > 70 THEN 'C'
		ELSE 'F'
		END AS 'letter_grade'
FROM student_grades
GROUP BY 'letter_grade';

-- Challenge:
-- We've created a database for customers and their orders. Not all of the customers have made orders, however. 
-- Come up with a query that lists the name and email of every customer followed by the item and price of orders they've made.
-- Use a LEFT OUTER JOIN so that a customer is listed even if they've made no orders, and don't add any ORDER BY.
SELECT c.name,
	c.email,
	o.item,
	o.price
FROM customers c
	LEFT OUTER JOIN orders o
        ON c.id = o.customer_id;

-- Create another query that will result in one row per each customer, with their name, email, and total amount of money they've spent on orders. 
-- Sort the rows according to the total money spent, from the most spent to the least spent.
SELECT c.name,
	c.email,
	SUM(price) AS spent
FROM customers c
	LEFT OUTER JOIN orders o
		ON c.id = o.customer_id
GROUP BY c.name
ORDER BY spent DESC;

-- Challenge:
-- We've created a database for a friend networking site, with a table storing data on each person, a table on each person's hobbies, and a table of friend connections between the people. 
-- Use a JOIN to display a table showing people's names with their hobbies.
SELECT p.fullname,
	h.name
FROM persons p
	JOIN hobbies h
        ON p.id = h.person_id;

-- Use another SELECT with a JOIN to show the names of each pair of friends, based on the data in the friends table.
SELECT a.fullname, b.fullname
FROM friends
	JOIN persons a
		ON a.id = friends.person1_id
	JOIN persons b
        ON b.id = friends.person2_id;
