---
id: api-accounts
title: Accounts
sidebar_label: Accounts
---

The *accounts* endpoints allow applications to create and manage subscriber accounts and associated devices. These endpoints also assist administrators in managing roles and permissions for personnel who have access to the iStreamPlanet Web Portal.

--------


## Accounts - v1


### Create account

Creates a new account from the posted account and profile details.

<br>

####  Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|username	|	|string	|required	|Username/email address for the user's account.|
|password	|	|string	|required	|Password for the user's account.|
|`profile`	|	|object	|required	|Username/email address for the user's account.|
|firstName	|`profile`	|string	|required	|User's firstname.|
|lastName	|`profile`	|string	|required	|User's lastname.|
|email		|`profile`	|string	|required	|Email address for the user's account.|
|iso2country|`profile`	|string	|required	|ISO 2-letter code for the user's country.|
|timezone	|`profile`	|number	|required	|Timezone offset from UTC for the user's location.|

<br/>

#### Password validation
The password is validated based on the tenant's password validation policy. 
The following independent conditions are checked when their corresponding policies are turned on.

* **Password minimum length:**
Always validated. Default is 6 characters. If it fails, then the call returns the error message: "Password minimum length is 6".

* **Digit is present:**
Default is off. If turned on and fails, then the call returns the error message: "Digit is required".

* **Lower case character is present:**
Default is off. If turned on and fails, then the call returns the error message: "Lower case character is required".

* **Upper case character is present:**
Default is off. If turned on and fails, then the call returns the error message: "Upper case character is required".

* **Special character is present:**
Default is off. If turned on and fails, then the call returns the error message: "Special character is required: " with the set of supported characters: __, ) ~ _ % ^ # } ? { [ ] / @ ! $ : . ( - | + ' *__

<br/>

#### Password validation failure
When password validation fails, the call returns HTTP status `422` with error code 1048: "New  password failed validation". Error messages for all failed conditions are concatenated in the same response. See the example "Create account - password validation failed".


<br/>

#### Error Responses

|HTTP Code|Error Code|Description
|---|---|---|
|**400**|1050|*Bad request*: Malformed request body|
|**400**|1042|*Password mismatch*|
|**404**|1041|*Not found*: User does not exist with specified username|
|**422**|1048|*Unprocessable entity*: New password failed validation|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/user/accounts
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "username": "example@istreamplanet.com",
    "password": "secret",
    "profile": {
        "firstName": "Example",
        "lastName": "User",
        "email": "example@istreamplanet.com",
        "iso2country": "US",
        "timezone": 0
    }
}

```



***Responses:***


Status: Create account - password validation failed | Code: 400



```js
{
    "requestID": "0ca05895-07bd-44a6-b241-259b29c93a6f",
    "timestamp": "2018-03-23T21:55:45.307075357Z",
    "errorCode": 1048,
    "errorMessage": "Password minimum length is 6. Digit is required. Upper case character is required. Special character is required: @ ! ? { [ ] / | + ' $ : . ( - * % ^ , ) ~ _ # } "
}
```



Status: Create account (success) | Code: 201



```js
{
    "requestID": "f0272c92-36a5-47c9-b01b-5c41dc6d3496",
    "timestamp": "2017-11-22T16:38:41.515394063Z",
    "account": {
        "uid": "6511b1c6-a595-4e1c-ae95-fda8528a63f9",
        "username": "mary.jackson@example.com",
        "profile": {
            "firstName": "Mary",
            "middleName": "",
            "lastName": "Jackson",
            "nickname": "Hail Mary",
            "zip": "23666",
            "email": "mary.jackson@example.com",
            "homePhone": "514-555-1212",
            "mobilePhone": "514-555-4321",
            "workPhone": "514-555-1234",
            "addressLine1": "1281 Peachtree Rd",
            "addressLine2": "Apt 23",
            "city": "Hampton",
            "state": "VA",
            "iso2country": "US",
            "photoUrl": "http://example.com/photo/9e8324ab",
            "thumbnailUrl": "http://example.com/thumb/32ab4c58",
            "education": "MS",
            "timezone": -8
        },
        "emailVerified": false
    },
    "sessionToken": "{{sessiontoken}}"
}
```



### Login

Takes a user's username and password, then validates the account and generates a session token.

<br/>

If enabled, the system checks the policy governing the _maximum number of failed login attempts_. 
When the call is successful, the user's credentials are validated and the call returns a session token.

<br/>

#### Body Parameters
|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|username	|string |required	|Email address for the user account.|
|password	|string |required	|Password for the user account.|

<br/>

#### Error Responses

|HTTP Code|Error Code|Description
|---|---|---|
|**400**|1050|*Bad request:* Malformed request body|
|**400**|1042|*Password mismatch*|
|**403**|1411|*Forbidden:* Account locked out |
|**404**|1041|*Not found:* User does not exist with specified username|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/user/tokens
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate request |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "username":"mary.jackson@example.com",
  "password":"hello_world123"
}
```



***Responses:***


Status: Login to an Orbis account | Code: 201



```js
{
    "requestID": "68ab1037-d864-4d8e-9657-8d8f7c445b70",
    "timestamp": "2017-11-22T16:50:47.581371495Z",
    "account": {
        "uid": "f14c2fd7-a895-4e31-b930-ced91ff9deef",
        "username": "mary.jackson@example.com",
        "profile": {
            "firstName": "Mary",
            "middleName": "",
            "lastName": "Jackson",
            "nickname": "Hail Mary",
            "zip": "23666",
            "email": "mary.jackson@example.com",
            "homePhone": "514-555-1212",
            "mobilePhone": "514-555-4321",
            "workPhone": "514-555-1234",
            "addressLine1": "1281 Peachtree Rd",
            "addressLine2": "Apt 23",
            "city": "Hampton",
            "state": "VA",
            "photoUrl": "http://example.com/photo/9e8324ab",
            "thumbnailUrl": "http://example.com/thumb/32ab4c58",
            "education": "MS",
            "timezone": -8
        },
        "emailVerified": false
    },
    "sessionToken": "{{sessiontoken}}"
}
```



### Login with federated credentials

Logs into the application with user credentials from a third-party identity provider or social network.

Each tenant must be configured with keys for each supported identity provider.

<br/>

If enabled, the system checks the policy governing the _maximum number of failed login attempts_.
When the call is successful, the user's credentials are validated and the call returns a session token.

<br>

#### Body Parameters
|Field			|Type	|Required	|Description	|
|---			|---	|---		|---			|
|accessToken	|string	|required	|UID for the user's account.|
|requestToken	|string	|required	|UID for the user's account.|
|tokenVerifier	|string	|required	|Signature timestamp for this request.|
|tokenSecret	|string	|required	|Secret UID signature for the user's account.|
|provider		|string	|required	|Short name for the identity provider or social network.|

<br>

#### Error Responses

|HTTP Code|Error Code|Description
|---|---|---|
|**400**|1050|*Bad request:* Malformed request body|
|**404**|1041|*Not found:* User does not exist with specified username|
|**403**|1411|*Forbidden:* Account locked out |

<br>

The following use case describes how to log in to Orbis and create an associated Orbis account, if necessary.

