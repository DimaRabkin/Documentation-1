---
description: This page goes over the filter functions in Upsolver.
---

# Filter functions

## `AND`

Returns `true` if all operands are true.

| inputs | result |
| :--- | :--- |
| `false`, `false` | `false` |
| `false`, `true` | `false` |
| `true`, `false` | `false` |
| `true`, `true` | `true` |

## `BETWEEN`

Checks if a value is between two values.

#### Inputs

* **value**
* **lowerBound**
* **upperBound**

## `CONTAINS`

Returns `true` for instances where the left operand contains the right operand.

#### Inputs

* **haystack**
* **needle**

| haystack | needle | result |
| :--- | :--- | :--- |
| `"abcde"` | `"a"` | `true` |
| `"abcde"` | `"f"` | `false` |

## `EQUAL_TO`

Returns true for instances where the operands are equal.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `0` | `0` | `true` |
| `1` | `0` | `false` |
| `0` | `1` | `false` |
| `"a"` | `"a"` | `true` |
| `"a"` | `"b"` | `false` |

## `EXISTS`

Opt in all the rows that contains the specified field.

| input | result |
| :--- | :--- |
| `"a"` | `true` |
|  | `false` |

## `GREATER_THAN`

Returns `true` for instances where operand 1 is greater than operand 2.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `0` | `0` | `false` |
| `1` | `0` | `true` |
| `0` | `1` | `false` |

## `GREATER_THAN_OR_EQUAL_TO`

Returns `true` for instances where operand 1 is greater than or equal to operand 2.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `0` | `0` | `true` |
| `1` | `0` | `true` |
| `0` | `1` | `false` |

## `IN_SET`

Returns `true` for instances where the value is contained in the given set.

#### Properties

* **Set** - Values separated by line breaks

| input | set | result |
| :--- | :--- | :--- |
| `"a"` | `"a` `b"` | `true` |
| `"c"` | `"a` `b"` | `false` |
| `1` | `"1` `2` `3.14"` | `true` |
| `2` | `"1` `2` `3.14"` | `true` |
| `3` | `"1` `2` `3.14"` | `false` |
| `3.14` | `"1` `2` `3.14"` | `true` |

## `IS_DUPLICATE`

Returns `true` if it's not the first time the input value is seen in the data within the specified window size.

#### Inputs

* **value** - value to deduplicate

#### Properties

* **Dedup Id**
* **Window Size** - Deduplication window size in minutes

## `LESS_THAN`

Returns `true` for instances where operand 1 is less than operand .

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `0` | `0` | `false` |
| `1` | `0` | `false` |
| `0` | `1` | `true` |

## `LESS_THAN_OR_EQUAL_TO`

Returns `true` for instances where operand 1 is less than or equal to operand 2.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `0` | `0` | `true` |
| `1` | `0` | `false` |
| `0` | `1` | `true` |

## `NOT`

Returns `true` if the value is **false**.

| input | result |
| :--- | :--- |
| `true` | `false` |
| `false` | `true` |

## `NOT_EQUAL_TO`

Returns `true` for instances where the operands are not equal.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `0` | `0` | `false` |
| `1` | `0` | `true` |
| `0` | `1` | `true` |
| `"a"` | `"a"` | `false` |
| `"a"` | `"b"` | `true` |

## `OR`

Returns `true` if **at least** one of the operands is **true**.

| inputs | result |
| :--- | :--- |
| `false`, `false` | `false` |
| `false`, `true` | `true` |
| `true`, `false` | `true` |
| `true`, `true` | `true` |

## `RANDOM`

Returns `true` for a percentage of items equal to the input.

#### Inputs

* **percent** - percentage \(in decimal; e.g. 0.2, 0.5, etc\) of items to mark as **true**

## `XOR`

Returns `true` only if the operands are different from each other.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `false` | `false` | `false` |
| `false` | `true` | `true` |
| `true` | `false` | `true` |
| `true` | `true` | `false` |

