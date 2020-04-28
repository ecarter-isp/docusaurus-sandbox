---
id: api-content
title: Content
sidebar_label: Content
---

The *content* endpoints allow applications to create, update, publish, unpublish, 
delete, and otherwise manage information about specific types of video assets.

--------

<!--  Structure, then remove this index section.    -->

## Indices

* [v1](#v1)

  * [Create video asset](#1-create-video-asset)
  * [Publish video asset](#2-publish-video-asset)
  * [Update video asset](#3-update-video-asset)
  * [Update isLive status for an asset](#4-update-islive-status-for-an-asset)
  * [Retrieve published asset by ID](#5-retrieve-published-asset-by-id)
  * [Retrieve private asset by published ID](#6-retrieve-private-asset-by-published-id)
  * [Retrieve private asset by ID](#7-retrieve-private-asset-by-id)
  * [Retrieve published asset by private ID](#8-retrieve-published-asset-by-private-id)
  * [Search private assets by keyword, date](#9-search-private-assets-by-keyword,-date)
  * [Search published assets by keyword, date](#10-search-published-assets-by-keyword,-date)
  * [Search private assets by IDs](#11-search-private-assets-by-ids)
  * [Retrieve published assets by IDs](#12-retrieve-published-assets-by-ids)
  * [Retrieve published assets by event IDs](#13-retrieve-published-assets-by-event-ids)
  * [Search published assets by categories](#14-search-published-assets-by-categories)
  * [Search private assets by event IDs](#15-search-private-assets-by-event-ids)
  * [Unpublish an asset](#16-unpublish-an-asset)
  * [Delete private asset](#17-delete-private-asset)
  * [Retrieve category keys](#18-retrieve-category-keys)
  * [Register notification endpoint](#19-register-notification-endpoint)
  * [Get recommendations](#20-get-recommendations)

* [v1/asset markers](#v1asset-markers)

  * [Creates or updates an asset marker](#1-creates-or-updates-an-asset-marker)
  * [Delete custom asset markers](#2-delete-custom-asset-markers)
  * [Retrieve asset markers](#3-retrieve-asset-markers)

* [v2/assets](#v2assets)

  * [Create asset](#1-create-asset)
  * [Update asset](#2-update-asset)
  * [Retrieve an asset](#3-retrieve-an-asset)
  * [Retrieve an asset by provider asset  ID](#4-retrieve-an-asset-by-provider-asset--id)
  * [Delete asset](#5-delete-asset)
  * [Patch asset](#6-patch-asset)

* [v2/banners](#v2banners)

  * [Create banner](#1-create-banner)
  * [Update banner](#2-update-banner)
  * [Retrieve banner](#3-retrieve-banner)
  * [List all banners](#4-list-all-banners)
  * [Delete banner](#5-delete-banner)
  * [Patch banner](#6-patch-banner)

* [v2/entities](#v2entities)

  * [Retrieve entity resource information](#1-retrieve-entity-resource-information)
  * [List Entities](#2-list-entities)
  * [Link entities](#3-link-entities)

* [v2/epg/competitions](#v2epgcompetitions)

  * [Create EPG competition](#1-create-epg-competition)
  * [Update scheduled competition](#2-update-scheduled-competition)
  * [Retrieve scheduled game from the EPG](#3-retrieve-scheduled-game-from-the-epg)
  * [Retrieve scheduled game from the EPG with assets](#4-retrieve-scheduled-game-from-the-epg-with-assets)
  * [Delete EPG competition](#5-delete-epg-competition)
  * [Patch EPG competition](#6-patch-epg-competition)

* [v2/epg/episodes](#v2epgepisodes)

  * [Create EPG episode](#1-create-epg-episode)
  * [Update EPG episode](#2-update-epg-episode)
  * [Retrieve scheduled show episode from the EPG](#3-retrieve-scheduled-show-episode-from-the-epg)
  * [Retrieve scheduled show episode from the EPG with assets](#4-retrieve-scheduled-show-episode-from-the-epg-with-assets)
  * [Delete EPG episode](#5-delete-epg-episode)
  * [Patch EPG episode](#6-patch-epg-episode)

* [v2/epg/events](#v2epgevents)

  * [Create EPG event](#1-create-epg-event)
  * [Update scheduled event](#2-update-scheduled-event)
  * [Retrieve scheduled event from the EPG](#3-retrieve-scheduled-event-from-the-epg)
  * [Retrieve scheduled event from the EPG with assets](#4-retrieve-scheduled-event-from-the-epg-with-assets)
  * [Delete EPG event](#5-delete-epg-event)
  * [Patch EPG event](#6-patch-epg-event)

* [v2/epg/movies](#v2epgmovies)

  * [Create EPG movie](#1-create-epg-movie)
  * [Update EPG movie](#2-update-epg-movie)
  * [Retrieve scheduled movie from the EPG](#3-retrieve-scheduled-movie-from-the-epg)
  * [Retrieve scheduled movie from the EPG with assets](#4-retrieve-scheduled-movie-from-the-epg-with-assets)
  * [Delete EPG movie](#5-delete-epg-movie)
  * [Patch EPG movie](#6-patch-epg-movie)

* [v2/epg/stations](#v2epgstations)

  * [Create station](#1-create-station)
  * [Update station](#2-update-station)
  * [Retrieve station](#3-retrieve-station)
  * [List stations](#4-list-stations)
  * [Delete station and associated schedules](#5-delete-station-and-associated-schedules)
  * [Patch station](#6-patch-station)

* [v2/epg/teamcompetitions](#v2epgteamcompetitions)

  * [Create EPG team competition](#1-create-epg-team-competition)
  * [Update scheduled team competition](#2-update-scheduled-team-competition)
  * [Retrieve scheduled team game from the EPG](#3-retrieve-scheduled-team-game-from-the-epg)
  * [Delete EPG team competition](#4-delete-epg-team-competition)
  * [Patch EPG team competition](#5-patch-epg-team-competition)

* [v2/genres](#v2genres)

  * [List genres](#1-list-genres)
  * [Retrieve genre](#2-retrieve-genre)

* [v2/images](#v2images)

  * [Upload a new image](#1-upload-a-new-image)
  * [Delete images](#2-delete-images)

* [v2/live/competitions](#v2livecompetitions)

  * [Create live competition](#1-create-live-competition)
  * [Update live competition](#2-update-live-competition)
  * [Retrieve live competition](#3-retrieve-live-competition)
  * [Delete live competition](#4-delete-live-competition)
  * [Patch live competition](#5-patch-live-competition)

* [v2/live/events](#v2liveevents)

  * [Retrieve live event](#1-retrieve-live-event)
  * [Create live event](#2-create-live-event)
  * [Update live event](#3-update-live-event)
  * [Delete live event](#4-delete-live-event)
  * [Patch live event](#5-patch-live-event)

* [v2/live/teamCompetitions](#v2liveteamcompetitions)

  * [Create live team competition](#1-create-live-team-competition)
  * [Update live team competition](#2-update-live-team-competition)
  * [Retrieve live team competition](#3-retrieve-live-team-competition)
  * [Delete live team competition](#4-delete-live-team-competition)
  * [Patch live team competition](#5-patch-live-team-competition)

* [v2/pages](#v2pages)

  * [Retrieve page](#1-retrieve-page)
  * [Create/Update page](#2-createupdate-page)
  * [Delete page](#3-delete-page)
  * [Retrieve a section of a page](#4-retrieve-a-section-of-a-page)
  * [Create/Update page section](#5-createupdate-page-section)
  * [Delete page section](#6-delete-page-section)

* [v2/publishing](#v2publishing)

  * [Publish a resource](#1-publish-a-resource)
  * [Unpublish a resource](#2-unpublish-a-resource)
  * [Apply draft to resource](#3-apply-draft-to-resource)

* [v2/schedule](#v2schedule)

  * [List scheduled content](#1-list-scheduled-content)
  * [Black out programs](#2-black-out-programs)
  * [Audit scheduled content](#3-audit-scheduled-content)
  * [Audit scheduled content for one station](#4-audit-scheduled-content-for-one-station)

* [v2/search](#v2search)

  * [List matching content](#1-list-matching-content)
  * [List matching stations](#2-list-matching-stations)
  * [List resources by matching genreIDs](#3-list-resources-by-matching-genreids)

* [v2/seasons](#v2seasons)

  * [Create a season](#1-create-a-season)
  * [Update a season](#2-update-a-season)
  * [Retrieve a season](#3-retrieve-a-season)
  * [Patch a season](#4-patch-a-season)

* [v2/serviceProviders](#v2serviceproviders)

  * [Get serviceProviders list](#1-get-serviceproviders-list)
  * [Get serviceProviders by ID *](#2-get-serviceproviders-by-id-*)
  * [Create serviceProviders](#3-create-serviceproviders)
  * [Delete serviceProviders](#4-delete-serviceproviders)
  * [Update serviceProviders by ID *](#5-update-serviceproviders-by-id-*)
  * [Patch service provider](#6-patch-service-provider)
  * [Get serviceProviderCategories list](#7-get-serviceprovidercategories-list)
  * [Get serviceProviderCategories by ID](#8-get-serviceprovidercategories-by-id)
  * [Create serviceProviderCategories](#9-create-serviceprovidercategories)
  * [Update serviceProviderCategories by ID](#10-update-serviceprovidercategories-by-id)
  * [Delete serviceProviderCategories](#11-delete-serviceprovidercategories)
  * [Patch service provider category](#12-patch-service-provider-category)
  * [Retrieve whitelisted resources](#13-retrieve-whitelisted-resources)
  * [Create new whitelisted resource](#14-create-new-whitelisted-resource)
  * [Update whitelisted resource](#15-update-whitelisted-resource)
  * [Patch whitelisted](#16-patch-whitelisted)

* [v2/shows](#v2shows)

  * [Create a show](#1-create-a-show)
  * [Update a show](#2-update-a-show)
  * [Retrieve a show](#3-retrieve-a-show)
  * [Patch a show](#4-patch-a-show)

* [v2/validation](#v2validation)

  * [List all custom attributes](#1-list-all-custom-attributes)

* [v2/vod](#v2vod)

  * [List VOD movies and episodes to update](#1-list-vod-movies-and-episodes-to-update)

* [v2/vod/competitions](#v2vodcompetitions)

  * [Create VOD Competition](#1-create-vod-competition)
  * [Update VOD Competition](#2-update-vod-competition)
  * [Retrieve game from the on-demand catalog](#3-retrieve-game-from-the-on-demand-catalog)
  * [Delete VOD competition](#4-delete-vod-competition)
  * [Patch VOD competition](#5-patch-vod-competition)

* [v2/vod/episodes](#v2vodepisodes)

  * [Create VOD episode](#1-create-vod-episode)
  * [Update VOD episode](#2-update-vod-episode)
  * [Retrieve show episode from the on-demand catalog](#3-retrieve-show-episode-from-the-on-demand-catalog)
  * [Delete VOD episode](#4-delete-vod-episode)
  * [Patch VOD episode](#5-patch-vod-episode)

* [v2/vod/events](#v2vodevents)

  * [Create VOD event](#1-create-vod-event)
  * [Update VOD event](#2-update-vod-event)
  * [Retrieve event from the on-demand catalog](#3-retrieve-event-from-the-on-demand-catalog)
  * [Delete VOD event](#4-delete-vod-event)
  * [Patch VOD event](#5-patch-vod-event)

* [v2/vod/movies](#v2vodmovies)

  * [Create VOD movie](#1-create-vod-movie)
  * [Update VOD movie](#2-update-vod-movie)
  * [Retrieve movie from the on-demand catalog](#3-retrieve-movie-from-the-on-demand-catalog)
  * [Delete VOD movie](#4-delete-vod-movie)
  * [Patch VOD movie](#5-patch-vod-movie)

* [v2/vod/teamcompetitions](#v2vodteamcompetitions)

  * [Create VOD Team Competition](#1-create-vod-team-competition)
  * [Update VOD Team Competition](#2-update-vod-team-competition)
  * [Retrieve team game from the on-demand catalog](#3-retrieve-team-game-from-the-on-demand-catalog)
  * [Delete VOD team competition](#4-delete-vod-team-competition)
  * [Patch VOD team competition](#5-patch-vod-team-competition)

* [v2/workflow](#v2workflow)

  * [Create a resource based on a gameID](#1-create-a-resource-based-on-a-gameid)

* [v3](#v3)

  * [Retrieve personalized page](#1-retrieve-personalized-page)
  * [Get personalized section (carousel)](#2-get-personalized-section-(carousel))

* [v4](#v4)

  * [Add page configuration](#1-add-page-configuration)
  * [Update page configuration](#2-update-page-configuration)
  * [Delete page configuration](#3-delete-page-configuration)
  * [Retrieve page configuration](#4-retrieve-page-configuration)
  * [Retrieve section configuration](#5-retrieve-section-configuration)
  * [Retrieve page](#6-retrieve-page)
  * [Add editorial section configuration](#7-add-editorial-section-configuration)
  * [Add "currently live" section](#8-add-"currently-live"-section)
  * [Add a "continue watching" section](#9-add-a-"continue-watching"-section)
  * [Add a "watch later" section](#10-add-a-"watch-later"-section)
  * [Update editorial section configuration](#11-update-editorial-section-configuration)
  * [List all sections configured for a tenant](#12-list-all-sections-configured-for-a-tenant)
  * [List all pages configured for a tenant](#13-list-all-pages-configured-for-a-tenant)
  * [Delete section configuration](#14-delete-section-configuration)
  * [Get section](#15-get-section)
  * [Patch page configuration](#16-patch-page-configuration)
  * [Patch section configuration](#17-patch-section-configuration)


--------


## Content - v1



### Create video asset


Creates a new PRIVATE (not yet published) video asset. Issuing this request does NOT publish the asset.

<br>

##### Body Parameters
|Field		|Type	|Required	|Description|
|---		|---	|---		|---		|
|name		|string	|required	|Name of the asset. Max length = 300. |
|description|string	|optional	|Asset description.|
|type		|string	|required	|Asset type. Currently supported value: *video*. |
|dateBegin	|string	|required	|Start date for a live event, in ISO-8601 (UTC timestamp) format: _2018-07-11T05:00:00.00Z_. |
|dateEnd	|string	|optional	|End date for a live event, in ISO-8601 (UTC timestamp) format: _2018-07-11T07:00:00.00Z_. |
|eventID	|string	|required	|A generated event identifier. |
|contentProvider|string	|optional	|Original provider of the content, currently iStreamPlanet.|


<!--

|livePlaybackURLs|string	|optional	|Map of playback URLs for the asset. Max URL length 1024. Currently supports 0 or 1 entry with the key "Default". Future release will include support for multiple playback URLs for various device types etc.|
|vodPlaybackURLs|string	|optional	|Map of playback URLs for videos on demand (VOD). Max URL length 1024. Currently supports 0 or 1 entry with the key "Default". Future release will include support for multiple playback URLs for various device types etc.|
|imageURLs|string	|optional	|Map of images associated with the video. Max URL length 1024. Currently has 0 or 1 entry with the key "Default". In the future other image URLs can be added, such as thumbnail, cover etc.|
|isLive|boolean	|optional	| Indicates whether the video stream event is currently live. Default is _false_.|
|adContentAssetID|string	|optional	|Used for client-side advertisements.|
|adParentGroup|string	|optional	|Used for client-side advertisements.|
|subType|string	|optional	|Content sub-type. Examples: Live video, VOD video, Highlight, Condensed Replay, Trailer, Preview, etc.|
|contentOwner|string	|optional	|Original provider of the content. Typically, a sports league or network. (This field is for your reference only.)|
|livePubPoint|string	|optional	|CDN publishing point for live events.|
|live2VODPubPoint|string|optional	|CDN publishing point for live events converted to VOD.|
|keywords	|string	|optional	|A comma or space delimited list of keywords. Keyword searches are case insensitive sub-string matches. |
|categories|string	|optional	|A comma separated list of key=value categories. Each key must be one of the supported keys displayed by the [Retrieve category keys](https://docs.dtc.istreamplanet.net/#ff8033fe-9de9-4e61-a164-c4cc60014410) endpoint.|

-->

<br>

##### Error Responses
|HTTP Code |Error Code |Description|
|---|---|---|
|**400**|1103 |*Bad Request*: Unsupported type|
|**400**|1104 |*Bad Request*: Unsupported category key|
|**401**|1000, 1001, 1002 |*Unauthorized*: Authentication token missing, invalid, or expired|
|**403**|1004 |*Forbidden*: Cannot write the requested resource|

<br>

<!--
	Max length of the asset description?  300 characters?
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v1/admin/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "name": "Soccer game",
    "description": "2019 US Youth Soccer Interregional",
    "type": "video",
    "dateBegin": "2019-03-05T03:00:00Z",
    "dateEnd": "2019-03-05T05:00:00Z",
    "eventID": "{{eventID}}",
    "contentProvider": "iStreamPlanet"
}
```



***Responses:***


Status: Admin creates a video asset with eventID & assetID and categories | Code: 201



```js
{
    "requestID": "6abb27e8-093c-4e68-8e64-aa3442adc0f6",
    "timestamp": "2017-11-30T18:37:15.670297923Z",
    "asset": {
        "id": "43435694",
        "name": "Soccer game",
        "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
        "type": "video",
        "keywords": "soccer, Girls, Interregional",
        "categories": "sport=soccer,country=us,league=ERL",
        "dateBegin": "2017-07-11T00:26:47.663039Z",
        "dateEnd": "2017-07-11T05:00:00Z",
        "eventID": "w5n3gxnv7ffpas6yh99k",
        "assetID": "90vi84gqsqhtph7653x9",
        "contentProvider": "IstreamPlanet",
        "islive": false,
        "createdAt": "2017-11-30T18:37:13.742534Z",
        "updatedAt": "2017-11-30T18:37:13.742534Z"
    }
}
```



### Publish video asset


Publishes a private asset. A published copy of the asset is created immediately. 
If the *publishTime* option is not specified, this call immediately publishes the asset.

<br>

**Note:** 
The publish operation may take a long time (on average 10-15 sec) to complete publication of an asset. Resolution of this issue is in progress.

<br>

The following changes take place when an asset is published:
* The ID field of the asset is different.
* The published asset can be found in the published realm, not the private realm.

All other fields of the asset are the same, including assetID and eventID.

<br>

##### Body Parameters

|Field  |Type	|Required	|Description	|
|---    |---	|---		|---    		|
|ID	    |string |required	|ID of the target private asset to be published.|
|publishTime |string | optional	|Timestamp indicating the date and time when this asset will be published.|
|expirationTime |string | optional	|Timestamp indicating the date and time when this asset will be automatically unpublished.|

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v1/admin/assets/publish
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "id":"{{videoAssetID}}"
}

```



***Responses:***


Status: Admin Publishes video asset immediately | Code: 201



```js
{
    "requestID": "93060629-7da9-4028-9aba-57cf01a24c37",
    "timestamp": "2018-01-18T21:54:27.154395346Z",
    "publishInfo": {
        "privateAssetId": "b076d61b06f8db47ce381b7bb12d7c7c",
        "publishedAssetId": "dd2f9f09db4f94b187438e380f8b6e35",
        "publishTime": "2018-01-18T21:50:25.333Z",
        "expirationTime": "2018-12-29T00:00:00Z"
    }
}
```



### Update video asset


Updates an existing PRIVATE (not yet published) video asset. Specify only the fields that need to be updated in the request; all other fields retain their current values.

<br/>

##### Body Parameters
|Field	|Type	|Required	|Modifiable	|Description|
|---	|---	|---		|---		|---		|
|id		|string	| required	| no		| ID of the target asset. |
|eventID|string	| required	| no		| ID of the target event. |
|type	|string	| required	| no		| Type of the target asset. Currently, the only supported type is _video_. |
|isLive	|boolean| optional	| no		| Indicates whether the asset is a live event. Default is _false_. Use [Update isLive state...](https://docs.dtc.istreamplanet.net/#f28edac4-7acc-4d4d-94dd-3a9d362353c1) to modify this setting. |
|categories|string	| optional	| no	| String list of categories for case insensitive partial match. This field will be updatable in the next release. |
|keyword|string	| optional	| yes	    | String for case insensitive partial match. Repeat to provide multiple search strings. Specify the entire set of desired keywords; old keyword data is overwritten. |
|name	|string	| optional	| yes		| Name of the asset to be updated. |
|description	|string	| optional	| yes		| Description of the target to be updated. |
|dateBegin	|string	|required	|yes	| Event _start_ date and time in ISO-8601 Timestamp format (2017-08-11T00:26:47.663039Z). |
|dateEnd	|string	|required	|yes	| Event _end_ date and time in ISO-8601 Timestamp format (2017-08-11T05:00:00.00Z). |
|livePlaybackURLs	|string	| optional	| yes		| URLs of the asset to be updated. |
|vodPlaybackURLs	|string	| optional	| yes		| URLs of the asset to be updated. |
|imageURLs	|string	| optional	| yes		| URLs of the asset to be updated. |

<br/>

Additional modifiable fields include: adContentAssetID, adParentGroup, subType, contentOwner, livePubPoint, live2VODPubPoint.


<br/>

##### Error Responses
|HTTP Code |Error Code |Description|
|---|---|---|
|**400**|1103 |*Bad Request*: Unsupported category|
|**400**|1104 |*Bad Request*: Unsupported category key|
|**401**|1000, 1001, 1002 |*Unauthorized*: Authentication token missing, invalid, or expired|
|**403**|1004 |*Forbidden*: Cannot write the requested resource|

<br>

<!--
EPC: When the Category and Category Keys become modifiable, error codes 1103 and 1104 will be possible.
-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v1/admin/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "id": "{{videoAssetID}}",
    "dateBegin": "2019-03-05T03:30:00Z",
    "dateEnd": "2019-03-05T05:30:00Z",
    "livePlaybackURLs": {
        "Default": "https://myserver.mytesturl.us/live/up"
    }
}
```



***Responses:***


Status: Admin Updates Video Asset | Code: 201



```js
{
    "requestID": "d704590f-36af-4cb1-89d7-de85266b105d",
    "timestamp": "2017-11-30T18:37:26.619581001Z",
    "asset": {
        "id": "43435694",
        "name": "Soccer game",
        "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
        "type": "video",
        "keywords": "soccer, Girls, Interregional",
        "categories": "sport=soccer,country=us,league=ERL",
        "dateBegin": "2017-08-11T00:26:47.663039Z",
        "dateEnd": "2017-08-11T05:00:00Z",
        "eventID": "w5n3gxnv7ffpas6yh99k",
        "assetID": "90vi84gqsqhtph7653x9",
        "contentProvider": "iStreamPlanet",
        "livePlaybackURLs": {
            "Default": "https://myserver.mytesturl.us/live/up"
        },
        "vodPlaybackURLs": {
            "Default": "https://myserver.mytesturl.us/vod/up"
        },
        "imageURLs": {
            "Default": "https://myserver.mytesturl.us/image/up"
        },
        "islive": false,
        "adContentAssetID": "adID123up",
        "adParentGroup": "adParent123up",
        "subType": "livestream up",
        "contentOwner": "self up",
        "livePubPoint": "livePub123up",
        "live2VODPubPoint": "live2VODPub123up",
        "createdAt": "2017-11-30T18:37:13.742534Z",
        "updatedAt": "2017-11-30T18:37:26.560863Z"
    }
}
```



### Update isLive status for an asset


Updates the isLive status of an asset (both private and published) in real time. This endpoint is available only for assets that have been published.

<br/>

**NOTE:** An account must have the `view-unpublished-content` permission to access private assets.
 
<br/>

##### Body Parameters
|Field	|Type	|Required	|Description|
|---	|---	|---		|---		|
|id		|string |required	|ID of the private (original) asset.|
|isLive	|string |boolean	|When set to _true_, immediately flags the specified asset as a live event. Default value is  _false_.|

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1004	|*Forbidden*: Caller not authorized to update the target asset.|
|404		|1040	|*Not Found*: Target asset not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v1/admin/assets/state
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "id":"{{videoAssetID}}",
  "isLive":true
}

```



***Responses:***


Status: Admin updates isLive state for both published and private assets | Code: 200



```js
{
    "requestID": "f9e72cb7-a062-4863-997d-69e33fa27abe",
    "timestamp": "2017-11-30T18:52:04.795897461Z",
    "message": "Successfully updated isLive state to true for asset 43435694, and associated published asset 43435708"
}
```



### Retrieve published asset by ID


Retrieves a published asset by its ID (primary key).

<br/>

##### Path Parameters
|Label	|Type	|Required			|Description	|
|---	|---	|---	|---		|
| publishedID	|string	|required	|ID of the requested asset.|

<br/>

##### Error Responses

|HTTP Code | Error | Description                |
|:---------|:------|:---------------------------|
|413  |1040 | *Resource not found*: None of the supplied IDs match existing assets.| 
|400  |1050 | *Bad request*: None of the supplied IDs match published assets.| 
|400  |1103 | *Format of request invalid*: Request syntax is not correct.| 

</br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/user/assets/{{publishedID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: User retrieves the published asset by the ID | Code: 200



```js
{
    "requestID": "cc524a2c-d292-4ef6-968e-cd05b2cdfeab",
    "timestamp": "2017-11-30T19:02:01.099092956Z",
    "asset": {
        "id": "43435708",
        "name": "Soccer game",
        "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
        "type": "video",
        "keywords": "soccer, Girls, Interregional",
        "categories": "sport=soccer,country=US,league=ERL",
        "dateBegin": "2017-08-11T00:26:47.663039Z",
        "dateEnd": "2017-08-11T05:00:00Z",
        "eventID": "w5n3gxnv7ffpas6yh99k",
        "assetID": "90vi84gqsqhtph7653x9",
        "contentProvider": "iStreamPlanet",
        "livePlaybackURLs": {
            "Default": "https://myserver.mytesturl.us/live/up"
        },
        "vodPlaybackURLs": {
            "Default": "https://myserver.mytesturl.us/vod/up"
        },
        "imageURLs": {
            "Default": "https://myserver.mytesturl.us/image/up"
        },
        "islive": true,
        "adContentAssetID": "adID123up",
        "adParentGroup": "adParent123up",
        "subType": "livestream up",
        "contentOwner": "self up",
        "livePubPoint": "livePub123up",
        "live2VODPubPoint": "live2VODPub123up",
        "createdAt": "2017-11-30T18:51:20.227537Z",
        "updatedAt": "2017-11-30T18:52:03.836465Z"
    }
}
```



### Retrieve private asset by published ID


Retrieves a private asset using the specified published assetID. 
An error is returned if the asset has not been published.

<br/>

**NOTE:** An account must have the `view-unpublished-content` permission to access private assets.

<br/>

##### Path Parameters
|Label	|Type	|Required		|Description	|
|---	|---	|---	|---			|
| publishedID	|string	|required	|ID of the requested asset.|

<br/>

##### Error Responses

|HTTP Code | Error | Description                |
|:---------|:------|:---------------------------|
|413  |1040 | *Resource not found*: None of the supplied IDs match existing assets.| 
|400  |1050 | *Bad request*: None of the supplied IDs match published assets.| 
|400  |1103 | *Format of request invalid*: Request syntax is not correct.| 

</br>

<!--
Are these the right error messages?
What is this endpoint used for?

NOTE: This endpoint was hardcoded:  "{{OCMServer}}/ocm/v1/admin/assets/associated/published/d18f6724cd69ef569976fd2619b594ee"
Replaced with one from the example: "{{OCMServer}}/ocm/v1/admin/assets/associated/published/{{publishedID}}"

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/admin/assets/associated/published/{{publishedID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Retrieve private asset by published asset.ID | Code: 200



```js
{
    "requestID": "678aac1e-e6aa-4b71-8362-f90cfc212c55",
    "timestamp": "2018-03-06T21:49:56.779332216Z",
    "asset": {
        "id": "7af07004accc669117071535a43bf284",
        "name": "Soccer game",
        "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
        "type": "video",
        "keywords": "soccer, Girls, Interregional",
        "categories": "sport=soccer,country=us,league=ERL",
        "dateBegin": "2017-07-11T00:26:47Z",
        "dateEnd": "2017-07-11T05:00:00Z",
        "eventID": "ufa7m2ex1l6wwjvzwwa1",
        "assetID": "hj32upw2ehmnpcm1l1yl",
        "contentProvider": "IstreamPlanet",
        "createdAt": "2018-03-06T21:49:27.583Z",
        "updatedAt": "2018-03-06T21:49:27.583Z"
    }
}
```



### Retrieve private asset by ID


Retrieves a private (unpublished) asset by ID, which is the asset's primary key.

<br/>

**NOTE:** An account must have the `view-unpublished-content` permission to access private assets.

<br/>

##### Path Parameters
|Label	|Type	|Required		|Description	|
|---	|---	|---	|---			|
| videoAssetID	|string	|required	|ID of the requested asset.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/admin/assets/private/{{videoAssetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Admin searches private assets by id | Code: 200



```js
{"requestID":"89ac7ace-b6a9-4feb-b0fa-fe181657fbe2","timestamp":"2018-01-18T22:07:44.701505894Z","asset":{"id":"380b7336379100017621bfe3301b8d51","name":"Soccer game","description":"2017 US Youth Soccer ODP Girls Thanksgiving Interregional","type":"video","keywords":"soccer, Girls, Interregional","categories":"sport=soccer,country=us,league=ERL","dateBegin":"2017-08-11T00:26:47Z","dateEnd":"2017-08-11T05:00:00Z","eventID":"bkere06bp096b1rr5ogp","assetID":"0dv4v18g2qn7vsayhghf","contentProvider":"iStreamPlanet","livePlaybackURLs":{"Default":"https://myserver.mytesturl.us/live/up"},"vodPlaybackURLs":{"Default":"https://myserver.mytesturl.us/vod/up"},"imageURLs":{"Default":"https://myserver.mytesturl.us/image/up"},"islive":false,"adContentAssetID":"adID123up","adParentGroup":"adParent123up","subType":"livestream up","contentOwner":"self up","livePubPoint":"livePub123up","live2VODPubPoint":"live2VODPub123up","createdAt":"2018-01-18T22:05:36.17Z","updatedAt":"2018-01-18T22:07:36.513Z"}}
```



### Retrieve published asset by private ID


Retrieves a published asset using the supplied private assetID.
An error is returned if the asset has not been published.

<br/>

**NOTE:** An account must have the `view-unpublished-content` permission to access private assets.

<br/>

##### Path Parameters
|Label	|Type	|Required		|Description	|
|---	|---	|---	|---			|
| videoAssetID	|string	|required	|ID of the requested asset.|

<br/>

##### Error Responses

|HTTP Code | Error | Description                |
|:---------|:------|:---------------------------|
|413  |1040 | *Resource not found*: None of the supplied IDs match existing assets.| 
|400  |1050 | *Bad request*: None of the supplied IDs match published assets.| 
|400  |1103 | *Format of request invalid*: Request syntax is not correct.| 

</br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/admin/assets/associated/private/{{videoAssetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Retrieve published asset by private asset.ID | Code: 400



```js
{
    "requestID": "5b863039-97e8-42ae-91f9-9ec8eb699770",
    "timestamp": "2018-03-06T21:51:15.96666678Z",
    "errorCode": 1050,
    "errorMessage": "Asset 46ecbb34b3cf88d23f1ffb5d71aa2dfd has not been published"
}
```



Status: Admin retrieves a private video asset by the assetID | Code: 200



```js
{
    "requestID": "722aa233-4bb0-4300-b38e-a68a6080f427",
    "timestamp": "2018-01-19T00:55:57.334592486Z",
    "assets": [
        {
            "id": "077a8b7172cd370d39e93e2d5beebada",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=soccer,country=us,league=ERL",
            "dateBegin": "2017-08-11T00:26:47Z",
            "dateEnd": "2017-08-11T05:00:00Z",
            "eventID": "xtzp75w4gcm52p28y0jc",
            "assetID": "80hape9302shybaajs16",
            "contentProvider": "iStreamPlanet",
            "livePlaybackURLs": {
                "Default": "https://myserver.mytesturl.us/live/up"
            },
            "vodPlaybackURLs": {
                "Default": "https://myserver.mytesturl.us/vod/up"
            },
            "imageURLs": {
                "Default": "https://myserver.mytesturl.us/image/up"
            },
            "islive": false,
            "adContentAssetID": "adID123up",
            "adParentGroup": "adParent123up",
            "subType": "livestream up",
            "contentOwner": "self up",
            "livePubPoint": "livePub123up",
            "live2VODPubPoint": "live2VODPub123up",
            "createdAt": "2018-01-19T00:55:48.942Z",
            "updatedAt": "2018-01-19T00:55:57.088Z"
        }
    ],
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "entitlements": null
}
```



Status: Retrieve published asset by private asset.ID | Code: 200



```js
{
    "requestID": "30236739-e0a1-41b5-ac93-a9c065963d15",
    "timestamp": "2018-03-06T21:49:32.965189129Z",
    "asset": {
        "id": "dd162097fd7e9e6a6893403a0766a289",
        "name": "Soccer game",
        "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
        "type": "video",
        "keywords": "soccer, Girls, Interregional",
        "categories": "sport=soccer,country=us,league=ERL",
        "dateBegin": "2017-07-11T00:26:47Z",
        "dateEnd": "2017-07-11T05:00:00Z",
        "eventID": "ufa7m2ex1l6wwjvzwwa1",
        "assetID": "hj32upw2ehmnpcm1l1yl",
        "contentProvider": "IstreamPlanet",
        "createdAt": "2018-03-06T21:49:37.416Z",
        "updatedAt": "2018-03-06T21:49:37.416Z"
    }
}
```



### Search private assets by keyword, date


Searches and filters private assets by keywords and dates, as specified by the query parameters.

<br>

**Notes:** 
* An account must have the `view-unpublished-content` permission to access private assets.
* All search parameters are processed as logical AND, so any results returned must meet __all__ of the specified search criteria.
* All dates are timestamps with a timezone in ISO-8601 format; for example: _2018-01-12T11:19:20.231-08:00_ or _2018-07-11T05:00:00.00Z_

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to access the target asset.|
|404		|1040	|*Not Found*: Target asset not found.|

<br/>

<!--

EPC:

|count	| Maximum number of items returned per search call (or per page); used for pagination. Default is 20.|
|offset	| Number of items to skip at the start of the returned result set; used for pagination. Default is 0.|
if number of objects more than count, start with <offset> record. 0-based.

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/admin/search/assets/private
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| keyword | soccer | Search event titles and descriptions for specified keyword values. Search is case-insensitive and can be repeated to specify multiple keywords. |
| date.gt | 2017-01-01T00:00:00-08 | After date: event dateBegin is _after_ the specified date. **Required**; this field must be populated to return results. |
| date.lt | 2019-12-10T00:00:00-08 | Before date: event dateBegin is _before_ the specified date. |
| count | 5 | Maximum number of objects returned per call. The default is 20. |
| offset | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |
| sort | updatedat | Field used to sort the returned items; supported values are *date*, *name*, and *updatedat*. |
| direction | desc | Sort direction for the returned items; supported values are *asc* (ascending) and *desc* (descending). |



***Responses:***


Status: Admin searches private assets by keyword, date | Code: 200



```js
{
    "requestID": "1ea488ed-610b-4647-957a-90825254248a",
    "timestamp": "2018-01-19T00:57:28.007238561Z",
    "assets": [
        {
            "id": "077a8b7172cd370d39e93e2d5beebada",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=soccer,country=us,league=ERL",
            "dateBegin": "2017-08-11T00:26:47Z",
            "dateEnd": "2017-08-11T05:00:00Z",
            "eventID": "xtzp75w4gcm52p28y0jc",
            "assetID": "80hape9302shybaajs16",
            "contentProvider": "iStreamPlanet",
            "livePlaybackURLs": {
                "Default": "https://myserver.mytesturl.us/live/up"
            },
            "vodPlaybackURLs": {
                "Default": "https://myserver.mytesturl.us/vod/up"
            },
            "imageURLs": {
                "Default": "https://myserver.mytesturl.us/image/up"
            },
            "islive": false,
            "adContentAssetID": "adID123up",
            "adParentGroup": "adParent123up",
            "subType": "livestream up",
            "contentOwner": "self up",
            "livePubPoint": "livePub123up",
            "live2VODPubPoint": "live2VODPub123up",
            "createdAt": "2018-01-19T00:55:48.942Z",
            "updatedAt": "2018-01-19T00:55:57.088Z"
        },
        {
            "id": "e6f610f527ba884f70dc97d92c600454",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=soccer,country=us,league=ERL",
            "dateBegin": "2017-07-11T00:26:47Z",
            "dateEnd": "2017-07-11T05:00:00Z",
            "eventID": "xbyh6rrbuastdtxreo3f",
            "assetID": "eosgf0ztnzbtg4bftppk",
            "contentProvider": "IstreamPlanet",
            "islive": false,
            "createdAt": "2018-01-18T23:27:41.551Z",
            "updatedAt": "2018-01-18T23:27:41.551Z"
        },
        {
            "id": "a3da407e2919c4964491e0f910e2dbd8",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=tennis",
            "dateBegin": "2017-07-11T00:26:47Z",
            "dateEnd": "2017-07-11T05:00:00Z",
            "eventID": "vx3rrb54fw2ij564vyct",
            "assetID": "s6vpf6kem0goq5yact0x",
            "contentProvider": "IstreamPlanet",
            "islive": false,
            "createdAt": "2018-01-18T22:53:09.412Z",
            "updatedAt": "2018-01-18T22:53:09.411Z"
        },
        {
            "id": "380b7336379100017621bfe3301b8d51",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=soccer,country=us,league=ERL",
            "dateBegin": "2017-08-11T00:26:47Z",
            "dateEnd": "2017-08-11T05:00:00Z",
            "eventID": "bkere06bp096b1rr5ogp",
            "assetID": "0dv4v18g2qn7vsayhghf",
            "contentProvider": "iStreamPlanet",
            "islive": true,
            "adContentAssetID": "adID123up",
            "adParentGroup": "adParent123up",
            "subType": "livestream up",
            "contentOwner": "self up",
            "livePubPoint": "livePub123up",
            "live2VODPubPoint": "live2VODPub123up",
            "createdAt": "2018-01-18T22:05:36.17Z",
            "updatedAt": "2018-01-18T22:08:16.948Z"
        }
    ],
    "metadata": {
        "count": 4,
        "totalCount": 4,
        "offset": 0
    },
    "entitlements": null
}
```



### Search published assets by keyword, date


Searches and filters published assets by keywords and dates. 

<br/>

**Notes:** 
* All query parameters are optional unless otherwise noted.
* All dates are timestamps with a timezone in ISO-8601 format; for example: _2018-01-12T11:19:20.231-08:00_ or _2018-07-11T05:00:00.00Z_
* All query parameters are processed as logical AND, so any results returned must meet __all__ of the specified search criteria. Consequently, using more parameters tends to return fewer results.

<br/>

<!-- EPC Questions and notes:
  •  What is the absolute maximum number of results that can be returned?**
  •  For `count` is there a max number of results per page?**
  •  (*) needs examples or further description on how to use this parameter in the Prog Guide**
  •  Notes: date.lte and date.gte are also valid;  offset = (page - 1) * itemsPerPage + 1?;  
  •  sort by date (event start), name, or updatedat (most recent additions); 
-->

##### Error Responses

|HTTP Code| Error | Description               |
|:--------|:------|:--------------------------|
|413  |1070 |*Request too large*: Too many results match the search.| 
|400  |1103 |*Format of request invalid*: Request syntax is not correct.| 

</br>
&nbsp;


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/user/search/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| date.gte | 2019-03-01T00:00:00-07:00 | After date: event dateBegin is _on or after_ the specified date. |
| date.lt | 2019-03-05T00:00:00-07:00 | Before date: event dateBegin is _before_ the specified date. |
| count | 5 | Maximum number of items returned for the search; used for pagination. Default is *20*. |
| offset | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is *0*. |
| sort | date | Sort column. Supported values are *date* (sort by start date), *name* (sort by event name), and *updatedat* (sort by most recently updated). |
| direction | desc | Sort direction for the returned items; supported values are *asc* (ascending) and *desc* (descending). |



***Responses:***


Status: User searches published assets by keyword, date | Code: 200



```js
{
    "requestID": "ad76d3f1-7c9c-45f7-9cb7-4761d0844d0a",
    "timestamp": "2018-01-19T00:54:15.436723312Z",
    "assets": [
        {
            "id": "39aa9b350623b2085131643ede6a55cb",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=tennis",
            "dateBegin": "2017-07-11T00:26:47Z",
            "dateEnd": "2017-07-11T05:00:00Z",
            "eventID": "vx3rrb54fw2ij564vyct",
            "assetID": "s6vpf6kem0goq5yact0x",
            "contentProvider": "IstreamPlanet",
            "islive": false,
            "createdAt": "2018-01-18T22:53:42.184Z",
            "updatedAt": "2018-01-18T22:53:42.184Z"
        },
        {
            "id": "a38d5f435c28b421551cc9b4d8cf3729",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=soccer,country=us,league=ERL",
            "dateBegin": "2017-08-11T00:26:47Z",
            "dateEnd": "2017-08-11T05:00:00Z",
            "eventID": "bkere06bp096b1rr5ogp",
            "assetID": "0dv4v18g2qn7vsayhghf",
            "contentProvider": "iStreamPlanet",
            "islive": true,
            "adContentAssetID": "adID123up",
            "adParentGroup": "adParent123up",
            "subType": "livestream up",
            "contentOwner": "self up",
            "livePubPoint": "livePub123up",
            "live2VODPubPoint": "live2VODPub123up",
            "updatedAt": "2018-01-18T22:08:16.746Z"
        }
    ],
    "metadata": {
        "count": 2,
        "totalCount": 2,
        "offset": 0
    },
    "entitlements": null
}
```



Status: Search published assets by keyword, date | Code: 200



```js
{
    "requestID": "95e7df32-219d-4a12-9495-61719b230f1a",
    "timestamp": "2018-06-01T18:14:58.95096928Z",
    "assets": [
        {
            "id": "a3c35c1d311f3edf9fc787be3c11daf5",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Game 3",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "dateBegin": "2018-07-13T00:26:47Z",
            "dateEnd": "2018-07-13T05:00:00Z",
            "eventID": "jlfald29yvo8na8ewett",
            "assetID": "lr1kg7wnmubzsbx7xlv3",
            "contentProvider": "IstreamPlanet",
            "isLive": false,
            "createdAt": "2018-02-26T21:00:37.731Z",
            "updatedAt": "2018-02-26T21:00:37.731Z",
            "packages": [
                {
                    "id": "70ddb190-4289-11e8-8b95-87fa2fa752ea",
                    "name": "April Chile Soccer",
                    "description": "Demo",
                    "bypassEntitlementCheck": false,
                    "billingPlans": [],
                    "customData": null,
                    "owned": false
                }
            ]
        },
        {
            "id": "c09d004b0b54b357f3781589a0461e28",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Game 2",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "dateBegin": "2018-07-12T00:26:47Z",
            "dateEnd": "2018-07-12T05:00:00Z",
            "eventID": "g1we5m5to3dvtwd65xpf",
            "assetID": "6h7xnvckinxxsl9lh5n2",
            "contentProvider": "IstreamPlanet",
            "isLive": false,
            "createdAt": "2018-02-26T21:00:13.297Z",
            "updatedAt": "2018-02-26T21:00:13.297Z",
            "packages": [
                {
                    "id": "65xj5o7o6tc5krcc4h9t",
                    "name": "Girls Youth Soccer Package",
                    "description": "Girls Youth Soccer Games",
                    "bypassEntitlementCheck": false,
                    "billingPlans": [
                        {
                            "id": "ba4dnp3y171t7daa5fgn",
                            "description": "Single payment subscription purchase",
                            "recurrence": "1M",
                            "prices": {
                                "Apple": {
                                    "USD": 1.99
                                },
                                "Google": {
                                    "USD": 1.99
                                },
                                "Vindicia": {
                                    "USD": 0.99
                                }
                            },
                            "productID": "",
                            "product": null
                        }
                    ],
                    "customData": null,
                    "owned": false
                },
                {
                    "id": "utt4jc1agdjut1mnmxlu",
                    "name": "Girls Youth Soccer Game 2",
                    "description": "Girls Youth Soccer Game 2",
                    "bypassEntitlementCheck": false,
                    "billingPlans": [
                        {
                            "id": "oegimaefm5nids2jrzrl",
                            "description": "Single event purchase",
                            "recurrence": null,
                            "prices": {
                                "Apple": {
                                    "USD": 0.99
                                },
                                "Google": {
                                    "USD": 0.99
                                },
                                "Vindicia": {
                                    "USD": 0.99
                                }
                            },
                            "productID": "",
                            "product": null
                        }
                    ],
                    "customData": null,
                    "owned": false
                }
            ]
        },
        {
            "id": "f682beefab2e52912a3c492f716ee90d",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Game 1",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "dateBegin": "2018-07-11T00:26:47Z",
            "dateEnd": "2018-07-11T05:00:00Z",
            "eventID": "pxhn3az1xcrr05h6wu67",
            "assetID": "p7tud62ia4wx8see2i9d",
            "contentProvider": "IstreamPlanet",
            "isLive": false,
            "createdAt": "2018-02-26T20:59:50.198Z",
            "updatedAt": "2018-02-26T20:59:50.198Z",
            "packages": [
                {
                    "id": "70ddb190-4289-11e8-8b95-87fa2fa752ea",
                    "name": "April Chile Soccer",
                    "description": "Demo",
                    "bypassEntitlementCheck": false,
                    "billingPlans": [],
                    "customData": null,
                    "owned": false
                },
                {
                    "id": "65xj5o7o6tc5krcc4h9t",
                    "name": "Girls Youth Soccer Package",
                    "description": "Girls Youth Soccer Games",
                    "bypassEntitlementCheck": false,
                    "billingPlans": [
                        {
                            "id": "ba4dnp3y171t7daa5fgn",
                            "description": "Single payment subscription purchase",
                            "recurrence": "1M",
                            "prices": {
                                "Apple": {
                                    "USD": 1.99
                                },
                                "Google": {
                                    "USD": 1.99
                                },
                                "Vindicia": {
                                    "USD": 0.99
                                }
                            },
                            "productID": "",
                            "product": null
                        }
                    ],
                    "customData": null,
                    "owned": false
                },
                {
                    "id": "be9rqcf3mqlsb7x7pbkf",
                    "name": "Girls Youth Soccer Game 1",
                    "description": "Girls Youth Soccer Game 1",
                    "bypassEntitlementCheck": false,
                    "billingPlans": [
                        {
                            "id": "oegimaefm5nids2jrzrl",
                            "description": "Single event purchase",
                            "recurrence": null,
                            "prices": {
                                "Apple": {
                                    "USD": 0.99
                                },
                                "Google": {
                                    "USD": 0.99
                                },
                                "Vindicia": {
                                    "USD": 0.99
                                }
                            },
                            "productID": "",
                            "product": null
                        }
                    ],
                    "customData": null,
                    "owned": false
                }
            ]
        },
        {
            "id": "12fdf68374567193cfbea6537d23b53b",
            "name": "Fox Sports 3",
            "type": "video",
            "keywords": "DRM, LIVE1001 FEATUREDSPORTS",
            "dateBegin": "2018-03-15T00:01:00Z",
            "dateEnd": "2099-03-15T00:01:00Z",
            "eventID": "CBC13",
            "assetID": "CBC13",
            "contentProvider": "iStreamPlanet",
            "livePlaybackURLs": {
                "DASH": "https://d30gb033f0paft.cloudfront.net/629418/dtv/fs3/master.mpd",
                "Default": "https://cbcdtvfs3-i.akamaihd.net/hls/live/627892/dtv/FS3-DTV/master.m3u8",
                "HLS": "https://cbcdtvfs3-i.akamaihd.net/hls/live/627892-b/dtv/FS3-DTV/master.m3u8"
            },
            "imageURLs": {
                "Default": "https://dtvlatamvod.akamaized.net/bugs/FoxSports3.jpg"
            },
            "isLive": true,
            "subType": "live",
            "updatedAt": "2018-03-28T17:52:45.984Z",
            "packages": []
        },
        {
            "id": "7e1a2d3ee06f537490bb0b0cebe0ab1c",
            "name": "Drama",
            "type": "video",
            "keywords": "VODCONTAINER",
            "dateBegin": "2018-03-15T00:00:14Z",
            "dateEnd": "2100-01-01T00:00:00Z",
            "eventID": "VOD1004",
            "assetID": "VOD1004",
            "contentProvider": "iStreamPlanet",
            "imageURLs": {
                "Default": "{{ocm:host}}search/assets?keyword=VOD1004&sort=date&direction=asc"
            },
            "isLive": false,
            "subType": "movies",
            "updatedAt": "2018-03-16T18:58:41.94Z",
            "packages": []
        }
    ],
    "metadata": {
        "count": 5,
        "totalCount": 231,
        "offset": 0
    },
    "entitlementsAvailable": true,
    "productsAvailable": true
}
```



### Search private assets by IDs


Retrieves private (unpublished) assets as specified by the list of IDs (the primary key) in the query.

<br>

Contents are only returned for valid published IDs. In the sample call, only one asset would be returned because no asset with *another_ID* exists.

<br/>

**NOTE:** An account must have the `view-unpublished-content` permission to access private assets.

<br>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to access the target asset.|
|404		|1040	|*Not Found*: Target asset not found.|

<br/>

<!-- Does this generate an error? -->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/admin/search/assets/private
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| id | {{videoAssetID}},another_ID | Value is a comma-separated list of asset IDs. Required. |



### Retrieve published assets by IDs


Returns a published asset for each (primary key) ID specified in the query.

<br>

Contents are only returned for valid published IDs. A mistake may return an empty set. In the example, only one asset is returned because no asset with *another_ID* exists.

</br>

##### Error Responses

|HTTP Code | Error | Description                |
|:---------|:------|:---------------------------|
|413  |1040 | *Resource not found*: None of the supplied IDs match existing assets.| 
|400  |1103 | *Format of request invalid*: Request syntax is not correct.| 

</br>
&nbsp;

[//]: <> (____  START OF SUGGESTIONS  ____________________________________________________)
<!--
  Please add any missing possible error responses for this endpoint. 
  
  For all URL parameters and JSON key=value pairs, indicate: 
  •  Whether it is required or optional. 
  •  Whether it may be modified. 
  •  The default value, if any, when no value is specified. 
  •  For selection menus, the list of all possible options: [north, east, west, south] 

  •  The expected data type [String, Boolean, Number, Array, JSON Object] 
    o For Numbers: 
       Integers only? 
       Precision limit for Decimals? [two decimal points for Currency] 
       Range limits [min = -40, max = 100] 

  •  For Date, Time, and Timestamp strings: 
    o Range limitations: [“Today”; “January 1, 1970”] 
    o Required or possible formats: [“Tomorrow”; “2018-12-31T23:59-07:00”] 

  NOTE: Any form-data content is temporary & for documentation purposes only! 
-->
[//]: <> (____  END OF SUGGESTIONS    ____________________________________________________)


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/user/search/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| id | {{publishedID}},another_ID | _Required_. Comma-separated list of published asset IDs. |



***Responses:***


Status: User searches for multiple published assets IDs (logical OR) | Code: 200



```js
{
    "requestID": "38e414dc-4594-43b5-91ae-fe1ac542a810",
    "timestamp": "2018-01-25T21:19:39.177578844Z",
    "assets": [
        {
            "id": "e4d0da2169a48aaa765d5daa2170a016",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=soccer,country=US,league=ERL",
            "dateBegin": "2017-07-11T00:26:47Z",
            "dateEnd": "2017-07-11T05:00:00Z",
            "eventID": "dd9mazmkt5agd629hn6e",
            "assetID": "1qd5k5auwcbyl0a60523",
            "contentProvider": "IstreamPlanet",
            "islive": false,
            "createdAt": "2018-01-25T21:19:36.823Z",
            "updatedAt": "2018-01-25T21:19:36.823Z"
        }
    ],
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "entitlements": null
}
```



### Retrieve published assets by event IDs


Returns a published asset for each eventID specified in the query.

<br/>

Contents are only returned for valid published IDs. A mistake may return an empty set. In the example, only one asset is returned because no asset with *another_ID* exists.

Optional **keyword** and **date** parameters can be added to the query. All query parameters are processed as logical AND, so any results returned must meet all of the specified criteria.

<br/>

##### Error Responses

|HTTP Code | Error | Description                |
|:---------|:------|:---------------------------|
|413  |1040 | *Resource not found*: None of the supplied IDs match existing assets.| 
|400  |1103 | *Format of request invalid*: Request syntax is not correct.| 

</br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/user/search/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| eventid | {{eventID}},another_eventID | _Required_. Comma-separated list of event IDs for the requested assets. |



***Responses:***


Status: User retrieves the published asset by the eventID | Code: 200



```js
{
    "requestID": "2288ca15-dcde-4738-8e5d-a56c40a5afbd",
    "timestamp": "2017-11-30T18:53:34.892365959Z",
    "assets": [
        {
            "id": "43435708",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "league=ERL,country=US,sport=soccer,",
            "dateBegin": "2017-08-11T00:26:47.663039Z",
            "dateEnd": "2017-08-11T05:00:00Z",
            "eventID": "w5n3gxnv7ffpas6yh99k",
            "assetID": "90vi84gqsqhtph7653x9",
            "contentProvider": "iStreamPlanet",
            "livePlaybackURLs": {
                "Default": "https://myserver.mytesturl.us/live/up"
            },
            "vodPlaybackURLs": {
                "Default": "https://myserver.mytesturl.us/vod/up"
            },
            "imageURLs": {
                "Default": "https://myserver.mytesturl.us/image/up"
            },
            "islive": true,
            "adContentAssetID": "adID123up",
            "adParentGroup": "adParent123up",
            "subType": "livestream up",
            "contentOwner": "self up",
            "livePubPoint": "livePub123up",
            "live2VODPubPoint": "live2VODPub123up",
            "createdAt": "2017-11-30T18:51:20.227537Z",
            "updatedAt": "2017-11-30T18:52:03.836465Z"
        }
    ],
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0,
        "ids": [
            "43435708"
        ]
    }
}
```



### Search published assets by categories


Returns a list of published assets that match a predefined category. 

All search parameters are processed as logical AND, so any results returned must meet all of the specified search criteria.

The categories used in the search are in the form _key=value_, where _key_ is one of the [predefined category keys](https://docs.dtc.istreamplanet.net/#ff8033fe-9de9-4e61-a164-c4cc60014410) with a target _value_.

<br>

##### Error Responses
|HTTP Code |Error Code |Description|
|---|---|---|
|**400**|1103 |*Bad Request*: Unsupported category - request syntax is not correct.|
|**400**|1104 |*Bad Request*: Unsupported category value - value is misspelled or does not exist.|
|**400**|1105 |*Bad Request*: Unsupported category key - key is misspelled or has not been defined.|
|**401**|1000, 1001, 1002 |*Unauthorized*: Authentication token missing, invalid, or expired. |
|**403**|1003 |*Forbidden*: Cannot read the requested resource|
|**413**|1070 |*Request too large*: Too many results match the search.|

<!-- How many is TOO MANY for |**413**|1070 |*Request too large*: Too many results match the search.| ??? -->

<!-- |**404**| |*Not found*: Requested resource ID missing, deleted, or incorrect.|| -->

<!-- totalCount: Maximum number of items returned for the search; used for pagination; default is *???*. -->

<br>

<!--

Retrieves a list of published assets matching the specified categories.
* All search parameters are optional.
* If multiple parameters are used, they are combined using logical AND (thus narrowing the search).
* The categories used in the search are in the form of _key=value_, where _key_ must be one of the predefined category keys. Invoke the [Retrieve category keys API](https://lively-satellite-4723.postman.co/collections/2309672-2baad776-266e-2a1f-f75c-27fb82d5aa35?workspace=b778f868-0dfc-41dc-8b84-fa15e1354134#c4ff196d-86d0-6b71-af5e-1aa8a3cd35af) to see the list of valid category keys and values.

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/user/search/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| sport | soccer | Match *key=value*, where *key* is a predefined category key.  May be specified multiple times to narrow results. |
| sort | updatedat | Sort column. Supported values are *date* (sort by start date), *name* (sort by event name), and *updatedat* (sort by most recently updated). |
| direction | desc | Sort direction for the returned items; supported values are *asc* (ascending) and *desc* (descending). |
| count | 5 | Number of items to retrieve per page; default is *20*. |
| offset | 0 | Number of items to skip at the start of the returned result set; used for pagination; default is *0*. |



***Responses:***


Status: User searches published assets by categories | Code: 200



```js
{
    "requestID": "ee8c576b-7d6b-4774-90f9-fead437b58bc",
    "timestamp": "2018-01-19T00:53:30.935970211Z",
    "assets": [
        {
            "id": "39aa9b350623b2085131643ede6a55cb",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=tennis",
            "dateBegin": "2017-07-11T00:26:47Z",
            "dateEnd": "2017-07-11T05:00:00Z",
            "eventID": "vx3rrb54fw2ij564vyct",
            "assetID": "s6vpf6kem0goq5yact0x",
            "contentProvider": "IstreamPlanet",
            "islive": false,
            "createdAt": "2018-01-18T22:53:42.184Z",
            "updatedAt": "2018-01-18T22:53:42.184Z"
        }
    ],
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "entitlements": null
}
```



### Search private assets by event IDs


Retrieves a list of assets by eventID.

<br/>

Any asset created with an eventID can be retrieved using its eventID. After publishing, the published copy can also be retrieved by the eventID. Contents are only returned for valid published IDs. In the sample call, only one asset would be returned because no asset with *another_ID* exists.

<br/>

**NOTE:** An account must have the `view-unpublished-content` permission to access private assets.

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to access the target asset.|
|404		|1040	|*Not Found*: Target asset not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/admin/search/assets/private
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| eventid | {{eventID}},another_ID | Value is a comma-separated list of event IDs. Required. |



***Responses:***


Status: Admin retrieves a private video asset by the eventID | Code: 200



```js
{
    "requestID": "9b66fef3-f604-483d-b3d8-2022ca125147",
    "timestamp": "2018-01-19T00:56:51.760110569Z",
    "assets": [
        {
            "id": "077a8b7172cd370d39e93e2d5beebada",
            "name": "Soccer game",
            "description": "2017 US Youth Soccer ODP Girls Thanksgiving Interregional",
            "type": "video",
            "keywords": "soccer, Girls, Interregional",
            "categories": "sport=soccer,country=us,league=ERL",
            "dateBegin": "2017-08-11T00:26:47Z",
            "dateEnd": "2017-08-11T05:00:00Z",
            "eventID": "xtzp75w4gcm52p28y0jc",
            "assetID": "80hape9302shybaajs16",
            "contentProvider": "iStreamPlanet",
            "livePlaybackURLs": {
                "Default": "https://myserver.mytesturl.us/live/up"
            },
            "vodPlaybackURLs": {
                "Default": "https://myserver.mytesturl.us/vod/up"
            },
            "imageURLs": {
                "Default": "https://myserver.mytesturl.us/image/up"
            },
            "islive": false,
            "adContentAssetID": "adID123up",
            "adParentGroup": "adParent123up",
            "subType": "livestream up",
            "contentOwner": "self up",
            "livePubPoint": "livePub123up",
            "live2VODPubPoint": "live2VODPub123up",
            "createdAt": "2018-01-19T00:55:48.942Z",
            "updatedAt": "2018-01-19T00:55:57.088Z"
        }
    ],
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "entitlements": null
}
```



### Unpublish an asset


Deletes a published asset, unpublishing it immediately.

This is a cleanup step that deletes a previously published asset as specified by *{{publishedID}}*.

<br>

##### Path Parameters
|Label		|Type	|Required	|Description|
|---		|---	|---		|---		|
|publishedID|string |required	|ID of the target asset.|	

<br>

##### Error Responses

|HTTP Code | Error | Description                |
|:---------|:------|:---------------------------|
|403  |1004 | *Forbidden*: Not authorized to write to or delete requested resource.|
|413  |1040 | *Resource not found*: None of the supplied IDs match existing assets.| 
|400  |1050 | *Bad request*: None of the supplied IDs match published assets.| 
|400  |1103 | *Format of request invalid*: Request syntax is not correct.| 

</br>


***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OCMServer}}/ocm/v1/admin/assets/published/{{publishedID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Admin unpublishes a published asset immediately | Code: 200



```js
{
    "requestID": "a4724e1d-600d-4462-89ee-96f008f3e6d0",
    "timestamp": "2017-11-30T21:47:51.955779914Z",
    "message": "Asset ID 43435875 was successfully deleted."
}
```



### Delete private asset


Deletes the specified private asset. 

<br/>

**Notes:** 
* An account must have the `view-unpublished-content` permission to access private assets.
* When a private asset is deleted, its corresponding published asset is also deleted.

<br>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|videoAssetID|string |required	|The target asset ID to be deleted.|	

<br>

This is a cleanup step to delete the previously created asset specified by *{{videoAssetID}}*.

<br>


***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OCMServer}}/ocm/v1/admin/assets/private/{{videoAssetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Admin deletes a private asset  {{videoAssetID}} | Code: 200



```js
{"requestID":"19aad03d-9971-4bcb-acf2-5db91a59566d","timestamp":"2017-11-30T21:48:17.768383036Z","message":"Asset ID 43435868 was successfully deleted."}
```



### Retrieve category keys


Retrieves a list of preconfigured category keys.

<!--

  "requestID": "7e2950f0-70d6-41e8-bba0-0b9b3378408e",
  "timestamp": "2018-02-01T02:23:22.496427073Z",
  "categoryKeys": [
    "league",
    "subleague",
    "sport",
    "country",
    "city"

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/user/categorykeys
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: User retrieves category keys copy | Code: 200



```js
{"requestID":"7e2950f0-70d6-41e8-bba0-0b9b3378408e","timestamp":"2018-02-01T02:23:22.496427073Z","categoryKeys":["league","subleague","sport","country","city"]}
```



### Register notification endpoint


Registers an endpoint to receive OCM callback notifications when the specified operation perfomed is on assets. Currently, only the updateState operation is supported.
The OCM callback notification is a POST request to the specified endpoint with the following data.  The data json has the field "operation", specifying the operation occurred, and the entire updated asset intformation. 

See example below:

```
{
"operation":"updateState",
  "asset":{
  "id":"43447544",
  "name":"Testing new publishing",
  "description":"Testing stuff",
  "type":"video",
  "dateBegin":"2017-07-11T00:26:47.663039Z",
  "eventID":"38c9f574-176c-4886-bbcc-3f7be01bbd18",
  "assetID":"d2494fcc-bfdd-448e-bb6d-22b668e9c75a",
  "contentProvider":"iStreamPlanet",
  "islive":true,
  "createdAt":"2017-12-13T05:15:04.259469Z",
  "updatedAt":"2017-12-13T07:20:25.585529Z"
  }
}
```


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v1/admin/notifications
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "type": "video",
    "operations": [
        "updateState"
    ],
    "secret": "mysecret1234567",
    "header": "Authorization",
    "url": "https://testsite/notifications"
}
```



***Responses:***


Status: Admin Registers Notification Endpoint | Code: 201



```js
{
    "requestID": "d2abe65a-9bc1-4085-82a7-805ff54288da",
    "timestamp": "2017-12-19T21:07:08.586876617Z",
    "notifiactionSubscription": {
        "type": "video",
        "operations": [
            "updateState"
        ],
        "url": "https://testsite/notifications",
        "header": "Authorization",
        "secret": "mysecret1234567"
    }
}
```



### Get recommendations


Takes a list of video asset or event IDs and returns the list ranked in order of the calling user's likely interest in each item.

<!-- Why is this a POST when it's not creating/modifying data?  Shouldn't it be a GET? -->

<br>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|404		|1040	|*Not Found*: Specified asset not found; possibly deleted or misspelled ID.|
|400		|1103	|*Bad Request*: Request syntax is not correct.| 

<!--  **EPC: What error is generated if the list is empty? 1060? 1103?** -->

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v1/user/assets/recommedations
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "assetIds": [
        "{{videoAsset1ID}}",
        "{{videoAsset2ID}}"
    ]
}
```



***Responses:***


Status: Get recommendations | Code: 200



```js
{
    "requestID": "2c1e7881-4d73-48d0-baf8-9959dcd41294",
    "timestamp": "2017-12-31T22:34:42.696067572Z",
    "recommendations": [
        {
            "id": "43464294",
            "score": 0.39539012
        },
        {
            "id": "43464299",
            "score": 0.39539012
        }
    ]
}
```



## v1/asset markers



### 1. Creates or updates an asset marker


In the body custom_markers are supposed to be exactly the text of the markers file you would like to receive but escaped to a string like the example.


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v1/admin/assets/markers
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "assetID": "asset1",
    "custom_markers": {
        "markers": [
            {
                "time": "2018-04-18T04:00:20.924Z",
                "event_id": 21736,
                "segmentation_type_id": 16,
                "upid": "AAAAAAAAAAA=",
                "upid_type": 8,
                "web_delivery_allowed": true
            },
            {
                "time": "2018-04-18T04:03:37.954Z",
                "event_id": 21738,
                "segmentation_type_id": 53
            },
            {
                "time": "2018-04-18T04:05:58.662Z",
                "event_id": 21740,
                "segmentation_type_id": 53
            },
            {
                "time": "2018-04-18T04:08:01.318Z",
                "event_id": 21741,
                "segmentation_type_id": 53
            },
            {
                "time": "2018-04-18T04:10:40.244Z",
                "event_id": 21742,
                "segmentation_type_id": 53
            },
            {
                "time": "2018-04-18T04:13:26.911Z",
                "event_id": 21743,
                "segmentation_type_id": 53
            },
            {
                "time": "2018-04-18T04:15:06.878Z",
                "event_id": 21736,
                "segmentation_type_id": 17
            }
        ]
    }
}
```



***Responses:***


Status: User searches published assets by multiple ids (logical OR) | Code: 200



```js
{"requestID":"38e414dc-4594-43b5-91ae-fe1ac542a810","timestamp":"2018-01-25T21:19:39.177578844Z","assets":[{"id":"e4d0da2169a48aaa765d5daa2170a016","name":"Soccer game","description":"2017 US Youth Soccer ODP Girls Thanksgiving Interregional","type":"video","keywords":"soccer, Girls, Interregional","categories":"sport=soccer,country=US,league=ERL","dateBegin":"2017-07-11T00:26:47Z","dateEnd":"2017-07-11T05:00:00Z","eventID":"dd9mazmkt5agd629hn6e","assetID":"1qd5k5auwcbyl0a60523","contentProvider":"IstreamPlanet","islive":false,"createdAt":"2018-01-25T21:19:36.823Z","updatedAt":"2018-01-25T21:19:36.823Z"}],"metadata":{"count":1,"totalCount":1,"offset":0},"entitlements":null}
```



### 2. Delete custom asset markers


Deletes custom markers for the specified published asset IDs.

Markers are only deleted for valid published asset IDs.

<br>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target custom marker.|
|404		|1040	|*Not Found*: Target asset not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: FORMDATA
URL: {{OCMServer}}/ocm/v1/admin/assets/markers/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| assetID | {{assetID}} | Value is a comma-separated list of asset IDs.
Required. |



***Responses:***


Status: User searches published assets by multiple ids (logical OR) | Code: 200



```js
{"requestID":"38e414dc-4594-43b5-91ae-fe1ac542a810","timestamp":"2018-01-25T21:19:39.177578844Z","assets":[{"id":"e4d0da2169a48aaa765d5daa2170a016","name":"Soccer game","description":"2017 US Youth Soccer ODP Girls Thanksgiving Interregional","type":"video","keywords":"soccer, Girls, Interregional","categories":"sport=soccer,country=US,league=ERL","dateBegin":"2017-07-11T00:26:47Z","dateEnd":"2017-07-11T05:00:00Z","eventID":"dd9mazmkt5agd629hn6e","assetID":"1qd5k5auwcbyl0a60523","contentProvider":"IstreamPlanet","islive":false,"createdAt":"2018-01-25T21:19:36.823Z","updatedAt":"2018-01-25T21:19:36.823Z"}],"metadata":{"count":1,"totalCount":1,"offset":0},"entitlements":null}
```



### 3. Retrieve asset markers


Retrieves both custom markers and internal VOD markers for the published asset specified in the query.

Contents are only returned for valid IDs of published assets. 
<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v1/user/assets/markers/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| assetID | {{assetID}} | Required.  Value is a comma-separated list of asset IDs. |



***Responses:***


Status: Retrieve asset segments | Code: 200



```js
{"requestID":"60794f22-bfb1-4f15-9b63-43775c1cf90e","timestamp":"2018-08-13T22:43:34.919371778Z","markers_info":{"assetID":"asset1","custom_markers":"{\r\n   \"markers\":[\r\n      {\r\n         \"time\":\"2018-04-18T04:00:20.924Z\",\r\n         \"event_id\":21736,\r\n         \"segmentation_type_id\":16,\r\n         \"upid\":\"AAAAAAAAAAA=\",\r\n         \"upid_type\":8,\r\n         \"web_delivery_allowed\":true\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:03:37.954Z\",\r\n         \"event_id\":21738,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:05:58.662Z\",\r\n         \"event_id\":21740,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:08:01.318Z\",\r\n         \"event_id\":21741,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:10:40.244Z\",\r\n         \"event_id\":21742,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:13:26.911Z\",\r\n         \"event_id\":21743,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:15:06.878Z\",\r\n         \"event_id\":21736,\r\n         \"segmentation_type_id\":17\r\n      }\r\n   ]\r\n}"}}
```



Status: User searches published assets by multiple ids (logical OR) | Code: 200



```js
{"requestID":"38e414dc-4594-43b5-91ae-fe1ac542a810","timestamp":"2018-01-25T21:19:39.177578844Z","assets":[{"id":"e4d0da2169a48aaa765d5daa2170a016","name":"Soccer game","description":"2017 US Youth Soccer ODP Girls Thanksgiving Interregional","type":"video","keywords":"soccer, Girls, Interregional","categories":"sport=soccer,country=US,league=ERL","dateBegin":"2017-07-11T00:26:47Z","dateEnd":"2017-07-11T05:00:00Z","eventID":"dd9mazmkt5agd629hn6e","assetID":"1qd5k5auwcbyl0a60523","contentProvider":"IstreamPlanet","islive":false,"createdAt":"2018-01-25T21:19:36.823Z","updatedAt":"2018-01-25T21:19:36.823Z"}],"metadata":{"count":1,"totalCount":1,"offset":0},"entitlements":null}
```



Status: Retrieve asset markers | Code: 200



```js
{"requestID":"60794f22-bfb1-4f15-9b63-43775c1cf90e","timestamp":"2018-08-13T22:43:34.919371778Z","markers_info":{"assetID":"asset1","custom_markers":"{\r\n   \"markers\":[\r\n      {\r\n         \"time\":\"2018-04-18T04:00:20.924Z\",\r\n         \"event_id\":21736,\r\n         \"segmentation_type_id\":16,\r\n         \"upid\":\"AAAAAAAAAAA=\",\r\n         \"upid_type\":8,\r\n         \"web_delivery_allowed\":true\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:03:37.954Z\",\r\n         \"event_id\":21738,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:05:58.662Z\",\r\n         \"event_id\":21740,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:08:01.318Z\",\r\n         \"event_id\":21741,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:10:40.244Z\",\r\n         \"event_id\":21742,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:13:26.911Z\",\r\n         \"event_id\":21743,\r\n         \"segmentation_type_id\":53\r\n      },\r\n      {\r\n         \"time\":\"2018-04-18T04:15:06.878Z\",\r\n         \"event_id\":21736,\r\n         \"segmentation_type_id\":17\r\n      }\r\n   ]\r\n}"}}
```



## v2/assets



### 1. Create asset


Creates an asset resource.

<br/>

##### Body Parameters

| Field  | Parent  |Type  | Description |  
|------:|---------|------|-------------|
| resourceType |   | string | Always "assets"   | |
| pictureID |   | string | URL for the picture resource. |  | 
| duration|   | number | Video duration in minutes.  |  |
| live|   | boolean | Indicates if this is a live feed (true; uses liveURLs) or not (false; uses vodURLs).   |  |
| environment|   | string | Enum: prod or test  |  |
| vodURLs |  | string | URLs for video on demand sources. ||
| *`liveURLs`* |  |object| URLs for live feeds. | |
| *`dash`* | *`liveURLs`* |  object |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. | |
| primary | *`dash`* | string | Primary URL for the DASH source.   |  | 
|backup|*`dash`*|string|Backup URL for DASH source.| |
|  *`hls`* | *`liveURLs`* | object | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.| |
| backup | *`hls`*|  string | Secondary URL for the HLS source. |   |
| primary | *`hls`* |string | Primary URL for the HLS source.   |  |
| publishStart |  | string | (optional) First date that this content is visible to end users. ISO 8601 format |
| publishEnd |  | string | (optional) Last date that this content is visible to end users. ISO 8601 format |

<br/>

##### Response Object

| Field  | Parent  |Type  | Description |  
|------:|---------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| assets   ||array||  |
| id |   | string | Unique ID for each asset  |  |
| resourceType |    | enum string | Always "assets"   | |
| pictureID |    | string | URL for the picture resource. |  | 
| duration|    | number | Video duration in minutes.  |  |
| live|    | boolean | Indicates if this is a live feed (true; uses liveURLs) or not (false; uses vodURLs).   |  |
| environment|    | string | Enum: prod or test  |  |
| vodURLs |   | string | URLs for video on demand sources. ||
| `liveURLs` |  |object| URLs for live feeds. | |
| `dash` | `liveURLs` |  object |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. | |
| primary | `dash` | string | Primary URL for the DASH source.   |  | 
| backup  | `dash`|string|Backup URL for DASH source.| |
| `hls` | `liveURLs` | object | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.| |
| backup  | `hls`|  string | Secondary URL for the HLS source. |   |
| primary | `hls` |string | Primary URL for the HLS source.   |  |
| publishStart |  | string | First date that this content is visible to end users. ISO 8601 format |
| publishEnd |  | string | Last date that this content is visible to end users. ISO 8601 format |

<br/>

##### Error Responses

|HTTP Code|Description
|---|---|
|**400**|*Bad request*|
|**401**|*Unauthorized*|
|**404**|*Not found*|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | <string> |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Body:***

```js        
{
    "resourceType": "assets",
    "pictureID": "b7b6f5bf792659fe38480cf61d46ee2d",
    "duration": 100,
    "live": true,
    "environment": "test",
    "liveURLs": {
        "dash": {
            "primary": "https://d30gb033f0paft.cloudfront.net/629831/dtv/animalplanet/master.mpd"
        },
        "hls": {
            "backup": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879-b/dtv/AnimalPlanet-DTV/master.m3u8",
            "primary": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879/dtv/AnimalPlanet-DTV/master.m3u8"
        }
    },
    "vodURLs": null,
    "drmID": "asdf",
    "availabilityStartsAt": "2019-04-18T04:00:00Z",
    "availabilityEndsAt": "2019-08-17T00:00:00Z",
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



***Responses:***


Status: Returns information about one asset | Code: 200



```js
{
    "requestID": "83ba61fe-fc64-4c47-9cb8-a47322e5d006",
    "timestamp": "2018-05-14T22:19:52.070325681Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "assets": [
        {
            "id": "e7d32347775f78daf1609c8e1bf5a850",
            "resourceType": "assets",
            "pictureID": "https://dtvlatamvod.akamaized.net/bugs/AnimalPlanet.jpg",
            "duration": 0,
            "live": false,
            "environment": "",
            "liveURLs": {
                "dash": {
                    "primary": "https://d30gb033f0paft.cloudfront.net/629831/dtv/animalplanet/master.mpd"
                },
                "hls": {
                    "backup": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879-b/dtv/AnimalPlanet-DTV/master.m3u8",
                    "primary": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879/dtv/AnimalPlanet-DTV/master.m3u8"
                }
            },
            "vodURLs": null
        }
    ]
}
```



Status: Create asset | Code: 200



```js
{
    "requestID": "13a2b58b-ca9b-4dde-8ab6-aafebdc20ea2",
    "timestamp": "2018-05-15T13:52:39.164249208Z",
    "metadata": {
        "count": 1,
        "totalCount": 0,
        "offset": 0
    },
    "assets": [
        {
            "id": "d4df9035a0b27ae57772055c49b5817e",
            "resourceType": "assets",
            "pictureID": "https://dtvlatamvod.akamaized.net/bugs/AnimalPlanet.jpg",
            "duration": 0,
            "live": false,
            "environment": "prod",
            "liveURLs": {
                "dash": {
                    "primary": "https://d30gb033f0paft.cloudfront.net/629831/dtv/animalplanet/master.mpd"
                },
                "hls": {
                    "backup": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879-b/dtv/AnimalPlanet-DTV/master.m3u8",
                    "primary": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879/dtv/AnimalPlanet-DTV/master.m3u8"
                }
            },
            "vodURLs": null,
		    "availabilityStartsAt": "2019-04-18T04:00:00Z",
		    "availabilityEndsAt": "2019-08-17T00:00:00Z",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        }
    ]
}
```



### 2. Update asset


Updates the specified asset resource.

<br/>

##### Path Parameters

|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|assetID|string |required	|ID of the asset to be updated. |

<br/>

##### Error Responses

|HTTP Code|Description
|---|---|
|**400**|*Bad request*|
|**401**|*Unauthorized*|
|**404**|*Not found*|

<br/>


##### Body Parameters

| Field  | Parent  |Type  | Description |  
|------:|---------|------|-------------|
| resourceType |   | string | Value is always **assets** for this endpoint. |
| pictureID |   | string | ID for the picture resource. |
| duration|   | number | Video duration in minutes.  | 
| live|   | boolean | Indicates if this is a live feed (**true** = uses liveURLs) or not (**false** = uses vodURLs).  | 
| environment|   | string | Value may be either **test** or **prod** (production).  | 
| drmID |   | string | DRM ID for the asset resource. |
| vodURLs |  | string | URLs for video on demand sources. |
| `liveURLs` |  |object| URLs for live feeds. |
| `dash` | `liveURLs` |  object |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. |
| primary | `dash` | string | Primary URL for the DASH source.   | 
| backup  | `dash`|string|Backup URL for DASH source.|
| `hls`  | `liveURLs` | object | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.|
| backup  | `hls`| string | Secondary URL for the HLS source.   |
| primary | `hls`| string | Primary URL for the HLS source.   | 
| availabilityStartsAt |  | string | Date when access to content *begins*. Timestamp in ISO 8601 format. |
| availabilityEndsAt |  | string | Date when access to content *ends*. Timestamp in ISO 8601 format. |
| publishStart	|  | string | Date when the asset *appears* on EPG and schedules. Timestamp in ISO 8601 format. |
| publishEnd	|  | string | Date when the asset *disappears* from EPG and schedules. Timestamp in ISO 8601 format. |

<br/>

<!--

##### Response object

| Field  | Parent  |Type  | Description | Notes 
|------:|---------|------|-------------|-------
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| *`metadata`*  | |   |   |   |  
| count      | *`metadata`* | number  | Count of items in response.  | min=1, max=100   
| totalCount | *`metadata`* | number | Total number of items available.  | |
| offset     | *`metadata`* | number | Number of items offset from the beginning of the list. | max=100
| *`assets`*   ||array||  |
| id |  | string | Unique ID for each asset  |  |
| resourceType |   | enum string | Always "assets"   | |
| pictureID |   | string | URL for the picture resource. |  | 
| duration|   | number | Video duration in minutes.  |  |
| live|   | boolean | Indicates if this is a live feed (true; uses liveURLs) or not (false; uses vodURLs).   |  |
| environment|   | string | Enum: prod or test  |  |
| vodURLs |  | string | URLs for video on demand sources. ||
| *`liveURLs`* |  |object| URLs for live feeds. | |
| *`dash`* | *`liveURLs`* |  object |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. | |
| primary | *`dash`* | string | Primary URL for the DASH source.   |  | 
|backup|*`dash`*|string|Backup URL for DASH source.| |
| *`hls`* | *`liveURLs`* | object | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.| |
| backup | *`hls`*|  string | Secondary URL for the HLS source. |   |
| primary | *`hls`* |string | Primary URL for the HLS source.   |  |
| publishStart |  | string | First date that this content is visible to end users. | ISO 8601 format |
| publishEnd |  | string | Last date that this content is visible to end users. | ISO 8601 format |

<br/>

-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/assets/{{assetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Body:***

```js        
{
    "id": "7f799b42-00ed-48e4-af0a-edecd82565ad",
    "resourceType": "assets",
    "publishStart": "2019-05-29T01:35:34.035Z",
    "published": true,
    "created": "2019-05-29T01:35:34.04Z",
    "updated": "2019-05-29T18:34:46.785Z",
    "contentLock": false,
    "pictureID": " ",
    "duration": 1200,
    "live": false,
    "environment": "prod",
    "liveURLs": null,
    "vodURLs": {
        "dash": {
            "backup": " ",
            "primary": "https://sparksports-vod.akamaized.net/spark/202/602df407-53fd-475f-9d92-54e6ace701b8/dash/001/602df407-53fd-475f-9d92-54e6ace701b8.mpd"
        },
        "hls": {
            "backup": " ",
            "primary": "https://sparksports-vod.akamaized.net/spark/202/602df407-53fd-475f-9d92-54e6ace701b8/dash/001/602df407-53fd-475f-9d92-54e6ace701b8.m3u8"
        }
    },
    "drmID": "",
    "availabilityStartsAt": "2019-02-02T01:00:00Z",
    "availabilityEndsAt": "2019-12-31T01:00:00Z",
    "regionIDs": null,
    "contentProvider": {
        "id": "spark",
        "category": "",
        "assetID": "20190529-ONEChampionshipWeeklyWeek22-01"
    }
}
```



### 3. Retrieve an asset


Returns descriptive metadata associated with the specified video asset.

<br/>

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|`assetID`|string|Yes|Asset identifier|

<br/>

##### Response object

| Field  | Parent  |Type  | Description |  
|-------:|---------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| *`assets`*   ||array||  |
| id |  | string | Unique ID for each asset  |  |
| resourceType |   | enum string | Always "assets"   | |
| pictureID |   | string | URL for the picture resource. |  | 
| duration|   | number | Video duration in minutes.  |  |
| live|   | boolean | Indicates if this is a live feed (true; uses liveURLs) or not (false; uses vodURLs).   |  |
| environment|   | string | Enum: prod or test  |  |
| vodURLs |  | string | URLs for video on demand sources. ||
| *`liveURLs`* |  |object| URLs for live feeds. | |
| *`dash`* | `liveURLs` |  object |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. | |
| primary | `dash` | string | Primary URL for the DASH source.   |  | 
| backup  | `dash` | string | Backup URL for DASH source.| |
|  *`hls`* | `liveURLs` | object | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.| |
| backup | `hls`|  string | Secondary URL for the HLS source. |   |
| primary | `hls` |string | Primary URL for the HLS source.   |  |

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station resources|
|404		|1040				|*Not Found*: No matching asset ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/assets/{{assetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Responses:***


Status: Retrieve a single asset | Code: 200



```js
{
    "requestID": "90aa12af-d1ed-4d61-9640-61a335ee891f",
    "timestamp": "2018-06-07T12:38:03.492540787Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "assets": [
        {
            "id": "e7d32347775f78daf1609c8e1bf5a850",
            "resourceType": "assets",
            "pictureID": "https://dtvlatamvod.akamaized.net/bugs/AnimalPlanet.jpg",
            "duration": 0,
            "live": false,
            "environment": "",
            "liveURLs": {
                "dash": {
                    "primary": "https://d30gb033f0paft.cloudfront.net/629831/dtv/animalplanet/master.mpd"
                },
                "hls": {
                    "backup": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879-b/dtv/AnimalPlanet-DTV/master.m3u8",
                    "primary": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879/dtv/AnimalPlanet-DTV/master.m3u8"
                }
            },
            "vodURLs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
		}
    ]
}
```



### 4. Retrieve an asset by provider asset  ID


<!-- Retrieve an asset -->

Returns the metadata associated with the specified video asset.

<br/>

##### Path Parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|providerAssetID|string| required | Provider asset identifier | 

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested asset|
|404		|1040				|*Not Found*: No matching asset ID found|

<br/>

<!--

##### Response object

| Field  | Parent  |Type  | Description | Notes 
|------:|---------|------|-------------|-------
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| *`metadata`*  | |   |   |   |  
| count      | `metadata` | number  | Count of items in response.  | min=1, max=100   
| totalCount | `metadata` | number | Total number of items available.  | |
| offset     | `metadata` | number | Number of items offset from the beginning of the list. | max=100
| *`assets`*   ||array||  |
| id |  | string | Unique ID for each asset  |  |
| resourceType |   | enum string | Always "assets"   | |
| pictureID |   | string | URL for the picture resource. |  | 
| duration|   | number | Video duration in minutes.  |  |
| live|   | boolean | Indicates if this is a live feed (true; uses liveURLs) or not (false; uses vodURLs).   |  |
| environment|   | string | Enum: prod or test  |  |
| vodURLs |  | string | URLs for video on demand sources. ||
| *`liveURLs`* |  |object| URLs for live feeds. | |
| *`dash`* | `liveURLs` |  object |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. | |
| primary | `dash` | string | Primary URL for the DASH source.   |  | 
| backup  | `dash` | string | Backup URL for DASH source.| |
|  *`hls`* | `liveURLs` | object | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.| |
| backup | `hls`|  string | Secondary URL for the HLS source. |   |
| primary | `hls` |string | Primary URL for the HLS source.   |  |

<br/>

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/assets
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| paid | {{providerAssetID}} |  |



***Responses:***


Status: Retrieve a single asset | Code: 200



```js
{
    "requestID": "90aa12af-d1ed-4d61-9640-61a335ee891f",
    "timestamp": "2018-06-07T12:38:03.492540787Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "assets": [
        {
            "id": "e7d32347775f78daf1609c8e1bf5a850",
            "resourceType": "assets",
            "pictureID": "https://dtvlatamvod.akamaized.net/bugs/AnimalPlanet.jpg",
            "duration": 0,
            "live": false,
            "environment": "",
            "liveURLs": {
                "dash": {
                    "primary": "https://d30gb033f0paft.cloudfront.net/629831/dtv/animalplanet/master.mpd"
                },
                "hls": {
                    "backup": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879-b/dtv/AnimalPlanet-DTV/master.m3u8",
                    "primary": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879/dtv/AnimalPlanet-DTV/master.m3u8"
                }
            },
            "vodURLs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
		}
    ]
}
```



### 5. Delete asset


Deletes the specified asset.


The asset will be deleted only if no other resources reference it. 
If the asset is referenced, the call returns `HTTP code 409` along with the IDs of the resources that reference the asset.

<br>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|assetID	|string |required	|ID for the target asset to be deleted.|

<br>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete target asset.|
|404		|1040	|*Not Found*: Target asset not found.|
|409		|1043	|*Conflict* : Target asset is referenced by other resources.|

<br>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/assets/{{assetID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |
| Content-Type | application/json |  |



### 6. Patch asset


Patches the specified asset resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the examples.

<br>

##### Path Parameters

|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|id|string |required	|ID of the asset to be updated. |

<br>

##### Body Parameters

| Field  | Parent  |Type  | Description |  
|------:|---------|------|-------------|
| pictureID || string, max=512 | ID for the standard image. |
| duration || number, min=0 | Video duration in minutes.  | 
| live || boolean | Indicates if this is a live feed (**true** = uses liveURLs) or not (**false** = uses vodURLs).  | 
| environment || string | Value may be either **test** or **prod** (production).  | 
| liveURLs ||object, allows null| URLs for live feeds. |
| dash |liveURLs|  object |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. |
| primary |dash| string, min=1 max=512 | Primary URL for the DASH source.   | 
| backup |dash|string, min=1 max=512|Backup URL for DASH source.|
| hls |liveURLs| object | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.|
| primary |hls| string, min=1 max=512 | Primary URL for the HLS source.   | 
| backup |hls| string, min=1 max=512 | Backup URL for the HLS source.   |
| vodURLs || object, allows null | URLs for video on demand sources. |
| dash |vodURLs|  object |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. |
| primary |dash| string, min=1 max=512 | Primary URL for the DASH source.   | 
| hls |vodURLs| object | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.|
| primary |hls| string, min=1 max=512 | Primary URL for the HLS source.   |
| drmID || string | DRM ID for the asset resource. |
| availabilityStartsAt || string, format=date-time | Date when access to content begins. Timestamp in ISO 8601 format. |
| availabilityEndsAt || string, format=date-time | Date when access to content ends. Timestamp in ISO 8601 format. |
| contentProvider || object, allows null | |
| id |contentProvider| string | Service provider ID. |
| category |contentProvider| string | Service provider category ID. |
| assetid |contentProvider| string | Service provider asset ID. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/assets/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |
| Accept | application/json |  |



***Body:***

```js        
{
    "availabilityStartsAt": "2020-02-16T00:00:00Z",
    "availabilityEndsAt": "2020-08-03T00:00:00Z",
    "contentProvider": {
        "id": "fe60dda3-b5fa-4e8d-8f91-c6de8995c059",
        "category": "1fd0a510cb6e8e2c07509fb85ba994ec",
        "assetID": "TITL2020021117050591"
    }
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "96e7c431-2c65-40dc-b80c-b6b2be3d4b48",
    "timestamp": "2020-03-21T18:00:11.903913Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "assets": [
        {
            "id": "4185fa14-9b09-4df4-8a2f-7c0c22451c9e",
            "resourceType": "assets",
            "publishStart": "2000-01-01T00:00:00Z",
            "published": true,
            "created": "2019-03-29T17:20:31.242Z",
            "updated": "2020-03-21T18:00:11.901Z",
            "contentLock": false,
            "pictureID": "8a1815ac-84f1-488a-9062-0e079eba2c45.png",
            "duration": 0,
            "live": false,
            "environment": "prod",
            "liveURLs": {
                "dash": {
                    "backup": "https://dtv-latam-abc.akamaized.net/dash/live/2013030-b/dtv/fox-ecuador-peru/master.mpd",
                    "primary": "https://dtv-latam-abc.akamaized.net/dash/live/2013030/dtv/fox-ecuador-peru/master.mpd"
                },
                "hls": {
                    "backup": "https://dtv-latam-abc.akamaized.net/hls/live/2013029-b/dtv/fox-ecuador-peru/master.m3u8",
                    "primary": "https://dtv-latam-abc.akamaized.net/hls/live/2013029/dtv/fox-ecuador-peru/master.m3u8"
                }
            },
            "vodURLs": null,
            "drmID": "4a9e2b56-6a18-4b3a-a061-8f7b26fd4ea7",
            "availabilityStartsAt": "2019-12-22T00:00:00Z",
            "availabilityEndsAt": "2100-01-01T00:00:00Z",
            "regionIDs": null,
            "contentProvider": {
                "id": "",
                "category": "",
                "assetID": ""
            }
        }
    ]
}
```



Status: Example 2 | Code: 200



```js
{
    "requestID": "54110491-c36d-40ba-9d8b-4ae84139f46b",
    "timestamp": "2020-03-21T18:10:39.981486Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "assets": [
        {
            "id": "74eb2948-a513-4afa-989a-582b7309b627",
            "resourceType": "assets",
            "publishStart": "2020-02-16T00:00:00Z",
            "publishEnd": "2020-08-03T00:00:00Z",
            "published": true,
            "created": "2020-02-12T19:25:48.358Z",
            "updated": "2020-03-21T18:10:39.978Z",
            "contentLock": false,
            "pictureID": "",
            "duration": 5256,
            "live": false,
            "environment": "prod",
            "liveURLs": null,
            "vodURLs": {
                "dash": {
                    "primary": "https://dtvlatam-vod6.akamaized.net/dtv/006/fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8/dash/001/fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8.mpd"
                },
                "hls": {
                    "primary": "https://dtvlatam-vod6.akamaized.net/dtv/006/fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8/hls/001/fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8.m3u8"
                }
            },
            "drmID": "fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8",
            "availabilityStartsAt": "2020-02-16T00:00:00Z",
            "availabilityEndsAt": "2020-08-03T00:00:00Z",
            "regionIDs": null,
            "contentProvider": {
                "id": "fe60dda3-b5fa-4e8d-8f91-c6de8995c059",
                "category": "1fd0a510cb6e8e2c07509fb85ba994ec",
                "assetID": "TITL2020021117050591"
            }
        }
    ]
}
```



Status: Example 3 | Code: 200



```js
{
    "requestID": "37a0866c-bb8c-484b-ab7a-b047e2e6a1be",
    "timestamp": "2020-03-21T18:13:12.672209Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "assets": [
        {
            "id": "74eb2948-a513-4afa-989a-582b7309b627",
            "resourceType": "assets",
            "publishStart": "2020-02-16T00:00:00Z",
            "publishEnd": "2020-08-03T00:00:00Z",
            "published": true,
            "created": "2020-02-12T19:25:48.358Z",
            "updated": "2020-03-21T18:13:12.669Z",
            "contentLock": false,
            "pictureID": "",
            "duration": 5256,
            "live": false,
            "environment": "prod",
            "liveURLs": null,
            "vodURLs": {
                "dash": {
                    "primary": "https://dtvlatam-vod6.akamaized.net/dtv/006/fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8/dash/001/fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8.mpd"
                },
                "hls": {
                    "primary": "https://dtvlatam-vod6.akamaized.net/dtv/006/fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8/hls/001/fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8.m3u8"
                }
            },
            "drmID": "fac27ca1-56aa-40f5-9fae-1d1c1e3e72c8",
            "availabilityStartsAt": "2020-02-16T00:00:00Z",
            "availabilityEndsAt": "2020-08-03T00:00:00Z",
            "regionIDs": null,
            "contentProvider": {
                "id": "fe60dda3-b5fa-4e8d-8f91-c6de8995c059",
                "category": "1fd0a510cb6e8e2c07509fb85ba994ec",
                "assetID": "TITL2020021117050591"
            }
        }
    ]
}
```



## v2/banners



### 1. Create banner


Creates a content banner "card" for use in collections.

<br/>

**Note: This API is available only for the new non-SportsRocket CMS.**

<br/>

##### Body Parameters

|Field  |Parent  |Type  |Required  |Description|
|---  |---  |---  |---    |---    |
|title  |    |string  |Yes    |Content main title|
|subtitle |    |string  |No      |Content subtitle|
|overlayText |  |string  |No      |Overlay ("badge") text|
|image  |    |string  |Yes    |Background image identifier|
|overlayImage |  |string  |No      |Overlay ("logo") image identifier|
|language  |  |string  |No      |Content language|
|`actions`  |  |array  |No      |Call to action parameters|
|type  |`actions`    |integer|Yes|OS platform: 0 = web, 1 = android, 2 = iOS|
|verb  |`actions`    |string|Yes|Action to take ("link" is the only verb currently used).|
|target  |`actions`    |string|Yes|Web URL or app view name|
|text  |`actions`    |string|Yes|Display text (typically for display in a button)|
| publishStart |  | string | (optional) First date that this content is visible to end users. | ISO 8601 format |
| publishEnd |  | string | (optional) Last date that this content is visible to end users. | ISO 8601 format |

<br/>

##### Error Responses

<!-- Which Orbis errors can cause the HTTP 400 error below??? -->

|HTTP Code|Error Code|Description|
|---|---|---|
|**400**| 1104, 1105 |*Bad request*: Unsupported key or value - key or value is misspelled or does not exist.|
|**401**| 1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**403**| 1004 |*Forbidden* to write to the requested resource.|

<br/>

<!-- The metadata fields below are confusing.  -->
<!-- These should be standardized along with the pagination field names used in other endpoints. -->

##### Response Object

| Field  | Parent  |Type  | Description |  
|------:|---|------|-------------|
| requestID || string | Generated log ID for this request.    |   | 
| timestamp || string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/banners
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | Content data type returned (string). |



***Body:***

```js        
{
    "resourceType": "banners",
    "title": "Second banner",
    "subtitle": "Another big event",
    "overlayText": "LIVE",
    "image": "ec6938e37fb95efc6d5eccaa25afa7f5.png",
    "overlayImage": "19e16a35aef87a171a04a744e4360a4e.png",
    "actions": [
        {
            "type": 2,
            "verb": "view",
            "target": "www.comingsoon.orbis.com/the-match",
            "text": "More Information"
        }
    ],
    "language": "en",
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



### 2. Update banner


Updates the specified existing banner.

<br/>

**Note: This API is available only for the new non-SportsRocket CMS.**

<br/>

##### Path Parameters

|Field  |Type  |Required|Description|
|---  |---  |---  |---  |
|bannerID  |string|Yes|Unique resource identifier of the banner item being updated.|

<br/>

##### Body Parameters

|Field  |Parent  |Type  |Required  |Description|
|---  |---  |---  |---    |---    |
|title  |    |string  |Yes    |Content main title|
|subtitle |    |string  |No      |Content subtitle|
|overlayText |  |string  |No      |Overlay ("badge") text|
|image  |    |string  |Yes    |Background image identifier|
|overlayImage |  |string  |No      |Overlay ("logo") image identifier|
|language  |  |string  |No      |Content language|
|`actions`  |  |array  |No      |Call to action parameters|
|type  |`actions`    |integer|Yes|Call to action type: 0 = web, 1 = android, 2 = iOS|
|verb  |`actions`    |string|Yes|Action to take ("link" is the only verb currently used).|
|target  |`actions`    |string|Yes|Web URL or app view name|
|text  |`actions`    |string|Yes|Display text (typically for display in a button)|
| publishStart |  | string | (optional) First date that this content is visible to end users. | ISO 8601 format |
| publishEnd |  | string | (optional) Last date that this content is visible to end users. | ISO 8601 format |

<br/>

##### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**400**|1103, 1104, 1105|*Bad request*: Request body malformed.|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**403**|1004|*Forbidden*: Cannot update the requested resource.|
|**404**|1040|*Not found*: Requested resource ID missing, deleted, or incorrect.|

<br/>

<!-- The metadata fields below are confusing.  -->
<!-- These should be standardized along with the pagination field names used in other endpoints. -->

##### Response Object

| Field | Parent   |Type  | Description |  
|------:|----------|------|-------------|
| requestID || string | Generated log ID for this request.    |   | 
| timestamp || string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/banners/{{bannerID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | Content data type returned (string). |



***Body:***

```js        
{
	"resourceType": "banners",
	"title": "Coming soon",
	"subtitle": "A big event!!",
	"overlayText": "LIVE",
	"image": "ec6938e37fb95efc6d5eccaa25afa7f5.png",
	"overlayImage": "19e16a35aef87a171a04a744e4360a4e.png",
	"actions": [{
		"type": 2,
		"verb": "view",
		"target": "www.comingsoon.orbis.com/the-match",
		"text": "More Information"
	}],
	"language": "en",
	"publishStart": "2019-01-01T15:00:00Z",
	"publishEnd": "2020-09-01T07:00:00Z"
}
```



### 3. Retrieve banner


Gets the specified content banner.
<br/>
<br/>
**Note: This API is available only for the new non-SportsRocket CMS.**
<br/>
<br/>

##### Path Parameters

|Field	|Type	|Required|Description|
|---	|---	|---	|---	|
|bannerID	|string|Yes|Unique identifier of requested banner item.|

<br/>

##### Error Responses 
|HTTP Code|Error Code|Description|
|---|---|---|
|**400**|1050, 1060|*Bad Request*: Response data bad or incomplete|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired|
|**403**|1003	|*Forbidden*: Cannot read the requested resource|
|**404**|1040	|*Not found*: Requested resource ID missing, deleted, or incorrect|

<br/>

##### Response Object 

<!-- The metadata fields below are confusing.  -->
<!-- These should be standardized along with the pagination field names used in other endpoints. -->

| Field  | Parent | Type | Description |  
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| *`bannerItems`* |   | array |  List of banner resources |   |
|id			|*`bannerItems`*|string|Unique identifier|	|
|resourceType|*`bannerItems`*|string|Value is always "_banner_". | |
|name		|*`bannerItems`*|string|Content name|	|
|shortName	|*`bannerItems`*|string|Abbreviated name|	|
|overlayText	|*`bannerItems`*|string|Overlay ("badge") text|	|
|image	|*`bannerItems`*|string|Background image ID|	|
|overlayImage	|*`bannerItems`*|string|Overlay ("logo") image ID|	|
|actions|*`bannerItems`*|array|Calls to action|	|
|language	|*`bannerItems`*|string|Content language|	|
| publishStart |  | string | First date that this content is visible to end users. ISO 8601 format |
| publishEnd |  | string | Last date that this content is visible to end users. ISO 8601 format |

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/banners/{{bannerID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get genre | Code: 200



```js
{
	"requestID":"c91fa0a7-f82c-4b18-a701-7a59a5ec779e",
	"timestamp":"2018-06-07T12:52:49.671562729Z",
	"metadata": 
	{
 		"count":1,
 		"totalCount":1,
 		"offset":0 
 	},
	"genres": 
	[
		{
 			"id":"067d70ff2bcc556a913e52da08cc9139",
			"resourceType":"genres",
			"name":"Adventure",
			"shortName":"Adventure",
			"language":"es"
		}
	]
}
```



### 4. List all banners


Gets the list of available content banners.

<br/>

**Note: This API is available only for the new non-SportsRocket CMS.**

<br/>

##### Error Responses 
|HTTP Code|Error Code|Description|
|---|---|---|
|**400**|1050, 1060|*Bad Request*: Response data bad or incomplete|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**403**|1003	|*Forbidden*: Cannot read the requested resource|
|**404**|1040	|*Not found*: Requested resource ID missing, deleted, or incorrect.|

<br/>

##### Response Object 

<!-- The metadata fields below are confusing.  -->
<!-- These should be standardized along with the pagination field names used in other endpoints. -->

| Field  | Parent | Type | Description |  
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| *`bannerItems`* |   | array |  List of banner resources |   |
|id			|*`bannerItems`*|string|Unique identifier|	|
|resourceType|*`bannerItems`*|string|Value is always "_banner_". | |
|name		|*`bannerItems`*|string|Content name|	|
|shortName	|*`bannerItems`*|string|Abbreviated name|	|
|overlayText	|*`bannerItems`*|string|Overlay ("badge") text|	|
|image	|*`bannerItems`*|string|Background image ID|	|
|overlayImage	|*`bannerItems`*|string|Overlay ("logo") image ID|	|
|actions|*`bannerItems`*|array|Calls to action|	|
|language	|*`bannerItems`*|string|Content language|	|
| publishStart |*`bannerItems`* | string | First date that this content is visible to end users. ISO 8601 format |
| publishEnd |*`bannerItems`* | string | Last date that this content is visible to end users. ISO 8601 format |

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/banners
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Get genre | Code: 200



```js
{
	"requestID":"c91fa0a7-f82c-4b18-a701-7a59a5ec779e",
	"timestamp":"2018-06-07T12:52:49.671562729Z",
	"metadata": 
	{
 		"count":1,
 		"totalCount":1,
 		"offset":0 
 	},
	"genres": 
	[
		{
 			"id":"067d70ff2bcc556a913e52da08cc9139",
			"resourceType":"genres",
			"name":"Adventure",
			"shortName":"Adventure",
			"language":"es"
		}
	]
}
```



### 5. Delete banner


Deletes the specified existing banner.
<br/>
<br/>
**Note: This API is available only for the new non-SportsRocket CMS.**
<br/>
<br/>
##### Path Parameters

|Field	|Type	|Required|Description|
|---	|---	|---	|---	|
|bannerID	|string|Yes|Unique identifier for the specified content banner.|

<br/>

##### Error Responses 
|HTTP Code|Error Code|Description|
|---|---|---|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**403**|1004	|*Forbidden*: Cannot delete the requested resource|
|**404**|1040	|*Not found*: Requested resource ID missing, deleted, or incorrect.|

<!-- Update these error messages and have them checked. -->

<br/>

<!--

##### Response Object

| Field |Type  | Description | Notes 
|------:|------|-------------|-------
| requestID | string | Generated log ID for this request.    |   | 
| timestamp | string | Generated log timestamp for this request.  |   |

<br/>

-->


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/banners/{{bannerID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | Content data type returned (string). |



### 6. Patch banner


Patches the specified banner resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the banner to be updated. |

<br>

##### Body Parameters

|Field  |Parent  |Type  |Description|
|---	|---  |--- |---    |
| publishStart |  | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd  |   | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| title  |    | string      |Content main title|
| subtitle |    | string       |Content subtitle|
| overlayText |  | string       |Overlay ("badge") text|
| image  |    | string     |Background image identifier|
| overlayImage |  | string        |Overlay ("logo") image identifier|
| actions  |  | array        |Call to action parameters|
| type	| actions    |integer|Call to action type: 0 = web, 1 = android, 2 = iOS|
| verb	| actions    |string|Action to take ("link" is the only verb currently used).|
| target | actions    |string|Web URL or app view name|
| text	| actions    |string|Display text (typically for display in a button)|
| language  |  | string        |Content language|


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/banners/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "title": "Conciertos",
    "image": "24d70df4-55f6-42a6-8ed9-715d8f455c3d.jpg",
    "overlayImage": "c2dac73c-6818-4871-883a-29fe00632ab0.jpg",
    "actions": [
        {
            "type": 0,
            "verb": "link",
            "target": "1SSLAOnStageLeyendas",
            "text": "Leyendas"
        }
    ],
    "language": "en"
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "85f5442b-2487-4363-b50e-65285b15c51c",
    "timestamp": "2020-03-25T20:06:35.348147Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "banners": [
        {
            "id": "92997e3d-26a4-4673-a683-e8a93bac2505",
            "resourceType": "banners",
            "publishStart": "2019-11-13T19:27:00.25Z",
            "published": true,
            "created": "2019-11-13T19:27:00.331Z",
            "updated": "2020-03-25T20:06:35.344Z",
            "contentLock": true,
            "title": "Conciertos",
            "image": "24d70df4-55f6-42a6-8ed9-715d8f455c3d.jpg",
            "overlayImage": "c2dac73c-6818-4871-883a-29fe00632ab0.jpg",
            "actions": [
                {
                    "type": 0,
                    "verb": "link",
                    "target": "1SSLAOnStageLeyendas",
                    "text": "Leyendas"
                }
            ],
            "language": "en"
        }
    ]
}
```



## v2/entities



### 1. Retrieve entity resource information


Returns descriptive information about the specified resource.

The resource may be of any type including shows, seasons, episodes, competitions, vod/movies, etc.

<br/>

##### Path Parameters
|Name|Data type|Required|Description|
|---|---|---|---|
|entityID|string|required|Entity identifier for the target resource.|

<br/>

##### Response object 
| Field  | Parent | Type | Description | 
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |  
| timestamp | | string | Generated log timestamp for this request.  |  
| `metadata`|	| object | Pagination fields.  |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| `entities` |   | array | List of resource entities.  | 
|**varies**|`entities`|object| Fields listed vary according to each type of entity retrieved. |

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested asset information|
|404		|1040				|*Not Found*: No matching entity ID found|

<br/>

<!-- NOTES
	1.	Endpoint was saved as "{{OCMServer}}/ocm/v2/entities/deee901311f2842307957ea285596b00?language=*"
		EPC reset the endpoint as "GET /ocm/v2/entities/{entityID}" which was in the documentation.
	
	2.	Enpoint was named "Returns information about any type of resource, including show, season, episode, competition, team, etc."
		EPC renamed the endpoint to "Retrieve entity resource information" (which is asset `metadata`)
	
	3.	Need to set "request parameters" in the correct format
	
	4.	The *``metadata``* field should be renamed to `pagination`
-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/entities/{{entityID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| If-None-Match | {{If-None-Match}} | Optional. Cache control header for reads. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | linked | Optional. Includes information about linked resources in the response. Value must be __linked__. |
| linkedType | shows | Optional. Filters response to include only linked entities of the specified type. Value may be any entity type (__shows, vod/movies, episodes__, etc.)  |



***Responses:***


Status: Returns information about any type of resource, including show, season, episode, competition, team, etc. | Code: 200



```js
{
    "requestID": "e2b73a9c-6ad4-4e54-836d-66197f881747",
    "timestamp": "2018-06-07T12:38:57.443254621Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "entities": [
        {
            "id": "e7d32347775f78daf1609c8e1bf5a850",
            "resourceType": "assets",
            "pictureID": "https://dtvlatamvod.akamaized.net/bugs/AnimalPlanet.jpg",
            "duration": 0,
            "live": false,
            "environment": "",
            "liveURLs": {
                "dash": {
                    "primary": "https://d30gb033f0paft.cloudfront.net/629831/dtv/animalplanet/master.mpd"
                },
                "hls": {
                    "backup": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879-b/dtv/AnimalPlanet-DTV/master.m3u8",
                    "primary": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879/dtv/AnimalPlanet-DTV/master.m3u8"
                }
            },
            "vodURLs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
		}
    ]
}
```



### 2. List Entities


Returns descriptive metadata about the specified resources.

The resources may be of any type including show, season, episode, competition, team, etc.

<br/>

##### Body Parameters
| Field  | Parent | Type | Description |  
|------:|--------|------|-------------|
| entityIDs | | string array | List of IDs for the target resources.    |   | 

<br/>

<!--

##### Path Parameters
|Name|Data type|Required|Description|
|---|---|---|---|
|entityID|string|required|Entity identifier for the target resource.|

<br/>

-->

##### Response object 
| Field  | Parent | Type | Description |  
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| `entities` |   | array |   |   |
|**varies**|`entities`|object| | Specific fields listed here depend on the entity types.	|

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested resources|

<!--|404		|1040				|*Not Found*: No matching station ID found|-->

<br/>

<!-- NOTES
	1.	Endpoint was saved as "{{OCMServer}}/ocm/v2/entities/deee901311f2842307957ea285596b00?language=*"
		EPC reset the endpoint as "GET /ocm/v2/entities/{entityID}" which was in the documentation.
	
	2.	Enpoint was named "Returns information about any type of resource, including show, season, episode, competition, team, etc."
		EPC renamed the endpoint to "Retrieve entity resource information" (which is asset `metadata`)
	
	3.	The *``metadata``* field should be renamed to `pagination`
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/entities/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |
| Content-Type | application/json | <string> |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| published | pub,unpub | Indicates whether response results include assets that are **pub**lished, **unpub**lished, or both. |



***Body:***

```js        
{
    "entityIDs": [
        "816bc916-5997-4fc2-9865-2e98344c9fca",
        "db1d60f5-c91e-4faf-82d6-638703de406d"
    ]
}
```



***Responses:***


Status: Returns information about any type of resource, including show, season, episode, competition, team, etc. | Code: 200



```js
{
    "requestID": "e2b73a9c-6ad4-4e54-836d-66197f881747",
    "timestamp": "2018-06-07T12:38:57.443254621Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "entities": [
        {
            "id": "e7d32347775f78daf1609c8e1bf5a850",
            "resourceType": "assets",
            "pictureID": "https://dtvlatamvod.akamaized.net/bugs/AnimalPlanet.jpg",
            "duration": 0,
            "live": false,
            "environment": "",
            "liveURLs": {
                "dash": {
                    "primary": "https://d30gb033f0paft.cloudfront.net/629831/dtv/animalplanet/master.mpd"
                },
                "hls": {
                    "backup": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879-b/dtv/AnimalPlanet-DTV/master.m3u8",
                    "primary": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879/dtv/AnimalPlanet-DTV/master.m3u8"
                }
            },
            "vodURLs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
		}
    ]
}
```



### 3. Link entities


Creates a link between the listed entities. The entities may be of any type including shows, seasons, episodes, vod/movies, teams, etc.

<br>

When [retrieving entity resource information](https://docs.dtc.istreamplanet.net/?version=latest#65081fb1-665d-431b-b287-4f15090f68d1): 

* You can include linked resources in any request by adding the "include=linked" query parameter.
* You can additionally filter these linked resources by type using the "linkedType={type}" query parameter.

<br/>

##### Body Parameters
|Name|Data type|Required|Description|
|---|---|---|---|
|entityIDs|string array|required| List of entity identifiers. |


<br/>

##### Response object 
| Field  | Parent | Type | Description |  
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| `entities`|   | array | List of resource entities.  |
|id			|`entities`|string	| Resource ID.	|
|resourceType|`entities`|string	| Resource type: shows, vod/movies, etc.	|
|published	|`entities`|boolean	| Whether the item is publically available.	|
|name		|`entities`|string	| Resource name.	|
|linkIDs	|`entities`|array	| List of linked resources.	|

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested resources|

<br/>


<!-- NOTES
	1.	Endpoint was saved as "{{OCMServer}}/ocm/v2/entities/deee901311f2842307957ea285596b00?language=*"
		EPC reset the endpoint as "GET /ocm/v2/entities/{entityID}" which was in the documentation.
	
	2.	Enpoint was named "Returns information about any type of resource, including show, season, episode, competition, team, etc."
		EPC renamed the endpoint to "Retrieve entity resource information" (which is asset `metadata`)
	
	3.	Need to set "request parameters" in the correct format
	
	4.	The *``metadata``* field should be renamed to `pagination`

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/entities/link/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "entityIDs": [
        "97871b99-c2c5-4b27-a53b-a61fc8a5cff6",
        "7f13daa9-fcce-4dad-b86a-53c6d3fe1e21"
    ]
}
```



***Responses:***


Status: Returns information about any type of resource, including show, season, episode, competition, team, etc. | Code: 200



```js
{
    "requestID": "e2b73a9c-6ad4-4e54-836d-66197f881747",
    "timestamp": "2018-06-07T12:38:57.443254621Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "entities": [
        {
            "id": "e7d32347775f78daf1609c8e1bf5a850",
            "resourceType": "assets",
            "pictureID": "https://dtvlatamvod.akamaized.net/bugs/AnimalPlanet.jpg",
            "duration": 0,
            "live": false,
            "environment": "",
            "liveURLs": {
                "dash": {
                    "primary": "https://d30gb033f0paft.cloudfront.net/629831/dtv/animalplanet/master.mpd"
                },
                "hls": {
                    "backup": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879-b/dtv/AnimalPlanet-DTV/master.m3u8",
                    "primary": "https://cbcdtvanimalplnt-i.akamaihd.net/hls/live/627879/dtv/AnimalPlanet-DTV/master.m3u8"
                }
            },
            "vodURLs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
		}
    ]
}
```



## v2/epg/competitions



### 1. Create EPG competition


Creates a scheduled EPG competition entry.

<br/>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Name  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| resourceType |    | enum string | Required. Contains the value "epg/competitions". | 
| startTime |   	| string | Required. A timestamp in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. A timestamp in ISO-8601 timestamp format.  |  
| duration |    	| number | Required. Video duration in minutes.  |  
| name |    		| string | Required. Full name. (max char length?) |
| shortName |   	| string | Shortened name.   (max char length?) |
| description |     | string | Full description. (max char length?) |
| shortDescription| | string | Shortened description. (max char length?) |
| language |    	| string | Required. Two-letter code for the spoken language.  |
| ratings |     	| string array | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string array | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this competition. | 
| genreIDs |    	| string array | List of genre IDs associated with this competition. | 
| genres |    		| string array | List of genres associated with this competition. | 
| regionIDs |    	| string array | List of region IDs associated with this competition. | 
| sportID |     	| string | ID for the sport associated with this competition. | 
| sportName |   	| string | Name for the sport associated with this competition. | 
| tournamentID |    | string | ID for the tournament associated with this competition. | 
| tournamentName |  | string | Name for the tournament associated with this competition. | 
| primaryPersonID |     	| string | ID for the primary or home competitor. | 
| primaryPersonName |   	| string | Name for the primary or home competitor. | 
| primaryPersonPictureID |  | string | ID for picture of the primary or home competitor.| 
| secondaryPersonID |   	| string | ID for the secondary or away competitor. | 
| secondaryPersonName |     | string | Name for the secondary or away competitor. | 
| secondaryPersonPictureID| | string | ID for picture of the secondary or away competitor. | 
| assetIDs |    	| string array | Comma-separated list of asset IDs to associate with this EPG competition. |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this competition. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  

<br/>

<!--
NOTE: The following fields are currently NOT included in this endpoint: 
leagueID, leagueName, gameID, venue
-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/competitions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "epg/competitions",
    "startTime": "2018-04-26T10:30:00Z",
    "endTime": "2018-04-26T11:00:00Z",
    "duration": 1800,
    "name": "Márcio Lima",
    "shortName": "Márcio Lima",
    "description": "BOB Márcio Lima é um instrutor de rapel em caverna, proprietário da Lobo Guará Bike Adventure e guia de mountain bike. Trabalha com sustentabilidade, saúde para o corpo e contribuições ao meio ambiente.",
    "shortDescription": "Márcio Lima é um instrutor de rapel.",
    "language": "pt",
    "pictureID": "asdf",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
    ],
    "ratingAdvisories": null,
    "stationID": "",
    "genreIDs": null,
    "genres": null,
    "regionIDs": null,
    "sportID": "",
    "sportName": "",
    "tournamentID": "",
    "tournamentName": "",
    "primaryPersonID": "",
    "primaryPersonName": "",
    "primaryPersonPictureID": "",
    "secondaryPersonID": "",
    "secondaryPersonName": "",
    "secondaryPersonPictureID": "",
    "assetIDs": null
}
```



### 2. Update scheduled competition


Updates the EPG entry for the specified competition.

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID for the target EPG competition entry. |

<br/>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Name  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| resourceType |    | enum string | Required. Contains the value "epg/competitions". | 
| startTime |   	| string | Required. Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number | Required. Video duration in minutes.  |  
| name |    		| string | Required. Full name. . . |
| shortName |   	| string | Shortened name. . . |
| description |     | string | Full description. . .|
| shortDescription| | string | Shortened description. . .|
| language |    	| string | Required. Two-letter code for the spoken language.  |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this competition. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  
| ratings |     	| string list | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this competition. | 
| genreIDs |    	| string list | List of genre IDs associated with this competition. | 
| genres |  		| string list | List of genres associated with this competition. | 
| regionIDs |    	| string list | List of region IDs associated with this competition. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this EPG competition. |
| sportID |     	| string | ID for the sport associated with this competition. | 
| sportName |   	| string | Name for the sport associated with this competition. | 
| gameID |    		| string | ID for the game associated with this competition. | 
| tournamentID |    | string | ID for the tournament associated with this competition.  | 
| tournamentName |  | string | Name for the tournament associated with this competition. | 
| primaryPersonID |     	| string | ID for the primary or home competitor. | 
| primaryPersonName |   	| string | Name for the primary or home competitor. | 
| primaryPersonPictureID |  | string | ID for picture of the primary or home competitor. | 
| secondaryPersonID | 	  | string | ID for the secondary or away competitor. | 
| secondaryPersonName |     | string | Name for the secondary or away competitor. | 
| secondaryPersonPictureID| | string | ID for picture of the secondary or away competitor. | 

<br/>

<!--

NOTE: The following fields are currently NOT included in this endpoint: 
venue, genres, regionIDs 

We should also include the maximum character lengths for the name, shortName, description and shortDescription fields.

-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/competitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Body:***

```js        
{
    "resourceType": "epg/competitions",
    "startTime": "2018-04-26T10:30:00Z",
    "endTime": "2018-04-26T11:00:00Z",
    "duration": 30,
    "name": "Márcio Lima",
    "shortName": "Márcio Lima",
    "description": "BOB Márcio Lima é um instrutor de rapel em caverna, proprietário da Lobo Guará Bike Adventure e guia de mountain bike. Trabalha com sustentabilidade, saúde para o corpo e contribuições ao meio ambiente.",
    "shortDescription": "Márcio Lima é um instrutor de rapel.",
    "language": "pt",
    "pictureID": "asdf",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
    ],
    "ratingAdvisories": null,
    "stationID": "",
    "genreIDs": null,
    "genres": null,
    "regionIDs": null,
    "sportID": "",
    "sportName": "",
    "gameID": "1234",
    "tournamentID": "",
    "tournamentName": "",
    "primaryPersonID": "",
    "primaryPersonName": "",
    "primaryPersonPictureID": "",
    "secondaryPersonID": "",
    "secondaryPersonName": "",
    "secondaryPersonPictureID": "",
    "assetIDs": null
}
```



### 3. Retrieve scheduled game from the EPG


Retrieves the specified scheduled game from the EPG.

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested scheduled game|
|404		|1040				|*Not Found*: No matching scheduled game ID found|

<br/>

<!--

#### Response object
The Notes column describes default and possible values, valid ranges, and fields that are nullable ( ø ), or required ( ʀ ). All fields are optional unless otherwise indicated.

<br>

| Name  | Parent |  Type  | Description | Notes
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata` |   |    |    |   |  
| count | metadata |number  | Current screen.  | min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  | min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. | min=1, max = 20
||||||
| *`epg/competitions`* |   |   |      |  |
| id | epg/competitions |string | Unique ID for each asset.  |  |
| resourceType | epg/competitions | enum string | "epg/competitions" | |
| startTime | epg/competitions | string | A timestamp.  |  |
| endTime | epg/competitions | string | A timestamp.  |  |
| duration | epg/competitions | number | Video duration in minutes.  |  |
| name | epg/competitions | string | Full name.  | (max char length?) |
| shortName | epg/competitions | string |   | (max char length?) |
| description | epg/competitions | string | Full description.  | (max char length?) |
| shortDescription | epg/competitions | string |   | (max char length?) |
| language | epg/competitions | string | Two-letter code for the spoken language.  |  |
| ratings | epg/competitions | string | Age-related ratings from boards and agencies. | ø  |
| ratingAdvisories | epg/competitions | string list | A list of content advisories.  | ø, Such as "Adult Situations", "Language", or "Violence" |
| stationID | epg/competitions | string  |  | |
| genreIDs | epg/competitions | string | | ø; |
| sportID | epg/competitions | string | | |
| sportName | epg/competitions | string | | |
| tournamentID | epg/competitions | string | | |
| tournamentName | epg/competitions | string | | |
| primaryPersonID | epg/competitions | string | | |
| primaryPersonName | epg/competitions | string | | |
| primaryPersonPictureID | epg/competitions | string | | |
| secondaryPersonID | epg/competitions | string | | |
| secondaryPersonName | epg/competitions | string | | |
| secondaryPersonPictureID | epg/competitions | string | | |
| assetIDs | epg/competitions | string | | ø; |
| pictureID | epg/competitions | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/competitions |  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. |  | 
| 3x4  | pictures | string | ID for a 3x4 image.  |  | 
| 4x3  | pictures | string | ID for a 4x3 image.  |  | 
| 16x9 | pictures | string | ID for a 16x9 image.  |  | 

<br/>

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/competitions/{{gameID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Retrieve scheduled game from the EPG | Code: 200



```js
{
    "requestID": "3615a4c8-5eef-48c3-817f-7c51b0996629",
    "timestamp": "2018-05-15T04:22:29.721400028Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/competitions": [
        {
            "id": "4ec20201a14219cd9331c456c5418a94",
            "resourceType": "epg/competitions",
            "startTime": "2018-04-27T10:46:00Z",
            "endTime": "2018-04-27T11:40:00Z",
            "duration": 0,
            "name": "Batallas con Marlines",
            "shortName": "Batallas con Marlines",
            "description": "Cyril está en Costa Rica por una razón importante. La búsqueda del pez más grande y poderoso del océano (450 kg), el pez espada.",
            "shortDescription": "La búsqueda del pez espada.",
            "language": "es",
            "pictureID": "7ea58145199cbae11657ed24007928e0",
            "pictures": {
                "2x3": "04aaa1f2a9a7b2c38e95104494b81cdf",
                "3x4": "e7f7e8986dcc8d6a91d25af310d89911",
                "4x3": "8639a78516070c5214ce6e7112cd6690",
                "16x9": "7ea58145199cbae11657ed24007928e0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Film & Publication Board}/{}/{10-12 PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "sportID": "",
            "sportName": "",
            "tournamentID": "",
            "tournamentName": "",
            "primaryPersonID": "",
            "primaryPersonName": "",
            "primaryPersonPictureID": "",
            "secondaryPersonID": "",
            "secondaryPersonName": "",
            "secondaryPersonPictureID": "",
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
		}
    ]
}
```



### 4. Retrieve scheduled game from the EPG with assets


Retrieves the specified scheduled game (assets included) from the EPG.

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested scheduled game|
|404		|1040				|*Not Found*: No matching scheduled game ID found|

<br/>

<!--

Original URL: {{OCMServer}}/ocm/v2/epg/competitions/4ec20201a14219cd9331c456c5418a94?language=*&include=assets

##### Response object
The Notes column describes default and possible values, valid ranges, and fields that are nullable ( ø ), or required ( ʀ ). All fields are optional unless otherwise indicated.


| Name  | Parent |  Type  | Description | Notes
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata` |   |    |    |   |  
| count | metadata |number  | Current screen.  | min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  | min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. | min=1, max = 20
||||||
| *`epg/competitions`* |   |   |      |  |
| id | epg/competitions |string | Unique ID for each asset.  |  |
| resourceType | epg/competitions | enum string | "epg/competitions" | |
| startTime | epg/competitions | string | A timestamp.  |  |
| endTime | epg/competitions | string | A timestamp.  |  |
| duration | epg/competitions | number | Video duration in minutes.  |  |
| name | epg/competitions | string | Full name.  | (max char length?) |
| shortName | epg/competitions | string |   | (max char length?) |
| description | epg/competitions | string | Full description.  | (max char length?) |
| shortDescription | epg/competitions | string |   | (max char length?) |
| language | epg/competitions | string | Two-letter code for the spoken language.  |  |
| ratings | epg/competitions | string | Age-related ratings from boards and agencies. | ø  |
| ratingAdvisories | epg/competitions | string list | A list of content advisories.  | ø, Such as "Adult Situations", "Language", or "Violence" |
| stationID | epg/competitions | string  |  | |
| genreIDs | epg/competitions | string | | ø; |
| sportID | epg/competitions | string | | |
| sportName | epg/competitions | string | | |
| tournamentID | epg/competitions | string | | |
| tournamentName | epg/competitions | string | | |
| primaryPersonID | epg/competitions | string | | |
| primaryPersonName | epg/competitions | string | | |
| primaryPersonPictureID | epg/competitions | string | | |
| secondaryPersonID | epg/competitions | string | | |
| secondaryPersonName | epg/competitions | string | | |
| secondaryPersonPictureID | epg/competitions | string | | |
| assetIDs | epg/competitions | string | | ø; |
| pictureID | epg/competitions | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/competitions |  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. |  | 
| 3x4  | pictures | string | ID for a 3x4 image.  |  | 
| 4x3  | pictures | string | ID for a 4x3 image.  |  | 
| 16x9 | pictures | string | ID for a 16x9 image.  |  | 

<br/>
-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/competitions/{{gameID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | assets | Includes descriptive metadata. |



***Responses:***


Status: Retrieve scheduled game from the EPG | Code: 200



```js
{
    "requestID": "3615a4c8-5eef-48c3-817f-7c51b0996629",
    "timestamp": "2018-05-15T04:22:29.721400028Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/competitions": [
        {
            "id": "4ec20201a14219cd9331c456c5418a94",
            "resourceType": "epg/competitions",
            "startTime": "2018-04-27T10:46:00Z",
            "endTime": "2018-04-27T11:40:00Z",
            "duration": 0,
            "name": "Batallas con Marlines",
            "shortName": "Batallas con Marlines",
            "description": "Cyril está en Costa Rica por una razón importante. La búsqueda del pez más grande y poderoso del océano (450 kg), el pez espada.",
            "shortDescription": "La búsqueda del pez espada.",
            "language": "es",
            "pictureID": "7ea58145199cbae11657ed24007928e0",
            "pictures": {
                "2x3": "04aaa1f2a9a7b2c38e95104494b81cdf",
                "3x4": "e7f7e8986dcc8d6a91d25af310d89911",
                "4x3": "8639a78516070c5214ce6e7112cd6690",
                "16x9": "7ea58145199cbae11657ed24007928e0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Film & Publication Board}/{}/{10-12 PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "sportID": "",
            "sportName": "",
            "tournamentID": "",
            "tournamentName": "",
            "primaryPersonID": "",
            "primaryPersonName": "",
            "primaryPersonPictureID": "",
            "secondaryPersonID": "",
            "secondaryPersonName": "",
            "secondaryPersonPictureID": "",
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
		}
    ]
}
```



### 5. Delete EPG competition


Deletes the specified EPG competition. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|ID	|string		|required	|ID for the targeted EPG competition. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified EPG competition.|
|404		|1040	|*Not Found*: No matching EPG competition ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/competitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request.   |
| Content-Type | application/json | ETag header for cache validation. |



### 6. Patch EPG competition


Patches the specified EPG competition resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the EPG competition to be updated. |

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this resource. | 
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| blackoutRegionIDs | | string list, allows null | |
| metadata |        | object | The metadata provider information for this resource.  |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| sportID |     	| string | ID for the sport associated with this resource. | 
| sportName |   	| string | Name for the sport associated with this resource. | 
| leagueID |        | string | |
| leagueName |      | string | |
| tournamentID |    | string | ID for the tournament associated with this resource.  | 
| tournamentName |  | string | Name for the tournament associated with this resource. | 
| gameID |    		| string | ID for the game associated with this resource. | 
| primaryPersonID |     	| string | ID for the primary or home competitor. | 
| primaryPersonName |   	| string | Name for the primary or home competitor. | 
| primaryPersonPictureID |  | string | ID for picture of the primary or home competitor. | 
| secondaryPersonID | 	  | string | ID for the secondary or away competitor. | 
| secondaryPersonName |     | string | Name for the secondary or away competitor. | 
| secondaryPersonPictureID| | string | ID for picture of the secondary or away competitor. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/competitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
 {
            "name": "Automovilismo NASCAR Cup Series",
            "shortName": "Automovilismo NASCAR Cup Series",
            "description": "Se disputa una nueva jornada de la NASCAR Cup Series. Desde el Atlanta Motor Speedway, en Hampton, Georgia.",
            "shortDescription": "Desde el Atlanta Motor Speedway, en Hampton, Georgia, Estados Unidos.",
            "language": "es",
            "pictureID": "aea6b061-d6d8-4c56-8f81-d4c65960de3f.jpg",
            "pictures": {
                "16x9": "aea6b061-d6d8-4c56-8f81-d4c65960de3f.jpg",
                "1x1": "193f49f1-bebd-4d45-bac2d-a3ef03769885.jpg",
                "2x3": "f0ad4369-aab1-403d-8c56-1083a21cca2f.jpg",
                "3x4": "a9cc793b-2687-480f-9eaf-1b3643c3b6d1.jpg",
                "4x3": "9eb7eada-b6b6-4432-8b16-ad0c63bdbe66.jpg"
            },
            "assetIDs": [
                "2d96cd46c4349079dbf9e6a6f0f723d5"
            ],
            "regionIDs": [
                "141a53b6-af6f-4092-ba1f-c289659310f2",
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0"
            ],
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "EP034414780018"
            }
        }
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "37b086a7-c442-45e1-a832-2e2e61ba85f2",
    "timestamp": "2020-03-21T22:04:03.912354Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/competitions": [
        {
            "id": "e5998e42-9ec7-4fc7-97ba-eb8d5ad22cbb",
            "resourceType": "epg/competitions",
            "publishStart": "2020-03-19T17:37:09.772Z",
            "publishEnd": "2020-03-22T08:00:00Z",
            "published": true,
            "created": "2020-03-11T18:07:17.244Z",
            "updated": "2020-03-21T22:04:03.905Z",
            "contentLock": false,
            "startTime": "2020-03-19T08:00:00Z",
            "endTime": "2020-03-19T11:30:00Z",
            "duration": 3600,
            "name": "Automovilismo NASCAR Cup Series",
            "shortName": "Automovilismo NASCAR Cup Series",
            "description": "Se disputa una nueva jornada de la NASCAR Cup Series. Desde el Atlanta Motor Speedway, en Hampton, Georgia.",
            "shortDescription": "Desde el Atlanta Motor Speedway, en Hampton, Georgia, Estados Unidos.",
            "language": "es",
            "pictureID": "aea6b061-d6d8-4c56-8f81-d4c65960de3f.jpg",
            "pictures": {
                "16x9": "aea6b061-d6d8-4c56-8f81-d4c65960de3f.jpg",
                "1x1": "193f49f1-bebd-4d45-bac2d-a3ef03769885.jpg",
                "2x3": "f0ad4369-aab1-403d-8c56-1083a21cca2f.jpg",
                "3x4": "a9cc793b-2687-480f-9eaf-1b3643c3b6d1.jpg",
                "4x3": "9eb7eada-b6b6-4432-8b16-ad0c63bdbe66.jpg"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "3243a410-4c30-4345-9735-836e3eeae2f3",
            "genreIDs": [
                "d0719647-b34c-439b-b902-aadb168008ab"
            ],
            "genres": [
                {
                    "id": "d0719647-b34c-439b-b902-aadb168008ab",
                    "name": "Carrera de automóviles"
                }
            ],
            "assetIDs": [
                "2d96cd46c4349079dbf9e6a6f0f723d5"
            ],
            "regionIDs": [
                "141a53b6-af6f-4092-ba1f-c289659310f2",
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0"
            ],
            "blackoutRegionIDs": null,
            "blackout": false,
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "EP034414780018"
            },
            "sportID": "",
            "sportName": "",
            "leagueID": "",
            "leagueName": "",
            "tournamentID": "",
            "tournamentName": "",
            "gameID": "",
            "primaryPersonID": "",
            "primaryPersonName": "",
            "primaryPersonPictureID": "",
            "secondaryPersonID": "",
            "secondaryPersonName": "",
            "secondaryPersonPictureID": ""
        }
    ]
}
```



## v2/epg/episodes



### 1. Create EPG episode


Creates a scheduled EPG episode entry.

<br/>

##### Response object
| Field  | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.   
| timestamp |    | string | Generated log timestamp for this request.  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| *`epg/episodes`* |   |   |      |  |
| id | epg/episodes  |string | Unique ID for each asset.  |  |
| resourceType | epg/episodes | enum string | *epg/episodes*   | |
| startTime | epg/episodes | string | A timestamp.  |  |
| endTime | epg/episodes | string | A timestamp.  |  |
| name | epg/episodes | string | Full name.  |  |
| shortName | epg/episodes | string |   |  |
| description | epg/episodes  | string | Full description.  |  |
| shortDescription | epg/episodes | string |   |  |
| genreIDs | epg/episodes  | string array | | |
| language | epg/episodes  | string | Two-letter code for the spoken language.  |  |
| ratings  | epg/episodes  | string | Content ratings by boards and associations.  | 
| ratingAdvisories | epg/episodes  | string array | A list of content advisories such as "Adult Situations", "Language", or "Violence". |
| duration | epg/episodes  | number |Duration in minutes. |  |
| stationIDs | epg/episodes  | string | |  |
| assetIDs | epg/episodes  | string | | 
| pictureID | epg/episodes  | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/episodes|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. | 
| 3x4  | pictures | string | ID for a 3x4 image.  |
| 4x3  | pictures | string | ID for a 4x3 image.  |
| 16x9 | pictures | string | ID for a 16x9 image.  |
| publishStart |  | string | (optional) First date that this content is visible to end users.  ISO 8601 format |
| publishEnd |  | string | (optional) Last date that this content is visible to end users.  ISO 8601 format |

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/episodes/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "id": "0316a2e2a45eac0af9bec8c157378d0a",
    "resourceType": "epg/episodes",
    "startTime": "2018-05-23T23:00:00Z",
    "endTime": "2018-05-24T00:00:00Z",
    "duration": 60,
    "name": "The Voice",
    "shortName": "The Voice",
    "description": "Each of the final four artists performs a solo cover, a duet with the coach and his or her first original song.",
    "shortDescription": "Each of the final four artists performs.",
    "language": "en",
    "pictureID": "fe83e1fc7a9d665b432536a3a5a4d850",
    "pictures": {
        "2x3": "c59cfd8cb8d8227cfe3279d996645b5f",
        "3x4": "ddadc6ec1be3cfd73a1160d5b101f850",
        "4x3": "f2db4a36e5e857c23bc67d046396d3cd",
        "16x9": "fe83e1fc7a9d665b432536a3a5a4d850"
    },
    "ratings": [
        "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
        "Canadian Parental Rating//PG",
        "USA Parental Rating//TVPG"
    ],
    "ratingAdvisories": [],
    "stationID": "079fd2ea771cb01fd7d23feb4164ea19",
    "genreIDs": [
        "54d83ad2f132c6ab294e66fdcfa28132",
        "9382383b772f91159b444f8a451006a9"
    ],
    "assetIDs": [
        "170cdfba4efef2cc2d179cf7bbedae1a"
    ],
    "season": 14,
    "episode": 27,
    "showName": "The Voice",
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



***Responses:***


Status: Create EPG episode | Code: 200



### 2. Update EPG episode


Updates the specified EPG episode entry.

<br>


##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|ID	|string		|required	|ID for the targeted EPG episode. |

<br/>

##### Response object
| Field  | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    | 
| timestamp |    | string | Generated log timestamp for this request.  |
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| *`epg/episodes`* |   |   |      |  |
| id | epg/episodes  |string | Unique ID for each asset.  |  |
| resourceType | epg/episodes | enum string | *epg/episodes*   | |
| startTime | epg/episodes | string | A timestamp.  |  |
| endTime | epg/episodes | string | A timestamp.  |  |
| name | epg/episodes | string | Full name.  |  |
| shortName | epg/episodes | string |   |  |
| description | epg/episodes  | string | Full description.  |  |
| shortDescription | epg/episodes | string |   |  |
| genreIDs | epg/episodes  | string list | | |
| language | epg/episodes  | string | Two-letter code for the spoken language.  |  |
| ratings  | epg/episodes  | string | Content ratings by boards and associations.  |
| ratingAdvisories | epg/episodes  | string list | A list of content advisories such as "Adult Situations", "Language", or "Violence". |
| duration | epg/episodes  | number |Duration in minutes. |  |
| stationIDs | epg/episodes  | string | |  |
| assetIDs | epg/episodes  | string | | 
| pictureID | epg/episodes  | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/episodes|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image.
| 3x4  | pictures | string | ID for a 3x4 image.
| 4x3  | pictures | string | ID for a 4x3 image.  
| 16x9 | pictures | string | ID for a 16x9 image. 
| publishStart |  | string | (optional) First date that this content is visible to end users. ISO 8601 format |
| publishEnd |  | string | (optional) Last date that this content is visible to end users. ISO 8601 format |

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/episodes/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "id": "170cdfba4efef2cc2d179cf7bbedae1a",
    "resourceType": "epg/episodes",
    "startTime": "2018-07-24T11:00:00Z",
    "endTime": "2018-07-24T12:00:00Z",
    "duration": 60,
    "name": "Amistoso Internacional: Boca vs. Independiente Medellín",
    "shortName": "Amistoso Internacional: Boca vs. Independiente Medellín",
    "description": "Resumen del partido amistoso entre Boca e Independiente Medellín, disputado en Boca Ratón.",
    "shortDescription": "Amistoso internacional. En Boca Ratón.",
    "language": "en",
    "pictureID": "fdfa7d956de7ea05c7ff69d57d6f8066",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [],
    "ratingAdvisories": [],
    "stationID": "766fcb5442f0148418cd6993632f7e00",
    "genreIDs": [
        "14d85b52e8e7fdb14250b28666d50db2"
    ],
    "assetIDs": [],
    "season": 1,
    "episode": 0,
    "showName": "Review",
	"publishStart": "2019-01-01T15:00:00Z",
	"publishEnd": "2020-09-01T07:00:00Z"
}
```



***Responses:***


Status: Retrieve scheduled show episode from the EPG | Code: 200



```js
{
    "requestID": "0598bc28-013e-4f3a-aa3d-78efb5ac0213",
    "timestamp": "2018-05-15T04:21:20.409361277Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/episodes": [
        {
            "id": "e47069c464fa3f6c576615f5d600758f",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T00:12:00Z",
            "endTime": "2018-04-26T01:06:00Z",
            "duration": 0,
            "name": "Latinoamérica Salvaje",
            "shortName": "Latino",
            "description": "Con una extensión de 800,000 km2, la Patagonia es el extremo más austral de América del Sur.",
            "shortDescription": "La Patagonia el extremo más austral.",
            "language": "es",
            "pictureID": "",
            "pictures": {
                "2x3": null,
                "3x4": null,
                "4x3": null,
                "16x9": null
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        }
    ]
}
```



### 3. Retrieve scheduled show episode from the EPG


Retrieves the specified scheduled show from the EPG.

<!-- The original endpoint was "{{OCMServer}}/ocm/v2/epg/episodes/fe11bed15ccb91e66b981c6faf404a44?language=*" -->

<br>

<!--

#### Response object

The Notes column describes default and possible values, valid ranges, and fields that are *nullable* (&oslash;), or *required* (*&#640;*). All fields are optional unless otherwise indicated.

<br/>

| Name  | Parent |  Type  | Description | Notes 
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    | *&#640;*  | 
| timestamp |    | string | Generated log timestamp for this request.  | *&#640;* |  
| *`metadata`* |   |        |   |  
| count | metadata |number  | Current screen.  |*&#640;* , min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  |*&#640;*, min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. |*&#640;*, min=1, max = 20
||||||
| *`epg/episodes`* |   |   |      |  |
| id | epg/episodes  |string | Unique ID for each asset.  |  |
| resourceType | epg/episodes | enum string | *epg/episodes*   | |
| startTime | epg/episodes | string | A timestamp.  |  |
| endTime | epg/episodes | string | A timestamp.  |  |
| name | epg/episodes | string | Full name.  |  |
| shortName | epg/episodes | string |   |  |
| description | epg/episodes  | string | Full description.  |  |
| shortDescription | epg/episodes | string |   |  |
| genreIDs | epg/episodes  | string list | | |
| language | epg/episodes  | string | Two-letter code for the spoken language.  |  |
| ratings  | epg/episodes  | string | Content ratings by boards and associations.  | &oslash; |
| ratingAdvisories | epg/episodes  | string list | A list of content advisories.  | Such as "Adult Situations", "Language", or "Violence" |
| duration | epg/episodes  | number |   |  |
| stationIDs | epg/episodes  | string | |  |
| assetIDs | epg/episodes  | string | | &oslash;; |
| pictureID | epg/episodes  | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/episodes|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. | &oslash;;  | 
| 3x4  | pictures | string | ID for a 3x4 image.  | &oslash;; | 
| 4x3  | pictures | string | ID for a 4x3 image.  | &oslash;; | 
| 16x9 | pictures | string | ID for a 16x9 image.  | &oslash;; |

<br/>

-->

##### Error Responses
|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested show episode|
|404		|1040				|*Not Found*: No matching show episode ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/episodes/fe11bed15ccb91e66b981c6faf404a44
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



### 4. Retrieve scheduled show episode from the EPG with assets


Retrieves the specified scheduled show (assets included) from the EPG.

<br/>

<!-- Original URL: {{OCMServer}}/ocm/v2/epg/episodes/e47069c464fa3f6c576615f5d600758f?language=*&include=assets

##### Response object

The Notes column describes default and possible values, valid ranges, and fields that are *nullable* (&oslash;), or *required* (*&#640;*). All fields are optional unless otherwise indicated.

<br/>

| Name  | Parent |  Type  | Description | Notes 
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    | *&#640;*  | 
| timestamp |    | string | Generated log timestamp for this request.  | *&#640;* |  
| *`metadata`* |   |        |   |  
| count | metadata |number  | Current screen.  |*&#640;* , min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  |*&#640;*, min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. |*&#640;*, min=1, max = 20
||||||
| *`epg/episodes`* |   |   |      |  |
| id | epg/episodes  |string | Unique ID for each asset.  |  |
| resourceType | epg/episodes | enum string | *epg/episodes*   | |
| startTime | epg/episodes | string | A timestamp.  |  |
| endTime | epg/episodes | string | A timestamp.  |  |
| name | epg/episodes | string | Full name.  |  |
| shortName | epg/episodes | string |   |  |
| description | epg/episodes  | string | Full description.  |  |
| shortDescription | epg/episodes | string |   |  |
| genreIDs | epg/episodes  | string list | | |
| language | epg/episodes  | string | Two-letter code for the spoken language.  |  |
| ratings  | epg/episodes  | string | Content ratings by boards and associations.  | &oslash; |
| ratingAdvisories | epg/episodes  | string list | A list of content advisories.  | Such as "Adult Situations", "Language", or "Violence" |
| duration | epg/episodes  | number |   |  |
| stationIDs | epg/episodes  | string | |  |
| assetIDs | epg/episodes  | string | | &oslash;; |
| pictureID | epg/episodes  | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/episodes|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. | &oslash;;  | 
| 3x4  | pictures | string | ID for a 3x4 image.  | &oslash;; | 
| 4x3  | pictures | string | ID for a 4x3 image.  | &oslash;; | 
| 16x9 | pictures | string | ID for a 16x9 image.  | &oslash;; |

<br/>

-->

##### Error Responses

|HTTP Code	|Error Code			|Description|
|:---		|:---				|:---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested show episode|
|404		|1040				|*Not Found*: No matching show episode ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/episodes/{{showID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | assets | Includes descriptive metadata. |



***Responses:***


Status: Retrieve scheduled show episode from the EPG | Code: 200



```js
{
    "requestID": "0598bc28-013e-4f3a-aa3d-78efb5ac0213",
    "timestamp": "2018-05-15T04:21:20.409361277Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/episodes": [
        {
            "id": "e47069c464fa3f6c576615f5d600758f",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T00:12:00Z",
            "endTime": "2018-04-26T01:06:00Z",
            "duration": 0,
            "name": "Latinoamérica Salvaje",
            "shortName": "Latino",
            "description": "Con una extensión de 800,000 km2, la Patagonia es el extremo más austral de América del Sur.",
            "shortDescription": "La Patagonia el extremo más austral.",
            "language": "es",
            "pictureID": "",
            "pictures": {
                "2x3": null,
                "3x4": null,
                "4x3": null,
                "16x9": null
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        }
    ]
}
```



### 5. Delete EPG episode


Deletes the specified EPG episode. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|ID	|string		|required	|ID for the targeted EPG episode. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified EPG episode.|
|404		|1040	|*Not Found*: No matching EPG episode ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/episodes/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request.   |
| Content-Type | application/json | ETag header for cache validation. |



### 6. Patch EPG episode


Patches the specified EPG episode resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|id	|string		|required	|ID of the EPG episode to be updated. |

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this resource. | 
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| blackoutRegionIDs | | string list, allows null | |
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| episode | | number | The episode number. |
| season | | number | The season number. |
| showID | | string | The show this episode belongs to. |
| seasonID |  | string | The season this episode belongs to. |
| showName |  | string | The name of the episode show. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/episodes/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "publishStart": "2020-03-18T18:27:00.744Z",
    "publishEnd": "2020-04-04T15:00:00Z",
    "startTime": "2020-04-01T15:00:00Z",
    "endTime": "2020-04-01T15:50:00Z",
    "duration": 3000,
    "name": "Aliens",
    "shortName": "James Cameron's Story of Science Fiction",
    "shortDescription": "La ciencia ficción se pregunta si la Tierra tiene o no la única vida inteligente en el universo.",
    "language": "es",
    "pictureID": "6be87e15-3f43-4d09-bef7-b24d3e306925.jpg",
    "ratings": [
        "USA Parental Rating//TV14",
        "Canadian Parental Rating//14+",
        "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12"
    ],
    "ratingAdvisories": null,
    "metadata": {
        "source": "com.gracenote.on-v3",
        "id": "EP029007380001"
    },
    "episode": 1,
    "season": 1
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "a0b2a231-5319-4b96-b49b-c11d932b3bb4",
    "timestamp": "2020-03-23T17:16:47.387983Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/episodes": [
        {
            "id": "c3a8f2f5-26cf-43c7-a68a-667d55b01332",
            "resourceType": "epg/episodes",
            "publishStart": "2020-03-18T18:27:00.744Z",
            "publishEnd": "2020-04-04T15:00:00Z",
            "published": true,
            "created": "2020-03-18T00:14:49.73Z",
            "updated": "2020-03-23T17:16:47.384Z",
            "contentLock": false,
            "startTime": "2020-04-01T15:00:00Z",
            "endTime": "2020-04-01T15:50:00Z",
            "duration": 3000,
            "name": "Aliens",
            "shortName": "James Cameron's Story of Science Fiction",
            "description": "Desde sus primeros días, la ciencia ficción se ha preguntado si la Tierra tiene o no la única vida inteligente en el universo; lo que uno puede aprender de los extraterrestres.",
            "shortDescription": "La ciencia ficción se pregunta si la Tierra tiene o no la única vida inteligente en el universo.",
            "language": "es",
            "pictureID": "6be87e15-3f43-4d09-bef7-b24d3e306925.jpg",
            "pictures": {
                "16x9": "6be87e15-3f43-4d09-bef7-b24d3e306925.jpg",
                "1x1": "de2568be-4d24-408e-a50a-048edd73f13d.jpg",
                "2x3": "0c7a82bc-c8d1-426c-b66f-976180a47a43.jpg",
                "3x4": "7ba4b6d5-3f49-42ae-a721-b402ef7162ac.jpg",
                "4x3": "cb1e9e6f-16ad-4c93-b463-e25af206cbad.jpg"
            },
            "ratings": [
                "USA Parental Rating//TV14",
                "Canadian Parental Rating//14+",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12"
            ],
            "ratingAdvisories": null,
            "stationID": "fac8403d2010f57f05837fc7928abd88",
            "genreIDs": [
                "288aa696-1f57-47e2-b841-b3ab5d94070a",
                "e523d2e8-8fbc-49f0-913e-d526c6d2e08a"
            ],
            "genres": [
                {
                    "id": "288aa696-1f57-47e2-b841-b3ab5d94070a",
                    "name": "Ciencia Ficción"
                },
                {
                    "id": "e523d2e8-8fbc-49f0-913e-d526c6d2e08a",
                    "name": "Documental"
                }
            ],
            "assetIDs": [
                "d50818bd651b4d1f6da517b384ed189d"
            ],
            "regionIDs": [
                "2e167237-c7bb-423b-b606-c31115adb1da",
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
                "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "141a53b6-af6f-4092-ba1f-c289659310f2"
            ],
            "blackoutRegionIDs": null,
            "blackout": false,
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "EP029007380001"
            },
            "episode": 1,
            "season": 1,
            "showID": "68ee469e5c7dd812227ec15f61c81e6c",
            "seasonID": "6ca05012-27f8-4d63-b1e8-da3bbc304e43",
            "showName": "James Cameron's Story of Science Fiction"
        }
    ]
}
```



## v2/epg/events



### 1. Create EPG event


Creates a scheduled EPG event entry.

<br/>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Name  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| resourceType |    | enum string | Required. Contains the value "epg/events". | 
| startTime |   	| string | Required. A timestamp in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. A timestamp in ISO-8601 timestamp format.  |  
| duration |    	| number | Required. Video duration in minutes.  |  
| name |    		| string | Required. Full name.  |
| shortName |   	| string | Shortened name.   |
| description |     | string | Full description. |
| shortDescription| | string | Shortened description. |
| language |    	| string | Required. Two-letter code for the spoken language.  |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this event. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  
| ratings |     	| string list | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this event. | 
| genreIDs |    	| string list | List of genre IDs associated with this event. | 
| genres |    		| string list | List of genres associated with this event. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this EPG event. |
| regionIDs |    	| string list | List of region IDs associated with this event. | 
| publishStart |	| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 
| publishEnd|		| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/events
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "epg/events",
    "startTime": "2018-04-26T00:30:00Z",
    "endTime": "2018-04-26T01:00:00Z",
    "duration": 10,
    "name": "Más Que Noticias",
    "shortName": "Más Que",
    "description": "Noticiero de Costa Rica que cada día indaga mediante reportajes a personalidades y empresas únicas, con historias extraordinarias e inolvidables.",
    "shortDescription": "asdf",
    "language": "es",
    "pictureID": "asdf",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [],
    "ratingAdvisories": [],
    "stationID": "60bb265bfd2de7e24a3b32da8fb38b97",
    "genreIDs": [
        "7af3784f6a86d74a1d5e29bb2e7887c3"
    ],
    "genres": [
        {
            "id": "7af3784f6a86d74a1d5e29bb2e7887c3",
            "name": "Noticias"
        }
    ],
    "assetIDs": [],
    "regionIDs": null,
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



### 2. Update scheduled event


Updates the EPG entry for the specified scheduled event.

<br>

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID for the scheduled event to be updated. | 

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/events/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "resourceType": "epg/events",
    "startTime": "2018-04-26T00:30:00Z",
    "endTime": "2018-04-26T01:00:00Z",
    "duration": 10,
    "name": "Más Que Noticias",
    "shortName": "Más Que",
    "description": "Noticiero de Costa Rica que cada día indaga mediante reportajes a personalidades y empresas únicas, con historias extraordinarias e inolvidables.",
    "shortDescription": "asdf",
    "language": "es",
    "pictureID": "asdf",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [],
    "ratingAdvisories": [],
    "stationID": "60bb265bfd2de7e24a3b32da8fb38b97",
    "genreIDs": [
        "7af3784f6a86d74a1d5e29bb2e7887c3"
    ],
    "genres": [
        {
            "id": "7af3784f6a86d74a1d5e29bb2e7887c3",
            "name": "Noticias"
        }
    ],
    "assetIDs": [],
    "regionIDs": null,
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



***Responses:***


Status: Retrieve scheduled event from the EPG | Code: 200



```js
{
    "requestID": "64d24e22-dd41-43ff-927a-a77877618e7c",
    "timestamp": "2018-05-15T04:19:41.681333576Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/events": [
        {
            "id": "2210abb74120596b216deb44d369bdee",
            "resourceType": "epg/events",
            "startTime": "2018-04-10T00:51:00Z",
            "endTime": "2018-04-10T01:03:00Z",
            "duration": 0,
            "name": "",
            "shortName": "",
            "description": "",
            "shortDescription": "",
            "language": "",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        }
    ]
}
```



### 3. Retrieve scheduled event from the EPG


Retrieves the specified scheduled event from the EPG.

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested scheduled event|
|404		|1040				|*Not Found*: No matching scheduled event ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/events/2210abb74120596b216deb44d369bdee
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Retrieve scheduled event from the EPG | Code: 200



```js
{
    "requestID": "64d24e22-dd41-43ff-927a-a77877618e7c",
    "timestamp": "2018-05-15T04:19:41.681333576Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/events": [
        {
            "id": "2210abb74120596b216deb44d369bdee",
            "resourceType": "epg/events",
            "startTime": "2018-04-10T00:51:00Z",
            "endTime": "2018-04-10T01:03:00Z",
            "duration": 0,
            "name": "",
            "shortName": "",
            "description": "",
            "shortDescription": "",
            "language": "",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        }
    ]
}
```



### 4. Retrieve scheduled event from the EPG with assets


Retrieves the specified scheduled event (assets included) from the EPG.

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested scheduled event|
|404		|1040				|*Not Found*: No matching scheduled event ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/events/6be0e5ba672c2b87001d6369d26ee6eb
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | assets | Includes descriptive metadata. |



***Responses:***


Status: Retrieve scheduled event from the EPG | Code: 200



```js
{
    "requestID": "64d24e22-dd41-43ff-927a-a77877618e7c",
    "timestamp": "2018-05-15T04:19:41.681333576Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/events": [
        {
            "id": "2210abb74120596b216deb44d369bdee",
            "resourceType": "epg/events",
            "startTime": "2018-04-10T00:51:00Z",
            "endTime": "2018-04-10T01:03:00Z",
            "duration": 0,
            "name": "",
            "shortName": "",
            "description": "",
            "shortDescription": "",
            "language": "",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null,
            "publishStart": "2019-01-01T15:00:00Z",
            "publishEnd": "2020-09-01T07:00:00Z"
        }
    ]
}
```



### 5. Delete EPG event


Deletes the specified EPG event entry. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|ID	|string		|required	|ID for the targeted EPG event. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified EPG event.|
|404		|1040	|*Not Found*: No matching EPG event ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/events/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request.   |
| Content-Type | application/json | ETag header for cache validation.  |



### 6. Patch EPG event


Patches the specified EPG event resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID of the EPG event to be updated. | 

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this resource. | 
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| blackoutRegionIDs | | string list, allows null | |
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/events/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "duration": 1800,
    "name": "24 Horas Deportes",
    "shortName": "24 Horas Deportes",
    "pictures": {
        "16x9": "b4393083-32b0-45ae-8fc8-b0d1405041b8.jpg",
        "1x1": "9bee3ab5-f43d-4dde-aa0f-e2c20be13606.jpg",
        "2x3": "f20e048b-0c29-4fa9-972c-d027f3b57b65.jpg",
        "3x4": "9d7bd96f-3e74-4a77-8407-57ebbbb1dcc4.jpg",
        "4x3": "c48e98c9-69d9-44c7-9092-6caad55969c9.jpg"
    },
    "ratings": null,
    "ratingAdvisories": null,
    "metadata": {
        "source": "com.gracenote.on-v3",
        "id": "SH011586030000"
    }
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "a1ce6162-9c4f-448b-845b-714ed4d30075",
    "timestamp": "2020-03-23T20:02:08.593411Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/events": [
        {
            "id": "1204fb1b-9e37-4e75-aacf-3a9c24921e1b",
            "resourceType": "epg/events",
            "publishStart": "2020-03-21T00:03:07.264Z",
            "publishEnd": "2020-03-31T23:00:00Z",
            "published": true,
            "created": "2020-03-14T00:14:43.028Z",
            "updated": "2020-03-23T20:02:08.589Z",
            "contentLock": false,
            "startTime": "2020-03-28T23:00:00Z",
            "endTime": "2020-03-28T23:30:00Z",
            "duration": 1800,
            "name": "24 Horas Deportes",
            "shortName": "24 Horas Deportes",
            "description": "Información deportiva.",
            "shortDescription": "Información deportiva.",
            "language": "es",
            "pictureID": "b4393083-32b0-45ae-8fc8-b0d1405041b8.jpg",
            "pictures": {
                "16x9": "b4393083-32b0-45ae-8fc8-b0d1405041b8.jpg",
                "1x1": "9bee3ab5-f43d-4dde-aa0f-e2c20be13606.jpg",
                "2x3": "f20e048b-0c29-4fa9-972c-d027f3b57b65.jpg",
                "3x4": "9d7bd96f-3e74-4a77-8407-57ebbbb1dcc4.jpg",
                "4x3": "c48e98c9-69d9-44c7-9092-6caad55969c9.jpg"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "977874c62505f06a2d2e7e55195721bf",
            "genreIDs": [
                "98436b0c-aebc-4b51-927c-06d4681507e9"
            ],
            "genres": [
                {
                    "id": "98436b0c-aebc-4b51-927c-06d4681507e9",
                    "name": "Deportes de acción"
                }
            ],
            "assetIDs": [
                "0067a3a90ac1fcdf8741f881f003d65c"
            ],
            "regionIDs": [
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5"
            ],
            "blackoutRegionIDs": null,
            "blackout": false,
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "SH011586030000"
            }
        }
    ]
}
```



## v2/epg/movies



### 1. Create EPG movie


Creates a movie entry in the electronic program guide (EPG) for a station.

<br/>

##### Path parameters
|Label|Data type|Required|Description|
|---|---|---|---|
|`movieID`|string|Yes|Asset identifier|

<br/>

##### Body Parameters
| Field | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| id |  |string | Unique ID for each asset.  |  |
| resourceType | | enum string |Required. Contains the value *epg/movies*   | |
| startTime | | string | Required. A timestamp in ISO-8601 timestamp format.  |  |
| endTime | | string | Required. A timestamp in ISO-8601 timestamp format.  |  |
| duration |  | number | Duration in minutes. |  |
| name | | string | Full name.  |  |
| shortName | | string | Shortened name.  |  |
| description |  | string | Full description.  |  |
| shortDescription | | string | Shortened description. |  |
| language |  | string | Two-letter code for the spoken language.  |  |
| pictureID |  | string | ID for the standard image. |  | 
||||||
| `pictures` |  |	| Images in various sizes for this EPG movie. |
| 2x3  | `pictures` | string | ID for a 2x3 image. | 
| 3x4  | `pictures` | string | ID for a 3x4 image.  | 
| 4x3  | `pictures` | string | ID for a 4x3 image.  | 
| 16x9 | `pictures` | string | ID for a 16x9 image.  | 
| ratings  |  | string | Content ratings by boards and associations.  | 
| ratingAdvisories |  | string list | A list of content advisories such as "Adult Situations", "Language", or "Violence". |
| stationID |  | string | ID for the station associated with this EPG movie. |
| genreIDs |  | string list | List of genre IDs associated with this EPG movie. | 
| assetIDs |  | string | Comma-separated list of asset IDs to associate with this EPG movie. | 
| releaseYear |  | number | 0 |
| publishStart |	| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 
| publishEnd|		| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 

<br/>

##### Response object
| Field | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    | 
| timestamp |    | string | Generated log timestamp for this request.  | 
||||||
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| *`epg/movies`* |  |  |  |  |  
| id | epg/movies  |string | Unique ID for each asset.  |  |
| resourceType | epg/movies | enum string | *epg/movies*   | |
| startTime | epg/movies | string | A timestamp.  |  |
| endTime | epg/movies | string | A timestamp.  |  |
| name | epg/movies | string | Full name.  |  |
| shortName | epg/movies | string |   |  |
| description | epg/movies  | string | Full description.  |  |
| shortDescription | epg/movies | string |   |  |
| genreIDs | epg/movies  | string list | | 
| language | epg/movies  | string | Two-letter code for the spoken language.  |  |
| ratings  | epg/movies  | string | Content ratings by boards and associations.  | 
| ratingAdvisories | epg/movies  | string list | A list of content advisories such as "Adult Situations", "Language", or "Violence". |
| duration | epg/movies  | number | Duration in minutes. |  |
| stationID | epg/movies  | string | |  |
| assetIDs | epg/movies  | string | | 
| releaseYear | epg/movies  | number | | 0 |
| publishStart |	| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 
| publishEnd|		| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 
| pictureID | epg/movies  | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/movies|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. | 
| 3x4  | pictures | string | ID for a 3x4 image.  | 
| 4x3  | pictures | string | ID for a 4x3 image.  | 
| 16x9 | pictures | string | ID for a 16x9 image.  | 

<br/>

##### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**400**|1103, 1104, 1105|*Bad request*: Request body malformed.|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**403**|1004|*Forbidden*: Cannot write the requested resource.|

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/movies/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use * as a wildcard for all languages. Default value is en for English. |



***Body:***

```js        
{
    "id": "34fe26d8bd1640066960317d89f81acf",
    "resourceType": "epg/movies",
    "startTime": "2018-05-23T05:00:00Z",
    "endTime": "2018-05-23T07:00:00Z",
    "duration": 120,
    "name": "Terminator Salvation: Director's Cut",
    "shortName": "Terminator",
    "description": "Although Judgment Day has in fact occurred, the future for which John Connor (Christian Bale) was prepared has been partly altered by the appearance of a stranger named Marcus Wright (Sam Worthington). Connor must determine if Wright has been rescued from the past, or sent from the future. As the machines prepare for a final battle, Connor and Wright delve deep into Skynet's heart, uncovering a secret that could lead to the annihilation of mankind.",
    "shortDescription": "Humanity fights back against Skynet's machine army.",
    "language": "en",
    "pictureID": "8e2322afa31e7932b5984bb46956ce0f",
    "pictures": {
        "2x3": "db0503b26ab7c1751628bb4b6e5fda73",
        "3x4": "4c07410aefdc41ab3890daab1b3ad671",
        "4x3": "b7513695aa88a2d412507ff717fdff19",
        "16x9": "8e2322afa31e7932b5984bb46956ce0f"
    },
    "ratings": [
        "Motion Picture Association of America/Restricted/R",
        "Departamento de Justiça, Classificação, Títulos e Qualificação/14 anos/14",
        "Australian Classification Board/Mature/M",
        "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 16 years/K16",
        "Régie du cinéma/13 Years and Over/13+",
        "Ley de Medios Audiovisuales//SAM 13"
    ],
    "ratingAdvisories": [
        "Adult Situations",
        "Brief Nudity",
        "Violence"
    ],
    "stationID": "079fd2ea771cb01fd7d23feb4164ea19",
    "genreIDs": [
        "f039f36f93ad99fa89851e8c4af99e13",
        "dd1f75e99999b923c6275ad202034d83"
    ],
    "assetIDs": [
        "841f3bb71aeb3da5851a88176ef0f313"
    ],
    "releaseYear": 0,
	"publishStart": "2019-01-01T15:00:00Z",
	"publishEnd": "2020-09-01T07:00:00Z"
}
```



***Responses:***


Status: Retrieve scheduled movie from the EPG | Code: 200



```js
{
    "requestID": "e365d504-eb8c-43d9-9aa2-4e285113ef98",
    "timestamp": "2018-05-15T04:22:06.853977833Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/movies": [
        {
            "id": "062d9f9ea98cbcae33524ca9f1f6ea8e",
            "resourceType": "epg/movies",
            "startTime": "2018-04-26T00:25:00Z",
            "endTime": "2018-04-26T02:00:00Z",
            "duration": 0,
            "name": "Vivir mata",
            "shortName": "Vivir mata",
            "description": "En México DF., dos amantes luchan por su relación después de que descubren que los dos mintieron sobre sus identidades.",
            "shortDescription": "Unos amantes ambivalentes tratan de lucha por su relación.",
            "language": "es",
            "pictureID": "7469501ba293542959790b9a6b3849de",
            "pictures": {
                "2x3": "8260ecd06cdcd05f1bc24cf3a5255869",
                "3x4": "3f10c9dc71fe3380f5de67a5edccf209",
                "4x3": "8e61c12a2c6d4af41ce4a52bd7e215f5",
                "16x9": "7469501ba293542959790b9a6b3849de"
            },
            "ratings": null,
            "ratingAdvisories": [
                "Adult Situations"
            ],
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null,
            "releaseYear": 0
        }
    ]
}
```



### 2. Update EPG movie


Updates descriptive information associated with the specified EPG movie entry.

<!-- This should be a PUT, right? -->

<br/>

##### Path parameters

|Label|Data type|Required|Description|
|---|---|---|---|
|`movieID`|string|Yes|Asset identifier|

<br/>


##### Body Parameters
| Field  | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| id |  |string | Unique ID for each asset.  |  |
| resourceType | | enum string |Required. Contains the value "epg/movies".   | |
| startTime | | string | Required. A timestamp in ISO-8601 timestamp format.  |  |
| endTime | | string | Required. A timestamp in ISO-8601 timestamp format.  |  |
| duration |  | number | Duration in minutes. |  |
| name | | string | Full name.  |  |
| shortName | | string | Shortened name.  |  |
| description |  | string | Full description.  |  |
| shortDescription | | string | Shortened description. |  |
| language |  | string | Two-letter code for the spoken language.  |  |
| pictureID |  | string | ID for the standard image. |  | 
||||||
| `pictures` |  |	| Images in various sizes for this EPG movie. |
| 2x3  | `pictures` | string | ID for a 2x3 image. | 
| 3x4  | `pictures` | string | ID for a 3x4 image.  | 
| 4x3  | `pictures` | string | ID for a 4x3 image.  | 
| 16x9 | `pictures` | string | ID for a 16x9 image.  | 
| ratings  |  | string | Content ratings by boards and associations.  | 
| ratingAdvisories |  | string list | A list of content advisories such as "Adult Situations", "Language", or "Violence". |
| stationID |  | string | ID for the station associated with this EPG movie. |
| genreIDs |  | string list | List of genre IDs associated with this EPG movie. | 
| assetIDs |  | string | Comma-separated list of asset IDs to associate with this EPG movie. | 
| releaseYear |  | number | 0 |
| publishStart |	| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 
| publishEnd|		| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 

<br/>

##### Response object

| Field  | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    | 
| timestamp |    | string | Generated log timestamp for this request. 
||||||
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| `epg/movies` |  | object array |  |  
| id | `epg/movies`  |string | Unique ID for each asset.  | 
| resourceType | `epg/movies` | enum string | Contains the value "epg/movies". |
| startTime | `epg/movies` | string | A timestamp.  |
| endTime | `epg/movies` | string | A timestamp.  |
| name | `epg/movies` | string | Full name.  |
| shortName | `epg/movies` | string | Shortened name.  |
| description | `epg/movies`  | string | Full description.  |
| shortDescription | `epg/movies` | string | Shortened description. |
| genreIDs | `epg/movies`  | string list | List of genre IDs associated with this EPG movie.| 
| language | `epg/movies`  | string | Two-letter code for the spoken language.  | 
| ratings  | `epg/movies`  | string | Content ratings by boards and associations.  | 
| ratingAdvisories | `epg/movies`  | string list | A list of content advisories such as "Adult Situations", "Language", or "Violence". |
| duration | `epg/movies`  | number | Duration in minutes.  | 
| stationID | `epg/movies`  | string | ID for the station associated with this EPG movie. |
| assetIDs | `epg/movies`  | string |  Comma-separated list of asset IDs to associate with this EPG movie. | 
| releaseYear | `epg/movies`  | number |  0 |
| pictureID | `epg/movies`  | string | ID for the standard image | 
||||||
| `pictures` | `epg/movies`| object  | Images in various sizes for this EPG movie. |
| 2x3  | `pictures` | string | ID for a 2x3 image. |
| 3x4  | `pictures` | string | ID for a 3x4 image.  |
| 4x3  | `pictures` | string | ID for a 4x3 image.  |
| 16x9 | `pictures` | string | ID for a 16x9 image.  |
| publishStart | `epg/movies`  | string | First date that this content is visible to end users. ISO 8601 format |
| publishEnd | `epg/movies` | string | Last date that this content is visible to end users. ISO 8601 format |

<br/>

##### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**400**|1103, 1104, 1105|*Bad request*: Request body malformed.|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**403**|1004|*Forbidden*: Cannot update the requested resource.|
|**404**|1040|*Not found*: Requested resource ID missing, deleted, or incorrect.|

<!--	|**304**|	|*Not modified*: <No Content>|	-->

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/movies/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Body:***

```js        
{
    "id": "34fe26d8bd1640066960317d89f81acf",
    "resourceType": "epg/movies",
    "startTime": "2018-05-23T05:00:00Z",
    "endTime": "2018-05-23T07:00:00Z",
    "duration": 120,
    "name": "Terminator Salvation: Director's Cut",
    "shortName": "Terminator",
    "description": "Although Judgment Day has in fact occurred, the future for which John Connor (Christian Bale) was prepared has been partly altered by the appearance of a stranger named Marcus Wright (Sam Worthington). Connor must determine if Wright has been rescued from the past, or sent from the future. As the machines prepare for a final battle, Connor and Wright delve deep into Skynet's heart, uncovering a secret that could lead to the annihilation of mankind.",
    "shortDescription": "Humanity fights back against Skynet's machine army.",
    "language": "en",
    "pictureID": "8e2322afa31e7932b5984bb46956ce0f",
    "pictures": {
        "2x3": "db0503b26ab7c1751628bb4b6e5fda73",
        "3x4": "4c07410aefdc41ab3890daab1b3ad671",
        "4x3": "b7513695aa88a2d412507ff717fdff19",
        "16x9": "8e2322afa31e7932b5984bb46956ce0f"
    },
    "ratings": [
        "Motion Picture Association of America/Restricted/R",
        "Departamento de Justiça, Classificação, Títulos e Qualificação/14 anos/14",
        "Australian Classification Board/Mature/M",
        "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 16 years/K16",
        "Régie du cinéma/13 Years and Over/13+",
        "Ley de Medios Audiovisuales//SAM 13"
    ],
    "ratingAdvisories": [
        "Adult Situations",
        "Brief Nudity",
        "Violence"
    ],
    "stationID": "079fd2ea771cb01fd7d23feb4164ea19",
    "genreIDs": [
        "f039f36f93ad99fa89851e8c4af99e13",
        "dd1f75e99999b923c6275ad202034d83"
    ],
    "assetIDs": [
        "841f3bb71aeb3da5851a88176ef0f313"
    ],
    "releaseYear": 0,
	"publishStart": "2019-01-01T15:00:00Z",
	"publishEnd": "2020-09-01T07:00:00Z"
}
```



***Responses:***


Status: Retrieve scheduled movie from the EPG | Code: 200



```js
{
    "requestID": "e365d504-eb8c-43d9-9aa2-4e285113ef98",
    "timestamp": "2018-05-15T04:22:06.853977833Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/movies": [
        {
            "id": "062d9f9ea98cbcae33524ca9f1f6ea8e",
            "resourceType": "epg/movies",
            "startTime": "2018-04-26T00:25:00Z",
            "endTime": "2018-04-26T02:00:00Z",
            "duration": 0,
            "name": "Vivir mata",
            "shortName": "Vivir mata",
            "description": "En México DF., dos amantes luchan por su relación después de que descubren que los dos mintieron sobre sus identidades.",
            "shortDescription": "Unos amantes ambivalentes tratan de lucha por su relación.",
            "language": "es",
            "pictureID": "7469501ba293542959790b9a6b3849de",
            "pictures": {
                "2x3": "8260ecd06cdcd05f1bc24cf3a5255869",
                "3x4": "3f10c9dc71fe3380f5de67a5edccf209",
                "4x3": "8e61c12a2c6d4af41ce4a52bd7e215f5",
                "16x9": "7469501ba293542959790b9a6b3849de"
            },
            "ratings": null,
            "ratingAdvisories": [
                "Adult Situations"
            ],
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null,
            "releaseYear": 0
        }
    ]
}
```



### 3. Retrieve scheduled movie from the EPG


Returns the descriptive information associated with the specified EPG movie.

<br/>

##### Path Parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|movieID|string|Yes|Asset identifier|

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested scheduled movie|
|404		|1040				|*Not Found*: No matching scheduled movie ID found|

<!-- |**304**|*Not modified*|No Content| -->

<br/>

<!--

##### Response Object

The Notes column describes default and possible values, valid ranges, and fields that are *nullable* (&oslash;), or *required* (*&#640;*). All fields are optional unless otherwise indicated.

<br/>

| Name  | Parent |  Type  | Description | Notes 
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    | *&#640;*  | 
| timestamp |    | string | Generated log timestamp for this request.  | *&#640;* |  
||||||
| *`metadata`* |   |   |   |   |  
| count | *`metadata`* |number  | Current screen.  |*&#640;* , min=1, max = 100   
| totalCount| *`metadata`* |number | Total number of screens.  |*&#640;*, min=1, max = 20
| offset | *`metadata`* | number | Number of lines from the top of the screen. |*&#640;*, min=1, max = 20
||||||
| *`epg/movies`* |  |  |  |  |  
| id | *`epg/movies`*  |string | Unique ID for each asset.  |  |
| resourceType | *`epg/movies`* | enum string | *epg/movies*   | |
| startTime | *`epg/movies`* | string | A timestamp.  |  |
| endTime | *`epg/movies`* | string | A timestamp.  |  |
| name | *`epg/movies`* | string | Full name.  |  |
| shortName | *`epg/movies`* | string |   |  |
| description | *`epg/movies`*  | string | Full description.  |  |
| shortDescription | *`epg/movies`* | string |   |  |
| genreIDs | *`epg/movies`*  | string list | | &oslash;; |
| language | *`epg/movies`*  | string | Two-letter code for the spoken language.  |  |
| ratings  | *`epg/movies`*  | string | Content ratings by boards and associations.  | &oslash; |
| ratingAdvisories | *`epg/movies`*  | string list | A list of content advisories.  | Such as "Adult Situations", "Language", or "Violence" |
| duration | *`epg/movies`*  | number |   |  |
| stationID | *`epg/movies`*  | string | |  |
| assetIDs | *`epg/movies`*  | string | | &oslash;; |
| releaseYear | *`epg/movies`*  | number | | 0 |
| pictureID | *`epg/movies`*  | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/movies|  |   |  |
| 2x3  | *`pictures`* | string | ID for a 2x3 image. | &oslash;;  | 
| 3x4  | *`pictures`* | string | ID for a 3x4 image.  | &oslash;; | 
| 4x3  | *`pictures`* | string | ID for a 4x3 image.  | &oslash;; | 
| 16x9 | *`pictures`* | string | ID for a 16x9 image.  | &oslash;; |

<br/>


<!-- NOTES
	1.	Endpoint was saved as "{{OCMServer}}/ocm/v2/epg/movies/2875e9a55b634bffa16901ff34861967?language=*"
		@ecarter reset the endpoint as "GET /ocm/v2/epg/movies/{{movieID}}" which was in the documentation.

	3.	Need to set "request parameters" in the correct format
	
	4.	The *``metadata``* field should be renamed to `pagination`

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/movies/{{movieID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Retrieve scheduled movie from the EPG | Code: 200



```js
{
	"requestID":"e365d504-eb8c-43d9-9aa2-4e285113ef98",
	"timestamp":"2018-05-15T04:22:06.853977833Z",
	"metadata":{
		"count":1,
		"totalCount":1,
		"offset":0
	},
	"epg/movies":[
		{
			"id":"062d9f9ea98cbcae33524ca9f1f6ea8e",
			"resourceType":"epg/movies",
			"startTime":"2018-04-26T00:25:00Z",
			"endTime":"2018-04-26T02:00:00Z",
			"duration":0,
			"name":"Vivir mata",
			"shortName":"Vivir mata",
			"description":"En México DF., dos amantes luchan por su relación después de que descubren que los dos mintieron sobre sus identidades.",
			"shortDescription":"Unos amantes ambivalentes tratan de lucha por su relación.",
			"language":"es",
			"pictureID":"7469501ba293542959790b9a6b3849de",
			"pictures":{
				"2x3":"8260ecd06cdcd05f1bc24cf3a5255869",
				"3x4":"3f10c9dc71fe3380f5de67a5edccf209",
				"4x3":"8e61c12a2c6d4af41ce4a52bd7e215f5",
				"16x9":"7469501ba293542959790b9a6b3849de"
			},
			"ratings":null,
			"ratingAdvisories":[
				"Adult Situations"
			],
			"stationID":"",
			"genreIDs":null,
			"assetIDs":null,
			"releaseYear":0,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
		}
	]
}
```



### 4. Retrieve scheduled movie from the EPG with assets


Retrieves the specified scheduled movie (assets included) from the EPG.

<!-- The original endpoint was "{{OCMServer}}/ocm/v2/epg/movies/2875e9a55b634bffa16901ff34861967?language=*&include=assets" -->

<br/>

<!-- Returns metadata associated with the specified movie from the EPG. -->


##### Path Parameters
|Name|Data type|Required|Description|
|---|---|---|---|
|movieID|string|required|Asset identifier|


<br/>

##### Error Responses
|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested scheduled movie|
|404		|1040				|*Not Found*: No matching scheduled movie ID found|

<br/>

<!--

##### Response object

The Notes column describes default and possible values, valid ranges, and fields that are *nullable* (&oslash;), or *required* (*&#640;*). All fields are optional unless otherwise indicated.

<br/>

| Name  | Parent |  Type  | Description | Notes 
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    | *&#640;*  | 
| timestamp |    | string | Generated log timestamp for this request.  | *&#640;* |  
||||||
| *`metadata`* |   |   |   |   |  
| count | metadata |number  | Current screen.  |*&#640;* , min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  |*&#640;*, min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. |*&#640;*, min=1, max = 20
||||||
| *`epg/movies`* |  |  |  |  |  
| id | epg/movies  |string | Unique ID for each asset.  |  |
| resourceType | epg/movies | enum string | *epg/movies*   | |
| startTime | epg/movies | string | A timestamp.  |  |
| endTime | epg/movies | string | A timestamp.  |  |
| name | epg/movies | string | Full name.  |  |
| shortName | epg/movies | string |   |  |
| description | epg/movies  | string | Full description.  |  |
| shortDescription | epg/movies | string |   |  |
| genreIDs | epg/movies  | string list | | &oslash;; |
| language | epg/movies  | string | Two-letter code for the spoken language.  |  |
| ratings  | epg/movies  | string | Content ratings by boards and associations.  | &oslash; |
| ratingAdvisories | epg/movies  | string list | A list of content advisories.  | Such as "Adult Situations", "Language", or "Violence" |
| duration | epg/movies  | number |   |  |
| stationID | epg/movies  | string | |  |
| assetIDs | epg/movies  | string | | &oslash;; |
| releaseYear | epg/movies  | number | | 0 |
| pictureID | epg/movies  | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/movies|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. | &oslash;;  | 
| 3x4  | pictures | string | ID for a 3x4 image.  | &oslash;; | 
| 4x3  | pictures | string | ID for a 4x3 image.  | &oslash;; | 
| 16x9 | pictures | string | ID for a 16x9 image.  | &oslash;; |

<br/>

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/movies/{{movieID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | assets | Includes descriptive metadata. |



***Responses:***


Status: Retrieve scheduled movie from the EPG | Code: 200



```js
{
    "requestID": "e365d504-eb8c-43d9-9aa2-4e285113ef98",
    "timestamp": "2018-05-15T04:22:06.853977833Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/movies": [
        {
            "id": "062d9f9ea98cbcae33524ca9f1f6ea8e",
            "resourceType": "epg/movies",
            "startTime": "2018-04-26T00:25:00Z",
            "endTime": "2018-04-26T02:00:00Z",
            "duration": 0,
            "name": "Vivir mata",
            "shortName": "Vivir mata",
            "description": "En México DF., dos amantes luchan por su relación después de que descubren que los dos mintieron sobre sus identidades.",
            "shortDescription": "Unos amantes ambivalentes tratan de lucha por su relación.",
            "language": "es",
            "pictureID": "7469501ba293542959790b9a6b3849de",
            "pictures": {
                "2x3": "8260ecd06cdcd05f1bc24cf3a5255869",
                "3x4": "3f10c9dc71fe3380f5de67a5edccf209",
                "4x3": "8e61c12a2c6d4af41ce4a52bd7e215f5",
                "16x9": "7469501ba293542959790b9a6b3849de"
            },
            "ratings": null,
            "ratingAdvisories": [
                "Adult Situations"
            ],
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null,
            "releaseYear": 0,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        }
    ]
}
```



### 5. Delete EPG movie


Deletes the specified EPG movie entry. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|ID	|string		|required	|ID for the targeted EPG movie. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified EPG movie.|
|404		|1040	|*Not Found*: No matching EPG movie ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/movies/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request.   |
| Content-Type | application/json | ETag header for cache validation.  |



### 6. Patch EPG movie


Patches the specified EPG movie resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID of the EPG movie to be updated. | 

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this resource. | 
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| blackoutRegionIDs | | string list, allows null | |
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| releaseYear | | number, min=1 max=3000 | The movie relese year |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/movies/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "startTime": "2020-03-22T07:00:00Z",
    "endTime": "2020-03-22T08:35:00Z",
    "duration": 5700,
    "name": "Alien Convergence",
    "shortName": "Alien Convergence",
    "ratings": [
        "Departamento de Justiça, Classificação, Títulos e Qualificação/16 anos/16",
        "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 16 or older./16",
        "Film & Publication Board/Parental Guidance Recommended/PG",
        "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12"
    ],
    "genreIDs": [
        "0a4bc512-038a-4399-9fce-44076f049cf7"
    ],
    "assetIDs": [
        "18989793418bf9b63e8d7742114bd1b9"
    ],
    "regionIDs": [
        "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
        "2e167237-c7bb-423b-b606-c31115adb1da",
        "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
        "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
        "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
        "141a53b6-af6f-4092-ba1f-c289659310f2"
    ],
    "releaseYear": 2017
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "994a714b-3f1d-45be-a997-daa856f02d00",
    "timestamp": "2020-03-23T20:29:18.478861Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/movies": [
        {
            "id": "5dd0e68b-435f-46b9-bec0-9fbb695f4473",
            "resourceType": "epg/movies",
            "publishStart": "2020-03-21T02:49:49.048Z",
            "publishEnd": "2020-03-25T07:00:00Z",
            "published": true,
            "created": "2020-03-08T00:14:54.674Z",
            "updated": "2020-03-23T20:29:18.474Z",
            "contentLock": false,
            "startTime": "2020-03-22T07:00:00Z",
            "endTime": "2020-03-22T08:35:00Z",
            "duration": 5700,
            "name": "Alien Convergence",
            "shortName": "Alien Convergence",
            "description": "Un nuevo avión de combate es la última esperanza de la humanidad en su lucha contra unos alienígenas con forma de reptil que están destruyendo la Tierra.",
            "shortDescription": "Un nuevo avión de combate es la última esperanza de la humanidad en su lucha contra los alienígenas.",
            "language": "es",
            "pictureID": "c5118e03-8511-4626-8353-6133840db932.jpg",
            "pictures": {
                "16x9": "c5118e03-8511-4626-8353-6133840db932.jpg",
                "1x1": "f3c1a829-cdf2-4d86-bd30-28a3f01ef6d1.jpg",
                "2x3": "547e3508-bbff-4df4-837f-a7cf6022f9e5.jpg",
                "3x4": "1d0f1e5c-33d7-41d2-b05a-5409d759f435.jpg",
                "4x3": "65b9d769-1992-48a4-a96f-a4842a3eb4b2.jpg"
            },
            "ratings": [
                "Departamento de Justiça, Classificação, Títulos e Qualificação/16 anos/16",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 16 or older./16",
                "Film & Publication Board/Parental Guidance Recommended/PG",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12"
            ],
            "ratingAdvisories": null,
            "stationID": "af860590c9834b6cf67458285e9d877b",
            "genreIDs": [
                "0a4bc512-038a-4399-9fce-44076f049cf7"
            ],
            "genres": [
                {
                    "id": "0a4bc512-038a-4399-9fce-44076f049cf7",
                    "name": "Drama"
                }
            ],
            "assetIDs": [
                "18989793418bf9b63e8d7742114bd1b9"
            ],
            "regionIDs": [
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "2e167237-c7bb-423b-b606-c31115adb1da",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
                "141a53b6-af6f-4092-ba1f-c289659310f2"
            ],
            "blackoutRegionIDs": null,
            "blackout": false,
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "MV010154190000"
            },
            "releaseYear": 2017,
            "regions": null
        }
    ]
}
```



## v2/epg/stations



### 1. Create station


Creates an EPG schedule entry.

<br/>

<!-- 

The `stationID` is automatically created/assigned during creation.
I assume the `provider`, `providerID`, `genreIDs`, and `genres` are also automatically assigned/associated during creation.

What are the max char lengths for shortName, stationNumer, etc.
-->

##### Body Parameters
All fields are optional unless otherwise indicated.

| Name			| Parent	|  Type	| Description |
|--------------:|-----------|-------|-------------|
| resourceType	|| enum string	| Required. Contains the value "epg/competitions". | 
| name    		|| string | Required. Full station name. . . |
| shortName   	|| string | Shortened name or the station call sign. . . |
| stationNumber || number | Station or channel number as designated by the tenant service.   |
| language    	|| string | Required. Two-letter code for the spoken language.  |
| languageRegion|| string | Code for the regional language variety, such as: en-*GB*, en-*US*, es-*419*, etc.| 
| pictureID    	|| string | ID for the station logo or preview image. | 
| callSign		|| string |Optional. Broadcast call sign letters for the station.	|
| blackoutStation || boolean		| Determines the station's blackout status. Default value is _false_. . . |
| regionIDs    	|| string list	| List of region IDs to associate with this station. | 
| assetIDs    	|| string list	| List of asset IDs to associate with this station. |
| `metadata`	|| object		| Metadata identifying this channel. |
| source		| `metadata`	| string |	Source for this station.	|
| id			| `metadata`	| string |	ID for this station.	|
| publishStart 	|| string | Required. Availability start date in ISO-8601 timestamp format.  | 
| publishEnd   	|| string | Required. Availability end date in ISO-8601 timestamp format.  |  

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/stations/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "resourceType": "epg/stations",
    "name": "Chelsea TV",
    "shortName": "CHELTV",
    "stationNumber": 0,
    "language": "en",
    "languageRegion": "",
    "pictureID": "",
    "callSign": "",
    "blackoutStation": false,
    "regionIDs": [
        " "
    ],
    "assetIDs": [
        "aa35b530-7aa5-455f-8a1c-f8b1fcf91d61"
    ],
    "metadata": {
        "source": " ",
        "id": " "
    },
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



### 2. Update station


Updates an EPG schedule entry.

<br/>

In the request body, only include the fields that you wish to update. All other fields will retain their existing values.

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|stationID	|string		|required	|ID for the targeted station. |

<br/>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Name			|  Type			| Description |
|--------------:|---------------|-------------|
| resourceType	| enum string	| Required. Contains the value "epg/competitions". | 
| name    		| string | Required. Full name. (max char length?) . . . |
| shortName   	| string | Shortened name.   (max char length?) . . . |
| stationNumber | number | Station or channel number as designated by the tenant service.   |
| language    	| string | Required. Two-letter code for the spoken language.  |
| languageRegion| string | Code for the regional language variety, such as: en-*GB*, en-*US*, es-*419*, etc.| 
| pictureID    	| string | ID for the station logo or preview image. | 
| provider		| string | Metadata source provider.  |
| providerID	| string | Metadata source ID. 		|
| callSign		| string |Optional. Broadcast call sign letters for the station.	|
| blackoutStation | boolean		| Determines the station's blackout status. Default value is _false_. . . |
| genreIDs     	| string list	| List of existing genre IDs to associate with this station.| 
| genres    	| string list	| List of genres to associate with this station. | 
| regionIDs    	| string list	| List of region IDs to associate with this station. | 
| assetIDs    	| string list	| List of asset IDs to associate with this station. |
| publishStart 	| string | Required. Availability start date in ISO-8601 timestamp format.  | 
| publishEnd   	| string | Required. Availability end date in ISO-8601 timestamp format.  |  

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/stations/{{stationID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
            "id": "9ef1088b-c65a-474e-939a-499b533ad645",
            "resourceType": "epg/stations",
            "published": false,
            "created": "2019-03-28T20:37:27.56Z",
            "updated": "2019-04-08T18:54:01.021Z",
            "contentLock": false,
            "name": "National Geographic Colombia HD",
            "shortName": "NGCCLHD",
            "stationNumber": 0,
            "language": "es",
            "languageRegion": "",
            "pictureID": "6e9979a43879e5db57a694731ace2f62",
            "pictures": {
                "sourcelogo-dark": "68c2c05051cb6d944a9a95842eae5db3",
                "sourcelogo-gray": "79189a25d79b6a845c425e0636de8bdc",
                "sourcelogo-light": "bcf4a7c596ec2240ab6ebea098506376",
                "sourcelogo-white": "325aa8ee9368d1d5b25c03e784ee5274"
            },
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": [
                "83f0ebb2-c281-47d2-869f-26e46faa3e41"
            ],
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "80076"
            }
        }
```



### 3. Retrieve station


Returns information about the specified station.

All query parameters are optional unless otherwise indicated.

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|stationID	|string		|required	|ID for the targeted station. |



<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired. |
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station.|
|404		|1040				|*Not Found*: No matching station ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/stations/{{stationID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Returns information about one station | Code: 200



```js
{
    "requestID": "b12dee72-7878-40ed-bd45-33d04b1e659c",
    "timestamp": "2018-05-15T04:17:58.582329465Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/stations": [
        {
            "id": "9b5b41be0d8cbba96d3df2ee6c070d2c",
            "resourceType": "epg/stations",
            "name": "E! TV Latin America Andes HD",
            "shortName": "DETVLHD",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "5be1d9459b4ea6a073a14e0f021d6739",
            "provider": "com.gracenote.source",
            "providerID": "101256",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        }
    ]
}
```



### 4. List stations


Returns a paged list of stations.  

All query parameters are optional.

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station|
|404		|1040				|*Not Found*: No matching station ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/stations
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Geo-Position | 4.711;-74.0721 | Global position specified as {_longitude;latitude_}. |
| Origin |  |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| count | 15 | Maximum number of results returned. Used for pagination. |



***Responses:***


Status: Returns a list of stations | Code: 200



```js
{
    "requestID": "86b195d9-efdf-43b2-83c0-aab2faabe490",
    "timestamp": "2018-05-15T04:16:43.7091757Z",
    "metadata": {
        "count": 16,
        "totalCount": 36,
        "offset": 20
    },
    "epg/stations": [
        {
            "id": "b9cb940286345c9a12706529c96a03cd",
            "resourceType": "epg/stations",
            "name": "ESPN Latin South (53) HD",
            "shortName": "ESPNLHD",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "e4179e0c4e4bfd5e949dae141098fbaf",
            "provider": "com.gracenote.source",
            "providerID": "99064",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "49b2a80f2ad1a2025fe09bdb5a9163c1",
            "resourceType": "epg/stations",
            "name": "Cartoon Network Panamerican HD",
            "shortName": "TOONLSH",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "9c5e3387ef29a1a0282639188d379538",
            "provider": "com.gracenote.source",
            "providerID": "94799",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "d8a3f87892611c9024335675959bbd8e",
            "resourceType": "epg/stations",
            "name": "FX LATIN AMERICA HD (Central Feed)",
            "shortName": "FXLCNHD",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "c229b5b02d8b7c6d9db3bd807939efdf",
            "provider": "com.gracenote.source",
            "providerID": "82819",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "766fcb5442f0148418cd6993632f7e00",
            "resourceType": "epg/stations",
            "name": "Fox Sports AM Premium South HD",
            "shortName": "FSALSPH",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "1bb5c318c1a6edbb29c65f7487ce0416",
            "provider": "com.gracenote.source",
            "providerID": "68952",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "f4447529b0b75dc648e49eca5853026a",
            "resourceType": "epg/stations",
            "name": "H2 HD LATAM DTVPA",
            "shortName": "H2LAHD",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "45a8bd2f43b1bbd33aebeff547fc46f6",
            "provider": "com.gracenote.source",
            "providerID": "100817",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "6e052ff01d4abc80010878f49b5b1419",
            "resourceType": "epg/stations",
            "name": "Cinemax Sur HD",
            "shortName": "MAXSURH",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "5247905cbbde2be83ccd391246c06c3f",
            "provider": "com.gracenote.source",
            "providerID": "99082",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "b29e9eb4e380ed067ed94c16bf470fc3",
            "resourceType": "epg/stations",
            "name": "Discovery Turbo Latin America",
            "shortName": "DTURBOL",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "cc0f83b4d98ab8bee8260a8be9fbd47f",
            "provider": "com.gracenote.source",
            "providerID": "46608",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "4d05ec21750dfba4b3e538af0bad6703",
            "resourceType": "epg/stations",
            "name": "Fox Life Argentina HD",
            "shortName": "FXLARGH",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "7d468e04d2cec515c35408331a3ca67d",
            "provider": "com.gracenote.source",
            "providerID": "97256",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "5dcccd15c0f2fcd354b6478619d6aad0",
            "resourceType": "epg/stations",
            "name": "A&E (DTVLA) HD",
            "shortName": "DAEHD",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "28f72262515e50c826cc689c9ed4cc2c",
            "provider": "com.gracenote.source",
            "providerID": "100086",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "8ba455178c3dff65f6ec7ce90d9373a2",
            "resourceType": "epg/stations",
            "name": "Animal Planet Pan Regional HD",
            "shortName": "ANIPPRH",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "b0de33e71c9cda96c92ef1633e51971c",
            "provider": "com.gracenote.source",
            "providerID": "97482",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "2c9d846b952305055d88e7ab41553241",
            "resourceType": "epg/stations",
            "name": "Max Prime Panamericano HD",
            "shortName": "PRIMPHD",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "d2efbf66d04aad49081353ee34860b53",
            "provider": "com.gracenote.source",
            "providerID": "80211",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "addc716f8d8e9f22a7b7cfcbe9a47d17",
            "resourceType": "epg/stations",
            "name": "National Geographic Argentina HD",
            "shortName": "NGCARHD",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "a0eed870a303dfdb5b02f011fee7ed51",
            "provider": "com.gracenote.source",
            "providerID": "91909",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "dbd0b3777454440ec2c6b07992e211e8",
            "resourceType": "epg/stations",
            "name": "Warner HD Latin Am",
            "shortName": "WBLHD",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "69471d8809ea0011965f93f7a3f789da",
            "provider": "com.gracenote.source",
            "providerID": "72166",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "079fd2ea771cb01fd7d23feb4164ea19",
            "resourceType": "epg/stations",
            "name": "Sony ENT TV Colombia HD English",
            "shortName": "SETVCEN",
            "stationNumber": "",
            "language": "en",
            "languageRegion": "",
            "pictureID": "",
            "provider": "com.gracenote.source",
            "providerID": "91589",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": [
                "6c7d25484999c438953ca2d4e75e6132"
            ],
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "f739718a1a904f9a3120d5f505a57b27",
            "resourceType": "epg/stations",
            "name": "Nat Geo Kids",
            "shortName": "NGKLA",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "06c101bb72c153db1370502ca437be2a",
            "provider": "com.gracenote.source",
            "providerID": "104524",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        },
        {
            "id": "80dcbe7f997c5b51a77e8a4ae1dc2a60",
            "resourceType": "epg/stations",
            "name": "Atreseries HD",
            "shortName": "ATRES",
            "stationNumber": "",
            "language": "es",
            "languageRegion": "",
            "pictureID": "5c1ddc33bf3c2b192c51580d8a37dc1a",
            "provider": "com.gracenote.source",
            "providerID": "90898",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": null,
            "assetIDs": null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z"
        }
    ]
}
```



### 5. Delete station and associated schedules


Deletes the specified station and its associated schedules. 
. .
<!-- Does specifying the language query parameter only delete the station information for that particular language? -->

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|stationID	|string		|required	|ID for the targeted station. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified station.|
|404		|1040	|*Not Found*: No matching station ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/epg/stations/{{stationID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| If-None-Match | {{If-None-Match}} |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



### 6. Patch station


Patches the specified station resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the station to be updated. |

<br>

##### Body Parameters

| Name  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| stationNumber | | number | Station or channel number as designated by the tenant service.   |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| languageRegion | | string | Code for the regional language variety, such as: en-*GB*, en-*US*, es-*419*, etc.| 
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |
| callSign | | string | Broadcast call sign letters for the station. |
| blackoutStation | | boolean | Determines the station's blackout status. Default value is _false_. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/stations/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "contentLock": true,
    "name": "Fox Chile",
    "shortName": "FOXLCH",
    "stationNumber": 0,
    "language": "es",
    "languageRegion": "",
    "pictureID": "5fe3926c-8830-44f3-b446-85c8c5d576fe.png",
    "pictures": {
        "sourcelogo-dark": "a598044d-d03e-4a45-912a-c679b6c0380a.png",
        "sourcelogo-gray": "809eb62b-19d7-4691-91f5-6a53e58588cb.png",
        "sourcelogo-light": "b4497ce6-4b07-4e17-a783-f52d6331f856.png",
        "sourcelogo-white": "335dcc94-f526-44ed-b12c-cdcec2c21307.png"
    },
    "callSign": "",
    "blackoutStation": false,
    "metadata": {
        "source": "com.gracenote.on-v3",
        "id": "56111"
    }
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "16ce832c-8bee-4d3f-9da8-69512e2fe561",
    "timestamp": "2020-03-24T03:55:23.731327Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/stations": [
        {
            "id": "dbba319d-3d03-4cf9-8e16-849dc12b862e",
            "resourceType": "epg/stations",
            "publishStart": "2019-01-01T15:00:00Z",
            "published": true,
            "created": "0001-01-01T00:00:00Z",
            "updated": "2020-03-24T03:55:22.117Z",
            "contentLock": true,
            "name": "Fox Chile",
            "shortName": "FOXLCH",
            "stationNumber": 0,
            "language": "es",
            "languageRegion": "",
            "pictureID": "5fe3926c-8830-44f3-b446-85c8c5d576fe.png",
            "pictures": {
                "sourcelogo-dark": "a598044d-d03e-4a45-912a-c679b6c0380a.png",
                "sourcelogo-gray": "809eb62b-19d7-4691-91f5-6a53e58588cb.png",
                "sourcelogo-light": "b4497ce6-4b07-4e17-a783-f52d6331f856.png",
                "sourcelogo-white": "335dcc94-f526-44ed-b12c-cdcec2c21307.png"
            },
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": [
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5"
            ],
            "assetIDs": [
                "fb2c4df6-be54-4919-9153-e59f4841f973"
            ],
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "56111"
            }
        }
    ]
}
```



## v2/epg/teamcompetitions



### 1. Create EPG team competition


Creates a team competition entry in the EPG schedule.

<br>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Name			| Parent	|  Type	| Description |
|--------------:|-----------|-------|-------------|
| resourceType	|| enum string	| Required. Contains the value "epg/teamCompetitions". | 
| startTime |   	| string | Required. Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number | Required. Video duration in minutes.  |  
| name    		|| string | Required. Full competition name. . . |
| shortName   	|| string | Shortened competition name. . . |
| description |     | string | Full description. . .|
| shortDescription| | string | Shortened description. . .|
| language    	|| string | Required. Two-letter code for the spoken language.  |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this team competition. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  
| ratings |     	| string list | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this team competition. | 
| genreIDs |    	| string list | List of genre IDs associated with this team competition. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this team competition. |
| sportID |     	| string | ID for the sport associated with this team competition. | 
| sportName |   	| string | Name for the sport associated with this team competition. | 
| tournamentID |    | string | ID for the tournament associated with this team competition.  | 
| tournamentName |  | string | Name for the tournament associated with this team competition. | 
| primaryTeamID |     	| string | ID for the primary or home team. | 
| primaryTeamName |   	| string | Name for the primary or home team. | 
| primaryTeamPictureID |  | string | ID for picture of the primary or home team. | 
| secondaryTeamID | 	  | string | ID for the secondary or away team. | 
| secondaryTeamName |     | string | Name for the secondary or away team. | 
| secondaryTeamPictureID| | string | ID for picture of the secondary or away team. | 
| publishStart 	|| string | Required. Availability start date in ISO-8601 timestamp format.  | 
| publishEnd   	|| string | Required. Availability end date in ISO-8601 timestamp format.  |  

<br/>

<!-- The following fields are not currently included in this endpoint:

| stationNumber || number | Station or channel number as designated by the tenant service.   |
| languageRegion|| string | Code for the regional language variety, such as: en-*GB*, en-*US*, es-*419*, etc.| 
| callSign		|| string |Optional. Broadcast call sign letters for the station.	|
| blackoutStation || boolean		| Determines the station's blackout status. Default value is _false_. . . |
| regionIDs    	|| string list	| List of region IDs to associate with this station. | 
| `metadata`	|| object		| Metadata identifying this channel. |
| source		| `metadata`	| string |	Source for this station.	|
| id			| `metadata`	| string |	ID for this station.	|
| gameID |    		| string | ID for the game associated with this team competition. | 

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/teamCompetitions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "epg/teamCompetitions",
    "startTime": "2018-04-28T02:00:00Z",
    "endTime": "2018-04-28T05:00:00Z",
    "duration": 0,
    "name": "New York Yankees en Los Angeles Angels",
    "shortName": "New York Yankees en Los Angeles Angels",
    "description": "Los Angels reciben a los Yankees en una serie de 3 juegos. Los Angeles derrotaron a New York en 4 de los 6 juegos el año pasado. Esa fue la primera serie anual en la que los Angels derrotan a los Yankees desde 2008.",
    "shortDescription": "Yankees enfrentan a Angels en California.",
    "language": "es",
    "pictureID": "",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": null,
    "ratingAdvisories": null,
    "stationID": "",
    "genreIDs": null,
    "assetIDs": null,
    "sportID": "",
    "sportName": "",
    "tournamentID": "",
    "tournamentName": "",
    "primaryTeamID": "",
    "primaryTeamName": "",
    "primaryTeamPictureID": "",
    "secondaryTeamID": "",
    "secondaryTeamName": "",
    "secondaryTeamPictureID": "",
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



### 2. Update scheduled team competition


Updates the EPG entry for the specified team competition.

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID for the target team competition entry. |

<br/>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Name  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| resourceType |    | enum string | Required. Contains the value "epg/teamCompetitions". | 
| startTime |   	| string | Required. Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number | Required. Video duration in minutes.  |  
| name |    		| string | Required. Full name. . . |
| shortName |   	| string | Shortened name. . . |
| description |     | string | Full description. . .|
| shortDescription| | string | Shortened description. . .|
| language |    	| string | Required. Two-letter code for the spoken language.  |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this team competition. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  
| ratings |     	| string list | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this team competition. | 
| genreIDs |    	| string list | List of genre IDs associated with this team competition. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this EPG competition. |
| sportID |     	| string | ID for the sport associated with this team competition. | 
| sportName |   	| string | Name for the sport associated with this team competition. | 
| gameID |    		| string | ID for the game associated with this team competition. | 
| tournamentID |    | string | ID for the tournament associated with this team competition.  | 
| tournamentName |  | string | Name for the tournament associated with this team competition. | 
| primaryTeamID |     	| string | ID for the primary or home team. | 
| primaryTeamName |   	| string | Name for the primary or home team. | 
| primaryTeamPictureID |  | string | ID for picture of the primary or home team. | 
| secondaryTeamID | 	  | string | ID for the secondary or away team. | 
| secondaryTeamName |     | string | Name for the secondary or away team. | 
| secondaryTeamPictureID| | string | ID for picture of the secondary or away team. | 
| publishStart |	| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 
| publishEnd|		| string | Date when the asset appears on EPG and schedules. Timestamp in ISO 8601 format. | 

<br/>

<!--
NOTE: The following fields are currently NOT included in this endpoint: 
leagueID, leagueName, gameID, venue, genres, regionIDs 

We should also include the maximum character lengths for the name, shortName, description and shortDescription fields.

-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "resourceType": "epg/teamCompetitions",
    "startTime": "2018-04-28T02:00:00Z",
    "endTime": "2018-04-28T05:00:00Z",
    "duration": 0,
    "name": "New York Yankees en Los Angeles Angels",
    "shortName": "New York Yankees en Los Angeles Angels",
    "description": "Los Angels reciben a los Yankees en una serie de 3 juegos. Los Angeles derrotaron a New York en 4 de los 6 juegos el año pasado. Esa fue la primera serie anual en la que los Angels derrotan a los Yankees desde 2008.",
    "shortDescription": "Yankees enfrentan a Angels en California.",
    "language": "es",
    "pictureID": "",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": null,
    "ratingAdvisories": null,
    "stationID": "",
    "genreIDs": null,
    "assetIDs": null,
    "sportID": "",
    "sportName": "",
    "gameID": "1234",
    "tournamentID": "",
    "tournamentName": "",
    "primaryTeamID": "",
    "primaryTeamName": "",
    "primaryTeamPictureID": "",
    "secondaryTeamID": "",
    "secondaryTeamName": "",
    "secondaryTeamPictureID": "",
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



### 3. Retrieve scheduled team game from the EPG


Retrieves the EPG entry for the specified team competition.

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID for the target team competition entry. |

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested team competition|
|404		|1040				|*Not Found*: No matching steam competition found|

<br/>

<!--

#### Response object
The Notes column describes default and possible values, valid ranges, and fields that are nullable ( ø ), or required ( ʀ ). All fields are optional unless otherwise indicated.

| Name  | Parent |  Type  | Description | Notes
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   | 
||||||
| `metadata` |   |    |    |   |  
| count | metadata |number  | Current screen.  | min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  | min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. | min=1, max = 20
||||||
| *`epg/teamCompetitions`* |   |   |      |  |
| id | epg/teamCompetitions |string | Unique ID for each asset.  |  |
| resourceType | epg/teamCompetitions | enum string | "epg/teamCompetitions" | |
| startTime | epg/teamCompetitions | string | A timestamp.  |  |
| endTime | epg/teamCompetitions | string | A timestamp.  |  |
| duration | epg/teamCompetitions | number | Video duration in minutes.  |  |
| name | epg/teamCompetitions | string | Full name.  | (max char length?) |
| shortName | epg/teamCompetitions | string |   | (max char length?) |
| description | epg/teamCompetitions | string | Full description.  | (max char length?) |
| shortDescription | epg/teamCompetitions | string |   | (max char length?) |
| language | epg/teamCompetitions | string | Two-letter code for the spoken language.  |  |
| ratings | epg/teamCompetitions | string | Age-related ratings from boards and agencies. | ø  |
| ratingAdvisories | epg/teamCompetitions | string list | A list of content advisories.  | ø, Such as "Adult Situations", "Language", or "Violence" |
| stationID | epg/teamCompetitions | string  |  | |
| genreIDs | epg/teamCompetitions | string | | ø; |
| sportID | epg/teamCompetitions | string | | |
| sportName | epg/teamCompetitions | string | | |
| tournamentID | epg/teamCompetitions | string | | |
| tournamentName | epg/teamCompetitions | string | | |
| primaryPersonID | epg/teamCompetitions | string | | |
| primaryPersonName | epg/teamCompetitions | string | | |
| primaryPersonPictureID | epg/teamCompetitions | string | | |
| secondaryPersonID | epg/teamCompetitions | string | | |
| secondaryPersonName | epg/teamCompetitions | string | | |
| secondaryPersonPictureID | epg/teamCompetitions | string | | |
| assetIDs | epg/teamCompetitions | string | | ø; |
| pictureID | epg/teamCompetitions | string | ID for the standard image |  | 
||||||
| *`pictures`* | epg/teamCompetitions |  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. |  | 
| 3x4  | pictures | string | ID for a 3x4 image.  |  | 
| 4x3  | pictures | string | ID for a 4x3 image.  |  | 
| 16x9 | pictures | string | ID for a 16x9 image.  |  | 

-->

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/epg/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Retrieve scheduled team game from the EPG | Code: 200



```js
{
	"requestID":"2d563a76-22c4-4e44-94d3-80e99ab9aca6",
	"timestamp":"2018-05-15T04:22:55.847098738Z",
	"metadata":{
		"count":1,
		"totalCount":1,
		"offset":0
	},
	"epg/teamCompetitions":[
		{
			"id":"38cdd1fdbb061ff71f9fe3607c1e633f",
			"resourceType":"epg/teamCompetitions",
			"startTime":"2018-04-28T02:00:00Z",
			"endTime":"2018-04-28T05:00:00Z",
			"duration":0,
			"name":"New York Yankees en Los Angeles Angels",
			"shortName":"New York Yankees en Los Angeles Angels",
			"description":"Los Angels reciben a los Yankees en una serie de 3 juegos. Los Angeles derrotaron a New York en 4 de los 6 juegos el año pasado. Esa fue la primera serie anual en la que los Angels derrotan a los Yankees desde 2008.",
			"shortDescription":"Yankees enfrentan a Angels en California.",
			"language":"es",
			"pictureID":"",
			"pictures":{
				"2x3":null,
				"3x4":null,
				"4x3":null,
				"16x9":null
			},
			"ratings":null,
			"ratingAdvisories":null,
			"stationID":"",
			"genreIDs":null,
			"assetIDs":null,
			"sportID":"",
			"sportName":"",
			"tournamentID":"",
			"tournamentName":"",
			"primaryTeamID":"",
			"primaryTeamName":"",
			"primaryTeamPictureID":"",
			"secondaryTeamID":"",
			"secondaryTeamName":"",
			"secondaryTeamPictureID":"",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		}
	]
}
```



### 4. Delete EPG team competition


Deletes the specified EPG team competition. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|id	|string		|required	|ID for the targeted EPG team competition. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified EPG team competition.|
|404		|1040	|*Not Found*: No matching EPG team competition ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request.   |
| Content-Type | application/json | ETag header for cache validation.  |



### 5. Patch EPG team competition


Patches the specified EPG team competition resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID of the EPG team competition to be updated. | 

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this resource. | 
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| blackoutRegionIDs | | string list, allows null | |
| metadata |        | object |  |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| sportID |     	| string | ID for the sport associated with this resource. | 
| sportName |   	| string | Name for the sport associated with this resource. | 
| leagueID |        | string | |
| leagueName |      | string | |
| tournamentID |    | string | ID for the tournament associated with this resource.  | 
| tournamentName |  | string | Name for the tournament associated with this resource. | 
| gameID |    		| string | ID for the game associated with this resource. | 
| primaryTeamID |     	| string | ID for the primary or home team. | 
| primaryTeamName |   	| string | Name for the primary or home team. | 
| primaryTeamPictureID |  | string | ID for picture of the primary or home team. | 
| secondaryTeamID | 	  | string | ID for the secondary or away team. | 
| secondaryTeamName |     | string | Name for the secondary or away team. | 
| secondaryTeamPictureID| | string | ID for picture of the secondary or away team. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/epg/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "duration": 9000,
    "name": "Brooklyn Nets vs. Boston Celtics",
    "shortName": "Baloncesto NBA",
    "description": "Los Celtics y los Nets chocan por tercera vez en la 2019-20. El equipo con condición de local ha ganado cada uno de últimos 7 partidos entre ambos equipos. Spencer Dinwiddle (BKN) promedia 24 puntos por juego ante Boston en la campaña.",
    "shortDescription": "Los Celtics y los Nets chocan por tercera vez en la 2019-20, en el TD Garden.",
    "language": "es",
    "ratings": null,
    "ratingAdvisories": null,
    "stationID": "c459315bcc20d2febab6c84c3156c8f9",
    "genreIDs": [
        "69107b1e-b3f8-4d61-be8e-49b8bccf6053"
    ],
    "assetIDs": [
        "3f6bfc6e6082b218383ad042ae3d3b1c"
    ],
    "regionIDs": [
        "2e167237-c7bb-423b-b606-c31115adb1da",
        "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
        "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
        "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
        "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
        "141a53b6-af6f-4092-ba1f-c289659310f2"
    ]
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "97faf54d-8c13-498b-a13e-3ec126330776",
    "timestamp": "2020-03-23T23:57:27.284204Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/teamCompetitions": [
        {
            "id": "55a85edf-471c-480a-a002-db4d8482eda5",
            "resourceType": "epg/teamCompetitions",
            "publishStart": "2020-03-21T00:02:54.265Z",
            "publishEnd": "2020-03-24T13:30:00Z",
            "published": true,
            "created": "2020-03-18T19:40:59.706Z",
            "updated": "2020-03-23T23:57:27.28Z",
            "contentLock": false,
            "startTime": "2020-03-21T13:30:00Z",
            "endTime": "2020-03-21T16:00:00Z",
            "duration": 9000,
            "name": "Brooklyn Nets vs. Boston Celtics",
            "shortName": "Baloncesto NBA",
            "description": "Los Celtics y los Nets chocan por tercera vez en la 2019-20. El equipo con condición de local ha ganado cada uno de últimos 7 partidos entre ambos equipos. Spencer Dinwiddle (BKN) promedia 24 puntos por juego ante Boston en la campaña.",
            "shortDescription": "Los Celtics y los Nets chocan por tercera vez en la 2019-20, en el TD Garden.",
            "language": "es",
            "pictureID": "49717731-04b0-420e-ba09-e92e3ea517da.jpg",
            "pictures": {
                "16x9": "49717731-04b0-420e-ba09-e92e3ea517da.jpg",
                "2x3": "05075694-8a1c-4d64-9f96-decaefc9d0c3.jpg",
                "3x4": "2ba6867a-1ec8-4818-a89e-e5ceba7fce91.jpg",
                "4x3": "7f4ba232-4d47-4703-ae40-0122105f8724.jpg"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "c459315bcc20d2febab6c84c3156c8f9",
            "genreIDs": [
                "69107b1e-b3f8-4d61-be8e-49b8bccf6053"
            ],
            "genres": [
                {
                    "id": "69107b1e-b3f8-4d61-be8e-49b8bccf6053",
                    "name": "Basquetbol"
                }
            ],
            "assetIDs": [
                "3f6bfc6e6082b218383ad042ae3d3b1c"
            ],
            "regionIDs": [
                "2e167237-c7bb-423b-b606-c31115adb1da",
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
                "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "141a53b6-af6f-4092-ba1f-c289659310f2"
            ],
            "blackoutRegionIDs": null,
            "blackout": false,
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "EP030312281816"
            },
            "sportID": "",
            "sportName": "",
            "leagueID": "",
            "leagueName": "",
            "tournamentID": "",
            "tournamentName": "",
            "gameID": "",
            "primaryTeamID": "",
            "primaryTeamName": "",
            "primaryTeamPictureID": "",
            "secondaryTeamID": "",
            "secondaryTeamName": "",
            "secondaryTeamPictureID": ""
        }
    ]
}
```



## v2/genres



### 1. List genres


Lists available genres for shows and channels.

<br/>

##### Response object 
| Field  | Parent | Type | Description |  
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| *`genres`* |   | array |  List of genre resources |   |
|id|genre|string|Unique identifier|
|resourceType|genre|string|Always "genres" |
|name|genre|string|Name of genre
|shortName|genre|string| Short name of genre|
|language|genre|string| Language of genre|
|publishStart|	|string	| First date that this content is visible to end users. ISO 8601 format: 2019-01-01T15:00:00Z
|publishEnd|	|string	| Last date that this content is visible to end users. ISO 8601 format:2020-09-01T07:00:00Z
|published|		|boolean| Shows if the asset publicly available.

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station resources|

<!--|404		|1040				|*Not Found*: No matching station ID found|-->

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/genres
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| offset | 0 | Number of items to skip from the start of the list; default = 0. |
| count |  |  |



***Responses:***


Status: List genres | Code: 200



```js
{
	"requestID":"9c3d78c8-a6ef-41b8-a435-6295ca6b4950",
	"timestamp":"2018-05-15T04:14:08.0156887Z",
	"metadata":{
		"count":20,
		"totalCount":163,
		"offset":20
	},
	"genres":[
		{
			"id":"067d70ff2bcc556a913e52da08cc9139",
			"resourceType":"genres",
			"name":"Adventure",
			"shortName":"Adventure",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"61e296bd844c24797d87db2a04ab59ac",
			"resourceType":"genres",
			"name":"Medical",
			"shortName":"Medical",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"a9d89bec1f4dd0045797b615dd733244",
			"resourceType":"genres",
			"name":"Religious",
			"shortName":"Religious",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"6741d8b7bdb176d9dfced66c79fa197c",
			"resourceType":"genres",
			"name":"Travel",
			"shortName":"Travel",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"e71b91bc15597ac5c0a2fbd50f3f8336",
			"resourceType":"genres",
			"name":"Science fiction",
			"shortName":"Science fiction",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"51bf35c00f9566e79ed79bd00b9fba83",
			"resourceType":"genres",
			"name":"Sitcom",
			"shortName":"Sitcom",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"4b7c4e1a01f4dbac6501656c9ea58840",
			"resourceType":"genres",
			"name":"Cooking",
			"shortName":"Cooking",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"557c02daad97c095c1eccbf7970d7a1e",
			"resourceType":"genres",
			"name":"Crime drama",
			"shortName":"Crime drama",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"d775f75f857ae6a6c2b33e487686da54",
			"resourceType":"genres",
			"name":"Mystery",
			"shortName":"Mystery",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"796398d76c22b7186bb5897cf4e67f59",
			"resourceType":"genres",
			"name":"Thriller",
			"shortName":"Thriller",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"f3d40476747c2a9ac274aa2ea160cacb",
			"resourceType":"genres",
			"name":"Outdoors",
			"shortName":"Outdoors",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"c6a19847abe30757fc05879143a3a412",
			"resourceType":"genres",
			"name":"Exercise",
			"shortName":"Exercise",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"1273f608e4eff289fd71ebff1199baba",
			"resourceType":"genres",
			"name":"Dance",
			"shortName":"Dance",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"b256764d6e11a1ed95b6794b1d0046c4",
			"resourceType":"genres",
			"name":"House/garden",
			"shortName":"House/garden",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"2a108151454214ca584a1a0c15ef2879",
			"resourceType":"genres",
			"name":"Home improvement",
			"shortName":"Home improvement",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"9923fb272e72ae070fadfc36af5adbc8",
			"resourceType":"genres",
			"name":"Bus./financial",
			"shortName":"Bus./financial",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"f5d5ea511e993e0f730307e1fe0a12c1",
			"resourceType":"genres",
			"name":"Comedy",
			"shortName":"Comedy",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"6b440527cd19427281379a5d5d1ef33f",
			"resourceType":"genres",
			"name":"Art",
			"shortName":"Art",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"f47988f829aebea541881860fea8e563",
			"resourceType":"genres",
			"name":"Environment",
			"shortName":"Environment",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		},
		{
			"id":"453670e245c05936181ec3c7d4a41adb",
			"resourceType":"genres",
			"name":"Golf",
			"shortName":"Golf",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		}
	]
}
```



### 2. Retrieve genre


Returns the specified genre.

<br/>

<!--	Original endpoint:
		{{OCMServer}}/ocm/v2/genres/067d70ff2bcc556a913e52da08cc9139?language=* 
-->

##### Path Parameters

|Label|Data type|Required|Description|
|---|---|---|---|
|`genreID`|string|required|Unique identifier of requested genre|

<br/>

##### Response object 

| Field  | Parent | Type | Description |  
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number	| Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number	| Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| *`genres`* |   | array |  List of genre resources |   |
|id			|*`genres`*|string|Unique identifier|	|
|resourceType|*`genres`*|string|Value is always "_genres_". | |
|name		|*`genres`*|string|Name of genre|	|
|shortName	|*`genres`*|string| Short name of genre|	|
|language	|*`genres`*|string| Language of genre|	|
|publishStart|	|string	| First date that this content is visible to end users. ISO 8601 format: 2019-01-01T15:00:00Z
|publishEnd|	|string	| Last date that this content is visible to end users. ISO 8601 format:2020-09-01T07:00:00Z
|published|		|boolean| Shows if the asset publicly available.

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station resources|
|404		|1040				|*Not Found*: No matching genre ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/genres/{{genreID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | _Required_. Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Get genre | Code: 200



```js
{
	"requestID":"c91fa0a7-f82c-4b18-a701-7a59a5ec779e",
	"timestamp":"2018-06-07T12:52:49.671562729Z",
	"metadata":{
		"count":1,
		"totalCount":1,
		"offset":0
	},
	"genres":[
		{
			"id":"067d70ff2bcc556a913e52da08cc9139",
			"resourceType":"genres",
			"name":"Adventure",
			"shortName":"Adventure",
			"language":"es",
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		}
	]
}
```



## v2/images



### 1. Upload a new image


Uploads an image file.

<!-- The descriptor and title don't seem to be talking about the same thing! -->

<br>

##### Body Parameters

|Field  |Type	|Required	|Description	|
|---    |---	|---		|---    		|
|image  |file   |required	|Image file that you wish to upload.|

<br>

##### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**400**|1052|*Bad Request*: The image was rejected as invalid|

<br/>

<!--

<br/>

#### Response object 

| Name  | Parent | Type | Description | Notes 
|------:|--------|------|-------------|-------
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| *`images`* |   |   |   |   |  
| id  | images | number  | ID for an image that was uploaded||


<br/>

-->


***Endpoint:***

```bash
Method: POST
Type: FORMDATA
URL: {{OCMServer}}/ocm/v2/images
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

| Key | Value | Description |
| --- | ------|-------------|
| image |  | Select  one or more image files to upload. |



### 2. Delete images


Deletes the specified image files.

<br>

##### Body Parameters

|Field  |Type	|Required	|Description	|
|---    |---	|---		|---    		|
|imageIds  |file list |required	|Image files that you wish to delete.|

<br>

##### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**400**|1040|*Not Found*: Specified image was not found.|
|**400**|1050, 1060|*Bad Request*: Image data incomplete or invalid.|


<br/>

<!--

#### Response object 

| Name  | Parent | Type | Description | Notes 
|------:|--------|------|-------------|-------
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| *`metadata`* |   |   |   |   |  
| count  | metadata | number  | Number of items returned.  ||
| totalCount| metadata | number | Total number of items.  ||
| offset | metadata | number | Offset from begging of list || 
| *`results`* |   | array |  List of various resources |   |
| *`entitled`* |   | array | List of entitled resource IDs | Present only if include=entitlements|
|**(varies)**||object|Properties vary by resource type||

<br/>

-->


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/images
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
	"imageIds": [ 


	]
}


```



## v2/live/competitions



### 1. Create live competition


Create a live competition (a game that is not scheduled on a channel or available as a VOD).

**Note: This API is available only for the new non-SportsRocket CMS.**


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/competitions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "live/competitions",
    "startTime": "2018-04-26T10:30:00Z",
    "endTime": "2018-04-26T11:00:00Z",
    "isLive": false,
    "name": "Márcio Lima",
    "shortName": "Márcio Lima",
    "description": "BOB Márcio Lima é um instrutor de rapel em caverna, proprietário da Lobo Guará Bike Adventure e guia de mountain bike. Trabalha com sustentabilidade, saúde para o corpo e contribuições ao meio ambiente.",
    "shortDescription": "Márcio Lima é um instrutor de rapel.",
    "venue": "",
    "language": "pt",
    "pictureID": "asdf",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
    ],
    "ratingAdvisories": null,
    "genreIDs": null,
    "genres": null,
    "regionIDs": null,
    "sportID": "",
    "sportName": "",
    "leagueID": "",
    "leagueName": "",
    "gameID": "1234",
    "tournamentID": "",
    "tournamentName": "",
    "primaryPersonID": "",
    "primaryPersonName": "",
    "primaryPersonPictureID": "",
    "secondaryPersonID": "",
    "secondaryPersonName": "",
    "secondaryPersonPictureID": "",
    "assetIDs": null,
    "publishStart": "2019-01-01T15:00:00Z",
    "publishEnd": "2020-09-01T07:00:00Z"
}
```



### 2. Update live competition


Updates the EPG entry for a live competition (a game that is not scheduled on a channel or available as a VOD).

**Note: This API is available only for the new non-SportsRocket CMS.**

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID for the target live competition entry. |

<br/>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| id |    		| string | ID associated with this live competition. | 
| resourceType |    | enum string | Required. Contains the value "live/competitions". | 
| startTime |   	| string | Required. Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. Ending time in ISO-8601 timestamp format.  |  
| isLive |    	| boolean | Required. Live status of this event.  |  
| name |    		| string | Required. Full name. . . |
| shortName |   	| string | Shortened name. . . |
| description |     | string | Full description. . .|
| shortDescription| | string | Shortened description. . .|
| venue	|    	| string | Name of the location where the event takes place.  |  
| language |    	| string | Required. Two-letter code for the spoken language.  |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this competition. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  
| ratings |     	| string list | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| genreIDs |    	| string list | List of genre IDs associated with this live competition. | 
| genres |  		| string list | List of genres associated with this live competition. | 
| regionIDs |    	| string list | List of region IDs associated with this live competition. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this live competition. |
| sportID |     	| string | ID for the sport associated with this live competition. | 
| sportName |   	| string | Name for the sport associated with this competition. | 
| leagueID |    | string | ID for the league associated with this live competition.  | 
| leagueName |  | string | Name for the league associated with this live competition. | 
| tournamentID |    | string | ID for the tournament associated with this live competition.  | 
| tournamentName |  | string | Name for the tournament associated with this live competition. | 
| primaryPersonID |     	| string | ID for the primary or home competitor. | 
| primaryPersonName |   	| string | Name for the primary or home competitor. | 
| primaryPersonPictureID |  | string | ID for picture of the primary or home competitor. | 
| secondaryPersonID | 	  | string | ID for the secondary or away competitor. | 
| secondaryPersonName |     | string | Name for the secondary or away competitor. | 
| secondaryPersonPictureID| | string | ID for picture of the secondary or away competitor. | 
| publishStart |   	| string | Required. Publishing start date/time in ISO-8601 timestamp format.  | 
| publishEnd |     	| string | Required. Publishing end date/time in ISO-8601 timestamp format.  |  

<br/>

<!--

NOTE: The following fields are currently NOT included in this endpoint: 
duration
| gameID |    		| string | ID for the game associated with this live competition. | 
| stationID |   	| string | ID for the station associated with this competition. | 


We should also include the maximum character lengths for the name, shortName, description and shortDescription fields.

-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/competitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
	"id": "{{id}}",
    "resourceType": "live/competitions",
    "startTime": "2018-04-26T10:30:00Z",
    "endTime": "2018-04-26T11:00:00Z",
    "isLive": false,
    "name": "Márcio Lima",
    "shortName": "Márcio Lima",
    "description": "BOB Márcio Lima é um instrutor de rapel em caverna, proprietário da Lobo Guará Bike Adventure e guia de mountain bike. Trabalha com sustentabilidade, saúde para o corpo e contribuições ao meio ambiente.",
    "shortDescription": "Márcio Lima é um instrutor de rapel.",
    "venue": "",
    "language": "pt",
    "pictureID": "asdf",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
    ],
    "ratingAdvisories": null,
    "genreIDs": null,
    "genres": null,
    "regionIDs": null,
    "sportID": "",
    "sportName": "",
    "leagueID": "",
    "leagueName": "",
    "gameID": "1234",
    "tournamentID": "",
    "tournamentName": "",
    "primaryPersonID": "",
    "primaryPersonName": "",
    "primaryPersonPictureID": "",
    "secondaryPersonID": "",
    "secondaryPersonName": "",
    "secondaryPersonPictureID": "",
    "assetIDs": null,
	"publishStart": "2019-01-01T15:00:00Z",
	"publishEnd": "2020-09-01T07:00:00Z"
}
```



### 3. Retrieve live competition


Retrieves the specified live competition (a game that is not scheduled on a channel or available as a VOD).

**Note: This API is available only for the new non-SportsRocket CMS.**

<br/>

##### Path Parameters
|Name|Data type|Required|Description|
|---|---|---|---|
|id|string|required|Live competition identifier.|

<br/>

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested live competition entry|
|404		|1040				|*Not Found*: No matching scheduled live competition found|

<br/>

<!--

<br/>
#### Response object
The Notes column describes default and possible values, valid ranges, and fields that are nullable ( ø ), or required ( ʀ ). All fields are optional unless otherwise indicated.

<br>

| Name  | Parent |  Type  | Description | Notes
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata` |   |    |    |   |  
| count | metadata |number  | Current screen.  | min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  | min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. | min=1, max = 20
||||||
| *`live/competitions`* |   |   |      |  |
| id | live/competitions |string | Unique ID for each asset.  |  |
| resourceType | live/competitions | enum string | "epg/competitions" | |
| startTime | live/competitions | string | A timestamp.  |  |
| endTime | live/competitions | string | A timestamp.  |  |
| duration | live/competitions | number | Video duration in minutes.  |  |
| name | live/competitions | string | Full name.  | (max char length?) |
| shortName | live/competitions | string |   | (max char length?) |
| description | live/competitions | string | Full description.  | (max char length?) |
| shortDescription | live/competitions | string |   | (max char length?) |
| isLive | live/competitions | boolean | Is game streaming now? | |
| venue | live/competitions | string |   | (max char length?) |
| language | live/competitions | string | Two-letter code for the spoken language.  |  |
| ratings | live/competitions | string | Age-related ratings from boards and agencies. | ø  |
| ratingAdvisories | live/competitions | string list | A list of content advisories.  | ø, Such as "Adult Situations", "Language", or "Violence" |
| genreIDs | live/competitions | string | | ø; |
| sportID | live/competitions | string | | |
| sportName | live/competitions | string | | |
| leagueID | live/competitions | string | | |
| leagueName | live/competitions | string | | |
| tournamentID | live/competitions | string | | |
| tournamentName | live/competitions | string | | |
| primaryPersonID | live/competitions | string | | |
| primaryPersonName | live/competitions | string | | |
| primaryPersonPictureID | live/competitions | string | | |
| secondaryPersonID | live/competitions | string | | |
| secondaryPersonName | live/competitions | string | | |
| secondaryPersonPictureID | live/competitions | string | | |
| assetIDs | live/competitions | string | | ø; |
| pictureID | live/competitions | string | ID for the standard image |  | 
||||||
| *`pictures`* | live/competitions |  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. |  | 
| 3x4  | pictures | string | ID for a 3x4 image.  |  | 
| 4x3  | pictures | string | ID for a 4x3 image.  |  | 
| 16x9 | pictures | string | ID for a 16x9 image.  |  | 

<br/>

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/live/competitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Retrieve scheduled game from the EPG | Code: 200



```js
{
	"requestID":"3615a4c8-5eef-48c3-817f-7c51b0996629",
	"timestamp":"2018-05-15T04:22:29.721400028Z",
	"metadata":{
		"count":1,
		"totalCount":1,
		"offset":0
	},
	"epg/competitions":[
		{
			"id":"4ec20201a14219cd9331c456c5418a94",
			"resourceType":"epg/competitions",
			"startTime":"2018-04-27T10:46:00Z",
			"endTime":"2018-04-27T11:40:00Z",
			"duration":0,
			"name":"Batallas con Marlines",
			"shortName":"Batallas con Marlines",
			"description":"Cyril está en Costa Rica por una razón importante. La búsqueda del pez más grande y poderoso del océano (450 kg), el pez espada.",
			"shortDescription":"La búsqueda del pez espada.",
			"language":"es",
			"pictureID":"7ea58145199cbae11657ed24007928e0",
			"pictures":{
				"2x3":"04aaa1f2a9a7b2c38e95104494b81cdf",
				"3x4":"e7f7e8986dcc8d6a91d25af310d89911",
				"4x3":"8639a78516070c5214ce6e7112cd6690",
				"16x9":"7ea58145199cbae11657ed24007928e0"
			},
			"ratings":[
				"Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
				"USA Parental Rating}/TVPG",
				"Canadian Parental Rating/PG",
				"Film Publication Board/10-12 PG"
			],
			"ratingAdvisories":null,
			"stationID":"",
			"genreIDs":null,
			"sportID":"",
			"sportName":"",
			"tournamentID":"",
			"tournamentName":"",
			"primaryPersonID":"",
			"primaryPersonName":"",
			"primaryPersonPictureID":"",
			"secondaryPersonID":"",
			"secondaryPersonName":"",
			"secondaryPersonPictureID":"",
			"assetIDs":null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		}
	]
}
```



### 4. Delete live competition


Removes a live competition (a game that is not scheduled on a channel or available as a VOD) from the CMS.

**Note: This API is available only for the new non-SportsRocket CMS.**

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|ID	|string		|required	|ID for the live competition game. |

<br>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified live game.|
|404		|1040	|*Not Found*: No matching live game ID found.|

<br>

<!--

#### Response object
The Notes column describes default and possible values, valid ranges, and fields that are nullable ( ø ), or required ( ʀ ). All fields are optional unless otherwise indicated.

<br>

| Name  | Parent |  Type  | Description | Notes
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |

-->


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/live/competitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Retrieve scheduled game from the EPG | Code: 200



```js
{"requestID":"3615a4c8-5eef-48c3-817f-7c51b0996629","timestamp":"2018-05-15T04:22:29.721400028Z","metadata":{"count":1,"totalCount":1,"offset":0},"epg/competitions":[{"id":"4ec20201a14219cd9331c456c5418a94","resourceType":"epg/competitions","startTime":"2018-04-27T10:46:00Z","endTime":"2018-04-27T11:40:00Z","duration":0,"name":"Batallas con Marlines","shortName":"Batallas con Marlines","description":"Cyril está en Costa Rica por una razón importante. La búsqueda del pez más grande y poderoso del océano (450 kg), el pez espada.","shortDescription":"La búsqueda del pez espada.","language":"es","pictureID":"7ea58145199cbae11657ed24007928e0","pictures":{"2x3":"04aaa1f2a9a7b2c38e95104494b81cdf","3x4":"e7f7e8986dcc8d6a91d25af310d89911","4x3":"8639a78516070c5214ce6e7112cd6690","16x9":"7ea58145199cbae11657ed24007928e0"},"ratings":["{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}","{USA Parental Rating}/{}/{TVPG}","{Canadian Parental Rating}/{}/{PG}","{Film \u0026 Publication Board}/{}/{10-12 PG}"],"ratingAdvisories":null,"stationID":"","genreIDs":null,"sportID":"","sportName":"","tournamentID":"","tournamentName":"","primaryPersonID":"","primaryPersonName":"","primaryPersonPictureID":"","secondaryPersonID":"","secondaryPersonName":"","secondaryPersonPictureID":"","assetIDs":null}]}
```



### 5. Patch live competition


Patches the specified LIVE competition resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the EPG competition to be updated. |

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |  
| isLive |    	| boolean | Required. Live status of this event.  |
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| blackoutRegionIDs | | string list, allows null | |
| metadata |        | object |  |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| sportID |     	| string | ID for the sport associated with this resource. | 
| sportName |   	| string | Name for the sport associated with this resource. | 
| leagueID |        | string | |
| leagueName |      | string | |
| tournamentID |    | string | ID for the tournament associated with this resource.  | 
| tournamentName |  | string | Name for the tournament associated with this resource. | 
| gameID |    		| string | ID for the game associated with this resource. | 
| primaryPersonID |     	| string | ID for the primary or home competitor. | 
| primaryPersonName |   	| string | Name for the primary or home competitor. | 
| primaryPersonPictureID |  | string | ID for picture of the primary or home competitor. | 
| secondaryPersonID | 	  | string | ID for the secondary or away competitor. | 
| secondaryPersonName |     | string | Name for the secondary or away competitor. | 
| secondaryPersonPictureID| | string | ID for picture of the secondary or away competitor. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/competitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "publishStart": "2019-11-11T01:35:50.136Z",
    "startTime": "2019-12-06T01:00:00Z",
    "endTime": "2019-12-06T06:00:00Z",
    "isLive": false,
    "name": "2019 Emirates Australian Open: Day 2",
    "shortName": "2019 Emirates Australian Open: Day 2",
    "description": "2019 Emirates Australian Open: Day 2",
    "shortDescription": "2019 Emirates Australian Open: Day 2",
    "pictures": {
        "16x9": "0566e7e5-9193-48a5-9687-d1a72914a53d.jpg",
        "2x3": "",
        "3x4": "",
        "4x3": ""
    },
    "regionIDs": [
        "7bb71990-1e8d-11e9-900e-9d49235d5db0"
    ],
    "blackoutRegionIDs": null,
    "sportID": "73108786-afed-4578-b696-13f4fd007592",
    "sportName": "Golf",
    "leagueID": "53650746-a157-4fe2-8d2c-b80888280116"
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "2baf54b2-51b9-40ae-a5ff-2fb2798f3797",
    "timestamp": "2020-03-25T18:30:58.281548Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "live/competitions": [
        {
            "id": "ba506fcd-a508-4d8a-9bbc-c66d1428c4b4",
            "resourceType": "live/competitions",
            "publishStart": "2019-11-11T01:35:50.136Z",
            "published": true,
            "created": "2019-11-11T01:35:50.136Z",
            "updated": "2020-03-25T18:30:58.279Z",
            "linkIDs": [
                "bdba885c-6527-45c2-a17e-6781fb75a240"
            ],
            "contentLock": false,
            "startTime": "2019-12-06T01:00:00Z",
            "endTime": "2019-12-06T06:00:00Z",
            "isLive": false,
            "name": "2019 Emirates Australian Open: Day 2",
            "shortName": "2019 Emirates Australian Open: Day 2",
            "description": "2019 Emirates Australian Open: Day 2",
            "shortDescription": "2019 Emirates Australian Open: Day 2",
            "venue": "",
            "language": "en",
            "pictureID": "",
            "pictures": {
                "16x9": "0566e7e5-9193-48a5-9687-d1a72914a53d.jpg",
                "2x3": "",
                "3x4": "",
                "4x3": ""
            },
            "ratings": null,
            "ratingAdvisories": null,
            "genreIDs": null,
            "genres": null,
            "assetIDs": [
                "23518c30-5954-43bf-b6ba-3009393f1fcd"
            ],
            "regionIDs": [
                "7bb71990-1e8d-11e9-900e-9d49235d5db0"
            ],
            "blackoutRegionIDs": null,
            "blackout": false,
            "metadata": {
                "source": "",
                "id": ""
            },
            "sportID": "73108786-afed-4578-b696-13f4fd007592",
            "sportName": "Golf",
            "leagueID": "53650746-a157-4fe2-8d2c-b80888280116",
            "leagueName": "",
            "tournamentID": "",
            "tournamentName": "",
            "gameID": "",
            "primaryPersonID": "",
            "primaryPersonName": "",
            "primaryPersonPictureID": "",
            "secondaryPersonID": "",
            "secondaryPersonName": "",
            "secondaryPersonPictureID": ""
        }
    ]
}
```



## v2/live/events



### 1. Retrieve live event


Get a live event (an event that is not scheduled on a channel or available as a VOD).

**Note: This API is available only for the new non-SportsRocket CMS.**


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/live/events/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * |  |



***Responses:***


Status: Retrieve scheduled event from the EPG | Code: 200



```js
{
	"requestID":"64d24e22-dd41-43ff-927a-a77877618e7c",
	"timestamp":"2018-05-15T04:19:41.681333576Z",
	"metadata":{
		"count":1,
		"totalCount":1,
		"offset":0
	},
	"epg/events":[
		{
			"id":"2210abb74120596b216deb44d369bdee",
			"resourceType":"epg/events",
			"startTime":"2018-04-10T00:51:00Z",
			"endTime":"2018-04-10T01:03:00Z",
			"duration":0,
			"name":"",
			"shortName":"",
			"description":"",
			"shortDescription":"",
			"language":"",
			"pictureID":"",
			"pictures":null,
			"ratings":null,
			"ratingAdvisories":null,
			"stationID":"",
			"genreIDs":null,
			"assetIDs":null,
			"publishStart": "2019-01-01T15:00:00Z",
			"publishEnd": "2020-09-01T07:00:00Z",
			"published": true
		}
	]
}
```



### 2. Create live event


Create a live event (an event that is not scheduled on a channel or available as a VOD).

**Note: This API is available only for the new non-SportsRocket CMS.**


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/events
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
    "resourceType": "live/events",
    "startTime": "2018-12-03T00:30:00Z",
    "endTime": "2018-12-03T01:00:00Z",
    "isLive": false,
    "name": "Más Que Noticias",
    "shortName": "Más Que",
    "description": "Noticiero de Costa Rica que cada día indaga mediante reportajes a personalidades y empresas únicas, con historias extraordinarias e inolvidables.",
    "shortDescription": "asdf",
    "venue": "",
    "language": "es",
    "pictureID": "asdf",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [],
    "ratingAdvisories": [],
    "genreIDs": [
        "7af3784f6a86d74a1d5e29bb2e7887c3"
    ],
    "genres": [
        {
            "id": "7af3784f6a86d74a1d5e29bb2e7887c3",
            "name": "Noticias"
        }
    ],
    "assetIDs": [],
    "regionIDs": null
}
```



***Responses:***


Status: Retrieve scheduled event from the EPG | Code: 200



```js
{"requestID":"64d24e22-dd41-43ff-927a-a77877618e7c","timestamp":"2018-05-15T04:19:41.681333576Z","metadata":{"count":1,"totalCount":1,"offset":0},"epg/events":[{"id":"2210abb74120596b216deb44d369bdee","resourceType":"epg/events","startTime":"2018-04-10T00:51:00Z","endTime":"2018-04-10T01:03:00Z","duration":0,"name":"","shortName":"","description":"","shortDescription":"","language":"","pictureID":"","pictures":null,"ratings":null,"ratingAdvisories":null,"stationID":"","genreIDs":null,"assetIDs":null}]}
```



### 3. Update live event


Update a live event (an event that is not scheduled on a channel or available as a VOD).

**Note: This API is available only for the new non-SportsRocket CMS.**


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/events/{{id}}
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
	"id": "{{id}}",
    "resourceType": "live/events",
    "startTime": "2018-04-26T00:30:00Z",
    "endTime": "2018-04-26T01:00:00Z",
    "isLive": false,
    "name": "Más Que Noticias",
    "shortName": "Más Que",
    "description": "Noticiero de Costa Rica que cada día indaga mediante reportajes a personalidades y empresas únicas, con historias extraordinarias e inolvidables.",
    "shortDescription": "asdf",
    "venue": "",
    "language": "es",
    "pictureID": "asdf",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": [],
    "ratingAdvisories": [],
    "genreIDs": [
        "7af3784f6a86d74a1d5e29bb2e7887c3"
    ],
    "genres": [
        {
            "id": "7af3784f6a86d74a1d5e29bb2e7887c3",
            "name": "Noticias"
        }
    ],
    "assetIDs": [],
    "regionIDs": null
}
```



***Responses:***


Status: Retrieve scheduled event from the EPG | Code: 200



```js
{"requestID":"64d24e22-dd41-43ff-927a-a77877618e7c","timestamp":"2018-05-15T04:19:41.681333576Z","metadata":{"count":1,"totalCount":1,"offset":0},"epg/events":[{"id":"2210abb74120596b216deb44d369bdee","resourceType":"epg/events","startTime":"2018-04-10T00:51:00Z","endTime":"2018-04-10T01:03:00Z","duration":0,"name":"","shortName":"","description":"","shortDescription":"","language":"","pictureID":"","pictures":null,"ratings":null,"ratingAdvisories":null,"stationID":"","genreIDs":null,"assetIDs":null}]}
```



### 4. Delete live event


Removes a live event (an event that is not scheduled on a channel or available as a VOD) from the CMS.

**Note: This API is available only for the new non-SportsRocket CMS.**

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|ID	|string	|required	|ID for the live event. |

<br>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified live event.|
|404		|1040	|*Not Found*: No matching live event ID found.|

<br>

<!--
<br/>
#### Response object
The Notes column describes default and possible values, valid ranges, and fields that are nullable ( ø ), or required ( ʀ ). All fields are optional unless otherwise indicated.

<br>

| Name  | Parent |  Type  | Description | Notes
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |
-->


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/live/events/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Retrieve scheduled game from the EPG | Code: 200



```js
{
    "requestID": "3615a4c8-5eef-48c3-817f-7c51b0996629",
    "timestamp": "2018-05-15T04:22:29.721400028Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/competitions": [
        {
            "id": "4ec20201a14219cd9331c456c5418a94",
            "resourceType": "epg/competitions",
            "startTime": "2018-04-27T10:46:00Z",
            "endTime": "2018-04-27T11:40:00Z",
            "duration": 0,
            "name": "Batallas con Marlines",
            "shortName": "Batallas con Marlines",
            "description": "Cyril está en Costa Rica por una razón importante. La búsqueda del pez más grande y poderoso del océano (450 kg), el pez espada.",
            "shortDescription": "La búsqueda del pez espada.",
            "language": "es",
            "pictureID": "7ea58145199cbae11657ed24007928e0",
            "pictures": {
                "2x3": "04aaa1f2a9a7b2c38e95104494b81cdf",
                "3x4": "e7f7e8986dcc8d6a91d25af310d89911",
                "4x3": "8639a78516070c5214ce6e7112cd6690",
                "16x9": "7ea58145199cbae11657ed24007928e0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Film & Publication Board}/{}/{10-12 PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "sportID": "",
            "sportName": "",
            "tournamentID": "",
            "tournamentName": "",
            "primaryPersonID": "",
            "primaryPersonName": "",
            "primaryPersonPictureID": "",
            "secondaryPersonID": "",
            "secondaryPersonName": "",
            "secondaryPersonPictureID": "",
            "assetIDs": null
        }
    ]
}
```



### 5. Patch live event


Patches the specified LIVE event resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID of the EPG event to be updated. | 

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |  
| isLive |    	| boolean | Required. Live status of this event.  |
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| blackoutRegionIDs | | string list, allows null | |
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/events/{{id}}
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
    "publishEnd": "2019-11-25T20:27:53.74Z",
    "contentLock": false,
    "startTime": "2019-11-01T17:55:00Z",
    "endTime": "2019-11-01T20:30:00Z",
    "isLive": false,
    "name": "BLAST Pro Series 2019: Copenhagen - Day 1",
    "shortName": "BLAST Pro Series 2019: Copenhagen - Day 1",
    "description": "BLAST Pro Series 2019: Copenhagen - Day 1",
    "shortDescription": "BLAST Pro Series 2019: Copenhagen - Day 1",
    "pictures": {
        "16x9": "cf766173-cb42-48a0-b70d-69e02ffc11bf.jpg",
        "2x3": "",
        "3x4": "",
        "4x3": ""
    },
    "ratings": null,
    "ratingAdvisories": null,
    "regionIDs": [
        "7bb71990-1e8d-11e9-900e-9d49235d5db0",
        "2efc0320-d5dc-11e9-867e-59779c8353a0"
    ],
    "blackoutRegionIDs": null
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "feed7e3b-cbef-4141-bef6-d1a67d9b1ddb",
    "timestamp": "2020-03-25T18:21:50.90681Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "live/events": [
        {
            "id": "f0a77593-2258-4e92-b482-854ec9260239",
            "resourceType": "live/events",
            "publishEnd": "2019-11-25T20:27:53.74Z",
            "published": false,
            "created": "2019-10-16T20:44:23.174Z",
            "updated": "2020-03-25T18:21:50.903Z",
            "linkIDs": [
                "fe3945cf-975f-43dc-a294-e09b7ef040cc"
            ],
            "contentLock": false,
            "startTime": "2019-11-01T17:55:00Z",
            "endTime": "2019-11-01T20:30:00Z",
            "isLive": false,
            "name": "BLAST Pro Series 2019: Copenhagen - Day 1",
            "shortName": "BLAST Pro Series 2019: Copenhagen - Day 1",
            "description": "BLAST Pro Series 2019: Copenhagen - Day 1",
            "shortDescription": "BLAST Pro Series 2019: Copenhagen - Day 1",
            "venue": "",
            "language": "en",
            "pictureID": "",
            "pictures": {
                "16x9": "cf766173-cb42-48a0-b70d-69e02ffc11bf.jpg",
                "2x3": "",
                "3x4": "",
                "4x3": ""
            },
            "ratings": null,
            "ratingAdvisories": null,
            "genreIDs": null,
            "genres": null,
            "assetIDs": [
                "724174b2-fdae-441b-b8b3-c37fbb6a83dc"
            ],
            "regionIDs": [
                "7bb71990-1e8d-11e9-900e-9d49235d5db0",
                "2efc0320-d5dc-11e9-867e-59779c8353a0"
            ],
            "blackoutRegionIDs": null,
            "blackout": false,
            "metadata": {
                "source": "",
                "id": ""
            }
        }
    ]
}
```



## v2/live/teamCompetitions



### 1. Create live team competition


Creates an EPG entry for a live team game (a game that is not scheduled on a channel or available as a VOD).

**Note: This API is available only for the new non-SportsRocket CMS.**

<br/>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Name  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| resourceType |    | enum string | Required. Contains the value "live/teamCompetitions". | 
| startTime |   	| string | Required. Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. Ending time in ISO-8601 timestamp format.  |  
| isLive |  		| boolean | Required. Live status of this event.  |  
| name |    		| string | Required. Full name. . . |
| shortName |   	| string | Shortened name. . . |
| description |     | string | Full description. . .|
| shortDescription| | string | Shortened description. . .|
| venue	|    		| string | Name of the location where the event takes place.  |  
| language |    	| string | Required. Two-letter code for the spoken language.  |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this live team competition. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  
| ratings |     	| string list | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| genreIDs |    	| string list | List of genre IDs associated with this live team competition. | 
| assetIDs |    	| string list | List of asset IDs associated with this live team competition. |
| sportID |     	| string | ID for the sport associated with this live team competition. | 
| sportName |   	| string | Name for the sport associated with this live team competition. | 
| leagueID |    | string | ID for the league associated with this live team competition.  | 
| leagueName |  | string | Name for the league associated with this live team competition. | 
| gameID |    		| string | ID for the game associated with this live team competition. | 
| tournamentID |    | string | ID for the tournament associated with this live team competition.  | 
| tournamentName |  | string | Name for the tournament associated with this live team competition. | 
| primaryTeamID |     	| string | ID for the primary or home team. | 
| primaryTeamName |   	| string | Name for the primary or home team. | 
| primaryTeamPictureID |  | string | ID for picture of the primary or home team. | 
| secondaryTeamID | 	  | string | ID for the secondary or away team. | 
| secondaryTeamName |     | string | Name for the secondary or away team. | 
| secondaryTeamPictureID| | string | ID for picture of the secondary or away team. | 

<br/>

<!--

NOTE: The following fields are currently NOT included in this endpoint: 	
		genres, regionIDs, stationID, duration

We should also include the maximum character lengths for the name, shortName, description and shortDescription fields.

-->


<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/teamCompetitions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "live/teamCompetitions",
    "startTime": "2018-04-28T02:00:00Z",
    "endTime": "2018-04-28T05:00:00Z",
    "isLive": false,
    "name": "New York Yankees en Los Angeles Angels",
    "shortName": "New York Yankees en Los Angeles Angels",
    "description": "Los Angels reciben a los Yankees en una serie de 3 juegos. Los Angeles derrotaron a New York en 4 de los 6 juegos el año pasado. Esa fue la primera serie anual en la que los Angels derrotan a los Yankees desde 2008.",
    "shortDescription": "Yankees enfrentan a Angels en California.",
    "venue": "",
    "language": "es",
    "pictureID": "",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": null,
    "ratingAdvisories": null,
    "genreIDs": null,
    "assetIDs": null,
    "sportID": "",
    "sportName": "",
    "leagueID": "",
    "leagueName": "",
    "gameID": "1234",
    "tournamentID": "",
    "tournamentName": "",
    "primaryTeamID": "",
    "primaryTeamName": "",
    "primaryTeamPictureID": "",
    "secondaryTeamID": "",
    "secondaryTeamName": "",
    "secondaryTeamPictureID": ""
}
```



### 2. Update live team competition


Updates the EPG entry for a live team competition (a game that is not scheduled on a channel or available as a VOD).

**Note: This API is available only for the new non-SportsRocket CMS.**

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID for the target live team competition. |

<br/>


##### Body Parameters
All fields are optional unless otherwise indicated.

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| id	|    		| string | ID associated with this live team competition. | 
| resourceType |    | enum string | Required. Contains the value "live/teamCompetitions". | 
| startTime |   	| string | Required. Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. Ending time in ISO-8601 timestamp format.  |  
| isLive |  		| boolean | Required. Live status of this event.  |  
| name |    		| string | Required. Full name. . . |
| shortName |   	| string | Shortened name. . . |
| description |     | string | Full description. . .|
| shortDescription| | string | Shortened description. . .|
| venue	|    		| string | Name of the location where the event takes place.  |  
| language |    	| string | Required. Two-letter code for the spoken language.  |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this live team competition. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  
| ratings |     	| string list | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| genreIDs |    	| string list | List of genre IDs associated with this live team competition. | 
| assetIDs |    	| string list | List of asset IDs associated with this live team competition. |
| sportID |     	| string | ID for the sport associated with this live team competition. | 
| sportName |   	| string | Name for the sport associated with this live team competition. | 
| leagueID |    | string | ID for the league associated with this live team competition.  | 
| leagueName |  | string | Name for the league associated with this live team competition. | 
| gameID |    		| string | ID for the game associated with this live team competition. | 
| tournamentID |    | string | ID for the tournament associated with this live team competition.  | 
| tournamentName |  | string | Name for the tournament associated with this live team competition. | 
| primaryTeamID |     	| string | ID for the primary or home team. | 
| primaryTeamName |   	| string | Name for the primary or home team. | 
| primaryTeamPictureID |  | string | ID for picture of the primary or home team. | 
| secondaryTeamID | 	  | string | ID for the secondary or away team. | 
| secondaryTeamName |     | string | Name for the secondary or away team. | 
| secondaryTeamPictureID| | string | ID for picture of the secondary or away team. | 

<br/>

<!--

NOTE: The following fields are currently NOT included in this endpoint: 	
		genres, regionIDs, stationID, duration

We should also include the maximum character lengths for the name, shortName, description and shortDescription fields.

-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
	"id": "{{id}}",
    "resourceType": "live/teamCompetitions",
    "startTime": "2018-04-28T02:00:00Z",
    "endTime": "2018-04-28T05:00:00Z",
    "isLive": false,
    "name": "New York Yankees en Los Angeles Angels",
    "shortName": "New York Yankees en Los Angeles Angels",
    "description": "Los Angels reciben a los Yankees en una serie de 3 juegos. Los Angeles derrotaron a New York en 4 de los 6 juegos el año pasado. Esa fue la primera serie anual en la que los Angels derrotan a los Yankees desde 2008.",
    "shortDescription": "Yankees enfrentan a Angels en California.",
    "venue": "",
    "language": "es",
    "pictureID": "",
    "pictures": {
        "2x3": null,
        "3x4": null,
        "4x3": null,
        "16x9": null
    },
    "ratings": null,
    "ratingAdvisories": null,
    "genreIDs": null,
    "assetIDs": null,
    "sportID": "",
    "sportName": "",
    "leagueID": "",
    "leagueName": "",
    "gameID": "1234",
    "tournamentID": "",
    "tournamentName": "",
    "primaryTeamID": "",
    "primaryTeamName": "",
    "primaryTeamPictureID": "",
    "secondaryTeamID": "",
    "secondaryTeamName": "",
    "secondaryTeamPictureID": ""
}
```



### 3. Retrieve live team competition


Retrieves the specified live team game (a game that is not scheduled on a channel or available as a VOD).

<br>

**Note: This API is available only for the new non-SportsRocket CMS.**

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID for the target live team competition game. |

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested live team game|
|404		|1040				|*Not Found*: No matching live team competition found|

<br/>


<!--

#### Response object
The Notes column describes default and possible values, valid ranges, and fields that are nullable ( ø ), or required ( ʀ ). All fields are optional unless otherwise indicated.


| Name  | Parent |  Type  | Description | Notes
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   | 
||||||
| `metadata` |   |    |    |   |  
| count | metadata |number  | Current screen.  | min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  | min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. | min=1, max = 20
||||||
| *`live/teamCompetitions`* |   |   |      |  |
| id | live/teamCompetitions |string | Unique ID for each asset.  |  |
| resourceType | live/teamCompetitions | enum string | "epg/teamCompetitions" | |
| startTime | live/teamCompetitions | string | A timestamp.  |  |
| endTime | live/teamCompetitions | string | A timestamp.  |  |
| duration | live/teamCompetitions | number | Video duration in minutes.  |  |
| name | live/teamCompetitions | string | Full name.  | (max char length?) |
| shortName | live/teamCompetitions | string |   | (max char length?) |
| description | live/teamCompetitions | string | Full description.  | (max char length?) |
| shortDescription | live/teamCompetitions | string |   | (max char length?) |
| venue | live/teamCompetitions | string |   | (max char length?) |
| language | live/teamCompetitions | string | Two-letter code for the spoken language.  |  |
| ratings | live/teamCompetitions | string | Age-related ratings from boards and agencies. | ø  |
| ratingAdvisories | epg/teamCompetitions | string list | A list of content advisories.  | ø, Such as "Adult Situations", "Language", or "Violence" |
| genreIDs | live/teamCompetitions | string | | ø; |
| sportID | live/teamCompetitions | string | | |
| sportName | live/teamCompetitions | string | | |
| leagueID | live/teamCompetitions | string | | |
| leagueName | live/teamCompetitions | string | | |
| tournamentID | live/teamCompetitions | string | | |
| tournamentName | live/teamCompetitions | string | | |
| primaryTeamID | live/teamCompetitions | string | | |
| primaryTeamName | live/teamCompetitions | string | | |
| primaryTeamPictureID | live/teamCompetitions | string | | |
| secondaryTeamID | live/teamCompetitions | string | | |
| secondaryTeamName | live/teamCompetitions | string | | |
| secondaryTeamPictureID | live/teamCompetitions | string | | |
| assetIDs | live/teamCompetitions | string | | ø; |
| pictureID | live/teamCompetitions | string | ID for the standard image |  | 
||||||
| *`pictures`* | live/teamCompetitions |  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. |  | 
| 3x4  | pictures | string | ID for a 3x4 image.  |  | 
| 4x3  | pictures | string | ID for a 4x3 image.  |  | 
| 16x9 | pictures | string | ID for a 16x9 image.  |  | 

-->

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/live/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Retrieve scheduled team game from the EPG | Code: 200



```js
{"requestID":"2d563a76-22c4-4e44-94d3-80e99ab9aca6","timestamp":"2018-05-15T04:22:55.847098738Z","metadata":{"count":1,"totalCount":1,"offset":0},"epg/teamCompetitions":[{"id":"38cdd1fdbb061ff71f9fe3607c1e633f","resourceType":"epg/teamCompetitions","startTime":"2018-04-28T02:00:00Z","endTime":"2018-04-28T05:00:00Z","duration":0,"name":"New York Yankees en Los Angeles Angels","shortName":"New York Yankees en Los Angeles Angels","description":"Los Angels reciben a los Yankees en una serie de 3 juegos. Los Angeles derrotaron a New York en 4 de los 6 juegos el año pasado. Esa fue la primera serie anual en la que los Angels derrotan a los Yankees desde 2008.","shortDescription":"Yankees enfrentan a Angels en California.","language":"es","pictureID":"","pictures":{"2x3":null,"3x4":null,"4x3":null,"16x9":null},"ratings":null,"ratingAdvisories":null,"stationID":"","genreIDs":null,"assetIDs":null,"sportID":"","sportName":"","tournamentID":"","tournamentName":"","primaryTeamID":"","primaryTeamName":"","primaryTeamPictureID":"","secondaryTeamID":"","secondaryTeamName":"","secondaryTeamPictureID":""}]}
```



### 4. Delete live team competition


Removes a live team competition (a game that is not scheduled on a channel or available as a VOD) from the CMS.

**Note: This API is available only for the new non-SportsRocket CMS.**

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|ID			|string		|required	|ID for the target live team competition game. |

<br>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified live team game.|
|404		|1040	|*Not Found*: No matching live team game ID found.|

<br>

<!--

#### Response object
The Notes column describes default and possible values, valid ranges, and fields that are nullable ( ø ), or required ( ʀ ). All fields are optional unless otherwise indicated.

<br>

| Name  | Parent |  Type  | Description | Notes
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |

<br>
-->


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/live/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Retrieve scheduled game from the EPG | Code: 200



```js
{
    "requestID": "3615a4c8-5eef-48c3-817f-7c51b0996629",
    "timestamp": "2018-05-15T04:22:29.721400028Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "epg/competitions": [
        {
            "id": "4ec20201a14219cd9331c456c5418a94",
            "resourceType": "epg/competitions",
            "startTime": "2018-04-27T10:46:00Z",
            "endTime": "2018-04-27T11:40:00Z",
            "duration": 0,
            "name": "Batallas con Marlines",
            "shortName": "Batallas con Marlines",
            "description": "Cyril está en Costa Rica por una razón importante. La búsqueda del pez más grande y poderoso del océano (450 kg), el pez espada.",
            "shortDescription": "La búsqueda del pez espada.",
            "language": "es",
            "pictureID": "7ea58145199cbae11657ed24007928e0",
            "pictures": {
                "2x3": "04aaa1f2a9a7b2c38e95104494b81cdf",
                "3x4": "e7f7e8986dcc8d6a91d25af310d89911",
                "4x3": "8639a78516070c5214ce6e7112cd6690",
                "16x9": "7ea58145199cbae11657ed24007928e0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Film & Publication Board}/{}/{10-12 PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "sportID": "",
            "sportName": "",
            "tournamentID": "",
            "tournamentName": "",
            "primaryPersonID": "",
            "primaryPersonName": "",
            "primaryPersonPictureID": "",
            "secondaryPersonID": "",
            "secondaryPersonName": "",
            "secondaryPersonPictureID": "",
            "assetIDs": null
        }
    ]
}
```



### 5. Patch live team competition


Patches the specified LIVE team competition resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID of the EPG team competition to be updated. | 

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |  
| isLive |    	| boolean | Required. Live status of this event.  |
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| blackoutRegionIDs | | string list, allows null | |
| metadata |        | object |  |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| sportID |     	| string | ID for the sport associated with this resource. | 
| sportName |   	| string | Name for the sport associated with this resource. | 
| leagueID |        | string | |
| leagueName |      | string | |
| tournamentID |    | string | ID for the tournament associated with this resource.  | 
| tournamentName |  | string | Name for the tournament associated with this resource. | 
| gameID |    		| string | ID for the game associated with this resource. | 
| primaryTeamID |     	| string | ID for the primary or home team. | 
| primaryTeamName |   	| string | Name for the primary or home team. | 
| primaryTeamPictureID |  | string | ID for picture of the primary or home team. | 
| secondaryTeamID | 	  | string | ID for the secondary or away team. | 
| secondaryTeamName |     | string | Name for the secondary or away team. | 
| secondaryTeamPictureID| | string | ID for picture of the secondary or away team. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/live/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "publishStart": "2019-02-01T15:00:00Z",
    "startTime": "2020-04-26T18:50:00Z",
    "endTime": "2020-04-26T21:00:00Z",
    "isLive": false,
    "name": " MW 35: Aston Villa v Crystal Palace",
    "shortName": " MW 35: Aston Villa v Crystal Palace",
    "description": "MW 35: Aston Villa v Crystal Palace",
    "shortDescription": " MW 35: Aston Villa v Crystal Palace",
    "venue": "Villa Park",
    "language": "en",
    "pictures": {
        "16x9": "52ba81f6-1e49-4bd7-bd81-79e0c49c2017.jpg",
        "2x3": "",
        "3x4": "",
        "4x3": "67766715-1d7d-45a0-a1e8-f44c81dda7a2.jpg"
    },
    "metadata": {
        "source": "gracenote",
        "id": "GNEG4TE4R3BEHN5"
    },
    "sportID": "ace5ede6-622b-4511-b1cb-7470f2d80bde",
    "sportName": "Soccer",
    "leagueID": "839b05d7-c99c-4059-9414-0288473f2b90",
    "gameID": "53aa4221-5c09-4a7b-a194-896178c02d15",
    "primaryTeamID": "e292490d-6c3e-41b5-baeb-42a8e06d9cee",
    "primaryTeamName": "Aston Villa",
    "primaryTeamPictureID": "2d0ca51a-63ae-42f2-8f5b-d579d12776d0.png",
    "secondaryTeamID": "5d666e1c-9c0f-4598-ac7b-8062ee327aa1",
    "secondaryTeamName": "Crystal Palace",
    "secondaryTeamPictureID": "152f3a41-9aeb-4456-b339-54aa9a926131.png"
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "56da7b9f-e482-4429-bbbf-91abe4739bdf",
    "timestamp": "2020-03-25T18:33:39.492711Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "live/teamCompetitions": [
        {
            "id": "7d750fba-f18a-499b-a7a1-ce622362bfb8",
            "resourceType": "live/teamCompetitions",
            "publishStart": "2019-02-01T15:00:00Z",
            "published": true,
            "created": "0001-01-01T00:00:00Z",
            "updated": "2020-03-25T18:33:39.489Z",
            "linkIDs": [
                "6bb08f41-14d1-441f-b179-f6693b0db398"
            ],
            "contentLock": false,
            "startTime": "2020-04-26T18:50:00Z",
            "endTime": "2020-04-26T21:00:00Z",
            "isLive": false,
            "name": " MW 35: Aston Villa v Crystal Palace",
            "shortName": " MW 35: Aston Villa v Crystal Palace",
            "description": "MW 35: Aston Villa v Crystal Palace",
            "shortDescription": " MW 35: Aston Villa v Crystal Palace",
            "venue": "Villa Park",
            "language": "en",
            "pictureID": "",
            "pictures": {
                "16x9": "52ba81f6-1e49-4bd7-bd81-79e0c49c2017.jpg",
                "2x3": "",
                "3x4": "",
                "4x3": "67766715-1d7d-45a0-a1e8-f44c81dda7a2.jpg"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "genreIDs": null,
            "genres": null,
            "assetIDs": [
                "8ad410c6-6e22-4e1e-9fc4-1de23783e55d"
            ],
            "regionIDs": null,
            "blackoutRegionIDs": null,
            "blackout": false,
            "metadata": {
                "source": "gracenote",
                "id": "GNEG4TE4R3BEHN5"
            },
            "sportID": "ace5ede6-622b-4511-b1cb-7470f2d80bde",
            "sportName": "Soccer",
            "leagueID": "839b05d7-c99c-4059-9414-0288473f2b90",
            "leagueName": "",
            "tournamentID": "",
            "tournamentName": "",
            "gameID": "53aa4221-5c09-4a7b-a194-896178c02d15",
            "primaryTeamID": "e292490d-6c3e-41b5-baeb-42a8e06d9cee",
            "primaryTeamName": "Aston Villa",
            "primaryTeamPictureID": "2d0ca51a-63ae-42f2-8f5b-d579d12776d0.png",
            "secondaryTeamID": "5d666e1c-9c0f-4598-ac7b-8062ee327aa1",
            "secondaryTeamName": "Crystal Palace",
            "secondaryTeamPictureID": "152f3a41-9aeb-4456-b339-54aa9a926131.png"
        }
    ]
}
```



## v2/pages



### 1. Retrieve page


Retrieves the specified carousel page. Each page contains a set of sections. Each section has a set of blocks.<br>

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---			|
|pageid	|string	|required	|ID of the page created in Contentwise.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/pages/{{pageid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Geo-Position | 39.109;-76.778 | Global position specified as {_longitude;latitude_}. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| region | Defaults |  |



### 2. Create/Update page


Creates or updates a page to fill the referenced UI. Each page contains a set of sections. Each section has a set of blocks.<br>
<!--
![Alt text](./PageAPIStub.png)
-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/pages/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
    "pageID": "TestPage",
    "sections": [
        "TestSectionOne",
        "TestSectionTwo"
    ]
}
```



### 3. Delete page


Deletes a page (and its sections and blocks) in the referenced UI. 

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|pageID	|string		|required	|ID for the referenced page. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified page.|
|404		|1040	|*Not Found*: No matching page ID found.|

<br/>
<!--
![Alt text](./PageAPIStub.png)
-->


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/pages/config/TestPage
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 4. Retrieve a section of a page


Retrieves the specified section of a carousel page to fill the referenced UI. Each section may be built by one or more blocks.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---			|
|pageid	|string	|required	|ID of the page created in Contentwise.|
|sectionid	|string	|required	|ID of the section to be retrieved.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/pages/{{pageid}}/sections/{{sectionid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Geo-Position | 39.109;-76.778 | Global position specified as {_longitude;latitude_}. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| region | Default | Indicates the desired region for the page.  The *Default* page is used if none is specified. |



### 5. Create/Update page section


Creates or updates a section of a page to fill the referenced UI. Each section may be built by one or more blocks.
<br>
<!--
![Alt text](./SectionAPIStub.png)
-->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/pages/TestPage/sections/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
    "sectionID": "TestSectionOne",
    "assetIDs": [
        "AssetIDOne",
        "AssetIDTwo"
    ]
}
```



### 6. Delete page section


Deletes a section of a page in the referenced UI. 

<br>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|pageSectionID	|string		|required	|ID for the referenced page section. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified page section.|
|404		|1040	|*Not Found*: No matching page section ID found.|

<br/>
<!--
![Alt text](./SectionAPIStub.png)
-->


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v2/pages/TestPage/sections/config/TestSectionOne
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



## v2/publishing



### 1. Publish a resource


Publishes a resource by specifying the date range during which it is available.

<br/>

**NOTE:** This API is available only for the new non-SportsRocket CMS.

<br/>

##### Path Parameters

|Field|Data type|Required|Description
|---|---|---|---|
|id|string|required|Specifies the video resource to be published|

<br/>

##### Body Parameters

|Field|Data type|Required|Description
|---|---|---|---|
|publishStart|string|required|Date when the content becomes available; in ISO-8601 timestamp format.|
|publishEnd|string|required|Date when the content is no longer available; in ISO-8601 timestamp format.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/publish/{{id}}
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
	"publishStart": "2019-01-01T15:00:00Z",
	"publishEnd": "2020-09-01T07:00:00Z"
}
```



### 2. Unpublish a resource


Unpublishes the specified video resource, making it immediately unavailable to users.

<br/>

**NOTE:** This API is available only for the new non-SportsRocket CMS.

<br/>

##### Path Parameters

|Field|Data type|Required|Description
|---|---|---|---|
|id|string|required|Specifies the video resource to be unpublished|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/unpublish/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### 3. Apply draft to resource


Applies any draft changes to the specified resource. This action updates the resource and makes the changes visible to users.

Until applied, any edits to a resource are saved as a draft that is not generally visible to users. 

<br/>

**Notes:** 
* This operation is applicable only to resources that already have a saved draft.
* This API is available only for the new non-SportsRocket CMS.

<br/>

##### Path Parameters

|Field|Data type|Required|Description
|---|---|---|---|
|id|string|required|Specifies the video resource to be published|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/publish/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



## v2/schedule



### 1. List scheduled content


Returns a list of scheduled content as specified by the query parameters.  The events are grouped by stationID and sorted by startTime in ascending order.

<br/>

All query parameters are optional unless otherwise indicated.

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested scheduled content|

<!-- |404		|1040				|*Not Found*: No matching scheduled content found|  -->

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/schedule
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| stationIDs | cd650491a210b9b17e1e53527c012e0b | Comma separated list of station IDs. |
| startTime.gte | 2019-03-18T00:00:00Z | Time range start. Select scheduled events that start _at or after_ the specified timestamp (in ISO-8601 format). |
| startTime.lte | 2019-03-27T00:00:00Z | Time range end. Select scheduled events that start _at or before_ the specified timestamp (in ISO-8601 format). |
| language | * | Code for the requested language. Use * as a wildcard for all languages. Default value is "en" for English. |
| count | 100 | Maximum number of results to return. Used for pagination. Default value is 10. |
| offset | 5 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |



***Responses:***


Status: Returns a list of scheduled content | Code: 200



```js
{
    "requestID": "741787f6-601a-4ac8-9893-1f0ee6e745fb",
    "timestamp": "2018-05-15T04:16:13.847853347Z",
    "metadata": {
        "count": 20,
        "totalCount": 2318,
        "offset": 20
    },
    "schedule": [
        {
            "id": "a1b7c37a468f4a7b57b57dbef74e6ebc",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T15:00:00Z",
            "endTime": "2018-04-26T16:00:00Z",
            "duration": 0,
            "name": "Made in Chelsea",
            "shortName": "Chelsea",
            "description": "Jamie invita a Spencer a un viaje a una estación de esquí europea, el problema es que Lucy se suma al grupo. Ahora, Spencer deberá elegir entre hacer feliz a Lauren o recuperar una vieja amistad.",
            "shortDescription": "Spencer viaja a una estación de esquí.",
            "language": "es",
            "pictureID": "3052eec4f835249b86b882e88a441413",
            "pictures": {
                "2x3": "b2be814050bca03d92005b474f6f66fb",
                "3x4": "a36ad46a120457f0b7d03e005509e8ec",
                "4x3": "a165bcd497f1c51d9dfe79610a35d791",
                "16x9": "3052eec4f835249b86b882e88a441413"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
                "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed for all ages}/{S}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "a5dc797cc2ee3f30cd8b5eb46c521bc4",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T16:00:00Z",
            "endTime": "2018-04-26T17:00:00Z",
            "duration": 0,
            "name": "Kiss bang love",
            "shortName": "Kiss bang",
            "description": "Programa que muestra que el amor está a un solo beso de distancia. Un grupo de chicas, con los ojos vendados, besa a otro grupo de chicos que también lleva los ojos vendados y decidirá quiénes pasarán a la siguiente etapa para continuar con la cita.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": {
                "2x3": null,
                "3x4": null,
                "4x3": null,
                "16x9": null
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "1d7d0714c66b4b1b2caf4ae6aa1888b5",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T17:00:00Z",
            "endTime": "2018-04-26T18:00:00Z",
            "duration": 0,
            "name": "Amor a bordo",
            "shortName": "Amor",
            "description": "El conductor será el chofer del \"taxi del amor\" que recorrerá las calles de la Gran Manzana.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "43b245a48092e62d023c0f27faa4c7af",
            "pictures": {
                "2x3": "77ec68043397f403f8f8f9cae47a3aa1",
                "3x4": "645473fe3a5503f9c9c2026dd6e0dd20",
                "4x3": "25d2b363ae0af36e383bea71dff6de43",
                "16x9": "43b245a48092e62d023c0f27faa4c7af"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "122183ecbdb049318cb982dce27a7404",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T18:00:00Z",
            "endTime": "2018-04-26T19:00:00Z",
            "duration": 0,
            "name": "Amor a bordo",
            "shortName": "Amor",
            "description": "El conductor será el chofer del \"taxi del amor\" que recorrerá las calles de la Gran Manzana.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "9d6aecc174ea4c3abf72beeaab8a85ac",
            "pictures": {
                "2x3": "c27e57271787bd2b1425647fa50bd00c",
                "3x4": "b1d6bb1e4850e2b0f3745937acd9c067",
                "4x3": "93d1590382613841e0caa1934c723927",
                "16x9": "9d6aecc174ea4c3abf72beeaab8a85ac"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "71b42134fb20151e8486e81fb68d41b9",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T19:00:00Z",
            "endTime": "2018-04-26T20:00:00Z",
            "duration": 0,
            "name": "WAGS LA",
            "shortName": "WAGS LA",
            "description": "Tia aprende una lección; Natalie y Olivia reciben una invitación para convertirse en embajadoras de una marca; Larry revela sus intenciones con Nicole; las audiciones de Barbie.",
            "shortDescription": "Tia aprende una lección.",
            "language": "es",
            "pictureID": "4b539883e97d3b43f649765be880a32c",
            "pictures": {
                "2x3": "c8c7773007e6450e1118a59f49cee12f",
                "3x4": "667d49793a4160c841811a29f311972b",
                "4x3": "6ee9333d2d7533bfc4c8646f8b4ed7ab",
                "16x9": "4b539883e97d3b43f649765be880a32c"
            },
            "ratings": [
                "{Canadian Parental Rating}/{}/{14+}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "7eea2346671b4c95b25811ff94bc9ab4",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T20:00:00Z",
            "endTime": "2018-04-26T21:00:00Z",
            "duration": 0,
            "name": "Cámbiame el Look",
            "shortName": "Cámbiame",
            "description": "Una mujer buscando una nueva vida en Hollywood necesita deshacerse de su estilo psychobilly.",
            "shortDescription": "Mujer se aferra a su estilo psychobilly.",
            "language": "es",
            "pictureID": "648cdb9fd38f2c7a0583d0749772a6a0",
            "pictures": {
                "2x3": "35484eb912306cbcb770cd2da2274532",
                "3x4": "8344184913d14e6fed70e2866042b1e2",
                "4x3": "0afb2da8bd6ae5f2ac2b17639b220d07",
                "16x9": "648cdb9fd38f2c7a0583d0749772a6a0"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "28a86867ec29a3f6c876038b4bfd67e7",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T21:00:00Z",
            "endTime": "2018-04-26T22:00:00Z",
            "duration": 0,
            "name": "Project Runway",
            "shortName": "Runway",
            "description": "Los diseñadores deben crear nuevos aspectos para mujeres que acaban de obtener nuevos peinados.",
            "shortDescription": "Diseñadores deben crear nuevos aspectos.",
            "language": "es",
            "pictureID": "775d4db6e27eec77f5777c4520563065",
            "pictures": {
                "2x3": "fdce3b681fb0cd0f01e9e419215fa81d",
                "3x4": "e101f875caea7eee893c2959a9e0e649",
                "4x3": "13759907318168ddc8960e0690178d14",
                "16x9": "775d4db6e27eec77f5777c4520563065"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Australian Classification Board}/{Mature}/{M}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "ceade7640f371d2d5f73ee2d0a452a5c",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T22:00:00Z",
            "endTime": "2018-04-26T23:00:00Z",
            "duration": 0,
            "name": "Project Runway",
            "shortName": "Runway",
            "description": "Los diseñadores tienen la oportunidad de presentar su ropa en una colección especial en las tiendas Lord & Taylor.",
            "shortDescription": "Colección especial de Lord & Taylor.",
            "language": "es",
            "pictureID": "2c7c4a4a83a4d9ff281dbe6152e90127",
            "pictures": {
                "2x3": "2a4b36f6a69c38a3e5ef3f90018b55b6",
                "3x4": "946ba0a22e0590a501fe4adca79dbd68",
                "4x3": "064754dfe65fdfb8a2dc6f713225df4a",
                "16x9": "2c7c4a4a83a4d9ff281dbe6152e90127"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Régie du cinéma}/{General}/{G}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Australian Classification Board}/{Mature}/{M}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "122957fa065bb418df19de1e3341dd52",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T23:00:00Z",
            "endTime": "2018-04-27T00:00:00Z",
            "duration": 0,
            "name": "Guerra de Pieles",
            "shortName": "Guer",
            "description": "Los tres artistas de cuerpos restantes trabajan con contorsionistas, creando hermosas y elaboradas ilusiones multi-cuerpo.",
            "shortDescription": "Artistas trabajan con contorsionistas.",
            "language": "es",
            "pictureID": "fdf09ee5cf2cde5063d4877870a1eba9",
            "pictures": {
                "2x3": "6c16b50f43a1999ffa0548ff91936901",
                "3x4": "a800a9b618e53784d4f3b1420b75f775",
                "4x3": "f686634dffa36adc03c7c628223126a9",
                "16x9": "fdf09ee5cf2cde5063d4877870a1eba9"
            },
            "ratings": [
                "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
                "{Australian Classification Board}/{Mature}/{M}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "48472675838ea08fb264b646ea0d3ee9",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T00:00:00Z",
            "endTime": "2018-04-27T01:00:00Z",
            "duration": 0,
            "name": "Keeping Up With the Kardashians",
            "shortName": "Kardashian",
            "description": "Las chicas comienzan a hacer las paces con la nueva relación de Rob, pero bromas en los medios sociales conducen a herir sentimientos; Kris y Kim llegan a sus puntos de ruptura; Kendall se siente excluida.",
            "shortDescription": "Bromas de Rob lastiman a las chicas.",
            "language": "es",
            "pictureID": "9d5432971829dd2af9fccd3717840da0",
            "pictures": {
                "2x3": "a487f97a475a0d2406e515f608d98fd9",
                "3x4": "098ea51641786b3490d397c520b5c61d",
                "4x3": "667d31e3f28cbf5ccac294c9a876b4a7",
                "16x9": "9d5432971829dd2af9fccd3717840da0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{16 anos}/{16}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Régie du cinéma}/{8 Years and Over}/{8+}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "378a4162135314c0573a959fb00d975c",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T01:00:00Z",
            "endTime": "2018-04-27T02:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El Dr. Dubrow trabaja con una madre que pasó 12 años pareciendo estar embarazada; el Dr. Nassif ayuda a una mujer incapaz de cerrar su boca desde la universidad; los médicos se reúnen con un jugador con un caso de senos masculinos.",
            "shortDescription": "Un jugador con caso de senos masculinos.",
            "language": "es",
            "pictureID": "09b46e7f1f1779a05475d887cf5c0f88",
            "pictures": {
                "2x3": "e1b939d4d1cbe85b326925fa94625950",
                "3x4": "29658b6d68b69f5c1a82cdfad2b5f1f7",
                "4x3": "26b06ed3594c2ced6b8dfe02345bf3d6",
                "16x9": "09b46e7f1f1779a05475d887cf5c0f88"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "3e3b7ff2cde29efe4721f58dff6bae85",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T02:00:00Z",
            "endTime": "2018-04-27T03:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El doctor Nassif asiste a una paciente libanesa que quiere operarse la nariz antes del día de su boda. El doctor Dubrow trata a una mujer cuya cirugía de pechos resultó defectuosa. Mama June, de \"Honey Boo Boo\", necesita ayuda.",
            "shortDescription": "Una nariz nueva.",
            "language": "es",
            "pictureID": "3334426d6b45c7037d24f661115dadb1",
            "pictures": {
                "2x3": "70d690917b248cc69eff60e177718b0e",
                "3x4": "5a66f579612757b249a48ab0a1984e2b",
                "4x3": "72c1767f42ad6810131aa2cde647984d",
                "16x9": "3334426d6b45c7037d24f661115dadb1"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "5084b8820bba27f2aa41e1d71f43f027",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T03:00:00Z",
            "endTime": "2018-04-27T04:00:00Z",
            "duration": 0,
            "name": "Cuídate de la Cámara, 9",
            "shortName": "Cuídate, 9",
            "description": "",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "6c1ee7af4f5fa7160f9f15a5789bf5ef",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T04:00:00Z",
            "endTime": "2018-04-27T05:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "Una madre no tiene más remedio que ponerse cinta de embalar sobre los pechos. Una joven enfermera necesita ayuda con su nariz. Una celebridad de segunda fila quiere que le dejen una nariz de estrella de cine.",
            "shortDescription": "Se pone cinta en los pechos.",
            "language": "es",
            "pictureID": "ac76c24b00ae95d23bd2819240fae2ed",
            "pictures": {
                "2x3": "5ad89ce4a86e98695a9bb16c0c34317b",
                "3x4": "20b2c650911f1cc1a0d544384acd3c85",
                "4x3": "cbbc32c77b06408a5fe8a1b1fadb08fa",
                "16x9": "ac76c24b00ae95d23bd2819240fae2ed"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "1eab2fbe99fff0056fd601492dbd54c2",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T05:00:00Z",
            "endTime": "2018-04-27T06:00:00Z",
            "duration": 0,
            "name": "E! News Live",
            "shortName": "E News",
            "description": "Resumen de las noticias más importantes.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "d5c40c0ed60cd33736b9b206b79f6913",
            "pictures": {
                "2x3": "c2b20fa00ea274ec2c846d1b08d929aa",
                "3x4": "e8b15fda76f9ad23044c28619b93d90a",
                "4x3": "d5282684baf70629d0ab0d1e620389a1",
                "16x9": "d5c40c0ed60cd33736b9b206b79f6913"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "5e7e225eeec4b1bb2760c6773d4477f1",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T06:00:00Z",
            "endTime": "2018-04-27T07:00:00Z",
            "duration": 0,
            "name": "Cámbiame el Look, 2",
            "shortName": "Cámbiame, 2",
            "description": "",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "e7d7a71816711af595fb52d47ad7cbed",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T07:00:00Z",
            "endTime": "2018-04-27T08:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El Dr. Dubrow trabaja con una madre que pasó 12 años pareciendo estar embarazada; el Dr. Nassif ayuda a una mujer incapaz de cerrar su boca desde la universidad; los médicos se reúnen con un jugador con un caso de senos masculinos.",
            "shortDescription": "Un jugador con caso de senos masculinos.",
            "language": "es",
            "pictureID": "09b46e7f1f1779a05475d887cf5c0f88",
            "pictures": {
                "2x3": "e1b939d4d1cbe85b326925fa94625950",
                "3x4": "29658b6d68b69f5c1a82cdfad2b5f1f7",
                "4x3": "26b06ed3594c2ced6b8dfe02345bf3d6",
                "16x9": "09b46e7f1f1779a05475d887cf5c0f88"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "ef8171e59614fad259d0608319b0ff54",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T08:00:00Z",
            "endTime": "2018-04-27T09:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El doctor Nassif asiste a una paciente libanesa que quiere operarse la nariz antes del día de su boda. El doctor Dubrow trata a una mujer cuya cirugía de pechos resultó defectuosa. Mama June, de \"Honey Boo Boo\", necesita ayuda.",
            "shortDescription": "Una nariz nueva.",
            "language": "es",
            "pictureID": "3334426d6b45c7037d24f661115dadb1",
            "pictures": {
                "2x3": "70d690917b248cc69eff60e177718b0e",
                "3x4": "5a66f579612757b249a48ab0a1984e2b",
                "4x3": "72c1767f42ad6810131aa2cde647984d",
                "16x9": "3334426d6b45c7037d24f661115dadb1"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "7e5b8cdacdec2dbb2783fd1f577de908",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T09:00:00Z",
            "endTime": "2018-04-27T10:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "Una madre no tiene más remedio que ponerse cinta de embalar sobre los pechos. Una joven enfermera necesita ayuda con su nariz. Una celebridad de segunda fila quiere que le dejen una nariz de estrella de cine.",
            "shortDescription": "Se pone cinta en los pechos.",
            "language": "es",
            "pictureID": "ac76c24b00ae95d23bd2819240fae2ed",
            "pictures": {
                "2x3": "5ad89ce4a86e98695a9bb16c0c34317b",
                "3x4": "20b2c650911f1cc1a0d544384acd3c85",
                "4x3": "cbbc32c77b06408a5fe8a1b1fadb08fa",
                "16x9": "ac76c24b00ae95d23bd2819240fae2ed"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "4627ec4a2bc315199a558a3b53523894",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T10:00:00Z",
            "endTime": "2018-04-27T11:00:00Z",
            "duration": 0,
            "name": "Keeping Up With the Kardashians",
            "shortName": "Kardashian",
            "description": "Las chicas comienzan a hacer las paces con la nueva relación de Rob, pero bromas en los medios sociales conducen a herir sentimientos; Kris y Kim llegan a sus puntos de ruptura; Kendall se siente excluida.",
            "shortDescription": "Bromas de Rob lastiman a las chicas.",
            "language": "es",
            "pictureID": "9d5432971829dd2af9fccd3717840da0",
            "pictures": {
                "2x3": "a487f97a475a0d2406e515f608d98fd9",
                "3x4": "098ea51641786b3490d397c520b5c61d",
                "4x3": "667d31e3f28cbf5ccac294c9a876b4a7",
                "16x9": "9d5432971829dd2af9fccd3717840da0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{16 anos}/{16}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Régie du cinéma}/{8 Years and Over}/{8+}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        }
    ]
}
```



### 2. Black out programs


Excludes targeted regions from viewing the specified EPG programs.
 
<br/>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Field  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| programIDs |  |string array | Unique ID for each program to be blacked out. Required. |
| blackoutRegionIDs |  | string array | Unique ID for each region where the programs will be blacked out. Required. |

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/schedule/blackout
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
    "programIDs": [
        "epg-episodeID",
        "epg-movieID",
        "epg-competitionID",
        "epg-teamcompetitionID",
        "epg-eventID"
    ],
    "blackoutRegionIDs": [
        "regionID1",
        "regionID2",
        "regionID3"
    ]
}
```



***Responses:***


Status: Create EPG episode | Code: 200



### 3. Audit scheduled content


Returns a list of all missing scheduled content. The results are grouped by station and sorted by station name in ascending order.

<br/>

<!--	Is this accurate? I don't see any path or query parameters for this endpoint. 
		How do we know the content is "missing"?  Are these items that are scheduled but unpublished?

All query parameters are optional unless otherwise indicated.

-->

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested scheduled content|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/schedule/audit
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Returns a list of scheduled content | Code: 200



```js
{
    "requestID": "741787f6-601a-4ac8-9893-1f0ee6e745fb",
    "timestamp": "2018-05-15T04:16:13.847853347Z",
    "metadata": {
        "count": 20,
        "totalCount": 2318,
        "offset": 20
    },
    "schedule": [
        {
            "id": "a1b7c37a468f4a7b57b57dbef74e6ebc",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T15:00:00Z",
            "endTime": "2018-04-26T16:00:00Z",
            "duration": 0,
            "name": "Made in Chelsea",
            "shortName": "Chelsea",
            "description": "Jamie invita a Spencer a un viaje a una estación de esquí europea, el problema es que Lucy se suma al grupo. Ahora, Spencer deberá elegir entre hacer feliz a Lauren o recuperar una vieja amistad.",
            "shortDescription": "Spencer viaja a una estación de esquí.",
            "language": "es",
            "pictureID": "3052eec4f835249b86b882e88a441413",
            "pictures": {
                "2x3": "b2be814050bca03d92005b474f6f66fb",
                "3x4": "a36ad46a120457f0b7d03e005509e8ec",
                "4x3": "a165bcd497f1c51d9dfe79610a35d791",
                "16x9": "3052eec4f835249b86b882e88a441413"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
                "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed for all ages}/{S}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "a5dc797cc2ee3f30cd8b5eb46c521bc4",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T16:00:00Z",
            "endTime": "2018-04-26T17:00:00Z",
            "duration": 0,
            "name": "Kiss bang love",
            "shortName": "Kiss bang",
            "description": "Programa que muestra que el amor está a un solo beso de distancia. Un grupo de chicas, con los ojos vendados, besa a otro grupo de chicos que también lleva los ojos vendados y decidirá quiénes pasarán a la siguiente etapa para continuar con la cita.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": {
                "2x3": null,
                "3x4": null,
                "4x3": null,
                "16x9": null
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "1d7d0714c66b4b1b2caf4ae6aa1888b5",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T17:00:00Z",
            "endTime": "2018-04-26T18:00:00Z",
            "duration": 0,
            "name": "Amor a bordo",
            "shortName": "Amor",
            "description": "El conductor será el chofer del \"taxi del amor\" que recorrerá las calles de la Gran Manzana.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "43b245a48092e62d023c0f27faa4c7af",
            "pictures": {
                "2x3": "77ec68043397f403f8f8f9cae47a3aa1",
                "3x4": "645473fe3a5503f9c9c2026dd6e0dd20",
                "4x3": "25d2b363ae0af36e383bea71dff6de43",
                "16x9": "43b245a48092e62d023c0f27faa4c7af"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "122183ecbdb049318cb982dce27a7404",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T18:00:00Z",
            "endTime": "2018-04-26T19:00:00Z",
            "duration": 0,
            "name": "Amor a bordo",
            "shortName": "Amor",
            "description": "El conductor será el chofer del \"taxi del amor\" que recorrerá las calles de la Gran Manzana.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "9d6aecc174ea4c3abf72beeaab8a85ac",
            "pictures": {
                "2x3": "c27e57271787bd2b1425647fa50bd00c",
                "3x4": "b1d6bb1e4850e2b0f3745937acd9c067",
                "4x3": "93d1590382613841e0caa1934c723927",
                "16x9": "9d6aecc174ea4c3abf72beeaab8a85ac"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "71b42134fb20151e8486e81fb68d41b9",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T19:00:00Z",
            "endTime": "2018-04-26T20:00:00Z",
            "duration": 0,
            "name": "WAGS LA",
            "shortName": "WAGS LA",
            "description": "Tia aprende una lección; Natalie y Olivia reciben una invitación para convertirse en embajadoras de una marca; Larry revela sus intenciones con Nicole; las audiciones de Barbie.",
            "shortDescription": "Tia aprende una lección.",
            "language": "es",
            "pictureID": "4b539883e97d3b43f649765be880a32c",
            "pictures": {
                "2x3": "c8c7773007e6450e1118a59f49cee12f",
                "3x4": "667d49793a4160c841811a29f311972b",
                "4x3": "6ee9333d2d7533bfc4c8646f8b4ed7ab",
                "16x9": "4b539883e97d3b43f649765be880a32c"
            },
            "ratings": [
                "{Canadian Parental Rating}/{}/{14+}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "7eea2346671b4c95b25811ff94bc9ab4",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T20:00:00Z",
            "endTime": "2018-04-26T21:00:00Z",
            "duration": 0,
            "name": "Cámbiame el Look",
            "shortName": "Cámbiame",
            "description": "Una mujer buscando una nueva vida en Hollywood necesita deshacerse de su estilo psychobilly.",
            "shortDescription": "Mujer se aferra a su estilo psychobilly.",
            "language": "es",
            "pictureID": "648cdb9fd38f2c7a0583d0749772a6a0",
            "pictures": {
                "2x3": "35484eb912306cbcb770cd2da2274532",
                "3x4": "8344184913d14e6fed70e2866042b1e2",
                "4x3": "0afb2da8bd6ae5f2ac2b17639b220d07",
                "16x9": "648cdb9fd38f2c7a0583d0749772a6a0"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "28a86867ec29a3f6c876038b4bfd67e7",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T21:00:00Z",
            "endTime": "2018-04-26T22:00:00Z",
            "duration": 0,
            "name": "Project Runway",
            "shortName": "Runway",
            "description": "Los diseñadores deben crear nuevos aspectos para mujeres que acaban de obtener nuevos peinados.",
            "shortDescription": "Diseñadores deben crear nuevos aspectos.",
            "language": "es",
            "pictureID": "775d4db6e27eec77f5777c4520563065",
            "pictures": {
                "2x3": "fdce3b681fb0cd0f01e9e419215fa81d",
                "3x4": "e101f875caea7eee893c2959a9e0e649",
                "4x3": "13759907318168ddc8960e0690178d14",
                "16x9": "775d4db6e27eec77f5777c4520563065"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Australian Classification Board}/{Mature}/{M}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "ceade7640f371d2d5f73ee2d0a452a5c",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T22:00:00Z",
            "endTime": "2018-04-26T23:00:00Z",
            "duration": 0,
            "name": "Project Runway",
            "shortName": "Runway",
            "description": "Los diseñadores tienen la oportunidad de presentar su ropa en una colección especial en las tiendas Lord & Taylor.",
            "shortDescription": "Colección especial de Lord & Taylor.",
            "language": "es",
            "pictureID": "2c7c4a4a83a4d9ff281dbe6152e90127",
            "pictures": {
                "2x3": "2a4b36f6a69c38a3e5ef3f90018b55b6",
                "3x4": "946ba0a22e0590a501fe4adca79dbd68",
                "4x3": "064754dfe65fdfb8a2dc6f713225df4a",
                "16x9": "2c7c4a4a83a4d9ff281dbe6152e90127"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Régie du cinéma}/{General}/{G}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Australian Classification Board}/{Mature}/{M}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "122957fa065bb418df19de1e3341dd52",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T23:00:00Z",
            "endTime": "2018-04-27T00:00:00Z",
            "duration": 0,
            "name": "Guerra de Pieles",
            "shortName": "Guer",
            "description": "Los tres artistas de cuerpos restantes trabajan con contorsionistas, creando hermosas y elaboradas ilusiones multi-cuerpo.",
            "shortDescription": "Artistas trabajan con contorsionistas.",
            "language": "es",
            "pictureID": "fdf09ee5cf2cde5063d4877870a1eba9",
            "pictures": {
                "2x3": "6c16b50f43a1999ffa0548ff91936901",
                "3x4": "a800a9b618e53784d4f3b1420b75f775",
                "4x3": "f686634dffa36adc03c7c628223126a9",
                "16x9": "fdf09ee5cf2cde5063d4877870a1eba9"
            },
            "ratings": [
                "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
                "{Australian Classification Board}/{Mature}/{M}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "48472675838ea08fb264b646ea0d3ee9",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T00:00:00Z",
            "endTime": "2018-04-27T01:00:00Z",
            "duration": 0,
            "name": "Keeping Up With the Kardashians",
            "shortName": "Kardashian",
            "description": "Las chicas comienzan a hacer las paces con la nueva relación de Rob, pero bromas en los medios sociales conducen a herir sentimientos; Kris y Kim llegan a sus puntos de ruptura; Kendall se siente excluida.",
            "shortDescription": "Bromas de Rob lastiman a las chicas.",
            "language": "es",
            "pictureID": "9d5432971829dd2af9fccd3717840da0",
            "pictures": {
                "2x3": "a487f97a475a0d2406e515f608d98fd9",
                "3x4": "098ea51641786b3490d397c520b5c61d",
                "4x3": "667d31e3f28cbf5ccac294c9a876b4a7",
                "16x9": "9d5432971829dd2af9fccd3717840da0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{16 anos}/{16}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Régie du cinéma}/{8 Years and Over}/{8+}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "378a4162135314c0573a959fb00d975c",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T01:00:00Z",
            "endTime": "2018-04-27T02:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El Dr. Dubrow trabaja con una madre que pasó 12 años pareciendo estar embarazada; el Dr. Nassif ayuda a una mujer incapaz de cerrar su boca desde la universidad; los médicos se reúnen con un jugador con un caso de senos masculinos.",
            "shortDescription": "Un jugador con caso de senos masculinos.",
            "language": "es",
            "pictureID": "09b46e7f1f1779a05475d887cf5c0f88",
            "pictures": {
                "2x3": "e1b939d4d1cbe85b326925fa94625950",
                "3x4": "29658b6d68b69f5c1a82cdfad2b5f1f7",
                "4x3": "26b06ed3594c2ced6b8dfe02345bf3d6",
                "16x9": "09b46e7f1f1779a05475d887cf5c0f88"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "3e3b7ff2cde29efe4721f58dff6bae85",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T02:00:00Z",
            "endTime": "2018-04-27T03:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El doctor Nassif asiste a una paciente libanesa que quiere operarse la nariz antes del día de su boda. El doctor Dubrow trata a una mujer cuya cirugía de pechos resultó defectuosa. Mama June, de \"Honey Boo Boo\", necesita ayuda.",
            "shortDescription": "Una nariz nueva.",
            "language": "es",
            "pictureID": "3334426d6b45c7037d24f661115dadb1",
            "pictures": {
                "2x3": "70d690917b248cc69eff60e177718b0e",
                "3x4": "5a66f579612757b249a48ab0a1984e2b",
                "4x3": "72c1767f42ad6810131aa2cde647984d",
                "16x9": "3334426d6b45c7037d24f661115dadb1"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "5084b8820bba27f2aa41e1d71f43f027",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T03:00:00Z",
            "endTime": "2018-04-27T04:00:00Z",
            "duration": 0,
            "name": "Cuídate de la Cámara, 9",
            "shortName": "Cuídate, 9",
            "description": "",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "6c1ee7af4f5fa7160f9f15a5789bf5ef",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T04:00:00Z",
            "endTime": "2018-04-27T05:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "Una madre no tiene más remedio que ponerse cinta de embalar sobre los pechos. Una joven enfermera necesita ayuda con su nariz. Una celebridad de segunda fila quiere que le dejen una nariz de estrella de cine.",
            "shortDescription": "Se pone cinta en los pechos.",
            "language": "es",
            "pictureID": "ac76c24b00ae95d23bd2819240fae2ed",
            "pictures": {
                "2x3": "5ad89ce4a86e98695a9bb16c0c34317b",
                "3x4": "20b2c650911f1cc1a0d544384acd3c85",
                "4x3": "cbbc32c77b06408a5fe8a1b1fadb08fa",
                "16x9": "ac76c24b00ae95d23bd2819240fae2ed"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "1eab2fbe99fff0056fd601492dbd54c2",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T05:00:00Z",
            "endTime": "2018-04-27T06:00:00Z",
            "duration": 0,
            "name": "E! News Live",
            "shortName": "E News",
            "description": "Resumen de las noticias más importantes.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "d5c40c0ed60cd33736b9b206b79f6913",
            "pictures": {
                "2x3": "c2b20fa00ea274ec2c846d1b08d929aa",
                "3x4": "e8b15fda76f9ad23044c28619b93d90a",
                "4x3": "d5282684baf70629d0ab0d1e620389a1",
                "16x9": "d5c40c0ed60cd33736b9b206b79f6913"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "5e7e225eeec4b1bb2760c6773d4477f1",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T06:00:00Z",
            "endTime": "2018-04-27T07:00:00Z",
            "duration": 0,
            "name": "Cámbiame el Look, 2",
            "shortName": "Cámbiame, 2",
            "description": "",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "e7d7a71816711af595fb52d47ad7cbed",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T07:00:00Z",
            "endTime": "2018-04-27T08:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El Dr. Dubrow trabaja con una madre que pasó 12 años pareciendo estar embarazada; el Dr. Nassif ayuda a una mujer incapaz de cerrar su boca desde la universidad; los médicos se reúnen con un jugador con un caso de senos masculinos.",
            "shortDescription": "Un jugador con caso de senos masculinos.",
            "language": "es",
            "pictureID": "09b46e7f1f1779a05475d887cf5c0f88",
            "pictures": {
                "2x3": "e1b939d4d1cbe85b326925fa94625950",
                "3x4": "29658b6d68b69f5c1a82cdfad2b5f1f7",
                "4x3": "26b06ed3594c2ced6b8dfe02345bf3d6",
                "16x9": "09b46e7f1f1779a05475d887cf5c0f88"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "ef8171e59614fad259d0608319b0ff54",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T08:00:00Z",
            "endTime": "2018-04-27T09:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El doctor Nassif asiste a una paciente libanesa que quiere operarse la nariz antes del día de su boda. El doctor Dubrow trata a una mujer cuya cirugía de pechos resultó defectuosa. Mama June, de \"Honey Boo Boo\", necesita ayuda.",
            "shortDescription": "Una nariz nueva.",
            "language": "es",
            "pictureID": "3334426d6b45c7037d24f661115dadb1",
            "pictures": {
                "2x3": "70d690917b248cc69eff60e177718b0e",
                "3x4": "5a66f579612757b249a48ab0a1984e2b",
                "4x3": "72c1767f42ad6810131aa2cde647984d",
                "16x9": "3334426d6b45c7037d24f661115dadb1"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "7e5b8cdacdec2dbb2783fd1f577de908",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T09:00:00Z",
            "endTime": "2018-04-27T10:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "Una madre no tiene más remedio que ponerse cinta de embalar sobre los pechos. Una joven enfermera necesita ayuda con su nariz. Una celebridad de segunda fila quiere que le dejen una nariz de estrella de cine.",
            "shortDescription": "Se pone cinta en los pechos.",
            "language": "es",
            "pictureID": "ac76c24b00ae95d23bd2819240fae2ed",
            "pictures": {
                "2x3": "5ad89ce4a86e98695a9bb16c0c34317b",
                "3x4": "20b2c650911f1cc1a0d544384acd3c85",
                "4x3": "cbbc32c77b06408a5fe8a1b1fadb08fa",
                "16x9": "ac76c24b00ae95d23bd2819240fae2ed"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "4627ec4a2bc315199a558a3b53523894",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T10:00:00Z",
            "endTime": "2018-04-27T11:00:00Z",
            "duration": 0,
            "name": "Keeping Up With the Kardashians",
            "shortName": "Kardashian",
            "description": "Las chicas comienzan a hacer las paces con la nueva relación de Rob, pero bromas en los medios sociales conducen a herir sentimientos; Kris y Kim llegan a sus puntos de ruptura; Kendall se siente excluida.",
            "shortDescription": "Bromas de Rob lastiman a las chicas.",
            "language": "es",
            "pictureID": "9d5432971829dd2af9fccd3717840da0",
            "pictures": {
                "2x3": "a487f97a475a0d2406e515f608d98fd9",
                "3x4": "098ea51641786b3490d397c520b5c61d",
                "4x3": "667d31e3f28cbf5ccac294c9a876b4a7",
                "16x9": "9d5432971829dd2af9fccd3717840da0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{16 anos}/{16}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Régie du cinéma}/{8 Years and Over}/{8+}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        }
    ]
}
```



### 4. Audit scheduled content for one station


Returns a list of missing scheduled content for the specified station.

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|stationID	|string		|required	|ID for the targeted station. |


<!-- All query parameters are optional unless otherwise indicated. -->

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station|
|404		|1040				|*Not Found*: No matching station ID found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/schedule/audit/{{stationID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Returns a list of scheduled content | Code: 200



```js
{
    "requestID": "741787f6-601a-4ac8-9893-1f0ee6e745fb",
    "timestamp": "2018-05-15T04:16:13.847853347Z",
    "metadata": {
        "count": 20,
        "totalCount": 2318,
        "offset": 20
    },
    "schedule": [
        {
            "id": "a1b7c37a468f4a7b57b57dbef74e6ebc",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T15:00:00Z",
            "endTime": "2018-04-26T16:00:00Z",
            "duration": 0,
            "name": "Made in Chelsea",
            "shortName": "Chelsea",
            "description": "Jamie invita a Spencer a un viaje a una estación de esquí europea, el problema es que Lucy se suma al grupo. Ahora, Spencer deberá elegir entre hacer feliz a Lauren o recuperar una vieja amistad.",
            "shortDescription": "Spencer viaja a una estación de esquí.",
            "language": "es",
            "pictureID": "3052eec4f835249b86b882e88a441413",
            "pictures": {
                "2x3": "b2be814050bca03d92005b474f6f66fb",
                "3x4": "a36ad46a120457f0b7d03e005509e8ec",
                "4x3": "a165bcd497f1c51d9dfe79610a35d791",
                "16x9": "3052eec4f835249b86b882e88a441413"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
                "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed for all ages}/{S}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "a5dc797cc2ee3f30cd8b5eb46c521bc4",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T16:00:00Z",
            "endTime": "2018-04-26T17:00:00Z",
            "duration": 0,
            "name": "Kiss bang love",
            "shortName": "Kiss bang",
            "description": "Programa que muestra que el amor está a un solo beso de distancia. Un grupo de chicas, con los ojos vendados, besa a otro grupo de chicos que también lleva los ojos vendados y decidirá quiénes pasarán a la siguiente etapa para continuar con la cita.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": {
                "2x3": null,
                "3x4": null,
                "4x3": null,
                "16x9": null
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "1d7d0714c66b4b1b2caf4ae6aa1888b5",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T17:00:00Z",
            "endTime": "2018-04-26T18:00:00Z",
            "duration": 0,
            "name": "Amor a bordo",
            "shortName": "Amor",
            "description": "El conductor será el chofer del \"taxi del amor\" que recorrerá las calles de la Gran Manzana.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "43b245a48092e62d023c0f27faa4c7af",
            "pictures": {
                "2x3": "77ec68043397f403f8f8f9cae47a3aa1",
                "3x4": "645473fe3a5503f9c9c2026dd6e0dd20",
                "4x3": "25d2b363ae0af36e383bea71dff6de43",
                "16x9": "43b245a48092e62d023c0f27faa4c7af"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "122183ecbdb049318cb982dce27a7404",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T18:00:00Z",
            "endTime": "2018-04-26T19:00:00Z",
            "duration": 0,
            "name": "Amor a bordo",
            "shortName": "Amor",
            "description": "El conductor será el chofer del \"taxi del amor\" que recorrerá las calles de la Gran Manzana.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "9d6aecc174ea4c3abf72beeaab8a85ac",
            "pictures": {
                "2x3": "c27e57271787bd2b1425647fa50bd00c",
                "3x4": "b1d6bb1e4850e2b0f3745937acd9c067",
                "4x3": "93d1590382613841e0caa1934c723927",
                "16x9": "9d6aecc174ea4c3abf72beeaab8a85ac"
            },
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "71b42134fb20151e8486e81fb68d41b9",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T19:00:00Z",
            "endTime": "2018-04-26T20:00:00Z",
            "duration": 0,
            "name": "WAGS LA",
            "shortName": "WAGS LA",
            "description": "Tia aprende una lección; Natalie y Olivia reciben una invitación para convertirse en embajadoras de una marca; Larry revela sus intenciones con Nicole; las audiciones de Barbie.",
            "shortDescription": "Tia aprende una lección.",
            "language": "es",
            "pictureID": "4b539883e97d3b43f649765be880a32c",
            "pictures": {
                "2x3": "c8c7773007e6450e1118a59f49cee12f",
                "3x4": "667d49793a4160c841811a29f311972b",
                "4x3": "6ee9333d2d7533bfc4c8646f8b4ed7ab",
                "16x9": "4b539883e97d3b43f649765be880a32c"
            },
            "ratings": [
                "{Canadian Parental Rating}/{}/{14+}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "7eea2346671b4c95b25811ff94bc9ab4",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T20:00:00Z",
            "endTime": "2018-04-26T21:00:00Z",
            "duration": 0,
            "name": "Cámbiame el Look",
            "shortName": "Cámbiame",
            "description": "Una mujer buscando una nueva vida en Hollywood necesita deshacerse de su estilo psychobilly.",
            "shortDescription": "Mujer se aferra a su estilo psychobilly.",
            "language": "es",
            "pictureID": "648cdb9fd38f2c7a0583d0749772a6a0",
            "pictures": {
                "2x3": "35484eb912306cbcb770cd2da2274532",
                "3x4": "8344184913d14e6fed70e2866042b1e2",
                "4x3": "0afb2da8bd6ae5f2ac2b17639b220d07",
                "16x9": "648cdb9fd38f2c7a0583d0749772a6a0"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "28a86867ec29a3f6c876038b4bfd67e7",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T21:00:00Z",
            "endTime": "2018-04-26T22:00:00Z",
            "duration": 0,
            "name": "Project Runway",
            "shortName": "Runway",
            "description": "Los diseñadores deben crear nuevos aspectos para mujeres que acaban de obtener nuevos peinados.",
            "shortDescription": "Diseñadores deben crear nuevos aspectos.",
            "language": "es",
            "pictureID": "775d4db6e27eec77f5777c4520563065",
            "pictures": {
                "2x3": "fdce3b681fb0cd0f01e9e419215fa81d",
                "3x4": "e101f875caea7eee893c2959a9e0e649",
                "4x3": "13759907318168ddc8960e0690178d14",
                "16x9": "775d4db6e27eec77f5777c4520563065"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Australian Classification Board}/{Mature}/{M}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "ceade7640f371d2d5f73ee2d0a452a5c",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T22:00:00Z",
            "endTime": "2018-04-26T23:00:00Z",
            "duration": 0,
            "name": "Project Runway",
            "shortName": "Runway",
            "description": "Los diseñadores tienen la oportunidad de presentar su ropa en una colección especial en las tiendas Lord & Taylor.",
            "shortDescription": "Colección especial de Lord & Taylor.",
            "language": "es",
            "pictureID": "2c7c4a4a83a4d9ff281dbe6152e90127",
            "pictures": {
                "2x3": "2a4b36f6a69c38a3e5ef3f90018b55b6",
                "3x4": "946ba0a22e0590a501fe4adca79dbd68",
                "4x3": "064754dfe65fdfb8a2dc6f713225df4a",
                "16x9": "2c7c4a4a83a4d9ff281dbe6152e90127"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TVPG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Régie du cinéma}/{General}/{G}",
                "{Canadian Parental Rating}/{}/{PG}",
                "{Australian Classification Board}/{Mature}/{M}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "122957fa065bb418df19de1e3341dd52",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-26T23:00:00Z",
            "endTime": "2018-04-27T00:00:00Z",
            "duration": 0,
            "name": "Guerra de Pieles",
            "shortName": "Guer",
            "description": "Los tres artistas de cuerpos restantes trabajan con contorsionistas, creando hermosas y elaboradas ilusiones multi-cuerpo.",
            "shortDescription": "Artistas trabajan con contorsionistas.",
            "language": "es",
            "pictureID": "fdf09ee5cf2cde5063d4877870a1eba9",
            "pictures": {
                "2x3": "6c16b50f43a1999ffa0548ff91936901",
                "3x4": "a800a9b618e53784d4f3b1420b75f775",
                "4x3": "f686634dffa36adc03c7c628223126a9",
                "16x9": "fdf09ee5cf2cde5063d4877870a1eba9"
            },
            "ratings": [
                "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
                "{Australian Classification Board}/{Mature}/{M}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "48472675838ea08fb264b646ea0d3ee9",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T00:00:00Z",
            "endTime": "2018-04-27T01:00:00Z",
            "duration": 0,
            "name": "Keeping Up With the Kardashians",
            "shortName": "Kardashian",
            "description": "Las chicas comienzan a hacer las paces con la nueva relación de Rob, pero bromas en los medios sociales conducen a herir sentimientos; Kris y Kim llegan a sus puntos de ruptura; Kendall se siente excluida.",
            "shortDescription": "Bromas de Rob lastiman a las chicas.",
            "language": "es",
            "pictureID": "9d5432971829dd2af9fccd3717840da0",
            "pictures": {
                "2x3": "a487f97a475a0d2406e515f608d98fd9",
                "3x4": "098ea51641786b3490d397c520b5c61d",
                "4x3": "667d31e3f28cbf5ccac294c9a876b4a7",
                "16x9": "9d5432971829dd2af9fccd3717840da0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{16 anos}/{16}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Régie du cinéma}/{8 Years and Over}/{8+}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "378a4162135314c0573a959fb00d975c",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T01:00:00Z",
            "endTime": "2018-04-27T02:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El Dr. Dubrow trabaja con una madre que pasó 12 años pareciendo estar embarazada; el Dr. Nassif ayuda a una mujer incapaz de cerrar su boca desde la universidad; los médicos se reúnen con un jugador con un caso de senos masculinos.",
            "shortDescription": "Un jugador con caso de senos masculinos.",
            "language": "es",
            "pictureID": "09b46e7f1f1779a05475d887cf5c0f88",
            "pictures": {
                "2x3": "e1b939d4d1cbe85b326925fa94625950",
                "3x4": "29658b6d68b69f5c1a82cdfad2b5f1f7",
                "4x3": "26b06ed3594c2ced6b8dfe02345bf3d6",
                "16x9": "09b46e7f1f1779a05475d887cf5c0f88"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "3e3b7ff2cde29efe4721f58dff6bae85",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T02:00:00Z",
            "endTime": "2018-04-27T03:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El doctor Nassif asiste a una paciente libanesa que quiere operarse la nariz antes del día de su boda. El doctor Dubrow trata a una mujer cuya cirugía de pechos resultó defectuosa. Mama June, de \"Honey Boo Boo\", necesita ayuda.",
            "shortDescription": "Una nariz nueva.",
            "language": "es",
            "pictureID": "3334426d6b45c7037d24f661115dadb1",
            "pictures": {
                "2x3": "70d690917b248cc69eff60e177718b0e",
                "3x4": "5a66f579612757b249a48ab0a1984e2b",
                "4x3": "72c1767f42ad6810131aa2cde647984d",
                "16x9": "3334426d6b45c7037d24f661115dadb1"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "5084b8820bba27f2aa41e1d71f43f027",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T03:00:00Z",
            "endTime": "2018-04-27T04:00:00Z",
            "duration": 0,
            "name": "Cuídate de la Cámara, 9",
            "shortName": "Cuídate, 9",
            "description": "",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "6c1ee7af4f5fa7160f9f15a5789bf5ef",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T04:00:00Z",
            "endTime": "2018-04-27T05:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "Una madre no tiene más remedio que ponerse cinta de embalar sobre los pechos. Una joven enfermera necesita ayuda con su nariz. Una celebridad de segunda fila quiere que le dejen una nariz de estrella de cine.",
            "shortDescription": "Se pone cinta en los pechos.",
            "language": "es",
            "pictureID": "ac76c24b00ae95d23bd2819240fae2ed",
            "pictures": {
                "2x3": "5ad89ce4a86e98695a9bb16c0c34317b",
                "3x4": "20b2c650911f1cc1a0d544384acd3c85",
                "4x3": "cbbc32c77b06408a5fe8a1b1fadb08fa",
                "16x9": "ac76c24b00ae95d23bd2819240fae2ed"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "1eab2fbe99fff0056fd601492dbd54c2",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T05:00:00Z",
            "endTime": "2018-04-27T06:00:00Z",
            "duration": 0,
            "name": "E! News Live",
            "shortName": "E News",
            "description": "Resumen de las noticias más importantes.",
            "shortDescription": "",
            "language": "es",
            "pictureID": "d5c40c0ed60cd33736b9b206b79f6913",
            "pictures": {
                "2x3": "c2b20fa00ea274ec2c846d1b08d929aa",
                "3x4": "e8b15fda76f9ad23044c28619b93d90a",
                "4x3": "d5282684baf70629d0ab0d1e620389a1",
                "16x9": "d5c40c0ed60cd33736b9b206b79f6913"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "5e7e225eeec4b1bb2760c6773d4477f1",
            "resourceType": "epg/events",
            "startTime": "2018-04-27T06:00:00Z",
            "endTime": "2018-04-27T07:00:00Z",
            "duration": 0,
            "name": "Cámbiame el Look, 2",
            "shortName": "Cámbiame, 2",
            "description": "",
            "shortDescription": "",
            "language": "es",
            "pictureID": "",
            "pictures": null,
            "ratings": null,
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "e7d7a71816711af595fb52d47ad7cbed",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T07:00:00Z",
            "endTime": "2018-04-27T08:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El Dr. Dubrow trabaja con una madre que pasó 12 años pareciendo estar embarazada; el Dr. Nassif ayuda a una mujer incapaz de cerrar su boca desde la universidad; los médicos se reúnen con un jugador con un caso de senos masculinos.",
            "shortDescription": "Un jugador con caso de senos masculinos.",
            "language": "es",
            "pictureID": "09b46e7f1f1779a05475d887cf5c0f88",
            "pictures": {
                "2x3": "e1b939d4d1cbe85b326925fa94625950",
                "3x4": "29658b6d68b69f5c1a82cdfad2b5f1f7",
                "4x3": "26b06ed3594c2ced6b8dfe02345bf3d6",
                "16x9": "09b46e7f1f1779a05475d887cf5c0f88"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "ef8171e59614fad259d0608319b0ff54",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T08:00:00Z",
            "endTime": "2018-04-27T09:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "El doctor Nassif asiste a una paciente libanesa que quiere operarse la nariz antes del día de su boda. El doctor Dubrow trata a una mujer cuya cirugía de pechos resultó defectuosa. Mama June, de \"Honey Boo Boo\", necesita ayuda.",
            "shortDescription": "Una nariz nueva.",
            "language": "es",
            "pictureID": "3334426d6b45c7037d24f661115dadb1",
            "pictures": {
                "2x3": "70d690917b248cc69eff60e177718b0e",
                "3x4": "5a66f579612757b249a48ab0a1984e2b",
                "4x3": "72c1767f42ad6810131aa2cde647984d",
                "16x9": "3334426d6b45c7037d24f661115dadb1"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{No One Under 16 Admitted}/{16}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "7e5b8cdacdec2dbb2783fd1f577de908",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T09:00:00Z",
            "endTime": "2018-04-27T10:00:00Z",
            "duration": 0,
            "name": "Botched",
            "shortName": "Botched",
            "description": "Una madre no tiene más remedio que ponerse cinta de embalar sobre los pechos. Una joven enfermera necesita ayuda con su nariz. Una celebridad de segunda fila quiere que le dejen una nariz de estrella de cine.",
            "shortDescription": "Se pone cinta en los pechos.",
            "language": "es",
            "pictureID": "ac76c24b00ae95d23bd2819240fae2ed",
            "pictures": {
                "2x3": "5ad89ce4a86e98695a9bb16c0c34317b",
                "3x4": "20b2c650911f1cc1a0d544384acd3c85",
                "4x3": "cbbc32c77b06408a5fe8a1b1fadb08fa",
                "16x9": "ac76c24b00ae95d23bd2819240fae2ed"
            },
            "ratings": [
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{12 anos}/{12}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        },
        {
            "id": "4627ec4a2bc315199a558a3b53523894",
            "resourceType": "epg/episodes",
            "startTime": "2018-04-27T10:00:00Z",
            "endTime": "2018-04-27T11:00:00Z",
            "duration": 0,
            "name": "Keeping Up With the Kardashians",
            "shortName": "Kardashian",
            "description": "Las chicas comienzan a hacer las paces con la nueva relación de Rob, pero bromas en los medios sociales conducen a herir sentimientos; Kris y Kim llegan a sus puntos de ruptura; Kendall se siente excluida.",
            "shortDescription": "Bromas de Rob lastiman a las chicas.",
            "language": "es",
            "pictureID": "9d5432971829dd2af9fccd3717840da0",
            "pictures": {
                "2x3": "a487f97a475a0d2406e515f608d98fd9",
                "3x4": "098ea51641786b3490d397c520b5c61d",
                "4x3": "667d31e3f28cbf5ccac294c9a876b4a7",
                "16x9": "9d5432971829dd2af9fccd3717840da0"
            },
            "ratings": [
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{16 anos}/{16}",
                "{USA Parental Rating}/{}/{TV14}",
                "{Canadian Parental Rating}/{}/{14+}",
                "{Régie du cinéma}/{8 Years and Over}/{8+}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Film & Publication Board}/{Parental Guidance Recommended}/{PG}"
            ],
            "ratingAdvisories": null,
            "stationID": "",
            "genreIDs": null,
            "assetIDs": null
        }
    ]
}
```



## v2/search



### 1. List matching content


Returns any resources matching the provided query string.

<br/>

**Notes**: 
* The startTime.gte and startTime.lte parameters are only supported on the new non-SportsRocket CMS implementation.
* All query parameters are optional unless otherwise indicated.

##### Query Parameters 

| Field | Description | 
|------:|-------------|
| language | Code for the requested language. Use * as a wildcard for all languages.|
|types|Optional. Comma-separated list of resource types to return.|
|query|Optional. Search by query string.|
|startTime.gte| Start range in ISO-8601 format (2018-11-20T15:00:00.000Z). Lists events that begin at or after the specified date and time.|
|startTime.lte |End range in ISO-8601 format (2019-11-20T15:00:00.000Z). Lists events that begin at or before the specified date and time.|
|liveEventDate.gte| Start range in ISO-8601 format (2018-11-20T15:00:00.000Z). Filters VOD events with a liveEventDate at or after the specified date and time.|
|liveEventDate.lte| End range in ISO-8601 format (2018-11-20T15:00:00.000Z). Filters VOD events with a liveEventDate at or before the specified date and time.|
|sort| Specifies field to sort results on. Valid values: startTime, endTime, updated, created, liveEventDate, name, relevance. Defaults to relevance on text search and name on non-text search.|
|sortOrder| Specifies direction of sort. Valid values: asc, desc.|
|published| Comma-separated list that specifies whether results should include published or unpublished content or both. Values: pub,unpub|
|searchMethods| Comma-separated list of fuctionality to use in text search. Valid values: fuzzy,prefix,exact,all|
|include |Request related data, such as "entitlements" to include in the results.|
| offset |Number of items to skip at the start of the returned result set; used for pagination. Default is 0.|

<br/>

##### Response Object 

| Field  | Parent | Type | Description | 
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| *`results`* |   | array |  List of various resources |   |
| *`entitled`* |   | array | List of entitled resource IDs. Present only if _include=entitlements_ is specified.|
|**(varies)**|	|object|Properties vary by resource type||

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station resources|

<!--|404		|1040				|*Not Found*: No matching station ID found|-->


<!--

{
    "requestID": "a2329606-e446-456c-8cb9-1fdb1c1e30dd",
    "timestamp": "2018-06-07T12:54:49.633410529Z",
    "metadata": {
        "count": 10,
        "totalCount": 285,
        "offset": 0
    },
    "results": [
        {
            "id": "7a7cfada20bb59db4521ec68e0ceb8b5",
            "resourceType": "shows",
            "startTime": "2011-07-13T00:00:00.000+00:00",
            "endTime": "",
            "name": "Dance Moms",
            "shortName": "Dance Moms",
            "description": "Abby Lee Miller dirige la compañía de baile Abby Lee, en Pittsburgh, que comenzó cuando tenía 14 años. Miller es una instructora notoriamente exigente y apasionada. Pero no es la única exigente del área - según las madres de sus alumnos, los que se presentan en esta docuserie. La serie destaca las altas y bajas de la competitiva temporada de danza mientras los bailarines van por el título nacional de danza. Miller instruye a sus alumnos al tiempo que lidia con madres exigentes que hacen de todo por ayudar a que los sueños de sus hijos se hagan realidad (¿o sueños de las madres?). El programa capta la interacción dinámica entre padres, maestros y estudiantes mientras que Miller intenta obtener lo mejor de sus alumnos.",
            "shortDescription": "",
            "pictureID": "92f709fa23ead730ba8224372d39969b",
            "pictures": {
                "2x3": null,
                "3x4": "de472405418fc043e5ffc3b2e359f9fe",
                "4x3": "1b4009ed493705c210f3547a98966820",
                "16x9": "92f709fa23ead730ba8224372d39969b"
            },
            "genreIDs": [
                "5d0e18705ddfa63fa5f6142809312a06",
                "14d85b52e8e7fdb14250b28666d50db2"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TVPG",
                "Canadian Parental Rating//PG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Australian Classification Board/Mature/M"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 7,
            "duration": 0,
            "seasonIDs": [
                "10cd31ccd4369e8aa0c0645c6584b62a",
                "6d6ef5b58afefb8c57ddbfc649d1b2a5",
                "40a47f2839daad65386a0d90c3d3bf77",
                "340e058284b1aac9f8bc814f0c17d1ca",
                "fec89ae07c424cc848cc8473ce7c1800",
                "139c4729f31e8251013951a50f190159",
                "f04e6cf0b6b692ed4711568b8ca7388d"
            ]
        },
        {
            "id": "89b558ec192499d1c55ca897f7905cbd",
            "resourceType": "shows",
            "startTime": "2017-08-27T00:00:00.000+00:00",
            "endTime": "",
            "name": "Juego sagrado",
            "shortName": "Juego sag",
            "description": "Resumen de cada uno de los partidos disputados en la Superliga argentina. Los goles, las jugadas polémicas, las grandes figuras de cada fecha. Con la conducción de Gustavo López y Martín Liberman.",
            "shortDescription": "",
            "pictureID": "c5b97d72e98841a5e31cc1bf27427567",
            "pictures": {
                "2x3": "60958e468b95449d1d076c86f545c371",
                "3x4": "8651e96394e434585e7a20bf047b65d3",
                "4x3": "44c6ff7d95f530bc865f7a0003324afc",
                "16x9": "c5b97d72e98841a5e31cc1bf27427567"
            },
            "genreIDs": [
                "14d85b52e8e7fdb14250b28666d50db2"
            ],
            "language": "es",
            "ratings": null,
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 0,
            "duration": 0,
            "seasonIDs": null
        },
        {
            "id": "d8b083eb7b2ffbdaa902d8dc91b83988",
            "resourceType": "vod/movies",
            "startTime": "2012-01-01T00:00:00.000+00:00",
            "endTime": "",
            "duration": 0,
            "name": "Qué esperar cuando estás esperando",
            "shortName": "Qué",
            "description": "Inspirada en el libro de Heidi Murkoff.",
            "shortDescription": "Inspirada en el libro de Heidi Murkoff.",
            "pictureID": "b9ec157df6ca89946d47806bd9717a4e",
            "pictures": {
                "2x3": "1c9ed31eba658466e0160b6a397156f9",
                "3x4": "3cabeb0d1e0082cf50fc867a171b5cd5",
                "4x3": "621cd950e3d411b2e541c1cb4d90d3e5",
                "16x9": "b9ec157df6ca89946d47806bd9717a4e"
            },
            "genreIDs": [
                "f5d5ea511e993e0f730307e1fe0a12c1"
            ],
            "language": "es",
            "ratings": [
                "Motion Picture Association of America/Parents Strongly Cautioned/PG-13",
                "British Board of Film Classification/12A/12A",
                "B.C. Film Classification Office/Parental Guidance/PG",
                "Saskatchewan Film and Video Classification Board/Parental Guidance/PG",
                "Manitoba Film Classification Board/Parental Guidance/PG",
                "Alberta's Film Classification Board/Parental Guidance/PG",
                "Ontario Film Authority/14A/14A",
                "Régie du cinéma/General/G",
                "Maritime Film Classification Board/Parental Guidance/PG",
                "UK Content Provider/12/12",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released without age restriction./0",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 7 years/K7",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Australian Classification Board/Mature/M",
                "Conseil Supérieur de l'Audiovisuel/Universal/Tous publics",
                "Medietilsynet/Tillatt for alle/A"
            ],
            "ratingAdvisories": [
                "Adult Language",
                "Adult Situations"
            ],
            "regionIDs": null,
            "releaseYear": 0,
            "assetIDs": null
        },
        {
            "id": "190edafd047191084516b2091889de60",
            "resourceType": "vod/movies",
            "startTime": "2008-01-01T00:00:00.000+00:00",
            "endTime": "",
            "duration": 0,
            "name": "Un Papá muy Poderoso",
            "shortName": "Papá.",
            "description": "Una adolescente (Madeline Carroll) precoz provoca una serie de eventos que hacen que el resultado de una elección descanse en las manos de su padre (Kevin Costner).",
            "shortDescription": "Una adolescente (Madeline Carroll) precoz provoca una serie de eventos que hacen que el resultado de una elección descanse en las manos de su padre (Kevin Costner).",
            "pictureID": "fa3269577c58077a87f722deeb89e78d",
            "pictures": {
                "2x3": "76f0f3058a07f88ac2a0e66392ff37ee",
                "3x4": "06d1d51f16063f7fba9aaf08e2e93e6a",
                "4x3": "d648726a0ffe096c994789f6f26b9c71",
                "16x9": "fa3269577c58077a87f722deeb89e78d"
            },
            "genreIDs": [
                "f5d5ea511e993e0f730307e1fe0a12c1"
            ],
            "language": "es",
            "ratings": [
                "Motion Picture Association of America/Parents Strongly Cautioned/PG-13",
                "B.C. Film Classification Office/Parental Guidance/PG",
                "Saskatchewan Film and Video Classification Board/Parental Guidance/PG",
                "Ontario Film Authority/Parental Guidance/PG",
                "Manitoba Film Classification Board/Parental Guidance/PG",
                "British Board of Film Classification/12A/12A",
                "Alberta's Film Classification Board/Parental Guidance/PG",
                "Maritime Film Classification Board/Parental Guidance/PG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 6 or older./6",
                "Australian Classification Board/Mature/M",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed for all ages/S"
            ],
            "ratingAdvisories": [
                "Adult Language",
                "Adult Situations"
            ],
            "regionIDs": null,
            "releaseYear": 0,
            "assetIDs": null
        },
        {
            "id": "11c1590ffe1b721cc7245e63d65fa932",
            "resourceType": "vod/movies",
            "startTime": "2000-01-01T00:00:00.000+00:00",
            "endTime": "",
            "duration": 0,
            "name": "La Célula",
            "shortName": "La Célula",
            "description": "Espantosas visiones se le revelan a una terapeuta cuando penetra en la mente de un asesino en serie en estado de coma.",
            "shortDescription": "Espantosas visiones se le revelan a una terapeuta cuando penetra en la mente de un asesino en serie en estado de coma.",
            "pictureID": "e7b5253c4bf9b0f479bf51dc50e40c05",
            "pictures": {
                "2x3": "22f9ef5772bf736a2e1cdf749eaf1599",
                "3x4": "11f9432563adc5a1a3e6c96baae67dce",
                "4x3": "7f5ea06238e5088109fa1b64653b2964",
                "16x9": "e7b5253c4bf9b0f479bf51dc50e40c05"
            },
            "genreIDs": [
                "796398d76c22b7186bb5897cf4e67f59"
            ],
            "language": "es",
            "ratings": [
                "Motion Picture Association of America/Restricted/R",
                "British Board of Film Classification/18/18",
                "Alberta's Film Classification Board/18A/18A",
                "B.C. Film Classification Office/18A/18A",
                "Manitoba Film Classification Board/Restricted/R",
                "Maritime Film Classification Board/Adult Accompaniment/14",
                "Ontario Film Authority/Restricted/R",
                "Régie du cinéma/16 Years and Over/16+",
                "Saskatchewan Film and Video Classification Board/18A/18A",
                "UK Content Provider/18/18",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/16 anos/16",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 16 or older./16",
                "Australian Classification Board/Restricted/R 18+",
                "Ley de Medios Audiovisuales//SAM 18"
            ],
            "ratingAdvisories": [
                "Adult Language",
                "Adult Situations",
                "Graphic Violence",
                "Nudity"
            ],
            "regionIDs": null,
            "releaseYear": 0,
            "assetIDs": null
        },
        {
            "id": "e3d39f1377a00e7074b26b9c65281c21",
            "resourceType": "vod/episodes",
            "startTime": "2014-10-13T00:00:00.000+00:00",
            "endTime": "",
            "name": "Corazón poco elegante - Parte 2",
            "shortName": "Corazón poco elegante - Parte 2",
            "description": "Un miembro del equipo es atacado por el Departamento de Justicia; Hetty recibe inquietantes noticias del director Leon Vance.",
            "shortDescription": "Un miembro del equipo es atacado por el Departamento de Justicia; Hetty recibe inquietantes noticias del director Leon Vance.",
            "pictureID": "236d7ad9e9742a542d1e095d778b9fff",
            "pictures": {
                "2x3": null,
                "3x4": "8cd19c8650a6cf6054a1e6d027a8e1d3",
                "4x3": "1b8ebaf07b81afe26af55a3fae0b36bb",
                "16x9": "236d7ad9e9742a542d1e095d778b9fff"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e",
                "44e9a05a1cc248998fa8711e7f722f1a",
                "067d70ff2bcc556a913e52da08cc9139",
                "d775f75f857ae6a6c2b33e487686da54"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TV14",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/14 anos/14",
                "Freiwillige Selbstkontrolle Fernsehen/Suitable for 16 years and above (ab 16 Jahren)/16",
                "Australian Classification Board/Mature/M",
                "Canadian Parental Rating//14+",
                "Régie du cinéma/13 Years and Over/13+",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 6,
            "episode": 3,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "2992198a3b7e899c8b72610ed122bb1f",
            "showName": "NCIS: Los Ángeles"
        },
        {
            "id": "af0f29161dcfa4716b846f9dd3dd360e",
            "resourceType": "shows",
            "startTime": "2009-09-22T00:00:00.000+00:00",
            "endTime": "",
            "name": "NCIS: Los Ángeles",
            "shortName": "NCIS",
            "description": "Agentes sumamente entrenados trabajan encubiertos con la tecnología disponible más avanzada para atrapar a los criminales que son considerados un peligro que atenta contra la seguridad nacional.",
            "shortDescription": "",
            "pictureID": "a3a8c28ceee0550c9468c7711a521d6d",
            "pictures": {
                "2x3": "ee6fb06c6c155c42b5f74d50350ed015",
                "3x4": "d9d9002a197bbe50a33889bd2ab1ef03",
                "4x3": "511d82318ebc97140677638ba3b7f93c",
                "16x9": "a3a8c28ceee0550c9468c7711a521d6d"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e",
                "44e9a05a1cc248998fa8711e7f722f1a",
                "067d70ff2bcc556a913e52da08cc9139",
                "d775f75f857ae6a6c2b33e487686da54"
            ],
            "language": "es",
            "ratings": [
                "Departamento de Justiça, Classificação, Títulos e Qualificação/14 anos/14",
                "USA Parental Rating//TV14",
                "Freiwillige Selbstkontrolle Fernsehen/Suitable for 16 years and above (ab 16 Jahren)/16",
                "Australian Classification Board/Mature/M",
                "Canadian Parental Rating//14+",
                "Régie du cinéma/13 Years and Over/13+",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 16 years/K16"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 9,
            "duration": 0,
            "seasonIDs": [
                "8f3a380af45d2dd2e49989a17d1dee8b",
                "33e406536f841bb2a95a1dcff0a28c2c",
                "53e04573cdbe05f6381cf49a4143cbf0",
                "b8f3bb508e260a4d3e6fc6080bd08a7c",
                "e56ed2d68a8b506ce811d3487d908239",
                "2992198a3b7e899c8b72610ed122bb1f",
                "33044c0ddc2c8a4d6fa0fe43b8f73472",
                "474a34355c465ecc5999069a0fa1bb54",
                "97d4a85b8dd134aa1e834a61baf60a47"
            ]
        },
        {
            "id": "b17ce714eb51e63bcfc7cc7d0186e998",
            "resourceType": "vod/episodes",
            "startTime": "2016-11-03T00:00:00.000+00:00",
            "endTime": "",
            "name": "Tres Toxinas y Tres Historias",
            "shortName": "Tres Toxinas y Tres Historias",
            "description": "Cuando los estudiantes de patología trabajan con el equipo en un caso frío, sus hallazgos afectarán a toda la familia de Rosewood.",
            "shortDescription": "Cuando los estudiantes de patología trabajan con el equipo en un caso frío, sus hallazgos afectarán a toda la familia de Rosewood.",
            "pictureID": "007aa828942fd6961581c936d6b1a07d",
            "pictures": {
                "2x3": null,
                "3x4": "d8c656839b31b8881651b81f9d8452dc",
                "4x3": "9e5d421f9d9104dcc9c51e3c4fb34ef0",
                "16x9": "007aa828942fd6961581c936d6b1a07d"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e"
            ],
            "language": "es",
            "ratings": [
                "Australian Classification Board/Mature/M",
                "USA Parental Rating//TV14",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12",
                "Canadian Parental Rating//14+",
                "Film & Publication Board/Parental Guidance Recommended/PG",
                "Conseil Supérieur de l'Audiovisuel/Allowed from 10 years/-10",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 12 or older and to age 6 or older with parental guidance./12"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 2,
            "episode": 6,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "966f7d665efc8e43b9165dcf95dadbf0",
            "showName": "Rosewood"
        },
        {
            "id": "2285ede5bc8dcc1a4a9de911cdb14933",
            "resourceType": "shows",
            "startTime": "2015-09-23T00:00:00.000+00:00",
            "endTime": "2017-04-28T00:00:00.000+00:00",
            "name": "Rosewood",
            "shortName": "Rosewood",
            "description": "Un patólogo brillante utiliza tecnología sofisticada para ayudar a una detective de la policía de Miami a resolver crímenes.",
            "shortDescription": "",
            "pictureID": "d457b592a3b622c90c6dd342d76dd1be",
            "pictures": {
                "2x3": null,
                "3x4": "91268b07de1e262281a74626ed36376a",
                "4x3": "c38758f0b6fbadf5f446db00ce692a1a",
                "16x9": "d457b592a3b622c90c6dd342d76dd1be"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e"
            ],
            "language": "es",
            "ratings": [
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12",
                "USA Parental Rating//TV14",
                "Canadian Parental Rating//14+",
                "Australian Classification Board/Mature/M",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 12 or older and to age 6 or older with parental guidance./12"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 2,
            "duration": 0,
            "seasonIDs": [
                "db9d2c726d457c4231c5c913e16416d9",
                "966f7d665efc8e43b9165dcf95dadbf0"
            ]
        },
        {
            "id": "b5a50f236e2488eda111227b0f3c2d9c",
            "resourceType": "vod/episodes",
            "startTime": "2016-12-01T00:00:00.000+00:00",
            "endTime": "",
            "name": "Media Vida & Noches en La Habana",
            "shortName": "Media Vida & Noches en La Habana",
            "description": "La investigación del caso Gerald hace que Rosewood y Villa vayan a Cuba, donde confrontan contra dos misterios.",
            "shortDescription": "La investigación del caso Gerald hace que Rosewood y Villa vayan a Cuba, donde confrontan contra dos misterios.",
            "pictureID": "56fc61c96a6ea8f46b812d3551b618d6",
            "pictures": {
                "2x3": null,
                "3x4": "52d7cc06b31600d183a6fbc2a2b5f9ae",
                "4x3": "23b299ed6be5e343b5850ecf8f282716",
                "16x9": "56fc61c96a6ea8f46b812d3551b618d6"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e"
            ],
            "language": "es",
            "ratings": [
                "Australian Classification Board/Mature/M",
                "USA Parental Rating//TV14",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12",
                "Canadian Parental Rating//14+",
                "Film & Publication Board/Parental Guidance Recommended/PG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/14 anos/14",
                "Conseil Supérieur de l'Audiovisuel/Allowed from 10 years/-10",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 12 or older and to age 6 or older with parental guidance./12"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 2,
            "episode": 9,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "966f7d665efc8e43b9165dcf95dadbf0",
            "showName": "Rosewood"
        },
        {
            "id": "6decfb81d0f51fb0154ac29e6a40671c",
            "resourceType": "vod/episodes",
            "startTime": "2017-09-12T00:00:00.000+00:00",
            "endTime": "",
            "name": "Ashlee's Big Decision Part 1",
            "shortName": "Ashlee's Big Decision Part 1",
            "description": "Abby regresa inesperadamente al estudio; Chloe actúa frente a Abby por primera vez en dos años, pero extraña a sus antiguas compañeras de equipo; Ashlee toma una decisión que sorprende al grupo.",
            "shortDescription": "Abby regresa inesperadamente al estudio; Chloe actúa frente a Abby por primera vez en dos años, pero extraña a sus antiguas compañeras de equipo; Ashlee toma una decisión que sorprende al grupo.",
            "pictureID": "97e1e722809fd9ba0827b82591c9362b",
            "pictures": {
                "2x3": null,
                "3x4": "7c648912ae0b80d4397d47ce2a3304f8",
                "4x3": "7ecbfdd9149f51db3ec4799392d929ef",
                "16x9": "97e1e722809fd9ba0827b82591c9362b"
            },
            "genreIDs": [
                "5d0e18705ddfa63fa5f6142809312a06",
                "14d85b52e8e7fdb14250b28666d50db2"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TVPG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Canadian Parental Rating//PG",
                "Australian Classification Board/Mature/M",
                "Film & Publication Board/Suitable for family viewing/Family"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 7,
            "episode": 21,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "f04e6cf0b6b692ed4711568b8ca7388d",
            "showName": "Dance Moms"
        },
        {
            "id": "f6b4ab25772d440d8777d4bd78472cb5",
            "resourceType": "vod/episodes",
            "startTime": "2017-09-05T00:00:00.000+00:00",
            "endTime": "",
            "name": "Stamina, Stamina, Stamina",
            "shortName": "Stamina, Stamina, Stamina",
            "description": "Laurieann Gibson regresa, decidida a ganar; con dos dúos y un baile en grupo, las chicas lidian con la energía y la actitud despiadada de la líder; Laurieann pierde la paciencia con las madres en una competencia.",
            "shortDescription": "Laurieann Gibson regresa, decidida a ganar; con dos dúos y un baile en grupo, las chicas lidian con la energía y la actitud despiadada de la líder; Laurieann pierde la paciencia con las madres en una competencia.",
            "pictureID": "b721fcb861bd362c330c74991f30405e",
            "pictures": {
                "2x3": null,
                "3x4": "4f9bfc536c77609d78f2e35bac983782",
                "4x3": "48484b7b6b3fb83dd22cfab1b676dfcb",
                "16x9": "b721fcb861bd362c330c74991f30405e"
            },
            "genreIDs": [
                "5d0e18705ddfa63fa5f6142809312a06",
                "14d85b52e8e7fdb14250b28666d50db2"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TVPG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Canadian Parental Rating//PG",
                "Australian Classification Board/Mature/M",
                "Film & Publication Board/Suitable for family viewing/Family"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 7,
            "episode": 20,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "f04e6cf0b6b692ed4711568b8ca7388d",
            "showName": "Dance Moms"
        }
    ]
}

-->


<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/search
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Geo-Position | 47.606209;-122.332069 | Global position specified as {_longitude;latitude_}. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use * as a wildcard for all languages. |
| types | live/competitions | _Optional_. Comma-separated list of resource types to return. |
| query | Lima | _Required_. Search by query string. |
| startTime.gte | 2018-11-20T15:00:00.000Z | Start range in ISO-8601 format: lists events that begin  _at or after_ the specified date and time. |
| startTime.lte | 2019-11-20T15:00:00.000Z | End range in ISO-8601 format: lists events that begin  _at or before_ the specified date and time. |
| include | entitlements | Request  related data to Include in the results. |
| offset | 5 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |



***Responses:***


Status: Returns a list of matching content | Code: 200



```js
{
    "requestID": "a2329606-e446-456c-8cb9-1fdb1c1e30dd",
    "timestamp": "2018-06-07T12:54:49.633410529Z",
    "metadata": {
        "count": 10,
        "totalCount": 285,
        "offset": 0
    },
    "results": [
        {
            "id": "7a7cfada20bb59db4521ec68e0ceb8b5",
            "resourceType": "shows",
            "startTime": "2011-07-13T00:00:00.000+00:00",
            "endTime": "",
            "name": "Dance Moms",
            "shortName": "Dance Moms",
            "description": "Abby Lee Miller dirige la compañía de baile Abby Lee, en Pittsburgh, que comenzó cuando tenía 14 años. Miller es una instructora notoriamente exigente y apasionada. Pero no es la única exigente del área - según las madres de sus alumnos, los que se presentan en esta docuserie. La serie destaca las altas y bajas de la competitiva temporada de danza mientras los bailarines van por el título nacional de danza. Miller instruye a sus alumnos al tiempo que lidia con madres exigentes que hacen de todo por ayudar a que los sueños de sus hijos se hagan realidad (¿o sueños de las madres?). El programa capta la interacción dinámica entre padres, maestros y estudiantes mientras que Miller intenta obtener lo mejor de sus alumnos.",
            "shortDescription": "",
            "pictureID": "92f709fa23ead730ba8224372d39969b",
            "pictures": {
                "2x3": null,
                "3x4": "de472405418fc043e5ffc3b2e359f9fe",
                "4x3": "1b4009ed493705c210f3547a98966820",
                "16x9": "92f709fa23ead730ba8224372d39969b"
            },
            "genreIDs": [
                "5d0e18705ddfa63fa5f6142809312a06",
                "14d85b52e8e7fdb14250b28666d50db2"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TVPG",
                "Canadian Parental Rating//PG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Australian Classification Board/Mature/M"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 7,
            "duration": 0,
            "seasonIDs": [
                "10cd31ccd4369e8aa0c0645c6584b62a",
                "6d6ef5b58afefb8c57ddbfc649d1b2a5",
                "40a47f2839daad65386a0d90c3d3bf77",
                "340e058284b1aac9f8bc814f0c17d1ca",
                "fec89ae07c424cc848cc8473ce7c1800",
                "139c4729f31e8251013951a50f190159",
                "f04e6cf0b6b692ed4711568b8ca7388d"
            ]
        },
        {
            "id": "89b558ec192499d1c55ca897f7905cbd",
            "resourceType": "shows",
            "startTime": "2017-08-27T00:00:00.000+00:00",
            "endTime": "",
            "name": "Juego sagrado",
            "shortName": "Juego sag",
            "description": "Resumen de cada uno de los partidos disputados en la Superliga argentina. Los goles, las jugadas polémicas, las grandes figuras de cada fecha. Con la conducción de Gustavo López y Martín Liberman.",
            "shortDescription": "",
            "pictureID": "c5b97d72e98841a5e31cc1bf27427567",
            "pictures": {
                "2x3": "60958e468b95449d1d076c86f545c371",
                "3x4": "8651e96394e434585e7a20bf047b65d3",
                "4x3": "44c6ff7d95f530bc865f7a0003324afc",
                "16x9": "c5b97d72e98841a5e31cc1bf27427567"
            },
            "genreIDs": [
                "14d85b52e8e7fdb14250b28666d50db2"
            ],
            "language": "es",
            "ratings": null,
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 0,
            "duration": 0,
            "seasonIDs": null
        },
        {
            "id": "d8b083eb7b2ffbdaa902d8dc91b83988",
            "resourceType": "vod/movies",
            "startTime": "2012-01-01T00:00:00.000+00:00",
            "endTime": "",
            "duration": 0,
            "name": "Qué esperar cuando estás esperando",
            "shortName": "Qué",
            "description": "Inspirada en el libro de Heidi Murkoff.",
            "shortDescription": "Inspirada en el libro de Heidi Murkoff.",
            "pictureID": "b9ec157df6ca89946d47806bd9717a4e",
            "pictures": {
                "2x3": "1c9ed31eba658466e0160b6a397156f9",
                "3x4": "3cabeb0d1e0082cf50fc867a171b5cd5",
                "4x3": "621cd950e3d411b2e541c1cb4d90d3e5",
                "16x9": "b9ec157df6ca89946d47806bd9717a4e"
            },
            "genreIDs": [
                "f5d5ea511e993e0f730307e1fe0a12c1"
            ],
            "language": "es",
            "ratings": [
                "Motion Picture Association of America/Parents Strongly Cautioned/PG-13",
                "British Board of Film Classification/12A/12A",
                "B.C. Film Classification Office/Parental Guidance/PG",
                "Saskatchewan Film and Video Classification Board/Parental Guidance/PG",
                "Manitoba Film Classification Board/Parental Guidance/PG",
                "Alberta's Film Classification Board/Parental Guidance/PG",
                "Ontario Film Authority/14A/14A",
                "Régie du cinéma/General/G",
                "Maritime Film Classification Board/Parental Guidance/PG",
                "UK Content Provider/12/12",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released without age restriction./0",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 7 years/K7",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Australian Classification Board/Mature/M",
                "Conseil Supérieur de l'Audiovisuel/Universal/Tous publics",
                "Medietilsynet/Tillatt for alle/A"
            ],
            "ratingAdvisories": [
                "Adult Language",
                "Adult Situations"
            ],
            "regionIDs": null,
            "releaseYear": 0,
            "assetIDs": null
        },
        {
            "id": "190edafd047191084516b2091889de60",
            "resourceType": "vod/movies",
            "startTime": "2008-01-01T00:00:00.000+00:00",
            "endTime": "",
            "duration": 0,
            "name": "Un Papá muy Poderoso",
            "shortName": "Papá.",
            "description": "Una adolescente (Madeline Carroll) precoz provoca una serie de eventos que hacen que el resultado de una elección descanse en las manos de su padre (Kevin Costner).",
            "shortDescription": "Una adolescente (Madeline Carroll) precoz provoca una serie de eventos que hacen que el resultado de una elección descanse en las manos de su padre (Kevin Costner).",
            "pictureID": "fa3269577c58077a87f722deeb89e78d",
            "pictures": {
                "2x3": "76f0f3058a07f88ac2a0e66392ff37ee",
                "3x4": "06d1d51f16063f7fba9aaf08e2e93e6a",
                "4x3": "d648726a0ffe096c994789f6f26b9c71",
                "16x9": "fa3269577c58077a87f722deeb89e78d"
            },
            "genreIDs": [
                "f5d5ea511e993e0f730307e1fe0a12c1"
            ],
            "language": "es",
            "ratings": [
                "Motion Picture Association of America/Parents Strongly Cautioned/PG-13",
                "B.C. Film Classification Office/Parental Guidance/PG",
                "Saskatchewan Film and Video Classification Board/Parental Guidance/PG",
                "Ontario Film Authority/Parental Guidance/PG",
                "Manitoba Film Classification Board/Parental Guidance/PG",
                "British Board of Film Classification/12A/12A",
                "Alberta's Film Classification Board/Parental Guidance/PG",
                "Maritime Film Classification Board/Parental Guidance/PG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 6 or older./6",
                "Australian Classification Board/Mature/M",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed for all ages/S"
            ],
            "ratingAdvisories": [
                "Adult Language",
                "Adult Situations"
            ],
            "regionIDs": null,
            "releaseYear": 0,
            "assetIDs": null
        },
        {
            "id": "11c1590ffe1b721cc7245e63d65fa932",
            "resourceType": "vod/movies",
            "startTime": "2000-01-01T00:00:00.000+00:00",
            "endTime": "",
            "duration": 0,
            "name": "La Célula",
            "shortName": "La Célula",
            "description": "Espantosas visiones se le revelan a una terapeuta cuando penetra en la mente de un asesino en serie en estado de coma.",
            "shortDescription": "Espantosas visiones se le revelan a una terapeuta cuando penetra en la mente de un asesino en serie en estado de coma.",
            "pictureID": "e7b5253c4bf9b0f479bf51dc50e40c05",
            "pictures": {
                "2x3": "22f9ef5772bf736a2e1cdf749eaf1599",
                "3x4": "11f9432563adc5a1a3e6c96baae67dce",
                "4x3": "7f5ea06238e5088109fa1b64653b2964",
                "16x9": "e7b5253c4bf9b0f479bf51dc50e40c05"
            },
            "genreIDs": [
                "796398d76c22b7186bb5897cf4e67f59"
            ],
            "language": "es",
            "ratings": [
                "Motion Picture Association of America/Restricted/R",
                "British Board of Film Classification/18/18",
                "Alberta's Film Classification Board/18A/18A",
                "B.C. Film Classification Office/18A/18A",
                "Manitoba Film Classification Board/Restricted/R",
                "Maritime Film Classification Board/Adult Accompaniment/14",
                "Ontario Film Authority/Restricted/R",
                "Régie du cinéma/16 Years and Over/16+",
                "Saskatchewan Film and Video Classification Board/18A/18A",
                "UK Content Provider/18/18",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/16 anos/16",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 16 or older./16",
                "Australian Classification Board/Restricted/R 18+",
                "Ley de Medios Audiovisuales//SAM 18"
            ],
            "ratingAdvisories": [
                "Adult Language",
                "Adult Situations",
                "Graphic Violence",
                "Nudity"
            ],
            "regionIDs": null,
            "releaseYear": 0,
            "assetIDs": null
        },
        {
            "id": "e3d39f1377a00e7074b26b9c65281c21",
            "resourceType": "vod/episodes",
            "startTime": "2014-10-13T00:00:00.000+00:00",
            "endTime": "",
            "name": "Corazón poco elegante - Parte 2",
            "shortName": "Corazón poco elegante - Parte 2",
            "description": "Un miembro del equipo es atacado por el Departamento de Justicia; Hetty recibe inquietantes noticias del director Leon Vance.",
            "shortDescription": "Un miembro del equipo es atacado por el Departamento de Justicia; Hetty recibe inquietantes noticias del director Leon Vance.",
            "pictureID": "236d7ad9e9742a542d1e095d778b9fff",
            "pictures": {
                "2x3": null,
                "3x4": "8cd19c8650a6cf6054a1e6d027a8e1d3",
                "4x3": "1b8ebaf07b81afe26af55a3fae0b36bb",
                "16x9": "236d7ad9e9742a542d1e095d778b9fff"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e",
                "44e9a05a1cc248998fa8711e7f722f1a",
                "067d70ff2bcc556a913e52da08cc9139",
                "d775f75f857ae6a6c2b33e487686da54"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TV14",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/14 anos/14",
                "Freiwillige Selbstkontrolle Fernsehen/Suitable for 16 years and above (ab 16 Jahren)/16",
                "Australian Classification Board/Mature/M",
                "Canadian Parental Rating//14+",
                "Régie du cinéma/13 Years and Over/13+",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 6,
            "episode": 3,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "2992198a3b7e899c8b72610ed122bb1f",
            "showName": "NCIS: Los Ángeles"
        },
        {
            "id": "af0f29161dcfa4716b846f9dd3dd360e",
            "resourceType": "shows",
            "startTime": "2009-09-22T00:00:00.000+00:00",
            "endTime": "",
            "name": "NCIS: Los Ángeles",
            "shortName": "NCIS",
            "description": "Agentes sumamente entrenados trabajan encubiertos con la tecnología disponible más avanzada para atrapar a los criminales que son considerados un peligro que atenta contra la seguridad nacional.",
            "shortDescription": "",
            "pictureID": "a3a8c28ceee0550c9468c7711a521d6d",
            "pictures": {
                "2x3": "ee6fb06c6c155c42b5f74d50350ed015",
                "3x4": "d9d9002a197bbe50a33889bd2ab1ef03",
                "4x3": "511d82318ebc97140677638ba3b7f93c",
                "16x9": "a3a8c28ceee0550c9468c7711a521d6d"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e",
                "44e9a05a1cc248998fa8711e7f722f1a",
                "067d70ff2bcc556a913e52da08cc9139",
                "d775f75f857ae6a6c2b33e487686da54"
            ],
            "language": "es",
            "ratings": [
                "Departamento de Justiça, Classificação, Títulos e Qualificação/14 anos/14",
                "USA Parental Rating//TV14",
                "Freiwillige Selbstkontrolle Fernsehen/Suitable for 16 years and above (ab 16 Jahren)/16",
                "Australian Classification Board/Mature/M",
                "Canadian Parental Rating//14+",
                "Régie du cinéma/13 Years and Over/13+",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 16 years/K16"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 9,
            "duration": 0,
            "seasonIDs": [
                "8f3a380af45d2dd2e49989a17d1dee8b",
                "33e406536f841bb2a95a1dcff0a28c2c",
                "53e04573cdbe05f6381cf49a4143cbf0",
                "b8f3bb508e260a4d3e6fc6080bd08a7c",
                "e56ed2d68a8b506ce811d3487d908239",
                "2992198a3b7e899c8b72610ed122bb1f",
                "33044c0ddc2c8a4d6fa0fe43b8f73472",
                "474a34355c465ecc5999069a0fa1bb54",
                "97d4a85b8dd134aa1e834a61baf60a47"
            ]
        },
        {
            "id": "b17ce714eb51e63bcfc7cc7d0186e998",
            "resourceType": "vod/episodes",
            "startTime": "2016-11-03T00:00:00.000+00:00",
            "endTime": "",
            "name": "Tres Toxinas y Tres Historias",
            "shortName": "Tres Toxinas y Tres Historias",
            "description": "Cuando los estudiantes de patología trabajan con el equipo en un caso frío, sus hallazgos afectarán a toda la familia de Rosewood.",
            "shortDescription": "Cuando los estudiantes de patología trabajan con el equipo en un caso frío, sus hallazgos afectarán a toda la familia de Rosewood.",
            "pictureID": "007aa828942fd6961581c936d6b1a07d",
            "pictures": {
                "2x3": null,
                "3x4": "d8c656839b31b8881651b81f9d8452dc",
                "4x3": "9e5d421f9d9104dcc9c51e3c4fb34ef0",
                "16x9": "007aa828942fd6961581c936d6b1a07d"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e"
            ],
            "language": "es",
            "ratings": [
                "Australian Classification Board/Mature/M",
                "USA Parental Rating//TV14",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12",
                "Canadian Parental Rating//14+",
                "Film & Publication Board/Parental Guidance Recommended/PG",
                "Conseil Supérieur de l'Audiovisuel/Allowed from 10 years/-10",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 12 or older and to age 6 or older with parental guidance./12"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 2,
            "episode": 6,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "966f7d665efc8e43b9165dcf95dadbf0",
            "showName": "Rosewood"
        },
        {
            "id": "2285ede5bc8dcc1a4a9de911cdb14933",
            "resourceType": "shows",
            "startTime": "2015-09-23T00:00:00.000+00:00",
            "endTime": "2017-04-28T00:00:00.000+00:00",
            "name": "Rosewood",
            "shortName": "Rosewood",
            "description": "Un patólogo brillante utiliza tecnología sofisticada para ayudar a una detective de la policía de Miami a resolver crímenes.",
            "shortDescription": "",
            "pictureID": "d457b592a3b622c90c6dd342d76dd1be",
            "pictures": {
                "2x3": null,
                "3x4": "91268b07de1e262281a74626ed36376a",
                "4x3": "c38758f0b6fbadf5f446db00ce692a1a",
                "16x9": "d457b592a3b622c90c6dd342d76dd1be"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e"
            ],
            "language": "es",
            "ratings": [
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12",
                "USA Parental Rating//TV14",
                "Canadian Parental Rating//14+",
                "Australian Classification Board/Mature/M",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 12 or older and to age 6 or older with parental guidance./12"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 2,
            "duration": 0,
            "seasonIDs": [
                "db9d2c726d457c4231c5c913e16416d9",
                "966f7d665efc8e43b9165dcf95dadbf0"
            ]
        },
        {
            "id": "b5a50f236e2488eda111227b0f3c2d9c",
            "resourceType": "vod/episodes",
            "startTime": "2016-12-01T00:00:00.000+00:00",
            "endTime": "",
            "name": "Media Vida & Noches en La Habana",
            "shortName": "Media Vida & Noches en La Habana",
            "description": "La investigación del caso Gerald hace que Rosewood y Villa vayan a Cuba, donde confrontan contra dos misterios.",
            "shortDescription": "La investigación del caso Gerald hace que Rosewood y Villa vayan a Cuba, donde confrontan contra dos misterios.",
            "pictureID": "56fc61c96a6ea8f46b812d3551b618d6",
            "pictures": {
                "2x3": null,
                "3x4": "52d7cc06b31600d183a6fbc2a2b5f9ae",
                "4x3": "23b299ed6be5e343b5850ecf8f282716",
                "16x9": "56fc61c96a6ea8f46b812d3551b618d6"
            },
            "genreIDs": [
                "557c02daad97c095c1eccbf7970d7a1e"
            ],
            "language": "es",
            "ratings": [
                "Australian Classification Board/Mature/M",
                "USA Parental Rating//TV14",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 12 years/K12",
                "Canadian Parental Rating//14+",
                "Film & Publication Board/Parental Guidance Recommended/PG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/14 anos/14",
                "Conseil Supérieur de l'Audiovisuel/Allowed from 10 years/-10",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 12 or older and to age 6 or older with parental guidance./12"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 2,
            "episode": 9,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "966f7d665efc8e43b9165dcf95dadbf0",
            "showName": "Rosewood"
        },
        {
            "id": "6decfb81d0f51fb0154ac29e6a40671c",
            "resourceType": "vod/episodes",
            "startTime": "2017-09-12T00:00:00.000+00:00",
            "endTime": "",
            "name": "Ashlee's Big Decision Part 1",
            "shortName": "Ashlee's Big Decision Part 1",
            "description": "Abby regresa inesperadamente al estudio; Chloe actúa frente a Abby por primera vez en dos años, pero extraña a sus antiguas compañeras de equipo; Ashlee toma una decisión que sorprende al grupo.",
            "shortDescription": "Abby regresa inesperadamente al estudio; Chloe actúa frente a Abby por primera vez en dos años, pero extraña a sus antiguas compañeras de equipo; Ashlee toma una decisión que sorprende al grupo.",
            "pictureID": "97e1e722809fd9ba0827b82591c9362b",
            "pictures": {
                "2x3": null,
                "3x4": "7c648912ae0b80d4397d47ce2a3304f8",
                "4x3": "7ecbfdd9149f51db3ec4799392d929ef",
                "16x9": "97e1e722809fd9ba0827b82591c9362b"
            },
            "genreIDs": [
                "5d0e18705ddfa63fa5f6142809312a06",
                "14d85b52e8e7fdb14250b28666d50db2"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TVPG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Canadian Parental Rating//PG",
                "Australian Classification Board/Mature/M",
                "Film & Publication Board/Suitable for family viewing/Family"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 7,
            "episode": 21,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "f04e6cf0b6b692ed4711568b8ca7388d",
            "showName": "Dance Moms"
        },
        {
            "id": "f6b4ab25772d440d8777d4bd78472cb5",
            "resourceType": "vod/episodes",
            "startTime": "2017-09-05T00:00:00.000+00:00",
            "endTime": "",
            "name": "Stamina, Stamina, Stamina",
            "shortName": "Stamina, Stamina, Stamina",
            "description": "Laurieann Gibson regresa, decidida a ganar; con dos dúos y un baile en grupo, las chicas lidian con la energía y la actitud despiadada de la líder; Laurieann pierde la paciencia con las madres en una competencia.",
            "shortDescription": "Laurieann Gibson regresa, decidida a ganar; con dos dúos y un baile en grupo, las chicas lidian con la energía y la actitud despiadada de la líder; Laurieann pierde la paciencia con las madres en una competencia.",
            "pictureID": "b721fcb861bd362c330c74991f30405e",
            "pictures": {
                "2x3": null,
                "3x4": "4f9bfc536c77609d78f2e35bac983782",
                "4x3": "48484b7b6b3fb83dd22cfab1b676dfcb",
                "16x9": "b721fcb861bd362c330c74991f30405e"
            },
            "genreIDs": [
                "5d0e18705ddfa63fa5f6142809312a06",
                "14d85b52e8e7fdb14250b28666d50db2"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TVPG",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
                "Canadian Parental Rating//PG",
                "Australian Classification Board/Mature/M",
                "Film & Publication Board/Suitable for family viewing/Family"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 7,
            "episode": 20,
            "duration": 0,
            "assetIDs": null,
            "showID": "",
            "seasonID": "f04e6cf0b6b692ed4711568b8ca7388d",
            "showName": "Dance Moms"
        }
    ]
}
```



### 2. List matching stations


Returns any station resources matching the provided query string.

All query parameters are optional unless otherwise indicated.

<br/>

##### Query Parameters 

| Field | Description | 
|------:|-------------|
| language | Code for the requested language. Use * as a wildcard for all languages.|
| query |Required. Search by query string.|
| offset |Number of items to skip at the start of the returned result set; used for pagination. Default is 0.|
| types |Optional. Comma-separated list of resource types to return, such as "epg".|

<br/>

##### Response Object 

| Field  | Parent | Type | Description |  
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| `results` |   | array |  List of various resources |   |
|**(varies)**|`results` |object|Properties vary by resource type||


<!--

##### Response Object 

| Field  | Parent | Type | Description | Notes 
|------:|--------|------|-------------|-------
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| *`results`* |   | array |  List of various resources |   |
|**(varies)**|*`results`*|object|Properties vary by resource type||

<br/>

-->


<br/>


<!--

{
    "requestID": "ce233dec-064c-44dd-ba0c-589d0958b898",
    "timestamp": "2018-11-19T20:09:25.799501215Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "results": [
        {
            "id": "778c1660103e0238d9beed4ae377aa09",
            "resourceType": "epg/stations",
            "name": "Animal Planet Pan Regional HD",
            "shortName": "ANIPPRH",
            "stationNumber": 0,
            "language": "es",
            "languageRegion": "",
            "pictureID": "a9a2c00466767aebc861b9ba72f6e793",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": [
                "f917cff6-025a-4917-84d6-fb686697d93c"
            ],
            "assetIDs": [
                "2a99012f34cfabc8e583592dcb21c205"
            ],
            "metadata": {
                "source": "com.gracenote.source",
                "id": "97482"
            },
            "ingestionLock": false
        }
    ]
}


<br/>

-->

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station resources|

<!--|404		|1040				|*Not Found*: No matching station ID found|-->

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/search/stations
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Geo-Position | 47.606209;-122.332069 | Global position specified as {_longitude;latitude_}. |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| query | <string> | _Required_. Search by query string. |
| offset | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is *0*. |
| types | epg | _Optional_. Comma-separated list of resource types to return. |



***Responses:***


Status: Returns a list of matching stations | Code: 200



```js
{
    "requestID": "ce233dec-064c-44dd-ba0c-589d0958b898",
    "timestamp": "2018-11-19T20:09:25.799501215Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "results": [
        {
            "id": "778c1660103e0238d9beed4ae377aa09",
            "resourceType": "epg/stations",
            "name": "Animal Planet Pan Regional HD",
            "shortName": "ANIPPRH",
            "stationNumber": 0,
            "language": "es",
            "languageRegion": "",
            "pictureID": "a9a2c00466767aebc861b9ba72f6e793",
            "callSign": "",
            "blackoutStation": false,
            "regionIDs": [
                "f917cff6-025a-4917-84d6-fb686697d93c"
            ],
            "assetIDs": [
                "2a99012f34cfabc8e583592dcb21c205"
            ],
            "metadata": {
                "source": "com.gracenote.source",
                "id": "97482"
            },
            "ingestionLock": false
        }
    ]
}
```



### 3. List resources by matching genreIDs


Returns any resources that match all of the specified genreIDs. All query parameters are optional unless otherwise indicated.

<br/>

##### Query Parameters 
| Field | Description | 
|------:|-------------|
| genreIDs | Required. Comma-separated list of IDs for genres you want to filter by.|
| language | Code for the requested language. Use * as a wildcard for all languages.|
|types|Optional. Comma-separated list of resource types to return.|
|query|Required. Search by query string.|
|startTime.gte| Start range in ISO-8601 format (2018-11-20T15:00:00.000Z). Lists events that begin at or after the specified date and time.|
|startTime.lte |End range in ISO-8601 format (2019-11-20T15:00:00.000Z). Lists events that begin at or before the specified date and time.|
|include |Request related data, such as "entitlements" to include in the results.|
| offset |Number of items to skip at the start of the returned result set; used for pagination. Default is 0.|

<br/>


##### Response Object 

| Field  | Parent | Type | Description | 
|------:|--------|------|-------------|
| requestID | | string | Generated log ID for this request.    |   | 
| timestamp | | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| *`results`* |   | array |  List of various resources |   |
| *`entitled`* |   | array | List of entitled resource IDs. Present only if _include=entitlements_ is specified.|
|**(varies)**|	|object|Properties vary by resource type||

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested station resources|

<!--|404		|1040				|*Not Found*: No matching station ID found|-->

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/search
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Geo-Position | 47.606209;-122.332069 | Global position specified as {_longitude;latitude_}. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| genreIDs | 966c0e48-976d-469e-b5f9-d003e3c22ace,38fda1fb-7570-4d9a-98be-3760a481edfc | _Required_. Comma-separated list of IDs for genres you want to filter by. |
| language | pt | Code for the requested language. Use * as a wildcard for all languages. |
| types | vod/episodes,shows | Comma-separated list of resource types to return. |
| query | Lima | Search by query string. |
| startTime.gte | 2017-11-20T15:00:00.000Z | Start range in ISO-8601 format: lists events that begin  _at or after_ the specified date and time. |
| startTime.lte | 2020-11-20T15:00:00.000Z | End range in ISO-8601 format: lists events that begin  _at or before_ the specified date and time. |
| include | entitlements | Request  related data to Include in the results. |
| offset | 5 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |



***Responses:***


Status: Resources matching genreIDs in Portuguese | Code: 200



```js
{
    "requestID": "2dc631da-ff08-430c-9fb6-a4101257e6e7",
    "timestamp": "2019-08-30T00:18:34.308429503Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "results": [
        {
            "id": "2c1d7ec7-6349-4ddb-8f35-761f59df21f5",
            "resourceType": "shows",
            "publishStart": "2019-08-01T14:22:18.46Z",
            "published": true,
            "created": "0001-01-01T00:00:00Z",
            "updated": "2019-08-30T00:17:30.831Z",
            "contentLock": false,
            "startTime": "",
            "endTime": "",
            "name": "El mundo de Luna",
            "shortName": "El mundo de Luna",
            "description": "Luna, una niña de 6 años, tiene claro que la Tierra es un gran laboratorio gigante lleno de oportunidades para aprender más sobre las cosas, y su pasión por la ciencia hace que explore el mundo con energía y entusiasmo.",
            "shortDescription": "Luna, una niña de 6 años, tiene claro que la Tierra es un gran laboratorio gigante lleno de oportunidades para aprender más sobre las cosas, y su pasión por la ciencia hace que explore el mundo con energía y entusiasmo.",
            "pictureID": "",
            "pictures": null,
            "provider": "com.gracenote.on-v3",
            "providerUID": "SH022598580000",
            "providerURL": "",
            "genreIDs": [
                "966c0e48-976d-469e-b5f9-d003e3c22ace",
                "8f3ed89d-6d37-453a-82f7-66b5c6a76014",
                "56562695-6b64-4d45-87e4-af898639692b",
                "38fda1fb-7570-4d9a-98be-3760a481edfc"
            ],
            "language": "pt",
            "ratings": [
                "Departamento de Justiça, Classificação, Títulos e Qualificação/Livre/L",
                "USA Parental Rating//TVY",
                "Canadian Parental Rating//C"
            ],
            "ratingAdvisories": null,
            "regionIDs": [
                "f917cff6-025a-4917-84d6-fb686697d93c",
                "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6"
            ],
            "seasons": 5,
            "seasonIDs": [
                "f742de4f-5e6c-496e-993d-e94483d3988b",
                "6cdf3316-8b5f-4bfb-ab4f-f087223bff23",
                "6cc5975e-7c15-4f6d-afd9-d956c2d9012a",
                "0888ed23-c167-46a1-b6b3-3f3a7b30f302",
                "568fbf9f-70c6-4824-88ba-7db88204afa7"
            ],
            "countryOfOrigin": null,
            "genres": [
                {
                    "id": "38fda1fb-7570-4d9a-98be-3760a481edfc",
                    "name": "Ciência"
                },
                {
                    "id": "56562695-6b64-4d45-87e4-af898639692b",
                    "name": "Fantasia"
                },
                {
                    "id": "8f3ed89d-6d37-453a-82f7-66b5c6a76014",
                    "name": "Infantil"
                },
                {
                    "id": "966c0e48-976d-469e-b5f9-d003e3c22ace",
                    "name": "Animação"
                }
            ]
        }
    ]
}
```



## v2/seasons



### 1. Create a season


Creates a new season for the specified show ID.

<br/>

##### Body Parameters

All fields are required unless otherwise indicated.

| Field  |  Type  | Description | 
|-------:|--------|-------------|
| id			| string | Unique ID for each season.  |
| resourceType	| string | "seasons"  | 
| startTime 	| string | A  timestamp for starting date of the season.  | 
| name			| string | Full name.  | 
| shortName 	| string | Shortened name.  | 
| language		| string | Two-letter code for the spoken language.  | 
| regionIDs 	| string | List of region IDs "whitelisted" for this season's episodes. | 
| vod/episodeIDs| string array| List of IDs for the episodes in this season.   | 
| episodeCount	| number | Number of episodes in this season as obtained from the metadata provider. |
| showID		| string | Unique ID for the show that this season belongs to.  |

<br/>

##### Response object

| Field  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   
| timestamp |    | string | Generated log timestamp for this request.   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number | Number of items skipped from the start of the list; default = 0.
|||||
| `seasons` 	|   		|   	 |      |  
| id			| `seasons` | string | Unique ID for each season.  |  
| resourceType	| `seasons` | string | "seasons"  | 
| startTime 	| `seasons` | string | Timestamp for starting date of the season.  |  
| name			| `seasons` | string | Full season name.  |  
| shortName 	| `seasons` | string | Shortened season name.  |  
| language		| `seasons` | string | Two-letter code for the spoken language.  |  
| regionIDs 	| `seasons` | string | List of region IDs associated with this season. |
| vod/episodeIDs| `seasons` | string array| List of IDs for episodes that belong to this season.  | 
| episodeCount	| `seasons` | number | Number of episodes in this season as obtained from the metadata provider. |
|||||
| `vod/episodes` |   |   |      |  
| id			| `vod/episodes` |string | Unique ID for each episode asset.  |  
| resourceType	| `vod/episodes` | enum string | *vod/episodes*   | 
| startTime 	| `vod/episodes` | string | Timestamp for starting date of the episode.  |  
| endTime		| `vod/episodes` | string | Timestamp for ending date of the episode.  |  
| duration		| `vod/episodes` | number | Video duration in minutes.  |  
| name			| `vod/episodes` | string | Full episode name.  |  
| shortName 	| `vod/episodes` | string | Shortened episode name.   |  
| description	| `vod/episodes` | string | Full episode description.  |  
| shortDescription | `vod/episodes` | string | Short episode description.   |  
| language		| `vod/episodes` | string | Two-letter code for the spoken language.  |  
| pictureID 	| `vod/episodes` | string | ID for the standard image for this episode. |  
| ratings		| `vod/episodes` | string | Age-related ratings from boards and agencies.  | 
| ratingAdvisories | `vod/episodes` | string array | A list of content advisories; such as "Adult Situations", "Language", or "Violence" |
| regionIDs 	| `vod/episodes` | string | List of region IDs associated with this episode. |
| season		| `vod/episodes` | number | Season number that this episode belongs to.|   
| episode		| `vod/episodes` | number | Episode order number for this episode within its season.|   
| genreIDs		| `vod/episodes` | string array | List of genre IDs associated with this episode.| 
| assetIDs		| `vod/episodes` | string array | List of asset IDs associated with this episode.| 
|||||
| `pictures` | `vod/episodes` |  |   |  
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  | 
| 16x9 | `pictures` | string | ID for a 16x9 image. | 

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/seasons/{{seasonID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "id": "84559ddf12afd7734678f6ad4ce3d3f4",
    "resourceType": "seasons",
    "startTime": "2018-05-30T00:00:00Z",
    "name": "Enigmas Revelados, 4",
    "shortName": "Enigmas, 4",
    "language": "es",
    "regionIDs": null,
    "vod/episodeIDs": [
        "bcc6311c66e75b31e5a9707bc42c3b28",
        "0a9b166f4f7a20391b8ff180d4e14a6c"
    ],
    "showID": "SH029140770000"
}
```



***Responses:***


Status: Get a single season | Code: 200



```js
{
    "requestID": "5af3aee2-df0c-4647-b92e-2ccabd97f0f0",
    "timestamp": "2018-05-15T04:20:25.439950054Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "seasons": [
        {
            "id": "9252df7e0a2a36d8cee97ed6402dcc6e",
            "resourceType": "seasons",
            "startTime": "2014-11-08T00:00:00.000+00:00",
            "name": "Enigmas Revelados, 3",
            "shortName": "Enigmas, 3",
            "language": "es",
            "regionIDs": null,
            "vod/episodeIDs": [
                "b687dac2047ee8d7d407ce7755df56ef",
                "7e5b9c1b462e4a1722316eeef6f6a503",
                "8a77b8093abe95949c1b2c410e793169",
                "0adb6be571b60ae9aa92ee7973d87f49",
                "d6e238b650e64919e4fe121efe4d50fd",
                "c0981a718ea9b365d34e72e7b7f85c2a",
                "d035539cd46b48fdb40d651243290814",
                "c3959764ab06b42d137dc5ffaeae3126",
                "9fa76fc7474b273a806ccf39d78892d7"
            ]
        }
    ],
    "vod/episodes": [
        {
            "id": "b687dac2047ee8d7d407ce7755df56ef",
            "resourceType": "vod/episodes",
            "startTime": "2014-12-06T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "En 1874, el teniente coronel George envió a Custer en una misión de exploración en el área de Black Hills; según se informa, descubrió oro ahí; esto desencadenó una fiebre de oro en los colonos que inundan las tierras americanas nativas sagradas.",
            "shortDescription": "En 1874, el teniente coronel George envió a Custer en una misión de exploración en el área de Black Hills; según se informa, descubrió oro ahí; esto desencadenó una fiebre de oro en los colonos que inundan las tierras americanas nativas sagradas.",
            "pictureID": "ff3f449d1d47f53213d1509bb402a3b9",
            "pictures": {
                "2x3": "393f7772aac8158d79569fd877e76b79",
                "3x4": "882a8f7f107fd115fbb6afc38fa748a2",
                "4x3": "43c1c32456c9936f1dd7c2ba0835b386",
                "16x9": "ff3f449d1d47f53213d1509bb402a3b9"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 5,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "7e5b9c1b462e4a1722316eeef6f6a503",
            "resourceType": "vod/episodes",
            "startTime": "2014-12-27T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Antes de que los EE.UU. fueran independientes, las vas tierras de América eran para el primero que las reclamara.",
            "shortDescription": "Antes de que los EE.UU. fueran independientes, las vas tierras de América eran para el primero que las reclamara.",
            "pictureID": "dd35b986e89eceb82857321b6ccc2f3f",
            "pictures": {
                "2x3": "e6db83a844a29d66fdd0c82a0a8cbebe",
                "3x4": "68b6efb27cabd9a230eb8f06f854753d",
                "4x3": "517fbe9d7dff6c1c5ea2d7c391794f1b",
                "16x9": "dd35b986e89eceb82857321b6ccc2f3f"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 8,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "8a77b8093abe95949c1b2c410e793169",
            "resourceType": "vod/episodes",
            "startTime": "2015-01-03T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Scott Wolter investiga el paradero exacto de una roca de 1350 kilos oculta en el museo de historia de la ciudad de Chicago.",
            "shortDescription": "Scott Wolter investiga el paradero exacto de una roca de 1350 kilos oculta en el museo de historia de la ciudad de Chicago.",
            "pictureID": "c65794148aa117bc987d273ce67f0986",
            "pictures": {
                "2x3": "a2eda668cf9274ecbfbd24b16d3ff641",
                "3x4": "0789dba8182a38410af2385149019396",
                "4x3": "092930ca8b23b7cc5ec1498a7e94fd57",
                "16x9": "c65794148aa117bc987d273ce67f0986"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 9,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "0adb6be571b60ae9aa92ee7973d87f49",
            "resourceType": "vod/episodes",
            "startTime": "2014-11-08T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Un hombre de Alabama afirma poseer un documento sobre la propiedad de un terreno firmado por Davy Crockett veinte años después de que éste muriera.",
            "shortDescription": "Un hombre de Alabama afirma poseer un documento sobre la propiedad de un terreno firmado por Davy Crockett veinte años después de que éste muriera.",
            "pictureID": "c6e6029510175b51d6da3c26b63405fc",
            "pictures": {
                "2x3": "9f006aeaf83fcf8905fc07a105427322",
                "3x4": "72a22389712e2637745231e810084ac4",
                "4x3": "c72f444de3c91f6bda490465fbd6f3ad",
                "16x9": "c6e6029510175b51d6da3c26b63405fc"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 1,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "d6e238b650e64919e4fe121efe4d50fd",
            "resourceType": "vod/episodes",
            "startTime": "2014-11-15T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Los buscadores de tesoros han estado tratando de localizar la mina de oro perdida de Dutchman, que se rumorea está en algún lugar cerca de la Montaña Superstition en Arizona, durante más de un siglo.",
            "shortDescription": "Los buscadores de tesoros han estado tratando de localizar la mina de oro perdida de Dutchman, que se rumorea está en algún lugar cerca de la Montaña Superstition en Arizona, durante más de un siglo.",
            "pictureID": "f54d8206cd006f052c4da96d3f0d9f4e",
            "pictures": {
                "2x3": "f3d4b88ea2e403d4375e28e760c1db06",
                "3x4": "68a8cb22a1f8f383464242c3160dee94",
                "4x3": "f151362bc9714395f4564e0955e8990b",
                "16x9": "f54d8206cd006f052c4da96d3f0d9f4e"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 2,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "c0981a718ea9b365d34e72e7b7f85c2a",
            "resourceType": "vod/episodes",
            "startTime": "2014-11-29T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "De Scott recibe un paquete extraño que señala a un legendario tesoro escondido en el sur de Utah.",
            "shortDescription": "De Scott recibe un paquete extraño que señala a un legendario tesoro escondido en el sur de Utah.",
            "pictureID": "043073a077ca14832f4df02ff4b2e1ea",
            "pictures": {
                "2x3": "dcfefa9e71c968ec7d3d9c5465ce3cc6",
                "3x4": "ccee28accdf07d3745ed398c6355d0e6",
                "4x3": "8be32dc789878676d1ca15f99b60dab5",
                "16x9": "043073a077ca14832f4df02ff4b2e1ea"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 4,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "d035539cd46b48fdb40d651243290814",
            "resourceType": "vod/episodes",
            "startTime": "2014-11-22T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Una roca que tiene la leyenda de una marca dejada por un gigante, es también algo sagrado para la gente cherokee, pero otros dicen que no son símbolos nativos.",
            "shortDescription": "Una roca que tiene la leyenda de una marca dejada por un gigante, es también algo sagrado para la gente cherokee, pero otros dicen que no son símbolos nativos.",
            "pictureID": "b6e5121fa53e8bb15d31002ad04c82ba",
            "pictures": {
                "2x3": "298ff5300004fbf81caa591de29cc96f",
                "3x4": "8aca28a15d891a921abc8389e809e6a8",
                "4x3": "620afa5cb1eeb40cf1c3b5993dd1eff0",
                "16x9": "b6e5121fa53e8bb15d31002ad04c82ba"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 3,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "c3959764ab06b42d137dc5ffaeae3126",
            "resourceType": "vod/episodes",
            "startTime": "2015-01-10T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Scott se aventura a la ciudad de Nueva York después de enterarse de que un antiguo obelisco egipcio ubicado en Central Park está siendo restaurado.",
            "shortDescription": "Scott se aventura a la ciudad de Nueva York después de enterarse de que un antiguo obelisco egipcio ubicado en Central Park está siendo restaurado.",
            "pictureID": "03e721e7a5e72d8d5f58479212140d14",
            "pictures": {
                "2x3": "c025342973979a5ccf7fa47bdc4379c2",
                "3x4": "0d85f69ccfdbcf3438986099eb99984f",
                "4x3": "7a5782483b0426f92affadc3ea24974d",
                "16x9": "03e721e7a5e72d8d5f58479212140d14"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 10,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "9fa76fc7474b273a806ccf39d78892d7",
            "resourceType": "vod/episodes",
            "startTime": "2015-01-17T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Scott Wolter se dirige hacia su estado natal, Minnesota para investigar si Pie Grande es real.",
            "shortDescription": "Scott Wolter se dirige hacia su estado natal, Minnesota para investigar si Pie Grande es real.",
            "pictureID": "7a3873d6308026e664432fc82d3cb7a5",
            "pictures": {
                "2x3": "a956461a599bf2813d5a31c9a668e8b3",
                "3x4": "58962f97529b35fdc84551a19de9d47e",
                "4x3": "92c42ad536029b6ce2199e43f8c4e3e2",
                "16x9": "7a3873d6308026e664432fc82d3cb7a5"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 11,
            "duration": 0,
            "assetIDs": null
        }
    ]
}
```



### 2. Update a season


Updates the specified existing season entry for a show.

<br/>

<!-- This should probably be a PUT rather than a POST -->

##### Body Parameters

All fields are required unless otherwise indicated.

| Field  |  Type  | Description | 
|-------:|--------|-------------|
| id			| string | Unique ID for each season.  |
| resourceType	| string | "seasons"  | 
| startTime 	| string | A  timestamp for starting date of the season.  | 
| name			| string | Full name.  | 
| shortName 	| string | Shortened name.  | 
| language		| string | Two-letter code for the spoken language.  | 
| regionIDs 	| string | List of region IDs "whitelisted" for this season's episodes. | 
| vod/episodeIDs| string array| List of IDs for the episodes in this season.   | 
| showID		| string | Unique ID for the show that this season belongs to.  |

<br/>

##### Response object

| Field  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   
| timestamp |    | string | Generated log timestamp for this request.   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number | Number of items skipped from the start of the list; default = 0.
|||||
| `seasons` 	|   		|   	 |      |  
| id			| `seasons` | string | Unique ID for each season.  |  
| resourceType	| `seasons` | string | "seasons"  | 
| startTime 	| `seasons` | string | Timestamp for starting date of the season.  |  
| name			| `seasons` | string | Full season name.  |  
| shortName 	| `seasons` | string | Shortened season name.  |  
| language		| `seasons` | string | Two-letter code for the spoken language.  |  
| regionIDs 	| `seasons` | string | List of region IDs associated with this season. |
| vod/episodeIDs| `seasons` | string array| List of IDs for episodes that belong to this season.  | 
| episodeCount	| `seasons` | number | Number of episodes in this season as obtained from the metadata provider. |
|||||
| `vod/episodes` |   |   |      |  
| id			| `vod/episodes` |string | Unique ID for each episode asset.  |  
| resourceType	| `vod/episodes` | enum string | *vod/episodes*   | 
| startTime 	| `vod/episodes` | string | Timestamp for starting date of the episode.  |  
| endTime		| `vod/episodes` | string | Timestamp for ending date of the episode.  |  
| duration		| `vod/episodes` | number | Video duration in minutes.  |  
| name			| `vod/episodes` | string | Full episode name.  |  
| shortName 	| `vod/episodes` | string | Shortened episode name.   |  
| description	| `vod/episodes` | string | Full episode description.  |  
| shortDescription | `vod/episodes` | string | Short episode description.   |  
| language		| `vod/episodes` | string | Two-letter code for the spoken language.  |  
| pictureID 	| `vod/episodes` | string | ID for the standard image for this episode. |  
| ratings		| `vod/episodes` | string | Age-related ratings from boards and agencies.  | 
| ratingAdvisories | `vod/episodes` | string array | A list of content advisories; such as "Adult Situations", "Language", or "Violence" |
| regionIDs 	| `vod/episodes` | string | List of region IDs associated with this episode. |
| season		| `vod/episodes` | number | Season number that this episode belongs to.|   
| episode		| `vod/episodes` | number | Episode order number for this episode within its season.|   
| genreIDs		| `vod/episodes` | string array | List of genre IDs associated with this episode.| 
| assetIDs		| `vod/episodes` | string array | List of asset IDs associated with this episode.| 
|||||
| `pictures` | `vod/episodes` |  |   |  
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  | 
| 16x9 | `pictures` | string | ID for a 16x9 image. | 

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/seasons/{{seasonID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "id": "84559ddf12afd7734678f6ad4ce3d3f4",
    "resourceType": "seasons",
    "startTime": "2018-05-30T00:00:00Z",
    "name": "Enigmas Revelados, 4",
    "shortName": "Enigmas, 4",
    "language": "es",
    "regionIDs": null,
    "vod/episodeIDs": [
        "bcc6311c66e75b31e5a9707bc42c3b28",
        "0a9b166f4f7a20391b8ff180d4e14a6c"
    ],
    "showID": "SH029140770000"
}
```



***Responses:***


Status: Get a single season | Code: 200



```js
{
    "requestID": "5af3aee2-df0c-4647-b92e-2ccabd97f0f0",
    "timestamp": "2018-05-15T04:20:25.439950054Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "seasons": [
        {
            "id": "9252df7e0a2a36d8cee97ed6402dcc6e",
            "resourceType": "seasons",
            "startTime": "2014-11-08T00:00:00.000+00:00",
            "name": "Enigmas Revelados, 3",
            "shortName": "Enigmas, 3",
            "language": "es",
            "regionIDs": null,
            "vod/episodeIDs": [
                "b687dac2047ee8d7d407ce7755df56ef",
                "7e5b9c1b462e4a1722316eeef6f6a503",
                "8a77b8093abe95949c1b2c410e793169",
                "0adb6be571b60ae9aa92ee7973d87f49",
                "d6e238b650e64919e4fe121efe4d50fd",
                "c0981a718ea9b365d34e72e7b7f85c2a",
                "d035539cd46b48fdb40d651243290814",
                "c3959764ab06b42d137dc5ffaeae3126",
                "9fa76fc7474b273a806ccf39d78892d7"
            ]
        }
    ],
    "vod/episodes": [
        {
            "id": "b687dac2047ee8d7d407ce7755df56ef",
            "resourceType": "vod/episodes",
            "startTime": "2014-12-06T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "En 1874, el teniente coronel George envió a Custer en una misión de exploración en el área de Black Hills; según se informa, descubrió oro ahí; esto desencadenó una fiebre de oro en los colonos que inundan las tierras americanas nativas sagradas.",
            "shortDescription": "En 1874, el teniente coronel George envió a Custer en una misión de exploración en el área de Black Hills; según se informa, descubrió oro ahí; esto desencadenó una fiebre de oro en los colonos que inundan las tierras americanas nativas sagradas.",
            "pictureID": "ff3f449d1d47f53213d1509bb402a3b9",
            "pictures": {
                "2x3": "393f7772aac8158d79569fd877e76b79",
                "3x4": "882a8f7f107fd115fbb6afc38fa748a2",
                "4x3": "43c1c32456c9936f1dd7c2ba0835b386",
                "16x9": "ff3f449d1d47f53213d1509bb402a3b9"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 5,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "7e5b9c1b462e4a1722316eeef6f6a503",
            "resourceType": "vod/episodes",
            "startTime": "2014-12-27T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Antes de que los EE.UU. fueran independientes, las vas tierras de América eran para el primero que las reclamara.",
            "shortDescription": "Antes de que los EE.UU. fueran independientes, las vas tierras de América eran para el primero que las reclamara.",
            "pictureID": "dd35b986e89eceb82857321b6ccc2f3f",
            "pictures": {
                "2x3": "e6db83a844a29d66fdd0c82a0a8cbebe",
                "3x4": "68b6efb27cabd9a230eb8f06f854753d",
                "4x3": "517fbe9d7dff6c1c5ea2d7c391794f1b",
                "16x9": "dd35b986e89eceb82857321b6ccc2f3f"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 8,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "8a77b8093abe95949c1b2c410e793169",
            "resourceType": "vod/episodes",
            "startTime": "2015-01-03T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Scott Wolter investiga el paradero exacto de una roca de 1350 kilos oculta en el museo de historia de la ciudad de Chicago.",
            "shortDescription": "Scott Wolter investiga el paradero exacto de una roca de 1350 kilos oculta en el museo de historia de la ciudad de Chicago.",
            "pictureID": "c65794148aa117bc987d273ce67f0986",
            "pictures": {
                "2x3": "a2eda668cf9274ecbfbd24b16d3ff641",
                "3x4": "0789dba8182a38410af2385149019396",
                "4x3": "092930ca8b23b7cc5ec1498a7e94fd57",
                "16x9": "c65794148aa117bc987d273ce67f0986"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 9,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "0adb6be571b60ae9aa92ee7973d87f49",
            "resourceType": "vod/episodes",
            "startTime": "2014-11-08T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Un hombre de Alabama afirma poseer un documento sobre la propiedad de un terreno firmado por Davy Crockett veinte años después de que éste muriera.",
            "shortDescription": "Un hombre de Alabama afirma poseer un documento sobre la propiedad de un terreno firmado por Davy Crockett veinte años después de que éste muriera.",
            "pictureID": "c6e6029510175b51d6da3c26b63405fc",
            "pictures": {
                "2x3": "9f006aeaf83fcf8905fc07a105427322",
                "3x4": "72a22389712e2637745231e810084ac4",
                "4x3": "c72f444de3c91f6bda490465fbd6f3ad",
                "16x9": "c6e6029510175b51d6da3c26b63405fc"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 1,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "d6e238b650e64919e4fe121efe4d50fd",
            "resourceType": "vod/episodes",
            "startTime": "2014-11-15T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Los buscadores de tesoros han estado tratando de localizar la mina de oro perdida de Dutchman, que se rumorea está en algún lugar cerca de la Montaña Superstition en Arizona, durante más de un siglo.",
            "shortDescription": "Los buscadores de tesoros han estado tratando de localizar la mina de oro perdida de Dutchman, que se rumorea está en algún lugar cerca de la Montaña Superstition en Arizona, durante más de un siglo.",
            "pictureID": "f54d8206cd006f052c4da96d3f0d9f4e",
            "pictures": {
                "2x3": "f3d4b88ea2e403d4375e28e760c1db06",
                "3x4": "68a8cb22a1f8f383464242c3160dee94",
                "4x3": "f151362bc9714395f4564e0955e8990b",
                "16x9": "f54d8206cd006f052c4da96d3f0d9f4e"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 2,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "c0981a718ea9b365d34e72e7b7f85c2a",
            "resourceType": "vod/episodes",
            "startTime": "2014-11-29T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "De Scott recibe un paquete extraño que señala a un legendario tesoro escondido en el sur de Utah.",
            "shortDescription": "De Scott recibe un paquete extraño que señala a un legendario tesoro escondido en el sur de Utah.",
            "pictureID": "043073a077ca14832f4df02ff4b2e1ea",
            "pictures": {
                "2x3": "dcfefa9e71c968ec7d3d9c5465ce3cc6",
                "3x4": "ccee28accdf07d3745ed398c6355d0e6",
                "4x3": "8be32dc789878676d1ca15f99b60dab5",
                "16x9": "043073a077ca14832f4df02ff4b2e1ea"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 4,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "d035539cd46b48fdb40d651243290814",
            "resourceType": "vod/episodes",
            "startTime": "2014-11-22T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Una roca que tiene la leyenda de una marca dejada por un gigante, es también algo sagrado para la gente cherokee, pero otros dicen que no son símbolos nativos.",
            "shortDescription": "Una roca que tiene la leyenda de una marca dejada por un gigante, es también algo sagrado para la gente cherokee, pero otros dicen que no son símbolos nativos.",
            "pictureID": "b6e5121fa53e8bb15d31002ad04c82ba",
            "pictures": {
                "2x3": "298ff5300004fbf81caa591de29cc96f",
                "3x4": "8aca28a15d891a921abc8389e809e6a8",
                "4x3": "620afa5cb1eeb40cf1c3b5993dd1eff0",
                "16x9": "b6e5121fa53e8bb15d31002ad04c82ba"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 3,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "c3959764ab06b42d137dc5ffaeae3126",
            "resourceType": "vod/episodes",
            "startTime": "2015-01-10T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Scott se aventura a la ciudad de Nueva York después de enterarse de que un antiguo obelisco egipcio ubicado en Central Park está siendo restaurado.",
            "shortDescription": "Scott se aventura a la ciudad de Nueva York después de enterarse de que un antiguo obelisco egipcio ubicado en Central Park está siendo restaurado.",
            "pictureID": "03e721e7a5e72d8d5f58479212140d14",
            "pictures": {
                "2x3": "c025342973979a5ccf7fa47bdc4379c2",
                "3x4": "0d85f69ccfdbcf3438986099eb99984f",
                "4x3": "7a5782483b0426f92affadc3ea24974d",
                "16x9": "03e721e7a5e72d8d5f58479212140d14"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 10,
            "duration": 0,
            "assetIDs": null
        },
        {
            "id": "9fa76fc7474b273a806ccf39d78892d7",
            "resourceType": "vod/episodes",
            "startTime": "2015-01-17T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Scott Wolter se dirige hacia su estado natal, Minnesota para investigar si Pie Grande es real.",
            "shortDescription": "Scott Wolter se dirige hacia su estado natal, Minnesota para investigar si Pie Grande es real.",
            "pictureID": "7a3873d6308026e664432fc82d3cb7a5",
            "pictures": {
                "2x3": "a956461a599bf2813d5a31c9a668e8b3",
                "3x4": "58962f97529b35fdc84551a19de9d47e",
                "4x3": "92c42ad536029b6ce2199e43f8c4e3e2",
                "16x9": "7a3873d6308026e664432fc82d3cb7a5"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Australian Classification Board}/{Parental Guidance}/{PG}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{Livre}/{L}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 3,
            "episode": 11,
            "duration": 0,
            "assetIDs": null
        }
    ]
}
```



### 3. Retrieve a season


Returns information for the specified season.

<br/>

<!--  Original endpoint: {{OCMServer}}/ocm/v2/seasons/a2a975b6759a787fd16343b6f1eb438a?language=*&include=vod/episodes -->

##### PATH PARAMETERS
| Label   | Type   | Required | Description | 
|--------:|--------|----------|-------------|
|seasonID | string | required | ID for the requested season. | 

<br/>

##### Response object

| Field  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   
| timestamp |    | string | Generated log timestamp for this request.   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number | Number of items skipped from the start of the list; default = 0.
|||||
| `seasons` 	|   		|   	 |      |  
| id			| `seasons` | string | Unique ID for each season.  |  
| resourceType	| `seasons` | string | "seasons"  | 
| startTime 	| `seasons` | string | Timestamp for starting date of the season.  |  
| name			| `seasons` | string | Full season name.  |  
| shortName 	| `seasons` | string | Shortened season name.  |  
| language		| `seasons` | string | Two-letter code for the spoken language.  |  
| regionIDs 	| `seasons` | string | List of region IDs associated with this season. |
| vod/episodeIDs| `seasons` | string array| List of IDs for episodes that belong to this season.  | 
| episodeCount	| `seasons` | number | Number of episodes in this season as obtained from the metadata provider. |
|||||
| `vod/episodes` |   |   |      |  
| id			| `vod/episodes` |string | Unique ID for each episode asset.  |  
| resourceType	| `vod/episodes` | enum string | *vod/episodes*   | 
| startTime 	| `vod/episodes` | string | Timestamp for starting date of the episode.  |  
| endTime		| `vod/episodes` | string | Timestamp for ending date of the episode.  |  
| duration		| `vod/episodes` | number | Video duration in minutes.  |  
| name			| `vod/episodes` | string | Full episode name.  |  
| shortName 	| `vod/episodes` | string | Shortened episode name.   |  
| description	| `vod/episodes` | string | Full episode description.  |  
| shortDescription | `vod/episodes` | string | Short episode description.   |  
| language		| `vod/episodes` | string | Two-letter code for the spoken language.  |  
| pictureID 	| `vod/episodes` | string | ID for the standard image for this episode. |  
| ratings		| `vod/episodes` | string | Age-related ratings from boards and agencies.  | 
| ratingAdvisories | `vod/episodes` | string array | A list of content advisories; such as "Adult Situations", "Language", or "Violence" |
| regionIDs 	| `vod/episodes` | string | List of region IDs associated with this episode. |
| season		| `vod/episodes` | number | Season number that this episode belongs to.|   
| episode		| `vod/episodes` | number | Episode order number for this episode within its season.|   
| genreIDs		| `vod/episodes` | string array | List of genre IDs associated with this episode.| 
| assetIDs		| `vod/episodes` | string array | List of asset IDs associated with this episode.| 
|||||
| `pictures` | `vod/episodes` |  |   |  
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  | 
| 16x9 | `pictures` | string | ID for a 16x9 image. | 

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/seasons/{{seasonID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | vod/episodes | Includes information for each specific episode. |



***Responses:***


Status: Get a single season | Code: 200



```js
{
    "requestID": "dce9eb4f-1295-4b72-aabb-8901dc40531d",
    "timestamp": "2018-06-07T13:01:43.440076662Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "seasons": [
        {
            "id": "9252df7e0a2a36d8cee97ed6402dcc6e",
            "resourceType": "seasons",
            "startTime": "2014-11-08T00:00:00.000+00:00",
            "name": "Enigmas Revelados, 3",
            "shortName": "Enigmas, 3",
            "language": "es",
            "regionIDs": null,
            "vod/episodeIDs": [
                "b687dac2047ee8d7d407ce7755df56ef",
                "7e5b9c1b462e4a1722316eeef6f6a503",
                "8a77b8093abe95949c1b2c410e793169",
                "0adb6be571b60ae9aa92ee7973d87f49",
                "d6e238b650e64919e4fe121efe4d50fd",
                "c0981a718ea9b365d34e72e7b7f85c2a",
                "d035539cd46b48fdb40d651243290814",
                "c3959764ab06b42d137dc5ffaeae3126",
                "9fa76fc7474b273a806ccf39d78892d7"
            ],
            "showID": "SH029140770000"
        }
    ]
}
```



### 4. Patch a season


Patches the specified EPG competition resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the season to be updated. |

<br>

##### Body Parameters

| Field  |  Type  | Description | 
|-------:|--------|-------------|
| startTime | string, format=date-time allows empty | Start time in ISO-8601 timestamp format.  | 
| name | string, min=1 max=512 | Full name for the resource. |
| shortName | string, max=512 | Shortened name for the resource. |
| language | string, min=2 max=2 | Two-letter code for the spoken language.  |
| regionIDs | string list, allows null | List of region IDs associated with this resource. | 
| vod/episodeIDs| string list, allows null | List of IDs for the episodes in this season.   | 
| showID | string, min=1 max=256 | The ID of the show this season belongs to. |
| seasonNumber  | number | The season number. |
| episodeCount  | number | The number of episodes in this season. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/seasons/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "startTime": "",
    "name": "Rome, 2",
    "shortName": "Rome, 2",
    "language": "en",
    "regionIDs": [
        "f917cff6-025a-4917-84d6-fb686697d93c",
        "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6",
        "2e167237-c7bb-423b-b606-c31115adb1da",
        "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
        "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
        "141a53b6-af6f-4092-ba1f-c289659310f2",
        "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
        "f5881a70-c07e-11e8-b4bb-adc8f08569d4"
    ],
    "vod/episodeIDs": [
        "df2a0dfa-1fb5-4b6b-8780-cde5784dbd01",
        "9e431170-d5d8-42ee-b07f-77641c745b00",
        "8cfa1512-ab78-4f55-995b-7e48e6d34274",
        "ffb38056-bc8f-483d-b772-ff3d2ba8022f"
    ],
    "episodeCount": 4
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "a01a2738-164b-4d10-9a48-f331ec4a4a0e",
    "timestamp": "2020-03-24T00:24:16.787589Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "seasons": [
        {
            "id": "73a0e23c-3d52-4a3d-a17f-2113139de1d6",
            "resourceType": "seasons",
            "publishStart": "2019-07-18T10:27:14.139Z",
            "published": true,
            "created": "0001-01-01T00:00:00Z",
            "updated": "2020-03-24T00:24:16.784Z",
            "contentLock": false,
            "startTime": "",
            "name": "Rome, 2",
            "shortName": "Rome, 2",
            "language": "en",
            "regionIDs": [
                "f917cff6-025a-4917-84d6-fb686697d93c",
                "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6",
                "2e167237-c7bb-423b-b606-c31115adb1da",
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "141a53b6-af6f-4092-ba1f-c289659310f2",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
                "f5881a70-c07e-11e8-b4bb-adc8f08569d4"
            ],
            "vod/episodeIDs": [
                "df2a0dfa-1fb5-4b6b-8780-cde5784dbd01",
                "9e431170-d5d8-42ee-b07f-77641c745b00",
                "8cfa1512-ab78-4f55-995b-7e48e6d34274",
                "ffb38056-bc8f-483d-b772-ff3d2ba8022f"
            ],
            "showID": "2325f5a3-b3db-4b94-8396-0b8092d5aa7e",
            "seasonNumber": 2,
            "episodeCount": 4
        }
    ]
}
```



## v2/serviceProviders



### 1. Get serviceProviders list



***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/serviceProviders
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Retrieve team game from the on-demand catalog | Code: 200



```js
{
    "requestID": "884a6319-d138-4af4-84a4-d525d5d0880b",
    "timestamp": "2018-05-15T04:28:09.909810814Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "vod/teamCompetitions": [
        {
            "id": "3df321e0d555329f75859682a4f18485",
            "resourceType": "vod/competitions",
            "name": "Fútbol Copa Libertadores",
            "shortName": "Fútbol",
            "description": "Jornada 2 del Grupo F de la Copa Conmebol Libertadores 2018. Santos, viene de caer de visitante 2-0 ante Real Garcilaso, recibe a Nacional, que igualó sin goles contra Estudiantes en Uruguay. Desde el Estadio Urbano Caldeira.",
            "shortDescription": "Jornada 2 del Grupo F de la Copa Conmebol Libertadores 2018. Santos, viene de caer de visitante 2-0 ante Real Garcilaso, recibe a Nacional, que igualó sin goles contra Estudiantes en Uruguay. Desde el Estadio Urbano Caldeira.",
            "duration": 0,
            "genreIDs": null,
            "language": "es",
            "ratings": null,
            "ratingAdvisories": null,
            "regionIDs": null,
            "pictures": {
                "2x3": null,
                "3x4": null,
                "4x3": null,
                "16x9": null
            },
            "pictureID": "",
            "sportID": "d670cf71cb7709020618a03c5208c84e",
            "sportName": "Soccer",
            "tournamentID": "",
            "tournamentName": "Fútbol Copa Libertadores",
            "primaryTeamID": "699f82255ddd75f675c4128a52e3054d",
            "primaryTeamName": "",
            "primaryTeamPictureID": "",
            "secondaryTeamID": "ff6717e473e80bf698bf2f50e3621595",
            "secondaryTeamName": "Club Nacional",
            "secondaryTeamPictureID": "",
            "assetIDs": null
        }
    ]
}
```



### 2. Get serviceProviders by ID *



***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/serviceProviders/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 3. Create serviceProviders



***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/serviceProviders/
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
    "resourceType": "serviceProviders",
    "publishStart": "0001-01-01T00:00:00Z",
    "publishEnd": "0001-01-01T00:00:00Z",
    "published": true,
    "name": "FOXPLAY+",
    "provider": "adi",
    "providerID": "foxplay+pa.com"
}
```



### 4. Delete serviceProviders


Deletes the serviceProviders for the specified IDs. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|serviceProviderID	|string		|required	|List of IDs for the targeted serviceProviders. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified serviceProviders.|
|404		|1040	|*Not Found*: No matching service provider IDs found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/serviceProviders/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 5. Update serviceProviders by ID *



***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/serviceProviders/{{id}}
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
    "id": "100418ababf07546859bd14ee58d7692",
    "resourceType": "serviceProviders",
    "publishStart": "0001-01-01T00:00:00Z",
    "publishEnd": "0001-01-01T00:00:00Z",
    "published": true,
    "name": "FOXPLAY+",
    "provider": "adi",
    "providerID": "foxplay+pa.com"
}
```



### 6. Patch service provider


Patches the specified service provider resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters

|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the service provider to be updated. |

<br>

##### Body Parameters

| Field  |  Type  | Description |
|------:|--------|-------------|
| name | string | |
| provider | string | |
| providerID | string | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/serviceProviders/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "name": "WB STUDIOS",
    "providerID": "warnerbrospa.com"
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "a32a6cf8-0a24-48a7-ad09-96b48c9572dd",
    "timestamp": "2020-03-25T19:16:06.318847Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "serviceProviders": [
        {
            "id": "a195f8956eb2f960b443792010eda56c",
            "resourceType": "serviceProviders",
            "publishStart": "2019-03-09T17:30:19.977Z",
            "published": true,
            "created": "2019-03-09T17:30:20.973Z",
            "updated": "2020-03-25T19:16:06.315Z",
            "contentLock": false,
            "name": "WB STUDIOS",
            "provider": "adi",
            "providerID": "warnerbrospa.com"
        }
    ]
}
```



### 7. Get serviceProviderCategories list



***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/serviceProviderCategories
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Responses:***


Status: Retrieve team game from the on-demand catalog | Code: 200



```js
{
    "requestID": "884a6319-d138-4af4-84a4-d525d5d0880b",
    "timestamp": "2018-05-15T04:28:09.909810814Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "vod/teamCompetitions": [
        {
            "id": "3df321e0d555329f75859682a4f18485",
            "resourceType": "vod/competitions",
            "name": "Fútbol Copa Libertadores",
            "shortName": "Fútbol",
            "description": "Jornada 2 del Grupo F de la Copa Conmebol Libertadores 2018. Santos, viene de caer de visitante 2-0 ante Real Garcilaso, recibe a Nacional, que igualó sin goles contra Estudiantes en Uruguay. Desde el Estadio Urbano Caldeira.",
            "shortDescription": "Jornada 2 del Grupo F de la Copa Conmebol Libertadores 2018. Santos, viene de caer de visitante 2-0 ante Real Garcilaso, recibe a Nacional, que igualó sin goles contra Estudiantes en Uruguay. Desde el Estadio Urbano Caldeira.",
            "duration": 0,
            "genreIDs": null,
            "language": "es",
            "ratings": null,
            "ratingAdvisories": null,
            "regionIDs": null,
            "pictures": {
                "2x3": null,
                "3x4": null,
                "4x3": null,
                "16x9": null
            },
            "pictureID": "",
            "sportID": "d670cf71cb7709020618a03c5208c84e",
            "sportName": "Soccer",
            "tournamentID": "",
            "tournamentName": "Fútbol Copa Libertadores",
            "primaryTeamID": "699f82255ddd75f675c4128a52e3054d",
            "primaryTeamName": "",
            "primaryTeamPictureID": "",
            "secondaryTeamID": "ff6717e473e80bf698bf2f50e3621595",
            "secondaryTeamName": "Club Nacional",
            "secondaryTeamPictureID": "",
            "assetIDs": null
        }
    ]
}
```



### 8. Get serviceProviderCategories by ID



***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/serviceProviderCategories/19bd58e742d96b72ac6c36a3e909c3ea
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 9. Create serviceProviderCategories



***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/serviceProviderCategories/
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
    "resourceType": "serviceProviderCategories",
    "publishStart": "0001-01-01T00:00:00Z",
    "publishEnd": "0001-01-01T00:00:00Z",
    "published": true,
    "name": "FOXPLAY+: FOXPLAY+_Subscription_HD_PA",
    "provider": "adi",
    "providerID": "FOXPLAY+_Subscription_HD_PA"
}
```



### 10. Update serviceProviderCategories by ID



***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/serviceProviderCategories/c8f4eedefecb5edcab951666524242d8
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
    "id": "c8f4eedefecb5edcab951666524242d8",
    "resourceType": "serviceProviderCategories",
    "publishStart": "0001-01-01T00:00:00Z",
    "publishEnd": "0001-01-01T00:00:00Z",
    "published": true,
    "name": "FOXPLAY+: FOXPLAY+_Subscription_HD_PA",
    "provider": "adi",
    "providerID": "FOXPLAY+_Subscription_HD_PA"
}
```



### 11. Delete serviceProviderCategories


Deletes the serviceProviderCategories for the specified IDs. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|serviceProviderCategoryID	|string		|required	|List of IDs for the targeted serviceProviderCategories. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified serviceProviderCategories.|
|404		|1040	|*Not Found*: No matching service provider category IDs found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/serviceProviderCategories/19bd58e742d96b72ac6c36a3e909c3ea
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 12. Patch service provider category


Patches the specified service provider category resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters

|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the service provider category to be updated. |

<br>

##### Body Parameters

| Field  |  Type  | Description |
|------:|--------|-------------|
| name | string | |
| provider | string | |
| providerID | string | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/serviceProviderCategories/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "name": "VIACOM: Viacom_Nickelodeon_FOD_HD_PA",
    "providerID": "Viacom_Nickelodeon_FOD_HD_PA"
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "6de1d826-da1f-44c8-928b-61b72d4c34af",
    "timestamp": "2020-03-25T19:19:12.173088Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "serviceProviderCategories": [
        {
            "id": "14681cad6afa0e6f0a85e15392f7599c",
            "resourceType": "serviceProviderCategories",
            "publishStart": "2019-03-09T17:31:00.738Z",
            "published": true,
            "created": "2019-03-09T17:31:01.75Z",
            "updated": "2020-03-25T19:19:12.17Z",
            "contentLock": false,
            "name": "VIACOM: Viacom_Nickelodeon_FOD_HD_PA",
            "provider": "adi",
            "providerID": "Viacom_Nickelodeon_FOD_HD_PA"
        }
    ]
}
```



### 13. Retrieve whitelisted resources


Retrieves the list of existing resources with defined whitelisted regions.

<br/>

##### Response object

| Name  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| `whitelisted` |   |   |      |  |
| id | `whitelisted` |string | Unique ID for each asset.  |  |
| resourceType | `whitelisted` | enum string | "whitelisted" | |
| publishStart	| `whitelisted` | string | When this content became/becomes available to subscribers. A timestamp in ISO 8601 format. | |
| publishEnd	| `whitelisted` | string | When this content became/becomes unavailable to subscribers. A timestamp in ISO 8601 format. | |
| published 	| `whitelisted` | boolean | Is the asset publicly available? | |
| created		| `whitelisted` | string | When this content was created. A timestamp in ISO 8601 format. | |
| updated		| `whitelisted` | string | When this content was last upated. A timestamp in ISO 8601 format. | |
| contentLock	| `whitelisted` | boolean | Is the asset content locked to prevent changes? | |
| regions | `whitelisted` | string list | A list of region UIDs retrieved from and matched to defined regions. |
| serviceProviderIDs | `whitelisted` | string array | List of service provider IDs. |   |
| adiProviderName | `whitelisted` | string | The service provider name. |   |
| adiServiceCategory | `whitelisted` | string | The service provider category. | |

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/whitelisted
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



### 14. Create new whitelisted resource


Creates a new whitelisted resource for the specified regions.

<br/>

##### Body Parameters

| Name  	|  Type  | Description | 
|----------:|--------|-------------|
| resourceType		| enum string | _Required_. Value must be set to "whitelisted". |
| regions			| string list | List of region UIDs retrieved from and matched to defined regions. |
| serviceProviderIDs| string | List of IDs for the service provider and service provider category. |

<br/>

##### Response object

| Name  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| `whitelisted` |   |   |      |  |
| id | `whitelisted` |string | Unique ID for each asset.  |  |
| resourceType | `whitelisted` | enum string | "whitelisted" | |
| publishStart	| `whitelisted` | string | When this content became/becomes available to subscribers. A timestamp in ISO 8601 format. | |
| publishEnd	| `whitelisted` | string | When this content became/becomes unavailable to subscribers. A timestamp in ISO 8601 format. | |
| published 	| `whitelisted` | boolean | Is the asset publicly available? | |
| created		| `whitelisted` | string | When this content was created. A timestamp in ISO 8601 format. | |
| updated		| `whitelisted` | string | When this content was last upated. A timestamp in ISO 8601 format. | |
| contentLock	| `whitelisted` | boolean | Is the asset content locked to prevent changes? | |
| regions | `whitelisted` | string list | A list of region UIDs retrieved from and matched to defined regions. |
| serviceProviderIDs | `whitelisted` | string array | List of service provider IDs. |   |
| adiProviderName | `whitelisted` | string | The service provider name. |   |
| adiServiceCategory | `whitelisted` | string | The service provider category. | |

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/whitelisted
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
    "resourceType": "whitelisted",
    "regions": [
        "{{regionID_1}}",
        "{{regionID_2}}"
    ],
    "serviceProviderIDs": [
        "{{serviceProviderID}}",
        "{{serviceProviderCategoryID}}"
    ]
}
```



### 15. Update whitelisted resource


Updates the specified whitelisted resource with the indicated regions and service provider IDs.

<!--	Original hardcoded endpoint: {{OCMServer}}/ocm/v2/whitelisted/deaa15d4de635c3a57776bc133cc37b8	-->

<br/>

##### Path Parameters
|Name|Data type|Required|Description|
|---|---|---|---|
|assetID|string|required|ID for the existing whitelisted asset.|

<br/>

##### Body Parameters

| Name  	|  Type  | Description | 
|----------:|--------|-------------|
| resourceType		| enum string | _Required_. Value must be set to "whitelisted". |
| regions			| string list | List of region UIDs retrieved from and matched to defined regions. |
| serviceProviderIDs| string | List of IDs for the service provider and service provider category. |

<br/>

##### Response object

| Name  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| `whitelisted` |   |   |      |  |
| id | `whitelisted` |string | Unique ID for each asset.  |  |
| resourceType | `whitelisted` | enum string | "whitelisted" | |
| publishStart	| `whitelisted` | string | When this content became/becomes available to subscribers. A timestamp in ISO 8601 format. | |
| publishEnd	| `whitelisted` | string | When this content became/becomes unavailable to subscribers. A timestamp in ISO 8601 format. | |
| published 	| `whitelisted` | boolean | Is the asset publicly available? | |
| created		| `whitelisted` | string | When this content was created. A timestamp in ISO 8601 format. | |
| updated		| `whitelisted` | string | When this content was last upated. A timestamp in ISO 8601 format. | |
| contentLock	| `whitelisted` | boolean | Is the asset content locked to prevent changes? | |
| regions | `whitelisted` | string list | A list of region UIDs retrieved from and matched to defined regions. |
| serviceProviderIDs | `whitelisted` | string array | List of service provider IDs. |   |
| adiProviderName | `whitelisted` | string | The service provider name. |   |
| adiServiceCategory | `whitelisted` | string | The service provider category. | |

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/whitelisted/{{assetID}}
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
    "resourceType": "whitelisted",
    "regions": [
        "{{regionID_1}}",
        "{{regionID_2}}"
    ],
    "serviceProviderIDs": [
        "{{serviceProviderID}}",
        "{{serviceProviderCategoryID}}"
    ]
}
```



### 16. Patch whitelisted


Patches the specified whitelisted resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters

|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the whitelisted resource to be updated. |

<br>

##### Body Parameters

| Name  	|  Type  | Description | 
|----------:|--------|-------------|
| regions			| string list | List of region UIDs retrieved from and matched to defined regions. |
| serviceProviderIDs| string | List of IDs for the service provider and service provider category. |
| adiProviderName | | |
| adiServiceCategory | | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/whitelisted/{{id}}
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
    "regions": [
        "f917cff6-025a-4917-84d6-fb686697d93c"
    ],
    "serviceProviderIDs": [
        "ede22431a99d3c8fba7a85022899fc98",
        "7689d99f039bcd318281306b39d51cf0"
    ]
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "3206ffb5-a3b5-4d49-8fcd-fe53c5d92e62",
    "timestamp": "2020-03-25T20:01:48.03645Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "whitelisted": [
        {
            "id": "bdb775a3816194164ee33054fede7d55",
            "resourceType": "whitelisted",
            "publishStart": "2019-03-09T17:31:13.745Z",
            "published": true,
            "created": "2019-03-09T17:31:13.921Z",
            "updated": "2020-03-25T20:01:48.033Z",
            "contentLock": false,
            "regions": [
                "f917cff6-025a-4917-84d6-fb686697d93c"
            ],
            "serviceProviderIDs": [
                "ede22431a99d3c8fba7a85022899fc98",
                "7689d99f039bcd318281306b39d51cf0"
            ],
            "adiProviderName": "",
            "adiServiceCategory": ""
        }
    ]
}
```



## v2/shows



### 1. Create a show


Creates a new EPG show entry.

<br/>

##### Request object

| Name  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| id	| |string | Unique ID for the requested show.  |  |
| resourceType | | enum string | "shows" | |
| startTime | | string | Timestamp starting date for the show.   |  |
| endTime	| | string | Timestamp ending date for the show.  |  |
| duration	| | number | Show duration in minutes.  |  |
| name		| | string | Full show name.  |
| shortName 	| | string | Shortened show name. |
| description	| | string | Full show description.  |
| shortDescription | | string | Short show description. |
| language| | string | Two-letter code for the spoken language.  |  |
| ratings | | string | Age-related ratings from boards and agencies. 
| ratingAdvisories | | string list | A list of content advisories, such as "Adult Situations", "Language", or "Violence" |
| seasons	| | number | Number of seasons for the show as obtained from the metadata provider. Value may be *0* or more.|   |
| seasonIDs | | string list | List of season IDs for this show.| |
| genreIDs	| | string | List of genre IDs associated with this show.| |
| regionIDs | | string | List of region IDs associated with this show.| |
| pictureID | | string | ID for the show's standard image. |  | 
||||||
| `pictures` | |  |   |  |
| 2x3  | `pictures` | string | ID for a 2x3 image. |  
| 3x4  | `pictures` | string | ID for a 3x4 image. | 
| 4x3  | `pictures` | string | ID for a 4x3 image. |   
| 16x9 | `pictures` | string | ID for a 16x9 image.| 
| publishStart |  | string | First date that this content is visible to end users. | Timestamp in ISO 8601 format. |
| publishEnd |  | string | Last date that this content is visible to end users. | Timestamp ISO 8601 format. |

<br/>

##### Response object
| Field  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata`|	 | object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| `shows`	|   | object array  |    | 
| id			| `shows` | string | Unique ID for each season.  |  |
| resourceType	| `shows` | string | "shows" | |
| startTime 	| `shows` | string | Timestamp starting date for the season.  |  |
| endTime 		| `shows` | string | Timestamp ending date for the season.  |  |
| name			| `shows` | string | Full season name.  |
| shortName 	| `shows` | string | Short season name.  |
| description	| `shows` | string | Full show description.  |
| shortDescription | `shows` | string | Short show description. |
||||||
| pictureID |`shows` | string | ID for the show's standard image. |  | 
| `pictures` | `shows` |  |   |  |
| 2x3  | `pictures` | string | ID for a 2x3 image. |  
| 3x4  | `pictures` | string | ID for a 3x4 image. | 
| 4x3  | `pictures` | string | ID for a 4x3 image. |   
| 16x9 | `pictures` | string | ID for a 16x9 image.| 
| genreIDs	| `shows` | string | List of genre IDs associated with this show.| |
| language	| `shows` | string | Two-letter code for the spoken language.  |  |
| ratings	| `shows`  | string | Age-related ratings from boards and agencies. 
| ratingAdvisories | `shows` | string list | A list of content advisories, such as "Adult Situations", "Language", or "Violence" |
| regionIDs | `shows` | string | List of region IDs associated with the season. |
| seasons	|`shows` | number | Number of seasons for the show as obtained from the metadata provider. Value may be *0* or more.|   |
| duration	|`shows` | number | Show duration in minutes.  |  |
| seasonIDs |`shows`| string list | List of season IDs for this show.| |
||||||
| `seasons`	|   | object array  |    | 
| id			| `seasons` | string | Unique ID for each season.  |  |
| resourceType	| `seasons` | string | "seasons" | |
| startTime 	| `seasons` | string | Timestamp starting date for the season.  |  |
| name			| `seasons` | string | Full season name.  |
| shortName 	| `seasons` | string | Short season name.  |
| language		| `seasons` | string | Two-letter code for the spoken language.  |  |
| regionIDs 	| `seasons` | string | List of region IDs associated with the season. |
| vod/episodeIDs| `seasons` | string list| List of IDs for the episodes in this season.  |
| episodeCount	| `seasons` | number | Number of episodes in this season as obtained from the metadata provider. |


<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/shows
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "id": "08b93632288c3c1cc894c365ad090290",
    "resourceType": "shows",
    "startTime": "2011-11-11T00:00:00Z",
    "endTime": "",
    "name": "Enigmas Revelados",
    "shortName": "Enigmas",
    "description": "Estados Unidos está lleno de secretos arqueológicos enterrados en la tierra! En esta serie, el geólogo forense Scott Wolter -- considerado un Indiana Jones de la vida real por algunos -- viaja por el país para descubrir algunos de los tesoros ocultos y revelar la historia asociada con ellos, descubriendo en el proceso que hay muchos estadounidenses que no saben sobre el pasado del país, y la historia que la gente sí sabe, no siempre cuenta toda la historia. Símbolos antiguos, reliquias religiosas y otros artefactos que desentierra Wolter indican que varias civilizaciones han dejado su huella en la nación.",
    "shortDescription": "",
    "pictureID": "e3129c65aeb1a349bb356100329c321c",
    "pictures": {
        "2x3": null,
        "3x4": "a3ba485ee790a67254e090d0e51f6667",
        "4x3": "40c7d64cf9e06fbcd9fcd664e0a4a748",
        "16x9": "e3129c65aeb1a349bb356100329c321c"
    },
    "genreIDs": null,
    "language": "es",
    "ratings": [
        "USA Parental Rating//TVG",
        "Canadian Parental Rating//G",
        "Régie du cinéma/General/G",
        "Australian Classification Board/Parental Guidance/PG"
    ],
    "ratingAdvisories": null,
    "regionIDs": null,
    "seasons": 3,
    "duration": 0,
    "seasonIDs": [
        "7515190294fda190a4d925d77d1a640c",
        "84559ddf12afd7734678f6ad4ce3d3f1",
        "9252df7e0a2a36d8cee97ed6402dcc6e"
    ]
}
```



***Responses:***


Status: Get a single show | Code: 200



```js
{"requestID":"a788d1ca-fff1-439d-909d-ffeeb63fe114","timestamp":"2018-05-15T08:28:28.868833009Z","metadata":{"count":1,"totalCount":1,"offset":0},"shows":[{"id":"08b93632288c3c1cc894c365ad090290","resourceType":"shows","startTime":"2012-12-21T00:00:00.000+00:00","endTime":"","name":"Enigmas Revelados","shortName":"Enigmas","description":"Estados Unidos está lleno de secretos arqueológicos enterrados en la tierra. En esta serie, el geólogo forense Scott Wolter -- considerado un Indiana Jones de la vida real por algunos -- viaja por el país para descubrir algunos de los tesoros ocultos y revelar la historia asociada con ellos, descubriendo en el proceso que hay muchos estadounidenses que no saben sobre el pasado del país, y la historia que la gente sí sabe, no siempre cuenta toda la historia. Símbolos antiguos, reliquias religiosas y otros artefactos que desentierra Wolter indican que varias civilizaciones han dejado su huella en la nación.","shortDescription":"","pictureID":"350ccfe50b68f778b89fdca38cea8e63","pictures":{"2x3":"e0538a576f85fceb07dd9ce27c944bfb","3x4":"9d9120c5d25989d7511e070ee2748898","4x3":"51917154b9c8c6f791a90b82c7fdae11","16x9":"350ccfe50b68f778b89fdca38cea8e63"},"genreIDs":null,"language":"es","ratings":["{USA Parental Rating}/{}/{TVG}","{Canadian Parental Rating}/{}/{G}","{Régie du cinéma}/{General}/{G}","{Australian Classification Board}/{Parental Guidance}/{PG}"],"ratingAdvisories":null,"regionIDs":null,"seasons":3,"duration":0,"seasonIDs":["7515190294fda190a4d925d77d1a640c","84559ddf12afd7734678f6ad4ce3d3f1","9252df7e0a2a36d8cee97ed6402dcc6e"]}],"seasons":[{"id":"7515190294fda190a4d925d77d1a640c","resourceType":"seasons","startTime":"2012-12-21T00:00:00.000+00:00","name":"Enigmas Revelados, 1","shortName":"Enigmas, 1","language":"es","regionIDs":null,"vod/episodeIDs":null},{"id":"84559ddf12afd7734678f6ad4ce3d3f1","resourceType":"seasons","startTime":"2013-11-30T00:00:00.000+00:00","name":"Enigmas Revelados, 2","shortName":"Enigmas, 2","language":"es","regionIDs":null,"vod/episodeIDs":null},{"id":"9252df7e0a2a36d8cee97ed6402dcc6e","resourceType":"seasons","startTime":"2014-11-08T00:00:00.000+00:00","name":"Enigmas Revelados, 3","shortName":"Enigmas, 3","language":"es","regionIDs":null,"vod/episodeIDs":null}]}
```



### 2. Update a show


Updates the specified EPG show entry.

<br/>

##### Request object

| Name  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| id	| |string | Unique ID for the requested show.  |  |
| resourceType | | enum string | "shows" | |
| startTime | | string | Timestamp starting date for the show.   |  |
| endTime	| | string | Timestamp ending date for the show.  |  |
| duration	| | number | Show duration in minutes.  |  |
| name		| | string | Full show name.  |
| shortName 	| | string | Shortened show name. |
| description	| | string | Full show description.  |
| shortDescription | | string | Short show description. |
| language| | string | Two-letter code for the spoken language.  |  |
| ratings | | string | Age-related ratings from boards and agencies. 
| ratingAdvisories | | string list | A list of content advisories, such as "Adult Situations", "Language", or "Violence" |
| seasons	| | number | Number of seasons for the show as obtained from the metadata provider. Value may be *0* or more.|   |
| seasonIDs | | string list | List of season IDs for this show.| |
| genreIDs	| | string | List of genre IDs associated with this show.| |
| regionIDs | | string | List of region IDs associated with this show.| |
| pictureID | | string | ID for the show's standard image. |  | 
||||||
| `pictures` | |  |   |  |
| 2x3  | `pictures` | string | ID for a 2x3 image. |  
| 3x4  | `pictures` | string | ID for a 3x4 image. | 
| 4x3  | `pictures` | string | ID for a 4x3 image. |   
| 16x9 | `pictures` | string | ID for a 16x9 image.| 
| publishStart |  | string | First date that this content is visible to end users. | Timestamp in ISO 8601 format. |
| publishEnd |  | string | Last date that this content is visible to end users. | Timestamp ISO 8601 format. |

<br/>

##### Response object
| Field  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata`|	 | object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| `shows`	|   | object array  |    | 
| id			| `shows` | string | Unique ID for each season.  |  |
| resourceType	| `shows` | string | "shows" | |
| startTime 	| `shows` | string | Timestamp starting date for the season.  |  |
| endTime 		| `shows` | string | Timestamp ending date for the season.  |  |
| name			| `shows` | string | Full season name.  |
| shortName 	| `shows` | string | Short season name.  |
| description	| `shows` | string | Full show description.  |
| shortDescription | `shows` | string | Short show description. |
||||||
| pictureID |`shows` | string | ID for the show's standard image. |  | 
| `pictures` | `shows` |  |   |  |
| 2x3  | `pictures` | string | ID for a 2x3 image. |  
| 3x4  | `pictures` | string | ID for a 3x4 image. | 
| 4x3  | `pictures` | string | ID for a 4x3 image. |   
| 16x9 | `pictures` | string | ID for a 16x9 image.| 
| genreIDs	| `shows` | string | List of genre IDs associated with this show.| |
| language	| `shows` | string | Two-letter code for the spoken language.  |  |
| ratings	| `shows`  | string | Age-related ratings from boards and agencies. 
| ratingAdvisories | `shows` | string list | A list of content advisories, such as "Adult Situations", "Language", or "Violence" |
| regionIDs | `shows` | string | List of region IDs associated with the season. |
| seasons	|`shows` | number | Number of seasons for the show as obtained from the metadata provider. Value may be *0* or more.|   |
| duration	|`shows` | number | Show duration in minutes.  |  |
| seasonIDs |`shows`| string list | List of season IDs for this show.| |
||||||
| `seasons`	|   | object array  |    | 
| id			| `seasons` | string | Unique ID for each season.  |  |
| resourceType	| `seasons` | string | "seasons" | |
| startTime 	| `seasons` | string | Timestamp starting date for the season.  |  |
| name			| `seasons` | string | Full season name.  |
| shortName 	| `seasons` | string | Short season name.  |
| language		| `seasons` | string | Two-letter code for the spoken language.  |  |
| regionIDs 	| `seasons` | string | List of region IDs associated with the season. |
| vod/episodeIDs| `seasons` | string list| List of IDs for the episodes in this season.  |
| episodeCount	| `seasons` | number | Number of episodes in this season as obtained from the metadata provider. |

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/shows/{{showID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "id": "08b93632288c3c1cc894c365ad090290",
    "resourceType": "shows",
    "startTime": "2011-11-11T00:00:00Z",
    "endTime": "",
    "name": "Enigmas Revelados",
    "shortName": "Enigmas",
    "description": "Estados Unidos está lleno de secretos arqueológicos enterrados en la tierra! En esta serie, el geólogo forense Scott Wolter -- considerado un Indiana Jones de la vida real por algunos -- viaja por el país para descubrir algunos de los tesoros ocultos y revelar la historia asociada con ellos, descubriendo en el proceso que hay muchos estadounidenses que no saben sobre el pasado del país, y la historia que la gente sí sabe, no siempre cuenta toda la historia. Símbolos antiguos, reliquias religiosas y otros artefactos que desentierra Wolter indican que varias civilizaciones han dejado su huella en la nación.",
    "shortDescription": "",
    "pictureID": "e3129c65aeb1a349bb356100329c321c",
    "pictures": {
        "2x3": null,
        "3x4": "a3ba485ee790a67254e090d0e51f6667",
        "4x3": "40c7d64cf9e06fbcd9fcd664e0a4a748",
        "16x9": "e3129c65aeb1a349bb356100329c321c"
    },
    "genreIDs": null,
    "language": "es",
    "ratings": [
        "USA Parental Rating//TVG",
        "Canadian Parental Rating//G",
        "Régie du cinéma/General/G",
        "Australian Classification Board/Parental Guidance/PG"
    ],
    "ratingAdvisories": null,
    "regionIDs": null,
    "seasons": 3,
    "duration": 0,
    "seasonIDs": [
        "7515190294fda190a4d925d77d1a640c",
        "84559ddf12afd7734678f6ad4ce3d3f1",
        "9252df7e0a2a36d8cee97ed6402dcc6e"
    ]
}
```



***Responses:***


Status: Get a single show | Code: 200



```js
{"requestID":"a788d1ca-fff1-439d-909d-ffeeb63fe114","timestamp":"2018-05-15T08:28:28.868833009Z","metadata":{"count":1,"totalCount":1,"offset":0},"shows":[{"id":"08b93632288c3c1cc894c365ad090290","resourceType":"shows","startTime":"2012-12-21T00:00:00.000+00:00","endTime":"","name":"Enigmas Revelados","shortName":"Enigmas","description":"Estados Unidos está lleno de secretos arqueológicos enterrados en la tierra. En esta serie, el geólogo forense Scott Wolter -- considerado un Indiana Jones de la vida real por algunos -- viaja por el país para descubrir algunos de los tesoros ocultos y revelar la historia asociada con ellos, descubriendo en el proceso que hay muchos estadounidenses que no saben sobre el pasado del país, y la historia que la gente sí sabe, no siempre cuenta toda la historia. Símbolos antiguos, reliquias religiosas y otros artefactos que desentierra Wolter indican que varias civilizaciones han dejado su huella en la nación.","shortDescription":"","pictureID":"350ccfe50b68f778b89fdca38cea8e63","pictures":{"2x3":"e0538a576f85fceb07dd9ce27c944bfb","3x4":"9d9120c5d25989d7511e070ee2748898","4x3":"51917154b9c8c6f791a90b82c7fdae11","16x9":"350ccfe50b68f778b89fdca38cea8e63"},"genreIDs":null,"language":"es","ratings":["{USA Parental Rating}/{}/{TVG}","{Canadian Parental Rating}/{}/{G}","{Régie du cinéma}/{General}/{G}","{Australian Classification Board}/{Parental Guidance}/{PG}"],"ratingAdvisories":null,"regionIDs":null,"seasons":3,"duration":0,"seasonIDs":["7515190294fda190a4d925d77d1a640c","84559ddf12afd7734678f6ad4ce3d3f1","9252df7e0a2a36d8cee97ed6402dcc6e"]}],"seasons":[{"id":"7515190294fda190a4d925d77d1a640c","resourceType":"seasons","startTime":"2012-12-21T00:00:00.000+00:00","name":"Enigmas Revelados, 1","shortName":"Enigmas, 1","language":"es","regionIDs":null,"vod/episodeIDs":null},{"id":"84559ddf12afd7734678f6ad4ce3d3f1","resourceType":"seasons","startTime":"2013-11-30T00:00:00.000+00:00","name":"Enigmas Revelados, 2","shortName":"Enigmas, 2","language":"es","regionIDs":null,"vod/episodeIDs":null},{"id":"9252df7e0a2a36d8cee97ed6402dcc6e","resourceType":"seasons","startTime":"2014-11-08T00:00:00.000+00:00","name":"Enigmas Revelados, 3","shortName":"Enigmas, 3","language":"es","regionIDs":null,"vod/episodeIDs":null}]}
```



### 3. Retrieve a show


Returns information for the specified show.

<br/>

##### PATH PARAMETERS
| Label   | Type   | Required | Description | 
|--------:|--------|----------|-------------|
|showID | string | required | ID for the requested show. | 

<br/>

##### Response object
| Field  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |   | 
| timestamp |    | string | Generated log timestamp for this request.  |   |  
| `metadata`|	 | object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| `seasons` |   |   |      |  |
| id			| seasons | string | Unique ID for each season.  |  |
| resourceType	| seasons | string | "seasons" | |
| startTime 	| seasons | string | Timestamp starting date for the season.  |  |
| name			| seasons | string | Full season name.  |
| shortName 	| seasons | string | Short season name.  |
| language		| seasons | string | Two-letter code for the spoken language.  |  |
| regionIDs 	| seasons | string | List of region IDs associated with the season. |
| vod/episodeIDs| seasons | string list| List of IDs for the episodes in this season.  |
| episodeCount	| seasons | number | Number of episodes in this season as obtained from the metadata provider. |
||||||
| `shows` |   |   |      |  |
| id		| shows |string | Unique ID for the requested show.  |  |
| resourceType	| shows | enum string | "shows" | |
| startTime | shows | string | Timestamp starting date for the show.   |  |
| endTime	| shows | string | Timestamp ending date for the show.  |  |
| duration	| shows | number | Show duration in minutes.  |  |
| name		| shows | string | Full show name.  |
| shortName 	| shows | string | Shortened show name. |
| description	| shows | string | Full show description.  |
| shortDescription | shows | string | Short show description. |
| language	| shows | string | Two-letter code for the show's spoken language.  |  |
| ratings	| shows | string | Age-related ratings from boards and agencies. | 
| ratingAdvisories | shows | string list | A list of content advisories, such as "Adult Situations", "Language", or "Violence". |
| seasons	| shows | number | Number of seasons for the show as obtained from the metadata provider. Value may be *0* or more.|   |
| seasonIDs | shows | string list | List of season IDs for this show.| |
| genreIDs	| shows | string | List of genre IDs associated with this show.| |
| regionIDs | shows | string | List of region IDs associated with this show.| |
| pictureID | shows | string | ID for the show's standard image. |  | 
||||||
| `pictures` | shows |  |   |  |
| 2x3  | `pictures` | string | ID for a 2x3 image. |  
| 3x4  | `pictures` | string | ID for a 3x4 image. | 
| 4x3  | `pictures` | string | ID for a 4x3 image. |   
| 16x9 | `pictures` | string | ID for a 16x9 image.| 

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/shows/{{showID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | seasons | Includes information for each specific season. |



***Responses:***


Status: Get a single show | Code: 200



```js
{
    "requestID": "a788d1ca-fff1-439d-909d-ffeeb63fe114",
    "timestamp": "2018-05-15T08:28:28.868833009Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "shows": [
        {
            "id": "08b93632288c3c1cc894c365ad090290",
            "resourceType": "shows",
            "startTime": "2012-12-21T00:00:00.000+00:00",
            "endTime": "",
            "name": "Enigmas Revelados",
            "shortName": "Enigmas",
            "description": "Estados Unidos está lleno de secretos arqueológicos enterrados en la tierra. En esta serie, el geólogo forense Scott Wolter -- considerado un Indiana Jones de la vida real por algunos -- viaja por el país para descubrir algunos de los tesoros ocultos y revelar la historia asociada con ellos, descubriendo en el proceso que hay muchos estadounidenses que no saben sobre el pasado del país, y la historia que la gente sí sabe, no siempre cuenta toda la historia. Símbolos antiguos, reliquias religiosas y otros artefactos que desentierra Wolter indican que varias civilizaciones han dejado su huella en la nación.",
            "shortDescription": "",
            "pictureID": "350ccfe50b68f778b89fdca38cea8e63",
            "pictures": {
                "2x3": "e0538a576f85fceb07dd9ce27c944bfb",
                "3x4": "9d9120c5d25989d7511e070ee2748898",
                "4x3": "51917154b9c8c6f791a90b82c7fdae11",
                "16x9": "350ccfe50b68f778b89fdca38cea8e63"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{USA Parental Rating}/{}/{TVG}",
                "{Canadian Parental Rating}/{}/{G}",
                "{Régie du cinéma}/{General}/{G}",
                "{Australian Classification Board}/{Parental Guidance}/{PG}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "seasons": 3,
            "duration": 0,
            "seasonIDs": [
                "7515190294fda190a4d925d77d1a640c",
                "84559ddf12afd7734678f6ad4ce3d3f1",
                "9252df7e0a2a36d8cee97ed6402dcc6e"
            ]
        }
    ],
    "seasons": [
        {
            "id": "7515190294fda190a4d925d77d1a640c",
            "resourceType": "seasons",
            "startTime": "2012-12-21T00:00:00.000+00:00",
            "name": "Enigmas Revelados, 1",
            "shortName": "Enigmas, 1",
            "language": "es",
            "regionIDs": null,
            "vod/episodeIDs": null
        },
        {
            "id": "84559ddf12afd7734678f6ad4ce3d3f1",
            "resourceType": "seasons",
            "startTime": "2013-11-30T00:00:00.000+00:00",
            "name": "Enigmas Revelados, 2",
            "shortName": "Enigmas, 2",
            "language": "es",
            "regionIDs": null,
            "vod/episodeIDs": null
        },
        {
            "id": "9252df7e0a2a36d8cee97ed6402dcc6e",
            "resourceType": "seasons",
            "startTime": "2014-11-08T00:00:00.000+00:00",
            "name": "Enigmas Revelados, 3",
            "shortName": "Enigmas, 3",
            "language": "es",
            "regionIDs": null,
            "vod/episodeIDs": null
        }
    ]
}
```



### 4. Patch a show


Patches the specified show resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the show to be updated. |

<br>

##### Body Parameters

| Name  | Parent |  Type  | Description | 
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| startTime |   	| string, format=date-time | Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string, format=date-time | Ending time in ISO-8601 timestamp format.  |
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| provider |		    | string | Metadata provider ID.  |
| providerID |	    | string | Metadata provider entity ID. |
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| seasons	|       | number, max=36000 | Number of seasons for the show.|
| seasonIDs |       | string list, allows null | List of season IDs for this show.| |
| countryOfOrigin | | string list, allows null | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/shows/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "name": "Jersey Shore",
    "pictureID": "",
    "provider": "com.gracenote.on-v3",
    "providerUID": "SH012491840000",
    "genreIDs": [
        "b3ab4f6b-a363-4938-91e6-fe877b39aaa6",
        "560e2c7e-f1a8-4892-b9c9-a9d5ebda50ac"
    ],
    "ratingAdvisories": null,
    "regionIDs": [
        "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
        "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6",
        "08329e10-c274-11e8-9b06-4d8a411f55a1",
        "2e167237-c7bb-423b-b606-c31115adb1da",
        "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
        "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
        "141a53b6-af6f-4092-ba1f-c289659310f2",
        "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0"
    ],
    "seasons": 6,
    "seasonIDs": [
        "bb9ea485-2538-4409-a3bf-0e1bb14b94c1",
        "8d9ec4a0-ed3f-4b0d-89ff-a4bf0cf4faf5",
        "7bfad074-6a24-47cf-8329-1ba44d4face7",
        "f86a4aa3-3bc4-4dde-9830-907e062c7990",
        "1b364780-1c2b-42d6-bc7b-6ae760cfef62",
        "646d592b-12b9-47d3-96a7-ae2f22d2ee5c"
    ],
    "countryOfOrigin": null
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "b190c9cb-a83a-42b8-8bfa-c0aae50cfd2e",
    "timestamp": "2020-03-24T02:51:42.360653Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "shows": [
        {
            "id": "bedafd98090d338a3145fbb5e1dab75b",
            "resourceType": "shows",
            "publishStart": "2019-03-19T14:09:31.672Z",
            "published": true,
            "created": "0001-01-01T00:00:00Z",
            "updated": "2020-03-24T02:51:42.357Z",
            "contentLock": false,
            "startTime": "",
            "endTime": "",
            "name": "Jersey Shore",
            "shortName": "Jersey Shore",
            "description": "Ocho personas se reúnen durante el verano para vivir y trabajar en Seaside Heights.",
            "shortDescription": "Ocho personas se reúnen durante el verano para vivir y trabajar en Seaside Heights.",
            "pictureID": "",
            "pictures": {
                "16x9": "fdd3bf96-88e8-489a-b7fd-ca66f6d06eed.jpg",
                "1x1": "d0532a15-c1cf-48ab-8b06-164f76104a73.jpg",
                "2x3": "cdc7a6e8-cc74-47dd-84a3-666809eabf70.jpg",
                "3x4": "a8099af4-ae50-4d0e-af84-5afb4b2cd6a6.jpg",
                "4x3": "1f8883df-f5d6-48e5-b1dc-4d1a59264c99.jpg"
            },
            "provider": "com.gracenote.on-v3",
            "providerUID": "SH012491840000",
            "genreIDs": [
                "b3ab4f6b-a363-4938-91e6-fe877b39aaa6",
                "560e2c7e-f1a8-4892-b9c9-a9d5ebda50ac"
            ],
            "language": "en",
            "ratings": [
                "Instituto de Cinematografía y de las Artes Visuales/Allowed from 18 Years/18",
                "Australian Classification Board/Mature Accompanied/MA 15+",
                "USA Parental Rating//TV14",
                "Canadian Parental Rating//14+",
                "Régie du cinéma/8 Years and Over/8+",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/16 anos/16"
            ],
            "ratingAdvisories": null,
            "regionIDs": [
                "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
                "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6",
                "08329e10-c274-11e8-9b06-4d8a411f55a1",
                "2e167237-c7bb-423b-b606-c31115adb1da",
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "141a53b6-af6f-4092-ba1f-c289659310f2",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0"
            ],
            "seasons": 6,
            "seasonIDs": [
                "bb9ea485-2538-4409-a3bf-0e1bb14b94c1",
                "8d9ec4a0-ed3f-4b0d-89ff-a4bf0cf4faf5",
                "7bfad074-6a24-47cf-8329-1ba44d4face7",
                "f86a4aa3-3bc4-4dde-9830-907e062c7990",
                "1b364780-1c2b-42d6-bc7b-6ae760cfef62",
                "646d592b-12b9-47d3-96a7-ae2f22d2ee5c"
            ],
            "countryOfOrigin": null,
            "genres": [
                {
                    "id": "560e2c7e-f1a8-4892-b9c9-a9d5ebda50ac",
                    "name": "Entertainment"
                },
                {
                    "id": "b3ab4f6b-a363-4938-91e6-fe877b39aaa6",
                    "name": "Reality"
                }
            ]
        }
    ]
}
```



## v2/validation



### 1. List all custom attributes


Lists all provisioned custom attributes for CMS resources in the tenant's environment.

<br>

When reading a resource, GET calls display custom attribute values in the customAttributes section. 

Tenants must submit a ticket to add new custom attribute fields.


<!-- The following feature has not been implemented and is currently not in plan:

		This same section can be added to the body of PUT/POST calls to modify custom attribute values for a resource. However, if the custom attribute schema specifies **"additionalProperties": false**, you cannot add fields that the schema does not already specify.

<!--
All query parameters are optional unless otherwise noted.
-->

<br>


***Endpoint:***

```bash
Method: GET
Type: RAW
URL: {{OCMServer}}/ocm/v2/validationSchemas/customAttributes
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Responses:***


Status: Retrieve the customAttributes validation schema | Code: 200



```js
{
    "requestID": "ffb2a2a9-9c91-4424-b18a-1d23c67056c3",
    "timestamp": "2019-09-30T19:36:28.513717132Z",
    "validationSchema": {
        "type": "object",
        "required": [
            "orientation"
        ],
        "properties": {
            "blackout": {
                "type": "boolean"
            },
            "color": {
                "type": "string",
                "minLength": 2,
                "maxLength": 10
            },
            "orientation": {
                "type": "string",
                "enum": [
                    "landscape",
                    "portrait"
                ]
            },
            "position": {
                "type": "integer"
            }
        },
        "additionalProperties": false
    }
}
```



## v2/vod



### 1. List VOD movies and episodes to update


Returns all VOD/episode and VOD/movie resources that need metadata updates.

<br/>

##### Response object

| Field  | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |
| timestamp |    | string | Generated log timestamp for this request.  |
|||||
| `metadata`	|   			| object | Pagination fields.   |   
| count 		| `metadata`	| number | Number of items in the current list; min=0, max = 100   
| totalCount	| `metadata`	| number | Total number of items returned by the request. 
| offset		| `metadata`	| number | Number of items skipped from the start of the list; default = 0.
|||||
| `vod/episodes`|  				| array  | List of VOD/episodes marked as needing metadata. |  
| id			| `vod/episodes`| string | Unique ID for each VOD/episode asset.  |  
| resourceType	| `vod/episodes`| string | "*vod/episodes*"  | 
| publishStart	| `vod/episodes`| string | When this content became/becomes available to subscribers. A timestamp in ISO 8601 format. |  
| published		| `vod/episodes`| boolean| Is the asset publicly available? | 
| created		| `vod/episodes`| string | When this content was created. A timestamp in ISO 8601 format. |  
| updated		| `vod/episodes`| string | When this content was last upated. A timestamp in ISO 8601 format. |  
| contentLock	| `vod/episodes`| boolean| Is the asset content locked to prevent changes? | 
| startTime		| `vod/episodes`| string | Scheduled start time. A timestamp in ISO 8601 format. |  
| endTime		| `vod/episodes`| string | Scheduled end time. A timestamp in ISO 8601 format. |  
| name			| `vod/episodes`	| string | Full name for the asset. |  
| shortName 	| `vod/episodes`	| string | Abbreviated name for the asset. |  
| description	| `vod/episodes`	| string | Full description. |  
| shortDescription |`vod/episodes`	| string | Short description. | 
| pictureID 	| `vod/episodes`| string | ID for the standard image. |  
|||||
| `pictures` | `vod/episodes`| string array | IDs for images with specific dimensions. |  
| 2x3  | `pictures` | string | ID for a 2x3 image. |   
| 3x4  | `pictures` | string | ID for a 3x4 image.  | 
| 4x3  | `pictures` | string | ID for a 4x3 image.  |   
| 16x9 | `pictures` | string | ID for a 16x9 image.  | 
| genreIDs | `vod/episodes`  | string array | List of genre IDs associated with this asset. | 
| language | `vod/episodes`  | string | Two-letter code for the spoken language.  |  
| ratings  | `vod/episodes`  | string array | Content ratings by boards and associations.  |
| ratingAdvisories | `vod/episodes`  | string array | List of content advisories such as "Adult Situations", "Language", or "Violence". |
| regionIDs | `vod/episodes`  | string array | Unique ID for each region where the asset is available. | 
| season | `vod/episodes` | number | Season for the current episode. | 
| episode| `vod/episodes` | number | Episode number for the current episode. | 
| duration	| `vod/episodes`| number |Show duration in minutes. |  
| assetIDs	| `vod/episodes`| string array | Comma-separated list of asset IDs associated with this VOD/episode. | 
| showID	| `vod/episodes`| string | Unique ID for the show series.  |  
| seasonID	| `vod/episodes`| string | Unique ID for this show season. |  
| showName	| `vod/episodes`| string | Overall name for the show series. |  
| genres	| `vod/episodes`| string array | List of genres associated with this asset. | 
| needsMetadata | `vod/episodes`  | boolean | Does the asset metadata need to be updated? | 
| countryOfOrigin |`vod/episodes`| string | Country of origin for this show.  |  
|||||
| `metadata`	| `vod/episodes` | object | Metadata description fields for this asset.   |   
| source	| `metadata` | string | Metadata source name.   |   
| id	| `metadata` | string | Metadata ID name.   |   
| `vod/movies`	|   			| array  | List of VOD/movies marked as needing metadata.  |  
| id			| `vod/movies`  | string | Unique ID for each VOD/movie asset.  |  
| resourceType	| `vod/movies`	| enum string | "*vod/episodes*"   | 
| publishStart	| `vod/movies`| string | When this content became/becomes available to subscribers. A timestamp in ISO 8601 format. |  
| publishEnd	| `vod/movies`| string | When this content became/becomes unavailable to subscribers. A timestamp in ISO 8601 format. |  
| published		| `vod/movies`| boolean| Is the asset publicly available? | 
| created		| `vod/movies`| string | When this content was created. A timestamp in ISO 8601 format. |  
| updated		| `vod/movies`| string | When this content was last upated. A timestamp in ISO 8601 format. |  
| contentLock	| `vod/movies`| boolean| Is the asset content locked to prevent changes? | 
| startTime 	| `vod/movies`	| string | Scheduled start time. A timestamp in ISO 8601 format.  |  
| endTime		| `vod/movies`	| string | Scheduled end time. A timestamp in ISO 8601 format.  |  
| duration		| `vod/movies`| number |Show duration in minutes. |  
| name			| `vod/movies`	| string | Full name for the asset. |  
| shortName 	| `vod/movies`	| string | Abbreviated name for the asset.  |  
| description	| `vod/movies`  | string | Full description. |  
| shortDescription |`vod/movies`| string | Short description.  | 
| pictureID | `vod/movies`  | string | ID for the standard image. |  
|||||
| `pictures` | `vod/movies` |  | IDs for images with specific dimensions.   |  
| 2x3  | `pictures` | string | ID for a 2x3 image. |   
| 3x4  | `pictures` | string | ID for a 3x4 image.  | 
| 4x3  | `pictures` | string | ID for a 4x3 image.  |   
| 16x9 | `pictures` | string | ID for a 16x9 image.  |  
| genreIDs | `vod/movies`  | string array | List of genre IDs associated with this asset. | 
| language | `vod/movies`  | string | Two-letter code for the spoken language.  |  
| ratings  | `vod/movies`  | string | Content ratings by boards and associations.  |
| ratingAdvisories | `vod/movies`  | string array | List of content advisories such as "Adult Situations", "Language", or "Violence" |
| regionIDs | `vod/movies`  | string array | Unique ID for each region where the asset is available. | 
| releaseYear | `vod/movies`  | number | Year that the movie was publicly released.  | 
| countryOfOrigin |`vod/movies`| string | Country of origin for this movie.  |  
| assetIDs	| `vod/movies` | string array | Comma-separated list of asset IDs to associated with this VOD/movie. | 
| genres	| `vod/movies`  | string array | List of genres associated with this asset. | 
| needsMetadata | `vod/movies`   | boolean | Indicates that the asset metadata is set to be updated with Gracenote information. | 
| `metadata`	| `vod/movies`  | boolean | Indicates that the asset metadata is set to be updated with Gracenote information. | 
| source	| `metadata` | string | Metadata source name.   |   
| id		| `metadata` | string | Metadata ID name.   |
| status	| `metadata` | string | Metadata status.   |

<br>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested VOD entry|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/vod/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request.   |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| needsMetadata | true | __Required__. Returns VOD/episode and VOD movie assets needing metadata updates. |



## v2/vod/competitions



### 1. Create VOD Competition


Creates a game competition entry in the on-demand catalog.


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/competitions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "vod/competitions",
    "publishStart": "2018-01-01T00:00:00Z",
    "publishEnd": "2020-01-01T00:00:00Z",
    "name": "Monstruo: Se Busca",
    "shortName": "Monstruo",
    "description": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
    "shortDescription": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
    "genreIDs": null,
    "language": "es",
    "ratings": [
        "{Canadian Parental Rating}/{}/{PG}",
        "{USA Parental Rating}/{}/{TVPG}"
    ],
    "ratingAdvisories": null,
    "regionIDs": null,
    "pictures": {
        "2x3": "3e30c8ab1e8fc496aa7ab6258ecf6c74",
        "3x4": "b21b21545e2e60313b0a05e9336fdcaf",
        "4x3": "39b6c70c17031b8a84ff81a9e96dac3c",
        "16x9": "e310931fff6c87d136725a31e4c763b5"
    },
    "pictureID": "e310931fff6c87d136725a31e4c763b5",
    "sportID": "d2fcc8f2f2e04ff67204e272bd93b1b7",
    "sportName": "Fishing",
    "gameID": "1234",
    "tournamentID": "75bd3585eb1a1138932dd23b9d004868",
    "tournamentName": "Monstruo: Se Busca",
    "primaryPersonID": "",
    "primaryPersonName": "",
    "primaryPersonPictureID": "",
    "secondaryPersonID": "",
    "secondaryPersonName": "",
    "secondaryPersonPictureID": "",
    "assetIDs": [
        "8dd59b4c-064b-4f88-8eea-4414c11e7177"
    ],
    "duration": 0
}
```



### 2. Update VOD Competition


Updates a game competition entry in the on-demand catalog.

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| competitionID		|string		|required	|ID for the target VOD team competition. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target game.|
|404		|1040	|*Not Found*: Target game not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/competitions/{{competitionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "vod/competitions",
    "publishStart": "2018-01-01T00:00:00Z",
    "publishEnd": "2020-01-01T00:00:00Z",
    "name": "Monstruo: Se Busca",
    "shortName": "MONST",
    "description": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
    "shortDescription": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
    "genreIDs": null,
    "language": "es",
    "ratings": [
        "{Canadian Parental Rating}/{}/{PG}",
        "{USA Parental Rating}/{}/{TVPG}"
    ],
    "ratingAdvisories": null,
    "regionIDs": null,
    "pictures": {
        "2x3": "3e30c8ab1e8fc496aa7ab6258ecf6c74",
        "3x4": "b21b21545e2e60313b0a05e9336fdcaf",
        "4x3": "39b6c70c17031b8a84ff81a9e96dac3c",
        "16x9": "e310931fff6c87d136725a31e4c763b5"
    },
    "pictureID": "e310931fff6c87d136725a31e4c763b5",
    "sportID": "d2fcc8f2f2e04ff67204e272bd93b1b7",
    "sportName": "Fishing",
    "gameID": "1234",
    "tournamentID": "75bd3585eb1a1138932dd23b9d004868",
    "tournamentName": "Monstruo: Se Busca",
    "primaryPersonID": "",
    "primaryPersonName": "",
    "primaryPersonPictureID": "",
    "secondaryPersonID": "",
    "secondaryPersonName": "",
    "secondaryPersonPictureID": "",
    "assetIDs": [
        "8dd59b4c-064b-4f88-8eea-4414c11e7177"
    ],
    "duration": 0
}
```



### 3. Retrieve game from the on-demand catalog


Retrieves the specified game from the on-demand catalog.

**Note: This API is available only for the new non-SportsRocket CMS.**

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested VOD competition entry|
|404		|1040				|*Not Found*: No matching scheduled VOD competition found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/vod/competitions/{{competitionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Retrieve game from the on-demand catalog | Code: 200



```js
{
    "requestID": "f9e830b2-fe37-4629-b7ea-571616386b80",
    "timestamp": "2018-05-15T04:26:28.987928398Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "vod/competitions": [
        {
            "id": "ac81a509d0a63cd84630256cde62975a",
            "resourceType": "vod/competitions",
            "name": "Monstruo: Se Busca",
            "shortName": "Monstruo",
            "description": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
            "shortDescription": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Canadian Parental Rating}/{}/{PG}",
                "{USA Parental Rating}/{}/{TVPG}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "pictures": {
                "2x3": "3e30c8ab1e8fc496aa7ab6258ecf6c74",
                "3x4": "b21b21545e2e60313b0a05e9336fdcaf",
                "4x3": "39b6c70c17031b8a84ff81a9e96dac3c",
                "16x9": "e310931fff6c87d136725a31e4c763b5"
            },
            "pictureID": "e310931fff6c87d136725a31e4c763b5",
            "sportID": "d2fcc8f2f2e04ff67204e272bd93b1b7",
            "sportName": "Fishing",
            "tournamentID": "75bd3585eb1a1138932dd23b9d004868",
            "tournamentName": "Monstruo: Se Busca",
            "primaryPersonID": "",
            "primaryPersonName": "",
            "primaryPersonPictureID": "",
            "secondaryPersonID": "",
            "secondaryPersonName": "",
            "secondaryPersonPictureID": "",
            "assetIDs": null,
            "duration": 0
        }
    ]
}
```



### 4. Delete VOD competition


Deletes the specified VOD competition.

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|vodCompetitionID	|string		|required	|ID for the targeted VOD competition. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified VOD competition.|
|404		|1040	|*Not Found*: No matching VOD competition ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/vod/competitions/{{competitionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 5. Patch VOD competition


Patches the specified VOD competition resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the VOD competition to be updated. |

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| pictureID |   	| string, max=512 | ID for the standard image. |
| sportID |     	| string | ID for the sport associated with this resource. | 
| sportName |   	| string | Name for the sport associated with this resource. | 
| leagueID |        | string | |
| leagueName |      | string | |
| tournamentID |    | string | ID for the tournament associated with this resource.  | 
| tournamentName |  | string | Name for the tournament associated with this resource. | 
| gameID |    		| string | ID for the game associated with this resource. | 
| primaryPersonID |     	| string | ID for the primary or home competitor. | 
| primaryPersonName |   	| string | Name for the primary or home competitor. | 
| primaryPersonPictureID |  | string | ID for picture of the primary or home competitor. | 
| secondaryPersonID | 	  | string | ID for the secondary or away competitor. | 
| secondaryPersonName |     | string | Name for the secondary or away competitor. | 
| secondaryPersonPictureID| | string | ID for picture of the secondary or away competitor. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| needsMetadata | | boolean | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/competitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
	"publishStart": "2019-05-17T00:17:45.687Z",
    "contentLock": false,
    "name": "French F1: Qualifying",
    "shortName": "French F1: Qualifying",
    "description": "French F1: Qualifying",
    "shortDescription": "French F1: Qualifying",
    "venue": "",
    "duration": 10800,
    "language": "en",
    "regionIDs": [
        "7bb71990-1e8d-11e9-900e-9d49235d5db0"
    ],
    "pictures": {
        "16x9": "b57164e3-4772-4601-8e1f-7b786165620d.jpg",
        "2x3": "",
        "3x4": "",
        "4x3": ""
    },
    "pictureID": "",
    "sportID": "1ac4e585-28d0-4a71-acf8-5bfef2b3be60",
    "sportName": "Auto Racing",
    "leagueID": "cc170b3f-1e6a-4af4-93dd-6c5c733af4d7",
    "leagueName": "",
    "tournamentID": "",
    "tournamentName": "",
    "gameID": "77165a88-4f2c-4166-bc6c-9caba63b7bab",
    "genreIDs": null,
    "metadata": {
        "source": "Unspecified",
        "id": "spark"
    }
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "2bd1c8c1-4fc1-41f1-8237-24d3cf7b42a6",
    "timestamp": "2020-03-25T18:06:19.706798Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "vod/competitions": [
        {
            "id": "daef5c39-e1be-4e82-9281-87deab46abb1",
            "resourceType": "vod/competitions",
            "publishStart": "2019-05-17T00:17:45.687Z",
            "published": true,
            "created": "2019-05-17T00:17:45.708Z",
            "updated": "2020-03-25T18:06:19.703Z",
            "contentLock": false,
            "name": "French F1: Qualifying",
            "shortName": "French F1: Qualifying",
            "description": "French F1: Qualifying",
            "shortDescription": "French F1: Qualifying",
            "venue": "",
            "duration": 10800,
            "language": "en",
            "ratings": null,
            "ratingAdvisories": null,
            "regionIDs": [
                "7bb71990-1e8d-11e9-900e-9d49235d5db0"
            ],
            "pictures": {
                "16x9": "b57164e3-4772-4601-8e1f-7b786165620d.jpg",
                "2x3": "",
                "3x4": "",
                "4x3": ""
            },
            "pictureID": "",
            "sportID": "1ac4e585-28d0-4a71-acf8-5bfef2b3be60",
            "sportName": "Auto Racing",
            "leagueID": "cc170b3f-1e6a-4af4-93dd-6c5c733af4d7",
            "leagueName": "",
            "tournamentID": "",
            "tournamentName": "",
            "gameID": "77165a88-4f2c-4166-bc6c-9caba63b7bab",
            "primaryPersonID": "",
            "primaryPersonName": "",
            "primaryPersonPictureID": "",
            "secondaryPersonID": "",
            "secondaryPersonName": "",
            "secondaryPersonPictureID": "",
            "assetIDs": [
                "e0ad8b5e-a511-45d2-aa5b-54f15c1951e9"
            ],
            "providerID": "spark",
            "genreIDs": null,
            "genres": null,
            "metadata": {
                "source": "Unspecified",
                "id": "spark"
            }
        }
    ]
}
```



## v2/vod/episodes



### 1. Create VOD episode


Creates a show episode entry in the on-demand catalog.


##### Response object
| Field  | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    | 
| timestamp |    | string | Generated log timestamp for this request.  |
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| *`seasons`* |   |   |      |  |
| id | seasons  |string | Unique ID for each season.  |  |
| resourceType | seasons   | string | "seasons"  | |
| startTime | seasons | string | A  timestamp for starting date of the season.  |  |
| name | seasons  | string | Full name.  |  |
| shortName | seasons  | string |   |  |
| language | seasons  | string | Two-letter code for the spoken language.  |  |
| regionIDs | seasons  | string |  |  |
| vod/episodeIDs | seasons   | string list|   |  |
||||||
| *`vod/episodes`* |   |   |      |  |
| id | vod/episodes  |string | Unique ID for each asset.  |  |
| resourceType | vod/episodes | enum string | *vod/episodes*   | |
| startTime | vod/episodes | string | A timestamp.  |  |
| endTime | vod/episodes | string | A timestamp.  |  |
| name | vod/episodes | string | Full name.  |  |
| shortName | vod/episodes | string |   |  |
| description | vod/episodes  | string | Full description.  |  |
| shortDescription | vod/episodes | string |   |  |
| genreIDs | vod/episodes  | string list | | |
| language | vod/episodes  | string | Two-letter code for the spoken language.  |  |
| ratings  | vod/episodes  | string | Content ratings by boards and associations.  | 
| ratingAdvisories | vod/episodes  | string list | A list of content advisories such as "Adult Situations", "Language", or "Violence". |
| regionIDs | vod/episodes  | string list | | |
| season | vod/episodes  | number |   |  |
| episode | vod/episodes  | number |   | |
| duration | vod/episodes  | number | Duration in minutes.  |  |
| assetIDs | vod/episodes  | string | | |
| pictureID | vod/episodes  | string | ID for the standard image |  | 
||||||
| *`pictures`* | vod/episodes|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. |  | 
| 3x4  | pictures | string | ID for a 3x4 image.  |  | 
| 4x3  | pictures | string | ID for a 4x3 image.  |  | 
| 16x9 | pictures | string | ID for a 16x9 image.  |  |
| publishStart |  | string | First date that this content is visible to end users. ISO 8601 format |
| publishEnd |  | string | Last date that this content is visible to end users.  ISO 8601 format |

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/episodes
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "id": "0316a2e2a45eac0af9bec8c157378d0a",
    "resourceType": "epg/episodes",
    "startTime": "2018-05-23T23:00:00Z",
    "endTime": "2018-05-24T00:00:00Z",
    "duration": 60,
    "name": "The Voice",
    "shortName": "The Voice",
    "description": "Each of the final four artists performs a solo cover, a duet with the coach and his or her first original song.",
    "shortDescription": "Each of the final four artists performs.",
    "language": "en",
    "pictureID": "fe83e1fc7a9d665b432536a3a5a4d850",
    "pictures": {
        "2x3": "c59cfd8cb8d8227cfe3279d996645b5f",
        "3x4": "ddadc6ec1be3cfd73a1160d5b101f850",
        "4x3": "f2db4a36e5e857c23bc67d046396d3cd",
        "16x9": "fe83e1fc7a9d665b432536a3a5a4d850"
    },
    "ratings": [
        "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
        "Canadian Parental Rating//PG",
        "USA Parental Rating//TVPG"
    ],
    "ratingAdvisories": [],
    "stationID": "079fd2ea771cb01fd7d23feb4164ea19",
    "genreIDs": [
        "54d83ad2f132c6ab294e66fdcfa28132",
        "9382383b772f91159b444f8a451006a9"
    ],
    "assetIDs": [
        "170cdfba4efef2cc2d179cf7bbedae1a"
    ],
    "season": 14,
    "episode": 27,
    "showName": "The Voice"
}
```



***Responses:***


Status: Create vod episode | Code: 200



### 2. Update VOD episode


Updates a show episode description in the on-demand catalog.

<br/>

<!-- This should be a PUT not a POST -->

##### Response object
| Name  | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    |
| timestamp |    | string | Generated log timestamp for this request.  | 
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| *`seasons`* |   |   |      |  |
| id | seasons  |string | Unique ID for each season.  |  |
| resourceType | seasons   | string | "seasons"  | |
| startTime | seasons | string | A  timestamp for starting date of the season.  |  |
| name | seasons  | string | Full name.  |  |
| shortName | seasons  | string |   |  |
| language | seasons  | string | Two-letter code for the spoken language.  |  |
| regionIDs | seasons  | string |  |  |
| vod/episodeIDs | seasons   | string list|   |  |
||||||
| *`vod/episodes`* |   |   |      |  |
| id | vod/episodes  |string | Unique ID for each asset.  |  |
| resourceType | vod/episodes | enum string | *vod/episodes*   | |
| startTime | vod/episodes | string | A timestamp.  |  |
| endTime | vod/episodes | string | A timestamp.  |  |
| name | vod/episodes | string | Full name.  |  |
| shortName | vod/episodes | string |   |  |
| description | vod/episodes  | string | Full description.  |  |
| shortDescription | vod/episodes | string |   |  |
| genreIDs | vod/episodes  | string list | | |
| language | vod/episodes  | string | Two-letter code for the spoken language.  |  |
| ratings  | vod/episodes  | string | Content ratings by boards and associations.  | 
| ratingAdvisories | vod/episodes  | string list | A list of content advisories such as "Adult Situations", "Language", or "Violence". |
| regionIDs | vod/episodes  | string list | | |
| season | vod/episodes  | number |   |  |
| episode | vod/episodes  | number |   | |
| duration | vod/episodes  | number | Duration in minutes.  |  |
| assetIDs | vod/episodes  | string | | |
| pictureID | vod/episodes  | string | ID for the standard image |  | 
||||||
| *`pictures`* | vod/episodes|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. |  | 
| 3x4  | pictures | string | ID for a 3x4 image.  |  | 
| 4x3  | pictures | string | ID for a 4x3 image.  |  | 
| 16x9 | pictures | string | ID for a 16x9 image.  |  |
| publishStart |  | string | First date that this content is visible to end users.  ISO 8601 format |
| publishEnd |  | string | Last date that this content is visible to end users.  ISO 8601 format |

<br>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/episodes/{{episodeID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "id": "0316a2e2a45eac0af9bec8c157378d0a",
    "resourceType": "vod/episodes",
    "startTime": "2018-05-23T23:00:00Z",
    "endTime": "2018-05-24T00:00:00Z",
    "duration": 60,
    "name": "The Voice",
    "shortName": "The Voice",
    "description": "Each of the final four artists performs a solo cover, a duet with the coach and his or her first original song.",
    "shortDescription": "Each of the final four artists performs.",
    "language": "en",
    "pictureID": "fe83e1fc7a9d665b432536a3a5a4d850",
    "pictures": {
        "2x3": "c59cfd8cb8d8227cfe3279d996645b5f",
        "3x4": "ddadc6ec1be3cfd73a1160d5b101f850",
        "4x3": "f2db4a36e5e857c23bc67d046396d3cd",
        "16x9": "fe83e1fc7a9d665b432536a3a5a4d850"
    },
    "ratings": [
        "Departamento de Justiça, Classificação, Títulos e Qualificação/12 anos/12",
        "Canadian Parental Rating//PG",
        "USA Parental Rating//TVPG"
    ],
    "ratingAdvisories": [],
    "stationID": "079fd2ea771cb01fd7d23feb4164ea19",
    "genreIDs": [
        "54d83ad2f132c6ab294e66fdcfa28132",
        "9382383b772f91159b444f8a451006a9"
    ],
    "assetIDs": [
        "170cdfba4efef2cc2d179cf7bbedae1a"
    ],
    "season": 14,
    "episode": 27,
    "showName": "The Voice"
}
```



***Responses:***


Status: Update vod episode | Code: 200



```js
{
    "assetIds": ["124asdf"]
}
```



### 3. Retrieve show episode from the on-demand catalog


Retrieves the specified episode from the on-demand catalog.

<!--

#### Response object

The Notes column describes default and possible values, valid ranges, and fields that are *nullable* ( &oslash; ), or *required* ( *&#640;* ). All fields are optional unless otherwise indicated.

<br/>

| Field  | Parent |  Type  | Description | Notes 
|------:|--------|--------|-------------|-------
| requestID |    | string | Generated log ID for this request.    | *&#640;*  | 
| timestamp |    | string | Generated log timestamp for this request.  | *&#640;* |  
||||||
| *`metadata`* |   |  |  |   |  
| count | metadata |number  | Current screen.  |*&#640;*, min=1, max = 100   
| totalCount| metadata |number | Total number of screens.  |*&#640;*, min=1, max = 20
| offset | metadata | number | Number of lines from the top of the screen. |*&#640;*, min=1, max = 20
||||||
| *`assets`* |   |   |      |  |
| id | assets  |string | Unique ID for each season.  |  |
| resourceType | assets   | string | *"assets"*  | |
| pictureID | assets  | string | ID for the standard image |  | 
| duration | assets  | number |   |  |
| live | assets  | boolean | Is this a live event?  | May be false or true. |
| environment | assets  | string |   |  |
| liveURLs | assets  | string |   |  &oslash;; |
| *`vodURLs`*| assets | | URLs for live feeds. |  | 
| *`dash`* | vodURLs | |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. | |
| primary | dash | string | Primary URL for the DASH source.   |  | 
| *`hls`* | vodURLs |  | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.| | 
| primary | hls | string | Primary URL for the HLS source.   |  |
||||||
| *`vod/episodes`* |   |   |      |  |
| id | vod/episodes  |string | Unique ID for each asset.  |  |
| resourceType | vod/episodes | enum string | *"vod/episodes"*   | |
| startTime | vod/episodes | string | A timestamp.  |  |
| endTime | vod/episodes | string | A timestamp.  |  |
| name | vod/episodes | string | Full name.  |  |
| shortName | vod/episodes | string |   |  |
| description | vod/episodes  | string | Full description.  |  |
| shortDescription | vod/episodes | string |   |  |
| genreIDs | vod/episodes  | string list | | |
| language | vod/episodes  | string | Two-letter code for the spoken language.  |  |
| ratings  | vod/episodes  | string | Content ratings by boards and associations.  | &oslash; |
| ratingAdvisories | vod/episodes  | string list | A list of content advisories.  | Such as "Adult Situations", "Language", or "Violence" |
| regionIDs | vod/episodes  | string list | | |
| season | vod/episodes  | number |   |  |
| episode | vod/episodes  | number |   | |
| duration | vod/episodes  | number |   |  |
| assetIDs | vod/episodes  | string | | |
| pictureID | vod/episodes  | string | ID for the standard image |  | 
||||||
| *`pictures`* | vod/episodes|  |   |  |
| 2x3  | pictures | string | ID for a 2x3 image. |  | 
| 3x4  | pictures | string | ID for a 3x4 image.  |  | 
| 4x3  | pictures | string | ID for a 4x3 image.  |  | 
| 16x9 | pictures | string | ID for a 16x9 image.  |  |

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/vod/episodes/{{episodeID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | assets | Includes descriptive metadata. |



***Responses:***


Status: Retrieve show episode from the on-demand catalog | Code: 200



```js
{
    "requestID": "9960c9aa-7ac1-4ea6-8b71-66c2bee6b4f7",
    "timestamp": "2018-05-15T04:28:21.581501469Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "assets": [
        {
            "id": "5223540365691495be6cedd0212727ed",
            "resourceType": "assets",
            "pictureID": "",
            "duration": 0,
            "live": false,
            "environment": "",
            "liveURLs": null,
            "vodURLs": {
                "dash": {
                    "primary": "https://dtvlatamvod-isp.akamaized.net/alpha/edcoutput/241000_DTVOD_TabooS1Epis/241000_MP4DS_HDTV_51ENG_51ENG_TVVOD_4472609.mpd"
                },
                "hls": {
                    "primary": "https://dtvlatamvod-isp.akamaized.net/alpha/edcoutput/241000_DTVOD_TabooS1Epis/master_fp.m3u8"
                }
            }
        }
    ],
    "vod/episodes": [
        {
            "id": "48ab731a9cb5508e0a7481a77bf30312",
            "resourceType": "vod/episodes",
            "startTime": "2017-01-07T00:00:00.000+00:00",
            "endTime": "",
            "name": "Taboo",
            "shortName": "Taboo",
            "description": "Londres, 1814. James Delaney, de quien todos pensaban que había muerto hacía años en África, regresa a la ciudad a reclamar la misteriosa herencia de su padre. En ese momento, Gran Bretaña está librando sendas guerras con Francia y Estados Unidos.",
            "shortDescription": "Londres, 1814. James Delaney, de quien todos pensaban que había muerto hacía años en África, regresa a la ciudad a reclamar la misteriosa herencia de su padre. En ese momento, Gran Bretaña está librando sendas guerras con Francia y Estados Unidos.",
            "pictureID": "19d236219e47ef8e636e98b77bb2664b",
            "pictures": {
                "2x3": "6c4e759703b2489007f6722d8763c25b",
                "3x4": "f2818d9519bd0c775435f917303ecb85",
                "4x3": "a9f1764292a3ecd3e8f837eba1f17290",
                "16x9": "19d236219e47ef8e636e98b77bb2664b"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{USA Parental Rating}/{}/{TVMA}",
                "{Canadian Parental Rating}/{}/{18+}",
                "{Régie du cinéma}/{18 Years and Over}/{18+}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}"
            ],
            "ratingAdvisories": null,
            "regionIDs": null,
            "season": 1,
            "episode": 1,
            "duration": 0,
            "assetIDs": [
                "5223540365691495be6cedd0212727ed"
            ]
        }
    ]
}
```



### 4. Delete VOD episode


Deletes the specified VOD episode. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|vodEpisodeID	|string		|required	|ID for the targeted VOD episode. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified VOD episode.|
|404		|1040	|*Not Found*: No matching VOD episode ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/vod/episodes/892116d03352a1b85a5cdbc21f932b4e
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| If-None-Match | {{If-None-Match}} | _Optional string_. Cache control header for reads. |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 5. Patch VOD episode


Patches the specified VOD episode resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|id	|string		|required	|ID of the VOD episode to be updated. |

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| season | | number | The season number. |
| episode | | number | The episode number. |
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| showID | | string | The show this episode belongs to. |
| seasonID |  | string | The season this episode belongs to. |
| showName |  | string | The name of the episode show. |
| countryOfOrigin | | string list, allows null | | 
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| needsMetadata | | boolean | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/episodes/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "contentLock": false,
    "name": "A Hit Is a Hit.",
    "shortName": "Los Soprano",
    "description": "Christopher y Adriana intentan hacer negocios en la industria de la música después de reunirse con el famoso rapero. Tony es invitado por un vecino a su exclusivo club para jugar al golf.",
    "shortDescription": "Christopher y Adriana intentan hacer negocios tras reunirse con el famoso rapero.",
    "pictureID": "6634c7fc-cfe7-427e-b852-733de0042015.jpg",
    "pictures": {
        "16x9": "6634c7fc-cfe7-427e-b852-733de0042015.jpg",
        "2x3": "6d18f50e-e2f4-4b7c-827c-b5fdab892ebe.jpg",
        "3x4": "8731f4de-e201-4dbb-afb4-6ad07e930539.jpg",
        "4x3": "df64d165-4a73-451c-8710-14528c470e81.jpg"
    },
    "genreIDs": [
        "7881a80d-83cb-4bf8-a615-c4ca3473ff90"
    ],
    "language": "es",
    "ratingAdvisories": null,
    "regionIDs": [
        "2e167237-c7bb-423b-b606-c31115adb1da",
        "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
        "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
        "141a53b6-af6f-4092-ba1f-c289659310f2",
        "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6",
        "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
        "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
        "08329e10-c274-11e8-9b06-4d8a411f55a1"
    ],
    "season": 1,
    "episode": 10,
    "duration": 3300,
    "assetIDs": [
        "ac38cf168458522e041c28966b0ecc0c"
    ],
    "showID": "07164175d3cc5f58f14ea1c34c2539d2",
    "seasonID": "cb0fd103-72fb-4fd3-af13-e614c697e210",
    "showName": "Los Soprano",
    "countryOfOrigin": [
        "USA"
    ]
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "6718e21f-bf7d-4b66-b0f3-60650fb350e1",
    "timestamp": "2020-03-24T06:18:43.482349Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "vod/episodes": [
        {
            "id": "043ff09263150f28890a79b8511bf6a3",
            "resourceType": "vod/episodes",
            "publishStart": "2016-05-16T00:00:00Z",
            "publishEnd": "2024-06-30T00:00:00Z",
            "published": true,
            "created": "0001-01-01T00:00:00Z",
            "updated": "2020-03-24T06:18:43.476Z",
            "contentLock": false,
            "name": "A Hit Is a Hit.",
            "shortName": "Los Soprano",
            "description": "Christopher y Adriana intentan hacer negocios en la industria de la música después de reunirse con el famoso rapero. Tony es invitado por un vecino a su exclusivo club para jugar al golf.",
            "shortDescription": "Christopher y Adriana intentan hacer negocios tras reunirse con el famoso rapero.",
            "pictureID": "6634c7fc-cfe7-427e-b852-733de0042015.jpg",
            "pictures": {
                "16x9": "6634c7fc-cfe7-427e-b852-733de0042015.jpg",
                "2x3": "6d18f50e-e2f4-4b7c-827c-b5fdab892ebe.jpg",
                "3x4": "8731f4de-e201-4dbb-afb4-6ad07e930539.jpg",
                "4x3": "df64d165-4a73-451c-8710-14528c470e81.jpg"
            },
            "genreIDs": [
                "7881a80d-83cb-4bf8-a615-c4ca3473ff90"
            ],
            "language": "es",
            "ratings": [
                "USA Parental Rating//TVMA",
                "Canadian Parental Rating//18+",
                "Régie du cinéma/18 Years and Over/18+",
                "Australian Classification Board/Mature Accompanied/MA 15+",
                "Departamento de Justiça, Classificação, Títulos e Qualificação/16 anos/16",
                "Mediakasvatus- ja kuvaohjelmayksikkö/Allowed from 16 years/K16"
            ],
            "ratingAdvisories": null,
            "regionIDs": [
                "2e167237-c7bb-423b-b606-c31115adb1da",
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "141a53b6-af6f-4092-ba1f-c289659310f2",
                "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
                "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
                "08329e10-c274-11e8-9b06-4d8a411f55a1"
            ],
            "season": 1,
            "episode": 10,
            "duration": 3300,
            "assetIDs": [
                "ac38cf168458522e041c28966b0ecc0c"
            ],
            "showID": "07164175d3cc5f58f14ea1c34c2539d2",
            "seasonID": "cb0fd103-72fb-4fd3-af13-e614c697e210",
            "showName": "Los Soprano",
            "genres": [
                {
                    "id": "7881a80d-83cb-4bf8-a615-c4ca3473ff90",
                    "name": "Crimen-drama"
                }
            ],
            "countryOfOrigin": [
                "USA"
            ],
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "EP009360990062",
                "status": "Mapped"
            }
        }
    ]
}
```



## v2/vod/events



### 1. Create VOD event


Creates an event entry in the on-demand catalog.


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/events
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "resourceType": "vod/events",
    "publishStart": "2010-01-01T00:00:00Z",
    "publishEnd": "2020-01-01T00:00:00Z",
    "published": true,
    "startTime": "",
    "endTime": "",
    "duration": 1,
    "name": "bneumann test vod/events",
    "shortName": "bneumann",
    "description": "bneumann test vod/events",
    "shortDescription": "bneumann",
    "language": "es",
    "pictureID": "ec6938e37fb95efc6d5eccaa25afa7f5",
    "pictures": {
        "16x9": "ec6938e37fb95efc6d5eccaa25afa7f5",
        "2x3": "19e16a35aef87a171a04a744e4360a4e",
        "3x4": "0051bbf3793e2e64b0114eb7cff8872b",
        "4x3": "153cb138245c309f52e440f5c42e6adb"
    },
    "genreIDs": null,
    "ratings": [
        "{Motion Picture Association of America}/{Restricted}/{R}",
        "{Manitoba Film Classification Board}/{14 Accompaniment}/{14A}",
        "{Alberta's Film Classification Board}/{14A}/{14A}",
        "{B.C. Film Classification Office}/{14A}/{14A}",
        "{Saskatchewan Film and Video Classification Board}/{14A}/{14A}",
        "{British Board of Film Classification}/{15}/{15}",
        "{Ontario Film Authority}/{18A}/{18A}",
        "{Maritime Film Classification Board}/{Adult Accompaniment}/{14}",
        "{UK Content Provider}/{15}/{15}",
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
        "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
        "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed from 12 years}/{K12}",
        "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
        "{Conseil Supérieur de l'Audiovisuel}/{Allowed from 10 years}/{-10}",
        "{Ministero dei Beni e delle Attività Culturali e del Turismo}/{All ages admitted.}/{T}",
        "{Ley de Medios Audiovisuales}/{}/{SAM 13}",
        "{Medietilsynet}/{Tillatt for alle}/{A}"
    ],
    "ratingAdvisories": [
        "Adult Language",
        "Adult Situations",
        "Strong Sexual Content"
    ],
    "regionIDs": [],
    "assetIDs": [],
    "genres": null,
    "contentLock": false,
    "metadata": {
        "source": "",
        "id": ""
    }
}
```



### 2. Update VOD event


Updates an event description in the on-demand catalog.

<!-- Original URL: {{OCMServer}}/ocm/v2/vod/events/a34b99fd-5454-411c-b2ae-1765541ac7c2 -->


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/events/{{eventID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |
| If-None-Match | {{If-None-Match}} | *Optional*. Cache control header for reads. |



***Body:***

```js        
{
            "id": "a34b99fd-5454-411c-b2ae-1765541ac7c2",
            "resourceType": "vod/events",
            "publishStart": "2010-01-01T00:00:00Z",
            "publishEnd": "2020-01-01T00:00:00Z",
            "published": true,
            "startTime": "",
            "endTime": "",
            "duration": 1,
            "name": "bneumann test vod/events",
            "shortName": "bneumann 4",
            "description": "bneumann test vod/events",
            "shortDescription": "bneumann",
            "language": "es",
            "pictureID": "ec6938e37fb95efc6d5eccaa25afa7f5",
            "pictures": {
                "16x9": "ec6938e37fb95efc6d5eccaa25afa7f5",
                "2x3": "19e16a35aef87a171a04a744e4360a4e",
                "3x4": "0051bbf3793e2e64b0114eb7cff8872b",
                "4x3": "153cb138245c309f52e440f5c42e6adb"
            },
            "genreIDs": null,
            "ratings": [
                "{Motion Picture Association of America}/{Restricted}/{R}",
                "{Manitoba Film Classification Board}/{14 Accompaniment}/{14A}",
                "{Alberta's Film Classification Board}/{14A}/{14A}",
                "{B.C. Film Classification Office}/{14A}/{14A}",
                "{Saskatchewan Film and Video Classification Board}/{14A}/{14A}",
                "{British Board of Film Classification}/{15}/{15}",
                "{Ontario Film Authority}/{18A}/{18A}",
                "{Maritime Film Classification Board}/{Adult Accompaniment}/{14}",
                "{UK Content Provider}/{15}/{15}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
                "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
                "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed from 12 years}/{K12}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Conseil Supérieur de l'Audiovisuel}/{Allowed from 10 years}/{-10}",
                "{Ministero dei Beni e delle Attività Culturali e del Turismo}/{All ages admitted.}/{T}",
                "{Ley de Medios Audiovisuales}/{}/{SAM 13}",
                "{Medietilsynet}/{Tillatt for alle}/{A}"
            ],
            "ratingAdvisories": [
                "Adult Language",
                "Adult Situations",
                "Strong Sexual Content"
            ],
            "regionIDs": [],
            "assetIDs": [],
            "genres": null,
            "contentLock": false,
            "metadata": {
                "source": "",
                "id": ""
            }
        }
```



### 3. Retrieve event from the on-demand catalog


Retrieves the specified event from the on-demand catalog.



<br>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested VOD entry|
|404		|1040				|*Not Found*: No matching VOD entry found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/vod/events/00f0c2a2-36bd-411a-b8ba-f324e156e9cb
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 4. Delete VOD event


Deletes the specified VOD event. 

<!-- Original URL: {{OCMServer}}/ocm/v2/vod/events/a34b99fd-5454-411c-b2ae-1765541ac7c2 -->

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|vodEventID	|string		|required	|ID for the targeted VOD event. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified VOD event.|
|404		|1040	|*Not Found*: No matching VOD event ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/vod/events/{{eventID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 5. Patch VOD event


Patches the specified VOD event resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID of the VOD event to be updated. | 

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| needsMetadata | | boolean | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/events/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "publishStart": "2019-02-02T01:00:00Z",
    "publishEnd": "2020-12-31T01:00:00Z",
    "contentLock": true,
    "duration": 1200,
    "name": "ONE Warrior: Season 1 Episode 5",
    "shortName": "ONE Warrior: Season 1 Episode 5",
    "description": "ONE Warrior: Season 1 Episode 5",
    "shortDescription": "ONE Warrior: Season 1 Episode 5",
    "language": "en",
    "pictureID": "c2d3dca2-34e3-4de4-904a-5c816acbf22b.jpg",
    "pictures": {
        "16x9": "c2d3dca2-34e3-4de4-904a-5c816acbf22b.jpg",
        "2x3": "",
        "3x4": "",
        "4x3": ""
    },
    "genreIDs": null,
    "ratings": null,
    "ratingAdvisories": null,
    "regionIDs": [
        "7bb71990-1e8d-11e9-900e-9d49235d5db0"
    ]
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "0f213237-3461-4ea4-9836-05ab1e5df723",
    "timestamp": "2020-03-25T18:16:26.426715Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "vod/events": [
        {
            "id": "b9767894-9abe-4c4d-9bc5-b169352a95dd",
            "resourceType": "vod/events",
            "publishStart": "2019-02-02T01:00:00Z",
            "publishEnd": "2020-12-31T01:00:00Z",
            "published": true,
            "created": "0001-01-01T00:00:00Z",
            "updated": "2020-03-25T18:16:26.422Z",
            "contentLock": true,
            "duration": 1200,
            "name": "ONE Warrior: Season 1 Episode 5",
            "shortName": "ONE Warrior: Season 1 Episode 5",
            "description": "ONE Warrior: Season 1 Episode 5",
            "shortDescription": "ONE Warrior: Season 1 Episode 5",
            "language": "en",
            "pictureID": "c2d3dca2-34e3-4de4-904a-5c816acbf22b.jpg",
            "pictures": {
                "16x9": "c2d3dca2-34e3-4de4-904a-5c816acbf22b.jpg",
                "2x3": "",
                "3x4": "",
                "4x3": ""
            },
            "genreIDs": null,
            "ratings": null,
            "ratingAdvisories": null,
            "regionIDs": [
                "7bb71990-1e8d-11e9-900e-9d49235d5db0"
            ],
            "assetIDs": [
                "89938fb9-2b64-40a8-bc3a-23db511ce12f"
            ],
            "genres": null,
            "metadata": {
                "source": "",
                "id": ""
            }
        }
    ]
}
```



## v2/vod/movies



### 1. Create VOD movie


Creates a movie entry in the on-demand catalog.

<!-- ???  |**200**|*VOD Movie information*|[VodMovieResponse](#vodmovieresponse)| -->

<br/>

##### Request parameters

|Field|Data type|Required|Description|Type
|---|---|---|---|---|
|`movieID`|string|Yes|Asset identifier|**path**|
|`language`|string|Yes|Requested language|**query**|

<!--
{
    "resourceType": "vod/movies",
    "startTime": "2010-01-01T00:00:00.000+00:00",
    "endTime": "",
    "duration": 1,
    "name": "Sex and the City 2",
    "shortName": "Sex City 2",
    "description": "Basada en la serie de televisión.",
    "shortDescription": "Basada en la serie de televisión.",
    "pictureID": "ec6938e37fb95efc6d5eccaa25afa7f5",
    "pictures": {
        "2x3": "19e16a35aef87a171a04a744e4360a4e",
        "3x4": "0051bbf3793e2e64b0114eb7cff8872b",
        "4x3": "153cb138245c309f52e440f5c42e6adb",
        "16x9": "ec6938e37fb95efc6d5eccaa25afa7f5"
    },
    "genreIDs": [],
    "language": "es",
    "ratings": [
        "{Motion Picture Association of America}/{Restricted}/{R}",
        "{Manitoba Film Classification Board}/{14 Accompaniment}/{14A}",
        "{Alberta's Film Classification Board}/{14A}/{14A}",
        "{B.C. Film Classification Office}/{14A}/{14A}",
        "{Saskatchewan Film and Video Classification Board}/{14A}/{14A}",
        "{British Board of Film Classification}/{15}/{15}",
        "{Ontario Film Authority}/{18A}/{18A}",
        "{Maritime Film Classification Board}/{Adult Accompaniment}/{14}",
        "{UK Content Provider}/{15}/{15}",
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
        "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
        "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed from 12 years}/{K12}",
        "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
        "{Conseil Supérieur de l'Audiovisuel}/{Allowed from 10 years}/{-10}",
        "{Ministero dei Beni e delle Attività Culturali e del Turismo}/{All ages admitted.}/{T}",
        "{Ley de Medios Audiovisuales}/{}/{SAM 13}",
        "{Medietilsynet}/{Tillatt for alle}/{A}"
    ],
    "ratingAdvisories": [
        "Adult Language",
        "Adult Situations",
        "Strong Sexual Content"
    ],
    "regionIDs": null,
    "releaseYear": 0
}


-->

<br/>

##### Response Object

| Field  | Parent  |Type  | Description |  
|------:|---|------|-------------|
| requestID || string | Generated log ID for this request.    |   | 
| timestamp || string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| vod/movies    ||      |      |  |
| id | | string | Unique ID for each asset.  |  |
| resourceType | | enum string | *vod/movies*   | |
| pictureID || string | URL for the picture resource. |  | 
| duration | | number | Video duration in minutes.  |  |
| publishStart  | | string | (optional) First date that this content is visible to end users.  ISO 8601 format |
| publishEnd | |  string | (optional) Last date that this content is visible to end users.  ISO 8601 format |

<br/>


##### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**400**|1103, 1104, 1105|*Bad request*: Request body malformed.|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired.|
|**403**|1004|*Forbidden*: Cannot write the requested resource.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/movies
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |



***Body:***

```js        
{
    "resourceType": "vod/movies",
    "startTime": "2010-01-01T00:00:00.000+00:00",
    "endTime": "",
    "duration": 1,
    "name": "Sex and the City 2",
    "shortName": "Sex City 2",
    "description": "Basada en la serie de televisión.",
    "shortDescription": "Basada en la serie de televisión.",
    "pictureID": "ec6938e37fb95efc6d5eccaa25afa7f5",
    "pictures": {
        "2x3": "19e16a35aef87a171a04a744e4360a4e",
        "3x4": "0051bbf3793e2e64b0114eb7cff8872b",
        "4x3": "153cb138245c309f52e440f5c42e6adb",
        "16x9": "ec6938e37fb95efc6d5eccaa25afa7f5"
    },
    "genreIDs": [],
    "language": "es",
    "ratings": [
        "{Motion Picture Association of America}/{Restricted}/{R}",
        "{Manitoba Film Classification Board}/{14 Accompaniment}/{14A}",
        "{Alberta's Film Classification Board}/{14A}/{14A}",
        "{B.C. Film Classification Office}/{14A}/{14A}",
        "{Saskatchewan Film and Video Classification Board}/{14A}/{14A}",
        "{British Board of Film Classification}/{15}/{15}",
        "{Ontario Film Authority}/{18A}/{18A}",
        "{Maritime Film Classification Board}/{Adult Accompaniment}/{14}",
        "{UK Content Provider}/{15}/{15}",
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
        "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
        "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed from 12 years}/{K12}",
        "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
        "{Conseil Supérieur de l'Audiovisuel}/{Allowed from 10 years}/{-10}",
        "{Ministero dei Beni e delle Attività Culturali e del Turismo}/{All ages admitted.}/{T}",
        "{Ley de Medios Audiovisuales}/{}/{SAM 13}",
        "{Medietilsynet}/{Tillatt for alle}/{A}"
    ],
    "ratingAdvisories": [
        "Adult Language",
        "Adult Situations",
        "Strong Sexual Content"
    ],
    "regionIDs": null,
    "releaseYear": 0
}
```



### 2. Update VOD movie


Updates the specified content associated with the target movie from the on-demand catalog.

<!-- |**200**|*VOD Movie information*|[VodMovieResponse](#vodmovieresponse)| -->

<br/>

##### Path parameters

|Name|Data type|Required|Description
|---|---|---|---|
|id|string|required| Identifier for the asset to be updated.|

<!--

<br/>


{
    "resourceType": "vod/movies",
    "startTime": "2010-01-01T00:00:00.000+00:00",
    "endTime": "",
    "duration": 1,
    "name": "Sex and the City 2",
    "shortName": "Sex City 2",
    "description": "Basada en la serie de televisión.",
    "shortDescription": "Basada en la serie de televisión.",
    "pictureID": "ec6938e37fb95efc6d5eccaa25afa7f5",
    "pictures": {
        "2x3": "19e16a35aef87a171a04a744e4360a4e",
        "3x4": "0051bbf3793e2e64b0114eb7cff8872b",
        "4x3": "153cb138245c309f52e440f5c42e6adb",
        "16x9": "ec6938e37fb95efc6d5eccaa25afa7f5"
    },
    "genreIDs": [],
    "language": "es",
    "ratings": [
        "{Motion Picture Association of America}/{Restricted}/{R}",
        "{Manitoba Film Classification Board}/{14 Accompaniment}/{14A}",
        "{Alberta's Film Classification Board}/{14A}/{14A}",
        "{B.C. Film Classification Office}/{14A}/{14A}",
        "{Saskatchewan Film and Video Classification Board}/{14A}/{14A}",
        "{British Board of Film Classification}/{15}/{15}",
        "{Ontario Film Authority}/{18A}/{18A}",
        "{Maritime Film Classification Board}/{Adult Accompaniment}/{14}",
        "{UK Content Provider}/{15}/{15}",
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
        "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
        "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed from 12 years}/{K12}",
        "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
        "{Conseil Supérieur de l'Audiovisuel}/{Allowed from 10 years}/{-10}",
        "{Ministero dei Beni e delle Attività Culturali e del Turismo}/{All ages admitted.}/{T}",
        "{Ley de Medios Audiovisuales}/{}/{SAM 13}",
        "{Medietilsynet}/{Tillatt for alle}/{A}"
    ],
    "ratingAdvisories": [
        "Adult Language",
        "Adult Situations",
        "Strong Sexual Content"
    ],
    "regionIDs": null,
    "releaseYear": 0
}

-->

<br>

##### Response object

| Name | Parent |Type  | Description |
|------:|---	|------|-------------|
| requestID |	| string | Generated log ID for this request.    |   | 
| timestamp |	| string | Generated log timestamp for this request.  |   |  
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
| vod/movies    ||      |      |  |
| id | | string | | Unique ID for each asset.  |  |
| resourceType || enum string | *vod/movies*   | |
| pictureID | | string | URL for the picture resource. |  | 
| duration || number | Video duration in minutes.  |  |
| publishStart |  | string | (optional) First date that this content is visible to end users. ISO 8601 format |
| publishEnd |  | string | (optional) Last date that this content is visible to end users. ISO 8601 format |

<br/>

##### Error Responses
|HTTP Code| Error Code |Description|
|---|---|---|
|**400**|1103, 1104, 1105|*Bad request*: Request body malformed|
|**401**|1000, 1001, 1002|*Unauthorized*: Authentication token missing, invalid, or expired|
|**403**|1004|*Forbidden*: Cannot update the requested resource|
|**404**|1040|*Not Found*: No matching VOD entry found|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/movies/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation.  |
| If-None-Match | {{If-None-Match}} | *Optional*. Cache control header for reads. |



***Body:***

```js        
{
    "resourceType": "vod/movies",
    "startTime": "2010-01-01T00:00:00.000+00:00",
    "endTime": "",
    "duration": 1,
    "name": "Sex and the City 2",
    "shortName": "Sex City 2",
    "description": "Basada en la serie de televisión.",
    "shortDescription": "Basada en la serie de televisión.",
    "pictureID": "ec6938e37fb95efc6d5eccaa25afa7f5",
    "pictures": {
        "2x3": "19e16a35aef87a171a04a744e4360a4e",
        "3x4": "0051bbf3793e2e64b0114eb7cff8872b",
        "4x3": "153cb138245c309f52e440f5c42e6adb",
        "16x9": "ec6938e37fb95efc6d5eccaa25afa7f5"
    },
    "genreIDs": [],
    "language": "es",
    "ratings": [
        "{Motion Picture Association of America}/{Restricted}/{R}",
        "{Manitoba Film Classification Board}/{14 Accompaniment}/{14A}",
        "{Alberta's Film Classification Board}/{14A}/{14A}",
        "{B.C. Film Classification Office}/{14A}/{14A}",
        "{Saskatchewan Film and Video Classification Board}/{14A}/{14A}",
        "{British Board of Film Classification}/{15}/{15}",
        "{Ontario Film Authority}/{18A}/{18A}",
        "{Maritime Film Classification Board}/{Adult Accompaniment}/{14}",
        "{UK Content Provider}/{15}/{15}",
        "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
        "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
        "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed from 12 years}/{K12}",
        "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
        "{Conseil Supérieur de l'Audiovisuel}/{Allowed from 10 years}/{-10}",
        "{Ministero dei Beni e delle Attività Culturali e del Turismo}/{All ages admitted.}/{T}",
        "{Ley de Medios Audiovisuales}/{}/{SAM 13}",
        "{Medietilsynet}/{Tillatt for alle}/{A}"
    ],
    "ratingAdvisories": [
        "Adult Language",
        "Adult Situations",
        "Strong Sexual Content"
    ],
    "regionIDs": null,
    "releaseYear": 0
}
```



### 3. Retrieve movie from the on-demand catalog


Returns the information associated with the specified movie from the on-demand catalog.

<!-- original endpoint string:
	{{OCMServer}}/ocm/v2/vod/movies/c92a91a31be26c3187d4ce89a5c201f5?language=*&include=assets
-->

<br>

##### Path Parameters

|Field|Data type|Required|Description
|---|---|---|---|
|movieID|string|required|Asset identifier|

<br>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested VOD entry|
|404		|1040				|*Not Found*: No matching VOD entry found|

<br/>

##### Response Object

<!-- The Notes column describes default and possible values, valid ranges. --->

| Field  | Parent |  Type  | Description |  
|------:|--------|--------|-------------|
| requestID |    | string | Generated log ID for this request.    | 
| timestamp |    | string | Generated log timestamp for this request.  | 
||||||
| `metadata`|	| object | Pagination fields.  |   |  
| count     |`metadata`	| number  | Number of items listed in this response; min = 0, max = 100.
| totalCount|`metadata`	| number | Total number of items returned by the request.
| offset	|`metadata`	| number	| Number of items skipped from the start of the list; default = 0.
||||||
| `assets` |   |   |      |  |
| id | `assets`  |string | Unique ID for each season.  |  |
| resourceType | `assets`   | string | *`assets`*  | |
| pictureID | `assets`  | string | ID for the standard image |  | 
| duration | `assets`  | number | Show duration in minutes.
  |  |
| environment | `assets`  | string | Enum: prod or test   |  |
| live | `assets`  | boolean | Is this a live event? Value may be *false* or *true*. |
| liveURLs | `assets`  | string | URLs for live feeds.  | 
| `vodURLs`| `assets` | | URLs for video on demand sources. |  | 
| `dash` | `vodURLs` | |Sources using the [DASH](https://www.wikiwand.com/en/Dynamic_Adaptive_Streaming_over_HTTP) protocol. | |
| primary | `dash` | string | Primary URL for the DASH source.   |  | 
| `hls` | `vodURLs` |  | Sources using the [HLS](https://www.wikiwand.com/en/HTTP_Live_Streaming) protocol.| | 
| primary | `hls` | string | Primary URL for the HLS source.   |  |
||||||
| `vod/movies` |   |   | List of VOD/movies.   |  |
| id | `vod/movies`  |string | Unique ID for each asset.  |  |
| resourceType | `vod/movies` | enum string | *`vod/movies`*   | |
| startTime | `vod/movies` | string | Starting time in ISO-8601 timestamp format. |  |
| endTime | `vod/movies` | string  | Ending time in ISO-8601 timestamp format. |  |
| name | `vod/movies` | string | Full name.  |  |
| shortName | `vod/movies` | string | Abbreviated name for the asset.  |  |
| description | `vod/movies`  | string | Full description.  |  |
| shortDescription | `vod/movies` | string | Short description.  |  |
| genreIDs | `vod/movies`  | string list | List of genre IDs associated with this asset. | |
| language | `vod/movies`  | string | Two-letter code for the spoken language.  |  |
| ratings  | `vod/movies`  | string | Content ratings by boards and associations.  |
| ratingAdvisories | `vod/movies`  | string list | A list of content advisories such as "Adult Situations", "Language", or "Violence" |
| regionIDs | `vod/movies`  | string list | List of region IDs associated with this competition. | |
| releaseYear | `vod/movies`  | number | Original release year for this movie.  | |
| duration | `vod/movies`  | number | Show duration in minutes.  |  |
| assetIDs | `vod/movies`  | string | Comma-separated list of asset IDs associated with this VOD/movie. | |
| pictureID | `vod/movies`  | string | ID for the standard image |  | 
||||||
| `pictures` | `vod/movies`|  | IDs for images with specific dimensions.  |  |
| 2x3  | `pictures` | string | ID for a 2x3 image. |  | 
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  | 
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  | 
| 16x9 | `pictures` | string | ID for a 16x9 image.  |  |

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/vod/movies/c92a91a31be26c3187d4ce89a5c201f5
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |
| include | assets | Includes descriptive metadata. |



***Responses:***


Status: Retrieve movie from the on-demand catalog | Code: 200



```js
{
    "requestID": "35bc89e8-f4c7-4c60-865f-4138eddab8fb",
    "timestamp": "2018-05-15T04:28:33.110144787Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "assets": [
        {
            "id": "33e23db5b036404b699c364b31a94ae7",
            "resourceType": "assets",
            "pictureID": "",
            "duration": 0,
            "live": false,
            "environment": "",
            "liveURLs": null,
            "vodURLs": {
                "dash": {
                    "primary": "https://dtvlatamvod-isp.akamaized.net/alpha/edcoutput/B02591306HD/B02591306HDDirecTVHDPELICULAS_4472849.mpd"
                },
                "hls": {
                    "primary": "https://dtvlatamvod-isp.akamaized.net/alpha/edcoutput/B02591306HD/master_fp.m3u8"
                }
            }
        }
    ],
    "vod/movies": [
        {
            "id": "c92a91a31be26c3187d4ce89a5c201f5",
            "resourceType": "vod/movies",
            "startTime": "2010-01-01T00:00:00.000+00:00",
            "endTime": "",
            "duration": 0,
            "name": "Sex and the City 2",
            "shortName": "Sex City 2",
            "description": "Basada en la serie de televisión.",
            "shortDescription": "Basada en la serie de televisión.",
            "pictureId": "ec6938e37fb95efc6d5eccaa25afa7f5",
            "pictures": {
                "2x3": "19e16a35aef87a171a04a744e4360a4e",
                "3x4": "0051bbf3793e2e64b0114eb7cff8872b",
                "4x3": "153cb138245c309f52e440f5c42e6adb",
                "16x9": "ec6938e37fb95efc6d5eccaa25afa7f5"
            },
            "genreIDs": null,
            "language": "es",
            "ratings": [
                "{Motion Picture Association of America}/{Restricted}/{R}",
                "{Manitoba Film Classification Board}/{14 Accompaniment}/{14A}",
                "{Alberta's Film Classification Board}/{14A}/{14A}",
                "{B.C. Film Classification Office}/{14A}/{14A}",
                "{Saskatchewan Film and Video Classification Board}/{14A}/{14A}",
                "{British Board of Film Classification}/{15}/{15}",
                "{Ontario Film Authority}/{18A}/{18A}",
                "{Maritime Film Classification Board}/{Adult Accompaniment}/{14}",
                "{UK Content Provider}/{15}/{15}",
                "{Departamento de Justiça, Classificação, Títulos e Qualificação}/{14 anos}/{14}",
                "{Freiwillige Selbstkontrolle der Filmwirtschaft}/{Released to age 12 or older and to age 6 or older with parental guidance.}/{12}",
                "{Mediakasvatus- ja kuvaohjelmayksikkö}/{Allowed from 12 years}/{K12}",
                "{Australian Classification Board}/{Mature Accompanied}/{MA 15+}",
                "{Conseil Supérieur de l'Audiovisuel}/{Allowed from 10 years}/{-10}",
                "{Ministero dei Beni e delle Attività Culturali e del Turismo}/{All ages admitted.}/{T}",
                "{Ley de Medios Audiovisuales}/{}/{SAM 13}",
                "{Medietilsynet}/{Tillatt for alle}/{A}"
            ],
            "ratingAdvisories": [
                "Adult Language",
                "Adult Situations",
                "Strong Sexual Content"
            ],
            "regionIDs": null,
            "releaseYear": 0,
            "assetIDs": [
                "33e23db5b036404b699c364b31a94ae7"
            ]
        }
    ]
}
```



### 4. Delete VOD movie


Deletes the specified VOD movie. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|vodMovieID	|string		|required	|ID for the targeted VOD movie. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified VOD movie.|
|404		|1040	|*Not Found*: No matching VOD movie ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/vod/movies/{{movieID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 5. Patch VOD movie


Patches the specified VOD movie resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID of the VOD movie to be updated. | 

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| pictureID |   	| string, max=512 | ID for the standard image. |
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| releaseYear | | number, min=1 max=3000 | The movie relese year |
| countryOfOrigin | | string list, allows null | | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| metadata |        | object | The metadata provider information for this resource. |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| needsMetadata | | boolean | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/movies/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "duration": 5400,
    "name": "Pop Star",
    "shortName": "Pop Star",
    "pictures": {
        "16x9": "9d843b6f-9026-441a-ab0b-da0f791a9579.jpg",
        "1x1": "aa610104-5047-46c7-8712-40f37a4c9d2a.jpg",
        "2x3": "8ae8bb81-9bc7-4625-9a3f-afce65bb74d1.jpg",
        "3x4": "db91111b-536e-49a9-bc35-41f7909fe368.jpg",
        "4x3": "6166eaf3-b118-4c5a-8d5b-4b9b1eaedee0.jpg"
    },
    "genreIDs": [
        "6149ecce-a902-4120-aeb4-c11ff4860a5c",
        "9c89a2ab-829b-486f-9cde-93f1d9154f62"
    ],
    "language": "es",
    "ratings": [
        "Motion Picture Association of America/Parental Guidance Suggested/PG",
        "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 12 or older and to age 6 or older with parental guidance./12",
        "Manitoba Film Classification Board/General/G",
        "Régie du cinéma/General/G"
    ],
    "ratingAdvisories": null,
    "regionIDs": [
        "2e167237-c7bb-423b-b606-c31115adb1da",
        "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
        "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
        "141a53b6-af6f-4092-ba1f-c289659310f2",
        "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6",
        "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
        "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
        "08329e10-c274-11e8-9b06-4d8a411f55a1"
    ],
    "releaseYear": 2013,
    "countryOfOrigin": null,
    "assetIDs": [
        "d28924157601631fca1cf032ccabebc5"
    ]
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "a9df17e2-9d41-4ebe-9180-012e69b7df2a",
    "timestamp": "2020-03-24T06:22:51.592598Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "vod/movies": [
        {
            "id": "627649118e9c9e03ff130f6cfba0a29e",
            "resourceType": "vod/movies",
            "publishStart": "2019-03-18T18:39:06.454Z",
            "published": true,
            "created": "0001-01-01T00:00:00Z",
            "updated": "2020-03-24T06:22:51.588Z",
            "contentLock": false,
            "duration": 5400,
            "name": "Pop Star",
            "shortName": "Pop Star",
            "description": "Un productor de música convence a una talentosa cantante a prestar su voz para una celebridad sin talento a cambio de un futuro contrato de grabación.",
            "shortDescription": "Una talentosa cantante debe prestar su voz para una celebridad sin talento a cambio de un contrato.",
            "pictureID": "9d843b6f-9026-441a-ab0b-da0f791a9579.jpg",
            "pictures": {
                "16x9": "9d843b6f-9026-441a-ab0b-da0f791a9579.jpg",
                "1x1": "aa610104-5047-46c7-8712-40f37a4c9d2a.jpg",
                "2x3": "8ae8bb81-9bc7-4625-9a3f-afce65bb74d1.jpg",
                "3x4": "db91111b-536e-49a9-bc35-41f7909fe368.jpg",
                "4x3": "6166eaf3-b118-4c5a-8d5b-4b9b1eaedee0.jpg"
            },
            "genreIDs": [
                "6149ecce-a902-4120-aeb4-c11ff4860a5c",
                "9c89a2ab-829b-486f-9cde-93f1d9154f62"
            ],
            "language": "es",
            "ratings": [
                "Motion Picture Association of America/Parental Guidance Suggested/PG",
                "Freiwillige Selbstkontrolle der Filmwirtschaft/Released to age 12 or older and to age 6 or older with parental guidance./12",
                "Manitoba Film Classification Board/General/G",
                "Régie du cinéma/General/G"
            ],
            "ratingAdvisories": null,
            "regionIDs": [
                "2e167237-c7bb-423b-b606-c31115adb1da",
                "5c3c1351-ed28-4cfa-8031-91c8a14912a5",
                "12f4f0eb-387e-4ff3-b8d0-a30c77acfe74",
                "141a53b6-af6f-4092-ba1f-c289659310f2",
                "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6",
                "1f9ff77b-e2a4-487c-a1bf-63c88b9439f0",
                "f5881a70-c07e-11e8-b4bb-adc8f08569d4",
                "08329e10-c274-11e8-9b06-4d8a411f55a1"
            ],
            "releaseYear": 2013,
            "countryOfOrigin": null,
            "assetIDs": [
                "d28924157601631fca1cf032ccabebc5"
            ],
            "genres": [
                {
                    "id": "6149ecce-a902-4120-aeb4-c11ff4860a5c",
                    "name": "Comedia-drama"
                },
                {
                    "id": "9c89a2ab-829b-486f-9cde-93f1d9154f62",
                    "name": "Romántico"
                }
            ],
            "metadata": {
                "source": "com.gracenote.on-v3",
                "id": "MV004885230000",
                "status": "Mapped"
            }
        }
    ]
}
```



## v2/vod/teamcompetitions



### 1. Create VOD Team Competition


Creates a schedule entry for a VOD team competition.

<br>

##### Body Parameters
All fields are optional unless otherwise indicated.

| Field			| Parent	|  Type	| Description |
|--------------:|-----------|-------|-------------|
| resourceType	|| enum string	| Required. Contains the value **vod/teamCompetitions**. | 
| startTime |   	| string | Required. Start time in ISO-8601 timestamp format.  | 
| endTime |     	| string | Required. Ending time in ISO-8601 timestamp format.  |  
| duration |    	| number | Required. Video duration in minutes.  |  
| name    		|| string | Required. Full competition name. . . |
| shortName   	|| string | Shortened competition name. . . |
| description |     | string | Full description. . .|
| shortDescription| | string | Shortened description. . .|
| language    	|| string | Required. Two-letter code for the spoken language.  |
| pictureID |   	| string | ID for the standard image. | 
|||||
| `pictures` |      | object | Images in various sizes for this team competition. | 
| 2x3  | `pictures` | string | ID for a 2x3 image.  |  
| 3x4  | `pictures` | string | ID for a 3x4 image.  |  
| 4x3  | `pictures` | string | ID for a 4x3 image.  |  
| 16x9 | `pictures` | string | ID for a 16x9 image. |  
| ratings |     	| string list | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| stationID |   	| string | ID for the station associated with this team competition. . . ?| 
| genreIDs |    	| string list | List of genre IDs associated with this team competition. | 
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this team competition. |
| sportID |     	| string | ID for the sport associated with this team competition. | 
| sportName |   	| string | Name for the sport associated with this team competition. | 
| tournamentID |    | string | ID for the tournament associated with this team competition.  | 
| tournamentName |  | string | Name for the tournament associated with this team competition. | 
| primaryTeamID |     	| string | ID for the primary or home team. | 
| primaryTeamName |   	| string | Name for the primary or home team. | 
| primaryTeamPictureID |  | string | ID for picture of the primary or home team. | 
| secondaryTeamID | 	  | string | ID for the secondary or away team. | 
| secondaryTeamName |     | string | Name for the secondary or away team. | 
| secondaryTeamPictureID| | string | ID for picture of the secondary or away team. | 
| publishStart 	|| string | Required. Availability start date in ISO-8601 timestamp format.  | 
| publishEnd   	|| string | Required. Availability end date in ISO-8601 timestamp format.  |  

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target game.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/teamCompetitions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "vod/teamCompetitions",
    "publishStart": "2018-01-01T00:00:00Z",
    "publishEnd": "2020-01-01T00:00:00Z",
    "name": "Monstruo: Se Busca",
    "shortName": "Monstruo",
    "description": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
    "shortDescription": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
    "venue": "",
    "duration": 0,
    "genreIDs": null,
    "language": "es",
    "ratings": [
        "{Canadian Parental Rating}/{}/{PG}",
        "{USA Parental Rating}/{}/{TVPG}"
    ],
    "ratingAdvisories": null,
    "regionIDs": null,
    "pictures": {
        "16x9": "e310931fff6c87d136725a31e4c763b5",
        "2x3": "3e30c8ab1e8fc496aa7ab6258ecf6c74",
        "3x4": "b21b21545e2e60313b0a05e9336fdcaf",
        "4x3": "39b6c70c17031b8a84ff81a9e96dac3c"
    },
    "pictureID": "e310931fff6c87d136725a31e4c763b5",
    "sportID": "d2fcc8f2f2e04ff67204e272bd93b1b7",
    "sportName": "Fishing",
    "leagueID": "",
    "leagueName": "",
    "gameID": "1234",
    "tournamentID": "75bd3585eb1a1138932dd23b9d004868",
    "tournamentName": "Monstruo: Se Busca",
    "primaryTeamID": "",
    "primaryTeamName": "",
    "primaryTeamPictureID": "",
    "secondaryTeamID": "",
    "secondaryTeamName": "",
    "secondaryTeamPictureID": "",
    "providerID": "",
    "assetIDs": [
        "8dd59b4c-064b-4f88-8eea-4414c11e7177"
    ],
    "genres": null
}
```



### 2. Update VOD Team Competition


Updates a schedule entry for a VOD team competition.

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| teamCompetitionID		|string		|required	|ID for the target VOD team competition. |

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/teamCompetitions/{{teamCompetitionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Content-Type | application/json | ETag header for cache validation. |



***Body:***

```js        
{
    "resourceType": "vod/teamCompetitions",
    "publishStart": "2018-01-01T00:00:00Z",
    "publishEnd": "2020-01-01T00:00:00Z",
    "published": true,
    "name": "Test",
    "shortName": "Monstruo",
    "description": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
    "shortDescription": "Cyril se enfrentará al pez lucio, devorador de patos y ratas almizcleras. El pez lobo posee una boca llena de dientes bien afilados que lo convierte en un gran depredador.",
    "venue": "",
    "duration": 0,
    "genreIDs": null,
    "language": "es",
    "ratings": [
        "{Canadian Parental Rating}/{}/{PG}",
        "{USA Parental Rating}/{}/{TVPG}"
    ],
    "ratingAdvisories": null,
    "regionIDs": null,
    "pictures": {
        "16x9": "e310931fff6c87d136725a31e4c763b5",
        "2x3": "3e30c8ab1e8fc496aa7ab6258ecf6c74",
        "3x4": "b21b21545e2e60313b0a05e9336fdcaf",
        "4x3": "39b6c70c17031b8a84ff81a9e96dac3c"
    },
    "pictureID": "e310931fff6c87d136725a31e4c763b5",
    "sportID": "d2fcc8f2f2e04ff67204e272bd93b1b7",
    "sportName": "Fishing",
    "leagueID": "",
    "leagueName": "",
    "gameID": "1234",
    "tournamentID": "75bd3585eb1a1138932dd23b9d004868",
    "tournamentName": "Monstruo: Se Busca",
    "primaryTeamID": "",
    "primaryTeamName": "",
    "primaryTeamPictureID": "",
    "secondaryTeamID": "",
    "secondaryTeamName": "",
    "secondaryTeamPictureID": "",
    "providerID": "",
    "assetIDs": [
        "8dd59b4c-064b-4f88-8eea-4414c11e7177"
    ],
    "genres": null
}
```



### 3. Retrieve team game from the on-demand catalog


Retrieves the specified team game from the on-demand catalog.

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| teamCompetitionID		|string		|required	|ID for the target VOD team competition. |

<br/>

##### Error Responses

|HTTP Code	|Error Code			|Description|
|---		|---				|---|
|400		|1050, 1060			|*Bad Request*: Request data bad or incomplete|
|401		|1000, 1001, 1002	|*Unauthorized*: Authentication token missing, invalid, or expired|
|403		|1003				|*Forbidden*: Caller not authorized to read the requested VOD competition entry|
|404		|1040				|*Not Found*: No matching scheduled VOD competition found|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v2/vod/teamCompetitions/{{teamCompetitionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| language | * | Code for the requested language. Use __*__ as a wildcard for all languages. Default value is __en__ for English. |



***Responses:***


Status: Retrieve team game from the on-demand catalog | Code: 200



```js
{"requestID":"884a6319-d138-4af4-84a4-d525d5d0880b","timestamp":"2018-05-15T04:28:09.909810814Z","metadata":{"count":1,"totalCount":1,"offset":0},"vod/teamCompetitions":[{"id":"3df321e0d555329f75859682a4f18485","resourceType":"vod/competitions","name":"Fútbol Copa Libertadores","shortName":"Fútbol","description":"Jornada 2 del Grupo F de la Copa Conmebol Libertadores 2018. Santos, viene de caer de visitante 2-0 ante Real Garcilaso, recibe a Nacional, que igualó sin goles contra Estudiantes en Uruguay. Desde el Estadio Urbano Caldeira.","shortDescription":"Jornada 2 del Grupo F de la Copa Conmebol Libertadores 2018. Santos, viene de caer de visitante 2-0 ante Real Garcilaso, recibe a Nacional, que igualó sin goles contra Estudiantes en Uruguay. Desde el Estadio Urbano Caldeira.","duration":0,"genreIDs":null,"language":"es","ratings":null,"ratingAdvisories":null,"regionIDs":null,"pictures":{"2x3":null,"3x4":null,"4x3":null,"16x9":null},"pictureID":"","sportID":"d670cf71cb7709020618a03c5208c84e","sportName":"Soccer","tournamentID":"","tournamentName":"Fútbol Copa Libertadores","primaryTeamID":"699f82255ddd75f675c4128a52e3054d","primaryTeamName":"","primaryTeamPictureID":"","secondaryTeamID":"ff6717e473e80bf698bf2f50e3621595","secondaryTeamName":"Club Nacional","secondaryTeamPictureID":"","assetIDs":null}]}
```



### 4. Delete VOD team competition


Deletes the specified VOD team competition. 

<br/>

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
|vodTeamCompetitionID	|string		|required	|ID for the targeted VOD team competition. |

<br/>

##### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to remove the specified VOD team competition.|
|404		|1040	|*Not Found*: No matching VOD team competition ID found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: 
URL: {{OCMServer}}/ocm/v2/vod/teamCompetitions/62c3acf6-773b-4c1b-b114-f0310f2d1669
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 5. Patch VOD team competition


Patches the specified VOD team competition resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path parameters

|Name|Data type|Required|Description|
|---|---|---|---|
|id |string| required | ID of the VOD team competition to be updated. | 

<br>

##### Body Parameters

| Field  | Parent |  Type  | Description |
|------:|--------|--------|-------------|
| publishStart |    | string, format=date-time allows null | First date that this content is visible to end users. ISO 8601 format. |
| publishEnd |      | string, format=date-time allows null | Last date that this content is visible to end users. ISO 8601 format. |
| contentLock |     | boolean | |
| name |    		| string, min=1 max=512 | Full name for the resource. |
| shortName |   	| string, max=512 | Shortened name for the resource. |
| description |     | string, max=10240 | Full description for the resource.|
| shortDescription| | string, max=10240 | Shortened description for the resource.|
| venue |           | string | |
| duration |    	| number, min=0 max=86400 | Video duration in minutes.  |  
| genreIDs |    	| string list, allows null | List of genre IDs associated with this resource. | 
| language |    	| string, min=2 max=2 | Two-letter code for the spoken language.  |
| ratings |     	| string list, allows null | Age-related ratings from boards and agencies. |
| ratingAdvisories| | string list, allows null | A list of content advisories. Such as "Adult Situations", "Language", or "Violence". |
| regionIDs |    	| string list, allows null | List of region IDs associated with this resource. | 
| pictures |      | object, allows null | Images in various sizes for this resource. |
| 1x1  | pictures | string, max=512 | ID for a 1x1 image.  |
| 2x3  | pictures | string, max=512 | ID for a 2x3 image.  | 
| 3x4  | pictures | string, max=512 | ID for a 3x4 image.  |  
| 4x3  | pictures | string, max=512 | ID for a 4x3 image.  |  
| 16x9 | pictures | string, max=512 | ID for a 16x9 image. |  
| pictureID |   	| string, max=512 | ID for the standard image. |
| sportID |     	| string | ID for the sport associated with this resource. | 
| sportName |   	| string | Name for the sport associated with this resource. | 
| leagueID |        | string | |
| leagueName |      | string | |
| tournamentID |    | string | ID for the tournament associated with this resource.  | 
| tournamentName |  | string | Name for the tournament associated with this resource. | 
| gameID |    		| string | ID for the game associated with this resource. | 
| primaryTeamID |     	| string | ID for the primary or home team. | 
| primaryTeamName |   	| string | Name for the primary or home team. | 
| primaryTeamPictureID |  | string | ID for picture of the primary or home team. | 
| secondaryTeamID | 	  | string | ID for the secondary or away team. | 
| secondaryTeamName |     | string | Name for the secondary or away team. | 
| secondaryTeamPictureID| | string | ID for picture of the secondary or away team. |
| assetIDs |    	| string list | Comma-separated list of asset IDs to associate with this resource. |
| metadata |        | object |  |
| source | metadata | string | Metadata provider id. |
| id | metadata | string | Metadata provider entity id. |
| status | metadata | string | Status of metadata provider entity. |
| needsMetadata | | boolean | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v2/vod/teamCompetitions/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |
| Content-Type | application/json |  |



***Body:***

```js        
{
    "name": "Bahrain F1 GP: Practice 1 (times unconfirmed)",
    "shortName": "Bahrain F1 GP: Practice 1 (times unconfirmed)",
    "description": "Bahrain F1 GP: Practice 1 (times unconfirmed)",
    "shortDescription": "Bahrain F1 GP: Practice 1 (times unconfirmed)",
    "duration": 7200,
    "regionIDs": [
        "7bb71990-1e8d-11e9-900e-9d49235d5db0"
    ],
    "sportID": "1ac4e585-28d0-4a71-acf8-5bfef2b3be60",
    "sportName": "Auto Racing",
    "leagueID": "53650746-a157-4fe2-8d2c-b80888280116",
    "leagueName": "Generic"
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "bfc2b28e-e162-410f-8102-dc50f5ae70ef",
    "timestamp": "2020-03-25T18:13:17.779576Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "vod/teamCompetitions": [
        {
            "id": "96d118f2-ee09-4772-bc8b-5175aff25254",
            "resourceType": "vod/teamCompetitions",
            "publishStart": "2020-03-20T10:45:00Z",
            "publishEnd": "2020-05-20T12:45:00Z",
            "published": true,
            "created": "2020-02-10T02:06:08.994Z",
            "updated": "2020-03-25T18:13:17.777Z",
            "linkIDs": [
                "2d0db2b6-3d7b-4376-9825-80318c93d8d1"
            ],
            "contentLock": false,
            "name": "Bahrain F1 GP: Practice 1 (times unconfirmed)",
            "shortName": "Bahrain F1 GP: Practice 1 (times unconfirmed)",
            "description": "Bahrain F1 GP: Practice 1 (times unconfirmed)",
            "shortDescription": "Bahrain F1 GP: Practice 1 (times unconfirmed)",
            "venue": "",
            "duration": 7200,
            "genreIDs": null,
            "language": "en",
            "ratings": null,
            "ratingAdvisories": null,
            "regionIDs": [
                "7bb71990-1e8d-11e9-900e-9d49235d5db0"
            ],
            "pictures": {
                "16x9": "",
                "2x3": "",
                "3x4": "",
                "4x3": ""
            },
            "pictureID": "",
            "sportID": "1ac4e585-28d0-4a71-acf8-5bfef2b3be60",
            "sportName": "Auto Racing",
            "leagueID": "53650746-a157-4fe2-8d2c-b80888280116",
            "leagueName": "Generic",
            "tournamentID": "",
            "tournamentName": "",
            "gameID": "",
            "primaryTeamID": "",
            "primaryTeamName": "",
            "primaryTeamPictureID": "",
            "secondaryTeamID": "",
            "secondaryTeamName": "",
            "secondaryTeamPictureID": "",
            "providerID": "145419dd-21f3-4b00-975f-537b58d03eeb",
            "assetIDs": [
                "9f2e83da-8591-4ee8-9e0a-a9316e5efced"
            ],
            "genres": null,
            "metadata": {
                "source": "",
                "id": "145419dd-21f3-4b00-975f-537b58d03eeb"
            }
        }
    ]
}
```



## v2/workflow



### 1. Create a resource based on a gameID


Creates a resource based on a VOD team competition.

<br/>

##### Body Parameters
|Field|Data type|Required|Description
|---|---|---|---|
|gameID|string|required|ID for the target VOD team competition.|
|resourceType|string|required|Contains the value "vod/teamCompetitions".|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v2/resourceFromGame
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
   "gameID": "01a59985-b449-4bfb-92f4-537bbd2f1a31",
   "resourceType": "vod/teamCompetitions"
}
```



## v3



### 1. Retrieve personalized page


Returns a page of recommended assets for the calling user.  The response contains the page structure and the first carousel section.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|pageid	|string	|required	|ID of the page created in Contentwise.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v3/pages/HOME
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| include | entitlements | *Optional*.  Additional related data to include in the response. The only supported value currently is **entitlements**. |



***Responses:***


Status: Get personalized page | Code: 200



```js
{
    "requestID": "c9606782-505a-4bf7-9a92-90b3ca748e4d",
    "timestamp": "2018-08-02T19:28:06.159357609Z",
    "page": {
        "sections": [
            {
                "label": "Curated carousel label",
                "sectionID": "100035:2@@default@@100029:2@@1@~@0~0",
                "subsections": [
                    {
                        "blockId": "100035:2@@default@@100029:2@@1",
                        "blockLabel": "Curated carousel label",
                        "blockType": "LAYOUT",
                        "items": [
                            {
                                "assetIDs": [
                                    "adc9aab54436b1a75de4fe4636dbf537"
                                ],
                                "description": "Desde su prisión, Miguel Hidalgo recuerda momentos de su vida, en particular su tiempo como cura en el pequeño pueblo de San Felipe Torres Mochas.",
                                "duration": 0,
                                "genreIDs": [
                                    "caebf4a82e81dc0958cea3ac8da61e27"
                                ],
                                "genres": [
                                    {
                                        "id": "caebf4a82e81dc0958cea3ac8da61e27",
                                        "name": "Drama"
                                    }
                                ],
                                "id": "c4d1725a5926051ad9720526480ab760",
                                "language": "es",
                                "name": "Hidalgo: La historia jamás contada",
                                "pictureID": "8b5cec0f1dd6f15c583f7daa1bf8dc9f",
                                "pictures": {
                                    "16x9": "b0c8e1627271b8183551ee21ee9ff049",
                                    "2x3": "6d7d8e716b37690c19d10744b63a0baa",
                                    "3x4": "4dffd81c4f8c1a5a4eed6ce89385d890",
                                    "4x3": "d2d1033786606c2948bf40b8034bb0e3"
                                },
                                "ratingAdvisories": null,
                                "ratings": null,
                                "regionIDs": null,
                                "releaseYear": 2010,
                                "resourceType": "vod/movies",
                                "shortDescription": "Desde su prisión, Hidalgo recuerda momentos de su vida.",
                                "shortName": "Hidalgo"
                            }
                        ]
                    }
                ]
            },
            {
                "sectionId": "100035:2@@default@@100012:1@@2@~@1~0"
            },
            {
                "sectionId": "100035:2@@default@@100012:1@@3@~@2~0"
            }
        ],
        "title": "MAIN"
    }
}
```



### 2. Get personalized section (carousel)


Retrieves a subsequent section list of recommended assets for the calling user.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---			|
|pageid	|string	|required	|ID of the page created in Contentwise.|
|sectionid	|string	|required	|ID of the section to be retrieved.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v3/pages/{{pageid}}/sections/{{sectionid}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |
| Geo-Position | 39.10;-76.77 | Global position specified as {_longitude;latitude_}. |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| include | entitlements | *Optional*.  Additional related data to include in the response. The only supported value currently is **entitlements**. |



***Responses:***


Status: Get personalized section | Code: 200



```js
{
    "requestID": "20c6a363-2921-4ac8-b036-d1fbf2bc2687",
    "timestamp": "2018-08-02T19:29:56.920650649Z",
    "section": {
        "label": "Curated carousel label",
        "sectionID": "100035:2@@default@@100029:2@@1@~@0~0",
        "subsections": [
            {
                "blockId": "100035:2@@default@@100029:2@@1",
                "blockLabel": "Curated carousel label",
                "blockType": "LAYOUT",
                "items": [
                    {
                        "assetIDs": [
                            "adc9aab54436b1a75de4fe4636dbf537"
                        ],
                        "description": "Desde su prisión, Miguel Hidalgo recuerda momentos de su vida, en particular su tiempo como cura en el pequeño pueblo de San Felipe Torres Mochas.",
                        "duration": 0,
                        "genreIDs": [
                            "caebf4a82e81dc0958cea3ac8da61e27"
                        ],
                        "genres": [
                            {
                                "id": "caebf4a82e81dc0958cea3ac8da61e27",
                                "name": "Drama"
                            }
                        ],
                        "id": "c4d1725a5926051ad9720526480ab760",
                        "language": "es",
                        "name": "Hidalgo: La historia jamás contada",
                        "pictureID": "8b5cec0f1dd6f15c583f7daa1bf8dc9f",
                        "pictures": {
                            "16x9": "b0c8e1627271b8183551ee21ee9ff049",
                            "2x3": "6d7d8e716b37690c19d10744b63a0baa",
                            "3x4": "4dffd81c4f8c1a5a4eed6ce89385d890",
                            "4x3": "d2d1033786606c2948bf40b8034bb0e3"
                        },
                        "ratingAdvisories": null,
                        "ratings": null,
                        "regionIDs": null,
                        "releaseYear": 2010,
                        "resourceType": "vod/movies",
                        "shortDescription": "Desde su prisión, Hidalgo recuerda momentos de su vida.",
                        "shortName": "Hidalgo"
                    }
                ]
            }
        ]
    }
}
```



## v4



### 1. Add page configuration


Creates a carousel page. 

Each carousel page may have several regions; each region is composed of one or more sections.
The "default" region is used whenever a Subscriber requests content from a region that is not available in the regions list.

<br>

##### Body Parameters

| Field  | Parent  |Type  | Description |  
|-------:|---------|------|-------------|
| id  |  | string | UID generated for this page configuration. | 
| `regions` |  |object| Set of regions defined for the page. | 
| *`region_id`* | `regions` | object | UID generated for this region. | 
| title 	| *`region_id`* | string | Title for this region.   |  
| sectionIDs| *`region_id`* | string list| List of sections for this region.  | 
| `default` | | object | UID generated for the default region. | 
| title 	| `default`| string | Title for the default region. | 
| sectionIDs| `default`| string list | List of sections for the default region. |  

<br>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v4/pages/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
    "id": "SheilaTest",
    "layouts": [
        {
            "title": "Argentina Home",
            "sectionIDs": [
                "FEATURED_AR",
                "LIVE_AR",
                "WATCHLIST",
                "CONTINUEWATCHING"
            ],
            "conditions": {
                "regionIDs": [
                    "74d9f086-2495-417d-9c51-4b0c62c604c6"
                ],
                "startTime": "2019-03-25T18:35:49.628Z",
                "endTime": "2019-03-25T18:35:49.628Z"
            }
        },
        {
            "title": "Brazil Home",
            "sectionIDs": [
                "FEATURED_BR",
                "WATCHLIST",
                "CONTINUEWATCHING"
            ],
            "conditions": {
                "regionIDs": [
                    "28dj472b-5b4a-4710-bacb-784b3acf5809"
                ]
            }
        }
    ],
    "default": {
        "title": "Home",
        "sectionIDs": [
            "FEATURED",
            "LIVE",
            "WATCHLIST",
            "CONTINUEWATCHING"
        ]
    }
}
```



### 2. Update page configuration


Updates the specified carousel page configuration. 

<br>

Each carousel page may have several regions; each region is composed of one or more sections.
The "default" region is used whenever a user requests content from a region that is not available in the regions list.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|pageID	|string |required	|UID for the target page.|

<br/>

##### Body Parameters

| Field  | Parent  |Type  | Description |  
|-------:|---------|------|-------------|
| `regions` |  |object| Set of regions defined for the page. | 
| *`region_id`* | `regions` | object | UID generated for this region. | 
| title 	| *`region_id`* | string | Title for this region.   |  
| sectionIDs| *`region_id`* | string list| List of sections for this region.  | 
| `default` | | object | UID generated for the default region. | 
| title 	| `default`| string | Title for the default region. | 
| sectionIDs| `default`| string list | List of sections for the default region. |  

<br/> 

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v4/pages/config/{{pageID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
    "layouts": [
        {
            "title": "Argentina Home",
            "sectionIDs": [
                "FEATURED_AR",
                "LIVE_AR",
                "WATCHLIST",
                "CONTINUEWATCHING"
            ],
            "conditions": {
            	"regionIDs": ["74d9f086-2495-417d-9c51-4b0c62c604c6"],
            	            "startTime": "2019-03-25T18:35:49.628Z",
            "endTime": "2019-03-25T18:35:49.628Z"
            }
        },
        {
            "title": "B Home",
            "sectionIDs": [
                "FEATURED_BR",
                "WATCHLIST",
                "CONTINUEWATCHING"
            ],
            "conditions": {
            	"regionIDs": ["28dj472b-5b4a-4710-bacb-784b3acf5809"]
            }
        }
    ],
    "default": {
        "title": "Home",
        "sectionIDs": [
            "FEATURED_AR",
            "LIVE",
            "WATCHLIST",
            "CONTINUEWATCHING"
        ]
    }
}
```



### 3. Delete page configuration


Deletes the specified carousel page configuration.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|pageID	|string |required	|UID for the target page.|

<br/>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v4/pages/config/{{pageID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 4. Retrieve page configuration


Returns the specified carousel page configuration.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|pageID	|string |required	|UID for the target page.|

<br/>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v4/pages/config/{{pageID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 5. Retrieve section configuration


Retrieves the specified editorial section configuration for carousels. 

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|sectionID	|string |required	|UID for the target section to be retrieved.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v4/sections/config/{{sectionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 6. Retrieve page


Returns the specified carousel page and displays its first section.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|pageID	|string |required	|UID for the target page.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v4/pages/{{pageID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 7. Add editorial section configuration


Generates an editorial section for a carousel page configuration.

<br/>

##### Body Parameters
|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|id		|string |required	|UID generated for this new section.|
|type	|string |required	|Section type. Set to _EDITORIAL_.|
|title	|string |required	|Title for this new section.|
|resourceIDs	|string list |required	|Asset IDs for the content items that can appear in this section.|

<br/>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v4/sections/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
    "id": "{{sectionID}}",
    "type": "EDITORIAL",
    "title": "Destacado",
    "resourceIDs": [
        "c1cf81cda1ed5db4001e096c8785de46",
        "c1cf81cda1ed5db4001e096c8785de47",
        "c1cf81cda1ed5db4001e096c8785de48"
    ]
}
```



### 8. Add "currently live" section


Generates an editorial section containing "live" content that is currently (or will soon be) available for viewing.

<br>

You can select content:

* Currently playing (ON_NOW)
* Starting soon (ON_NEXT)
* Both currently playing and starting soon (ON_NOW_NEXT)

<br/>

##### Body Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|id		|string |required	|Unique ID the user enters. Alphanumeric only.|
|type	|string |required	|Section type. Value must be set to _LIVE_.|
|title	|string |required	|Title for this new section.|
|stationIDs	|string list|optional	|Station/channel IDs. If left blank all, content for all channels will be included.|
|selection|string|required|One of: _ON_NOW_, _ON_NEXT_, _ON_NOW_NEXT_.|
|resourceTypes|string list|required|Any combination of  of _live/competitions_, _live/events_, _live/teamCompetitions_, _epg/competition_, _epg/episode_, _epg/events_, _epg/movies_, _epg/teamCompetitions_|
|maxResourceCount	|number |required	|Maximum number of results that will appear in the collection. Valid range is 1 to 50.|


<br/>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.



<!-- Add error info:

   "errorCode": 1043,
    "errorMessage": "Resource already exists"

    "errorCode": 1050,
    "errorMessage": "Failed to parse input:1050 - 400: failed validation schema: resourceTypes.1:{resourceTypes.1 must be one of the following: \"epg/competitions\", \"epg/teamCompetitions\", \"epg/events\", \"epg/movies\", \"epg/episodes\", \"live/competitions\", \"live/teamCompetitions\", \"live/events\"},(root):{Must validate at least one schema (anyOf)},resourceTypes.0:{resourceTypes.0 must be one of the following: \"epg/competitions\", \"epg/teamCompetitions\", \"epg/events\", \"epg/movies\", \"epg/episodes\", \"live/competitions\", \"live/teamCompetitions\", \"live/events\"} (failed validation schema: (root):{Must validate at least one schema (anyOf)},resourceTypes.0:{resourceTypes.0 must be one of the following: \"epg/competitions\", \"epg/teamCompetitions\", \"epg/events\", \"epg/movies\", \"epg/episodes\", \"live/competitions\", \"live/teamCompetitions\", \"live/events\"},resourceTypes.1:{resourceTypes.1 must be one of the following: \"epg/competitions\", \"epg/teamCompetitions\", \"epg/events\", \"epg/movies\", \"epg/episodes\", \"live/competitions\", \"live/teamCompetitions\", \"live/events\"})"

-->


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v4/sections/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
    "id": "LIVE_AR",
    "type": "LIVE",
    "title": "Live in Argentina",
    "resourceTypes": [
        "epg/movies",
        "live/teamCompetitions"
    ],
    "channelIDs": [
        "c1cf81cda1ed5db4001e096c8785de48",
        "c1cf81cda1edasd"
    ]
}
```



### 9. Add a "continue watching" section


Generates the list of assets that the subscriber has started but not yet finished watching.
This carousel section is automatically personalized and updated for each subscriber account.

<br/>

##### Body Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|id		|string |required	|Set to _CONTINUEWATCHING_ for this section type.|
|type	|string |required	|Set to _CONTINUEWATCHING_ for this section type.|
|title	|string |required	|Title for this section.|

<br/>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v4/sections/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
   "id": "CONTINUEWATCHING",
   "type": "CONTINUEWATCHING",
   "title": "Continue assistindo"
}
```



### 10. Add a "watch later" section


Generates the list of assets that the subscriber has added to their "to watch" list.
This carousel section is personalized for each subscriber.

<br/>

##### Body Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|id		|string |required	|Set to _WATCHLATER_ for this section type.|
|type	|string |required	|Set to _WATCHLATER_ for this section type.|
|title	|string |required	|Title for this section.|

<br/>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{OCMServer}}/ocm/v4/sections/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
   "id": "WATCHLATER",
   "type": "WATCHLATER",
   "title": "Lista assista mais tarde"
}
```



### 11. Update editorial section configuration


Updates the specified editorial section configuration for carousels. 

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|sectionID	|string |required	|UID for the target section to be updated.|

<br/>

##### Body Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|type	|string |required	|Section type. Set to _EDITORIAL_.|
|title	|string |required	|Updated title for this section.|
|resourceIDs	|string list |required	|Updated list of asset IDs to appear in this section.|

<br>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{OCMServer}}/ocm/v4/sections/config/{{sectionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



***Body:***

```js        
{
    "type": "EDITORIAL",
    "title": "Destacado",
    "resourceIDs": [
        "c1cf81cda1ed5db4001e096c8785de48"
    ]
}
```



### 12. List all sections configured for a tenant


Retrieves all carousel section configurations for the current tenant.

<br>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v4/sections/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 13. List all pages configured for a tenant


Lists all carousel page configurations for the current tenant.

<br>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v4/pages/config
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 14. Delete section configuration


Deletes the specified carousel section configuration.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|sectionId	|string |required	|UID for the target section to be deleted.|

<br/>

**NOTE**: This endpoint is authorized for Internal Use Only by iStreamPlanet and is _subject to change without notice_.


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{OCMServer}}/ocm/v4/sections/config/{{sectionId}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 15. Get section


Retrieves and displays the specified carousel section.

Call this endpoint to retrieve additional sections beyond the first carousel section for a page.

<br/>

##### Path Parameters
|Label	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|sectionID	|string |required	|UID for the target section.|

<br/>

<!-- 

* Results are filtered by region.
* Retrieves all banners; banners do not have region attributes. 

-->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{OCMServer}}/ocm/v4/sections/{{sectionID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json | Content data type returned (string). |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



### 16. Patch page configuration


Patches the specified page configuration resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the page configuration to be updated. |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v4/pages/config/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |



***Body:***

```js        
{
    "layouts": [
        {
            "sectionIDs": [
                "Featured2",
                "Documentalesydocuseries"
            ],
            "conditions": {
                "regionIDs": [
                    "5c3c1351-ed28-4cfa-8031-91c8a14912a5"
                ]
            }
        },
        {
            "title": "Mexico",
            "sectionIDs": [
                "Featured",
                "moviesMix"
            ],
            "conditions": {
                "regionIDs": [
                    "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6"
                ]
            }
        }
    ],
    "default": {
        "title": "Default",
        "sectionIDs": [
            "Featured"
        ],
        "conditions": {}
    }
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "75c7e139-a98e-4451-9a86-a08d077f85bb",
    "timestamp": "2020-03-25T20:30:52.539145Z"
}
```



### 17. Patch section configuration


Patches the specified section configuration resource.

<br>

The body of a PATCH API request is a JSON merge patch document which specifies changes to be made to a target resource. 
The patch document uses syntax that closely resembles the structure of the resource being modified. 
This patch document consists of a subset of any of the top level fields. 
Top level object fields must either be completely specified or null, if allowed, as shown in the example.

<br>

<!--
The body of a PATCH API request is a JSON merge patch document. A JSON merge patch document specifies changes to be made to a target resource using a syntax that closely resembles the resource being modified. 

A JSON merge patch document consists of a subset of any of the the top level fields. Top level object fields must be completely specified, or null if allowed, see examples.
-->

##### Path Parameters
|Label		|Type		|Required	|Description|
|---		|---		|---		|---		|
| id		|string		|required	|ID of the section configuration to be updated. |

<br>

##### Body Parameters
|Label	|Type	|Description	|
|---	|---	|---			|
|title	|string 	|Updated title for this section.|
|type	|string 	|Section type. Set to EDITORIAL.|
|resourceIDs	|string list 	|Updated list of asset IDs to appear in this section.|
|stationIDs | string list | |
|selection| string | |
|resourceTypes | string list | |
|maxResourceCount |number | |


***Endpoint:***

```bash
Method: PATCH
Type: RAW
URL: {{OCMServer}}/ocm/v4/sections/config/{{id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Session token required to authenticate the request. |



***Body:***

```js        
{
    "resourceIDs": [
        "2bb04a60-723e-4a1f-8e75-ed14c2870be0"
    ]
}
```



***Responses:***


Status: Example 1 | Code: 200



```js
{
    "requestID": "4852f788-33e3-4ffb-9439-24d0b5d3b0e7",
    "timestamp": "2020-03-25T20:34:22.676383Z"
}
```



---
[Back to top](#content)
> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2020-04-08 15:59:28 by [docgen](https://github.com/thedevsaddam/docgen)