1. First, the web or mobile app initiates a login with Gigya (the identity provider), using [Registration-as-a-Service](https://developers.gigya.com/display/GD/OAuth+2.0+Compliant+REST+API); see _Use Case 2 - Direct Server-to-Server Flow_. This generates a Gigya User object, which provides data fields for the Orbis login.

2. From the User structure, Orbis requires UID, UIDSignature, and SignatureTimestamp to validate the login information. The web/mobile app then generates a POST to /oam/v1/user/network with the Gigya credentials:

	```json
	POST /oam/v1/users/network
	Authorization: Bearer <api-token>
	Content-Type: application/json
	{
	    "accessToken":   user.UID,
	    "requestToken":  user.UID,
	    "tokenVerifier": user.SignatureTimestamp,
	    "tokenSecret":   user.UIDSignature,
	    "provider":      "gigya",
	}
	```

3. Orbis uses this data to validate the request. If the user account (with the matching Gigya UID) has already been registered, then an Orbis session token is generated to provide access to other Orbis systems.

4. If the Gigya UID has not been registered, Orbis queries Gigya to get a few user details (only enough to support identifying customers to resolve support issues), which are used to create a Orbis account. An Orbis session token is then generated for the newly registered account and returned to the web/mobile app:

	```
	200 OK
	{
	    uid: "4321-abcd-9876-fedc",
	    username: "mary.jackson@example.com",
	    profile: {
	        firstName: "Mary",
	        lastName: "Jackson",
	        email: "mary.jackson@example.com"
	    }
	}
	```

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/user/network
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "accessToken": "an-access-token",
    "requestToken": "a-request-token",
    "tokenVerifier": "verifier",
    "tokenSecret": "secret",
    "provider": "Twitter"
}
```



### Register federated account

Registers an account by associating an external identifier with a login provider. 

<br>

Some workflows, such as billing, require an Orbis UID to exist before an access token can be generated for an account.
This endpoint enables such workflows for new accounts. Note that calling this endpoint is not a prerequisite for using the `/oam/v1/user/network` or `/oam/v2/user/network` endpoints.

<!--  Original text:
Registers an account associating an exernal identifier with a login provider.  The intent is to enable new account workflows which
require an Orbis UID to exist, such as for billing purposes, before an access token can be generated.  The use of this endpoint is not 
a prerequisite to the use of /oam/v1/user/network or /oam/v2/user/network
-->

<br>

#### Body Parameters
|Field			|Type	|Required	|Description	|
|---			|---	|---		|---			|
|externalID  	|string	|required	|Account identifier registered with the identity provider, such as an email address. |
|provider		|string	|required	|Short name for the identity provider or social network.|

<br>

#### Error Responses

|HTTP Code|Error Code|Description
|---|---|---|
|**400**|1050|*Bad request:* Malformed request body, or unknown provider |

<br>

The following use case describes how to use the social registration endpoint

1. Registration controller registers an account:

	```json
	POST /oam/v1/users/network/create
	Authorization: Bearer <session-token>
	Content-Type: application/json
	{
	    "externalID":   "claims.subject@example.com",
	    "provider":     "forgerock"
	}
	```

2. If a matching account does not exist, an account will be registered, which includes a uid:

	```
	201 OK
	{
	    "uid": "4321-abcd-9876-fedc",
		"socialuid": "claims.subject@example.com",
		"userType":"forgerock"
	}
	```
If the account already exists, you will receive the existing account.

3. Create subscription, etc. using the uid.
4. Call `POST /oam/v2/users/network` from the user's device to log in and get a session token.

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/user/network/create
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "externalID": "claims.subject@example.com",
    "provider": "forgerock"
}
```



### Renew session token


Takes an existing session token, then requests a new one with the renewal process.


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v1/user/tokens
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Renew session token (failure) | Code: 0



```js
{
    "requestID": "a86977cb-ec39-4427-9d8a-cb77e009de4f",
    "timestamp": "2020-02-14T23:58:42.246468177Z",
    "errorMessage": "Unauthorized"
}
```



Status: Renew session token (success) | Code: 0



```js
{
    "requestID": "6fc1acaf-7039-4cff-9327-534d7572b9ce",
    "timestamp": "2020-02-14T23:59:16.351734476Z",
    "sessionToken": "eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoic2Vzc2lvbiIsInVpZCI6ImE3OWFlMTkzLTdkYzQtNDFlMS1hNzBhLTZkMTU3M2IyM2RiMiIsImFub24iOmZhbHNlLCJwZXJtaXNzaW9ucyI6bnVsbCwiYXBpS2V5IjoiOWQxOWIzZWQtYzA1Zi00ZTBjLWEzMzgtNDE4NzA1MTAwZGEzIiwicmVnaW9ucyI6WyI3NDU2OGE1MC0xMjkxLTQ2NDMtYjI3ZC0wNTJlMjQ5YTRhMTMiLCIwODMyOWUxMC1jMjc0LTExZTgtOWIwNi00ZDhhNDExZjU1YTEiLCI5NmFmOGMwMC1mYTQzLTExZTgtYmExNC0yN2IyNGM5Y2IwMjQiLCJjNjRmZDE0Yy1kM2VlLTRlNjQtYTM3Zi03ODI4NzU2YjA3MjEiLCIxNGI5OWRhZi0yODliLTRhYTEtODAxNy00YTkxYWZhZDAwNmIiXSwiZXhwIjoxNTgxNzI4MzU2LCJpYXQiOjE1ODE3MjQ3NDksImlzcyI6Ik9yYmlzLU9BTS1WMSIsInN1YiI6ImE3OWFlMTkzLTdkYzQtNDFlMS1hNzBhLTZkMTU3M2IyM2RiMiJ9.yP_FBKgtnSM4LVIbTeRyHgIeTfFda78VkH0pzTrkUeJ8DpsnxUT2SSJEYMipNgqTwi904DQNp67u4u9WZZRFDg"
}
```



### Retrieve account info


Returns detailed account and profile data for the current user ID. Requires a session token.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OAMServer}}/oam/v1/user/accounts
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Get Account Info | Code: 200



```js
{
    "requestID": "1db445f0-5b0d-4c39-9aa0-261ef6d00a91",
    "timestamp": "2017-11-22T16:56:32.153710919Z",
    "account": {
        "uid": "f14c2fd7-a895-4e31-b930-ced91ff9deef",
        "username": "mary.jackson@example.com",
        "profile": {
            "firstName": "Mary",
            "middleName": "",
            "lastName": "Jackson",
            "nickname": "Hail Mary",
            "zip": "23666",
            "email": "mary.jackson@example.com",
            "homePhone": "514-555-1212",
            "mobilePhone": "514-555-4321",
            "workPhone": "514-555-1234",
            "addressLine1": "1281 Peachtree Rd",
            "addressLine2": "Apt 23",
            "city": "Hampton",
            "state": "VA",
            "photoUrl": "http://example.com/photo/9e8324ab",
            "thumbnailUrl": "http://example.com/thumb/32ab4c58",
            "education": "MS",
            "timezone": -8
        },
        "emailVerified": false
    }
}
```



### Retrieve account info (admin)

Returns detailed account and profile data for the specified user ID, including login history, transactions, and entitlements. 
Requires administrative privileges.

<br/>

#### Path Parameters
|Label	|Type	|Required |Description	|
|---	|---	|---		|---		|
|userid| string |required	|The UID for the user account.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OAMServer}}/oam/v1/admin/accounts/{{userid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### Update account info

Updates the specified fields within an account. Can also update custom data fields, if they have been configured for the tenant.

<br/>

<!--
#### Body Parameters

|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|userID	|string |required	|ID of the user to be added to the role.|

Question: Shouldn't there be a UUID as a key field somewhere so that we know we are updating the right user?


  "firstName": "Mary",
    "middleName": "",
    "lastName": "Jackson",
    "nickname": "Hail Mary",
    "zip": "23666",
    "email": "mary.jackson@example.com",
    "homePhone": "514-555-1212",
    "mobilePhone": "514-555-4321",
    "workPhone": "514-555-1234",
    "addressLine1": "1281 Peachtree Rd",
    "addressLine2": "Apt 23",
    "city": "Hampton",
    "state": "VA",
    "photoUrl": "http://example.com/photo/9e8324ab",
    "thumbnailUrl": "http://example.com/thumb/32ab4c58",
    "education": "MS",
    "timezone": -8,
    "customData": 
   	{"preferences" : 
    	{"language": 
    		{"client": "batman", "audio": "robin", "subtitles": "joker"}
    	}
   	}
}

<!-- EPC: testable? -->


#### Use Case: Custom Data Schema

Given a tenant custom data schema such as:

```    
database=tenant polices.custom_data.schema:{  
   "title":"Tenant A Custom Data Schema",
   "type":"object",
   "additionalProperties":false,
   "properties":{  
      "preferences":{  
         "type":"object",
         "additionalProperties":false,
         "properties":{  
            "language":{  
               "type":"object",
               "additionalProperties":false,
               "properties":{  
                  "client":{  
                     "type":"string",
                     "minLength":1
                  },
                  "audio":{  
                     "type":"string",
                     "minLength":1
                  },
                  "subtitles":{  
                     "type":"string",
                     "minLength":1
                  }
               }
            }
         }
      }
   }
}
```
<br>
    
You could use this endpoint to update the following language fields for a user account:
```
"customData": {
	"preferences" : {
    	"language": 
    		{"client": "batman", "audio": "robin", "subtitles": "joker"}
    }
}
```
<br>

Note, however, that because the custom data schema specifies '"additionalProperties": false', you cannot add fields that the schema does not already specify. The following request would generate an error, because the "FOO" field is not specified in the schema:
```
"customData": {
    "preferences" : {
    	"language": 
    		{"client": "batman", "audio": "robin", "subtitles": "joker", "FOO": "bar"}
    }
}
```


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v1/user/accounts
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "firstName": "Mary",
    "middleName": "",
    "lastName": "Jackson",
    "nickname": "Hail Mary",
    "zip": "23666",
    "email": "mary.jackson@example.com",
    "homePhone": "514-555-1212",
    "mobilePhone": "514-555-4321",
    "workPhone": "514-555-1234",
    "addressLine1": "1281 Peachtree Rd",
    "addressLine2": "Apt 23",
    "city": "Hampton",
    "state": "VA",
    "photoUrl": "http://example.com/photo/9e8324ab",
    "thumbnailUrl": "http://example.com/thumb/32ab4c58",
    "education": "MS",
    "timezone": -8,
    "customData": {
    	"preferences" : {
    		"language": {
    			"client": "es",
    			"audio": "es",
    			"subtitles": "en"
    		}
    	}
   	}
}
```



***Responses:***


Status: Update Account Info | Code: 401



```js
{
    "requestID": "e997b88d-a548-4319-8158-d92772441b57",
    "timestamp": "2017-11-22T16:57:00.987509247Z"
}
```



### Update account info (admin)

Updates the specified fields within the target account. Can also update custom data fields, if they have been configured for the tenant.

Requires administrative privileges.

<br/>

#### Path Parameters
|Label	|Type	|Required |Description	|
|---	|---	|---		|---		|
|userid| string |required	|The UID for the user account.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v1/admin/accounts/{{userid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "customData": { "commerce": {"rwcVoucherRefund" : true} }
}
```



