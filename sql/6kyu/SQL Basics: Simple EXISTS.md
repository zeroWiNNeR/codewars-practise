## INSTRUCTIONS
For this challenge you need to create a SELECT statement that will contain data about departments that had a sale with a price over 98.00 dollars. This SELECT statement will have to use an EXISTS to achieve the task.

departments table schema

| id | name

sales table schema

| id | department_id | | name | price | card_name | card_number | transaction_date

resultant table schema

| id | name |

NOTE: Your solution should use pure SQL. Ruby is used within the test cases to do the actual testing. Do not: alias tables as this can cause a failure.

## SOLUTION

    SELECT id, name
    FROM departments d
    WHERE EXISTS (SELECT * FROM sales s WHERE s.department_id = d.id AND s.price > 98);
