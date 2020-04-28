---
id: api-geography
title: Geography 
sidebar_label: Geography 
---

The *geography* endpoints allow administrators to define geographic regions to be 
associated with assets and packages. 
Assets associated with a region will only appear in searches when the subscriber 
is in that particular region. Similarly, packages associated with a region will 
only appear in API responses for subscribers located in that region.

Note that in cases where a region border cannot be determined precisely, subscribers 
on that border may need to be assigned to BOTH regions to ensure their access to an 
asset or package. 

---

## Administration

API endpoints used to create and delete geographic regions.


### Create or update region from lat/long/radius

Creates or updates the specified region. 

* If an ID is specified, the region is created (or updated, if it already exists).
* If no ID has been specified, a new ID and region are created.
* Regions are created using a combination of latitude, longitude, and radius to define a circle. The *unit* of the radius must be specified as *"MI"* or *"KM"*.


#### Body Parameters
|Field	|Parent	|Type	|Required	|Description	|
|---	|---	|---	|---		|---			|
|name	|		|string	|required	| Name/ID of the region.|
|type	|		|string	|required	| Region type. Supported values are *circle* and *locations*.|
|`circle`	|	|object	|required	| Region definition.|
|latitude	|`circle`	|real		|required	| Global latitude position; 34.0522, for example.|
|longitude	|`circle`	|real	|required	| Global longitude position; -118.2437, for example.|
|radius		|`circle`	|real	|required	| 20.0, for example.|
|unit		|`circle`	|string	|required	| Either *"KM"* for kilometers or *"MI"* for miles.|

<br/>

***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OGMServer}}/ogm/v1/regions
```

<br>  
<br>  

***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |


<br> <br>

***Body:***

```js        
{
    "name": "OGM Circle Region",
    "circle": {
        "latitude": 34.0522,
        "longitude": -118.2437,
        "radius": 20,
        "unit": "KM"
    },
    "type": "circle"
}
```



***Responses:***


Status: Put OGM Circle Region in miles | Code: 200



```js
{
    "requestID": "6840ba60-197a-4166-b139-4f6c1556069e",
    "timestamp": "2018-07-13T23:25:34.720828615Z",
    "id": "d6d66875-b407-4201-95e9-69c3b7baf376",
    "count": 1
}
```



Status: Put OGM Circle Region in Kilometers | Code: 200



```js
{
    "requestID": "65d3e075-21a6-41d6-87a7-d8521293a2e0",
    "timestamp": "2018-07-13T23:27:20.407913441Z",
    "id": "22d9f5f7-8458-418a-be2b-8d2b7551cb7a",
    "count": 1
}
```



### Create or update region from country/region/city/postal codes

Creates or updates the specified region. 

* If an existing ID is specified, that region is updated; otherwise, a new region is created using the specified ID.
* Regions are created using _codes_ for country, region, city, and postal code. The codes used must match the ones returned by the [Geography endpoints](https://docs.dtc.istreamplanet.net/#c41f01eb-8dcf-4b48-b681-9729e8c25c0c) for country, region, and city. 
* Postal codes are simple strings which, if used, must match the strings returned for the designated country.

<br/>

####  Body Parameters
|Field	|Parent	|Type	|Required	|Description	|
|---	|---	|---	|---		|---			|
|name	|		|string	|required|	 Name/ID of the region.|
|type	|		|string	|required	|  Region type. Supported values are [circle, locations].|
|`locations`	|	|object	|required	| Region definition.|
|countryCode	|`locations`	|string	|required| Code for a geographic nation; "usa", for example.|
|regionCode		|`locations`	|string	|optional| Code for a geographic subsection; "wa", for example.|
|cityCode		|`locations`	|string	|optional| Code for a designated city; "114", for example.|
|postalCode		|`locations`	|string	|optional| A valid code for the country/region; "98144"  for example.|

<br/>

#### Response Object
|Field		|Type	|Description	|
|---		|---	|---			|
|requestID	|string	| Unique log ID for this request.|
|timestamp	|string	| Date and time when executed.|
|count		|integer| Count for each response beginning with 1.|
| id		|string	| Region ID.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OGMServer}}/ogm/v1/regions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "name": "OGM Region Los Angeles No ID",
    "locations": [
        {
            "countryCode": "usa",
            "regionCode": "ca",
            "cityCode": "113"
        }
    ],
    "type": "locations"
}
```



***Responses:***


Status: Put OGM Region without Region ID | Code: 200



```js
{"requestID":"926ff722-5e4d-4d0a-ac0c-e2f2e60e222f","timestamp":"2018-07-09T21:48:25.788856586Z","id":"a36fdfe4-34a3-4ad6-85ff-1498637c76ae","count":1}
```



Status: Put OGM Region with Region ID | Code: 200



```js
{"requestID":"1cd5bab6-59df-4345-9177-106adfc55219","timestamp":"2018-06-12T18:54:50.136238713Z","id":"ogm-region-1","count":1}
```



### Delete region

Deletes the specified region ID.

<br/>

#### Path Parameters
|Label		|Type	|Required	|Description	|
|---		|---	|---		|---			|
|ogmRegion	|string	|required	| The ID of the region to be deleted.|

<br/>

#### Response Object
|Field		|Type	|Description	|
|---		|---	|---			|
|requestID	|string | The unique log ID for this request.|
|timestamp	|string | The date and time when executed.|
|id			|string | The region ID. |
|count		|integer| The count for each response beginning with 0.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target region.|
|404		|1040	|*Not Found*: Target region not found.|

<br/>



***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OGMServer}}/ogm/v1/regions/{{ogmRegion}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Delete OGM Region | Code: 200



```js
{"requestID":"c17640e7-c266-4577-b444-945f336e8822","timestamp":"2018-06-12T18:55:09.335190859Z","id":"ogm-region-1","count":0}
```



## Code Retrieval

API endpoints for retrieving country, local region (such as state/province/territory), 
and city codes used to specify and build geographic regions.


### List all country codes

Returns country codes and names for all countries. The codes returned can be used to create regions.

<br/>

#### Response Object
|Field	|Parent |Type	|Description	|
|---	|---	|---	|---			|
| requestID	|	| string |  Unique log ID for this request.|
| timestamp	|	| string |  Date and time when executed.|
| `codeNames`	|	| object |  List of code names and full names for all countries. |
| code		|`codeNames`	| string|  Code name for the country.|
| name		|`codeNames`	| string|  Full name of the country.|


<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OGMServer}}/ogm/v1/codes
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get Geo Country Codes | Code: 200