### Request password reset

Allows an account owner to reset their password. 

This endpoint creates a reset password link and then sends the link to the 
verified email address for the account. 
The created link contains a Reset Password Token as a query parameter. 
See [Confirm password reset](https://docs.dtc.istreamplanet.net/#573288e6-6e16-4fdd-a98a-b924b1980e06) 
for details.

<br>

#### Body Parameters

|Field	|Type	|Required	|Description|
|---	|---	|---		|---		|
|email	|string |required	|Account's verified email address.|	

<br>

#### Password Validation
For detailed information on password validation, see the description in [Create account](https://docs.dtc.istreamplanet.net/#65c143f7-83af-4ca6-84f3-990ecd2c9f11).

<br/>

#### Error Responses

|HTTP Code|Error |Description
|---|---|---|
|**400**|1050|*Bad request*: Malformed request body|
|**403**|1411|*Forbidden*: Account locked out |
|**404**|1041|*Not found*: Account does not exist with specified username|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/user/accounts/password/reset
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "email": "mary.jackson@example.com"
}
```



### Confirm password reset

Accepts the password reset link that was sent to the account email address
by the 
[Request password reset](https://docs.dtc.istreamplanet.net/#23f0befe-9b41-4861-8668-923eafbd18f2) endpoint. 

<!-- Question: password reset token appears in the Body as well as in the endpoint call? -->
   
<br>

#### Body Parameters
|Field	|Type	|Required	|Description|
|---	|---	|---		|---		|
|newPassword	|string |required	|New replacement password for the account.|	
|resetToken	|string |required		|Reset token generated by the RequestPasswordReset call.|

<br>

#### Password Validation
For detailed information on password validation, see the description in [Create account](https://docs.dtc.istreamplanet.net/#65c143f7-83af-4ca6-84f3-990ecd2c9f11).


<br/>

#### Error Responses

|HTTP Code|Error |Description
|---|---|---|
|**400**|1050|*Bad request*: Malformed request body|
|**422**|1048|*Unprocessable entity*: New password failed validation|

<br/>

<!-- 
|1048   |422        |New password failed validation

|**400**|1042|*Password mismatch*|
|**403**|1411|*Forbidden*: Account locked out |
|**404**|1041|*Not found*: User does not exist with specified username|
-->

<!--

#### Response Body Description
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
URL: {{OAMServer}}/oam/v1/user/accounts/password/reset/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| resetToken | ${passwordResetToken} | Generated reset token. Required. |



***Body:***

```js        
{
  "newPassword" : "newPassword",
  "resetToken" : "resetTokenFromPasswordResetCall"
}
```



### Change password

Permits logged in account owners to change their password.

<br/>

#### Body Parameters

|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|currentPassword	|string |required	|Current (old) password for the account.|
|newPassword		|string |required	|New replacement assword for the account.|

<br/>

#### Password validation
For detailed information on password validation, see the description in [Create account](https://docs.dtc.istreamplanet.net/#65c143f7-83af-4ca6-84f3-990ecd2c9f11).

<br/>

#### Error Responses

|HTTP Code|Error |Description
|---|---|---|
|**400**|1050|*Bad request*: Malformed request body|
|**400**|1042|*Password mismatch*|
|**403**|1411|*Forbidden*: Account locked out |
|**404**|1041|*Not found*: Account does not exist with specified username|
|**422**|1048|*Unprocessable entity*: New password failed validation|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v1/user/accounts/password
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "currentPassword": "oldPassword",
  "newPassword": "newPassword"
}
```



### Request email verification

Sends an email verification link to the email address for the account. The email verification token is attached to the URL via the query string parameter, __verifyEmailToken__, as seen in the [Confirm email verification](https://docs.dtc.istreamplanet.net/?version=latest#2f206456-d9cd-488c-8329-8d75dad89d8e) endpoint.

<br>

#### Option to Convert a __verify Email Token__ to a __Session Token__
* For any given account, the *first* call to this endpoint can optionally pass the __verifyEmailToken__ to the [Confirm email verification](https://docs.dtc.istreamplanet.net/?version=latest#2f206456-d9cd-488c-8329-8d75dad89d8e) endpoint and exchange it for a session token.
* See the [Confirm email verification](https://docs.dtc.istreamplanet.net/?version=latest#2f206456-d9cd-488c-8329-8d75dad89d8e) endpoint for details.


<br/>

#### Body Parameters

|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|email	|string |required	|Email address to be verified for the account.|


#### Returns 200

```
200 OK
{
  requestID: "...",
  timestamp: "...",
  message: "Verification code has been sent to your email account"
}
```

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/user/email/verify
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "email": "mary.jackson@example.com"
}
```



***Responses:***


Status: Update Account Info | Code: 401



```js
{
    "requestID": "e997b88d-a548-4319-8158-d92772441b57",
    "timestamp": "2017-11-22T16:57:00.987509247Z"
}
```



### Confirm email verification

Confirms that an email address has been verified.

The tenant can optionally configure this endpoint to return a __SessionToken__ to the account owner. 
* If so configured, the *FIRST* call to this endpoint for a given __verifyEmailToken__ returns a __SessionToken__. 
* Subsequent calls to this endpoint with the same __verifyEmailToken__ will return an HTTP 400 Status Error Code.
* The link to this endpoint (and the Verify Email Token) was generated by the [Request email verification](https://docs.dtc.istreamplanet.net/?version=latest#62385364-75f3-4952-a9a7-0cd46f084b26) endpoint.

<br/>

#### Returns 200

```
200 OK
{
  requestID: "...",
  timestamp: "...",
  message: "Your email has been verified",
}
```


```
200 OK
{
  requestID: "...",
  timestamp: "...",
  message: "Your email has been verified",
  sessionToken: "a-valid-session-token-here"
}
```


<!-- 

#### Response Body Description
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
URL: {{OAMServer}}/oam/v1/user/email/verify
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| verifyEmailToken | {{verifyEmailToken}} | Optional. Email verification security token for the user account.  |



***Responses:***


Status: Update Account Info | Code: 401



```js
{
    "requestID": "e997b88d-a548-4319-8158-d92772441b57",
    "timestamp": "2017-11-22T16:57:00.987509247Z"
}
```



### List all matching accounts

Returns any accounts matching a string or regular expression (regex) in the firstname, lastname, email, or username fields.  

<br/>

#### Body Parameters

|Field    |Type  |Required  |Description  |
|---    |---  |---    |---      |
|match    |string  |required  |Regex or string to match. Use ".*" to return all accounts.  If a '+' exists in a match string, precede it with '\\\\' to escape the sequence.|
|sort    |string  |required  |Sorts the list of accounts on the specified field; for example: `profile.username`.<br>For reverse order, prefix the value with a minus '-'; for example: `-profile.email`.|
|page    |integer|required  |The number of output pages to skip over (default 0).|
|pagesize  |integer|optional  |Maximum number of items to return per page/call (default 20).|

<br>


<!-- response

| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.

<br>

-->

#### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested data|

<!--|404		|1040				|*Not Found*: No matching station ID found|-->

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/admin/accounts/search
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "match": ".*",
    "sort": "created",
    "page": 0,
    "pagesize": 1000
}
```



***Responses:***


Status: Search users for "mary" | Code: 200



```js
{
    "requestID": "f0272c92-36a5-47c9-b01b-5c41dc6d3496",
    "timestamp": "2017-11-22T16:38:41.515394063Z",
    "count": 1,
    "totalCount": 1,
    "results": [
        {
            "uid": "6511b1c6-a595-4e1c-ae95-fda8528a63f9",
            "username": "mary.jackson@example.com",
            "profile": {
                "firstName": "Mary",
                "middleName": "",
                "lastName": "Jackson",
                "nickname": "Hail Mary",
                "zip": "23666",
                "email": "mary.jackson@example.com",
                "homePhone": "514-555-1212",
                "mobilePhone": "514-555-4321",
                "workPhone": "514-555-1234",
                "addressLine1": "1281 Peachtree Rd",
                "addressLine2": "Apt 23",
                "city": "Hampton",
                "state": "VA",
                "photoUrl": "http://example.com/photo/9e8324ab",
                "thumbnailUrl": "http://example.com/thumb/32ab4c58",
                "education": "MS",
                "timezone": -8
            },
            "emailVerified": false
        }
    ]
}
```



### Disable / enable account

Sets the specified account as *disabled* or *active*. 

<br>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|userID |string |required	|ID for the target account to be enabled or disabled.|

<br>

#### Body Parameters
|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|status	|string	|required	|Sets the account status; supported values are *disabled* and *active*.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target account.|
|404		|1040	|*Not Found*: Target account not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v1/accounts/status/{{userid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user session token to authenticate request |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "status": "disabled"
}
```



***Responses:***


Status: Disable Account | Code: 200



```js
{
    "requestID": "d70bcd36-c22b-4f3e-a9c1-802015abdffd",
    "timestamp": "2019-11-25T08:11:41.390633Z",
    "account": {
        "_id": "5ddb867f13d743dbb161aff2",
        "createTime": "2019-11-25T07:45:03.841Z",
        "uid": "f018f08c-b8c2-4e8c-81a1-ec1a1142efce",
        "username": "user@gmail.com",
        "roles": [],
        "profile": {
            "firstName": "User",
            "lastName": "Name",
            "email": "user@gmail.com",
            "timezone": 0,
            "iso2country": "US"
        },
        "emailVerified": false,
        "customData": {},
        "devices": [],
        "userType": "ott",
        "status": "disabled"
    }
}
```



Status: Activate Account | Code: 200



```js
{
    "requestID": "bf627fc9-3e02-495e-a5e2-66384939f3aa",
    "timestamp": "2019-11-25T08:09:35.927848Z",
    "account": {
        "_id": "5ddb867f13d743dbb161aff2",
        "createTime": "2019-11-25T07:45:03.841Z",
        "uid": "f018f08c-b8c2-4e8c-81a1-ec1a1142efce",
        "username": "user@gmail.com",
        "roles": [],
        "profile": {
            "firstName": "User",
            "lastName": "Name",
            "email": "user@gmail.com",
            "timezone": 0,
            "iso2country": "US"
        },
        "emailVerified": false,
        "customData": {},
        "devices": [],
        "userType": "ott",
        "status": "active"
    }
}
```



### Delete an account

Deletes the specified user account. 

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|userid| string | _required_| The UID for the user account.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the specified user account.|
|404		|1040	|*Not Found*: No matching user ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OAMServer}}/oam/v1/admin/accounts/{{userid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Delete an account | Code: 0



```js
{
    "requestID": "65a1bf7a-bc58-4492-a010-1402fe3a863b",
    "timestamp": "2019-12-16T20:26:42.848115661Z"
}
```



### List all permissions


Retrieves the list of permissions that tenants can assign to roles, Web Portal members, and subscribers.

<br>

NOTE: Permissions marked with an asterisk<sup>*<sup> can be applied to subscriber accounts in the client application. All other permissions can be applied to Portal users.

<br>

|Permission Name    |Description    |
|---                |---
|allow-any-geolocation<sup>*<sup>  |Subscriber can acquire enititlement regardless of location.|
|bypass-device-limit<sup>*<sup>   |Subscriber can override device registration limits.|
|create-content     |Create assets.|
|delete-content     |Delete assets.|
|ignore-entitlement-checks<sup>*<sup> |Subscriber can watch any asset.|
|ignore-stream-limits<sup>*<sup> |Subscriber can watch any number of streams simultaneously.|
|manage-appconfigs |View, add, change and delete client application configurations.|
|manage-billingplans	|Add, update and delete billing plans.|
|manage-carousel    	|Curate content carousel.|
|manage-categories  	|Add and delete categories.|
|manage-entitlements	|Grant, update and delete user entitlements.|
|manage-feeds       	|Add and delete MRSS feed subscriptions.|
|manage-notifications   |Add web subscription to asset change notifications.|
|manage-packages    	|Add/update packages.|
|manage-permissions 	|Add, update, delete and list permissions.|
|manage-policies    	|Update tenant policies.|
|manage-products    	|Add, change and delete products.|
|manage-regions			|Add, change and delete geographic regions.|
|manage-roles       	|Add, update, delete and list roles.|
|manage-subscriptions   |Validate a subscription. Cancel a subscription.|
|manage-user-roles  	|Add users to roles, remove users from roles, list users in role.|
|manage-users       	|Delete users.|
|publish-content    	|Publish assets.|
|read-permissions   	|List permissions.|
|read-subscriptions 	|Get a user's subscriptions (other than the calling user).|
|read-userdetails   	|Read user profiles (other than the calling user), search users.|
|refund             	|Refund a credit card transaction.|
|update-content     	|Update asset properties.|
|update-content-streams	|Update asset stream URL properties.|
|view-entitlements  	|Get entitlements for a user (other than the calling user). <br>Get user entitlements to a package (other than the calling user). <br>Get user entitlements to specific assets (other than the calling user).|
|view-monitoring      	|Monitor system metrics. (Not available for all installations.)|
|view-policies      	|View tenant policies.|
|view-unpublished-content   |Read private assets and get private assets associated with public assets.|
|write-userdetails  	|Update user profiles (other than the calling user).|

<br>

<!--
NOTE: The all-tenants permission does not appear in this list because it is only available within iStreamPlanet.
-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OAMServer}}/oam/v1/permissions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Get all permissions | Code: 200



```js
{
    "requestID": "f01c6cab-8f71-488c-b31a-bc0fdcfdda2d",
    "timestamp": "2018-07-30T23:51:40.38114169Z",
    "permissions": [
        {
            "name": "allow-any-geolocation",
            "description": "Allow enititlement request regardless of user location"
        },
        {
            "name": "create-content",
            "description": "Create assets."
        },
        {
            "name": "delete-content",
            "description": "Delete assets."
        },
        {
            "name": "manage-billingplans",
            "description": "Add, update and delete billing plans."
        },
        {
            "name": "manage-carousel",
            "description": "Curate content carousel"
        },
        {
            "name": "manage-categories",
            "description": "Add and delete categories."
        },
        {
            "name": "manage-entitlements",
            "description": "Grant, update and delete user entitlements."
        },
        {
            "name": "manage-feeds",
            "description": "Add and delete MRSS feed subscriptions."
        },
        {
            "name": "manage-notifications",
            "description": "Add web subscription to asset change notifications."
        },
        {
            "name": "manage-packages",
            "description": "Add/update packages."
        },
        {
            "name": "manage-permissions",
            "description": "Add, update, delete and list permissions."
        },
        {
            "name": "manage-policies",
            "description": "Update tenant policies."
        },
        {
            "name": "manage-products",
            "description": "Add, change and delete products"
        },
        {
            "name": "manage-roles",
            "description": "Add, update, delete and list roles."
        },
        {
            "name": "manage-subscriptions",
            "description": "Validate a subscription. Cancel a subscription."
        },
        {
            "name": "manage-user-roles",
            "description": "Add users to roles, remove users from roles, list users in role."
        },
        {
            "name": "manage-users",
            "description": "Delete users"
        },
        {
            "name": "publish-content",
            "description": "Publish assets."
        },
        {
            "name": "read-permissions",
            "description": "List permissions."
        },
        {
            "name": "read-subscriptions",
            "description": "Get a user's subscriptions (other than the calling user)."
        },
        {
            "name": "read-userdetails",
            "description": "Read user profiles (other than the calling user), search users."
        },
        {
            "name": "refund",
            "description": "Refund a credit card transaction."
        },
        {
            "name": "update-content",
            "description": "Update asset properties."
        },
        {
            "name": "view-entitlements",
            "description": "Get entitlements for a user (other than the calling user). Get user entitlements to a package (other than the calling usr). Get user entitlements to specific assets (other than the calling user)."
        },
        {
            "name": "view-policies",
            "description": "View tenant policies."
        },
        {
            "name": "view-unpublished-content",
            "description": "Read private assets and get private assets associated with public assets."
        },
        {
            "name": "write-userdetails",
            "description": "Update user profiles (other than the calling user)."
        }
    ]
}
```



### Add a user to a role

Adds the current user (specified in the Body) to the role specified in the Path.

<br/>

#### Path Parameters

|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|role	|string |required	|Name of the target role.|

<br/>

#### Body Parameters

|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|userID	|string |required	|ID of the user to be added to the role.|

<!-- EPC: testable? -->

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/roles/{{role}}/users
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "userID": "{{userid}}"
}
```



### Create a role

Creates a new role which can be assigned to administrators.

<br/>

#### Body Parameters

|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|name	|string |required	|Name of the new role.|
|description	|string |required	|Description of the new role.|
|permissions	|string |required	|List of permissions for the new role.|

<br/>

<!-- EPC: testable? -->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v1/roles
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "name": "developer",
  "description": "Orbis developer",
  "permissions": [
  	"run-code",
  	"view-code"
  ]
}
```



### Update a role

Updates the description and list of permissions that define the specified role.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|role	|string |required	|Name of the role to be updated.|

<br/>

#### Body Parameters
|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|description	|string |optional	|Updated description for the role.|
|permissions	|string |optional	|Updated list of permissions for the target role.|

<br/>
<!-- EPC: testable? -->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v1/roles/{{role}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "description": "Orbis developer",
  "permissions": [
    "run-code",
    "view-code"
  ]
}
```



### List all roles


Retrieves a list of all current roles, including their associated descriptions and permissions.

<br>

The following roles are predefined for all system installations.

|Role				|Description    	|
|---           		|---				|
|Administrator		|All permissions.	|
|ContentEditor    	|Create, publish, update and delete assets.|
|CustomerService   	|Manage users and their details, subscriptions and entitlements.|
|PackageManager    	|Add, update and delete packages.|
|PricingManager  	|Add, update and delete billing plans and products.|
|UserManager		|View, update and delete users.|


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OAMServer}}/oam/v1/roles
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### List all users in a role

Retrieves all members of the specified role.  A user may belong to multiple roles simultaneously.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|role	|string |required	|Name of the target role.|

<br/>

<!-- EPC: testable? -->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OAMServer}}/oam/v1/roles/{{role}}/users
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### Remove a user from a role

