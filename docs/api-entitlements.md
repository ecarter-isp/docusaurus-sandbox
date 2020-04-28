---
id: api-entitlements
title: Entitlements
sidebar_label: Entitlements
---

These endpoints allow applications to manage relationships between asset packages, 
subscriptions, billing plans, and their entitlement tokens. 
To access a video asset, an account must have an entitlement token which is specific to that asset.

--------

## Entitlements - v1


### Add a package

Defines a group of video assets as a package for sale to fans.

<br/>

#### Body Parameters

|Field			|Parent		|Type		|Required	|Description|
|---			|---		|---		|---		|---		|
|`package`		|			|object		|required	|Package definition (container). |
|id				|`package`	|string		|required	|Unique package identifier. |
|name			|`package`	|string		|required	|Package name. |
|description	|`package`	|string		|required	|Package description. |
|assetIDs		|`package`	|string list|required	|List of asset IDs associated with this package. |
|billingPlanIDs	|`package`	|string list|required	|List of billing plan IDs associated with this package. |
|regionWhitelist|`package`	|string list|optional	|List of region IDs for locations where this package can be viewed. |

<br/>



***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OEMServer}}/oem/v1/user/packages/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "package": {
    "id": "{{package1ID}}",
    "name": "{{packageName}}",
    "description": "{{packageDescription}}",
    "assetIDs": ["{{asset1ID}},{{asset2ID}}"],
    "billingPlanIDs": ["{{billingPlan1ID}}"],
    "regionWhitelist": ["{{region1ID}}"]
  }
}
```



### Add a free package


Defines a group of video assets as a **free** package made available to fans without purchase.

<br/>

#### Body Parameters

|Field			|Parent		|Type		|Required	|Description|
|---			|---		|---		|---		|---		|
|`package`		|			|object		|required	|Package definition (container). |
|id				|`package`	|string		|required	|Unique free package identifier. |
|name			|`package`	|string		|required	|Package name. |
|description	|`package`	|string		|required	|Package description. |
|assetIDs		|`package`	|string list|required	|List of asset IDs associated with this free package. |
|bypassEntitlementCheck	|`package`	|boolean|required	|Flag to bypass entitlement authorization check. Must be set to _true_. |

<br/>




***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OEMServer}}/oem/v1/user/packages/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "package": {
    "id": "{{freePackageID}}",
    "name": "{{packageName}}",
    "description": "{{packageDescription}}",
    "bypassEntitlementCheck": true,
    "assetIDs": ["{{freeAsset1ID}}", "{{freeAsset2ID}}"]
  }
}
```



### Update a package


Updates the specified package of video assets. This endpoint may be used to add a new asset to an existing package.
Any parameters not listed in the body remain unchanged.

<br/>

#### Path Parameters

|Label			|Type		|Required	|Description|
|---		|---		|---		|---		|
|package1ID	|string		|required	|ID of the package to be updated. |

<br/>

#### Body Parameters

|Field			|Parent		|Type		|Required	|Description|
|---			|---		|---		|---		|---		|
|`package`		|			|object		|required	|Package definition (container). |
|id				|`package`	|string		|required	|Unique package identifier. |
|name			|`package`	|string		|optional	|Package name. |
|description	|`package`	|string		|optional	|Package description. |
|assetIDs		|`package`	|string list|optional	|List of asset IDs associated with this package. |
|bypassEntitlementCheck	|`package`	|boolean list|optional	|Flag to bypass entitlement authorization. Default is _false_. Set to _true_ for free packages. |
|regionWhitelist|`package`	|string list|optional	|List of region IDs where this package can be viewed. |

<br/>