```js
{
    "requestID": "b77aed78-0264-41f9-999c-9ffd5c172981",
    "timestamp": "2018-06-12T18:52:06.162203917Z",
    "codeNames": [
        {
            "code": "***",
            "name": "Reserved/Private"
        },
        {
            "code": "?",
            "name": "Unknown"
        },
        {
            "code": "abw",
            "name": "Aruba"
        },
        {
            "code": "afg",
            "name": "Afghanistan"
        },
        {
            "code": "ago",
            "name": "Angola"
        },
        {
            "code": "aia",
            "name": "Anguilla"
        },
        {
            "code": "ala",
            "name": "Aland Islands"
        },
        {
            "code": "alb",
            "name": "Albania"
        },
        {
            "code": "and",
            "name": "Andorra"
        },
        {
            "code": "ant",
            "name": "Netherlands Antilles"
        },
        {
            "code": "are",
            "name": "United Arab Emirates"
        },
        {
            "code": "arg",
            "name": "Argentina"
        },
        {
            "code": "arm",
            "name": "Armenia"
        },
        {
            "code": "asi",
            "name": "Asia (Unknown Country)"
        },
        {
            "code": "asm",
            "name": "American Samoa"
        },
        {
            "code": "ata",
            "name": "Antarctica"
        },
        {
            "code": "atf",
            "name": "French Southern Territories"
        },
        {
            "code": "atg",
            "name": "Antigua and Barbuda"
        },
        {
            "code": "aus",
            "name": "Australia"
        },
        {
            "code": "aut",
            "name": "Austria"
        },
        {
            "code": "aze",
            "name": "Azerbaijan"
        },
        {
            "code": "bdi",
            "name": "Burundi"
        },
        {
            "code": "bel",
            "name": "Belgium"
        },
        {
            "code": "ben",
            "name": "Benin"
        },
        {
            "code": "bes",
            "name": "Bonaire/Sint Eustatius/Saba"
        },
        {
            "code": "bfa",
            "name": "Burkina Faso"
        },
        {
            "code": "bgd",
            "name": "Bangladesh"
        },
        {
            "code": "bgr",
            "name": "Bulgaria"
        },
        {
            "code": "bhr",
            "name": "Bahrain"
        },
        {
            "code": "bhs",
            "name": "Bahamas"
        },
        {
            "code": "bih",
            "name": "Bosnia And Herzegovina"
        },
        {
            "code": "blm",
            "name": "Saint Barthelemy"
        },
        {
            "code": "blr",
            "name": "Belarus"
        },
        {
            "code": "blz",
            "name": "Belize"
        },
        {
            "code": "bmu",
            "name": "Bermuda"
        },
        {
            "code": "bol",
            "name": "Bolivia"
        },
        {
            "code": "bra",
            "name": "Brazil"
        },
        {
            "code": "brb",
            "name": "Barbados"
        },
        {
            "code": "brn",
            "name": "Brunei Darussalam"
        },
        {
            "code": "btn",
            "name": "Bhutan"
        },
        {
            "code": "bvt",
            "name": "Bouvet Island"
        },
        {
            "code": "bwa",
            "name": "Botswana"
        },
        {
            "code": "caf",
            "name": "Central African Republic"
        },
        {
            "code": "can",
            "name": "Canada"
        },
        {
            "code": "cck",
            "name": "Cocos (Keeling) Islands"
        },
        {
            "code": "che",
            "name": "Switzerland"
        },
        {
            "code": "chl",
            "name": "Chile"
        },
        {
            "code": "chn",
            "name": "China"
        },
        {
            "code": "civ",
            "name": "Cote D Ivoire"
        },
        {
            "code": "cmr",
            "name": "Cameroon"
        },
        {
            "code": "cod",
            "name": "Democratic Republic Of The Congo"
        },
        {
            "code": "cog",
            "name": "Congo"
        },
        {
            "code": "cok",
            "name": "Cook Islands"
        },
        {
            "code": "col",
            "name": "Colombia"
        },
        {
            "code": "com",
            "name": "Comoros"
        },
        {
            "code": "cpv",
            "name": "Cape Verde"
        },
        {
            "code": "cri",
            "name": "Costa Rica"
        },
        {
            "code": "cub",
            "name": "Cuba"
        },
        {
            "code": "cuw",
            "name": "Curacao"
        },
        {
            "code": "cxr",
            "name": "Christmas Island"
        },
        {
            "code": "cym",
            "name": "Cayman Islands"
        },
        {
            "code": "cyp",
            "name": "Cyprus"
        },
        {
            "code": "cze",
            "name": "Czech Republic"
        },
        {
            "code": "deu",
            "name": "Germany"
        },
        {
            "code": "dji",
            "name": "Djibouti"
        },
        {
            "code": "dma",
            "name": "Dominica"
        },
        {
            "code": "dnk",
            "name": "Denmark"
        },
        {
            "code": "dom",
            "name": "Dominican Republic"
        },
        {
            "code": "dza",
            "name": "Algeria"
        },
        {
            "code": "ecu",
            "name": "Ecuador"
        },
        {
            "code": "egy",
            "name": "Egypt"
        },
        {
            "code": "eri",
            "name": "Eritrea"
        },
        {
            "code": "esh",
            "name": "Western Sahara"
        },
        {
            "code": "esp",
            "name": "Spain"
        },
        {
            "code": "est",
            "name": "Estonia"
        },
        {
            "code": "eth",
            "name": "Ethiopia"
        },
        {
            "code": "eur",
            "name": "Europe (Unknown Country)"
        },
        {
            "code": "fin",
            "name": "Finland"
        },
        {
            "code": "fji",
            "name": "Fiji"
        },
        {
            "code": "flk",
            "name": "Falkland Islands (Malvinas)"
        },
        {
            "code": "fra",
            "name": "France"
        },
        {
            "code": "fro",
            "name": "Faroe Islands"
        },
        {
            "code": "fsm",
            "name": "Federated States Of Micronesia"
        },
        {
            "code": "gab",
            "name": "Gabon"
        },
        {
            "code": "gbr",
            "name": "United Kingdom"
        },
        {
            "code": "geo",
            "name": "Georgia"
        },
        {
            "code": "ggy",
            "name": "Guernsey"
        },
        {
            "code": "gha",
            "name": "Ghana"
        },
        {
            "code": "gib",
            "name": "Gibraltar"
        },
        {
            "code": "gin",
            "name": "Guinea"
        },
        {
            "code": "glp",
            "name": "Guadeloupe"
        },
        {
            "code": "gmb",
            "name": "Gambia"
        },
        {
            "code": "gnb",
            "name": "Guinea-Bissau"
        },
        {
            "code": "gnq",
            "name": "Equatorial Guinea"
        },
        {
            "code": "grc",
            "name": "Greece"
        },
        {
            "code": "grd",
            "name": "Grenada"
        },
        {
            "code": "grl",
            "name": "Greenland"
        },
        {
            "code": "gtm",
            "name": "Guatemala"
        },
        {
            "code": "guf",
            "name": "French Guiana"
        },
        {
            "code": "gum",
            "name": "Guam"
        },
        {
            "code": "guy",
            "name": "Guyana"
        },
        {
            "code": "hkg",
            "name": "Hong Kong"
        },
        {
            "code": "hmd",
            "name": "Heard And Mc Donald Islands"
        },
        {
            "code": "hnd",
            "name": "Honduras"
        },
        {
            "code": "hrv",
            "name": "Croatia"
        },
        {
            "code": "hti",
            "name": "Haiti"
        },
        {
            "code": "hun",
            "name": "Hungary"
        },
        {
            "code": "idn",
            "name": "Indonesia"
        },
        {
            "code": "imn",
            "name": "Isle of Man"
        },
        {
            "code": "ind",
            "name": "India"
        },
        {
            "code": "iot",
            "name": "British Indian Ocean Territory"
        },
        {
            "code": "irl",
            "name": "Ireland"
        },
        {
            "code": "irn",
            "name": "Iran (Islamic Republic Of)"
        },
        {
            "code": "irq",
            "name": "Iraq"
        },
        {
            "code": "isl",
            "name": "Iceland"
        },
        {
            "code": "isr",
            "name": "Israel"
        },
        {
            "code": "ita",
            "name": "Italy"
        },
        {
            "code": "jam",
            "name": "Jamaica"
        },
        {
            "code": "jey",
            "name": "Jersey"
        },
        {
            "code": "jor",
            "name": "Jordan"
        },
        {
            "code": "jpn",
            "name": "Japan"
        },
        {
            "code": "kaz",
            "name": "Kazakhstan"
        },
        {
            "code": "ken",
            "name": "Kenya"
        },
        {
            "code": "kgz",
            "name": "Kyrgyzstan"
        },
        {
            "code": "khm",
            "name": "Cambodia"
        },
        {
            "code": "kir",
            "name": "Kiribati"
        },
        {
            "code": "kna",
            "name": "Saint Kitts and Nevis"
        },
        {
            "code": "kor",
            "name": "South Korea"
        },
        {
            "code": "kwt",
            "name": "Kuwait"
        },
        {
            "code": "lao",
            "name": "Lao Peoples Democratic Republic"
        },
        {
            "code": "lbn",
            "name": "Lebanon"
        },
        {
            "code": "lbr",
            "name": "Liberia"
        },
        {
            "code": "lby",
            "name": "Libyan Arab Jamahiriya"
        },
        {
            "code": "lca",
            "name": "Saint Lucia"
        },
        {
            "code": "lie",
            "name": "Liechtenstein"
        },
        {
            "code": "lka",
            "name": "Sri Lanka"
        },
        {
            "code": "lso",
            "name": "Lesotho"
        },
        {
            "code": "ltu",
            "name": "Lithuania"
        },
        {
            "code": "lux",
            "name": "Luxembourg"
        },
        {
            "code": "lva",
            "name": "Latvia"
        },
        {
            "code": "mac",
            "name": "Macau"
        },
        {
            "code": "maf",
            "name": "Saint Martin"
        },
        {
            "code": "mar",
            "name": "Morocco"
        },
        {
            "code": "mco",
            "name": "Monaco"
        },
        {
            "code": "mda",
            "name": "Moldova"
        },
        {
            "code": "mdg",
            "name": "Madagascar"
        },
        {
            "code": "mdv",
            "name": "Maldives"
        },
        {
            "code": "mex",
            "name": "Mexico"
        },
        {
            "code": "mhl",
            "name": "Marshall Islands"
        },
        {
            "code": "mkd",
            "name": "Macedonia"
        },
        {
            "code": "mli",
            "name": "Mali"
        },
        {
            "code": "mlt",
            "name": "Malta"
        },
        {
            "code": "mmr",
            "name": "Myanmar"
        },
        {
            "code": "mne",
            "name": "Montenegro"
        },
        {
            "code": "mng",
            "name": "Mongolia"
        },
        {
            "code": "mnp",
            "name": "Northern Mariana Islands"
        },
        {
            "code": "moz",
            "name": "Mozambique"
        },
        {
            "code": "mrt",
            "name": "Mauritania"
        },
        {
            "code": "msr",
            "name": "Montserrat"
        },
        {
            "code": "mtq",
            "name": "Martinique"
        },
        {
            "code": "mus",
            "name": "Mauritius"
        },
        {
            "code": "mwi",
            "name": "Malawi"
        },
        {
            "code": "mys",
            "name": "Malaysia"
        },
        {
            "code": "myt",
            "name": "Mayotte"
        },
        {
            "code": "nam",
            "name": "Namibia"
        },
        {
            "code": "ncl",
            "name": "New Caledonia"
        },
        {
            "code": "ner",
            "name": "Niger"
        },
        {
            "code": "nfk",
            "name": "Norfolk Island"
        },
        {
            "code": "nga",
            "name": "Nigeria"
        },
        {
            "code": "nic",
            "name": "Nicaragua"
        },
        {
            "code": "niu",
            "name": "Niue"
        },
        {
            "code": "nld",
            "name": "Netherlands"
        },
        {
            "code": "nor",
            "name": "Norway"
        },
        {
            "code": "npl",
            "name": "Nepal"
        },
        {
            "code": "nru",
            "name": "Nauru"
        },
        {
            "code": "nzl",
            "name": "New Zealand"
        },
        {
            "code": "omn",
            "name": "Oman"
        },
        {
            "code": "pak",
            "name": "Pakistan"
        },
        {
            "code": "pan",
            "name": "Panama"
        },
        {
            "code": "pcn",
            "name": "Pitcairn"
        },
        {
            "code": "per",
            "name": "Peru"
        },
        {
            "code": "phl",
            "name": "Philippines"
        },
        {
            "code": "plw",
            "name": "Palau"
        },
        {
            "code": "png",
            "name": "Papua New Guinea"
        },
        {
            "code": "pol",
            "name": "Poland"
        },
        {
            "code": "pri",
            "name": "Puerto Rico"
        },
        {
            "code": "prk",
            "name": "North Korea"
        },
        {
            "code": "prt",
            "name": "Portugal"
        },
        {
            "code": "pry",
            "name": "Paraguay"
        },
        {
            "code": "pse",
            "name": "Palestinian Territories"
        },
        {
            "code": "pyf",
            "name": "French Polynesia"
        },
        {
            "code": "qat",
            "name": "Qatar"
        },
        {
            "code": "reu",
            "name": "Reunion"
        },
        {
            "code": "rou",
            "name": "Romania"
        },
        {
            "code": "rus",
            "name": "Russian Federation"
        },
        {
            "code": "rwa",
            "name": "Rwanda"
        },
        {
            "code": "sau",
            "name": "Saudi Arabia"
        },
        {
            "code": "sdn",
            "name": "Sudan"
        },
        {
            "code": "sen",
            "name": "Senegal"
        },
        {
            "code": "sgp",
            "name": "Singapore"
        },
        {
            "code": "sgs",
            "name": "South Georgia / South Sandwich Isl"
        },
        {
            "code": "shn",
            "name": "St. Helena"
        },
        {
            "code": "sjm",
            "name": "Svalbard And Jan Mayen Islands"
        },
        {
            "code": "slb",
            "name": "Solomon Islands"
        },
        {
            "code": "sle",
            "name": "Sierra Leone"
        },
        {
            "code": "slv",
            "name": "El Salvador"
        },
        {
            "code": "smr",
            "name": "San Marino"
        },
        {
            "code": "som",
            "name": "Somalia"
        },
        {
            "code": "spm",
            "name": "St. Pierre And Miquelon"
        },
        {
            "code": "srb",
            "name": "Serbia"
        },
        {
            "code": "ssd",
            "name": "South Sudan"
        },
        {
            "code": "stp",
            "name": "Sao Tome and Principe"
        },
        {
            "code": "sur",
            "name": "Suriname"
        },
        {
            "code": "svk",
            "name": "Slovakia (Slovak Republic)"
        },
        {
            "code": "svn",
            "name": "Slovenia"
        },
        {
            "code": "swe",
            "name": "Sweden"
        },
        {
            "code": "swz",
            "name": "Swaziland"
        },
        {
            "code": "sxm",
            "name": "Sint Maarten"
        },
        {
            "code": "syc",
            "name": "Seychelles"
        },
        {
            "code": "syr",
            "name": "Syrian Arab Republic"
        },
        {
            "code": "tca",
            "name": "Turks and Caicos Islands"
        },
        {
            "code": "tcd",
            "name": "Chad"
        },
        {
            "code": "tgo",
            "name": "Togo"
        },
        {
            "code": "tha",
            "name": "Thailand"
        },
        {
            "code": "tjk",
            "name": "Tajikistan"
        },
        {
            "code": "tkl",
            "name": "Tokelau"
        },
        {
            "code": "tkm",
            "name": "Turkmenistan"
        },
        {
            "code": "tls",
            "name": "Timor-Leste"
        },
        {
            "code": "ton",
            "name": "Tonga"
        },
        {
            "code": "tto",
            "name": "Trinidad and Tobago"
        },
        {
            "code": "tun",
            "name": "Tunisia"
        },
        {
            "code": "tur",
            "name": "Turkey"
        },
        {
            "code": "tuv",
            "name": "Tuvalu"
        },
        {
            "code": "twn",
            "name": "Taiwan Province Of China"
        },
        {
            "code": "tza",
            "name": "Tanzania"
        },
        {
            "code": "uga",
            "name": "Uganda"
        },
        {
            "code": "ukr",
            "name": "Ukraine"
        },
        {
            "code": "umi",
            "name": "Us Minor Outlying Islands"
        },
        {
            "code": "ury",
            "name": "Uruguay"
        },
        {
            "code": "usa",
            "name": "United States"
        },
        {
            "code": "uzb",
            "name": "Uzbekistan"
        },
        {
            "code": "vat",
            "name": "Holy See (Vatican City State)"
        },
        {
            "code": "vct",
            "name": "Saint Vincent and the Grenadines"
        },
        {
            "code": "ven",
            "name": "Venezuela"
        },
        {
            "code": "vgb",
            "name": "British Virgin Islands"
        },
        {
            "code": "vir",
            "name": "Us Virgin Islands"
        },
        {
            "code": "vnm",
            "name": "Viet Nam"
        },
        {
            "code": "vut",
            "name": "Vanuatu"
        },
        {
            "code": "wlf",
            "name": "Wallis And Futuna Islands"
        },
        {
            "code": "wsm",
            "name": "Samoa"
        },
        {
            "code": "yem",
            "name": "Yemen"
        },
        {
            "code": "zaf",
            "name": "South Africa"
        },
        {
            "code": "zmb",
            "name": "Zambia"
        },
        {
            "code": "zwe",
            "name": "Zimbabwe"
        }
    ]
}
```



