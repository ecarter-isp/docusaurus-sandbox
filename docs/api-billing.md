---
id: api-billing
title: Billing
sidebar_label: Billing
---

The *billing* endpoints are used manage product purchases, refunds, billing plans, subscriptions, and related attributes. 
These endpoints allow applications to support in-app mobile purchases as well as credit card transactions via PCI-compliant secure web forms.

--------

## Billing - v1


### Finalize web session


Finalizes the web session and commits the data submitted by the web client to the payment processor.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|WebSessionID	|string |required	|ID for the user's web session.|


***Endpoint:***

```bash
Method: PUT
Type: FORMDATA
URL: {{OBMServer}}/obm/v1/user/websessions/{{WebSessionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### List billing plans


Lists all known billing plans for the calling user.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/user/billingplans
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### Retrieve a billing plan


Retrieves the specified billing plan.


<!-- 

Add the billingPlanID path parameter description

Add error msgs

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/user/billingplans/{{billingPlanID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### Get a product


Returns the specified product.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|productID	|string |required	|ID for the target product to be retrieved.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/products/{{productID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### List products


Returns a list of all products. Optionally returns only those products matching the specified query parameters.

To get the one product (if any) for a package and billing plan, specify both the _package_ and _billingplan_ parameters.

<br/>

**Notes:** 
* All query parameters are optional unless otherwise noted.
* The _sort_, _skip_ and _count_ query parameters only apply when neither _package_, _billingplan_, nor _assetids_ are provided.
* All query parameters are processed as logical AND, so any results returned must meet **all** of the specified search criteria. Consequently, using more parameters tends to return fewer results.

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/products
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| package |  | Returns all products associated with the specified package ID. |
| billingplan |  | Returns all products associated with the specified billing plan ID. |
| assetids |  | Comma-separated list of asset IDs for which to return products. |
| sort | name.en | Sorts the products by the specified field for the indicated language. |
| skip | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |
| count | 10 | Maximum number of items returned for the search; used for pagination. Default is 20. |



***Responses:***


Status: Get products for billing plan | Code: 200



```js
{
    "requestID": "63519291-7cb0-4f2a-bc59-6906400d263a",
    "timestamp": "2018-05-29T01:36:35.556682Z",
    "products": [
        {
            "id": "f2f8193d-ab48-45e5-8c34-52c9caad0198",
            "packageID": "38a9oflp7jstuinb93tc",
            "billingPlanID": "m8yjganycaqb5ciuguw2",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        }
    ]
}
```



Status: Get the first ten products sorted by the name field (English version) | Code: 200



```js
{
    "requestID": "fe076954-db66-49fa-92d4-03e4fbf90612",
    "timestamp": "2018-05-29T01:41:57.254945Z",
    "products": [
        {
            "id": "ab5c7834-db20-4ab4-8bae-d04e6528648f",
            "packageID": "cpv2s0j24mx6ow3253a7",
            "billingPlanID": "1q6efmhjmx3jwrp4l48a",
            "name": {
                "en": "AAA",
                "es": "NHL 2018-19"
            },
            "shortDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 2
        },
        {
            "id": "f2f8193d-ab48-45e5-8c34-52c9caad0198",
            "packageID": "38a9oflp7jstuinb93tc",
            "billingPlanID": "m8yjganycaqb5ciuguw2",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "ac99ce36-8108-434b-9dbb-5eb7b294335b",
            "packageID": "l58xb7d1oxbsdvoite46",
            "billingPlanID": "f2u3th1z6tfxoxe8az1h",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "a8eb1bed-ef93-4aab-8cb0-0d5c4e264873",
            "packageID": "oxl9z1s1jsqwxyp286u1",
            "billingPlanID": "4070nkcrrm99ekci62s1",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "0103c989-1496-4e0d-b89c-e453a236b67b",
            "packageID": "wph1bkwml96cbusi3e4g",
            "billingPlanID": "2lqxmu5w9gs5o1f630bi",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "759f8dcf-af0c-480b-85f4-9de6a8d8d183",
            "packageID": "3ci72pyk9c4yj0qsqar5",
            "billingPlanID": "l7dnhtub3ct3hri6bb0y",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "2a41ef89-25a5-4a9a-852f-f68c676711c0",
            "packageID": "jiixlcay2ul9iyxub9a8",
            "billingPlanID": "84e7e913x5bq38d4m49h",
            "name": {
                "en": "NHL 2018-19",
                "es": "NHL 2018-19"
            },
            "shortDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 2
        }
    ]
}
```



Status: Get products for package | Code: 200



```js
{
    "requestID": "d4c61345-a459-47ac-b055-03edc52d89d4",
    "timestamp": "2018-05-29T01:34:08.288021Z",
    "products": [
        {
            "id": "ab5c7834-db20-4ab4-8bae-d04e6528648f",
            "packageID": "cpv2s0j24mx6ow3253a7",
            "billingPlanID": "1q6efmhjmx3jwrp4l48a",
            "name": {
                "en": "AAA",
                "es": "NHL 2018-19"
            },
            "shortDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 2
        }
    ]
}
```



Status: Get product for package and billing plan | Code: 200



```js
{
    "requestID": "e87f9b2e-cb6b-43a6-8a24-47a2180c1f80",
    "timestamp": "2018-05-29T01:39:25.677166Z",
    "product": {
        "id": "ab5c7834-db20-4ab4-8bae-d04e6528648f",
        "packageID": "cpv2s0j24mx6ow3253a7",
        "billingPlanID": "1q6efmhjmx3jwrp4l48a",
        "name": {
            "en": "AAA",
            "es": "NHL 2018-19"
        },
        "shortDesc": {
            "en": "NHL League Pass 2018-19",
            "es": "NHL Pase de la liga 2018-19"
        },
        "longDesc": {
            "en": "NHL League Pass 2018-19",
            "es": "NHL Pase de la liga 2018-19"
        },
        "storeData": {
            "Apple": {
                "storeProductID": "NHL 2018",
                "customData": {
                    "tier": 4
                }
            },
            "Google": {
                "storeProductID": "NHL-2018.1",
                "customData": {}
            },
            "Vindicia": {
                "storeProductID": "NHL 2018",
                "customData": {
                    "productType": "Premium"
                }
            }
        },
        "version": 2
    }
}
```



Status: Get products for assets | Code: 200



```js
{
    "requestID": "e4f1503a-2515-4e38-85b4-c4b60d24d016",
    "timestamp": "2018-05-29T04:42:30.008523Z",
    "products": [
        {
            "id": "f2f8193d-ab48-45e5-8c34-52c9caad0198",
            "packageID": "38a9oflp7jstuinb93tc",
            "billingPlanID": "m8yjganycaqb5ciuguw2",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "ac99ce36-8108-434b-9dbb-5eb7b294335b",
            "packageID": "l58xb7d1oxbsdvoite46",
            "billingPlanID": "f2u3th1z6tfxoxe8az1h",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "a8eb1bed-ef93-4aab-8cb0-0d5c4e264873",
            "packageID": "oxl9z1s1jsqwxyp286u1",
            "billingPlanID": "4070nkcrrm99ekci62s1",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "0103c989-1496-4e0d-b89c-e453a236b67b",
            "packageID": "wph1bkwml96cbusi3e4g",
            "billingPlanID": "2lqxmu5w9gs5o1f630bi",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "759f8dcf-af0c-480b-85f4-9de6a8d8d183",
            "packageID": "3ci72pyk9c4yj0qsqar5",
            "billingPlanID": "l7dnhtub3ct3hri6bb0y",
            "name": {
                "en": "NHL 2018",
                "es": "NHL 2018"
            },
            "shortDesc": {
                "en": "NHL League Pass",
                "es": "NHL Pase de la liga"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 1
        },
        {
            "id": "2a41ef89-25a5-4a9a-852f-f68c676711c0",
            "packageID": "jiixlcay2ul9iyxub9a8",
            "billingPlanID": "84e7e913x5bq38d4m49h",
            "name": {
                "en": "NHL 2018-19",
                "es": "NHL 2018-19"
            },
            "shortDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 2
        },
        {
            "id": "ab5c7834-db20-4ab4-8bae-d04e6528648f",
            "packageID": "cpv2s0j24mx6ow3253a7",
            "billingPlanID": "1q6efmhjmx3jwrp4l48a",
            "name": {
                "en": "AAA",
                "es": "NHL 2018-19"
            },
            "shortDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "longDesc": {
                "en": "NHL League Pass 2018-19",
                "es": "NHL Pase de la liga 2018-19"
            },
            "storeData": {
                "Apple": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "tier": 4
                    }
                },
                "Google": {
                    "storeProductID": "NHL-2018.1",
                    "customData": {}
                },
                "Vindicia": {
                    "storeProductID": "NHL 2018",
                    "customData": {
                        "productType": "Premium"
                    }
                }
            },
            "version": 2
        }
    ]
}
```



### List user subscriptions


Returns a list of subscriptions associated with the calling user.  Optionally includes the related packages in the response.

<br/>

##### Path Parameters
|Label  |Type   |Required   |Description|
|---    |---    |---        |---        |
|include |string |optional   | Set value to "packages" to recieve package information along with each subcription.|

<br/>

#### Response Object
|Field      |Parent |Type   |Required   |Description    |
|---        |---    |---    |---        |---            |
|`subscriptions`| | array | required | List of subscription objects for the calling user
|uid  | subscriptions  |string |required   |UID of user this subscription belongs to|
|productID|  subscriptions | string |required | ProductID as it exists in the payment processor
|packageID|  subscriptions | string | required | PackageID for the package to which this subscription grants an entitlement |
|store| subscriptions | string | required | Payment processor that this subscription is processed on (Vindicia, Apple, Google, Roku, Amazon)
|storeSubscriptionID | subscriptions | string | required | Identifier for this subscription in the store's system
|startDate| subscriptions | string | required | Date this subscription started
|endDate | subscriptions | string | required | Date this subscription will end. This is updated when renewals are charged.
|nextBillDate|subscriptions | string | optional | For Active subscriptions this is the date of the next renewal charge, will be blank for non-active subcriptions
|status| subscriptions| string| required| Potential Values are "Active" and "Canceled"
|transactionIDs|subscriptions | array | optional | List of transactionIDs that are associated with this subscription
|paymentMethodID |subscriptions | string | optional | ID of payment method used for this subcription.   
|`packages`| | array | optional | List of packages that this subscripton provides an entitlement to, along additional information
|id|packages|string|required|PackageID of this package
|name|packages|string|required|Name of this package
|description|packages|string|required|Description of this package
|bypassEntitlementCheck|packages|bool|required|If this is set to true any user will be entitleed to this package
|billingPlanIDs|packages|array|required| All billing plans linked to this package by a product
|productIDs|packages|array|required| All products linked to this package
|regionWhitelist|packages|array|required| All whitelisted regions linked to this package
|createdTimeStamp|packages|string|required| Date on which this package was created
|modifiedTimestamp|packages|string|required| Date on which this package was last modified

<br>



<!--

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|userid	|string |required	|ID for the user whose subscriptions you wish to retrieve.|

<br/>

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/user/accounts/subscriptions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| include | packages | Optional. Returns all packages related to the user's subscriptions. If used, value must be set to *packages*.  |



### List user subscriptions (admin)


Retrieves subscriptions for the specified user. Requires administrative privileges.

Optionally includes the related packages in the response.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|userid	|string |required	|ID for the user whose subscriptions you wish to retrieve.|

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/admin/accounts/{{userid}}/subscriptions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| include | packages | Optional. Returns all packages related to the user's subscriptions.  If used, value must be set to *packages*. |



### Cancel subscription


Cancels the subscription for the specified product. A successful call stops future charges for the logged in user.

When **disentitleImmediately** is set to *true*, entitlements granted by the subscription are immediately revoked. Otherwise, the user remains entitled until what would have been the next billing date.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|productID	|string |required	|ID for the product subscription you wish to cancel.|

<br/>

##### Body Parameters
|Field	|Type	|Required	|Description|
|---	|---	|---		|---		|
|disentitleImmediately	|boolean |optional	|If set to *true*, immediately revokes the subscription entitlements. Default value is *false*.|

<br/>

<!--

##### Response Body Description
|Field	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>
-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OBMServer}}/obm/v1/user/accounts/subscriptions/{{productID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| action | cancel | Required.  Value must be set to *cancel* to end the user's subscription.  |



***Body:***

```js        
{
  "disentitleImmediately": false
}
```



### Cancel subscription (admin)


Cancels the specified user's subscription to the target product. A successful call stops future charges for the specified user. Requires administrative privileges.

When **disentitleImmediately** is set as *true*, entitlements granted by the subscription are immediately revoked. Otherwise, the user remains entitled until what would have been the next billing date.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|userID	|string |required	|ID for the user whose subscription you wish to cancel.|
|productID	|string |required	|ID for the product subscription you wish to cancel.|

<br/>

##### Body Parameters
|Field	|Type	|Required	|Description|
|---	|---	|---		|---		|
|disentitleImmediately	|boolean |optional	|If set to *true*, immediately revokes the subscription entitlements. Default value is _false_.|

<br/>

<!--

<br>

##### Response Body Description
|Field	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>
-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OBMServer}}/obm/v1/admin/accounts/{{userid}}/subscriptions/{{productID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| action | cancel | Required. Value must be set to *cancel* to end the user's subscription. |



***Body:***

```js        
{
  "disentitleImmediately": false
}
```



### Refund a transaction (admin)


Refunds up to 100% of a user's credit card transaction. Optionally revokes the entitlements associated with this transaction. Requires 
administrative privileges.

**Note:** App-store transactions cannot be refunded with this endpoint.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|userid	|string |required	|ID for the user whose transaction you wish to refund.|
|storeOrderId	|string |required	|ID for the store transaction you wish to refund.|

<br/>

##### Body Parameters
|Field		|Type	|Required	|Description|
|---		|---	|---		|---		|
|percentage	|integer|required	|Percentage of the original purchase amount to refund to the user. Maximum is 100 percent. |
|removeEntitlements	|boolean |optional	|If set to _true_, immediately revokes the associated entitlements. Default value is  _false_.|

<br/>


<!--

##### Response Body Description
|Field	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|

EPC: Potential errors this call may generate?

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/admin/accounts/{{userid}}/transactions/{{storeOrderId}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| action | refund | Value must be set to "refund" to revoke the user's original transaction.
Required. |



***Body:***

```js        
{
  "percentage": 50,
  "removeEntitlements": false
}
```



### Report a transaction refund (admin)


Reports the refund of a transaction performed by a third-party payment processor, then records the refund in Vindicia Cashbox and the subscriber's transaction history. The refund amount is not limited by the original amount of the transaction. Requires administrative privileges.

<br>

Additional options:
* May revoke the entitlements associated with this transaction. 
* May assign a custom transaction ID for the refund. 
* May include note text associated with this refund. 

<br>

**Note:** App-store transactions cannot be refunded with this endpoint.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|userid	|string |required	|ID for the subscriber whose transaction you wish to refund.|
|storeOrderId	|string |required	|ID for the store transaction you wish to refund.|

<br/>

##### Body Parameters
|Field		|Type	|Required	|Description|
|---		|---	|---		|---		|
|percentage	|integer|required if amount not provided |Percentage of the original purchase amount to refund to the subscriber. Maximum is 100 percent. |
|amount		|number |required if percentage not provided | Amount in the original transaction's currency to refund. No maximum value. |
|removeEntitlements	|boolean |optional	|If set to _true_, immediately revokes the associated entitlements. Default value is  _false_. |
|refundID	|string |optional |If a string value is provided here, it is used as the new refund transaction ID. |
|note		|string |optional |Optional note text to add to the refund transaction. |

<br/>

<!--

##### Response Body Description
|Field	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|

EPC: Potential errors this call may generate?

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/admin/accounts/{{userid}}/transactions/{{storeOrderId}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| action | report-refund | Value must be set to "report-refund" to report a refund against the Store Order ID in the URL. Required. |



***Body:***

```js        
{
  "amount": 10.50,
  "removeEntitlements": false,
  "refundID": "storeOrderId_refund_ext_1",
  "note": "This refund was processed by an external payment provider."
}
```



### Retrieve an active subscription report


Returns a report listing all active subscriptions.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/subscriptions/reports/active
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



### Check user subscriptions (admin)


Checks the subscriptions for a specified user immediately, ignoring the _subscription.NextCheckDate_. 

Useful for testing subscription validation. Requires administrative privileges.

<br/>

##### Path Parameters

|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|userid	|string		|required	|ID of the target user account. |

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/admin/{{userid}}//subscriptions/check
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### Retrieve a canceled subscription report


Returns a report listing all canceled subscriptions.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/subscriptions/reports/canceled
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



## App Store Integrations



### Record Transaction from iTunes in-app purchase


Takes a receipt generated by iTunes and records it within Orbis. The receipt is validated with both iTunes and Orbis.

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/accounts/transactions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| paymentProcessor | apple | Value must be set to "apple" to record iTunes store purchases.
Required. |
| action | record | Value must be set to "record" to complete the purchase.
Required. |



***Body:***

```js        
{
  "receipt": "{{receiptData}}",
  "productID": "{{storeProductID}}",
  "packageID": "{{packageID}}",
  "currency": "USD",
  "action": "Purchase"
}
```



### Record Transaction from Google in-app purchase


Takes a receipt generated by Google and records it within Orbis. The receipt is validated with both Google and Orbis.

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/accounts/transactions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| paymentProcessor | google | Value must be set to "google" to record Google store purchases.
Required. |
| action | record | Value must be set to "record" to complete the purchase.
Required. |



***Body:***

```js        
{
  "receipt": "{\"orderId\":\"{{googleOrderID}}\",\"packageName\":\"com.istreamplanet.orbisinapp\",\"productId\":\"{{storeProductID}}\",\"purchaseTime\":151209421193,\"purchaseState\":0,\"purchaseToken\":\"{{purchaseToken}}\"}",
  "productID": "{{storeProductID}}",
  "currency": "USD",
  "packageID": "{{packageID}}",
  "action": "Purchase"
}
```



### Record Transaction from Roku in-app purchase


Takes a receipt generated by Roku and records it within Orbis. The receipt is validated with both Roku and Orbis.

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/accounts/transactions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| paymentProcessor | Roku | Value must be set to "Roku" to record Roku store purchases.
Required. |
| action | record | Value must be set to "record" to complete the purchase.
Required. |



***Body:***

```js        
{
  "receipt": "{{rokuReceiptId}}",
  "productID": "{{storeProductId}}",
  "packageID": "{{packageId}}",
  "currency": "USD",
  "action": "Purchase"
}
```



### Record Transaction from Amazon in-app purchase


Takes a receipt generated by Amazon and records it within Orbis. The receipt is validated with both Amazon and Orbis.

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/accounts/transactions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| paymentProcessor | amazon | Value must be set to "amazon" to record Amazon store purchases. Required.
 |
| action | record | Value must be set to "record" to complete the purchase.
Required. |



***Body:***

```js        
{
  "receipt": {"amazonUserId":"{{amazonUserId}}","amazonReceiptId":"{{amazonReceiptId}}"},
  "productID": "{{storeProductID}}",
  "currency": "USD",
  "packageID": "{{packageID}}",
  "action": "Purchase"
}
```



### Restore purchases from iTunes receipt


Takes a receipt generated by iTunes and restores purchases within Orbis. 

The receipt is validated with iTunes to get the latest information. Entitlements and valid products that are specified in the receipt--but missing from Orbis--will be added. Transactions for the restored purchases are returned by the request.

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| transactions	| Transaction list | The list of transaction for Entitlements that were restored.|

<br/>
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/accounts/transactions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| paymentProcessor | apple | Required. Value must be set to *apple* to record iTunes store purchases. |
| action | RestorePurchases | Required. Value must be set to *RestoredPurchases* to record and re-validate the purchase in platform database. |



***Body:***

```js        
{
  "receipt": "{{receiptData}}",
  "productID": "{{ignored}}",
  "packageID": "{{ignored}}",
  "currency": "USD",
  "action": "RestoredPurchases"
}
```



## Billing Plan Administration



### Create recurring billing plan


Creates a billing plan for a recurring subscription purchase. 

Different prices can be specified for each payment processor.
The recurrence is specified in the form _{frequency}{interval}_ where _{frequency}_ is an integer, and _{interval}_ is one of the following letters:

*  **s**: second
*  **m**: minute
*  **h**: hour
*  **d**: day
*  **M**: month
*  **y**: year
  
A monthly recurrence would be "**1M**". A quarterly recurrence would be "**3M**". Recurrences in seconds, minutes and hours are intended only for testing purposes.


For example, a monthly recurrence would be specified with **1M**, while a quarterly recurrence would be **3M**. Recurrences in seconds, minutes, and hours are intended for testing purposes only.
<!--
#### Body Parameters
{
  "id": "{{billingPlanID}}",
  "description": "Monthly payment plan",
  "recurrence": "1M",
  "prices": {
    "Apple": {
      "USD": 9.99
    },
    "Google": {
      "USD": 9.99
    },
    "Vindicia": {
      "USD": 7.99
    }
  }
}

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/admin/billingplans
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "id": "{{billingPlanID}}",
    "description": "Monthly payment plan",
    "recurrence": "1M",
    "prices": {
        "Apple": {
            "USD": 9.99
        },
        "Google": {
            "USD": 9.99
        },
        "Vindicia": {
            "USD": 7.99
        }
    }
}
```



