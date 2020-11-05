---
description: >-
  This page goes over how to map your data to a desired schema using Transform
  with SQL in Upsolver.
---

# Mapping data to a desired schema

Transform with SQL enables you to map your data into a desired schema. The process of mapping in Upsolver is done in two simple steps:

1. Ingest your raw data into the data lake by configuring a data source in Upsolver.
2. Map your data to a desired schema by configuring an output using SQL.

To demonstrate, assume we have the following data in CSV format in a data source called **Purchases** \(all values in this table are **strings**\).

| purchase\_id | customer\_id | product\_name | quantity | unit\_price |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 1 | Orange | 3 | 0.25 |
| 2 | 1 | Apple | 1 | 0.5 |
| 3 | 1 | Banana | 2 | 0.25 |

## Define simple schema

If we define a table as:

```sql
SELECT customer_id, purchase_id, product_name
FROM Purchases
```

The resulting table reflects that query as events stream in. The final table contains the data:

| customer\_id | purchase\_id | product\_name |
| :--- | :--- | :--- |
| “1” | “1” | “Orange” |
| “1” | “2” | “Apple” |
| “1” | “3” | “Banana” |

## Rename column names

Renaming of column names is being done as follows using the `AS` statement:

```sql
SELECT customer_id AS Customer, purchase_id AS Purchase, 
       product_name AS Product
FROM Purchases
```

The column names in the resulting table have been renamed:

| Customer | Purchase | Product |
| :--- | :--- | :--- |
| “1” | “1” | “Orange” |
| “1” | “2” | “Apple” |
| “1” | “3” | “Banana” |

## Data type conversion

Conversion of data types is done using `:` next to the selected column name. 

We will demonstrate a conversion of the column quantity from the example data source **Purchases** \(which is in **string** format\) into **`BIGINT`** format.

```sql
SELECT customer_id, purchase_id, product_name, quantity:BIGINT
FROM Purchases
```

The resulting table reflects the conversion:

| customer\_id | purchase\_id | product\_name | quantity |
| :--- | :--- | :--- | :--- |
| “1” | “1” | “Orange” | 3 |
| “1” | “2” | “Apple” | 1 |
| “1” | “3” | “Banana” | 2 |

## Perform calculations

It is possible to perform inline calculations when defining the schema.

If we define a table as:

```sql
SELECT customer_id, purchase_id, product_name, 
       quantity:BIGINT * unit_price:BIGINT as total_cost:BIGINT
FROM Purchases
```

The result of the query is the following table which contains the calculated field `total_cost`:

| customer\_id | purchase\_id | product\_name | total\_cost |
| :--- | :--- | :--- | :--- |
| “1” | “1” | “Orange” | 0.75 |
| “1” | “2” | “Apple” | 0.5 |
| “1” | “3” | “Banana” | 0.5 |

It is also possible to first calculate the field and then just use it in the query:

```sql
SET total_cost = quantity:BIGINT * unit_price:BIGINT;
SELECT customer_id, purchase_id, product_name, total_cost
FROM Purchases
```