### List all state codes for a country

Returns all codes and full names for all states or provinces in the specified country. The codes returned can be used to create regions.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|countryCode	|string	|required	| The code name for the country.|

<br/>

#### Response Object
|Field	|Parent |Type	|Description	|
|---	|---	|---	|---			|
| requestID	|	| string | Unique log ID for this request.|
| timestamp	|	| string | Date and time when executed.|
| `codeNames`	|	| object | List of code names and full names for all states or provinces in the specified country. |
| code		|`codeNames`	| string| Code name for the state or province.|
| name		|`codeNames`	| string| Full name of the state or province.|


<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OGMServer}}/ogm/v1/codes/{{countryCode}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get Geo Region Codes (USA) | Code: 200



```js
{"requestID":"be9b368e-f230-4815-b454-7b88e7aa7bbb","timestamp":"2018-06-12T18:52:26.860368927Z","codeNames":[{"code":"aol","name":"AOL"},{"code":"al","name":"Alabama"},{"code":"ak","name":"Alaska"},{"code":"az","name":"Arizona"},{"code":"ar","name":"Arkansas"},{"code":"ca","name":"California"},{"code":"co","name":"Colorado"},{"code":"ct","name":"Connecticut"},{"code":"de","name":"Delaware"},{"code":"dc","name":"District Of Columbia"},{"code":"fl","name":"Florida"},{"code":"ga","name":"Georgia"},{"code":"hi","name":"Hawaii"},{"code":"id","name":"Idaho"},{"code":"il","name":"Illinois"},{"code":"in","name":"Indiana"},{"code":"ia","name":"Iowa"},{"code":"ks","name":"Kansas"},{"code":"ky","name":"Kentucky"},{"code":"la","name":"Louisiana"},{"code":"me","name":"Maine"},{"code":"md","name":"Maryland"},{"code":"ma","name":"Massachusetts"},{"code":"mi","name":"Michigan"},{"code":"mn","name":"Minnesota"},{"code":"ms","name":"Mississippi"},{"code":"mo","name":"Missouri"},{"code":"mt","name":"Montana"},{"code":"ne","name":"Nebraska"},{"code":"nv","name":"Nevada"},{"code":"nh","name":"New Hampshire"},{"code":"nj","name":"New Jersey"},{"code":"nm","name":"New Mexico"},{"code":"ny","name":"New York"},{"code":"nc","name":"North Carolina"},{"code":"nd","name":"North Dakota"},{"code":"oh","name":"Ohio"},{"code":"ok","name":"Oklahoma"},{"code":"or","name":"Oregon"},{"code":"pa","name":"Pennsylvania"},{"code":"ri","name":"Rhode Island"},{"code":"sc","name":"South Carolina"},{"code":"sd","name":"South Dakota"},{"code":"tn","name":"Tennessee"},{"code":"tx","name":"Texas"},{"code":"?","name":"United States"},{"code":"ut","name":"Utah"},{"code":"vt","name":"Vermont"},{"code":"va","name":"Virginia"},{"code":"wa","name":"Washington"},{"code":"webtv","name":"Webtv"},{"code":"wv","name":"West Virginia"},{"code":"wi","name":"Wisconsin"},{"code":"wy","name":"Wyoming"}]}
```



### List city codes

Returns city codes and names for all cities in the specified country and state. The codes returned can be used to create regions.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
| countryCode	| string	|required	| The code name for the country.|
| stateCode		| string	|required	| The code name of the state.|

<br/>

#### Response Object
|Field	|Parent |Type	|Description	|
|---	|---	|---	|---			|
| requestID	|	| string | The unique log ID for this request.|
| timestamp	|	| string | The date and time when executed.|
| `codeNames`	|	| object | The list of code names and full names for all cities in the specified country and state. |
| code		|`codeNames`	| string| The code name for the city.|
| name		|`codeNames`	| string| The full name of the city.|



***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OGMServer}}/ogm/v1/codes/{{countryCode}}/{{stateCode}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get Geo City Codes (USA/WA) | Code: 200



```js
{
    "requestID": "fc0cc987-5146-480b-8c54-ca620cb39c05",
    "timestamp": "2018-06-12T16:30:18.277402282Z",
    "codeNames": [
        {
            "code": "1503",
            "name": "?"
        },
        {
            "code": "1138",
            "name": "Aberdeen"
        },
        {
            "code": "30739",
            "name": "Acme"
        },
        {
            "code": "20484",
            "name": "Addy"
        },
        {
            "code": "38274",
            "name": "Adna"
        },
        {
            "code": "30740",
            "name": "Airway Heights"
        },
        {
            "code": "60888",
            "name": "Albion"
        },
        {
            "code": "46051",
            "name": "Allyn"
        },
        {
            "code": "33703",
            "name": "Almira"
        },
        {
            "code": "20509",
            "name": "Amanda Park"
        },
        {
            "code": "50632",
            "name": "Amboy"
        },
        {
            "code": "2293",
            "name": "Anacortes"
        },
        {
            "code": "30741",
            "name": "Anatone"
        },
        {
            "code": "45739",
            "name": "Anderson Island"
        },
        {
            "code": "60841",
            "name": "Appleton"
        },
        {
            "code": "60854",
            "name": "Ardenvoir"
        },
        {
            "code": "48863",
            "name": "Ariel"
        },
        {
            "code": "6308",
            "name": "Arlington"
        },
        {
            "code": "50633",
            "name": "Ashford"
        },
        {
            "code": "33704",
            "name": "Asotin"
        },
        {
            "code": "496",
            "name": "Auburn"
        },
        {
            "code": "2978",
            "name": "Bainbridge Island"
        },
        {
            "code": "48079",
            "name": "Baring"
        },
        {
            "code": "9924",
            "name": "Battle Ground"
        },
        {
            "code": "61621",
            "name": "Bay Center"
        },
        {
            "code": "51206",
            "name": "Beaver"
        },
        {
            "code": "38972",
            "name": "Belfair"
        },
        {
            "code": "1312",
            "name": "Bellevue"
        },
        {
            "code": "273",
            "name": "Bellingham"
        },
        {
            "code": "60889",
            "name": "Belmont"
        },
        {
            "code": "20500",
            "name": "Benge"
        },
        {
            "code": "38719",
            "name": "Benton City"
        },
        {
            "code": "60908",
            "name": "Beverly"
        },
        {
            "code": "39206",
            "name": "Bickleton"
        },
        {
            "code": "30742",
            "name": "Bingen"
        },
        {
            "code": "2291",
            "name": "Black Diamond"
        },
        {
            "code": "4372",
            "name": "Blaine"
        },
        {
            "code": "65066",
            "name": "Blakely Island"
        },
        {
            "code": "50634",
            "name": "Bonney Lake"
        },
        {
            "code": "757",
            "name": "Bothell"
        },
        {
            "code": "19907",
            "name": "Bow"
        },
        {
            "code": "1038",
            "name": "Bremerton"
        },
        {
            "code": "11985",
            "name": "Brewster"
        },
        {
            "code": "39207",
            "name": "Bridgeport"
        },
        {
            "code": "30743",
            "name": "Brinnon"
        },
        {
            "code": "60872",
            "name": "Brownstown"
        },
        {
            "code": "38276",
            "name": "Brush Prairie"
        },
        {
            "code": "15152",
            "name": "Buckley"
        },
        {
            "code": "60821",
            "name": "Bucoda"
        },
        {
            "code": "23782",
            "name": "Buena"
        },
        {
            "code": "38720",
            "name": "Burbank"
        },
        {
            "code": "60808",
            "name": "Burley"
        },
        {
            "code": "1598",
            "name": "Burlington"
        },
        {
            "code": "11768",
            "name": "Burton"
        },
        {
            "code": "44797",
            "name": "Camano Island"
        },
        {
            "code": "690",
            "name": "Camas"
        },
        {
            "code": "50635",
            "name": "Camp Murray"
        },
        {
            "code": "34642",
            "name": "Carbonado"
        },
        {
            "code": "60809",
            "name": "Carlsborg"
        },
        {
            "code": "47360",
            "name": "Carlton"
        },
        {
            "code": "13157",
            "name": "Carnation"
        },
        {
            "code": "60842",
            "name": "Carrolls"
        },
        {
            "code": "60843",
            "name": "Carson"
        },
        {
            "code": "595",
            "name": "Cashmere"
        },
        {
            "code": "38976",
            "name": "Castle Rock"
        },
        {
            "code": "13417",
            "name": "Cathlamet"
        },
        {
            "code": "20507",
            "name": "Centerville"
        },
        {
            "code": "383",
            "name": "Centralia"
        },
        {
            "code": "50636",
            "name": "Chattaroy"
        },
        {
            "code": "7878",
            "name": "Chehalis"
        },
        {
            "code": "15540",
            "name": "Chelan"
        },
        {
            "code": "60855",
            "name": "Chelan Falls"
        },
        {
            "code": "3264",
            "name": "Cheney"
        },
        {
            "code": "9132",
            "name": "Chewelah"
        },
        {
            "code": "38959",
            "name": "Chimacum"
        },
        {
            "code": "50637",
            "name": "Chinook"
        },
        {
            "code": "46068",
            "name": "Cinebar"
        },
        {
            "code": "51309",
            "name": "Clallam Bay"
        },
        {
            "code": "6007",
            "name": "Clarkston"
        },
        {
            "code": "48629",
            "name": "Clayton"
        },
        {
            "code": "30744",
            "name": "Cle Elum"
        },
        {
            "code": "21051",
            "name": "Clearlake"
        },
        {
            "code": "14890",
            "name": "Clinton"
        },
        {
            "code": "50638",
            "name": "Colbert"
        },
        {
            "code": "13415",
            "name": "Colfax"
        },
        {
            "code": "41241",
            "name": "College Place"
        },
        {
            "code": "20505",
            "name": "Colton"
        },
        {
            "code": "7889",
            "name": "Colville"
        },
        {
            "code": "60856",
            "name": "Conconully"
        },
        {
            "code": "38275",
            "name": "Concrete"
        },
        {
            "code": "38945",
            "name": "Connell"
        },
        {
            "code": "16329",
            "name": "Conway"
        },
        {
            "code": "60822",
            "name": "Copalis Beach"
        },
        {
            "code": "60823",
            "name": "Copalis Crossing"
        },
        {
            "code": "20498",
            "name": "Cosmopolis"
        },
        {
            "code": "45501",
            "name": "Cougar"
        },
        {
            "code": "35745",
            "name": "Coulee City"
        },
        {
            "code": "38979",
            "name": "Coulee Dam"
        },
        {
            "code": "876",
            "name": "Coupeville"
        },
        {
            "code": "38980",
            "name": "Cowiche"
        },
        {
            "code": "38967",
            "name": "Creston"
        },
        {
            "code": "39208",
            "name": "Curlew"
        },
        {
            "code": "60824",
            "name": "Curtis"
        },
        {
            "code": "39209",
            "name": "Cusick"
        },
        {
            "code": "30745",
            "name": "Custer"
        },
        {
            "code": "39232",
            "name": "Dallesport"
        },
        {
            "code": "23783",
            "name": "Danville"
        },
        {
            "code": "5659",
            "name": "Darrington"
        },
        {
            "code": "19187",
            "name": "Davenport"
        },
        {
            "code": "19189",
            "name": "Dayton"
        },
        {
            "code": "50639",
            "name": "Deer Harbor"
        },
        {
            "code": "38978",
            "name": "Deer Park"
        },
        {
            "code": "34643",
            "name": "Deming"
        },
        {
            "code": "20492",
            "name": "Dixie"
        },
        {
            "code": "60825",
            "name": "Doty"
        },
        {
            "code": "60857",
            "name": "Dryden"
        },
        {
            "code": "5657",
            "name": "Dupont"
        },
        {
            "code": "5459",
            "name": "Duvall"
        },
        {
            "code": "50640",
            "name": "East Olympia"
        },
        {
            "code": "30746",
            "name": "East Wenatchee"
        },
        {
            "code": "39210",
            "name": "Easton"
        },
        {
            "code": "38278",
            "name": "Eastsound"
        },
        {
            "code": "17661",
            "name": "Eatonville"
        },
        {
            "code": "5451",
            "name": "Edmonds"
        },
        {
            "code": "60879",
            "name": "Edwall"
        },
        {
            "code": "60810",
            "name": "Elbe"
        },
        {
            "code": "60891",
            "name": "Electric City"
        },
        {
            "code": "60880",
            "name": "Elk"
        },
        {
            "code": "6350",
            "name": "Ellensburg"
        },
        {
            "code": "15149",
            "name": "Elma"
        },
        {
            "code": "60892",
            "name": "Elmer City"
        },
        {
            "code": "49209",
            "name": "Eltopia"
        },
        {
            "code": "20493",
            "name": "Endicott"
        },
        {
            "code": "43682",
            "name": "Entiat"
        },
        {
            "code": "2134",
            "name": "Enumclaw"
        },
        {
            "code": "17136",
            "name": "Ephrata"
        },
        {
            "code": "50641",
            "name": "Ethel"
        },
        {
            "code": "60893",
            "name": "Evans"
        },
        {
            "code": "237",
            "name": "Everett"
        },
        {
            "code": "34644",
            "name": "Everson"
        },
        {
            "code": "21049",
            "name": "Fairchild Air Force Base"
        },
        {
            "code": "20186",
            "name": "Fairfield"
        },
        {
            "code": "13365",
            "name": "Fall City"
        },
        {
            "code": "60890",
            "name": "Farmington"
        },
        {
            "code": "1589",
            "name": "Federal Way"
        },
        {
            "code": "274",
            "name": "Ferndale"
        },
        {
            "code": "50642",
            "name": "Ford"
        },
        {
            "code": "34645",
            "name": "Forks"
        },
        {
            "code": "60881",
            "name": "Four Lakes"
        },
        {
            "code": "45505",
            "name": "Fox Island"
        },
        {
            "code": "20724",
            "name": "Freeland"
        },
        {
            "code": "9185",
            "name": "Friday Harbor"
        },
        {
            "code": "60895",
            "name": "Fruitland"
        },
        {
            "code": "60826",
            "name": "Galvin"
        },
        {
            "code": "39211",
            "name": "Garfield"
        },
        {
            "code": "23784",
            "name": "George"
        },
        {
            "code": "50643",
            "name": "Gifford"
        },
        {
            "code": "5450",
            "name": "Gig Harbor"
        },
        {
            "code": "51208",
            "name": "Glenoma"
        },
        {
            "code": "60844",
            "name": "Glenwood"
        },
        {
            "code": "9055",
            "name": "Gold Bar"
        },
        {
            "code": "13419",
            "name": "Goldendale"
        },
        {
            "code": "18781",
            "name": "Graham"
        },
        {
            "code": "30747",
            "name": "Grand Coulee"
        },
        {
            "code": "15454",
            "name": "Grandview"
        },
        {
            "code": "39200",
            "name": "Granger"
        },
        {
            "code": "20573",
            "name": "Granite Falls"
        },
        {
            "code": "60827",
            "name": "Grapeview"
        },
        {
            "code": "60828",
            "name": "Grayland"
        },
        {
            "code": "60845",
            "name": "Grays River"
        },
        {
            "code": "19687",
            "name": "Greenacres"
        },
        {
            "code": "37974",
            "name": "Greenbank"
        },
        {
            "code": "39044",
            "name": "Hamilton"
        },
        {
            "code": "46388",
            "name": "Hansville"
        },
        {
            "code": "60873",
            "name": "Harrah"
        },
        {
            "code": "20488",
            "name": "Harrington"
        },
        {
            "code": "39045",
            "name": "Hartline"
        },
        {
            "code": "30748",
            "name": "Hay"
        },
        {
            "code": "50644",
            "name": "Heisson"
        },
        {
            "code": "60798",
            "name": "Hobart"
        },
        {
            "code": "19857",
            "name": "Hoodsport"
        },
        {
            "code": "60909",
            "name": "Hooper"
        },
        {
            "code": "15151",
            "name": "Hoquiam"
        },
        {
            "code": "60829",
            "name": "Humptulips"
        },
        {
            "code": "20508",
            "name": "Hunters"
        },
        {
            "code": "60846",
            "name": "Husum"
        },
        {
            "code": "38277",
            "name": "Ilwaco"
        },
        {
            "code": "38981",
            "name": "Inchelium"
        },
        {
            "code": "39213",
            "name": "Index"
        },
        {
            "code": "60811",
            "name": "Indianola"
        },
        {
            "code": "60896",
            "name": "Ione"
        },
        {
            "code": "5031",
            "name": "Issaquah"
        },
        {
            "code": "38977",
            "name": "Joyce"
        },
        {
            "code": "39214",
            "name": "Kahlotus"
        },
        {
            "code": "10658",
            "name": "Kalama"
        },
        {
            "code": "60812",
            "name": "Kapowsin"
        },
        {
            "code": "20503",
            "name": "Keller"
        },
        {
            "code": "13418",
            "name": "Kelso"
        },
        {
            "code": "5454",
            "name": "Kenmore"
        },
        {
            "code": "484",
            "name": "Kennewick"
        },
        {
            "code": "4377",
            "name": "Kent"
        },
        {
            "code": "19796",
            "name": "Kettle Falls"
        },
        {
            "code": "4038",
            "name": "Keyport"
        },
        {
            "code": "5448",
            "name": "Kingston"
        },
        {
            "code": "1830",
            "name": "Kirkland"
        },
        {
            "code": "39215",
            "name": "Kittitas"
        },
        {
            "code": "60847",
            "name": "Klickitat"
        },
        {
            "code": "36187",
            "name": "La Center"
        },
        {
            "code": "14757",
            "name": "La Conner"
        },
        {
            "code": "60813",
            "name": "La Grande"
        },
        {
            "code": "19798",
            "name": "La Push"
        },
        {
            "code": "2736",
            "name": "Lacey"
        },
        {
            "code": "30749",
            "name": "Lacrosse"
        },
        {
            "code": "17530",
            "name": "Lake Stevens"
        },
        {
            "code": "45216",
            "name": "Lakebay"
        },
        {
            "code": "9888",
            "name": "Lakewood"
        },
        {
            "code": "60897",
            "name": "Lamona"
        },
        {
            "code": "20485",
            "name": "Lamont"
        },
        {
            "code": "3025",
            "name": "Langley"
        },
        {
            "code": "60882",
            "name": "Latah"
        },
        {
            "code": "60898",
            "name": "Laurier"
        },
        {
            "code": "5573",
            "name": "Leavenworth"
        },
        {
            "code": "60830",
            "name": "Lebam"
        },
        {
            "code": "3607",
            "name": "Liberty Lake"
        },
        {
            "code": "60831",
            "name": "Lilliwaup"
        },
        {
            "code": "60899",
            "name": "Lincoln"
        },
        {
            "code": "20511",
            "name": "Lind"
        },
        {
            "code": "60832",
            "name": "Littlerock"
        },
        {
            "code": "19188",
            "name": "Long Beach"
        },
        {
            "code": "50944",
            "name": "Longbranch"
        },
        {
            "code": "60820",
            "name": "Longmire"
        },
        {
            "code": "636",
            "name": "Longview"
        },
        {
            "code": "60858",
            "name": "Loomis"
        },
        {
            "code": "51043",
            "name": "Loon Lake"
        },
        {
            "code": "39204",
            "name": "Lopez Island"
        },
        {
            "code": "34646",
            "name": "Lummi Island"
        },
        {
            "code": "38982",
            "name": "Lyle"
        },
        {
            "code": "60802",
            "name": "Lyman"
        },
        {
            "code": "2871",
            "name": "Lynden"
        },
        {
            "code": "2979",
            "name": "Lynnwood"
        },
        {
            "code": "39216",
            "name": "Mabton"
        },
        {
            "code": "60859",
            "name": "Malaga"
        },
        {
            "code": "60900",
            "name": "Malden"
        },
        {
            "code": "60901",
            "name": "Malo"
        },
        {
            "code": "60833",
            "name": "Malone"
        },
        {
            "code": "60860",
            "name": "Malott"
        },
        {
            "code": "23785",
            "name": "Manchester"
        },
        {
            "code": "39217",
            "name": "Mansfield"
        },
        {
            "code": "15541",
            "name": "Manson"
        },
        {
            "code": "30750",
            "name": "Maple Falls"
        },
        {
            "code": "5429",
            "name": "Maple Valley"
        },
        {
            "code": "60803",
            "name": "Marblemount"
        },
        {
            "code": "60902",
            "name": "Marcus"
        },
        {
            "code": "60861",
            "name": "Marlin"
        },
        {
            "code": "60883",
            "name": "Marshall"
        },
        {
            "code": "2060",
            "name": "Marysville"
        },
        {
            "code": "60834",
            "name": "Matlock"
        },
        {
            "code": "38961",
            "name": "Mattawa"
        },
        {
            "code": "60862",
            "name": "Mazama"
        },
        {
            "code": "50645",
            "name": "Mcchord Afb"
        },
        {
            "code": "38983",
            "name": "Mccleary"
        },
        {
            "code": "9885",
            "name": "Mckenna"
        },
        {
            "code": "6005",
            "name": "Mead"
        },
        {
            "code": "16943",
            "name": "Medical Lake"
        },
        {
            "code": "17647",
            "name": "Medina"
        },
        {
            "code": "38965",
            "name": "Menlo"
        },
        {
            "code": "5455",
            "name": "Mercer Island"
        },
        {
            "code": "50646",
            "name": "Mesa"
        },
        {
            "code": "60903",
            "name": "Metaline"
        },
        {
            "code": "60904",
            "name": "Metaline Falls"
        },
        {
            "code": "60863",
            "name": "Methow"
        },
        {
            "code": "60884",
            "name": "Mica"
        },
        {
            "code": "49265",
            "name": "Mill Creek"
        },
        {
            "code": "10007",
            "name": "Milton"
        },
        {
            "code": "60814",
            "name": "Mineral"
        },
        {
            "code": "60835",
            "name": "Moclips"
        },
        {
            "code": "244771",
            "name": "Mohler"
        },
        {
            "code": "60864",
            "name": "Monitor"
        },
        {
            "code": "15153",
            "name": "Monroe"
        },
        {
            "code": "33725",
            "name": "Montesano"
        },
        {
            "code": "9274",
            "name": "Morton"
        },
        {
            "code": "15556",
            "name": "Moses Lake"
        },
        {
            "code": "38974",
            "name": "Mossyrock"
        },
        {
            "code": "5658",
            "name": "Mount Vernon"
        },
        {
            "code": "5150",
            "name": "Mountlake Terrace"
        },
        {
            "code": "13939",
            "name": "Moxee"
        },
        {
            "code": "5453",
            "name": "Mukilteo"
        },
        {
            "code": "39219",
            "name": "Naches"
        },
        {
            "code": "60848",
            "name": "Nahcotta"
        },
        {
            "code": "38968",
            "name": "Napavine"
        },
        {
            "code": "38973",
            "name": "Naselle"
        },
        {
            "code": "47069",
            "name": "Neah Bay"
        },
        {
            "code": "60836",
            "name": "Neilton"
        },
        {
            "code": "12098",
            "name": "Nespelem"
        },
        {
            "code": "16027",
            "name": "Newman Lake"
        },
        {
            "code": "9179",
            "name": "Newport"
        },
        {
            "code": "19686",
            "name": "Nine Mile Falls"
        },
        {
            "code": "34648",
            "name": "Nooksack"
        },
        {
            "code": "60815",
            "name": "Nordland"
        },
        {
            "code": "9882",
            "name": "North Bend"
        },
        {
            "code": "45376",
            "name": "North Bonneville"
        },
        {
            "code": "30751",
            "name": "North Lakewood"
        },
        {
            "code": "45561",
            "name": "Northport"
        },
        {
            "code": "6347",
            "name": "Oak Harbor"
        },
        {
            "code": "39201",
            "name": "Oakesdale"
        },
        {
            "code": "38971",
            "name": "Oakville"
        },
        {
            "code": "30752",
            "name": "Ocean Park"
        },
        {
            "code": "20486",
            "name": "Ocean Shores"
        },
        {
            "code": "30753",
            "name": "Odessa"
        },
        {
            "code": "19685",
            "name": "Okanogan"
        },
        {
            "code": "18936",
            "name": "Olalla"
        },
        {
            "code": "50647",
            "name": "Olga"
        },
        {
            "code": "571",
            "name": "Olympia"
        },
        {
            "code": "3215",
            "name": "Omak"
        },
        {
            "code": "11728",
            "name": "Onalaska"
        },
        {
            "code": "50941",
            "name": "Orcas"
        },
        {
            "code": "20482",
            "name": "Orient"
        },
        {
            "code": "38970",
            "name": "Orondo"
        },
        {
            "code": "33453",
            "name": "Oroville"
        },
        {
            "code": "22636",
            "name": "Orting"
        },
        {
            "code": "38962",
            "name": "Othello"
        },
        {
            "code": "13931",
            "name": "Otis Orchards"
        },
        {
            "code": "60874",
            "name": "Outlook"
        },
        {
            "code": "60849",
            "name": "Oysterville"
        },
        {
            "code": "7248",
            "name": "Pacific"
        },
        {
            "code": "50648",
            "name": "Pacific Beach"
        },
        {
            "code": "60816",
            "name": "Packwood"
        },
        {
            "code": "20502",
            "name": "Palisades"
        },
        {
            "code": "20510",
            "name": "Palouse"
        },
        {
            "code": "15086",
            "name": "Parker"
        },
        {
            "code": "11882",
            "name": "Pasco"
        },
        {
            "code": "60865",
            "name": "Pateros"
        },
        {
            "code": "20483",
            "name": "Paterson"
        },
        {
            "code": "38969",
            "name": "Pe Ell"
        },
        {
            "code": "60866",
            "name": "Peshastin"
        },
        {
            "code": "60910",
            "name": "Plymouth"
        },
        {
            "code": "18053",
            "name": "Point Roberts"
        },
        {
            "code": "19186",
            "name": "Pomeroy"
        },
        {
            "code": "2133",
            "name": "Port Angeles"
        },
        {
            "code": "46848",
            "name": "Port Gamble"
        },
        {
            "code": "30754",
            "name": "Port Hadlock"
        },
        {
            "code": "34649",
            "name": "Port Ludlow"
        },
        {
            "code": "9166",
            "name": "Port Orchard"
        },
        {
            "code": "13192",
            "name": "Port Townsend"
        },
        {
            "code": "6017",
            "name": "Poulsbo"
        },
        {
            "code": "23786",
            "name": "Prescott"
        },
        {
            "code": "8099",
            "name": "Preston"
        },
        {
            "code": "6354",
            "name": "Prosser"
        },
        {
            "code": "1048",
            "name": "Pullman"
        },
        {
            "code": "3350",
            "name": "Puyallup"
        },
        {
            "code": "17663",
            "name": "Quilcene"
        },
        {
            "code": "60837",
            "name": "Quinault"
        },
        {
            "code": "23787",
            "name": "Quincy"
        },
        {
            "code": "5447",
            "name": "Rainier"
        },
        {
            "code": "39198",
            "name": "Randle"
        },
        {
            "code": "60799",
            "name": "Ravensdale"
        },
        {
            "code": "15150",
            "name": "Raymond"
        },
        {
            "code": "60885",
            "name": "Reardan"
        },
        {
            "code": "367",
            "name": "Redmond"
        },
        {
            "code": "60800",
            "name": "Redondo"
        },
        {
            "code": "3638",
            "name": "Renton"
        },
        {
            "code": "30026",
            "name": "Republic"
        },
        {
            "code": "60817",
            "name": "Retsil"
        },
        {
            "code": "22260",
            "name": "Rice"
        },
        {
            "code": "3625",
            "name": "Richland"
        },
        {
            "code": "8018",
            "name": "Ridgefield"
        },
        {
            "code": "9154",
            "name": "Ritzville"
        },
        {
            "code": "39065",
            "name": "Riverside"
        },
        {
            "code": "23788",
            "name": "Rochester"
        },
        {
            "code": "44665",
            "name": "Rock Island"
        },
        {
            "code": "20489",
            "name": "Rockford"
        },
        {
            "code": "60804",
            "name": "Rockport"
        },
        {
            "code": "60801",
            "name": "Rollingbay"
        },
        {
            "code": "60875",
            "name": "Ronald"
        },
        {
            "code": "20495",
            "name": "Roosevelt"
        },
        {
            "code": "39220",
            "name": "Rosalia"
        },
        {
            "code": "47181",
            "name": "Rosburg"
        },
        {
            "code": "8014",
            "name": "Roslyn"
        },
        {
            "code": "23789",
            "name": "Roy"
        },
        {
            "code": "38964",
            "name": "Royal City"
        },
        {
            "code": "60838",
            "name": "Ryderwood"
        },
        {
            "code": "33732",
            "name": "Salkum"
        },
        {
            "code": "17648",
            "name": "Sammamish"
        },
        {
            "code": "20499",
            "name": "Satsop"
        },
        {
            "code": "48973",
            "name": "Seabeck"
        },
        {
            "code": "10008",
            "name": "Seahurst"
        },
        {
            "code": "114",
            "name": "Seattle"
        },
        {
            "code": "60850",
            "name": "Seaview"
        },
        {
            "code": "23790",
            "name": "Sedro Woolley"
        },
        {
            "code": "38975",
            "name": "Sekiu"
        },
        {
            "code": "8991",
            "name": "Selah"
        },
        {
            "code": "7949",
            "name": "Sequim"
        },
        {
            "code": "20501",
            "name": "Shaw Island"
        },
        {
            "code": "13416",
            "name": "Shelton"
        },
        {
            "code": "60805",
            "name": "Silvana"
        },
        {
            "code": "46069",
            "name": "Silver Creek"
        },
        {
            "code": "495",
            "name": "Silverdale"
        },
        {
            "code": "35152",
            "name": "Silverlake"
        },
        {
            "code": "60851",
            "name": "Skamokawa"
        },
        {
            "code": "48969",
            "name": "Skykomish"
        },
        {
            "code": "10044",
            "name": "Snohomish"
        },
        {
            "code": "17532",
            "name": "Snoqualmie"
        },
        {
            "code": "35155",
            "name": "Snoqualmie Pass"
        },
        {
            "code": "60867",
            "name": "Soap Lake"
        },
        {
            "code": "19184",
            "name": "South Bend"
        },
        {
            "code": "60876",
            "name": "South Cle Elum"
        },
        {
            "code": "60818",
            "name": "South Colby"
        },
        {
            "code": "50649",
            "name": "South Prairie"
        },
        {
            "code": "15306",
            "name": "Southworth"
        },
        {
            "code": "9886",
            "name": "Spanaway"
        },
        {
            "code": "30755",
            "name": "Spangle"
        },
        {
            "code": "129",
            "name": "Spokane"
        },
        {
            "code": "38966",
            "name": "Sprague"
        },
        {
            "code": "20512",
            "name": "Springdale"
        },
        {
            "code": "20504",
            "name": "St John"
        },
        {
            "code": "5458",
            "name": "Stanwood"
        },
        {
            "code": "20490",
            "name": "Starbuck"
        },
        {
            "code": "60806",
            "name": "Startup"
        },
        {
            "code": "60868",
            "name": "Stehekin"
        },
        {
            "code": "19084",
            "name": "Steilacoom"
        },
        {
            "code": "20497",
            "name": "Steptoe"
        },
        {
            "code": "15455",
            "name": "Stevenson"
        },
        {
            "code": "60869",
            "name": "Stratford"
        },
        {
            "code": "15965",
            "name": "Sultan"
        },
        {
            "code": "30756",
            "name": "Sumas"
        },
        {
            "code": "2913",
            "name": "Sumner"
        },
        {
            "code": "9227",
            "name": "Sunnyside"
        },
        {
            "code": "50650",
            "name": "Suquamish"
        },
        {
            "code": "255",
            "name": "Tacoma"
        },
        {
            "code": "19185",
            "name": "Taholah"
        },
        {
            "code": "60839",
            "name": "Tahuya"
        },
        {
            "code": "39205",
            "name": "Tekoa"
        },
        {
            "code": "38947",
            "name": "Tenino"
        },
        {
            "code": "60905",
            "name": "Thornton"
        },
        {
            "code": "60877",
            "name": "Thorp"
        },
        {
            "code": "45843",
            "name": "Tieton"
        },
        {
            "code": "48036",
            "name": "Tokeland"
        },
        {
            "code": "14948",
            "name": "Toledo"
        },
        {
            "code": "33736",
            "name": "Tonasket"
        },
        {
            "code": "13928",
            "name": "Toppenish"
        },
        {
            "code": "20487",
            "name": "Touchet"
        },
        {
            "code": "38575",
            "name": "Toutle"
        },
        {
            "code": "17664",
            "name": "Tracyton"
        },
        {
            "code": "38574",
            "name": "Trout Lake"
        },
        {
            "code": "60886",
            "name": "Tumtum"
        },
        {
            "code": "6307",
            "name": "Tumwater"
        },
        {
            "code": "30757",
            "name": "Twisp"
        },
        {
            "code": "45377",
            "name": "Underwood"
        },
        {
            "code": "17959",
            "name": "Union"
        },
        {
            "code": "60906",
            "name": "Uniontown"
        },
        {
            "code": "2827",
            "name": "University Place"
        },
        {
            "code": "60907",
            "name": "Usk"
        },
        {
            "code": "60840",
            "name": "Vader"
        },
        {
            "code": "20494",
            "name": "Valley"
        },
        {
            "code": "17653",
            "name": "Valleyford"
        },
        {
            "code": "1473",
            "name": "Vancouver"
        },
        {
            "code": "60878",
            "name": "Vantage"
        },
        {
            "code": "15831",
            "name": "Vashon"
        },
        {
            "code": "60819",
            "name": "Vaughn"
        },
        {
            "code": "9913",
            "name": "Veradale"
        },
        {
            "code": "60853",
            "name": "Wahkiacus"
        },
        {
            "code": "39202",
            "name": "Waitsburg"
        },
        {
            "code": "60807",
            "name": "Waldron"
        },
        {
            "code": "6006",
            "name": "Walla Walla"
        },
        {
            "code": "50651",
            "name": "Wallula"
        },
        {
            "code": "15085",
            "name": "Wapato"
        },
        {
            "code": "17963",
            "name": "Warden"
        },
        {
            "code": "8772",
            "name": "Washougal"
        },
        {
            "code": "39203",
            "name": "Washtucna"
        },
        {
            "code": "38545",
            "name": "Waterville"
        },
        {
            "code": "60870",
            "name": "Wauconda"
        },
        {
            "code": "50652",
            "name": "Wauna"
        },
        {
            "code": "60887",
            "name": "Waverly"
        },
        {
            "code": "20035",
            "name": "Wellpinit"
        },
        {
            "code": "594",
            "name": "Wenatchee"
        },
        {
            "code": "44998",
            "name": "West Richland"
        },
        {
            "code": "23791",
            "name": "Westport"
        },
        {
            "code": "45983",
            "name": "White Salmon"
        },
        {
            "code": "39218",
            "name": "White Swan"
        },
        {
            "code": "39199",
            "name": "Wilbur"
        },
        {
            "code": "34650",
            "name": "Wilkeson"
        },
        {
            "code": "60871",
            "name": "Wilson Creek"
        },
        {
            "code": "20496",
            "name": "Winlock"
        },
        {
            "code": "9911",
            "name": "Winthrop"
        },
        {
            "code": "20491",
            "name": "Wishram"
        },
        {
            "code": "5452",
            "name": "Woodinville"
        },
        {
            "code": "6012",
            "name": "Woodland"
        },
        {
            "code": "44853",
            "name": "Yacolt"
        },
        {
            "code": "287",
            "name": "Yakima"
        },
        {
            "code": "17300",
            "name": "Yelm"
        },
        {
            "code": "18562",
            "name": "Zillah"
        }
    ]
}
```



## Region Retrieval

API endpoints used to retrieve defined geographic regions.


### List regions

Returns the ID, name, and geographic location of all defined regions.

<br>

#### Response Object
|Field		|Parent	|Type		|Description	|
|---		|---	|---		|---			|
|requestID	|		|string		| Unique log ID for this request.|
|timestamp	|		|string		| Date and time when the request was executed.|
|count		|		|integer	| Total count of defined regions listed in the response.|
|`regions`	|		|object array| List of region definitions.|
|id			|`regions`|string	|ID of the region.		|
|name		|`regions`		|string		| Name of the region.|
|type		|`regions`		|string		| Region type. Supported values are [circle, locations].|
|`circle`	|`regions`	|object		| Region definition.|
|latitude	|`circle`	|real	|   34.0522, for example.|
|longitude	|`circle`	|real	| -118.2437, for example.|
|radius		|`circle`	|real	| 20.0, for example.|
|unit		|`circle`	|string	| Radius measurement unit. Either "KM" for kilometers or "MI" for miles.|
|`locations`|`regions`	|object array	| List of region definitions.|
|countryCode	|`locations`	|string	| Code for geographic nation; "usa", for example.|
|countryName	|`locations`	|string	| Name for geographic nation; "United States", for example.|
|regionCode		|`locations`	|string	| Code for geographic subsection; "wa", for example.|
|regionName		|`locations`	|string	| Name for geographic subsection; "Washington", for example.|
|cityCode		|`locations`	|string	| Code for a city designation; "114", for example.|
|cityName		|`locations`	|string	| Name for a city designation; "Seattle", for example.|
|postalCode		|`locations`	|string	| A valid code for the country/region; "98101"  for example.|

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OGMServer}}/ogm/v1/regions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get OGM regions | Code: 200