***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OEMServer}}/oem/v1/user/packages/{{package1ID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "package": {
        "id": "{{package1ID}}",
        "name": "{{packageName}}",
    	"description": "{{packageDescription}}",
        "bypassEntitlementCheck": false,
        "assetIDs": [
            "{{asset1ID}}",
            "{{asset2ID}}"
        ],
        "regionWhitelist": [
            "{{region1ID}}"
        ]
    }
}
```



### Retrieve package information


Returns information for the specified package, including productIDs.

<br>

Currently, a productID is calculated on the fly using packageID_billingPlanID.
A productID is not calculated on all package search calls.



<br/>

#### Path Parameters

|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|package1ID	|string		|required	|ID of the package to be retrieved. |

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/user/packages/{{package1ID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| excludeFields |  | Omit the specified fields. Currently, the only valid value is *assetids*. |



***Responses:***


Status: Retrieve package information | Code: 200



```js
{
    "requestID": "5f536774-f666-4929-be6c-6028b31046b5",
    "timestamp": "2019-12-13T00:01:06.253239722Z",
    "package": {
        "id": "d2595580-3935-11e8-b85b-c9864ba6c1ca3",
        "name": "Argentina Test",
        "description": "Argentina Test",
        "bypassEntitlementCheck": false,
        "billingPlanIDs": [
            "616ARS-Monthly-FreeTrial",
            "15DayFreeTrialMonthly_004"
        ],
        "productIDs": {
            "15DayFreeTrialMonthly_004": "29b8c4d1-6f90-4e4d-843e-50b2c8528bde"
        },
        "customData": {
            "testfield": "TestCustomData"
        },
        "createdTimestamp": "2018-06-01T18:25:58Z",
        "modifiedTimestamp": "2018-06-01T18:25:58Z"
    }
}
```



### List all packages


Returns a list of all packages in a paginated result set.

All query parameters are optional unless otherwise indicated.

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/user/packages
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| count | 200 | Maximum number of items returned for the search; used for pagination. Default is 20. |
| skip | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |
| sort | name | Sorts the list of packages by the specified field. |
| excludeFields | assetids | Omit the specified fields. Currently, the only valid value is *assetids*. |



***Responses:***


Status: Get packages with count and skip | Code: 200



```js
{
    "requestID": "0d3f46a1-966e-49d2-84cd-c1755f19f7fc",
    "timestamp": "2018-05-17T17:02:10.755842287Z",
    "packages": [
        {
            "id": "zl73kex42t3gj5tuqf6i",
            "name": "Argentina Oro",
            "description": "Argentina Oro",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "jyq1ybbkb1s30t0sfbak"
            ],
            "billingPlanIDs": [
                "ja2edjk4dmolxgowp4i3"
            ]
        },
        {
            "id": "nanh8lrxpps8rpmu9cpk",
            "name": "Argentina Oro",
            "description": "Argentina Oro",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "yxa9vcmnq02jb8b5ymae"
            ],
            "billingPlanIDs": [
                "ja2edjk4dmolxgowp4i3"
            ]
        }
    ],
    "metadata": {
        "count": 2,
        "skip": 3,
        "totalCount": 147
    }
}
```



### List all subscription packages


Returns a list of all packages that are subscriptions in a paginated result set.

All query parameters are optional unless otherwise indicated.

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/user/packages
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| subscriptions |  | Selects subscription packages only. No value is required. |
| count | 20 | Maximum number of items returned for the search; used for pagination. Default is 20. |
| skip | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |



***Responses:***


Status: Get subscription packages | Code: 200



```js
{
    "requestID": "a129a14c-8290-4a38-a9b3-740373ecf5e6",
    "timestamp": "2018-05-17T17:57:49.646033046Z",
    "packages": [
        {
            "id": "7d6eb650-2e27-11e8-93ef-dd9abf020151",
            "name": "Otters",
            "description": "Oregon City Otters boys curling team\n\n",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "0b987d709cbb2b9bccef857bc5630c3e"
            ],
            "billingPlanIDs": [
                "\u0001\t",
                "Cascadia Curling - Silver",
                "Cascadia Curling - Gold"
            ]
        },
        {
            "id": "5a0e8710-376b-11e8-a5b7-83983f3c2ccc",
            "name": "Bobcats",
            "description": "Bremerton Bobcats girls curling team\n\n",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "0b987d709cbb2b9bccef857bc5630c3e"
            ],
            "billingPlanIDs": [
                "Cascadia Curling - Silver",
                "Cascadia Curling - Gold",
                "       "
            ]
        },
        {
            "id": "5c6f0c50-376b-11e8-a5b7-83983f3c2ccc",
            "name": "Orcas",
            "description": "Olympia Orcas girls curling team\n\n",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "0b987d709cbb2b9bccef857bc5630c3e"
            ],
            "billingPlanIDs": [
                "Cascadia Curling - Silver",
                "Cascadia Curling - Gold",
                "       "
            ]
        }
    ],
    "metadata": {
        "count": 3,
        "skip": 2,
        "totalCount": 22
    }
}
```



### List packages for billing plans


Returns all packages associated with the specified billing plan(s) in a paginated result set.

All query parameters are optional unless otherwise indicated.

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/user/packages
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| billingPlanIDs | {{billingPlan1ID}} | Comma-separated list of one or more billing plan IDs. |
| skip |  | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |
| count |  | Maximum number of items returned for the search; used for pagination. Default is 20. |



***Responses:***


Status: Get packages for a billing plan, return 2 out of 6 total | Code: 200



```js
{
    "requestID": "7770c01c-159b-4fdd-a052-40f5436c79cf",
    "timestamp": "2018-05-17T16:58:30.7837668Z",
    "packages": [
        {
            "id": "akv8dqdjbpps8xp1h6st",
            "name": "Argentina Oro",
            "description": "Argentina Oro",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "pees2xmdbkeugg6expxu"
            ],
            "billingPlanIDs": [
                "ja2edjk4dmolxgowp4i3"
            ]
        },
        {
            "id": "zl73kex42t3gj5tuqf6i",
            "name": "Argentina Oro",
            "description": "Argentina Oro",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "jyq1ybbkb1s30t0sfbak"
            ],
            "billingPlanIDs": [
                "ja2edjk4dmolxgowp4i3"
            ]
        }
    ],
    "metadata": {
        "count": 2,
        "skip": 0,
        "totalCount": 6
    }
}
```



### List packages with custom data


Returns a list of all packages with the specified custom data.

All query parameters are optional unless otherwise noted.



<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/user/packages
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| customData.Sport | Basketball | Required. Custom data being requested. |
| skip |  | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |
| count |  | Maximum number of items returned for the search; used for pagination. Default is 20. |



***Responses:***


Status: Get package by custom data | Code: 200



```js
{
    "requestID": "356212e0-9144-4f5f-b407-a8898835f8da",
    "timestamp": "2018-05-17T17:07:22.021637228Z",
    "packages": [
        {
            "id": "sn74mnaawdpt1wqnsh1x",
            "name": "Chile Oro",
            "description": "Chile Oro",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "t65mjh715wmekjj42iz1"
            ],
            "billingPlanIDs": [
                "48drivy04dq26c3o8d9w"
            ],
            "customData": {
                "League": "NBA",
                "Sport": "Basketball"
            }
        }
    ],
    "metadata": {
        "count": 20,
        "skip": 0,
        "totalCount": 1
    }
}
```



### List user packages and entitlements for assets (admin)


Returns a list of packages and entitlements for the provided asset IDs for the specified user.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|userid	|string		|required	|ID of the target user account. |

<br/>

#### Body Parameters
|Field		|Type		|Required	|Description|
|---		|---		|---		|---		|
|assetIDs	|string list|optional	|List of asset IDs. |

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OEMServer}}/oem/v1/admin/entitlements/{{userid}}/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "assetIDs": [
        "{{videoAsset1ID}}",
        "{{videoAsset2ID}}",
        "{{videoAsset3ID}}"
    ]
}
```



***Responses:***


Status: Empty list of packages and entitlements | Code: 200



```js
{
    "requestID": "b52cdf9c-b4a3-4178-b04b-8837fcbd8d71",
    "timestamp": "2019-12-13T00:13:52.318481578Z",
    "assetPackages": [],
    "packages": [],
    "billingPlans": []
}
```



### Delete a package


Deletes the specified package, making it unavailable for purchase (or for viewing, if the package is free).

<br/>

#### Path Parameters

|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|package1ID	|string		|required	|ID of the package to be deleted. |

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target package.|
|404		|1040	|*Not Found*: Target package not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OEMServer}}/oem/v1/user/packages/{{package1ID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Admin unpublishes a pulished asset immediately | Code: 200



```js
{"requestID":"a4724e1d-600d-4462-89ee-96f008f3e6d0","timestamp":"2017-11-30T21:47:51.955779914Z","message":"Asset ID 43435875 was successfully deleted."}
```



### Grant an entitlement


Grants a package entitlement to the current subscriber. Normally, this happens automatically as a result of a purchase. This endpoint is intended for use by customer support tools.


<br/>

#### Body Parameters

|Field			|Parent		|Type		|Required	|Description|
|---			|---		|---		|---		|---		|
|`entitlement`	|			|object		|required	|Entitlement definition (container). |
|packageID		|`entitlement`	|string		|required	|Unique package identifier. |
|uid			|`entitlement`	|string		|required	|Unique user account ID. |
|startDate		|`entitlement`	|string		|required	|Start date timestamp for user's entitlement to the package. |

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OEMServer}}/oem/v1/admin/entitlements/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "entitlement": {
    "packageID": "{{package1ID}}",
    "uid": "{{userid}}",
    "startDate": "2018-02-01T01:00:00Z"
  }
}
```



### Update entitlements with token


Grants package entitlements to a subscriber based on the contents of a JWT provided in the body of the request.


<br/>

#### Body Parameters

|Field				|Type		|Required	|Description									|
|---				|---		|---		|---											|
|`entitlementToken`	|string		|required	|JWT containing the user ID and entitlements	|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OEMServer}}/oem/v1/entitlements/token
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "entitlementToken": "JWT goes here",
  "provider": "{{tenantName}}"
}
```



### Update a user entitlement (admin)


Updates a subscription entitlement. 

