---
description: This page goes over the type conversion functions in Upsolver.
---

# Type conversion functions

## `HEX_TO_DECIMAL`

Converts a hexadecimal string value to its corresponding decimal number.

| input | result |
| :--- | :--- |
| `"###"` | `null` |
| `"ff"` | `255` |
| `"0xff"` | `255` |

## `TO_DOUBLE`

Convert a **number** to a **double**.

| value | result |
| :--- | :--- |
| `3` | `3.0` |
| `3.5` | `3.5` |

## `TO_FLOAT`

Convert a **number** to a **float**.

| value | result |
| :--- | :--- |
| `3` | `3.0` |
| `3.5` | `3.5` |
| `-3.5` | `-3.5` |

## **`TO_INT`**

Convert a **number** to an **integer**.

| value | result |
| :--- | :--- |
| `3` | `3` |
| `3.5` | `3` |
| `-3.5` | `-3` |

## `TO_LONG`

Convert a **number** to a **long**.

| value | result |
| :--- | :--- |
| `3` | `3` |
| `3.5` | `3` |
| `-3.5` | `-3` |

## `TO_NUMBER`

Convert to a **number** type.

| value | result |
| :--- | :--- |
| `"###"` | `null` |
| `"10"` | `10` |
| `"5.1"` | `5.1` |
| `5.1` | `5.1` |

## `TO_STRING`

Converts any value to a **string**.

| input | result |
| :--- | :--- |
| `1` | `"1"` |
| `1.5` | `"1.5"` |

