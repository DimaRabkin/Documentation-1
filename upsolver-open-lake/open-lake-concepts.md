---
description: Welcome to Upsolver Open Lake
---

# Open Lake concepts

Upsolver provides a SQL engine to allow users easily query processed data. Open Lake has an hierarchical structure that allow users to group and work with data outputted from Upsolver.

 A `CREATE TABLE` statement will define the Catalog, Schema and Table that the user is creating. For example: in the `CREATE TABLE upsolver.shopping.orders ()` statement`upsolver` is the Catalog, `shopping` is the Schema and `orders` is the Table.

## Open Lake Catalog

The Upsolver Catalog is being defined and utilized by the Upsolver ecosystem.  For example, if the user creates a Table under Catalog `upsolver`, they will be able to start outputting data into the table from Upsolver.

## Schema

Each Catalog can have multiple Schemas. Schemas can also be interpreted as databases in a  data warehouse. It provides the ability to logically organize tables together. Schemas can be a business units, applications or anything that can logically group tables together.

## Table

Each Schema can have multiple Tables. Each table hosts the data that's being outputted from [Upsolver data outputs.](../data-outputs-and-data-transformation/data-outputs/)

