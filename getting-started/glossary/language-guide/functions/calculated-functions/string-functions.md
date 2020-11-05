---
description: This page goes over the string functions in Upsolver.
---

# String functions

## `BASE64_DECODE`

Decode a base 64 string into a string.

| value | result |
| :--- | :--- |
| `"SGVsbG8gV29ybGQ="` | `"Hello World"` |
| `"###"` | `null` |

## `BYTES_SUBSTRING`

Returns a substring of the input, using the offsets in bytes of the UTF-8 encoded byte representation. Partial characters and invalid UTF-8 code points are removed from the result.

#### Inputs

* **value** - Value to substring

#### Properties

* **Start Index** - The inclusive start index in bytes
* **End Index** - The exclusive end index in bytes

| value | Start Index | End Index | result |
| :--- | :--- | :--- | :--- |
| `"Hello World"` | `0` | `10` | `"Hello Worl"` |
| `"Hello World"` | `1` | `10` | `"ello Worl"` |
| `"⻤Hello Wor⻤"` | `1` | `10` | `"Hello W"` |
| `"⻤Hello Wor⻤"` | `0` | `10` | `"⻤Hello W"` |
| `"Hello"` | `0` | `10` | `"Hello"` |

## `JOIN_ARRAYS`

Joins any number of arrays by index using a MessageFormat pattern.

#### Properties

* **Format String** - The format string where `{n}` prints the nth input. 
  * For example, the pattern `'{0}.{0}.{1}'` on the inputs `'a'` and `'b'` will result in the string `'a.a.b'`

## `MD5`

Hashes the input using MD5.

| input | result |
| :--- | :--- |
| `"hello world"` | `"5eb63bbbe01eeed093cb22bb8f5acdc3"` |

## `REGEX`

Matches the regular expression on the input string. Returns the escape groups if any exists or the original string if none exists.

#### Properties

* **Pattern** - Regular Expression Pattern

| input | Pattern | result |
| :--- | :--- | :--- |
| `"abcijefjabc"` | `"abc"` | `"abc"`, `"abc"` |

## `REGEX_MATCH_POSITION`

Matches the regular expression on the input string and returns the index of the first match.

#### Inputs

* **value**
* **startPosition**

#### Properties

* **Pattern** - Pattern to search for

## `REGEX_NAMED_GROUPS`

Matches the regular expression on the input string. Returns record with field names and group names.

#### Properties

* **Pattern** - Regular Expression Pattern
* **All Matches** - Return all the matches of the pattern, and not only the first one
* **Filter Empty** - Filter out empty matches

