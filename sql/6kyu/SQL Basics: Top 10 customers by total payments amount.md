## INSTRUCTIONS
For this kata we will be using the DVD Rental database.

You are working for a company that wants to reward its top 10 customers with a free gift. You have been asked to generate a simple report that returns the top 10 customers by total amount spent ordered from highest to lowest. Total number of payments has also been requested.

The query should output the following columns:

customer_id [int4]
email [varchar]
payments_count [int]
total_amount [float]
and has the following requirements:

only returns the 10 top customers, ordered by total amount spent from highest to lowest

Database Schema

![image](https://user-images.githubusercontent.com/30005649/197559194-fb9f986d-899c-4428-8d04-ca2994c97f04.png)


## SOLUTION

    SELECT
      customer.customer_id,
      customer.email,
      COUNT(payment.amount) AS payments_count,
      SUM(CAST(payment.amount AS FLOAT)) AS total_amount
    FROM customer
    INNER JOIN payment ON customer.customer_id = payment.customer_id
    GROUP BY(customer.customer_id)
    ORDER BY(total_amount) DESC
    LIMIT 10