Use this endpoint to extend the end date of an entitlement. Normally this happens automatically as monthly subscription payments are credited. This endpoint is intended for use by customer support tools.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|userid	|string		|required	|ID of the target user account. |
|package1ID	|string		|required	|ID of the package to be updated. |


<br/>

#### Body Parameters
|Field			|Parent		|Type		|Required	|Description|
|---			|---		|---		|---		|---		|
|`entitlement`	|			|object		|required	|Entitlement definition (container). |
|packageID		|`entitlement`	|string		|required	|Unique package identifier. |
|uid			|`entitlement`	|string		|required	|Unique user account ID. |
|startDate		|`entitlement`	|string		|required	|Start date for user's entitlement to the package; in timestamp format. |
|endDate		|`entitlement`	|string		|required	|End date for user's entitlement to the package; in timestamp format. |

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OEMServer}}/oem/v1/admin/entitlements/{{userid}}/{{package1ID}}/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "entitlement": {
    "packageID": "{{package1ID}}",
    "uid": "{{userid}}",
    "startDate": "2018-02-01T01:00:00Z",
    "endDate": "2019-02-01T01:00:00Z"
  }
}
```



### List all entitlements


Returns all the entitlements for the logged-in user.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/entitlements
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### List all entitlements for a user (admin)


Returns all the entitlements for the specified user. Requires administrative privileges.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|userid	|string		|required	|ID of the target user account. |

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/admin/entitlements/{{userid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### Grant asset entitlements for a user (admin)


Grants entitlements to the target list of asset IDs for the specified subscriber.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|userid	|string		|required	|ID of the target subscriber account. |

<br/>

#### Body Parameters
|Field		|Type		|Required	|Description|
|---		|---		|---		|---		|
|assetIDs	|string list|optional	|List of asset IDs. |

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OEMServer}}/oem/v1/admin/entitlements/{{userid}}/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "assetIDs": [
        "{{asset1ID}}",
        "{{asset2ID}}"
    ]
}
```



### List entitlements for user and assets


Retrieves the calling user's entitlement and package information for a set of specified asset IDs.

<br/>

#### Path Parameters
|Label  |Type   |Required   |Description|
|---    |---    |---        |---        |
|assetIDs |string |optional   | Comma-seperated list of asset IDs for which you'd like the package information.|

<br/>

#### Response Object
|Field      |Parent |Type   |Required   |Description    |
|---        |---    |---    |---        |---            |
|`assetPackages`| | array | optional | List of packages associated with the requested asset IDs. Can be empty.
|assetID  | assetPackages  |optional |required   |One of the requested asset IDs.
|packageIDs	|  assetPackages | string |required | Array of package IDs that contain the related asset ID.
|packages|  | array | required | List of full package objects from the `assetPackages` list.
|products|  | array | required | List of full product objects for products that contain the packages in the `assetPackages` field.
|billingplans |  | array | required | List of billing plan objects associated with the products in the `products` fields.

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/entitlements/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| assetIDs | {{asset1ID}},{{asset2ID}} | List of asset IDs separated by commas. *Required.* |



***Responses:***


Status: List entitlements for user and assets | Code: 0