<table>
  <thead>
    <tr>
      <th style="text-align:left">input</th>
      <th style="text-align:left">Pattern</th>
      <th style="text-align:left">All Matches</th>
      <th style="text-align:left">Filter Empty</th>
      <th style="text-align:left">result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><code>&quot;https://www.domain.com/</code>
        </p>
        <p><code>page.html&quot;</code>
        </p>
      </td>
      <td style="text-align:left">
        <p><code>&quot;^(?:(?&lt;scheme&gt;.*?):\/)?\/?</code>
        </p>
        <p><code>(?&lt;domain&gt;[^:\/\s]+)</code>
        </p>
        <p><code>(?::(?&lt;port&gt;\d*))?(?:(\/\w+)*\/)</code>
        </p>
        <p><code>(?&lt;page&gt;[\w\-\.]+[^#?\s]+)</code>
        </p>
        <p><code>(?:.*)?$&quot;</code>
        </p>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left">
        <p><code>{&quot;scheme&quot;:</code>
        </p>
        <p><code>&quot;https&quot;,</code>
        </p>
        <p><code>&quot;domain&quot;:</code>
        </p>
        <p><code>&quot;www.domain.com&quot;,</code>
        </p>
        <p><code>&quot;page&quot;:</code>
        </p>
        <p><code>&quot;page.html&quot;}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>&quot;http://www.domain.com:</code>
        </p>
        <p><code>8080/page.html&quot;</code>
        </p>
      </td>
      <td style="text-align:left">
        <p><code>&quot;^(?:(?&lt;scheme&gt;.*?):\/)?\/?</code>
        </p>
        <p><code>(?&lt;domain&gt;[^:\/\s]+)</code>
        </p>
        <p><code>(?::(?&lt;port&gt;\d*))?(?:(\/\w+)*\/)</code>
        </p>
        <p><code>(?&lt;page&gt;[\w\-\.]+[^#?\s]+)</code>
        </p>
        <p><code>(?:.*)?$&quot;</code>
        </p>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left">
        <p><code>{&quot;scheme&quot;:</code>
        </p>
        <p><code>&quot;http&quot;,</code>
        </p>
        <p><code>&quot;domain&quot;:</code>
        </p>
        <p><code>&quot;www.domain.com&quot;,</code>
        </p>
        <p><code>&quot;port&quot;:</code>
        </p>
        <p> <code>&quot;8080&quot;,</code>
        </p>
        <p><code>&quot;page&quot;:</code>
        </p>
        <p><code>&quot;page.html&quot;}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;123&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;^(?&lt;digits&gt;\d*)$&quot;</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left">
        <p><code>{&quot;digits&quot;:</code>
        </p>
        <p><code>&quot;123&quot;}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;foo&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;^(?&lt;digits&gt;\d*)$&quot;</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>null</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;^(?&lt;digits&gt;\d*)$&quot;</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>{&quot;digits&quot;: &quot;&quot;}</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;^(?&lt;digits&gt;\d*)$&quot;</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>true</code>
      </td>
      <td style="text-align:left"><code>null</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;www.upsolver.com&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;\bwww.(?&lt;domain&gt;[^\.]*).com\b&quot;</code>
      </td>
      <td style="text-align:left"><code>true</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left">
        <p><code>{&quot;domain&quot;:</code>
        </p>
        <p><code>&quot;upsolver&quot;}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;www.a.com www.b.com&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;\bwww.(?&lt;domain&gt;[^\.]*).com\b&quot;</code>
      </td>
      <td style="text-align:left"><code>true</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>{&quot;domain&quot;: &quot;a&quot;}</code>, <code>{&quot;domain&quot;: &quot;b&quot;}</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>&quot;www.a.com www.b.com&quot;</code>
      </td>
      <td style="text-align:left"><code>&quot;\bwww.(?&lt;domain&gt;[^\.]*).com\b&quot;</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>false</code>
      </td>
      <td style="text-align:left"><code>{&quot;domain&quot;: &quot;a&quot;}</code>
      </td>
    </tr>
  </tbody>
</table>

## `REPLACE`

Replace substrings within a string.

#### Properties

* **Pattern** - Pattern to replace \(regex\)
* **Replacement** - Replacement string

| value | Pattern | Replacement | result |
| :--- | :--- | :--- | :--- |
| `"Hello World"` | `"Hello"` | `null` | `" World"` |
| `"Hello World"` | `"Hello"` | `"foo"` | `"foo World"` |
| `"World"` | `"Hello"` | `"foo"` | `"World"` |

## `SHA1`

Hashes the input using SHA-1.

| input | result |
| :--- | :--- |
| `"hello world"` | `"2aae6c35c94fcfb415dbe95f408b9ce91ee846ed"` |

## `SHA256`

Hashes the input using SHA-256.

| input | result |
| :--- | :--- |
| `"Hello SHA"` | `"4ea3b17f15346417f4c9b2ff94a1bfe82de99fdb0bbd30dc4dca031ab920d5e4"` |

## `SPLIT`

Returns the given string split by the provided delimiter.

#### Properties

* **Delimiter**

| input | Delimiter | result |
| :--- | :--- | :--- |
| `"a,b,c,d"` | `","` | `"a"`, `"b"`, `"c"`, `"d"` |
| `"a,,b"` | `","` | `"a"`, `"b"` |
| `",a,b,"` | `","` | `"a"`, `"b"` |
| `"~~a~~b~~"` | `"~~"` | `"a"`, `"b"` |
| `"abc"` | `""` | `"a"`, `"b""c"`, |

## `SPLIT_TO_RECORD`

Returns the given string split by the provided delimiter.

#### Properties

* **Field Names**
* **Delimiter**
* **Filter Empty Values**

| value | Field Names | Delimiter | Filter Empty Values | result |
| :--- | :--- | :--- | :--- | :--- |
| `"1,2,3,4"` | `"a,b,c"` | `","` | `false` | `{"a": "1", "b": "2", "c": "3"}` |
| `"1,2"` | `"a,b,c"` | `","` | `false` | `{"a": "1", "b": "2", "c": ""}` |
| `"1,,3"` | `"a,b,c"` | `","` | `true` | `{"a": "1", "c": "3"}` |

## `STRING_FORMAT`

Format any number of inputs into a string using the given format.

#### Properties

* **Format String** - The format string where `{n}` prints the nth input. 
  * For example, the pattern `'{0}.{0}.{1}`' on the inputs `'a'` and `'b'` will result in the string `'a.a.b'`

| inputs | Format String | result |
| :--- | :--- | :--- |
| `"a"`, `"b"`, `"c"` | `"{0} {1} {2}"` | `"a b c"` |
| `1.23` | `"{0}"` | `"1.23"` |
| `0.5` | `"{0,number,percent}"` | `"50%"` |
| `1.23` | `"{0,number,#.###}"` | `"1.235"` |
| `1.2` | `"{0,number,#.###}"` | `"1.2"` |
| `1.23` | `"{0,number,0.000}"` | `"1.235"` |
| `1.2` | `"{0,number,0.000}"` | `"1.200"` |
| `1.23E8` | `"{0,number,###,###.###}"` | `"123,456,789.012"` |
| `1.23E8` | `"{0,number,000,000.000}"` | `"123,456,789.012"` |

## `STRING_LENGTH`

Gets the length of the string.

| input | result |
| :--- | :--- |
| `""` | `0` |
| `"Hello"` | `5` |

## `STRIP_MARGIN`

For each line remove prefix of control or whitespace characters followed by the given margin char.

#### Properties

* **Margin Char**

| input | Margin Char | result |
| :--- | :--- | :--- |
| `"Hello` `∣ World"` | `"∣"` | `"Hello` `World"` |

## `STRIP_PREFIX`

Remove the given prefix string from the beginning of the string.

#### Properties

* **Prefix**

| input | Prefix | result |
| :--- | :--- | :--- |
| `"((foo))"` | `"("` | `"(foo))"` |
| `"foo"` | `"("` | `"foo"` |

## `STRIP_SUFFIX`

Remove the given suffix string from the end of the string.

#### Properties

* **Suffix**

| input | Suffix | result |
| :--- | :--- | :--- |
| `"((foo))"` | `")"` | `"((foo)"` |
| `"foo"` | `")"` | `"foo"` |

## `SUBSTRING`

Returns a string that is a substring of the given string.

#### Inputs

* **value**
* **startPosition**
* **endPosition**

| value | startPosition | endPosition | result |
| :--- | :--- | :--- | :--- |
| `"Hello World"` | `0` | `5` | `"Hello"` |
| `"Hello"` | `0` | `-1` | `"Hello"` |
| `"Hello"` | `1` | `3` | `"el"` |
| `"Hello"` | `6` | `-1` | `""` |
| `"Hello"` | `-3` | `-2` | `"ll"` |

## `TOP_PRIVATE_DOMAIN`

Get the top private domain from a domain name.

| value | result |
| :--- | :--- |
| `"www.example.com"` | `"example.com"` |
| `"www.example.co.uk"` | `"example.co.uk"` |
| `"www.example.uk.com"` | `"example.uk.com"` |

## `TO_LOWER`

Converts the string to lowercase letters.

| input | result |
| :--- | :--- |
| `"HELLO world"` | `"hello world"` |

## `TO_UPPER`

Converts the string to uppercase letters.

| input | result |
| :--- | :--- |
| `"HELLO world"` | `"HELLO WORLD"` |

## `TRANSLATE`

Translates the given value using a given dictionary.

#### Properties

* **Dictionary**
* **Keep Values Without Translation** - Whether to keep values that have that are not mapped to a value in the feature
* **Empty As Null** - If set, empty values will be treated as null

| input | Dictionary | Keep Values Without Translation | Empty As Null | result |
| :--- | :--- | :--- | :--- | :--- |
| `"a"` | `"a,Antman` `b,Batman` `d,"` | `false` | `false` | `"Antman"` |
| `"b"` | `"a,Antman` `b,Batman` `d,"` | `false` | `false` | `"Batman"` |
| `"c"` | `"a,Antman` `b,Batman` `d,"` | `false` | `false` | `null` |
| `"c"` | `"a,Antman` `b,Batman` `d,"` | `true` | `false` | `"c"` |
| `"d"` | `"a,Antman` `b,Batman` `d,"` | `true` | `true` | `null` |
| `"d"` | `"a,Antman` `b,Batman` `d,"` | `true` | `false` | `""` |
| `1234` | `"1234.0,good"` | `false` | `false` | `"good"` |
| `1234` | `"1234.0,good"` | `false` | `false` | `"good"` |
| `0` | `"0.0,good"` | `false` | `false` | `"good"` |
| `0` | `"-0.0,good"` | `false` | `false` | `"good"` |
| `0` | `"-0.0,good"` | `false` | `false` | `"good"` |
| `123456000000000000` | `"1.23456e17,good"` | `false` | `false` | `"good"` |
| `6` | `"6.000000000000001,good"` | `false` | `false` | `null` |

## `TRIM`

Returns the given string without leading or trailing whitespaces.

| input | result |
| :--- | :--- |
| `"foo"` | `"foo"` |
| `" foo"` | `"foo"` |
| `"foo "` | `"foo"` |
| `" foo "` | `"foo"` |

## `TRIM_CHARS`

Returns the given string without leading or trailing characters.

#### Properties

* **Characters**

| input | Characters | result |
| :--- | :--- | :--- |
| `"-==--Hello World---=---"` | `"-="` | `"Hello World"` |
| `""` | `"-"` | `""` |
| `"-----------"` | `"-"` | `""` |
| `"x-----------"` | `"-"` | `"x"` |
| `"-----------x"` | `"-"` | `"x"` |
| `"------x-----"` | `"-"` | `"x"` |
| `"x-----------x"` | `"-"` | `"x-----------x"` |

## `URL_DECODE`

Decode url encoded text.

| input | result |
| :--- | :--- |
| `"The+quick+brown+fox"` | `"The quick brown fox"` |
| `"Comment+%235"` | `"Comment #5"` |

## `URL_ENCODE`

Encode text to url encoded format.

| input | result |
| :--- | :--- |
| `"The quick brown fox"` | `"The+quick+brown+fox"` |
| `"Comment #5"` | `"Comment+%235"` |

## `URL_PARSER`

Parses the URI/URL into its component parts.

| value | result |
| :--- | :--- |
| "https://www.domain.com/page.html" | {"scheme": "https", "authority": "www.domain.com", "host": "www.domain.com", "path": "/page.html"} |
| "https://user:pass@www.domain.com:80/page.html?query\#fragment" | {"scheme": "https", "user\_info": "user:pass", "authority": "user:pass@www.domain.com:80", "host": "www.domain.com", "port": 80, "path": "/page.html", "query": "query", "fragment": "fragment"} |
| "user:pass@www.domain.com/page.html?query" | {"user\_info": "user:pass", "authority": "user:pass@www.domain.com", "host": "www.domain.com", "path": "/page.html", "query": "query"} |
| "www.domain.com/page.html\#fragment" | {"authority": "www.domain.com", "host": "www.domain.com", "path": "/page.html", "fragment": "fragment"} |
| "/www.domain.com" | {"path": "/www.domain.com"} |

## `UUID_GENERATOR`

Returns UUID.

#### Inputs

* **hash** - Value for extra randomness

