---
id: api-experience
title: Experience 
sidebar_label: Experience 
---

The *experience* endpoints allow applications to store and manage information that is specific to each subscriber's video content interactions. 
These endpoints handle the subscriber's watchlist, content progress markers, and system limitations set by the tenant's streaming policies.

--------

## Managing Streaming Policies


### Get tenant streaming policies

Returns the streaming policies for the specified tenant.  A value of 0 indicates that a policy is not being enforced.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|tenant	|string |required	|Name of the tenant whose streaming policies will be retrieved.|

<br/>

#### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired|
|**403**|1003|*Forbidden*: Cannot read the requested resource|
|**404**|1040|*Not found*: Requested resource ID missing, deleted, or incorrect|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OXMServer}}/oxm/v1/streampolicy/{{tenant}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get tenant streaming policies | Code: 200



```js
{
    "maxPerUser": 5,
    "maxPerAsset": 2
}
```



### Set tenant streaming policies

Sets the streaming policies for the specified tenant.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|tenant	|string |required	|Name of the tenant whose streaming policies will be set.|

<br/>

#### Body Parameters
|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
| maxPerUser	| integer |required	|Number of concurrent streams allowed for a single user.|
| maxPerAsset	| integer |required	|Number of concurrent streams allowed for a specific asset.|
| maxDevices	| integer |required	|Number of concurrent devices allowed for a single user.|

<br>

**Important:** *maxPerAsset* must be less than or equal to *maxPerUser*.

A value of 0 will result in the policy not being enforced.

<br>

#### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**400**|1103, 1104, 1105|*Bad request*: Request body malformed.|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**403**|1004|*Forbidden*: Cannot update the requested resource.|
|**404**|1040|*Not found*: Requested resource ID missing, deleted, or incorrect.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OXMServer}}/oxm/v1/streampolicy/{{tenant}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "maxPerUser": 5,
    "maxPerAsset": 2,
    "maxDevices": 0
}
```



***Responses:***

Status: Set tenant streaming policies | Code: 200




### List stream progress history

Lists all "in progress" streams for a user. Any previously deleted streams are not returned.

<br/>

#### Response Object

|Field	|Type	|Description	|
|---	|---	|---			|
| tenantID	| string | Name of the tenant.|
| userID	| string | Unique ID for the user.|
| assetID	| string | Unique ID for each asset. |
| progress	| integer| Number of seconds viewed for each asset.|
| timestamp	| string | Date and time when this request was executed.|


<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OXMServer}}/oxm/v1/streams/history
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get Stream Progress History | Code: 200



```js
[
    {
        "tenantId": "istreamplanet",
        "userId": "2468517b-3ec5-4d8a-a6b9-e6b1653df163",
        "assetId": "af8280e5-d52a-4dfb-aecc-09945d06e969",
        "progress": 666,
        "timestamp": "2019-04-25T19:06:21.577870309Z"
    }
]
```



### Delete stream progress

Deletes the user's stream progress value for the specified asset. 

Call this endpoint after the user has successfully finished viewing an asset to ensure that the stream will start from the beginning when viewed again in the future.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|assetID| string |required	|ID of the video asset to be reset to position zero.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target stream marker.|
|404		|1040	|*Not Found*: Target stream marker not found.|

<br/>



***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OXMServer}}/oxm/v1/streams/{{assetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Delete Stream Progress | Code: 204



### Retrieve stream progress

Returns the most recent progress value for the specified asset. 

Call this endpoint before playing a previously viewed stream to ensure that it begins at the user's last viewed position.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|assetID|string |required	|ID of the target asset to be played starting at the last viewed position.|

<br/>



***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OXMServer}}/oxm/v1/streams/{{assetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get stream progress | Code: 200



```js
{
    "tenantId": "istreamplanet",
    "userId": "2468517b-3ec5-4d8a-a6b9-e6b1653df163",
    "assetId": "af8280e5-d52a-4dfb-aecc-09945d06e969",
    "progress": 123,
    "timestamp": 1526327019067
}
```



### Retrieve stream counts

Returns the number of concurrent streams in use by the Subscriber for the listed asset. 

Optionally returns the number of streams in use on each device.

<br/>

#### Response Object

|Field	|Type |Description	|
|---	|---  |---			|
| _assetID_ **:** _streamCounts_ | map (_string : number_) | _<&nbsp;streaming-asset-ID&nbsp;> **:** <&nbsp;number-of-streams&nbsp;>_ <br><br>Or, if **include=device** is used, <br><br>_<&nbsp;streaming-asset-ID&nbsp;>_ **:** {_deviceID_ **:** _number_, _deviceID_ **:** _number_, ...}|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OXMServer}}/oxm/v1/streams/counts
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| include | device | Optional.  Currently, the only valid value is "**device**". Returns detailed device information. |



***Responses:***


Status: Get stream counts | Code: 200



```js
{"af8280e5-d52a-4dfb-aecc-09945d06e969":1}
```



### Stream stop

Specifies that the stream is no longer being viewed and returns the final progress value. 

Stream concurrency is removed from Redis. When the progress value is provided, the stream progress is also recorded.

<br/>

#### Path Parameters

|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|assetID|string |required	|ID of the stream that the user was watching.|

<br/>



***Endpoint:***

```bash
Method: PUT
Type: FORMDATA
URL: {{OXMServer}}/oxm/v1/streams/{{assetID}}/stopped
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| device | <string> | Optional. Device name or ID. If not provided, the device IP address is used. When provided, it must match the **deviceID** specified in the body of the [Request an entitlement token](https://docs.dtc.istreamplanet.net/#70bc1097-ed46-4efe-8892-118145f9662d) call. |
| progress | <integer> | Optional. Progress  in seconds from the beginning of the stream. If not provided, no progress value will be stored in the database. |



***Responses:***


Status: Stream Stop | Code: 204



### Track stream concurrency and progress

Notifies the system that a user is watching a stream. 

This is the main endpoint used to track both stream concurrency (how many concurrent streams the user is viewing) and, optionally, the user's progress through the stream. The client application should call this endpoint at no more than two minute intervals during the entire time the stream is viewed, including times when the stream is paused.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|assetID|string |required	|ID of the stream that the user is watching.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: FORMDATA
URL: {{OXMServer}}/oxm/v1/streams/{{assetID}}/streaming
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| device | <string> | Optional. Device name or ID. If not provided, the device IP address is used. When provided, it must match the **deviceID** specified in the body of the [Request entitlement token](https://docs.dtc.istreamplanet.net/#70bc1097-ed46-4efe-8892-118145f9662d) call. |
| progress | <integer> | Optional. Progress value in seconds from the beginning of the stream. If not provided, no progress value will be stored in the database. |



***Responses:***

Status: Track stream concurrency and progress | Code: 204


## Managing Watchlists


### Remove an asset from the watchlist

Removes the specified asset ID from the subscriber's watchlist.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|assetID|string	|required	|ID of the asset to be removed from the subscriber's watchlist.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target stream marker.|
|404		|1040	|*Not Found*: Target stream marker not found.|



<br/>


***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OXMServer}}/oxm/v1/towatch/{{assetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Delete asset from "to watch" list | Code: 200



### Add an asset to the watchlist

Adds the specified the asset ID to the subscriber's watch list.

<br/>

#### Path Parameters

|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|assetID|string |required	|ID of the asset to be added from the user's watchlist.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: FORMDATA
URL: {{OXMServer}}/oxm/v1/towatch/{{assetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Add asset to "to watch" list | Code: 200



### Retrieve the watchlist

Returns the list of asset IDs in the subscriber's "to watch" list.

<br/>

#### Body Parameters
|Field	|Type	|Description	|
|---	|---	|---			|
| requestID	| string |Unique log ID for this request.|
| timestamp	| string |Date and time when this call was executed.|
| assetIDs	| string list |List of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list |List of requested asset IDs that have no metadata.|
| assets	| string |Descriptive metadata for the requested asset IDs. |
| `count`	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>

**Count Values**:
* _acquired_: &nbsp; number of asset IDs acquired from OCM v2; see the _assetIDs_ list.
* _notFound_: &nbsp; number of asset IDs for which there is no metadata; see the _assetIDsNotFound_ list.
* _returned_: &nbsp; number of asset metadata objects returned. (The value of _returned_ should be _acquired_ - _unwanted_.)
* _unwanted_: &nbsp; number of asset metadata objects returned from OCM v2 which were not requested. <br/>
(This value should always be zero; non-zero values would generate an error in OCM v2.)

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OXMServer}}/oxm/v1/towatch
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| full | true | *Optional boolean*.  If set to **true**, returns all metadata for the watchlist entries. This parameter only works for assets stored in the OCM v2 schema. Assets stored in OCM v1 return no metadata and display as "not found".
 |



***Responses:***


Status: Get "to watch" list with full parameter | Code: 200



```js
{
    "requestID": "1200ac02-4c21-4835-8edf-462dd335b302",
    "timestamp": "2018-05-23T17:55:39.590328174Z",
    "assetIDs": [
        "c56f185963ea17987c910834e0a575a6"
    ],
    "assetIDsNotFound": [
        "6h7xnvckinxxsl9lh5n2",
        "a68d40370913aa5c56515d52c3b0d42c",
        "f682beefab2e52912a3c492f716ee90d",
        "test1234"
    ],
    "assets": [
        {
            "id": "c56f185963ea17987c910834e0a575a6",
            "name": "Barrio Chino II",
            "shortName": "BarrioChin",
            "description": "El detective Jake Gittes, sin saberlo, se convierte en cómplice de un crimen de pasión premeditado.",
            "shortDescription": "Un detective investiga un crimen de pasión premeditado.",
            "resourceType": "movie",
            "releaseYear": 1990,
            "language": "es",
            "pictureID": "3a81d257ce1768dd7f4cc3c0a10c82f1",
            "pictures": {
                "16x9": "3a81d257ce1768dd7f4cc3c0a10c82f1",
                "2x3": "9bbb6bb34c0c99c9fb149584c2b22878",
                "3x4": "204f341541e8004f558580bf6230b379",
                "4x3": "a2080da7011719a696fbd71e23289de5"
            },
            "genres": [
                "Mystery"
            ],
            "genreIDs": [
                "d775f75f857ae6a6c2b33e487686da54"
            ]
        }
    ],
    "count": {
        "acquired": 1,
        "notFound": 4,
        "returned": 1,
        "unwanted": 0
    }
}
```



Status: Get "to watch" list | Code: 200



```js
{
    "requestID": "386c37d8-da8a-46b2-bca3-09009081e31b",
    "timestamp": "2018-05-14T19:39:05.228675074Z",
    "assetIDs": [
        "07832utleyahe1dpbubg"
    ],
    "count": {
        "returned": 1
    }
}
```



---
[Back to top](api-experience)