Removes the specified user from the target role.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|role	|string |required	|Name of the target role.|
|userid	|string |required	|ID of the user to be removed from the target role.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified user from the target role.|
|404		|1040	|*Not Found*: No matching target role found.|
|404		|1041	|*Not Found*: No matching user ID found.|

<br/>

<!-- EPC: testable? -->


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OAMServer}}/oam/v1/roles/{{role}}/users/{{userid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### Delete a role

Deletes the specified role from those available to be assigned to administrators.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|role	|string |required	|Name of the role to be deleted.|

<br/>


#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target role.|
|404		|1040	|*Not Found*: No matching target role found.|

<br/>

<!-- EPC: testable? -->


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OAMServer}}/oam/v1/roles/{{role}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



## Accounts - v2


### Create account with device ID

Creates a new account from the provided user information and device ID. The device ID is checked to ensure that the user is not logging in from more devices than allowed by tenant policy. If successful, a session token is returned.

<br>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|username		||string	|required	|Username/email address for the subscriber's account.|
|password		||string	|required	|Password for the subscriber's account.|
|deviceID		||string	|required	|Unique ID for the subscriber's device.|
|regCode		||string	|			|Device registration code.|
|deviceName		||string	|			|Descriptive name for the subscriber's device.	|
|deviceCategory ||string	|			|General device type. Must be one of: computer \| connected \| mobile|
|computerDevice	||string	|			|Computer software subtype. Must be one of: browser \| app|
|browserName	||string	|			|Browser name. Must be one of: chrome \| firefox \| ie \| safari \| opera \| other|
|browserVersion	||string	|			|Browser version.	|
|connectedDevice||string	|			|Connected device subtype. Must be one of: roku \| smarttv \| tyzen \| lg \| xbox \| playstation|
|mobileDevice	||string	|			|Mobile device subtype. (i = Apple; a = Android). Must be one of: iphone \| ipad \| aphone \| atablet|
|osName			||string	|			|OS running on the device. Must be one of: mac \| windows \| linux \| bsd \| android \| other|
|osVersion		||string	|			|Current version of the primary OS running on the device. |
|clientAppName	||string	|			|Name of the client application installed on the device.		|
|clientAppVersion||string	|		|Current version of the client application installed on the device.	|
|`profile`	|	|object	|required	|Username/email address for the subscriber's account.|
|firstName	|`profile`	|string	|required	|Subscriber's firstname.|
|lastName	|`profile`	|string	|required	|Subscriber's lastname.|
|email		|`profile`	|string	|required	|Email address for the subscriber's account.|
|timezone	|`profile`	|integer	|required	|Timezone offset from UTC for the subscriber's location.|

<br/>


<!--

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|username	|	|string	|required	|Username/email address for the user's account.|
|password	|	|string	|required	|Password for the user's account.|
|deviceID	|	|string	|required	|Unique ID for the user's device.|
|`profile`	|	|object	|required	|Username/email address for the user's account.|
|firstName	|`profile`	|string	|required	|User's firstname.|
|lastName	|`profile`	|string	|required	|User's lastname.|
|email		|`profile`	|string	|required	|Email address for the user's account.|
|timezone	|`profile`	|integer	|required	|Timezone offset from UTC for the user's location.|

-->

#### Password validation
The password is validated based on the tenant's password validation policy. 

The following independent dimensions are validated when their corresponding policies are turned on.

* **Password minimum length:**
Always validated. Default is 6 characters. If fails, returns the error message: "Password minimum length is 6"

* **Digit is present:**
Default is off. If turned on and fails, returns the error message "Digit is required"

* **Lower case character is present:**
Default is off. If turned on and fails, returns the error message "Lower case character is required"

* **Upper case character is present:**
Default is off. If turned on and fails, returns the error message "Upper case character is required"

* **Special character is present:**
Default is off. If turned on and fails, returns the error message "Special character is required: " and displays the list of supported characters: __, ) ~ _ % ^ # } ? { [ ] / @ ! $ : . ( - | + ' *__

