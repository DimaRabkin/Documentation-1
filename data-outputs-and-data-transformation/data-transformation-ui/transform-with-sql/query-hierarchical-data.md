---
description: This article goes over how to query hierarchical data using SQL in Upsolver.
---

# Query hierarchical data

Transform with SQL enables to query hierarchical data. 

{% hint style="info" %}
**See:** [SQL syntax reference - Hierarchical data](../../../getting-started/glossary/language-guide/sql.md#hierarchical-data)
{% endhint %}

For the following examples, we will assume that three events stream into the data source `Purchases` over time:

```sql
{ 
    "purchase_id": 1, "customer_id": 1, 
    "products": 
    [ 
        { "name": "Orange", "quantity": 3, "unit_price": 0.25 }, 
        { "name": "Banana", "quantity": 4, "price": 0.1 } 
    ] 
}
{ 
    "purchase_id": 2, "customer_id": 1, 
    "products": 
    [ 
        { "name": "Apple", "quantity": 1, "unit_price": 0.5 } 
    ] 
}
{ 
    "purchase_id": 1, "customer_id": 1, 
    "products": 
    [ 
        { "name": "Orange", "quantity": -2, "unit_price": 0.25 } 
    ] 
}
```

## **Using nested fields in `GROUP BY` statement:**

With Transform with SQL, accessing nested fields in hierarchical data is simple and intuitive.

Fields in nested records can be accessed using the dot syntax. If a field is in an array, we use square braces `[]` to denote that.

Let’s have a look at the following query:

```sql
SELECT customer_id,
       products[].name product_name,
       products[].quantity * products[].unit_price total_cost
  FROM Purchases
 GROUP BY customer_id, products[].name
```

The result would be be:

| customer\_id | product\_name | total\_cost |
| :--- | :--- | :--- |
| 1 | "Orange" | 0.25 |
| 1 | "Banana" | 0.4 |
| 1 | "Apple" | 0.5 |

## **Calculations on hierarchical data:**

When doing calculations on hierarchical data, the result is placed back in the nested hierarchy. This "target location" affects how an operation works when dealing with arrays.

### **Example 1**

The following query:

```sql
SET products[].total_cost = products[].quantity * products[].unit_price;
SET number_of_purchased_products = SUM_VALUES(products[].quantity);
```

Results in the following output:

```sql
{ 
    "purchase_id": 1, "customer_id": 1, “number_of_purchased_products”: 7, 
    "products": 
    [ 
        { "name": "Orange", "quantity": 3, "unit_price": 0.25, “total_cost”: 0.75 }, 
        { "name": "Banana", "quantity": 4, "price": 0.1, “total_cost”: 0.4} 
    ]
}
{ 
    "purchase_id": 2, "customer_id": 1, “number_of_purchased_products”: 1, 
    "products": 
    [ 
        { "name": "Apple", "quantity": 1, "unit_price": 0.5, “total_cost”: 0.5 } 
    ]
}
{ 
    "purchase_id": 1, "customer_id": 1, “number_of_purchased_products”: -2, 
    "products": 
    [    
        { "name": "Orange", "quantity": -2, "unit_price": 0.25, “total_cost”: -0.5 } 
    ] 
}
```

{% hint style="info" %}
**Note:** `total_cost` resulted in an array but `number_of_purchased_products` didn't. This is because some operations like `SUM_VALUE` return a single value, regardless of how many inputs they have.

Inline operations use the deepest possible location in the nesting as their target location.
{% endhint %}

### **Example 2**

```sql
SET product_indexes = MAP_WITH_INDEX(products[]);
```

Results in the following data:

```sql
{ 
    "purchase_id": 1, "customer_id": 1, 
    “product_indexes”: 
    [ 
        {“index”: 0, "name": "Orange", "quantity": 3, "unit_price": 0.25}, 
        {“index”: 1, "name": "Banana", "quantity": 4, "price": 0.1} 
    ],
    "products": 
    [ 
        { "name": "Orange", "quantity": 3, "unit_price": 0.25}, 
        { "name": "Banana", "quantity": 4, "price": 0.1} 
    ]
}
{ 
    "purchase_id": 2, "customer_id": 1,
    “product_indexes”: 
    [
        “index” : 0, "name": "Apple", "quantity": 1, "unit_price": 0.5} 
    ],
    "products": 
    [ 
        { "name": "Apple", "quantity": 1, "unit_price": 0.5} 
    ]
}
{ 
    "purchase_id": 1, "customer_id": 1,
    “product_indexes”: 
    [
        {“index” : 0, "name": "Orange", "quantity": -2, "unit_price": 0.25} 
    ],
    "products": 
    [ 
        { "name": "Orange", "quantity": -2, "unit_price": 0.25} 
    ] 
}
```

### **Example 3**

The following query:

```sql
SET products_quantity = FROM_KEY_VALUE(products[].name, products[].quantity, “name,quantity” );
```

Results in the following data:

```sql
{ 
    "purchase_id": 1, "customer_id": 1, 
    "products": 
    [ 
        { "name": "Orange", "quantity": 3, "unit_price": 0.25}, 
        { "name": "Banana", "quantity": 4, "price": 0.1} 
    ],
    “products_quantity”: 
    [
        {“Orange”: 3},
        {“Banana”: 4}
    ]
}
{ 
    "purchase_id": 2, "customer_id": 1,
    "products": 
    [ 
        { "name": "Apple", "quantity": 1, "unit_price": 0.5} 
    ],
    “products_quantity”
    [
    	{“Apple”: 1}
    ]
}
{ 
    "purchase_id": 1, "customer_id": 1,
    "products": 
    [ 
        { "name": "Orange", "quantity": -2, "unit_price": 0.25} 
    ],
    “products_quantity”:
    [
    	{“Orange”: -2}
    ] 
}
```

### **Example 4**

The following query:

```sql
SET indexed_products = ZIP(products);
```

Results in the following data:

```sql
{ 
    "purchase_id": 1, "customer_id": 1, 
    "products": 
    [ 
        { "name": "Orange", "quantity": 3, "unit_price": 0.25}, 
        { "name": "Banana", "quantity": 4, "price": 0.1} 
    ],
    “indexed_products”:
    [
        {
            “index”: 0, 
            “field_1”: { "name": "Orange", "quantity": 3, "unit_price": 0.25}
        }, 
        {	
            “index”: 1,
            “field_1”: { "name": "Banana", "quantity": 4, "price": 0.1} 
        }
    ]
}
{ 
"purchase_id": 2, "customer_id": 1**, **
"products": 
    [ 
        { "name": "Apple", "quantity": 1, "unit_price": 0.5} 
    ],
    “indexed_products”:
    [
        {
            “index”: 0,
    	    “field_1”: { "name": "Apple", "quantity": 1, "unit_price": 0.5} 
        }
    ]
}
{ 
    "purchase_id": 1, "customer_id": 1**,** 
    "products": 
    [ 
        { "name": "Orange", "quantity": -2, "unit_price": 0.25} 
    ],
    “Indexed_products”:
    [
        {
            “index”: 0,
            “field_1”: { "name": "Orange", "quantity": -2, "unit_price": 0.25} 
        }
    ]
}
```