### Create recurring billing plan with 14-day trial period


Creates a billing plan for a recurring subscription purchase. 

Different prices can be specified for each payment processor.
The recurrence is specified in the form {_frequency_}{_interval_} where _frequency_ is an integer, and _interval_ is one of the following:

  * **s**: second
  * **m**: minute
  * **h**: hour
  * **d**: day
  * **M**: month
  * **y**: year
  
For example, a monthly recurrence would be specified with **1M**, while a quarterly recurrence would be **3M**. This endpoint sets a 14-day cycle (**14d**) as a trial period. Recurrences in seconds, minutes, and hours are intended for testing purposes only.

<!--

Body parameter description:

{
  "id": "{{billingPlanID}}",
  "description": "Monthly payment plan",
  "recurrence": "1M",
  "prices": {
    "Apple": {
      "USD": 9.99
    },
    "Google": {
      "USD": 9.99
    },
    "Vindicia": {
      "USD": 7.99
    }
  },
  "trialperiod":{
  	"cycleLength": "14d",
  	"cycles": 1
  }
}

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/admin/billingplans
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Body:***

```js        
{
    "id": "{{billingPlanID}}",
    "description": "Monthly payment plan",
    "recurrence": "1M",
    "prices": {
        "Apple": {
            "USD": 9.99
        },
        "Google": {
            "USD": 9.99
        },
        "Vindicia": {
            "USD": 7.99
        }
    },
    "trialperiod": {
        "cycleLength": "14d",
        "cycles": 1
    }
}
```