<br/>

#### Password validation failure
When password validation fails, the call returns HTTP status `422` with error code 1048: "New password failed validation". Error messages for all failed conditions are concatenated in the same response. See the example "Create account - password validation failed".

<br/>

#### Error Responses

|HTTP Code|Error |Description
|---|---|---|
|**400**|1050|*Bad request*: Malformed request body|
|**422**|1048|*Unprocessable entity*: New password failed validation|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/user/accounts
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "username": "mary.jackson@example.com",
    "password": "password",
    "deviceID": "{{deviceID}}",
    "regCode": "{{regCode}}",
    "profile": {
        "firstName": "Mary",
        "lastName": "Jackson",
        "email": "mary.jackson@example.com",
        "timezone": -8
    },
    "deviceName": "deviceName",
    "deviceCategory": "computer",
    "computerDevice": "browser",
    "browserName": "chrome",
    "browserVersion": "chrome-version-number",
    "connectedDevice": "roku",
    "mobileDevice": "aphone",
    "osName": "android",
    "osVersion": "primary-OS",
    "clientAppName": "app-name",
    "clientAppVersion": "Current app version"
}
```



***Responses:***


Status: Create account - password validation failed | Code: 400



```js
{
    "requestID": "0ca05895-07bd-44a6-b241-259b29c93a6f",
    "timestamp": "2018-03-23T21:55:45.307075357Z",
    "errorCode": 1048,
    "errorMessage": "Password minimum length is 6. Digit is required. Upper case character is required. Special character is required: @ ! ? { [ ] / | + ' $ : . ( - * % ^ , ) ~ _ # } "
}
```



Status: Create account with deviceID (success) | Code: 201



```js
{
    "requestID": "f0272c92-36a5-47c9-b01b-5c41dc6d3496",
    "timestamp": "2017-11-22T16:38:41.515394063Z",
    "deviceID": "{{deviceID}}",
    "account": {
        "uid": "6511b1c6-a595-4e1c-ae95-fda8528a63f9",
        "username": "mary.jackson@example.com",
        "profile": {
            "firstName": "Mary",
            "middleName": "",
            "lastName": "Jackson",
            "nickname": "Hail Mary",
            "zip": "23666",
            "email": "mary.jackson@example.com",
            "homePhone": "514-555-1212",
            "mobilePhone": "514-555-4321",
            "workPhone": "514-555-1234",
            "addressLine1": "1281 Peachtree Rd",
            "addressLine2": "Apt 23",
            "city": "Hampton",
            "state": "VA",
            "iso2country":"US",
            "photoUrl": "http://example.com/photo/9e8324ab",
            "thumbnailUrl": "http://example.com/thumb/32ab4c58",
            "education": "MS",
            "timezone": -8
        },
        "emailVerified": false
    },
    "sessionToken": "{{sessiontoken}}"
}
```



### Create anonymous account

Registers an anonymous user with no permissions. Returns the user ID for the user and a session token.

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/anonymous/register
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Register anonymous user | Code: 201



```js
{
    "requestID": "9722e078-a3a1-4128-b84a-a823c03677cd",
    "timestamp": "2018-10-05T17:11:24.396070989Z",
    "account": {
        "uid": "d27588d5-fe49-4b0e-97b8-1e311417ce38",
        "roles": null,
        "profile": {},
        "emailVerified": false,
        "customData": null,
        "devices": null,
        "userType": "anonymous",
        "status": "active"
    },
    "sessionToken": "eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoic2Vzc2lvbiIsInVpZCI6ImQyNzU4OGQ1LWZlNDktNGIwZS05N2I4LTFlMzExNDE3Y2UzOCIsImFub24iOnRydWUsInBlcm1pc3Npb25zIjpudWxsLCJhcGlLZXkiOiI1MWFmMDA5Ni1jZjQwLTQ1YTItYWNjZi0wMWJiOTFmNTVkNWIiLCJvcmlnaW5hbFRlbmFudCI6IiIsImV4cCI6MTUzODkzMjI4NCwiaWF0IjoxNTM4NzU5NDg0LCJpc3MiOiJPcmJpcy1PQU0tVjEiLCJzdWIiOiJkMjc1ODhkNS1mZTQ5LTRiMGUtOTdiOC0xZTMxMTQxN2NlMzgifQ.Ip81zlVbEmSx0xCm3SAn07hoCUIkA-Dq-ZQIFAEmCs5NKvyIxUFoyZh9QYXyOanqBSW3uq5tYFrJLK_5oTeJ-A"
}
```



### Login with device ID

Takes a username and password, and logs in on the specified device.

<br/>

If enabled, the following tenant policy limits are checked:
* Maximum number of failed login attempts
* Maximum total of registered devices per subscriber account

When successful, the subscriber's credentials are validated and the call returns a session token.

<br/>

#### Body Parameters
|Field		|Type	|Required	|Description	|
|---		|---	|---		|---			|
|username	|string	|required	|Username/email address for the subscriber's account.|
|password	|string	|required	|Password for the subscriber's account.|
|deviceID	|string	|required	|Unique ID for the subscriber's device.|
|regCode	|string	|			|Device registration code.|
|deviceName	|string	|			|Descriptive name for the subscriber's device.	|
|deviceCategory	|string	|		|General device type. Must be one of: computer \| connected \| mobile|
|computerDevice	|string	|		|Computer software subtype. Must be one of: browser \| app|
|browserName	|string	|		|Browser name. Must be one of: chrome \| firefox \| ie \| safari \| opera \| other|
|connectedDevice|string	|		|Connected device subtype. Must be one of: roku \| smarttv \| tyzen \| lg \| xbox \| playstation|
|mobileDevice	|string	|		|Mobile device subtype. (i = Apple; a = Android). Must be one of: iphone \| ipad \| aphone \| atablet|
|osName		|string	|			|OS running on the device. Must be one of: mac \| windows \| linux \| bsd \| android \| other|
|osVersion	|string	|			|Current version of the primary OS running on the device. |
|clientAppName	|string	|		|Name of the app installed on the device.		|
|clientAppVersion	|string	|	|Current app version installed on the device.	|

<br/>

#### Error Responses
|HTTP Code|Error Code|Description
|---|---|---|
|**400**|1050|*Bad request:* Malformed request body|
|**400**|1042|*Password mismatch*|
|**403**|1408|*Forbidden:* User cannot exceed concurrent device limits set by tenant policy |
|**403**|1411|*Forbidden:* Account locked out |
|**404**|1040|*Resource not found*|
|**404**|1041|*Not found:* User does not exist with specified username|

<!-- What error messages may be returned for device ID problems?  -->

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/user/tokens
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "username": "mary.jackson@example.com",
    "password": "password",
    "deviceID": "{{deviceID}}",
    "regCode": "{{regCode}}",
    "deviceName": "deviceName",
    "deviceCategory": "computer",
    "computerDevice": "browser",
    "browserName": "chrome",
    "browserVersion": "chrome-version-number",
    "connectedDevice": "roku",
    "mobileDevice": "aphone",
    "osName": "android",
    "osVersion": "primary-OS",
    "clientAppName": "app-name",
    "clientAppVersion": "Current app version"
}
```



