# Postgres

* Install
  ```
  $ sudo apt-get update
  $ sudo apt-get install postgresql postgresql-contrib
  ```

* Verify access

  ```
  $ sudo -i -u postgres
  $ psql
  $ \q
  $ exit
  ```

* Create role and set password

  ```
  $ sudo -i -u postgres
  $ createuser --interactive
  # Create rails role
  $ psql
  $ \password rails
  $ \q
  $ exit
  ```

* Delete a existing role

  ```
  $ sudo -i -u postgres  
  $ psql
  $ DROP ROLE role_name;
  $ \q
  $ exit
  ```


* List existing databases

  ```
  $ sudo -i -u postgres
  $ psql
  $ \list
  $ \q
  $ exit
  ```

* List existing roles

  ```
  $ sudo -i -u postgres
  $ psql
  $ \du
  $ \q
  $ exit
  ```

* Create a new DB

  ```
  $ sudo -i -u postgres
  $ createdb hello`
  $ exit
  ```


* Get info about current connection (User, database, etc.)

  `conninfo`

* Connect to postgres specifying connection information

  ```
  psql -U postgres -d rails -h 127.0.0.1 -W
  psql -U postgres -h 127.0.0.1
  ```

  | Paramenter  | Description |
  | :---------: | ----------- |
  | -U          | User        |
  | -d          | Database    |
  | -h          | Host        |

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