```js
{
    "requestID": "71670ecc-4d47-413b-936f-a883b9d62429",
    "timestamp": "2019-12-19T23:52:16.719601971Z",
    "assetPackages": [
        {
            "assetID": "eb63bc9d-d71f-4e2d-be72-bbfcaf22e410",
            "packageIDs": [
                "0mf3nhpxb3lbkbj8xa2f2roqu",
                "00ae74f0-8882-11e9-a443-233a0f5b042f"
            ]
        }
    ],
    "packages": [
        {
            "id": "0mf3nhpxb3lbkbj8xa2f2roqu",
            "name": "Girls Youth Soccer ",
            "description": "Girls Youth Soccer Games 11",
            "bypassEntitlementCheck": true,
            "billingPlanIDs": [
                "latestandgreatstbilling"
            ],
            "productIDs": {
                "latestandgreatstbilling": "82710733-f741-453b-986f-37e30b7fd020"
            },
            "customData": {
                "currency": "2333 f . af kafkekjfekakd",
                "league": "2233",
                "mediumDescription": "22",
                "productPrice": "2223",
                "sport": "true",
                "sportId": "```kk`k`k"
            },
            "owned": true
        },
        {
            "id": "00ae74f0-8882-11e9-a443-233a0f5b042f",
            "name": "Jun6Package",
            "bypassEntitlementCheck": false,
            "billingPlanIDs": [
                "TESTBP_2776",
                "billing_all_access"
            ],
            "productIDs": {
                "TESTBP_2776": "91c7833c-bbf3-4b40-b4fe-ac64af8bd9f9",
                "billing_all_access": "47afab5e-4d5c-4a49-a416-ccd8873b04f8"
            },
            "customData": {
                "currency": "fkfjeifiej 3i3ijfjf",
                "league": "",
                "leagueId": "dfafef",
                "longDescription": "afadafdff",
                "mediumDescription": "afdaf",
                "productDescription": "afafaf",
                "productName": "sdf",
                "productPrice": "2223",
                "shortDescription": "affada",
                "skuNumber": "1233",
                "skuType": "2232111",
                "sport": "faf",
                "sportId": "sss"
            },
            "owned": false
        }
    ],
    "billingPlans": [
        {
            "id": "TESTBP_2776",
            "description": "s111111111111111",
            "recurrence": "1y",
            "prices": {
                "Amazon": {
                    "CAD": 0.02
                },
                "Apple": {
                    "CAD": 1.49,
                    "USD": 3.99
                }
            },
            "trialperiod": {
                "cycleLength": "3d",
                "cycles": 1
            },
            "customData": {}
        },
        {
            "id": "billing_all_access",
            "description": "Monthly All Access Season ",
            "recurrence": "1M",
            "prices": {
                "Amazon": {
                    "BRL": 1,
                    "CAD": 0,
                    "USD": 0
                },
                "Apple": {
                    "BRL": 0,
                    "CAD": 0,
                    "USD": 0
                },
                "Google": {
                    "BRL": 0,
                    "CAD": 0,
                    "USD": 0
                },
                "Roku": {
                    "BRL": 0,
                    "CAD": 0,
                    "USD": 0
                },
                "Vindicia": {
                    "BRL": 0,
                    "CAD": 0,
                    "USD": 0
                }
            },
            "trialperiod": null,
            "customData": {}
        },
        {
            "id": "latestandgreatstbilling",
            "description": "latestandgreatstbilling",
            "recurrence": "1M",
            "prices": {
                "Vindicia": {
                    "USD": 1.11
                }
            },
            "trialperiod": null,
            "customData": {}
        }
    ],
    "Products": [
        {
            "id": "91c7833c-bbf3-4b40-b4fe-ac64af8bd9f9",
            "packageID": "00ae74f0-8882-11e9-a443-233a0f5b042f",
            "billingPlanID": "TESTBP_2776",
            "name": {
                "en": "test empty"
            },
            "shortDesc": {
                "en": "test empty"
            },
            "longDesc": {
                "en": "test empty"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "TEST_Trial_Delete_This",
                    "customData": {}
                }
            },
            "version": 1,
            "created": "2019-10-06T11:35:54.701Z",
            "modified": "2019-10-06T11:35:54.701Z"
        },
        {
            "id": "47afab5e-4d5c-4a49-a416-ccd8873b04f8",
            "packageID": "00ae74f0-8882-11e9-a443-233a0f5b042f",
            "billingPlanID": "billing_all_access",
            "name": {
                "en": "asdfsdfsdf"
            },
            "shortDesc": {
                "en": "asdfsdfsdf"
            },
            "longDesc": {
                "en": "asdfsdfsdfasd"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "DTV_TEST_CLAIREADDITION_006666",
                    "customData": {}
                }
            },
            "version": 2,
            "created": "2019-10-06T11:41:23.038Z",
            "modified": "2019-10-29T19:06:18.392Z"
        },
        {
            "id": "82710733-f741-453b-986f-37e30b7fd020",
            "packageID": "0mf3nhpxb3lbkbj8xa2f2roqu",
            "billingPlanID": "latestandgreatstbilling",
            "name": {
                "en": "latestandgreatestproduct"
            },
            "shortDesc": {
                "en": "latestandgreatestproduct"
            },
            "longDesc": {
                "en": "latestandgreatestproduct"
            },
            "storeData": {
                "Amazon": {
                    "storeProductID": "3",
                    "customData": {}
                },
                "Apple": {
                    "storeProductID": "latestandgreatestproduct",
                    "customData": {
                        "latestandgreatestproduct": "1"
                    }
                },
                "Google": {
                    "storeProductID": "1",
                    "customData": {}
                },
                "Roku": {
                    "storeProductID": "5",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "2",
                    "customData": {}
                }
            },
            "version": 2,
            "created": "2018-12-19T00:56:27.014Z",
            "modified": "2019-12-09T23:47:30.261Z"
        }
    ]
}
```



### List entitlements for user and package (admin)


Returns entitlement information for the specified user and package.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|userid	|string		|required	|ID of the target subscriber account. |
|package1ID	|string		|required	|ID of the target package. |

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/admin/entitlements/{{userid}}/{{package1ID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### Request an entitlement token (admin)


Requests a CDN or DRM token to playback a video asset. The requested token type is returned if the subscriber is entitled to the asset.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|userid		|string		|required	|ID of the target subscriber account. |


<br>

#### Body Parameters
|Field			|Parent	|Type	|Required	|Description	|
|---			|---	|---	|---		|---			|
|assetID		|		|string	|required	|Asset ID requested.|
|playbackUrl	|		|string	|required	|Playback URL for this asset ID. |
|`capabilities`	|		|object |optional	|An optional parameter for reporting device capabilities that might affect video playback. |
|widevineSecurityLevel |`capabilities` | string | optional |The level of the Widevine DRM implementation on the device. Value may be: **L1** \| **L3**. |


<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OEMServer}}/oem/v1/user/accounts/{{userid}}/entitlement
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| tokentype | turner-akamai     | Type of CDN or DRM token required.  Currently supported values are:   
* **turner-akamai**  (Akamai CDN for Turner Broadcasting)   
* **none** (entitlement check with no CDN or DRM protection)

Values to be supported in an upcoming release:  
* **akamai** (Akamai CDN)  
* **isp-atlas** (Atlas DRM) |



***Body:***

```js        
{
    "assetID": "{{asset1ID}}",
    "playbackUrl": "http://www.some.akamai.com/dir/dir2/dir3/dir4/master.m3u8",
    "capabilities": {
        "widevineSecurityLevel": "L1"
    }
}
```



***Responses:***


Status: Request Entitlement Token | Code: 201



```js
{
    "requestID": "74f8e59e-0ef8-4cc5-a741-128c56cdeb15",
    "timestamp": "2017-12-01T20:48:20.148472263Z",
    "entitled": true,
    "assetID": "f329c36a-d280-11e7-883c-37316ed34246",
    "entitlementToken": "{{entitlementToken}}",
    "tokenType": "turner-akamai"
}
```



### Delete an entitlement (admin)


Removes the entitlement to the specified package for the target user. 

This normally happens automatically when a subscription expires. This endpoint is intended for use by customer support tools.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|userid	|string		|required	|ID of the target user account. |
|package1ID	|string		|required	|ID of the target package. |

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified package for the target user.|
|404		|1040	|*Not Found*: No matching package IDs found.|
|404		|1041	|*Not Found*: No matching user ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OEMServer}}/oem/v1/admin/entitlements/{{userid}}/{{package1ID}}/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Admin unpublishes a pulished asset immediately | Code: 200



```js
{"requestID":"a4724e1d-600d-4462-89ee-96f008f3e6d0","timestamp":"2017-11-30T21:47:51.955779914Z","message":"Asset ID 43435875 was successfully deleted."}
```



### Add assets to packages


Adds one or more assets to one or more packages.

<br>

Attempts to add all of the listed asset IDs to all of the specified package IDs. 
Returns `200` whether the listed asset IDs are already present or not; 
duplicate asset IDs are ignored.

<br>

#### Body Parameters
| Field | Description |
| ----- | ----------- |
| packageIDs |List of one or more package IDs to update. |
| assetIDs |List of one or more asset IDs to add. |

<br>


#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to add the specified asset IDs to the target packages.|
|404		|1040	|*Not Found*: No matching package IDs found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OEMServer}}/oem/v1/packages/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "packageIDs": [
        "{{package1ID}}"
    ],
    "assetIDs": [
        "{{asset1ID}}",
        "{{asset2ID}}"
    ]
}
```



### Remove assets from packages


Attempts to remove all of the listed asset IDs from all of the specified package IDs.

Returns `200` whether the listed asset IDs are present or not.

<br>

#### Body Parameters
| Field | Description |
| ----- | ----------- |
| packageIDs |List of one or more package IDs to update. |
| assetIDs | List of one or more asset IDs to remove from the packages. |

