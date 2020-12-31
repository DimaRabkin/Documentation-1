# CREATE TABLE

## Synopsis

```sql
CREATE CATALOG.SCHEMA.TABLE [ IF NOT EXISTS ]
table_name (
  { column_name data_type 
    [ COMMENT comment ] 
    [ WITH ( property_name = expression [, ...] ) ]
  | LIKE existing_table_name 
    [ { INCLUDING | EXCLUDING } PROPERTIES ] 
  }
  [, ...]
)
[ COMMENT table_comment ]
[ WITH ( property_name = expression 
                      [  primary_keys = Array[, ...],
                         partitioned_by = Array[, ...],
                         compute_cluster = 'default',
                         retention={ minutes | hours | days },
                         storage_location = 's3://...')
                       ] 
         ) 
 ]
```

## Description

Create a new, empty table with the specified columns. 

The optional `WITH` clause can be used to set properties on the newly created table. To list all available table properties, run the following query:

```sql
SELECT * FROM system.metadata.table_properties
```

To list all available column properties, run the following query:

```sql
SELECT * FROM system.metadata.column_properties
```

## Examples

Create a new table `orders` including user defined properties.

```sql
CREATE TABLE upsolver.shopping.orders (
  orderid bigint,
  orderstatus varchar,
  totalprice double,
  order_amt int,
  order_completed boolean,
  order_time timestamp,
  orderdate date,
  partition_region varchar
)
WITH (  primary_keys = Array['orderid'],
        partitioned_by = Array['partition_region', 'orderdate'],
        compute_cluster = 'default',
        retention='90 days',
        storage_location = 's3://upsolver-managed-us-east-1/shopping/data')
```

#### primary\_keys 

Primary keys are the IDs used as the keys to match records to determine whether a record already exists. Upsolver will use these keys to perform the UPSERT operations. This can be useful in a CDC use case where records are being continuously refreshed and updated.

#### partitioned\_by 

Open Lake allows tables to be partitioned by how users typically access their day. In the example, the `orders` table first partitions by its region and within each region, partitioned by `orderdate`. 

#### compute\_cluster

The name or ID of the compute cluster hosting the defined table.

#### retention

Time defined to keep data in the table. It can be by minutes, hours or days. Data outside of the retention period will be deleted. The time is calculated from the time an event is written to the Open Lake environment.

#### storage\_location

Amazon S3 locations are supported today by Open Lake. The user needs to have an appropriate S3 connection defined. If a valid connection is missing, Open Lake will ask the user to create a connection and run the `CREATE` statement again.

## Additional examples

Create the table `orders` if it does not already exist, adding a table comment and a column comment:

```sql
CREATE TABLE IF NOT EXISTS upsolver.shopping.orders (
  orderid bigint,
  orderstatus varchar,
  totalprice double,
  order_amt int,
  order_completed boolean,
  order_time timestamp,
  orderdate date,
  pa
COMMENT 'A table to keep track of orders.'
```

Create the table `bigger_orders` using the columns from `orders` plus additional columns at the start and end:

```sql
CREATE TABLE upsolver.shopping.bigger_orders (
  biggerorders_id bigint,
  LIKE orders,
  biggerorders_orderdate date
)
```

## 

## 

