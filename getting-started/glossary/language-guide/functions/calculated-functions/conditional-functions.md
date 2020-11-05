---
description: This page goes over the conditional functions in Upsolver.
---

# Conditional functions

## `COALESCE`

Returns the first value that is not null or missing.

| inputs | result |
| :--- | :--- |
| `"Foo"` | `"Foo"` |
| `"Foo"`, `"Bar"` | `"Foo"` |
| `null`, `"Foo"`, `null`, `"Bar"` | `"Foo"` |
| `"Foo"`, `null`, `"Bar"` | `"Foo"` |

## `IF_ELSE`

If there is a `true` boolean value in the `condition` parameter then return the first value. Otherwise, return the second.

#### Inputs

* **condition**
* **`true_value`**
* **`false_value`**

| condition | `true_value` | `false_value` | result |
| :--- | :--- | :--- | :--- |
| `true` | `"foo"` | `"bar"` | `"foo"` |
| `false` | `"foo"` | `"bar"` | `"bar"` |
|  | `"foo"` | `"bar"` | `"bar"` |

## `NULL_IF`

If there is a `true` boolean value in the `condition` parameter, then return null. Otherwise, return the value.

#### Inputs

* **condition**
* **value**

| condition | value | result |
| :--- | :--- | :--- |
| `true` | `"foo"` | `null` |
| `false` | `"foo"` | `"foo"` |
|  | `"foo"` | `"foo"` |

