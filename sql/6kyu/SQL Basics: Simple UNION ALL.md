## INSTRUCTIONS
For this challenge you need to create a UNION statement, there are two tables ussales and eusales the parent company tracks each sale at its respective location in each table, you must all filter the sale price so it only returns rows with a sale greater than 50.00. You have been tasked with combining that data for future analysis. Order by location (US before EU), then by id.

(us/eu)sales table schema

| id | name | price | card_name | card_number | transaction_date |

resultant table schema

location (EU for eusales and US for ussales) | id | name | price (greater than 50.00) | card_name | card_number | transaction_date |

NOTE: Your solution should use pure SQL. Ruby is used within the test cases to do the actual testing.

## SOLUTION

    SELECT
      'US' AS location,
      us_sales.id AS id,
      us_sales.name AS name,
      us_sales.price AS price,
      us_sales.card_name AS card_name,
      us_sales.card_number AS card_number,
      us_sales.transaction_date AS transaction_date
    FROM ussales us_sales
    WHERE us_sales.price > 50
    UNION ALL (
      SELECT
        'EU' AS location,
        eu_sales.id AS id,
        eu_sales.name AS name,
        eu_sales.price AS price,
        eu_sales.card_name AS card_name,
        eu_sales.card_number AS card_number,
        eu_sales.transaction_date AS transaction_date
      FROM eusales eu_sales
      WHERE eu_sales.price > 50
    )
    ORDER BY location DESC, id;
