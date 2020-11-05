---
description: This page goes over the date functions in Upsolver.
---

# Date functions

## `ADD_TIME_ZONE_OFFSET`

Add a timezone offset to a date. 

{% hint style="info" %}
The timezone offset can be in any of the standard formats accepted by Java's [`ZoneId.of`](https://docs.oracle.com/javase/8/docs/api/java/time/ZoneId.html) method \(America/New\_York, +02:00, etc.\).
{% endhint %}

#### Inputs

* time
* zone

| time | zone | result |
| :--- | :--- | :--- |
| `"2018-03-10T08:55:12.456Z"` | `"+02:00"` | `"2018-03-10T10:55:12.456Z"` |
| `"2018-03-10T08:55:12.456Z"` | `"America/New_York"` | `"2018-03-10T03:55:12.456Z"` |
| `"2018-03-10T08:55:12.456Z"` | `""` | `null` |
| `"2018-03-10T08:55:12.456Z"` | `"Invalid Zone Id"` | `null` |

## `BETWEEN`

Checks if a date is between two dates.

#### Inputs

* **value**
* **lowerBound**
* **upperBound**

## `DATE_FORMAT`

Convert date into string.

#### Properties

* **Format** - The date format to output. 
  * The format uses the [Java DateTimeFormatter format](https://docs.oracle.com/javase/9/docs/api/java/time/format/DateTimeFormatter.html). 
  * For example, `yyyy-MM-dd HH:mm:ss` will output strings in the format `2017-07-23 14:33:54`. 
  * `yyyy-MM-dd'T'HH:mm:ss.SSS'Z'` will output strings in the format `2017-07-23T14:33:54.756Z`.

| time | zone | result |
| :--- | :--- | :--- |
| `"2018-03-10T08:55:12.456Z"` | `"yyyy/MM/dd HH:mm:ss.SSS"` | `"2018/03/10 08:55:12.456"` |
| `"2018-03-10T08:55:12.456Z"` | `"yyyy/MM/dd"` | `"2018/03/10"` |
| `"2018-03-10T08:55:12.456Z"` | `"HH:mm:ss.SS"` | `"08:55:12.45"` |
| `"2018-03-10T08:55:12.456Z"` | `"E"` | `"Sat"` |

## `PARSE_DATE`

Convert a date string in the provided format into a date. 

{% hint style="warning" %}
If the date is missing or not in the correct format, this feature will not return a value.
{% endhint %}

#### Properties

* **Format** - The date format to output. 
  * The format uses the [Java DateTimeFormatter format](https://docs.oracle.com/javase/9/docs/api/java/time/format/DateTimeFormatter.html). 
  * For example, `yyyy-MM-dd HH:mm:ss` will output strings in the format `2017-07-23 14:33:54`. 
  * `yyyy-MM-dd'T'HH:mm:ss.SSS'Z'` will output strings in the format `2017-07-23T14:33:54.756Z`.

<table>
  <thead>
    <tr>
      <th style="text-align:left">date</th>
      <th style="text-align:left">Format</th>
      <th style="text-align:left">result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>&quot;2017-09-25 22:11:00&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;yyyy-MM-dd HH:mm:ss&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;2017-09-25T22:11:00Z&quot;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;2018-03-19&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;yyyy-MM-dd&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;2018-03-19T00:00:00Z&quot;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;2018_Mar_21_17:59:05.689&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;yyyy_MMM_dd_HH:mm:ss.SSS&quot;</code>
      </td>
      <td style="text-align:left">
        <p><code>&quot;2018-03-21T17:</code>
        </p>
        <p><code>59:05.689Z&quot;</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;2018_Mar_21&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;yyyy_MMM_dd&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;2018-03-21T00:00:00Z&quot;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;2018_Mar_21_24:59:05.689 America/Los_Angeles&quot;</code>
      </td>
      <td style="text-align:left">
        <p><code>&quot;yyyy_MMM_dd_kk:</code>
        </p>
        <p><code>mm:ss.SSS VV&quot;</code>
        </p>
      </td>
      <td style="text-align:left">
        <p><code>&quot;2018-03-21T07:</code>
        </p>
        <p><code>59:05.689Z&quot;</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## `TO_UNIX_EPOCH_MILLIS`

Convert a date to its Epoch \(unix\) milliseconds representation.

| date | result |
| :--- | :--- |
| `"2018-03-10T08:55:12.456Z"` | `1520672112456` |

## `TO_UNIX_EPOCH_SECONDS`

Convert a date to its Epoch \(unix\) seconds representation.

| date | result |
| :--- | :--- |
| `"2018-03-10T08:55:12.456Z"` | `1520672112` |

## `UNIX_EPOCH_TO_DATE`

Convert epoch seconds or milliseconds to a date.

| epochMillis | result |
| :--- | :--- |
| `1520672112456` | `"2018-03-10T08:55:12.456Z"` |
| `1520672112` | `"2018-03-10T08:55:12Z"` |
| `1520672112456000` | `"2018-03-10T08:55:12.456Z"` |
| `1520672112456000000` | `"2018-03-10T08:55:12.456Z"` |

