# Data types

Open Lake has a set of built-in data types, described below. 

* BOOLEAN
* INTEGER
* DATE
* TIMESTAMP 
* BIGINT
* DOUBLE
* VARCHAR

#### `BOOLEAN`

> This type captures boolean values `true` and `false`.

#### `INTEGER`

> A 32-bit signed two’s complement integer with a minimum value of `-2^31` and a maximum value of `2^31 - 1`. The name `INT` is also available for this type.

#### `BIGINT`

> A 64-bit signed two’s complement integer with a minimum value of `-2^63` and a maximum value of `2^63 - 1`.

#### `DOUBLE`

> A double is a 64-bit inexact, variable-precision implementing the IEEE Standard 754 for Binary Floating-Point Arithmetic.

#### `VARCHAR`

> Variable length character data with an optional maximum length.
>
> Example type definitions: `varchar`, `varchar(20)`

#### `DATE`

> Calendar date \(year, month, day\).
>
> Example: `DATE '2001-08-22'`

#### `TIMESTAMP`

> Instant in time that includes the date and time of day without a time zone. Values of this type are parsed and rendered in the session time zone.
>
> Example: `TIMESTAMP '2001-08-22 03:04:05.321'`