<br>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified asset IDs from the target packages.|
|404		|1040	|*Not Found*: No matching package IDs found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OEMServer}}/oem/v1/packages/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
	"packageIDs": [ "{{package1ID}}" ],
	"assetIDs":   [ "{{asset1ID}}" ]
}
```



## Package Graphs - v1

Endpoints that deal with package relationships (Packages of Packages).

<br>

### Add a child package

Adds a child package to a package. 

The parent and child packages must already exist. 
If a user is entitled to a package, the user is also entitled to any child packages of that package.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|parentPackageID |string |required	|ID for the parent package.|
|childPackageID |string |required	|ID for the child package to be added.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target package.|
|404		|1040	|*Not Found*: Target package not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: FORMDATA
URL: {{OEMServer}}/oem/v1/packages/{{parentPackageID}}/child/{{childPackageID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Content-Type | application/json |  |


<br/>

### Get all parent packages

Retrieves any parent packages for the specified (child) package.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|childPackageID |string |required	|ID for the specified child package.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1003	|*Forbidden*: Caller not authorized to read the requested resource.|
|404		|1040	|*Not Found*: Target package not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/packages/{{childPackageID}}/parents/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### Get all child packages


Retrieves any child packages for the specified (parent) package. 

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|parentPackageID |string |required	|ID for the specified parent package.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1003	|*Forbidden*: Caller not authorized to read the requested resource.|
|404		|1040	|*Not Found*: Target package not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v1/packages/{{parentPackageID}}/children/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### Remove a child package


Removes a child package from a package. 

> __NOTE:__
> This action does not delete the child package, it only removes the relationship between the specified packages. 
> This call reports success as long as the child and parent packages both exist.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|parentPackageID |string |required	|ID for the parent package.|
|childPackageID |string |required	|ID for the child package.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified package relationship.|
|404		|1040	|*Not Found*: No matching package found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OEMServer}}/oem/v1/packages/{{parentPackageID}}/child/{{childPackageID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Content-Type | application/json |  |



## Entitlements - v2



### Retrieve package


Returns information about the specified package, including any associated products, billing plans, or entitlements.

Currently, the productID is calculated on the fly using packageID_billingPlanID.  However, the productID is not calculated on all package search calls.

All query parameters are optional unless otherwise noted.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|packageID	|string		|required	|ID of the target package. |

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v2/packages/{{packageID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| include | billingplans,entitlements,products | List of associated items to include: *products, billingplans, entitlements*. |
| excludeFields | assetids | Omit the specified fields. Currently, the only valid value is *assetids*. |



### Retrieve packages for billing plans


Returns all packages associated with one or more specified billing plans. The packages are returned in a paginated result set.

All query parameters are optional unless otherwise noted.

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v2/packages
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| billingPlanIDs | {{billingPlan1ID}} | Comma-separated list of one or more billing plan IDs. |
| include | billingplans,entitlements,products | List of associated items to include: *products, billingplans, entitlements*. |
| skip | 0 | Number of returned items to skip from the beginning. Default is 0. |
| count | 10 | Maximum number of items to return per call. Default is 20. |



***Responses:***


Status: Get packages for a billing plan, return 2 out of 6 total | Code: 200



```js
{
    "requestID": "7770c01c-159b-4fdd-a052-40f5436c79cf",
    "timestamp": "2018-05-17T16:58:30.7837668Z",
    "packages": [
        {
            "id": "akv8dqdjbpps8xp1h6st",
            "name": "Argentina Oro",
            "description": "Argentina Oro",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "pees2xmdbkeugg6expxu"
            ],
            "billingPlanIDs": [
                "ja2edjk4dmolxgowp4i3"
            ]
        },
        {
            "id": "zl73kex42t3gj5tuqf6i",
            "name": "Argentina Oro",
            "description": "Argentina Oro",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "jyq1ybbkb1s30t0sfbak"
            ],
            "billingPlanIDs": [
                "ja2edjk4dmolxgowp4i3"
            ]
        }
    ],
    "metadata": {
        "count": 2,
        "skip": 0,
        "totalCount": 6
    }
}
```



### List packages


Lists all available packages in a paginated result set.

All query parameters are optional unless otherwise noted.

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v2/packages
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| count | 10 | Maximum number of items to return per call. Default is 20. |
| skip | 0 | Number of returned items to skip from the beginning. Default is 0. |
| sort | name | Sorts the packages on the specified field. |
| include | billingplans,entitlements,products | List of associated items to include: *products, billingplans, entitlements*. |
| excludeFields | assetids | Omit the specified fields. Currently, the only valid value is *assetids*. |



***Responses:***


Status: List packages (count 3, skip 5) | Code: 200



```js
{
    "requestID": "5db5a3fb-cb58-40b7-9f25-9f8b88d816a7",
    "timestamp": "2020-04-02T22:02:06.625094595Z",
    "packages": [
        {
            "id": "pGw1oiAESOKy6gOl",
            "name": "2 RunScope Test Package",
            "description": "A second package for test purposes with updated description",
            "bypassEntitlementCheck": false,
            "createdTimestamp": "2020-03-04T06:59:35Z",
            "modifiedTimestamp": "2020-03-04T06:59:44.687Z"
        },
        {
            "id": "7d7450a0-8b66-11e8-bfbe-0da88ea9287d",
            "name": "2018 Int'l Field Hockey Pass",
            "description": "Watch live and on-demand.",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "de674067cd47a311b0abb40e60090d5f",
                "f75d9b6a5c435e61c58a7f3536c67202",
                "a2c3a628836026c057148347505f7698",
                "99338cc10c3653a9e35d0bac8e948c9e",
                "865f008923cef3c7399f75195afbc0ff",
                "a8c42cce811af96e996a1ec62a740770",
                "85ea7b2d7201f0904b808b788d5b5b80",
                "94a65242d307934961b3f4d34fe140ab",
                "e308b389f155114716c9edf2e56f23af",
                "507e3514061341b802d99263ee556858",
                "e4052386ab441c685ac6b8d17a89f2a5",
                "2ac3d3fdcdb7d9504dd3149f947cc385",
                "35bda70cf5909fe389ac90fbb3a20a83",
                "3c1386e7fc1527520faf38b10af5ff6f",
                "d10b80b4cf3925ffc0f8c02d945173b7",
                "a3aeff4b590cba4f57ac150796f7d7b9",
                "3ce42eeeb90bd2a3a5de36cec647200a",
                "c63dec13582a54be680f287d1f4ecc00",
                "bef31c326c3e62f349a82d9999c816ec",
                "1cda5cada12c121aa645e412b93132af",
                "8fd58a985eea0d094905c11100c995c9",
                "c323e7d44d435d369485b659fd653344",
                "3953f2aafa18dede90da2fb133f082a3",
                "bf325cb63157e2e7871dcd851f324a21",
                "b36fc067c71b79d0fd14881cccdaf4fb",
                "bb116160bfc6fa42704f35e8f2a2785c",
                "5f0aaf78a5e8deff2d9e0d5b52565e11",
                "05761ed6289ccec25b91dfe7c06bce67",
                "c167afc3a95035f14f255e2125042722",
                "52bfb3e1d900fb91880abd6adb7630bc",
                "6a1b47ab726956bbb745e121a3c96c5c",
                "968cf0489a1a5104547f745b9efc736b",
                "1aaba57acd95c13d19ef5c155b5211b8",
                "41ce74aff0d164da2db7e4b0fae4526e",
                "1e07a42ff512bf8a2b7b57df72a4511e",
                "ae56bdd233611a61c0daebae94aab01b",
                "e125871203b8862537df49dcff57f44f",
                "f09b0c45bd291be869a667080f81f990",
                "4cb172e6229433857fb980ad0a0fa9c8",
                "2030d1a0eb627bc74145fffd0ee90197",
                "35e67dcebc96bcf3c4595dea43b2085b",
                "af94588c2e2c45dfb12efda2fe1d0081",
                "aa55483bcd44806d45755ab81b03a110",
                "34d9171f04fc80b06ebf9dc7f0b2b626",
                "3278df02b5706a2efbe3c346ee6aa70a",
                "287427561d4e28f18dbccbb95c7540a0",
                "87562042c1019c64511ade75ab6d8c01",
                "6421543647b3809725a482be33e6d597",
                "46359cab4eeaf59e1e3d1c9336fa7b84",
                "128df442a94368064f076b051ca22426",
                "371e6d71d79941579312e32c9d16e339",
                "7058108e9e235755ecd52b5d935a0bab",
                "528ed5f14d90d960c351cedcb29f519f",
                "94b92fcc7e71eb87557c90e7f6b33036",
                "894be99c589aaa2af4f53b6155336bec",
                "9f540c1b5ab25cea991cddfcd4dd849c",
                "e32f99413c9bf0e82b8d0c571dcf6500",
                "8888388c72f0c1dbf15cb1fc1ac3361a",
                "c607046ced8dc3381af3e42cc9d42ac7",
                "bbccc29513d9542a9c26c95f676b4eee",
                "cfde9748322c58e07131320066c2e262",
                "25db0724b0f549e1d3478ab7d24f88cf",
                "38c99de98508b415e05e61c345a38d28",
                "6829c39c2e81898a9a6ca3f9be87ab7b",
                "3e8a32c52a97e3fd1925a0db9088a9fa",
                "83e81b71fdf34e8805b1ca7cc6b7ff9a",
                "de9446b5bf34ec1464612e43423f431c",
                "c563cb8b377b98f75ddadf39a316d8f8",
                "8fd7b58d542404b307a389f37e1f35d3",
                "f52926acb3cd2779481ac8cb749a5b9a",
                "cf967fac9697c6493964a80c52351133",
                "3d2db507ec6d00838a346f476e1711ff",
                "dc2acf6ef49fa080dff1c3a866a5ccbd",
                "7663cc4c6a6a1d79e19bc47e85ca4c76",
                "18746245d0a48be9c646eb81fe0f831d",
                "98d784cccb64d0188e856fc1f2444c55",
                "5a87cf1ccd63f7cca0abdaefcf2ca0ba",
                "084ad1490f597c4f33794258b795e171",
                "4e61ec6f93e2df62d5f2a294839ddd2d",
                "c6dfaf5116dd92b2145f73c385ab9036",
                "5197d55eac1e331e95fbc18b372488b8",
                "2b7e29ca94c17824394ae3cee33c9460",
                "14afaeff6a85d9855755798175a27bb6",
                "dee3fec22c1f348b9d37778d58d73d87",
                "409fc0d3361710e0ec1c6d52e20e7819",
                "eddcd8ab77a9c3d8272c76aed300a56d",
                "57ba586645a290026eea1d1c8ee74f06",
                "25687d9a881c43931289a42ea3c5b31e",
                "b3042917ed81309ac1b1002bba8580bf",
                "c4583723cc815d616d4c309cb7bc4d3d",
                "f4ba06a5584b9aee411d2f377de59080",
                "b3ad5aa5dfa2afd3185f2c3545d6c688",
                "81532072317c681a30f1911b0c7006fa",
                "e28a518abd7eb8b33171f1131a0b4256",
                "e135112cc2cc90f69f1b9d2374fe0c39",
                "b520ddc6822555495e5b1b71a73c3995",
                "d91a3ff97e857811d242215dabdaca86",
                "45aec7269839ca0611bfd1d025fda1f2",
                "fc9736cde42dc2eb98f83f21c50b00b7",
                "5c2e8edaf915d624d4bd80b063eebfe2",
                "c45f59e2bf92f83475b53614b44a505b",
                "e919c0d45883ecc8b1cb59045e02af12",
                "c595e7cef54ecfe2f1bc15c05ca00acc",
                "b561a150f98a83b7c11ed0ad37ce9919",
                "fa49476fc47ff4eef7b564c6533a2e12",
                "060fa8563190bd7f7df6afe2eae2fccd",
                "dff30066eda9a8268951223005270b3b",
                "bbb4fed9066c73f2b356eff49b628112",
                "7024b6cea62a6785e24cc9b80d260df2",
                "578d3208453b259ff0b8616e8a19fe62",
                "25412ff92307e30ef3943da8ba8347ed",
                "9e664104be07da49aaefbed8d81c31ff",
                "19c162e744bbd92a903c7276f8e04995",
                "9bacaef424c08095d6ffa6e86114518a",
                "62108e1c0bad43e60a132f76dafe833c",
                "7ce544cc37c707fd74b9a282257c04ca",
                "b8cd4ba865595731ac5dbed7dadfe22b",
                "428e4dbfe0630e3f5cf3851bda12f09f",
                "ff91c0a400c8d9cde83b5ef57e1d5c2b",
                "a76ef5ca0bc51f9fd42cef830cf7ed38",
                "1c1817698c4259585af57b47de500824",
                "91e7565619a6d7e6d20a3853a8abb64a",
                "30504d5883b5f83862e1f50550452222",
                "f2012ca1d1412bd155e2f890c8a59059",
                "f0a2ddc2c5b5cd182ce72f6bcae099bd",
                "6beac0af43c824b801902a91d77aa811",
                "c6abe4679d0f5f2ffb4d1ba7b01aa8e6",
                "c9bb80dde137ca9b483885ad72ad39c7",
                "f14d6c25cd5bc3c62f36a8bbacd47e9f",
                "ca6b8b59ad064742e48efd73ed90f936",
                "89d687235b3804f4b7fc6c77e51765ac",
                "d494e01eb51a631ef131526fd03912ea",
                "c4aab7aef6580150292421dee283b58d",
                "713c360f9447adea5abbcd401b53d737",
                "9ec1d5e587d7363bb0a3234949357e46",
                "db40010682dbfb9ea18b1d1f08fc45fb",
                "48d710892f269754c593f64045f5c634",
                "c25e58c25645b296fc4ca892ef487ffd",
                "d5e89e3a1ba07cdf0b2211234304b3eb",
                "97c767941b0684d4533f825786d364cd",
                "faa87094cb7d70eeeca8671a585e78ce",
                "e32ffc3d8247ced5b2028370f53f9df0",
                "cc717a67895bdbdc400f1625c58d1709",
                "d321cb0cc085ee51a29bc64376e3ac37",
                "6b08bd96cecfa864af5fdd2b7510ac85",
                "f19124b46df4c082a7c80ddfb572d431",
                "f3e232f11d0f52b24ca66d3ab3842b47",
                "a5ba20d81ce949d6bd5adae75d25a776",
                "9ffea2f74a603cd20eccaec0c530ad83",
                "b7430cf5063bf03e26edce7eb3ef8b39",
                "32436c9a1cb076d66b355fdbf378983f",
                "c6415ef1d32d98253c717a3de2d78d07",
                "59e32d9fc19d13d6047bdeffa90dcae4",
                "5a4e6476daae52653838677e125b1b5e",
                "443a6e5ebc5e0b3ced4c80d5c03d9838",
                "c873f7d9a806435d5e8c5868944e0cbc",
                "f0f34fb9e9e7d8971d3f0b61d96925e8",
                "b678b54fe9cbafbda1f5fed8ef19f384",
                "a8ccbd4c20dfbb1b3bd1deceb1501397",
                "df1bc325aa2541d1c2a5664fd062101e",
                "b7feaff33126f743c6fee1dbe5692554",
                "1295c9ffe31d3d48d86ca29b2975e3f9",
                "d399f155c546515fc508794cf5c09c43",
                "ac3238dffc24000f0fa1950c9164ddcb",
                "1141e84735546f9e7cc0c81d8f0bcc4d",
                "86c6d2ae31893582db1b6f45dc242caa",
                "5421b2e20c15bfe16a38e6ad4b7714f0",
                "7ab11dfbd4ffb48e63eae2512614e6f8",
                "a8a969807473183222050fcab66a3354",
                "6838ced76b5ab01cf815094c793dbc2f",
                "db916370ae6cb9f4d9222218c529777a",
                "8763c7a6b9edf650b982c76879e23347",
                "3c07760b67baaa8d3552b34d4ec152f3",
                "fe30261544ca242d3b9ebce76093821a",
                "d242556f69ac739449dd0efbcb5bc90c",
                "7615ba4f8a3d13ed56cf8f5513342685",
                "8b76770e3e791e97a2f52591db870475",
                "80275f0d-752e-4426-8338-65a88e340e34",
                "452c8e8f-5ecb-4f8e-b1a4-6c00b44ff916"
            ],
            "billingPlanIDs": [
                "FreeBillingPlanTest"
            ],
            "productIDs": [
                "f4ebba6c-6da5-4c94-b78c-a3aecad1a62b"
            ],
            "customData": {
                "currency": "USD",
                "league": "FIH",
                "leagueId": "41",
                "longDescription": "Watch every 2018 Men’s World Cup, Women’s World Cup and Women’s Champions Trophy match live and on-demand through December 2018. Stream on all supported devices any time. Available in US only.",
                "mediumDescription": "Watch live and on-demand through December 2018. Stream on all supported devices any time. Available in US only. ",
                "productDescription": "Watch live and on-demand.",
                "productName": "2018 Int'l Field Hockey Pass",
                "productPrice": "9.99",
                "shortDescription": "Watch live and on-demand.",
                "skuNumber": "fh_fih_annual_999_18",
                "skuType": ""
            },
            "createdTimestamp": "2019-03-01T00:20:58Z",
            "modifiedTimestamp": "2020-03-27T22:34:16.677Z"
        },
        {
            "id": "20190226_testpackage",
            "name": "20190226 Test Package",
            "description": "Girls Youth Soccer Games 1",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "233f82625c0e1aa0e28b74fbd01f951c",
                "2f1003d57cc3432c8d61333115332486",
                "111c5f32-e277-4c1e-a48a-979d6d95c39c",
                "f0647151-3c28-44bf-8cb5-0c4b68c7b8d7",
                "invalid-asset-ID",
                "d6f969a1-8649-4a66-b342-1b911a8bd9f2",
                "8b76770e3e791e97a2f52591db870475",
                "6440cf15-f9af-408e-9002-933f5d33d3c8",
                "7615ba4f8a3d13ed56cf8f5513342685",
                "86c0c197b4a8182c9b335415cd9cd9e1",
                "0a9314c34cbb3d789ea0dcdbc60332b5",
                "d746994450158e3aa76df761cd11a470",
                "2c2a921e030e138e1a59693fa86d2c92",
                "8d721c7de628453265f62c702f5f9990",
                "d3692dc1-b18f-4ba4-9528-154421d1c9c7",
                "b3468ec8d44a8e2372dcb1c979fc8d39",
                "30164bc7-2d78-40e6-976b-bdf36d32c8f5",
                "4917928935588a51707cc35d94dcee8d",
                "80275f0d-752e-4426-8338-65a88e340e34",
                "8957b7fb-0a99-4c5e-bae8-4a08709aa377"
            ],
            "billingPlanIDs": [
                "afafafeif93389384274928492392922"
            ],
            "productIDs": [
                "837e6e14-0f4d-4cb2-9c80-51a673dce22b"
            ],
            "regionWhitelist": [
                "ngldkk1p1sbjzg27spjz",
                "7a94ea90-bb8e-11e8-a6ac-2522b9238b35",
                "74568a50-1291-4643-b27d-052e249a4a13"
            ],
            "createdTimestamp": "2019-02-27T00:02:08Z",
            "modifiedTimestamp": "2019-10-28T23:20:40.533Z"
        }
    ],
    "metadata": {
        "count": 3,
        "totalCount": 84,
        "skip": 5
    }
}
```



Status: Include All Entitled Info | Code: 200



```js
{
    "requestID": "5a2be7ea-1c45-4a37-a9ad-49ff9acbf765",
    "timestamp": "2019-03-21T22:16:01.638958047Z",
    "packages": [
        {
            "id": "7d7450a0-8b66-11e8-bfbe-0da88ea9287d",
            "name": "2018 Int'l Field Hockey Pass",
            "description": "Watch live and on-demand.",
            "bypassEntitlementCheck": false,
            "billingPlanIDs": [
                "FreeBillingPlanTest"
            ],
            "productIDs": [
                "f4ebba6c-6da5-4c94-b78c-a3aecad1a62b"
            ],
            "customData": {
                "currency": "USD",
                "league": "FIH",
                "leagueId": "41",
                "longDescription": "Watch every 2018 Men’s World Cup, Women’s World Cup and Women’s Champions Trophy match live and on-demand through December 2018. Stream on all supported devices any time. Available in US only.",
                "mediumDescription": "Watch live and on-demand through December 2018. Stream on all supported devices any time. Available in US only. ",
                "productDescription": "Watch live and on-demand.",
                "productName": "2018 Int'l Field Hockey Pass",
                "productPrice": "9.99",
                "shortDescription": "Watch live and on-demand.",
                "skuNumber": "fh_fih_annual_999_18",
                "skuType": ""
            },
            "createdTimestamp": "2019-03-01T00:20:58Z",
            "modifiedTimestamp": "2019-03-01T00:20:58.745Z"
        },
        {
            "id": "20190226_testpackage",
            "name": "20190226 Test Package",
            "description": "Girls Youth Soccer Games 1",
            "bypassEntitlementCheck": false,
            "regionWhitelist": [
                "ngldkk1p1sbjzg27spjz"
            ],
            "createdTimestamp": "2019-02-27T00:02:08Z",
            "modifiedTimestamp": "2019-03-19T23:47:05.45Z"
        },
        {
            "id": "package_all_access",
            "name": "All Access Season Pass",
            "description": "All Access Season Pass",
            "bypassEntitlementCheck": false,
            "billingPlanIDs": [
                "asdf3",
                "15DayFreeTrialMonthly_001",
                "15DayFreeTrialMonthly_003"
            ],
            "productIDs": [
                "b2c534b7-3174-41ca-a069-96a091353d0e",
                "d9ce9481-71d2-40de-b295-cf0eefef7d6e",
                "0bb31ba1-ed8f-4470-b3ef-6975d8d074fe"
            ],
            "createdTimestamp": "2018-06-08T22:45:37Z",
            "modifiedTimestamp": "2018-08-28T18:44:21.137Z"
        }
    ],
    "entitled": [
        "7d7450a0-8b66-11e8-bfbe-0da88ea9287d",
        "20190226_testpackage",
        "package_all_access"
    ],
    "metadata": {
        "count": 3,
        "totalCount": 64,
        "skip": 0,
        "entitlementsAvailable": true
    }
}
```



### List subscription packages


Lists all subscription packages in a paginated result set.

All query parameters are optional unless otherwise noted.

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v2/packages
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| subscriptions |  | Required.  Select subscription packages only.  This key requires no value. |
| include | billingplans,entitlements,products | List of associated items to include: *products, billingplans, entitlements*. |
| skip | 0 | Number of returned items to skip from the beginning. Default is 0. |
| count | 10 | Maximum number of items to return per call. Default is 20. |



***Responses:***


Status: Get subscription packages | Code: 200



```js
{
    "requestID": "a129a14c-8290-4a38-a9b3-740373ecf5e6",
    "timestamp": "2018-05-17T17:57:49.646033046Z",
    "packages": [
        {
            "id": "7d6eb650-2e27-11e8-93ef-dd9abf020151",
            "name": "Otters",
            "description": "Oregon City Otters boys curling team\n\n",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "0b987d709cbb2b9bccef857bc5630c3e"
            ],
            "billingPlanIDs": [
                "\u0001\t",
                "Cascadia Curling - Silver",
                "Cascadia Curling - Gold"
            ]
        },
        {
            "id": "5a0e8710-376b-11e8-a5b7-83983f3c2ccc",
            "name": "Bobcats",
            "description": "Bremerton Bobcats girls curling team\n\n",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "0b987d709cbb2b9bccef857bc5630c3e"
            ],
            "billingPlanIDs": [
                "Cascadia Curling - Silver",
                "Cascadia Curling - Gold",
                "       "
            ]
        },
        {
            "id": "5c6f0c50-376b-11e8-a5b7-83983f3c2ccc",
            "name": "Orcas",
            "description": "Olympia Orcas girls curling team\n\n",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "0b987d709cbb2b9bccef857bc5630c3e"
            ],
            "billingPlanIDs": [
                "Cascadia Curling - Silver",
                "Cascadia Curling - Gold",
                "       "
            ]
        }
    ],
    "metadata": {
        "count": 3,
        "skip": 2,
        "totalCount": 22
    }
}
```



### List packages with custom data


Lists all packages with the specified custom data.

All query parameters are optional unless otherwise noted.

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v2/packages
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| customData.Sport | Basketball | Required.  Custom data being requested. |
| include | products,billingplans,entitlements | List of associated items to include: *products, billingplans, entitlements*. |
| skip | 0 | Number of returned items to skip from the beginning. Default is 0. |
| count | 20 | Maximum number of items to return per call. Default is 20. |



***Responses:***


Status: Get package by custom data | Code: 200



```js
{
    "requestID": "356212e0-9144-4f5f-b407-a8898835f8da",
    "timestamp": "2018-05-17T17:07:22.021637228Z",
    "packages": [
        {
            "id": "sn74mnaawdpt1wqnsh1x",
            "name": "Chile Oro",
            "description": "Chile Oro",
            "bypassEntitlementCheck": false,
            "assetIDs": [
                "t65mjh715wmekjj42iz1"
            ],
            "billingPlanIDs": [
                "48drivy04dq26c3o8d9w"
            ],
            "customData": {
                "League": "NBA",
                "Sport": "Basketball"
            }
        }
    ],
    "metadata": {
        "count": 20,
        "skip": 0,
        "totalCount": 1
    }
}
```



### Request entitlement token


Allows an application to request a CDN or DRM token to playback a video asset. The requested token type is returned if the user is entitled to the asset.

<br/>

#### Body Parameters
|Field			|Parent	|Type	|Required	|Description	|
|---			|---	|---	|---		|---			|
|assetID		|		|string	|required	|Asset ID requested|
|playbackUrl	|		|string	|required	|Playback URL for this asset ID |
|deviceID		|		|string	|required	|Device ID for presentation (defaults to the caller's IP address) |
|`capabilities`	|		|object |optional	|An optional parameter for reporting device capabilities that might affect video playback |
|widevineSecurityLevel |`capabilities` | string | optional |The level of the Widevine DRM implementation on the device. Valid values are **L1** and **L3**. |


> __NOTE:__
> If the device ID is provided, it must match the device query parameter of the API calls for
> [Track stream concurrency and progress](https://docs.dtc.istreamplanet.net/#b29f2916-8c89-4316-91fc-e2f565114b61)  and 
> [Stream stop](https://docs.dtc.istreamplanet.net/#54bd1329-4dfd-4a36-a9f9-08dcd68806c1).

***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OEMServer}}/oem/v2/entitlement
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| tokentype | turner-akamai | Type of CDN or DRM token required.  Currently supported values are:   
* **turner-akamai**  (Akamai CDN for Turner Broadcasting)   
* **none** (entitlement check with no CDN or DRM protection)

Values to be supported in an upcoming release:  
* **akamai** (Akamai CDN)  
* **isp-atlas** (Atlas DRM) |



***Body:***

```js        
{
    "assetID": "{{asset1ID}}",
    "playbackUrl": "http://www.some.akamai.com/dir/dir2/dir3/dir4/master.m3u8",
    "deviceID": "postman",
    "capabilities": {
        "widevineSecurityLevel": "L3"
    }
}
```



***Responses:***


Status: Request Entitlement Token | Code: 201



```js
{
    "requestID": "74f8e59e-0ef8-4cc5-a741-128c56cdeb15",
    "timestamp": "2017-12-01T20:48:20.148472263Z",
    "entitled": true,
    "assetID": "f329c36a-d280-11e7-883c-37316ed34246",
    "entitlementToken": "{{entitlementToken}}",
    "tokenType": "turner-akamai"
}
```

<br/>

### Retrieve entitlement details

Identifies if the user is entitled to an asset and, if so, why.

<br/>

#### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|assetID	|string		|required	|Asset ID that you want entitlement information for.|

<br/>

***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OEMServer}}/oem/v2/entitlement/asset/{{assetID}}/details/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Content-Type | application/json |  |



---

[Back to top of Entitlements](api-entitlements)