### Create non-recurring billing plan


Creates a billing plan for a one-time purchase. Different prices can be specified for each payment processor.

<!--

Body Parameters:

{
  "id": "{{billingPlanID}}",
  "description": "Single payment plan",
  "prices": {
    "Apple": {
      "USD": 0.99
    },
    "Google": {
      "USD": 0.99
    },
    "Vindicia": {
      "USD": 0.79

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/admin/billingplans
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "id": "{{billingPlanID}}",
    "description": "Single payment plan",
    "prices": {
        "Apple": {
            "USD": 0.99
        },
        "Google": {
            "USD": 0.99
        },
        "Vindicia": {
            "USD": 0.79
        }
    }
}
```



### Update billing plan


Updates the specified existing billing plan.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|billingPlanID	|string |required	|ID for the target billing plan to be updated.|

<br/>

<!--

##### Body Parameters

{
  "id": "updatedBillingPlan",
  "description": "updated Description",
  "occurrences": 4,
  "recurrence": "30d",
  "prices": {
    "Vindicia": {
      "USD": 99.99
    }
  }
}
-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OBMServer}}/obm/v1/admin/billingplans/{{billingPlanID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "id": "updatedBillingPlan",
  "description": "updated Description",
  "occurrences": 4,
  "recurrence": "30d",
  "prices": {
    "Vindicia": {
      "USD": 99.99
    }
  }
}
```



### Delete billing plan


Deletes the specified existing billing plan.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|billingPlanID	|string |required	|ID for the target billing plan to be deleted.|

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified billing plan.|
|404		|1040	|*Not Found*: No matching billing plan ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OBMServer}}/obm/v1/admin/billingplans/{{billingPlanID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



## Product Administration



### Create a product


Creates a product based on a package and billing plan with app store-specific metadata.

<br/>

##### Body Parameters
|Field		|Parent		|Type	|Required	|Description|
|---		|---	|---	|---		|---		|
|packageID	|	|string 	|required	|ID for the target package to be created.|
|billingPlanID| |string 	|required	|ID for the target billing plan to be created.|
|version	|	|integer	|required	|New version number for this product update.|
|name		|	|string object |required	|Name of product to be created (for one or more languages).|
|shortDesc	|	|string object	|required	|Short description of product to be created (for one or more languages).|
|longDesc	|	|string object	|required	|Long description of product to be created (for one or more languages).|
|`storeData`	|	|string 	|required	|ID for the target product to be created.|
|_storeName_|`storeData`	|string |required	|Store name.  Must be one of [Apple, Google, Vindicia]|
|storeProductID|_storeName_	|string |required	|ID for the target product in this store.|
|customData|_storeName_		|string |optional	|Custom data for the target product to be created.|

<br/>

<!--

##### Body Parameters
{
            "packageID": "d2595580-3935-11e8-b85b-c9864ba6c1ca",
            "billingPlanID": "asdf3",
            "name": {
                "en": "DIRECTV GO",
                "es": "DIRECTV GO",
                "pt": "DIRECTV GO"
            },
            "shortDesc": {
                "en": "DIRECTV GO",
                "es": "DIRECTV GO",
                "pt": "DIRECTV GO"
            },
            "longDesc": {
                "en": "TV made for you. Always stay on with DIRECTV GO.",
                "es": "Televisión a tu manera. Mantente siempre On con DIRECTV GO.",
                "pt": "Televisão do seu jeito. Siga ligado com DIRECTV GO."
            },
            "storeData": {
                "Vindicia": {
                    "storeProductID": "TEST_ORBIS_ENTITLEMENTS_002",
                    "customData": {
                        "country": "AR",
                        "productType": "Base",
                        "vindicia_tax_classification": "VOD",
						"primaryLanguage": "ES",
						"imageFileName": "DTVGO_Argentina_2.png"
                    }
                }
            }
}

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/products
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "packageID": "runscopePackageId",
    "billingPlanID": "22vgd2xuun2003g1hylv",
    "name": {
        "en": "English Name",
        "es": "Spanish Name"
    },
    "shortDesc": {
        "en": "English short",
        "es": "Spanish short"
    },
    "longDesc": {
        "en": "English long",
        "es": "Spanish long"
    }
}
```



***Responses:***


Status: Create a product | Code: 200



### Update a product


Updates the information associated with the specified product.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|productID	|string |required	|ID for the target product to be updated.|

<br/>

The Body Parameters you wish to update are the only ones that must be included.

##### Body Parameters
|Field		|Parent		|Type		|Description|
|---		|---		|---		|---		|
|packageID	|	|string 	|ID for the target package to be updated.|
|billingPlanID| |string 	|ID for the target billing plan to be updated.|
|version	|	|integer 	|New version number for this product update.|
|name		|	|string object 	|Name of product to be updated (for one or more languages).|
|shortDesc	|	|string object	|Short description of product to be updated (for one or more languages).|
|longDesc	|	|string object	|Long description of product to be updated (for one or more languages).|
|`storeData`	|	|string 	|ID for the target product to be updated.|
|_storeName_|`storeData`	|string 	|Store name.  Must be one of [Apple, Google, Vindicia]|
|storeProductID|_storeName_	|string 	|ID for the target product in this store.|
|customData|_storeName_		|string 	|Custom data for the target product to be updated.|


<br/>

<!--
{
  "packageID": "{{packageID}}",
  "billingPlanID": "{{billingPlanID}}",
  "name": {
    "en": "Squamish 2018+",
    "es": "Squamish 2018 Plus"
  },
  "shortDesc": {
    "en": "Squamish League Pass+",
    "es": "Squamish Pase de la liga Plus"
  },
  "longDesc": {
    "en": "Squamish League Pass Plus 2018-19",
    "es": "Squamish Pase de la liga Plus 2018-19"
  },
  "storeData": {
    "Apple": {
      "storeProductID": "Squamish2018Plus",
      "customData": {
        "tier": 4
        }
      },
      "Google": {
        "storeProductID": "Squamish18G+"
      },
      "Vindicia": {
        "storeProductID": "Squamish 2018 Plus",
        "customData": {
            "productType": "Premium"
        }
      }
  },
  "version": 1
}


-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OBMServer}}/obm/v1/products/{{productID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "packageID": "{{packageID}}",
  "billingPlanID": "{{billingPlanID}}",
  "name": {
    "en": "Squamish 2018+",
    "es": "Squamish 2018 Plus"
  },
  "shortDesc": {
    "en": "Squamish League Pass+",
    "es": "Squamish Pase de la liga Plus"
  },
  "longDesc": {
    "en": "Squamish League Pass Plus 2018-19",
    "es": "Squamish Pase de la liga Plus 2018-19"
  },
  "storeData": {
    "Apple": {
      "storeProductID": "Squamish2018Plus",
      "customData": {
        "tier": 4
        }
      },
      "Google": {
        "storeProductID": "Squamish18G+"
      },
      "Vindicia": {
        "storeProductID": "Squamish 2018 Plus",
        "customData": {
            "productType": "Premium"
        }
      }
  },
  "version": 1
}

```



***Responses:***


Status: Update a product | Code: 200



### Delete a product


Deletes the specified existing product.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|productID	|string |required	|ID for the target product to be deleted.|

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete target product.|
|404		|1040	|*Not Found*: Target product not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OBMServer}}/obm/v1/products/{{productID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



## Purchase Flow APIs



### Initialize WebSession for subscription purchase


Creates a WebSession so that a web client can submit credit card payment data securely through Vindicia's Hosted Order Automation forms.

<br/>

##### Body Parameters
|Field		|Parent	|Type	|Required	|Description|
|---		|---	|---	|---		|---		|
|redirectSuccess	|		|string	|required	|URL target for a successful transaction. |
|redirectError		|		|string	|required	|URL target for an unsuccessful transaction. |
|paymentMethodID	|		|string	|required	|Customer's payment method notation: Visa, Amex, Carte Blanche, etc. |
|currency			|		|string	|required	|Three-letter national currency code: USD, BRL, EUR, etc. |
|startTimestamp		|		|string	|required	|Start date and time for this billing transaction, in ISO-8601 (UTC) format: _2017-07-11T05:00:00.00Z_ .|
|`baseProduct`|		|object	|(required)	|PackageID and billingPlanID of the base product. (Only required for a multi-product subscription).|
|packageID|`baseProduct`|string	|(required)	|PackageID of the base product. (Only required for a multi-product subscription).|
|billingPlanID|`baseProduct`|string	|(required)	|BillingPlanID of the base product. (Only required for a multi-product subscription).|
|`products`|		|object		|required	|Comma separated list of items being purchased.|
|_{{packageID1}}: {{billingPlanID1}}_|`products`	|string: string	|required	|ID for each product package and its associated billing plan.|
|`billingAddress`|				|object	|required	|Customer's full billing address.|
|name		|`billingAddress`	|string	|required	|Customer's full name.|
|addr1		|`billingAddress`	|string	|required	|Customer's street address.|
|city		|`billingAddress`	|string	|required	|Customer's city.|
|district	|`billingAddress`	|string	|required	|Customer's state, province, or district.|
|postalCode	|`billingAddress`	|string	|required	|Customer's postal or ZIP code.|
|country	|`billingAddress`	|string	|required	|Customer's country.|
|`discounts`|					|object array	|optional	|Discount codes that can be applied to subscription packages.|
|packageID1		|`discounts`|string	|optional	|PackageID which accepts this subscription discount.|
|billingPlanID1	|`discounts`|string	|optional	|BillingPlanID which accepts this subscription discount.|
|code1			|`discounts`|string	|optional	|Promotional discount code for the specified _{{packageID1}}: {{billingPlanID1}}_.|

<!--

            "packageID": "{{packageID1}}",
            "billingPlanID": "{{billingPlanID1}}",
            "code": "{{promoCode}}"
            
|packageID1		|`products`|string	|optional	|PackageID1 of a multi-product subscription.|
|billingPlanID1	|`products`|string	|optional	|BillingPlanID1 of a multi-product subscription.|
-->            

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/websessions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| method | subscribe | Value must be set to "subscribe" to process the user's subscription. Required. |



***Body:***

```js        
{
    "redirectSuccess": "http://localhost:8081/sbs.html?good=1",
    "redirectError": "http://localhost:8081/sbs.html?bad=1",
    "paymentMethodID": "MainPayment",
    "currency": "USD",
    "startTimestamp": "0",
    "baseProduct": {
        "packageID": "{{packageID2}}",
        "billingPlanID": "{{billingPlanID2}}"
    },
    "products": {
        "{{packageID1}}": "{{billingPlanID1}}",
        "{{packageID2}}": "{{billingPlanID2}}"
    },
    "billingAddress": {
        "name": "Other Guy",
        "addr1": "1234 Fake Street",
        "city": "Fake Town",
        "district": "FakeState",
        "postalCode": "54375",
        "country": "USA"
    },
    "discounts": [
        {
            "packageID": "{{packageID1}}",
            "billingPlanID": "{{billingPlanID1}}",
            "code": "{{promoCode}}"
        },
        {
            "packageID": "{{packageID2}}",
            "billingPlanID": "{{billingPlanID2}}",
            "code": "{{promoCode}}"
        }
    ]
}
```



***Responses:***


Status: Initialize WebSession for subscription purchase (single product) | Code: 0



Status: Initialize WebSession for subscription purchase (multi-product) | Code: 0



### Initialize WebSession for one-off purchase


Creates a WebSession so that a web client can submit credit card payment data securely through Vindicia's Hosted Order Automation forms.

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/websessions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| method | purchase | Value must be set to "purchase" to process the user's one-off purchase. Required. |



***Body:***

```js        
{
  "redirectSuccess": "http://localhost:8081/sbs.html?good=1",
    "redirectError": "http://localhost:8081/sbs.html?bad=1",
    "paymentMethodID":"MainPayment",
    "currency": "USD",
    "products": {
      "9gq7ikzom7joct3ehce2": "asdf3"
    },
    "billingAddress": {
        "name": "Other Guy",
        "addr1": "1234 Fake Street",
        "city": "Fake Town",
        "district": "FakeState",
        "postalCode": "54375",
        "country": "USA"
    }
}
```



### Perform a simulated transaction


Performs a simulated transaction without processing a payment or making any changes on the server.

<br/>

##### Body Parameters
|Field	|Parent		|Type	|Required	|Description|
|---	|---		|---	|---		|---		|
|billingPlanID	|	|string |required	|Unique ID for the target billing plan.|
|packageID		|	|string |required	|Unique ID for the package being "purchased".|
|currency		|	|string |required	|Three-letter currency code for this billing address.|
|***dryRun***			|	|boolean |required	|Must be set to *true* to ensure that payment processing **does not** occur.|
|`address`	|	|object |optional	|If supplied, this billing address will be used for tax calculations.|
|name		|`address`	|string |required	|Customer's full name.|
|addr1		|`address`	|string |required	|Street address.  Can add _addr2_ if needed for more complex locations.|
|city		|`address`	|string |required	|City name|
|district	|`address`	|string |required	|Code for state or province|
|postalCode	|`address`	|string |required	|Postal code or ZIP code|
|country	|`address`	|string |required	|Country code (or full name?)|

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/accounts/transactions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| action | purchase | Value must be set to "purchase" to process the simulated purchase.
Required. |



***Body:***

```js        
{
  "billingPlanID": "{{billingPlanId}}",
  "packageID": "{{packageID}}",
  "currency": "USD",
  "paymentMethodID": "{{paymentMethodID}}",
  "address":{
    "name":"Somebody Famous",
    "addr1":"201 Forrest Ave",
    "city":"East Brewton",
    "district":"AL",
    "postalCode":"36426",
    "country":"US"
  },
  "dryRun": true
}
```



### Perform a simulated transaction with discount code


Performs a simulated transaction using a discount code. No payment is processed nor are any changes made on the server.

The paymentMethodID is optional. If supplied, the address associated with the existing account will be used to calculate taxes.
The address is optional. If supplied, it will be used to calculate taxes.

<br/>

##### Body Parameters
|Field	|Parent		|Type	|Required	|Description|
|---	|---		|---	|---		|---		|
|billingPlanID	|	|string |required	|Unique ID for the target billing plan.|
|packageID		|	|string |required	|Unique ID for the package being "purchased".|
|currency		|	|string |required	|Three-letter currency code for this billing address.|
|***dryRun***			|	|boolean |required	|Must be set to *true* to ensure that payment processing **does not** occur.|
|***discountcode***		|	|boolean |required	|Must be set to a valid promotional code.|
|`address`	|	|object |optional	|If supplied, this billing address will be used for tax calculations.|
|name		|`address`	|string |required	|Customer's full name.|
|addr1		|`address`	|string |required	|Street address.  Can add _addr2_ if needed for more complex locations.|
|city		|`address`	|string |required	|City name|
|district	|`address`	|string |required	|Code for state or province|
|postalCode	|`address`	|string |required	|Postal code or ZIP code|
|country	|`address`	|string |required	|Country code (or full name?)|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/accounts/transactions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| action | purchase | Value must be set to "purchase" to process the simulated purchase.
Required. |



***Body:***

```js        
{
  "billingPlanID": "{{billingPlanId}}",
  "packageID": "{{packageID}}",
  "currency": "USD",
  "paymentMethodID": "{{paymentMethodID}}",
  "address":{
    "name":"Somebody Famous",
    "addr1":"201 Forrest Ave",
    "city":"East Brewton",
    "district":"AL",
    "postalCode":"36426",
    "country":"US"
  },
  "dryRun": true,
  "discountcode": "brazil"
}
```



## Wallet / User Payment Management



### Initialize WebSession for payment update


Creates a WebSession so that the web client can update the user's credit card payment data securely through Vindicia's Hosted Order Automation forms.

<br/>

<!--

##### Response Body Description
|Name	|Type	|Description	|
|---	|---	|---			|
| requestID	| string | The unique log ID for this request.|
| timestamp	| string | The date and time when this call was executed.|
| assetIDs	| string list | The list of requested asset IDs that have existing metadata.|
| assetIDsNotFound	| string list | The list of requested asset IDs that have no metadata.|
| assets	| string | The metadata for the requested asset IDs. |
| count	| object | Counters for the asset ID search results; see **Count Values** below. |

<br/>
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OBMServer}}/obm/v1/user/websessions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| method | savePayment | Value must be set to "savePayment" to process and save the user's updated credit card data.
Required. |



