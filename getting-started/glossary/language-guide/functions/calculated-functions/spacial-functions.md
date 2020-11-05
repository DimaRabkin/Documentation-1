---
description: This page goes over the spacial functions in Upsolver.
---

# Spacial functions

## `WKT_SPATIAL_CONTAINS`

Checks if the first WKT formatted spatial object contains the second.

#### Inputs

* **first**
* **second**

| first | second | result |
| :--- | :--- | :--- |
| `"POLYGON((-10 30, -40 40, -10 -20, 40 20, 0 0, -10 30))"` | `"POINT(10 0)"` | `true` |
| `"POLYGON((-10 30, -40 40, -10 -20, 40 20, 0 0, -10 30))"` | `"POINT(15 0)"` | `false` |

## `WKT_SPATIAL_INTERSECT`

Checks if the WKT formatted spatial objects intersect.

#### Inputs

* **first**
* **second**

| first | second | result |
| :--- | :--- | :--- |
| `"POLYGON((-10 30, -40 40, -10 -20, 40 20, 0 0, -10 30))"` | `"POINT(10 0)"` | `true` |
| `"POLYGON((-10 30, -40 40, -10 -20, 40 20, 0 0, -10 30))"` | `"POINT(16 0)"` | `false` |

