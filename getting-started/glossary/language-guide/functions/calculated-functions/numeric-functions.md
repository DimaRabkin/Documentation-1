---
description: This page goes over the numeric functions in Upsolver.
---

# Numeric functions

## `ABS`

Returns the absolute value of a number.

| input | result |
| :--- | :--- |
| `5` | `5` |
| `-3` | `3` |
| `0` | `0` |

## `ADD`

Adds two numbers together.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `5.1` | `2.5` | `7.6` |
| `5` | `2` | `7` |
| `5` | `2.5` | `7.5` |

## `CEILING`

Returns the smallest integer value that is greater than or equal to the value.

| input | result |
| :--- | :--- |
| `5.9` | `6` |
| `-5.9` | `-5` |

## `COS`

Returns the **cosine** of the value in **radians**.

| input | result |
| :--- | :--- |
| `0.785` | `0.707` |
| `1.05` | `0.5` |
| `1.57` | `6.12E-17` |
| `2.09` | `-0.5` |
| `1.57` | `6.12E-17` |

## `DEGREES`

Converts the specified **radians to degrees**.

| input | result |
| :--- | :--- |
| `0` | `0` |
| `3.14` | `180` |
| `6.28` | `360` |

## `DIVIDE`

Divides the first number by the second.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `5.1` | `2.5` | `2.04` |
| `5` | `2.5` | `2` |
| `5` | `0` | `null` |

## `EXP`

A mathematical function that returns the exponential value of the specified number $$e^x$$ where $$x$$ is the input value.

| input | result |
| :--- | :--- |
| `1` | `2.72` |
| `2` | `7.39` |
| `3` | `20.1` |
| `NaN` | `NaN` |

## `FLOOR`

Returns the largest integer value that is equal to or less than the value.

| input | result |
| :--- | :--- |
| `5.9` | `5` |
| `-5.9` | `-6` |

## `GET_PROCESSING_TIME`

Gets the task time.

#### Inputs

* **`time`** — Must be the time field from the data.

## `GREATEST`

Return the maximum value.

| inputs | result |
| :--- | :--- |
| `[1, 0.2]`, `[30]` | `30` |

## `INTEGER_DIVIDE`

Divides the first number by the second and returns the integer part of the result.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `5.1` | `2.5` | `2` |
| `5` | `2.5` | `2` |
| `-5.1` | `2.5` | `-2` |
| `3` | `0` | `null` |
| `0` | `0` | `null` |
| `0` | `3` | `null` |

## `LN`

Returns the **natural logarithm** of the input.

#### Input

* $$n$$ such that $$n > 0$$ 

#### Return value

* $$ln(n)$$ or $$log_e(n)$$ where $$e \approx 2.71828183$$ 

| input | result |
| :--- | :--- |
| `0.5` | `-0.693` |
| `1` | `0` |
| `2` | `0.693` |
| `0` | `null` |
| `-1` | `null` |

## `LOG`

Returns the **logarithm** of input $$n$$.

#### Input

* $$n$$ such that $$n > 0$$ 
* **base** — The base to use for the logarithm.

#### Return value

* $$log_{\text{base}}(n)$$ 

| $$n$$ | base | result |
| :--- | :--- | :--- |
| `2` | `2.0` | `1` |
| `4` | `2.0` | `2` |
| `8` | `2.0` | `3` |
| `1` | `10.0` | `0` |
| `10` | `10.0` | `1` |
| `100` | `10.0` | `2` |
| `-2` | `2.0` | `null` |

## `MOD`

Returns the remainder of the first number divided by the second.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `5` | `2` | `1` |
| `5.3` | `2.2` | `0.9` |
| `5` | `-2` | `1` |

## `MULTIPLY`

Multiplies two numbers.

| operand 1  | operand 2 | result |
| :--- | :--- | :--- |
| `5.1` | `2.5` | `12.8` |
| `5` | `2.5` | `12.5` |

## `NEGATE`

Negates the input value.

| input | result |
| :--- | :--- |
| `1` | `-1` |
| `-1` | `1` |

## `POWER`

A mathematical function that raises the first value to the power of the second value.

#### Inputs

* **base** 
* **exponent** 

| base | exponent | result |
| :--- | :--- | :--- |
| `2` | `0` | `1` |
| `2` | `1` | `2` |
| `2` | `2` | `4` |
| `2` | `3` | `8` |
| `2` | `4` | `16` |

## `RADIANS`

Converts the specified **degrees** **to** **radians**.

| input | result |
| :--- | :--- |
| `0` | `0` |
| `180` | `3.14` |
| `360` | `6.28` |

## `RECIPROCAL`

Returns the reciprocal $$\frac{1}{x}$$ where $$x$$ is the input value.

| input | result |
| :--- | :--- |
| `2` | `0.5` |
| `4` | `0.25` |
| `1` | `1` |
| `0` | `null` |

## `ROUND`

Returns the value rounded to a certain number of decimal places.

#### Inputs

* **value** — The number to round.
* **precision** — The number of decimal places to keep; defaults to 0.

| value | precision | result |
| :--- | :--- | :--- |
| `2.365` | `1` | `2.4` |
| `2.345` | `1` | `2.3` |
| `2.345` | `2` | `2.35` |
| `2.345` |  | `2` |
| `2.345` | `0` | `2` |

## `SIGN`

Returns a value \(1, 0, or -1\) indicating the sign of the value.

| input | result |
| :--- | :--- |
| `5` | `1` |
| `0` | `0` |
| `-5.5` | `-1` |

## `SIN`

Returns the **sine** of the value in **radians**.

| input | result |
| :--- | :--- |
| `0.785` | `0.707` |
| `1.05` | `0.866` |
| `1.57` | `1` |
| `2.09` | `0.866` |
| `1.57` | `1` |

## `SQRT`

A mathematical function that returns the square root of the value.

| input | result |
| :--- | :--- |
| `4` | `2` |
| `-2` | `null` |

## `SQUARE`

A mathematical function that returns the square of the value.

| input | result |
| :--- | :--- |
| `2` | `4` |
| `-2` | `4` |

## `SUBTRACT`

Subtracts the second number from the first.

| operand 1 | operand 2 | result |
| :--- | :--- | :--- |
| `5.1` | `2.5` | `2.6` |
| `5` | `2.5` | `2.5` |

## `TAN`

Returns the **tangent** of the value in **radians** using Java's [`Math.tan`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html) method.

| input | result |
| :--- | :--- |
| `-1.57` | `-1.63E16` |
| `-0.785` | `-1.0` |
| `0.0` | `0.0` |
| `0.785` | `1.0` |
| `1.57` | `1.63E16` |

## `TAN_H`

Returns the **hyperbolic tangent** of the value in **radians** using Java's [`Math.tanh`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html) method.

| input | result |
| :--- | :--- |
| `-1.57` | `-0.917` |
| `-0.785` | `-0.656` |
| `0.0` | `0.0` |
| `0.785` | `0.656` |
| `1.57` | `0.917` |

## `TRUNC`

Returns the value truncated to a certain number of decimal places.

#### Inputs

* **value** - The number to truncate.
* **precision** - The number of decimal places to keep; defaults to 0.

| value | precision | result |
| :--- | :--- | :--- |
| `2.365` | `1` | `2.3` |
| `2.345` | `1` | `2.3` |
| `2.345` | `2` | `2.34` |
| `2.345` |  | `2` |
| `2.345` | `0` | `2` |

