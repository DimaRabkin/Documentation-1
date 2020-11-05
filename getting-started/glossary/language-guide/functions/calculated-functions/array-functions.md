---
description: This page goes over the array functions in Upsolver.
---

# Array functions

## `ARRAY_MAX`

Return the maximum value in an array.

| inputs | result |
| :--- | :--- |
| `1`, `0.2`, `30` | `30` |

## `ARRAY_MIN`

Return the minimum value in an array.

| inputs | result |
| :--- | :--- |
| `1`, `0.2`, `30` | `0.2` |

## `ARRAY_SUM`

Sums all the values in the array.

| inputs | result |
| :--- | :--- |
| `1`, `0.2`, `30` | `31.2` |

## `CONCAT`

Concatenates all values into a single string, separated by the separator.

#### Properties

* **Separator** - String to use as a separator between elements

| input | Separator | result |
| :--- | :--- | :--- |
| `"a"`, `"b"`, `"c"` | `", "` | `"a, b, c"` |
| `5.5` | `", "` | `"5.5"` |
| `"a"`, `"b"`, `"c"` | `""` | `"abc"` |

## `COUNT_VALUES`

Returns the amount of items in a given array.

| input | result |
| :--- | :--- |
|  | `0` |
| `"a"`, `"b"`, `"c"` | `3` |

## `COUNT_VALUES_IF`

Returns the amount of `true` values in a given array.

| input | result |
| :--- | :--- |
|  | `0` |
| `true`, `false`, `true` | `2` |

## `DISTINCT_VALUES`

Get all the distinct elements in the array.

| input | result |
| :--- | :--- |
| `1`, `2`, `3`, `4`, `4`, `1` | `1`, `2`, `3`, `4` |

## `ELEMENT_AT`

Gets the element at the given index in the array.

#### Properties

* **Index** - The index of the item to return

| input | Index | result |
| :--- | :--- | :--- |
| `"a"`, `"b"`, `"c"` | `1` | `"b"` |
| `"a"` | `1` | `null` |
| `"a"`, `"b"`, `"c"` | `-1` | `null` |

## `FIRST_ELEMENT`

Gets the first element in the array.

| input | result |
| :--- | :--- |
|  | `null` |
| `"a"`, `"b"`, `"c"` | `"a"` |

## `LAST_ELEMENT`

Gets the last element in the array.

| input | result |
| :--- | :--- |
|  | `null` |
| `"a"`, `"b"`, `"c"` | `"c"` |

## `LEAST`

Return the minimum value.

| input | result |
| :--- | :--- |
| `[1, 0.2]`, `[30]` | `0.2` |