***Responses:***


Status: Login to an Orbis account with a device | Code: 201



```js
{
    "requestID": "68ab1037-d864-4d8e-9657-8d8f7c445b70",
    "timestamp": "2017-11-22T16:50:47.581371495Z",
    "account": {
        "uid": "f14c2fd7-a895-4e31-b930-ced91ff9deef",
        "username": "mary.jackson@example.com",
        "profile": {
            "firstName": "Mary",
            "middleName": "",
            "lastName": "Jackson",
            "nickname": "Hail Mary",
            "zip": "23666",
            "email": "mary.jackson@example.com",
            "homePhone": "514-555-1212",
            "mobilePhone": "514-555-4321",
            "workPhone": "514-555-1234",
            "addressLine1": "1281 Peachtree Rd",
            "addressLine2": "Apt 23",
            "city": "Hampton",
            "state": "VA",
            "photoUrl": "http://example.com/photo/9e8324ab",
            "thumbnailUrl": "http://example.com/thumb/32ab4c58",
            "education": "MS",
            "timezone": -8
        },
        "emailVerified": false
    },
    "sessionToken": "{{sessiontoken}}"
}
```



### Login with federated credentials and device ID

Logs into the platform with user credentials from the specified identity provider or social network.

Each tenant must be configured with keys for each supported identity provider.

<br/>

If enabled, the following tenant policy limits are checked:
* Maximum number of failed login attempts
* Maximum total of registered devices per user account

When successful, the user's credentials are validated and the call returns a session token.

<br/>

#### Body Parameters
|Field			|Type	|Required	|Description	|
|---			|---	|---		|---			|
|accessToken	|string	|required	|UID for the user's account.|
|provider		|string	|required	|Short name for the identity provider or social network.|
|deviceID		|string	|required	|Unique ID for the user's device.|

<br/>

#### Error Responses
|HTTP Code|Error |Description
|---|---|---|
|**400**|1050|*Bad request:* Malformed request body|
|**403**|1408|*Forbidden:* User cannot exceed concurrent device limits set by tenant policy |
|**403**|1411|*Forbidden:* Account locked out |
|**404**|1040|*Resource not found*|
|**404**|1041|*Not found:* User does not exist with specified username|

<!-- What are the error messages that may be returned for device ID problems?  -->

<br/>

The following use case describes how to log in to Orbis and create an associated Orbis account, if necessary.
1. First the web or mobile app initiates a login with Gigya, using [Registration-as-a-Service](https://developers.gigya.com/display/GD/OAuth+2.0+Compliant+REST+API); see _Use Case 2 - Direct Server-to-Server Flow_. This generates a Gigya User object, which provides data fields for the Orbis login.

2. From the User structure, the OAM requires UID, UIDSignature, and SignatureTimestamp to validate the login information. The web/mobile app then generates a POST to /oam/v1/user/network with the Gigya credentials:

	```json
	POST /oam/v1/users/network
	Authorization: Bearer <api-token>
	Content-Type: application/json
	{
	    "accessToken":   user.UID,
	    "requestToken":  user.UID,
	    "tokenVerifier": user.SignatureTimestamp,
	    "tokenSecret":   user.UIDSignature,
	    "provider":      "gigya",
	}
	```

3. OAM uses this data to validate the request. If the user account (with the matching Gigya UID) has already been registered, then an Orbis session token is generated to provide access to other Orbis systems.

4. If the Gigya UID has not been registered, OAM queries Gigya to get a few user details (only enough to support identifying customers to resolve support issues), which are used to create a Orbis account. An Orbis session token is then generated for the newly registered account and returned to the web/mobile app:

	```json
	200 OK
	{
	    uid: "4321-abcd-9876-fedc",
	    username: "mary.jackson@example.com",
	    profile: {
	        firstName: "Mary",
	        lastName: "Jackson",
	        email: "mary.jackson@example.com"
	    }
	}
	```

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/user/network
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "accessToken": "the TVE token",
    "provider": "dtv_latam",
    "deviceID": "{{deviceID}}"
}
```



### Login anonymous account

Logs in to an anonymous account with no permissions using the user ID returned from the creation of an anonymous account.

<br/>

#### Body Parameters

|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|userID| string | required	|Generated UID for the anonymous user account.|

<br/>

#### Error Responses
|HTTP Code|Error Code|Description
|---|---|---|
|**400**|1050|*Bad request:* Malformed request body|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/anonymous/login
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "userID": "{{anonuserid}}"
}
```



