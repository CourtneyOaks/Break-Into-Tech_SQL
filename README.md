# BreakIntoTech_SQL

##### Welcome to my SQL portfolio from the Break Into Tech certification program! This code repository contains examples of SQL I've written toward the completion of this course. Feel free to take a look and reach out if you have any questions.

Challenge:
*Come up with a query that lists the name and email of every customer followed by the item and price of orders they've made. Use a LEFT OUTER JOIN so that a customer is listed even if they've made no orders, and don't add any ORDER BY.*
  
  SELECT c.name,
	c.email,
	o.item,
	o.price
	FROM customers c
	LEFT OUTER JOIN orders o
        	ON c.id = o.customer_id;

*Now, create another query that will result in one row per each customer, with their name, email, and the total amount of money they've spent on orders. Sort the rows according to the total money spent, from the most spent to the least spent.*
		SELECT c.name,
			c.email,
			SUM(price) AS spent
		FROM customers c
			LEFT OUTER JOIN orders o
				ON c.id = o.customer_id
		GROUP BY c.name
   		ORDER BY spent DESC;



Challenge:
*We've created a table with all the Harry Potter movies, with a sequel_id column that matches the id of the sequel for each movie. Issue a SELECT that will show the title of each movie next to its sequel's title (or NULL if it doesn't have a sequel).*
		SELECT movies.title,
			sequels.title
		FROM movies
			LEFT OUTER JOIN movies sequels
        			ON movies.sequel_id = sequels.id;



Challenge:
We've created a database for a friend networking site, with a table storing data on each person, a table on each person's hobbies, and a table of friend connections between the people. In this first step, use a JOIN to display a table showing people's names with their hobbies.
		SELECT p.fullname,
			h.name
		FROM persons p
			JOIN hobbies h
				ON p.id = h.person_id;
Now, use another SELECT with a JOIN to show the names of each pair of friends, based on the data in the friends table.
		SELECT a.fullname, b.fullname
		FROM friends
			JOIN persons a
				ON a.id = friends.person1_id
			JOIN persons b
				ON b.id = friends.person2_id;
![image](https://github.com/CourtneyOaks/BreakIntoTech_SQL/assets/102244119/fedc4053-7888-4e63-9347-48116bbe4b49)