```js
{
    "requestID": "475f0f3b-97cf-4059-9215-6af4b902018d",
    "timestamp": "2018-08-01T21:01:55.496763496Z",
    "count": 4,
    "regions": [
        {
            "id": "c239e1fa-569e-4bb6-b77e-05b7c3254bcd",
            "name": "OGM Circle Region No ID",
            "type": "circle",
            "circle": {
                "latitude": 34.0522,
                "longitude": -118.2437,
                "radius": 20,
                "unit": "KM"
            }
        },
        {
            "id": "2b6de728-4757-4456-911c-65f762ccba65",
            "name": "OGM Region No ID",
            "type": "locations",
            "locations": [
                {
                    "countryCode": "usa",
                    "countryName": "United States",
                    "regionCode": "wa",
                    "regionName": "Washington",
                    "cityCode": "114",
                    "cityName": "Seattle"
                }
            ]
        },
        {
            "id": "3703-VALIDATE1",
            "name": "3703-VALIDATE1",
            "type": "circle",
            "circle": {
                "latitude": 34.0522,
                "longitude": -118.2438,
                "radius": 20,
                "unit": "MI"
            }
        },
        {
            "id": "7ca0fccc-125f-41e4-93c7-90fc1d4d81e5",
            "name": "Shaun Test",
            "type": "circle",
            "circle": {
                "latitude": 34.0522,
                "longitude": -118.2437,
                "radius": 20,
                "unit": "MI"
            }
        }
    ]
}
```



