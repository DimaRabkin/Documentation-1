---
description: This page goes over the structural functions in Upsolver.
---

# Structural functions

## `FROM_KEY_VALUE`

Maps a list of key values to a record with fields for each key.

#### Inputs

* **key**
* **value**

#### Properties

* **Keys**

#### Example

Input

```sql
{
  "data": [
    { "key": "a", "value": 1 },
    { "key": "b", "value": 2 }
  ]
}
```

SQL

```sql
SET result = FROM_KEY_VALUE('a,b', data[].key, data[].value)
```

Result

```sql
{
  "result": {
    "a": 1,
    "b": 2
  }
}
```

## `GET_RANGE`

Returns range of numbers between start and end \(inclusive\).

#### Inputs

* **first**
* **last**

## `ITEM_INDEX`

Gets the index of the item.

#### Properties

* **Global Index** - Use the global index in the event instead of the index in the containing array
* **Count Nulls**

## `JSON_PATH`

Extracts data from JSON objects.

#### Inputs

* **JSON** - A String that contains JSON Document

#### Properties

* **Path** - JSON Path Expression

<table>
  <thead>
    <tr>
      <th style="text-align:left">JSON</th>
      <th style="text-align:left">Path</th>
      <th style="text-align:left">result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>&quot;[{</code>
        <br /><code>&quot;name&quot;: &quot;The Great Gatsby&quot;,</code>
        <br /><code>&quot;author&quot;: {</code>
        <br /><code>&quot;name&quot;: &quot;F. Scott Fitzgerald&quot;</code>
        <br /><code>}</code>
        <br /><code>},</code>
        <br /><code>{</code>
        <br /><code>&quot;name&quot;: &quot;Nineteen Eighty-Four&quot;,</code>
        <br /><code>&quot;author&quot;: {</code>
        <br /><code>&quot;name&quot;: &quot;George Orwell&quot;</code>
        <br /><code>}</code>
        <br /><code>}]&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;$[*].author.name&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;F. Scott Fitzgerald&quot;</code>, <code>&quot;George Orwell&quot;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;{ &quot;net_id&quot;: 41 }&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;net_id&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;41&quot;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;{ &quot;net_id&quot;: [41, 42] }&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;net_id&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;[41, 42]&quot;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;{ &quot;net_id&quot;: [41, 42] }&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;net_id[*]&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;41&quot;</code>, <code>&quot;42&quot;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;{ &quot;net_id&quot;: [41, 42] }&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;net_id.parent&quot;</code>
      </td>
      <td style="text-align:left"><code>null</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;[1,2,3]&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;$[*]&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;1&quot;</code>, <code>&quot;2&quot;</code>, <code>&quot;3&quot;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;[{</code>
        <br /><code>&quot;name&quot;: &quot;The Great Gatsby&quot;,</code>
        <br /><code>&quot;author&quot;: {</code>
        <br /><code>&quot;name&quot;: &quot;F. Scott Fitzgerald&quot;</code>
        <br /><code>}</code>
        <br /><code>},</code>
        <br /><code>{</code>
        <br /><code>&quot;name&quot;: &quot;Nineteen Eighty-Four&quot;,</code>
        <br /><code>&quot;author&quot;: {</code>
        <br /><code>&quot;name&quot;: &quot;George Orwell&quot;</code>
        <br /><code>}</code>
        <br /><code>}]&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;$[*].author.name&quot;</code>
      </td>
      <td style="text-align:left">
        <p><code>&quot;{&quot;name&quot;:&quot;F. Scott Fitzgerald&quot;}&quot;</code>,</p>
        <p><code>&quot;{&quot;name&quot;:&quot;George Orwell&quot;}&quot;</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## `JSON_TO_RECORD`

Extracts data from JSON objects.

#### Properties

* **Mappings** - JSON to field mappings
* **Output Array** - If the string contains multiple JSON records use this to allow outputing all of them

| value | Mappings | Output Array | result |
| :--- | :--- | :--- | :--- |
| "{ "a": "Hello" }" | "a,a,string" | true | {"a": "Hello"} |
| "{ "a": { "value": "Hello" }, "b" : { "value": "World" } }" | "a.value,a.value,string b.value,b.value,string" | true | {"a.value": "Hello", "b.value": "World"} |

## `MAP_WITH_INDEX`

Outputs an index and a value field. Index contains a zero based index and value contains the value in the input field.

#### Inputs

* **value** - The value to convert to a record

| value | result |
| :--- | :--- |
| `"a"`, `"b"`, `"c"` | `{"index": 0, "value": "a"}`, `{"index": 1, "value": "b"}`, `{"index": 2, "value": "c"}` |

## `QUERY_STRING_TO_RECORD`

Extracts data from query string.

#### Properties

* **Mappings** - Field names

## `TO_ARRAY`

Outputs the values from the inputs as an array.

| inputs | result |
| :--- | :--- |
| `["a", "c"]`, `["b"]` | `"a"`, `"c"`, `"b"` |

## `ZIP`

Combines multiple arrays by index into records.

