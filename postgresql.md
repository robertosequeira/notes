# Postgres


## Testing querys with provided values

```sql
WITH customers (id, name) AS (
  VALUES
    (1, 'Customer 1'),
    (2, 'Customer 2'),
    (3, 'Customer 3')
),
orders (id, customer_id, amount) AS (
  VALUES 
    (1, 1, 150),
    (2, 2, 75),
    (3, 1, 200)
)
SELECT c.id, COALESCE(sum(amount), 0) total
FROM customers c
  LEFT OUTER JOIN orders o on c.id = o.customer_id
GROUP BY c.id
```