### List matching regions

Returns any regions matching the provided query text. The text may be a prefix to a field value or a term within a field value. The search is case-insensitive.

Regions may contain multiple locations. In addition to searching the region name, this endpoint searches the following fields of region locations: countryName, regionName (the state/province), cityName and postalCode.

<br/>

#### Response Object
|Field		|Parent	|Type	|Description	|
|---		|---	|---	|---			|
|requestID	|	|string	| The unique log ID for this request.|
|timestamp	|	|string	| The date and time when executed.|
| count     |	| number  | Number of items listed in this response; min = 0, max = 100.
|`regions`	|	|object	|	|
| id		|`regions`|string	| The region ID.|
| name		|`regions`|string	| The region name.|

<br/>



#### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested resources|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OGMServer}}/ogm/v1/regions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| query | Sea | _Required_. Search by query string. |



***Responses:***


Status: Search OGM regions | Code: 200



```js
{
    "requestID": "4bf6976d-9a37-473a-a511-cd318b28fe7a",
    "timestamp": "2018-08-01T21:02:14.528738299Z",
    "count": 1,
    "regions": [
        {
            "id": "2b6de728-4757-4456-911c-65f762ccba65",
            "name": "OGM Region No ID",
            "type": "locations",
            "locations": [
                {
                    "countryCode": "usa",
                    "countryName": "United States",
                    "regionCode": "wa",
                    "regionName": "Washington",
                    "cityCode": "114",
                    "cityName": "Seattle"
                }
            ]
        }
    ]
}
```



