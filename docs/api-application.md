---
id: api-application
title: Application 
sidebar_label: Application
---

The _application_ service endpoints are used to create and manage client application configurations.

--------

## Application - v1

### Create application configuration

Creates a new application configuration.


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{AppServer}}/app/v1/configs
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
    "application": "test",
    "settings": {
        "title": "App Title",
        "status": "active",
        "bounds": {
            "top": 5,
            "bottom": -5,
            "left": 2.5,
            "right": -2.5
        }
    },
    "s3bucket": "sloekito-epg-dev-1"
}
```



### Update application configuration


Updates the specified application configuration.

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to update or write the specified application configuration.|
|404		|1040	|*Not Found*: No matching application configuration found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{AppServer}}/app/v1/configs/{{applicationName}}
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
    "application": "sparksport",
    "settings": {
        "featureFlags": {
            "deviceLocationEnabledAndroid": true,
            "deviceLocationEnabledIOS": true,
            "ppvEnabledWeb": true,
            "billingCopy": {
                "learnMore": "",
                "purchaseStepSubDetails": ""
            }
        },
        "highVolumeEvents": [
            {
                "eventDescription": "WRC Germany 2017",
                "headline": "Are you here to watch this match?-Second",
                "matchId": "b3c240ca-b90e-49ac-8651-54effee17ddf",
                "pictureIds": {
                    "16x9": "d94116ea-deca-4ebe-a884-54c29320d8f6.jpg"
                },
                "redirectEndTime": "2019-09-12T00:00:00.000Z",
                "redirectStartTime": "2019-09-05T00:00:00.000Z",
                "timeDescription": "Fri 06 Sep - 12:00am-12:00AM NZT"
            }
        ],
        "leagueLogos": [
            {
                "cardLogo": "cd06d27a-48b0-4807-b9c4-48f89d063cdb.png",
                "comment": "FIH",
                "leagueId": "b826b141-6b29-4da1-a8aa-1dc1c1c93b06"
            },
            {
                "cardLogo": "7105dba8-7f7b-475f-95f0-f757601e7650.png",
                "comment": "FormulaOne",
                "leagueId": "cc170b3f-1e6a-4af4-93dd-6c5c733af4d7"
            },
            {
                "cardLogo": "385b0345-47a8-4267-ad8d-62087c8b9b39.png",
                "comment": "FormulaTwo",
                "leagueId": "4f37ce19-485d-48e9-adde-13e5899ee370"
            },
            {
                "cardLogo": "ae90510b-32d3-482e-a058-f34f344d2588.png",
                "comment": "World Rally Championship",
                "leagueId": "06cc4645-de74-44bf-82a7-a23a69cbae1a"
            },
            {
                "cardLogo": "c68317e6-9df0-44cc-9a1e-526177c6d34b.png",
                "comment": "One Championship",
                "leagueId": "2f78eea8-cc6c-4da6-8ddb-c27f96a2bc05"
            },
            {
                "cardLogo": "77ce72a0-5651-4432-b7b6-025234bcf9d3.jpg",
                "comment": "UFC",
                "leagueId": "9173cb5c-a1a7-4fd4-b15b-d6defcb779b6"
            }
        ],
        "packageId": "c4757270-2a37-11e9-a2ff-bd8ac90b5375",
        "pageInformation": {
            "AUTHENTICATED_HOME": {
                "BANNER_V4_SECTION_ID": "Authenticated_BANNERS",
                "FREEMIUM_RAILS_V3_PAGE_ID": "FREEMIUM",
                "RAILS_V3_PAGE_ID": "HOME",
                "comment": "Prepend What's On and Append Sports and Channel rails on client"
            },
            "LOGIN": {
                "BANNER_V4_SECTION_ID": "Authenticated_BANNERS",
                "comment": "this wont be Authenticated_BANNERS once we setup login banners"
            },
            "PPV": {
                "PPV_SECTION_ID": "PPV",
                "comment": "PPV_SECTION_ID indicates which section to fetch PPV events from.",
                "comment2": "Don't include it (or change name to xPPV_SECTION_ID) to completely hide the PPV tab in the apps"
            },
            "SPORT_EPCR": {
                "comment": "Heineken Champions Cup",
                "comment2": "rememember to fallback to SPORT_generic if fields are missing"
            },
            "SPORT_EPL": {
                "comment": "Premier League",
                "comment2": "rememember to fallback to SPORT_generic if fields are missing"
            },
            "SPORT_FIH_Pro_League": {
                "BANNER_V4_SECTION_ID": "Hockey_BANNERS",
                "RAILS_V3_PAGE_ID": "HOCKEY",
                "comment": "FIH Pro League"
            },
            "SPORT_FORMULA_ONE": {
                "BANNER_V4_SECTION_ID": "Motorsport_BANNERS",
                "RAILS_V3_PAGE_ID": "MOTORSPORT",
                "comment": "Formula One",
                "comment2": "rememember to fallback to SPORT_generic if fields are missing"
            },
            "SPORT_NBA": {
                "BANNER_V4_SECTION_ID": "NBA_BANNERS",
                "RAILS_V3_PAGE_ID": "NBA",
                "comment": "NBA",
                "comment2": "rememember to fallback to SPORT_generic if fields are missing"
            },
            "SPORT_One_Championship": {
                "comment": "One Championship",
                "comment2": "rememember to fallback to SPORT_generic if fields are missing"
            },
            "SPORT_RWC2019": {
                "BANNER_V4_SECTION_ID": "RWC2019",
                "RAILS_V3_PAGE_ID": "RUGBYWORLDCUP",
                "comment": "Rugby World Cup 2019"
            },
            "SPORT_WRC": {
                "BANNER_V4_SECTION_ID": "Motorsport_BANNERS",
                "RAILS_V3_PAGE_ID": "MOTORSPORT",
                "comment": "FIA World Rally Championship",
                "comment2": "rememember to fallback to SPORT_generic if fields are missing"
            },
            "SPORT_generic": {
                "BANNER_V4_SECTION_ID": "Authenticated_BANNERS",
                "RAILS_V3_PAGE_ID": "TEST",
                "comment": "fallback to SPORT_generic if Sport or Sport keys are missing",
                "comment2": "Prepend What's On and Append Sports rail on client"
            },
            "UNAUTHENTICATED_HOME": {
                "BANNER_V4_SECTION_ID": "Authenticated_BANNERS",
                "RAILS_V3_PAGE_ID": "HOME",
                "comment": "Prepend What's On and Append Sports and Channel rails on client",
                "comment2": "this wont be Authenticated_BANNERS once we setup login banners"
            }
        },
        "playerConfig": {
            "android": {
                "bitrate": {
                    "defaultMax": 3500000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "chromecast": {
                "bitrate": {
                    "defaultMax": 10000000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "freeview": {
                "bitrate": {
                    "defaultMax": 10000000,
                    "defaultMin": 1400000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "freeview_puck": {
                "bitrate": {
                    "defaultMax": 10000000,
                    "defaultMin": 1400000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "freeview_stb": {
                "bitrate": {
                    "defaultMax": 4500000,
                    "defaultMin": 1400000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "iOS": {
                "bitrate": {
                    "defaultMax": 3500000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "lg": {
                "bitrate": {
                    "defaultMax": 4500000,
                    "defaultMin": 1400000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "maxBitrate": 3500000,
            "panasonic": {
                "bitrate": {
                    "defaultMax": 10000000,
                    "defaultMin": 1400000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "samsung": {
                "bitrate": {
                    "defaultMax": 10000000,
                    "defaultMin": 1400000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "sony_android": {
                "bitrate": {
                    "defaultMax": 4500000,
                    "defaultMin": 1400000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "web": {
                "bitrate": {
                    "defaultMax": 10000000
                },
                "playerStalledFailoverTimeoutSec": 30
            },
            "xbox": {
                "bitrate": {
                    "defaultMax": 10000000
                },
                "playerStalledFailoverTimeoutSec": 30
            }
        },
        "purchaseConfig": {
            "vouchersEnabled": true,
            "walletEnabled": true
        },
        "purchaseOptions": {
            "rwc2019": {
                "billingPlanId": "SparkSport_PPV_RWC_Full_Tournament",
                "packageId": "6bca1c50-5a72-11e9-8fa2-3b4d6f712866"
            },
            "trialSubscription": {
                "billingPlanId": "SparkSport_TEST_1Day_Pass_01",
                "entitlementPeriodDays": 0,
                "packageId": "c4757270-2a37-11e9-a2ff-bd8ac90b5375"
            },
            "winBackSubscription": {
                "billingPlanId": "SparkSport_0dFree_1mRecur",
                "packageId": "c4757270-2a37-11e9-a2ff-bd8ac90b5375"
            }
        },
        "sports": [
            {
                "id": "SPORT_RWC2019",
                "images": {
                    "channelLogo": "0a3229fb-3c0d-481f-9362-818b46e47cdf.png",
                    "headerLogo": "0a3229fb-3c0d-481f-9362-818b46e47cdf.png"
                },
                "isHidden": false,
                "leagueId": "132395b5-087e-480a-9cdd-d8119c4fcc2d",
                "logoBackgroundColorHex": "#FFFFFF",
                "name": "RWC2019",
                "sportId": "4637bda3-df0b-4aed-bbd9-cd70e596b443"
            },
            {
                "id": "SPORT_FIH_Pro_League",
                "images": {
                    "channelLogo": "6724e0f3-0dac-4a9c-8ccc-03d906d6ee27.png",
                    "headerLogo": "6724e0f3-0dac-4a9c-8ccc-03d906d6ee27.png"
                },
                "isHidden": false,
                "leagueId": null,
                "logoBackgroundColorHex": "#000000",
                "name": "Field Hockey",
                "sportId": "7e2bf924-3433-4fec-ba70-95f986a98687"
            },
            {
                "id": "SPORT_FORMULA_ONE",
                "images": {
                    "channelLogo": "726c142e-fafe-409a-ba25-f7430c31675e.png",
                    "headerLogo": "726c142e-fafe-409a-ba25-f7430c31675e.png"
                },
                "isHidden": false,
                "leagueId": null,
                "logoBackgroundColorHex": "#E10600",
                "name": "Formula One",
                "sportId": "3601e817-a576-4c9d-a2f2-1f05f423427e"
            },
            {
                "id": "SPORT_WRC",
                "images": {
                    "channelLogo": "6fad4bca-6ed0-4221-88be-466988ecbf3a.png",
                    "headerLogo": "6fad4bca-6ed0-4221-88be-466988ecbf3a.png"
                },
                "isHidden": false,
                "leagueId": null,
                "logoBackgroundColorHex": "#E10600",
                "name": "FIA World Rally Championship",
                "sportId": "3601e817-a576-4c9d-a2f2-1f05f423427e"
            },
            {
                "id": "SPORT_NBA",
                "images": {
                    "channelLogo": "094bc37a-e0f8-49e8-98e8-e9df914a51e4.png",
                    "headerLogo": "094bc37a-e0f8-49e8-98e8-e9df914a51e4.png"
                },
                "isHidden": false,
                "leagueId": null,
                "logoBackgroundColorHex": "#17408B",
                "name": "NBA",
                "sportId": "0441658c-d816-4b37-b9b6-c333ab5d058c"
            },
            {
                "id": "SPORT_EPCR",
                "images": {
                    "channelLogo": "67f473e0-0e1b-4181-842a-969e2560328a.png",
                    "headerLogo": "67f473e0-0e1b-4181-842a-969e2560328a.png"
                },
                "isHidden": true,
                "leagueId": null,
                "logoBackgroundColorHex": "#1e1d3f",
                "name": "Heineken Champions Cup",
                "sportId": "e3403874-0486-4520-bafd-8b460474fb92"
            },
            {
                "id": "SPORT_One_Championship",
                "images": {
                    "channelLogo": "34a0a0b2-021a-432c-924d-2dd94b83e503.png",
                    "headerLogo": "34a0a0b2-021a-432c-924d-2dd94b83e503.png"
                },
                "isHidden": true,
                "leagueId": null,
                "logoBackgroundColorHex": "#000000",
                "name": "One Championship",
                "sportId": "471f1a06-3670-4f13-a02c-e7edb84ff2a0"
            },
            {
                "id": "SPORT_EPL",
                "images": {
                    "channelLogo": "279b793b-4b84-4f04-96af-ba372305ec99.png",
                    "headerLogo": "279b793b-4b84-4f04-96af-ba372305ec99.png"
                },
                "isHidden": true,
                "leagueId": "c3c39f64-ed87-41df-aa2f-70a849749b9e",
                "logoBackgroundColorHex": "#000000",
                "name": "Premier League",
                "sportId": "ea3c8187-0f9f-4f75-b947-cc5762765546"
            }
        ],
        "tournaments": [
            {
                "description": "Rugby World Cup 2019",
                "id": "rwc2019",
                "leagueId": "132395b5-087e-480a-9cdd-d8119c4fcc2d",
                "pictureIds": {
                    "banner": "",
                    "phoneBanner": "",
                    "tabletBanner": "",
                    "webBanner": ""
                },
                "tournamentEndTime": "2020-03-01T00:00:00.000Z",
                "tournamentId": null,
                "tournamentStartTime": "2019-08-15T00:00:00.000Z",
                "tournamentTeams": [
                    {
                        "name": "Argentina",
                        "pictureId": "ff5ddb35-ebce-4986-93da-58ea38beb004.png",
                        "teamId": "6addd73e-d9bd-4dac-a8cc-fbfb3969272f"
                    },
                    {
                        "name": "Australia",
                        "pictureId": "4611738c-0a1a-4233-ad39-9ed94f351ab5.png",
                        "teamId": "4c7c0048-6a29-4614-b2f0-91ff6c6583cf"
                    },
                    {
                        "name": "Canada",
                        "pictureId": "35c31fe7-675f-4036-b5d7-43f7e50469e4.png",
                        "teamId": "f9f30ae4-0e47-491a-b153-1d0127c89a29"
                    },
                    {
                        "name": "England",
                        "pictureId": "652a871f-035d-4c4a-ab73-f2028889d9b2.png",
                        "teamId": "b11402f9-d684-45ed-95be-7a723da4ccd4"
                    },
                    {
                        "name": "Fiji",
                        "pictureId": "78dc2748-f5b5-4437-a3c0-4505729635a9.png",
                        "teamId": "cca72e17-1344-4edf-9cce-f0e3b2f82237"
                    },
                    {
                        "name": "France",
                        "pictureId": "2b26493e-7489-45c4-8c97-ef8b3c008370.png",
                        "teamId": "f0aae43e-bc38-47f8-bbe2-3f3b2ef8b8c9"
                    },
                    {
                        "name": "Georgia",
                        "pictureId": "b1ef49dc-3b78-467c-9ddc-442b33029263.png",
                        "teamId": "3bba9644-26f5-49d0-82c6-cae61ea8d2f5"
                    },
                    {
                        "name": "Ireland",
                        "pictureId": "72521dfb-28a4-4148-a2f0-bef43a446c32.png",
                        "teamId": "d0856d08-2a89-46bd-aca6-dda59e983182"
                    },
                    {
                        "name": "Italy",
                        "pictureId": "2385b490-1f85-4614-9de6-d59a5ccf013d.png",
                        "teamId": "36441aa8-294a-42cb-a361-2ea0b7cc79eb"
                    },
                    {
                        "name": "Japan",
                        "pictureId": "4a0ba112-df95-41d4-bd09-a580c85c0d4c.png",
                        "teamId": "97220542-e1a1-4c24-95de-8b4aac511bbb"
                    },
                    {
                        "name": "Namibia",
                        "pictureId": "4f10f67c-615c-4965-8e04-7fca5dc18d95.png",
                        "teamId": "e75268c3-7742-4d1f-8fea-5b7ec2cdfab0"
                    },
                    {
                        "name": "New Zealand",
                        "pictureId": "ee9438cd-fae7-4510-ab43-2023e7a8973b.png",
                        "teamId": "6b0a9cfe-ad5c-4905-97c6-03c8c728e776"
                    },
                    {
                        "name": "Russia",
                        "pictureId": "a626b826-3410-40e8-97d9-4dc84e7ae65d.png",
                        "teamId": "9af44b53-68dc-4160-a414-4166c123692b"
                    },
                    {
                        "name": "Samoa",
                        "pictureId": "2e2cfdb9-7fb1-4979-ae44-5339732afb0c.png",
                        "teamId": "afbc39b3-9f32-46e3-b369-15e6fce993b4"
                    },
                    {
                        "name": "Scotland",
                        "pictureId": "77a5141a-fcb4-43e7-9eca-da665f354c19.png",
                        "teamId": "e11fa2c4-9661-4cb4-8671-8b8ad7390621"
                    },
                    {
                        "name": "South Africa",
                        "pictureId": "5f1e54b0-c9c2-47b9-a846-0de4bc8f80da.png",
                        "teamId": "40997ca8-0d01-4f5f-8d6a-ce6e17e7f54f"
                    },
                    {
                        "name": "Tonga",
                        "pictureId": "39b9c925-8632-4219-bd15-7604f717c284.png",
                        "teamId": "874ed7ce-eda2-4891-8fb7-5ba13ac51914"
                    },
                    {
                        "name": "United States",
                        "pictureId": "6fc8dcf8-e519-43a1-9b90-653ce78ff403.png",
                        "teamId": "c9a0d950-37e6-4c1e-b178-7c3304ecbc88"
                    },
                    {
                        "name": "Uruguay",
                        "pictureId": "4884614d-5de0-4468-b5d5-d8776e708bc3.png",
                        "teamId": "445ff236-f43e-4e46-aa21-6c2b8d2bb1f0"
                    },
                    {
                        "name": "Wales",
                        "pictureId": "66384cf7-de25-4cae-9443-125389679a39.png",
                        "teamId": "a50f5b4a-29bf-466a-85de-53c8382ccea0"
                    }
                ]
            }
        ],
        "trialSubscriptionInfo": {
            "billingPlanId": "SparkSport_TEST_1Day_Pass_01",
            "entitlementPeriodDays": 0,
            "packageId": "c4757270-2a37-11e9-a2ff-bd8ac90b5375"
        }
    },
    "s3bucket": "orbis-spark-appconfig-stage"
}
```



### Retrieve application configuration

Returns the specified application configuration by application name.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|applicationName	|string |required	|ID for the desired application configuration.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{AppServer}}/app/v1/configs/{{applicationName}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



### List all application configurations


Returns a list of all application configurations.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{AppServer}}/app/v1/configs
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



### Delete application configuration

Deletes the specified application configuration.

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the specified application configuration.|
|404		|1040	|*Not Found*: No matching application configuration found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{AppServer}}/app/v1/configs/{{applicationName}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



---
[Back to top](#application)
> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2020-04-08 15:58:08 by [docgen](https://github.com/thedevsaddam/docgen)