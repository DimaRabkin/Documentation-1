---
description: This page goes over the external API functions in Upsolver.
---

# External API functions

## `GEO_IP`

Use an IP Address to lookup geo information.

#### Inputs

* **IP Address** - The IP address to use for geo ip information lookup

#### Properties

* **Attributes** - The attribute to extract for the given IP address

| IP Address | Attributes | result |
| :--- | :--- | :--- |
| `"2.87.124.4"` | `["Locale Code"]` | `"en"` |
| `"2.87.124.4"` | `["Continent Code"]` | `"EU"` |
| `"2.87.124.4"` | `["Continent Name"]` | `"Europe"` |
| `"2.87.124.4"` | `["Country Iso Code"]` | `"GR"` |
| `"2.87.124.4"` | `["Country Name"]` | `"Greece"` |
| `"2.87.124.4"` | `["Subdivision 1 Iso Code"]` | `"L"` |
| `"2.87.124.4"` | `["Subdivision 1 Name"]` | `"South Aegean"` |
| `"2.87.124.4"` | `["City Name"]` | `"Rhodes"` |
| `"2.87.124.4"` | `["Metro Code"]` | `""` |
| `"2.87.124.4"` | `["Time Zone"]` | `"Europe/Athens"` |

## `USER_AGENT_PARSER`

Parse the user agent and extract a parameter from it.

#### Inputs

* **User Agent String** - String representation of a user agent

#### Properties

* **Attributes** - The attributes to extract