***Responses:***


Status: Login anonymous user | Code: 200



```js
{
	"requestID":"3d07f889-c6a9-43a7-857c-0286bfab6b08",
	"timestamp":"2018-09-21T20:21:45.047470012Z",
	"account":
	{
		"createTime":"2018-09-21T20:20:00Z",
		"uid":"62c79890-8796-4b81-a156-f41d5f667061",
		"roles":[],
		"profile":{},
		"emailVerified":false,
		"customData":{},
		"devices":[],
		"userType":"anonymous",
		"status":"active",
		"clientid":"Client ID"
		
	},
		"sessionToken":"eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoic2Vzc2lvbiIsInVpZCI6IjYyYzc5ODkwLTg3OTYtNGI4MS1hMTU2LWY0MWQ1ZjY2NzA2MSIsImFub24iOmZhbHNlLCJwZXJtaXNzaW9ucyI6bnVsbCwiYXBpS2V5IjoiNTFhZjAwOTYtY2Y0MC00NWEyLWFjY2YtMDFiYjkxZjU1ZDViIiwib3JpZ2luYWxUZW5hbnQiOiIiLCJleHAiOjE1Mzc3MzQxMDUsImlhdCI6MTUzNzU2MTMwNSwiaXNzIjoiT3JiaXMtT0FNLVYxIiwic3ViIjoiNjJjNzk4OTAtODc5Ni00YjgxLWExNTYtZjQxZDVmNjY3MDYxIn0.zIYqyvZWL_gHC9UwWoVPsrV6EBZ5Tmza-H9lcaArXlP_t1ltk19zTOPLBrQ24_fGbKEeEHsexTt3q301KHzbhw"
	
}
```



### Convert anonymous account to registered account

Converts an anonymous account to a registered account. 

The request body and password validation parameters are the same as used by the [Create Account](https://docs.dtc.istreamplanet.net/#65c143f7-83af-4ca6-84f3-990ecd2c9f11) endpoint. The user ID will remain the same.

<br>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|username	|	|string	|required	|Username/email address for the user's account.|
|password	|	|string	|required	|Password for the user's account.|
|`profile`	|	|object	|required	|Username/email address for the user's account.|
|firstName	|`profile`	|string	|required	|User's firstname.|
|lastName	|`profile`	|string	|required	|User's lastname.|
|email		|`profile`	|string	|required	|Email address for the user's account.|
|iso2country|`profile`	|string	|required	|ISO 2-letter code for the user's country.|
|timezone	|`profile`	|integer	|required	|Timezone offset from UTC for the user's location.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/anonymous/convert/ott
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "username": "ePresley@example.com",
    "password": "password123!",
    "profile": {
        "firstName": "Elvis",
        "lastName": "Presley",
        "email": "ePresley@example.com",
        "iso2country":"US",
        "timezone": -8
    }
}

```



***Responses:***


Status: Convert anonymous user to OTT user | Code: 200



```js
{
    "requestID": "cea6aaeb-3357-4af3-8da4-3d9d1ea55069",
    "timestamp": "2018-10-05T17:14:59.919850964Z",
    "account": {
        "_id": "5bb79c0be3918d1c3c60ca7e",
        "uid": "76b9e969-3e71-4239-b9a3-82618d516a63",
        "username": "ePresley",
        "roles": [],
        "profile": {
            "firstName": "Elvis",
            "lastName": "Presley",
            "email": "epresley@example.com",
            "timezone": -8,
            "iso2country": "US"
        },
        "emailVerified": false,
        "customData": {},
        "devices": [],
        "userType": "ott",
        "status": "active"
    },
    "sessionToken": "eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoic2Vzc2lvbiIsInVpZCI6Ijc2YjllOTY5LTNlNzEtNDIzOS1iOWEzLTgyNjE4ZDUxNmE2MyIsImFub24iOmZhbHNlLCJwZXJtaXNzaW9ucyI6bnVsbCwiYXBpS2V5IjoiNTFhZjAwOTYtY2Y0MC00NWEyLWFjY2YtMDFiYjkxZjU1ZDViIiwib3JpZ2luYWxUZW5hbnQiOiIiLCJleHAiOjE1Mzg5MzI0OTksImlhdCI6MTUzODc1OTY5OSwiaXNzIjoiT3JiaXMtT0FNLVYxIiwic3ViIjoiNzZiOWU5NjktM2U3MS00MjM5LWI5YTMtODI2MThkNTE2YTYzIn0.ZJdFbgi3K55TiSM2G7IjjFKQ1UD-ZNvlR453QMFS8Ie91MH_O4cXUkpsGhIbMnq5sCXL4xnvbg1RFO9-OU9_MQ"
}
```



### Convert anonymous account to federated (social) account

Convert an anonymous account to a federated (social) account. The user ID will remain the same.

The body of the request is the same as [Login with federated credentials](https://docs.dtc.istreamplanet.net/#aa3727ea-633f-40e9-8649-95ad92117eb5).

<br>

#### Body Parameters
|Field			|Type	|Required	|Description	|
|---			|---	|---		|---			|
|accessToken	|string	|required	|UID for the user's account.|
|requestToken	|string	|required	|UID for the user's account.|
|tokenVerifier	|string	|required	|Signature timestamp for this request.|
|tokenSecret	|string	|required	|Secret UID signature for the user's account.|
|provider		|string	|required	|Short name for the identity provider or social network.|

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/anonymous/convert/federated
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
	"provider": "Gigya",
	"accessToken": "someAccessToken"
}

```



***Responses:***


Status: Convert anonymous user to OTT user | Code: 200



```js
{
    "requestID": "cea6aaeb-3357-4af3-8da4-3d9d1ea55069",
    "timestamp": "2018-10-05T17:14:59.919850964Z",
    "account": {
        "_id": "5bb79c0be3918d1c3c60ca7e",
        "uid": "76b9e969-3e71-4239-b9a3-82618d516a63",
        "username": "ePresley",
        "roles": [],
        "profile": {
            "firstName": "Elvis",
            "lastName": "Presley",
            "email": "epresley@example.com",
            "timezone": -8,
            "iso2country": "US"
        },
        "emailVerified": false,
        "customData": {},
        "devices": [],
        "userType": "ott",
        "status": "active"
    },
    "sessionToken": "eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoic2Vzc2lvbiIsInVpZCI6Ijc2YjllOTY5LTNlNzEtNDIzOS1iOWEzLTgyNjE4ZDUxNmE2MyIsImFub24iOmZhbHNlLCJwZXJtaXNzaW9ucyI6bnVsbCwiYXBpS2V5IjoiNTFhZjAwOTYtY2Y0MC00NWEyLWFjY2YtMDFiYjkxZjU1ZDViIiwib3JpZ2luYWxUZW5hbnQiOiIiLCJleHAiOjE1Mzg5MzI0OTksImlhdCI6MTUzODc1OTY5OSwiaXNzIjoiT3JiaXMtT0FNLVYxIiwic3ViIjoiNzZiOWU5NjktM2U3MS00MjM5LWI5YTMtODI2MThkNTE2YTYzIn0.ZJdFbgi3K55TiSM2G7IjjFKQ1UD-ZNvlR453QMFS8Ie91MH_O4cXUkpsGhIbMnq5sCXL4xnvbg1RFO9-OU9_MQ"
}
```



### Renew session token with deviceID

Takes an existing session token, then requests a new one with the renewal process.

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|**400**	|1410	|*Bad Request*: Attempt to update device or renew device token has failed |
|**403**	|1408	|*Forbidden:* User cannot exceed concurrent device limits set by tenant policy |

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v2/user/tokens
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Renew session token with deviceID (success) | Code: 0