### Get region by ID

Returns the specified region by ID.

<br/>

#### Path Parameters

|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|regionID	|string	|required	|The ID of the region to be retrieved.|

<br/>

#### Response Object
|Field		|Parent	|Type	|Description	|
|---		|---	|---	|---			|
|requestID	|	|string	| The unique log ID for this request.|
|timestamp	|	|string	| The date and time when executed.|
|count		|	|integer| The count for each response beginning with 1.|
|`regions`	|	|object	|	|
| id		|`regions`|string	| The region ID.|
| name		|`regions`|string	| The region name.|
| `locations`	|`regions`	|object array | one or more locations|
| countryCode	|`locations`	|string	|usa|
| countryName	|`locations`	|string	|United States|
| regionCode	|`locations`	|string	|wa|
| regionName	|`locations`	|string	|state, province, or region|
| cityCode		|`locations`	|string	|114|
| cityName		|`locations`	|string	|Seattle|
| postalCode	|`locations`	|string	|postal or ZIP code|

<br/>

***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OGMServer}}/ogm/v1/regions/{{regionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get OGM Circle Region | Code: 200



```js
{"requestID":"b9520ab9-5f41-48f5-b42a-6ee570b6a41d","timestamp":"2018-08-01T21:03:00.322326694Z","count":1,"regions":[{"id":"c239e1fa-569e-4bb6-b77e-05b7c3254bcd","name":"OGM Circle Region No ID","type":"circle","circle":{"latitude":34.0522,"longitude":-118.2437,"radius":20,"unit":"KM"}}]}
```



Status: Get OGM locations region | Code: 200



```js
{
    "requestID":"57306b13-600b-44f4-b360-c77cc9ad8d03","timestamp":"2018-08-01T21:03:42.97898892Z",
    "count":1,
    "regions":
    [
        {"id":"2b6de728-4757-4456-911c-65f762ccba65",
        "name":"OGM Region No ID",
        "type":"locations","locations":
        [
            {"countryCode":"usa",
            "countryName":"United States",
            "regionCode":"wa",
            "regionName":"Washington",
            "cityCode":"114",
            "cityName":"Seattle"}
        ]
        }
    ]
}
```


---

[Back to top](api-geography)