<table>
  <thead>
    <tr>
      <th style="text-align:left">User Agent String</th>
      <th style="text-align:left">Attributes</th>
      <th style="text-align:left">result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>&quot;Mozilla/5.0</p>
        <p>(*Mac OS X 10?12*)</p>
        <p>adbeat.com*</p>
        <p>Version*</p>
        <p>Safari*&quot;</p>
      </td>
      <td style="text-align:left">
        <p>[&quot;Matching Pattern&quot;, &quot;Rendering</p>
        <p>Engine Maker&quot;, &quot;Rendering Engine</p>
        <p>Description&quot;, &quot;Rendering Engine</p>
        <p>Version&quot;, &quot;Rendering Engine Name&quot;,</p>
        <p>&quot;Device Brand Name&quot;, &quot;Device Code</p>
        <p>Name&quot;, &quot;Device Pointing Method&quot;,</p>
        <p>&quot;Device Type&quot;, &quot;Device Maker&quot;,</p>
        <p>&quot;Device Name&quot;, &quot;Aol Version&quot;, &quot;Css</p>
        <p>Version&quot;, &quot;Is Modified&quot;, &quot;Is</p>
        <p>Anonymized&quot;, &quot;Is Fake&quot;, &quot;Crawler&quot;,</p>
        <p>&quot;Is SyndicationReader&quot;, &quot;Is</p>
        <p>Tablet&quot;, &quot;Is MobileDevice&quot;,</p>
        <p>&quot;ActiveX Controls&quot;, &quot;Java</p>
        <p>Applets&quot;, &quot;VBScript&quot;,</p>
        <p>&quot;JavaScript&quot;, &quot;BackgroundSounds&quot;,</p>
        <p>&quot;Cookies&quot;, &quot;Tables&quot;, &quot;IFrames&quot;,</p>
        <p>&quot;Frames&quot;, &quot;Win64&quot;, &quot;Win32&quot;,</p>
        <p>&quot;Win16&quot;, &quot;Beta&quot;, &quot;Alpha&quot;,</p>
        <p>&quot;Platform Maker&quot;, &quot;Platform Bits&quot;,</p>
        <p>&quot;Platform Description&quot;, &quot;Platform</p>
        <p>Version&quot;, &quot;Platform&quot;, &quot;Minor</p>
        <p>Version&quot;, &quot;Major Version&quot;,</p>
        <p>&quot;Version&quot;, &quot;Browser Modus&quot;,</p>
        <p>&quot;Browser Maker&quot;, &quot;Browser Bits&quot;,</p>
        <p>&quot;Browser Type&quot;, &quot;Browser&quot;,</p>
        <p>&quot;Comment&quot;, &quot;Parent&quot;, &quot;LiteMode&quot;,</p>
        <p>&quot;Master Parent&quot;]</p>
      </td>
      <td style="text-align:left">
        <p>{&quot;Matching Pattern&quot;</p>
        <p>:&quot;Mozilla/5.0</p>
        <p>(*Mac OS X 10?12*)</p>
        <p>adbeat.com* Version* Safari*&quot;,</p>
        <p>&quot;Rendering Engine</p>
        <p>Maker&quot;: &quot;Apple Inc</p>
        <p>&quot;,&quot;Rendering Engine</p>
        <p>Description&quot;:</p>
        <p>&quot;For Google Chrome,</p>
        <p>iOS(including both</p>
        <p>mobile Safari,</p>
        <p>WebViews within third</p>
        <p>-party apps,and web</p>
        <p>clips),Safari,</p>
        <p>Arora, Midori,</p>
        <p>OmniWeb, Shiira,</p>
        <p>iCab since version 4,</p>
        <p>Web,SRWare Iron,</p>
        <p>Rekonq,and in</p>
        <p>Maxthon 3.&quot;,</p>
        <p>&quot;Rendering Engine</p>
        <p>Version&quot;: &quot;&quot;,</p>
        <p>&quot;Rendering Engine</p>
        <p>Name&quot;: &quot;WebKit&quot;,</p>
        <p>&quot;Device Brand Name&quot;: &quot;Apple&quot;,</p>
        <p>&quot;Device Code Name&quot;:</p>
        <p>&quot;Macintosh&quot;,</p>
        <p>&quot;Device Pointing</p>
        <p>Method&quot;: &quot;mouse&quot;,</p>
        <p>&quot;Device Type&quot;:</p>
        <p>&quot;Desktop&quot;,</p>
        <p>&quot;Device Maker&quot;:</p>
        <p>&quot;Apple Inc&quot;,</p>
        <p>&quot;Device Name&quot;:</p>
        <p>&quot;Macintosh&quot;,</p>
        <p>&quot;Aol Version&quot;:</p>
        <p>&quot;0&quot;, &quot;Css Version&quot;:</p>
        <p>&quot;0&quot;, &quot;Is Modified&quot;:</p>
        <p>&quot;false&quot;,</p>
        <p>&quot;Is Anonymized&quot;:</p>
        <p>&quot;false&quot;, &quot;Is Fake&quot;:</p>
        <p>&quot;false&quot;, &quot;Crawler&quot;:</p>
        <p>&quot;true&quot;,</p>
        <p>&quot;Is SyndicationReader</p>
        <p>&quot;:&quot;false&quot;,</p>
        <p>&quot;Is Tablet&quot;: &quot;false&quot;,</p>
        <p>&quot;Is MobileDevice&quot;:</p>
        <p>&quot;false&quot;,</p>
        <p>&quot;ActiveX Controls&quot;:</p>
        <p>&quot;false&quot;,</p>
        <p>&quot;Java Applets&quot;:</p>
        <p>&quot;true&quot;, &quot;VBScript&quot;:</p>
        <p>&quot;false&quot;,</p>
        <p>&quot;JavaScript&quot;:</p>
        <p>&quot;false&quot;,</p>
        <p>&quot;BackgroundSounds&quot;:</p>
        <p>&quot;false&quot;,</p>
        <p>&quot;Cookies&quot;: &quot;false&quot;,</p>
        <p>&quot;Tables&quot;: &quot;false&quot;,</p>
        <p>&quot;IFrames&quot;: &quot;false&quot;,</p>
        <p>&quot;Frames&quot;: &quot;false&quot;,</p>
        <p>&quot;Win64&quot;: &quot;false&quot;,</p>
        <p>&quot;Win32&quot;: &quot;false&quot;,</p>
        <p>&quot;Win16&quot;: &quot;false&quot;,</p>
        <p>&quot;Beta&quot;: &quot;false&quot;,</p>
        <p>&quot;Alpha&quot;: &quot;false&quot;,</p>
        <p>&quot;Platform Maker&quot;:</p>
        <p>&quot;Apple Inc&quot;,</p>
        <p>&quot;Platform Bits&quot;:</p>
        <p>&quot;32&quot;,</p>
        <p>&quot;Platform Description</p>
        <p>&quot;:&quot;macOS&quot;,</p>
        <p>&quot;Platform Version&quot;:</p>
        <p>&quot;10.12&quot;,</p>
        <p>&quot;Platform&quot;: &quot;macOS&quot;,</p>
        <p>&quot;Minor Version&quot;: &quot;0&quot;</p>
        <p>&quot;Major Version&quot;: &quot;0&quot;,</p>
        <p>&quot;Version&quot;: &quot;0.0&quot;,</p>
        <p>&quot;Browser Modus&quot;: &quot;&quot;,</p>
        <p>&quot;Browser Maker&quot;:</p>
        <p>&quot;adbeat.com&quot;,</p>
        <p>&quot;Browser Bits&quot;:&quot;32&quot;,</p>
        <p>&quot;Browser Type&quot;:</p>
        <p>&quot;Bot/Crawler&quot;,</p>
        <p>&quot;Browser&quot;:</p>
        <p>&quot;Adbeat Bot&quot;,</p>
        <p>&quot;Comment&quot;: &quot;Adbeat&quot;,</p>
        <p>&quot;Parent&quot;: &quot;Adbeat&quot;,</p>
        <p>&quot;LiteMode&quot;: &quot;false&quot;,</p>
        <p>&quot;Master Parent&quot;:</p>
        <p>&quot;false&quot;}</p>
      </td>
    </tr>
  </tbody>
</table>

## `WURFL_USER_AGENT`

Extracts user agent info using WURFL engine.

#### Inputs

* **User Agent** - The User Agent string to parse

#### Properties

* **Connection** - The connection to the bucket that contains the browsers.list file
* **Wurfl File** - The path to the browsers.list file within the connection