```js
{
    "requestID": "464c2d99-b396-4fe2-abc2-32f693a3a9d4",
    "timestamp": "2020-02-14T00:31:37.443231443Z",
    "sessionToken": "eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoic2Vzc2lvbiIsInVpZCI6ImQyNmJkYzJmLTJjYWItNGY3NC1hNzk5LWEyYjE2NDEwZGIyMiIsImFub24iOmZhbHNlLCJwZXJtaXNzaW9ucyI6bnVsbCwiYXBpS2V5IjoiOWQxOWIzZWQtYzA1Zi00ZTBjLWEzMzgtNDE4NzA1MTAwZGEzIiwiZGV2aWNlSUQiOiJpdWJmMnQ4eWhka3M2cDN3d3ltMiIsInJlZ2lvbnMiOlsiNzQ1NjhhNTAtMTI5MS00NjQzLWIyN2QtMDUyZTI0OWE0YTEzIiwiMDgzMjllMTAtYzI3NC0xMWU4LTliMDYtNGQ4YTQxMWY1NWExIiwiOTZhZjhjMDAtZmE0My0xMWU4LWJhMTQtMjdiMjRjOWNiMDI0IiwiYzY0ZmQxNGMtZDNlZS00ZTY0LWEzN2YtNzgyODc1NmIwNzIxIiwiMTRiOTlkYWYtMjg5Yi00YWExLTgwMTctNGE5MWFmYWQwMDZiIl0sImV4cCI6MTU4MTY0Mzg5NywiaWF0IjoxNTgxNjM2NjM4LCJpc3MiOiJPcmJpcy1PQU0tVjEiLCJzdWIiOiJkMjZiZGMyZi0yY2FiLTRmNzQtYTc5OS1hMmIxNjQxMGRiMjIifQ._WL59TiksbgYigHZK-UJGkyQ_GaHnRai6cGCAmaEpgx5jUwuGD0LVgTVmaxx5iO6Mc0kH2B0jInRnZWQdlMHsQ"
}
```



Status: Renew session token with deviceID (failure) | Code: 0



```js
{
    "requestID": "6f85ec71-9c42-442f-9e7f-a5f55c7d02b6",
    "timestamp": "2020-02-14T22:35:41.880755458Z",
    "errorMessage": "Unauthorized"
}
```



### Request device registration code

Creates a code to be used to register a connected device with a user's account.

The deviceID parameter should be a unique value generated by the connected device application and retained for later use.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|deviceID| string | required|UID for the user's device.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/device/register/{{deviceID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Request device registration code | Code: 0



```js
{
    "requestID": "2ce51765-b2b9-4c30-80ad-e9a0fe6d787f",
    "timestamp": "2020-02-13T23:36:08.51651453Z",
    "message": "successfully retrieved device registration code",
    "regCode": "7DCCB792"
}
```



### Register a device

Associates a connected device with the user's account.

If tenant policy limits the number of registered devices and the user has already registered the maximum number of devices, this call may fail or remove a previously registered device, depending on the tenant policy settings.

<br/>

#### Path Parameters
|Label		|Type	|Required |Description	|
|---	|---	|---		|---		|
|registrationCode| string | required	|A generated confirmation code entered by the user.|

<br/>

#### Error Responses
|HTTP Code|Error |Description
|---|---|---|
|**403**|1408|*Forbidden:* User cannot exceed concurrent device limits set by tenant policy |
|**404**|1040|*Resource not found*|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v2/device/register/{{registrationCode}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Register a device | Code: 0



```js
{
    "requestID": "ba299728-d2e8-4519-9e07-7d76496b5a71",
    "timestamp": "2020-02-14T18:13:38.912411691Z",
    "message": "successfully registered device",
    "deviceCount": 2,
    "registeredDevices": [
        "xw42u81jy0iruy1le4xv",
        "iapilwt205yil5duggmh"
    ]
}
```



### Login a device

Logs a device as online within the Orbis system.

<br/>

#### Body Parameters

|Field	|Type	|Required |Description	|
|---	|---	|---		|---		|
|deviceID| string | required	|UID for the user's device.|
|regCode| string | required	|A generated registration code entered by the user.|

<br/>

#### Error Responses
|HTTP Code|Error Code|Description
|---|---|---|
|**400**|1050|*Bad request:* Malformed request body|
|**403**|1408|*Forbidden:* User cannot exceed concurrent device limits set by tenant policy |
|**404**|1040|*Resource not found*|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OAMServer}}/oam/v2/device/tokens/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{apitoken}} | Requires the tenant API token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "deviceID": "{{deviceID}}", 
  "regCode": "{{registrationCode}}"
} 
```



### Renew a device

Takes an existing device token, then requests a new one with the renewal process.

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|**400**	|1410	|*Bad Request*: Attempt to update device or renew device token has failed |
|**403**	|1408	|*Forbidden:* User cannot exceed concurrent device limits set by tenant policy |

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OAMServer}}/oam/v2/device/tokens/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{devicetoken}} | Requires the user's device token to authenticate the request. |
| Content-Type | application/json |  |



***Responses:***


Status: Renew a device (success) | Code: 0



```js
{
    "requestID": "be7c6490-6346-4756-a5f3-0e0fc0222c71",
    "timestamp": "2020-02-14T00:46:54.511473Z",
    "message": "successfully renewed device token",
    "deviceToken": "eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoic2Vzc2lvbiIsInVpZCI6ImRkZGRkZGRkLWRkZGQtZGRkZC1kZGRkLWRkZGRkZGRkZGRkZCIsImFub24iOmZhbHNlLCJwZXJtaXNzaW9ucyI6WyJhbGxvdy1hbnktZ2VvbG9jYXRpb24iXSwiYXBpS2V5IjoiMTExMTExMTEtMTExMS0xMTExLTExMTEtMTExMTExMTExMTExIiwiY3VzdG9tIjp7InRva2VuIjp7InV1aWQiOiIyYjI4OWQ5NS05ZGIyLTQ1MmYtODA3OC0wN2VjNGQ2NjJlMmEiLCJpc3N1ZWQiOjE1ODE2NDEyMTR9LCJpZCI6ImZmODAzMmVkLWE5MzMtNGM3Ni1iNDMzLTYxZWQ2ZjIxNTcxZiIsImRldmljZU5hbWUiOiIiLCJkZXZpY2VJRCI6ImFiY2RlMTIzNDUifSwiZXhwIjoxNTgyMjQxMjE0LCJpYXQiOjE1ODE2NDEyMTQsImlzcyI6Ik9yYmlzLU9BTS1WMSIsInN1YiI6ImRkZGRkZGRkLWRkZGQtZGRkZC1kZGRkLWRkZGRkZGRkZGRkZCJ9.t1j-1sHB2DNI3E-81SPLToZuCGQg1Zx3tILtXr0CQHoEQpi_yWd1m0t69kGuJT0_ZOIiEJgGvLXJ53h0Iy1c-Q"
}
```



Status: Renew a device (failure) | Code: 0



```js
{
    "requestID": "26876792-7eae-4b6c-98bb-c58cee33c688",
    "timestamp": "2020-02-13T23:52:16.121312729Z",
    "errorMessage": "Unauthorized"
}
```



### Retrieve a device

Retrieves a registered device as specified by internalDeviceID. 

The ID used in this call must be a value from the "id" field for a device returned by calling the [List all user devices](https://docs.dtc.istreamplanet.net/?version=latest#99aba8d0-0dc7-46af-8d5f-5d158a1d9574) endpoint.

<br/>

#### Path Parameters
|Label	|Type	|Required |Description	|
|---	|---	|---		|---		|
|internalDeviceID| string | required	|UID for the user's device.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|404		|1040	|*Not Found*: No matching device ID found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OAMServer}}/oam/v2/user/devices/{{internalDeviceID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### List all user devices

Retrieves all registered devices for the calling user.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OAMServer}}/oam/v2/user/devices
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request.  |
| Content-Type | application/json |  |



### Delete device

Removes the specified registered device from the user's account. 

Note that the specified ID must be the "id" field of a device returned by the [Get devices](https://docs.dtc.istreamplanet.net/#e36c4624-6acb-4eda-855d-9741338a306f) endpoint.

<br/>

#### Path Parameters
|Label	|Type	|Required |Description	|
|---	|---	|---		|---		|
|internalDeviceID| string | required	|UID for the user's device.|

<br/>

#### Body Parameters
|Field		|Type	|Required	|Description	|
|---		|---	|---		|---			|
|username	|string	|required	|Username/email address for the user's account.|
|password	|string	|required	|Password for the user's account.|
|deviceID	|string	|required	|Unique ID for the user's device.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified device for the target user.|
|404		|1040	|*Not Found*: No matching device ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OAMServer}}/oam/v2/user/devices/{{internalDeviceID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "username":"mary.jackson@example.com",
  "password":"password",
  "deviceID":"{{deviceID}}"
}
```



---
[Back to top](#accounts)
> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2020-04-08 15:43:57 by [docgen](https://github.com/thedevsaddam/docgen)