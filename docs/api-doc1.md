---
id: api-doc1
title: List all country codes
---

### {{OGMServer}}/ogm/v1/codes

Returns country codes and names for all countries. The codes returned can be used to create regions.

<br/>

##### Response Object
|Field	|Parent |Type	|Description	|
|---	|---	|---	|---			|
| requestID	|	| string |  Unique log ID for this request.|
| timestamp	|	| string |  Date and time when executed.|
| `codeNames`	|	| object |  List of code names and full names for all countries. |
| code		|`codeNames`	| string|  Code name for the country.|
| name		|`codeNames`	| string|  Full name of the country.|

<br/>