***Body:***

```js        
{
  "redirectSuccess": "http://localhost:8081/sbs.html?good=1",
    "redirectError": "http://localhost:8081/sbs.html?bad=1",
    "paymentMethodID": "{{paymentMethod}}",
    "currency": "USD",
    "billingAddress": {
        "name": "Other Guy",
        "addr1": "1234 Fake Street",
        "city": "Fake Town",
        "district": "FakeState",
        "postalCode": "54375",
        "country": "USA"
    },
    "updateSubscriptions": false
}
```



### List all saved cards for a user


Retrieves all saved credit cards for the current user.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/user/accounts/creditcards
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



***Responses:***


Status: Get User's Saved Cards | Code: 200



```js
{
    "requestID": "86ba0576-9ba4-4d4f-88ca-0bf52953fff4",
    "timestamp": "2019-03-07T22:55:54.025108389Z",
    "creditcardentries": [
        {
            "id": "MyFavoriteCard",
            "uid": "6ece9641-dbbb-4d14-9c7b-0cadc8295410",
            "lastFourDigits": "1445",
            "expiryDate": "2019-08-17T17:36:48Z",
            "active": true,
            "dateAdded": "2019-03-06T17:36:48Z",
            "paymentProcessorCreditCardInfo": {
                "Vindicia": {
                    "paymentMethodID": "MyFavoriteCard"
                }
            }
        }
    ]
}
```



### List all payment methods for a user


Retrieves all payment methods for the current user.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OBMServer}}/obm/v1/user/accounts/paymentmethods
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



***Responses:***


Status: List all payment methods for a user | Code: 0



```js
{
    "requestID": "efa0ad36-52eb-4565-bf91-306e3ea3d45d",
    "timestamp": "2020-01-23T23:02:25.54298491Z",
    "paymentMethods": [
        {
            "id": "mainpayment",
            "created": "2020-01-23T22:59:32Z",
            "type": "CreditCard",
            "primary": true,
            "active": true,
            "address": {
                "name": "Example User",
                "addr1": "167 Victoria St W",
                "addr2": "",
                "city": "Auckland",
                "district": "Texas",
                "postalCode": "10110",
                "country": "US",
                "phone": ""
            },
            "creditCard": {
                "lastDigits": "8291",
                "expirationDate": "202111"
            }
        }
    ]
}
```



---
[Back to top](#billing)
> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2020-04-08 15:58:27 by [docgen](https://github.com/thedevsaddam/docgen)