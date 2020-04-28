---
id: api-content-reporting
title: Content Reporting
sidebar_label: Content Reporting
---

The _content reporting_ endpoints allow inspecting and troubleshooting quality issues in the VOD show and movie catalogs. 
The catalog report data is automatically updated with information from the metadata provider every 12 hours.

--------

## Content Reporting


### Generate mediaflow reports

Forces an immediate update of the data for the movie reports.

<br>

Report data for the VOD catalog updates every 12 hours. 
However, if you need more up-to-date information, 
you can call this endpoint to refresh the movie report data within about 5 minutes.


***Endpoint:***

```bash
Method: POST
Type: 
URL: {{CMRServer}}/cmr/v1/report/generate/mediaflow
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



### Generate movie reports

Forces an immediate update of the movie reports from the VOD catalog. 
Regenerated movie reports are available about 5 minutes after the request.

<br>

VOD catalog report data is automatically updated every 12 hours.
This endpoint refreshes the show reports with the most current catalog data available.

<br>


***Endpoint:***

```bash
Method: POST
Type: 
URL: {{CMRServer}}/cmr/v1/report/generate/movies
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



### Get movie report

Returns a detailed view of metadata provider and OCM movie information for side-by-side comparison. 

<!-- Original endpoint: {{CMRServer}}/cmr/v1/report/movies/MV006412610000 -->

<br>

This view is available to help troubleshoot movies for which OCM resources do not precisely match with their metadata provider counterparts.

<br>

##### Path Parameters
|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|movieID	|string |required	|ID for the target movie.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{CMRServer}}/cmr/v1/report/movies/{{movieID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



***Responses:***


Status: Get Movie Report | Code: 200



```js
{
    "requestID": "2c3b6902-c9e9-4c0b-b094-ff5d65dc11f6",
    "timestamp": "2019-08-22T00:12:20.326546359Z",
    "item": {
        "id": "MV006412610000",
        "title": "47 Ronin: La leyenda del samurái",
        "programmappings": [
            {
                "status": "Mapped",
                "paid": "TITL2019070312503407",
                "availability": {
                    "start": "2019-07-04T00:00:00Z",
                    "end": "2020-01-17T00:00:00Z"
                }
            },
            {
                "status": "Mapped",
                "paid": "TITL2019070211183117",
                "availability": {
                    "start": "2019-07-04T00:00:00Z",
                    "end": "2020-01-17T00:00:00Z"
                }
            }
        ],
        "mapId": [
            "dd32ef9d-bea0-42a1-a6d4-c5be8df890a0",
            "6787c539-8b0c-40f7-a4ec-033f5af6be4b"
        ],
        "resources": [
            {
                "id": "6787c539-8b0c-40f7-a4ec-033f5af6be4b",
                "resourceType": 12,
                "publishStart": "2019-07-04T00:00:00Z",
                "publishEnd": "2020-01-17T00:00:00Z",
                "published": true,
                "contentLock": false,
                "name": "47 Ronin: La leyenda del samurái",
                "shortName": "47 Ronin: La leyenda del samurái",
                "language": "es",
                "assetID": "5b19b21e-a2a8-412b-b199-661dc76160bb",
                "regionIDs": [
                    "f917cff6-025a-4917-84d6-fb686697d93c",
                    "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6"
                ],
                "metadata": {
                    "id": "MV006412610000",
                    "source": "com.gracenote.on-v3",
                    "status": "Mapped"
                },
                "asset": {
                    "contentProvider": {
                        "id": "ffa3097e-32ad-4ab3-bc6f-2b5f29aae876",
                        "category": "15153d96d9f779062921cf6472085a20",
                        "assetid": "TITL2019070211183117"
                    }
                }
            },
            {
                "id": "dd32ef9d-bea0-42a1-a6d4-c5be8df890a0",
                "resourceType": 12,
                "publishStart": "2019-07-04T00:00:00Z",
                "publishEnd": "2020-01-17T00:00:00Z",
                "published": true,
                "contentLock": false,
                "name": "47 Ronin: La leyenda del samurái",
                "shortName": "47 Ronin: La leyenda del samurái",
                "language": "es",
                "assetID": "c3ee43fe-e676-417c-9fa0-218d969ab354",
                "regionIDs": [
                    "f917cff6-025a-4917-84d6-fb686697d93c",
                    "6f5a23f0-ce64-11e8-8fc8-5ffa72a08bf6"
                ],
                "metadata": {
                    "id": "MV006412610000",
                    "source": "com.gracenote.on-v3",
                    "status": "Mapped"
                },
                "asset": {
                    "contentProvider": {
                        "id": "ffa3097e-32ad-4ab3-bc6f-2b5f29aae876",
                        "category": "15153d96d9f779062921cf6472085a20",
                        "assetid": "TITL2019070312503407"
                    }
                }
            }
        ]
    }
}
```



### Get movies report

Returns general quality metrics for:

* __resourceTotals__ <br>
 The total number of resources from GI and OCM accessed to generate the reports.

* __allMovies__ <br>
 Quality metrics for all movies.

<br>

#### Resource Totals

| Field | Description |
|---------------------------|------------------------------------------------------------------------------------------------|
| numEpisodeResources       | OCM vod/episodes (11) with metadata and with a non-empty metadata id |
| numPubEpisodeResources    | Published OCM vod/episode |
| numSeasonResources        | OCM season (7) |
| numShowResources          | OCM show (8) with a provider id that starts with SH |
| numPubShowResources       | Published OCM shos |
| numShows                  | Metadata provider programs (shows) with a TMSID that starts with SH |
| numEpisodes               | Metadata provider programs (episodes) with a TMSID that starts with EP |
| numJoinedEpisodeResources | OCM vod/episodes joined to metadata provider episodes by TMSID |
| numJoinedShowResources    | OCM shows joined to metadata provider shows by TMSID |
| numJoinedSeasonEpisodes   | Metadata provider episodes joined to seasons |
| numJoinedShowEpisodes     | Metadata provider episodes joined to shows without seasons |


#### Shows With VOD Episodes

| Field | Description |
|---------------------------|------------------------------------------------------------------------------------------------|
| numShows                  | Metadata provider shows |
| numShowResources          | OCM shows |
| numUnmappedShows          | Metadata provider shows not mapped to an OCM show by GI |
| numShowsWithDupResource   | Metadata provider shows that have duplicate OCM shows |
| numLockedShowResources    | OCM locked shows |
| unmappedShows             | List of show TMSIDs for numUnmappedShows |
| showsWithDupResources     | List of show TMSIDs for numShowsWithDupResource |
| seasons                   | Seasons report |
| episodes                  | Episodes report |


#### Seasons

| Field | Description |
|--------------------------------------|-------------------------------------------------------------------------------------|
| numShowsWithSeasons                  | Metadata provider shows that have seasons |
| numShowsWithMissingSeasons           | Metadata provider shows that have more seasons than the OCM show |
| numShowsWithExtraSeasons             | Metadata provider shows that have fewer seasons than the OCM show |
| numShowsWithMismatchedSeasonNumbers  | Metadata provider shows that have season numbers mismatched with the OCM show seasons |
| numShowsWithUnmappedSeasons          | Metadata provider shows that have seasons not mapped to OCM seasons by GI |
| numSeasons                           | Metadata provider seasons |
| numUnmappedSeasons                   | Metadata provider seasons not mapped to an OCM season by GI |
| numSeasonsWithMismatchedShowID       | OCM seasons with incorrect show uplink |
| showsWithMissingSeasons              | List of show TMSIDs for numShowsWithMissingSeasons |
| showsWithExtraSeasons                | List of show TMSIDs for numShowsWithExtraSeasons |
| showsWithMismatchedSeasonNumbers     | List of show TMSIDs for numShowsWithMismatchedSeasonNumbers |
| ShowsWithUnmappedSeasons             | List of show TMSIDs for numShowsWithUnmappedSeasons |
| showsWithSeasonsWithMismatchedShowID | List of show TMSIDs for numSeasonsWithMismatchedShowID |


#### Episodes
| Field | Description |
|--------------------------------------|-------------------------------------------------------------------------------------|
| numEpisodes                          | Metadata provider episodes |
| numEpisodesWithPaid                  | Metadata provider episodes with a provider asset ID (PAID) |
| numEpisodesWithResources             | Metadata provider episodes with OCM resources |
| numUnmappedEpisodes                  | Metadata provider episodes not mapped to an OCM resource by GI |
| numLockedEpisodes                    | OCM locked episode resources |
| numShowsWithMissingEpisodes          | Metadata provider shows that have more episodes than the OCM show resource |
| numShowsWithExtraEpisodes            | Metadata provider shows that have fewer episodes than the OCM show resource |
| numShowsWithMissingEpisodeIDs        | Metadata provider shows that have mapped OCM episodes missing from the OCM show vod/episodes | 
| numShowsWithExtraEpisodeIDs          | OCM show with vod/episodes missing from the metadata provider show mapped episodes |
| numEpisodesWithDupResources          | Metadata provider episodes with duplicate OCM episodes |
| numEpisodesWithDupPublishedResources | Metadata provider episodes with duplicate published OCM episodes |
| numShowsWithDupEpisodes              | Metadata provider shows that have duplicate OCM episodes |
| numShowsWithDupPublishedEpisodes.    | Metadata provider shows that have duplicate published OCM episodes |
| numEpisodesWithMismatchedShowID      | OCM episodes with incorrect show uplink |
| numEpisodesWithMismatchedSeasonID    | OCM episodes with incorrect season uplink |
| numEpisodesMissingRegions            | OCM episodes with missing regions |
| numShowsWithEpisodesMissingRegions   | OCM shows with episodes missing regions |
| numEpisodesWithMismatchedPaid        | OCM episodes with PAID that does not match the metadata provider episode PAID |
| numShowsWithEpisodesWithMismatchedPaid | OCM shows with episodes with mismatch PAID |
| showsWithMissingEpisodes             | List of show TMSIDs for numShowsWithMissingEpisodes |            
| showsWithExtraEpisodes               | List of show TMSIDs for numShowsWithExtraEpisodes |
| showsWithMissingEpisodeIDs           | List of show TMSIDs for numShowsWithMissingEpisodeIDs |
| showsWithExtraEpisodeIDs             | List of show TMSIDs for numShowsWithExtraEpisodeIDs |
| showsWithDupEpisodes                 | List of show TMSIDs for numShowsWithDupEpisodes |
| episodesMissingRegions               | List of show TMSIDs for numEpisodesMissingRegions |
| showsWithEpisodesMissingRegions      | List of show TMSIDs for numShowsWithEpisodesMissingRegions |
| episodesWithMismatchedPaid           | List of episode TMSIDs for numEpisodesWithMismatchedPaid |
| showsWithEpisodesWithMismatchedPaid  | List of show TMSIDs for numShowsWithEpisodesWithMismatchedPaid |

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{CMRServer}}/cmr/v1/report/movies
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Accept | application/json |  |



***Responses:***


Status: Get Movies Report | Code: 200



```js
{
    "requestID": "fc806ca8-5168-460b-963d-a79544f36f6a",
    "timestamp": "2019-08-22T00:11:20.797808209Z",
    "item": {
        "updated": "2019-08-21T21:12:49.774Z",
        "type": "all",
        "resourceTotals": {
            "numMovieResources": 1419,
            "numPubMovieResources": 1234,
            "numMovies": 7896,
            "numJoinedMovieResources": 1419
        },
        "allMovies": {
            "numMovies": 7896,
            "numMoviesWithPaid": 1945,
            "numMoviesResources": 1419,
            "numUnmappedMovies": 0,
            "numLockedMovies": 0,
            "numMoviesWithDupResources": 229,
            "numMoviesWithDupPublishedResources": 191,
            "numMoviesMissingRegions": 0,
            "numMoviesWithMismatchedPaid": 1,
            "moviesWithDupResources": [
                "MV000422670000",
                "MV000529580000",
                "MV000530550000",
                "MV000550950000",
                "MV000594000000",
                "MV000602980000",
                "MV000621370000",
                "MV000623260000",
                "MV000634080000",
                "MV000676110000",
                "MV000678590000",
                "MV000681790000",
                "MV000683380000",
                "MV000712760000",
                "MV000729430000",
                "MV000795640000",
                "MV000805730000",
                "MV000860790000",
                "MV000910660000",
                "MV000918680000",
                "MV000985340000",
                "MV001045490000",
                "MV001141260000",
                "MV001159760000",
                "MV001273460000",
                "MV001339080000",
                "MV001445560000",
                "MV001455820000",
                "MV001512590000",
                "MV001581940000",
                "MV001605650000",
                "MV001630160000",
                "MV001640510000",
                "MV001668680000",
                "MV001732110000",
                "MV001760500000",
                "MV001764430000",
                "MV001816040000",
                "MV001904470000",
                "MV001932960000",
                "MV001945170000",
                "MV001973860000",
                "MV002009790000",
                "MV002023300000",
                "MV002116240000",
                "MV002140210000",
                "MV002205840000",
                "MV002404240000",
                "MV002408810000",
                "MV002574190000",
                "MV002670930000",
                "MV002680230000",
                "MV002705150000",
                "MV002714310000",
                "MV003441150000",
                "MV003492030000",
                "MV003793220000",
                "MV003875960000",
                "MV003902490000",
                "MV003954620000",
                "MV004009110000",
                "MV004011910000",
                "MV004013870000",
                "MV004015730000",
                "MV004147060000",
                "MV004312070000",
                "MV004367500000",
                "MV004469940000",
                "MV004495270000",
                "MV004681120000",
                "MV004688730000",
                "MV004837950000",
                "MV004861910000",
                "MV004923710000",
                "MV004981470000",
                "MV005003860000",
                "MV005006360000",
                "MV005028400000",
                "MV005043670000",
                "MV005188570000",
                "MV005366830000",
                "MV005393250000",
                "MV005496960000",
                "MV005677130000",
                "MV005716570000",
                "MV005759290000",
                "MV005839340000",
                "MV005909650000",
                "MV006090300000",
                "MV006139790000",
                "MV006284860000",
                "MV006412610000",
                "MV006536040000",
                "MV006606930000",
                "MV006672940000",
                "MV006989910000",
                "MV007065070000",
                "MV007339370000",
                "MV007433850000",
                "MV007599690000",
                "MV007835630000",
                "MV007846250000",
                "MV007882460000",
                "MV007906090000",
                "MV007911990000",
                "MV007973750000",
                "MV008127790000",
                "MV008214250000",
                "MV008224920000",
                "MV008325830000",
                "MV008594860000",
                "MV008595570000",
                "MV008686100000",
                "MV008765680000",
                "MV008887640000",
                "MV009042090000",
                "MV009076080000",
                "MV009215870000",
                "MV009361930000",
                "MV009436840000",
                "MV009483760000",
                "MV009628200000",
                "MV009736910000",
                "MV009834780000",
                "MV009957850000",
                "MV009996290000",
                "MV010040210000",
                "MV010043940000",
                "MV010074950000",
                "MV010078380000",
                "MV010102350000",
                "MV010111360000",
                "MV010125460000",
                "MV010116830000",
                "MV010173880000",
                "MV010228270000",
                "MV010230110000",
                "MV010280170000",
                "MV010354160000",
                "MV010437850000",
                "MV010517040000",
                "MV010570790000",
                "MV010572830000",
                "MV010498650000",
                "MV010587100000",
                "MV010721180000",
                "MV010721190000",
                "MV010752570000",
                "MV010749000000",
                "MV010752530000",
                "MV010790670000",
                "MV010800690000",
                "MV010802050000",
                "MV010817010000",
                "MV010818740000",
                "MV010818890000",
                "MV010875700000",
                "MV010819950000",
                "MV010818470000",
                "MV010850130000",
                "MV010875970000",
                "MV010817110000",
                "MV010857610000",
                "MV010818950000",
                "MV010903410000",
                "MV010886960000",
                "MV010944960000",
                "MV010965160000",
                "MV011081210000",
                "MV011041500000",
                "MV011643760000",
                "MV011631790000",
                "MV011631780000",
                "MV011645330000",
                "MV011620770000",
                "MV011661810000",
                "MV011772940000",
                "MV011822430000",
                "MV011919140000",
                "MV011924560000",
                "MV011942840000",
                "MV011944500000",
                "MV011974470000",
                "MV011994660000",
                "MV012064560000",
                "MV012075520000",
                "MV012099770000",
                "MV012131640000",
                "MV012072010000",
                "MV012238330000",
                "MV012285310000",
                "MV012302400000",
                "MV012246830000",
                "MV012355320000",
                "MV012348560000",
                "MV012349800000",
                "MV012357610000",
                "MV012360790000",
                "MV012389440000",
                "MV012425140000",
                "MV012411810000",
                "MV012429490000",
                "MV012369300000",
                "MV012431580000",
                "MV012416030000",
                "MV012428130000",
                "MV012425150000",
                "MV012428360000",
                "MV012427990000",
                "MV012441390000",
                "MV012460220000",
                "MV012529730000",
                "MV012583660000",
                "MV012529770000",
                "MV012554700000",
                "MV012561600000",
                "MV012504530000",
                "MV012529780000",
                "MV012554590000",
                "MV012504510000",
                "MV012529800000",
                "MV012504500000",
                "MV012588580000",
                "MV012554720000",
                "MV012510660000",
                "MV012554360000",
                "MV012718090000",
                "MV012689600000",
                "MV012828410000"
            ],
            "moviesWithDupPublishedResources": [
                "MV000422670000",
                "MV000529580000",
                "MV000530550000",
                "MV000550950000",
                "MV000594000000",
                "MV000621370000",
                "MV000623260000",
                "MV000634080000",
                "MV000676110000",
                "MV000678590000",
                "MV000681790000",
                "MV000712760000",
                "MV000729430000",
                "MV000795640000",
                "MV000805730000",
                "MV000860790000",
                "MV000910660000",
                "MV000918680000",
                "MV001045490000",
                "MV001159760000",
                "MV001273460000",
                "MV001339080000",
                "MV001445560000",
                "MV001455820000",
                "MV001512590000",
                "MV001581940000",
                "MV001605650000",
                "MV001630160000",
                "MV001668680000",
                "MV001732110000",
                "MV001760500000",
                "MV001764430000",
                "MV001816040000",
                "MV001904470000",
                "MV001932960000",
                "MV001945170000",
                "MV001973860000",
                "MV002023300000",
                "MV002116240000",
                "MV002140210000",
                "MV002205840000",
                "MV002404240000",
                "MV002408810000",
                "MV002574190000",
                "MV002670930000",
                "MV002680230000",
                "MV002705150000",
                "MV002714310000",
                "MV003441150000",
                "MV003875960000",
                "MV003902490000",
                "MV003954620000",
                "MV004009110000",
                "MV004011910000",
                "MV004013870000",
                "MV004015730000",
                "MV004147060000",
                "MV004312070000",
                "MV004367500000",
                "MV004469940000",
                "MV004495270000",
                "MV004681120000",
                "MV004837950000",
                "MV004861910000",
                "MV004923710000",
                "MV004981470000",
                "MV005003860000",
                "MV005006360000",
                "MV005028400000",
                "MV005043670000",
                "MV005188570000",
                "MV005366830000",
                "MV005393250000",
                "MV005496960000",
                "MV005716570000",
                "MV005759290000",
                "MV005839340000",
                "MV005909650000",
                "MV006090300000",
                "MV006284860000",
                "MV006412610000",
                "MV006536040000",
                "MV006606930000",
                "MV006672940000",
                "MV007339370000",
                "MV007433850000",
                "MV007835630000",
                "MV007882460000",
                "MV007906090000",
                "MV007911990000",
                "MV007973750000",
                "MV008127790000",
                "MV008214250000",
                "MV008325830000",
                "MV008594860000",
                "MV008595570000",
                "MV008765680000",
                "MV008887640000",
                "MV009042090000",
                "MV009076080000",
                "MV009215870000",
                "MV009361930000",
                "MV009483760000",
                "MV009628200000",
                "MV009736910000",
                "MV009834780000",
                "MV009957850000",
                "MV009996290000",
                "MV010040210000",
                "MV010043940000",
                "MV010111360000",
                "MV010125460000",
                "MV010116830000",
                "MV010173880000",
                "MV010228270000",
                "MV010230110000",
                "MV010280170000",
                "MV010354160000",
                "MV010570790000",
                "MV010572830000",
                "MV010498650000",
                "MV010587100000",
                "MV010721180000",
                "MV010721190000",
                "MV010752570000",
                "MV010749000000",
                "MV010752530000",
                "MV010790670000",
                "MV010802050000",
                "MV010817010000",
                "MV010818740000",
                "MV010818890000",
                "MV010875700000",
                "MV010819950000",
                "MV010818470000",
                "MV010850130000",
                "MV010875970000",
                "MV010817110000",
                "MV010857610000",
                "MV010818950000",
                "MV010903410000",
                "MV010886960000",
                "MV011081210000",
                "MV011041500000",
                "MV011643760000",
                "MV011631790000",
                "MV011631780000",
                "MV011645330000",
                "MV011620770000",
                "MV011661810000",
                "MV011772940000",
                "MV011822430000",
                "MV011919140000",
                "MV011942840000",
                "MV011944500000",
                "MV011974470000",
                "MV011994660000",
                "MV012064560000",
                "MV012075520000",
                "MV012099770000",
                "MV012131640000",
                "MV012238330000",
                "MV012285310000",
                "MV012302400000",
                "MV012355320000",
                "MV012348560000",
                "MV012357610000",
                "MV012360790000",
                "MV012389440000",
                "MV012425140000",
                "MV012411810000",
                "MV012369300000",
                "MV012431580000",
                "MV012428130000",
                "MV012428360000",
                "MV012441390000",
                "MV012460220000",
                "MV012529730000",
                "MV012583660000",
                "MV012529770000",
                "MV012561600000",
                "MV012504530000",
                "MV012529780000",
                "MV012554590000",
                "MV012588580000",
                "MV012554720000",
                "MV012510660000",
                "MV012554360000",
                "MV012718090000",
                "MV012689600000",
                "MV012828410000"
            ],
            "moviesWithMismatchedPaid": [
                "MV001034950000"
            ]
        }
    }
}
```



### Generate show reports

Forces an immediate update of the show reports from the VOD catalog.
Regenerated show reports are available about 15 minutes after the request.

<br>

VOD catalog report data is automatically updated every 12 hours.
This endpoint refreshes the show reports with the most current catalog data available.


***Endpoint:***

```bash
Method: POST
Type: 
URL: {{CMRServer}}/cmr/v1/report/generate/shows
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



### Get show summary report

Returns the list of shows that have VOD episodes and indicates the degree of parity (_seasonDifference_ and _episodeDifference_)
with the metadata provider for each show. The 'shows' array field may be converted to CSV format.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{CMRServer}}/cmr/v1/report/showsummary
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Accept | application/json |  |



***Responses:***


Status: Get Show Summary Report | Code: 200



```js
{
    "requestID": "3a857d51-272f-4d1f-90a2-57c3912c7beb",
    "timestamp": "2019-08-22T00:13:29.988760615Z",
    "item": {
        "updated": "2019-08-21T21:22:38.577Z",
        "shows": [
            {
                "show": {
                    "id": "SH029882450000",
                    "title": "(Des) Encuentros",
                    "seasonCount": 2,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "3f951b69-e542-4080-a73c-1a78b30ead4a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024808590000",
                    "title": "1 Contra Todos",
                    "seasonCount": 3,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "0c2f7049-8669-42e4-964b-ef6c7c024d4d",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025982540000",
                    "title": "1, 2, 3 hipnotízame",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "02ce5f28-36ba-4eb7-ab0f-f7dd959ea3f9",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031333350000",
                    "title": "1989: El año que nos marcó",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "94592848-6f47-4cfe-a16a-696c778c0348",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025048390000",
                    "title": "2091",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "458d701e-cde5-443b-a768-631677955587",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030084680000",
                    "title": "4 Blocks",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "c687574a-e93e-4d3d-955b-0adda29c8f2d",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014229840000",
                    "title": "4 esposas, 1 marido",
                    "seasonCount": 13,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "5539f178-357f-4451-bb6c-529b9081e3c6",
                    "published": true,
                    "seasonCount": 13,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031572810000",
                    "title": "44 gatos",
                    "seasonCount": 1,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "317e137a-1a9d-42b6-abfe-3069ccf3b9dc",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024774990000",
                    "title": "60 días preso: el experimento",
                    "seasonCount": 5,
                    "episodeCount": 27,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "46b2b7de-107d-4172-b508-cb9432ef8ba9",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028241510000",
                    "title": "9-1-1",
                    "seasonCount": 3,
                    "episodeCount": 27,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 29
                },
                "resource": {
                    "id": "78d52f95-6719-4e74-94c1-56c0fc72144a",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 29
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031777420000",
                    "title": "A Discovery of Witches",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "2dd8c48a-47f4-4a3b-b2d6-ae78d91955cf",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017260080000",
                    "title": "A Mother's Son",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "47876276-9e58-4f0b-aa16-58560bd92ff5",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020245750000",
                    "title": "A la caza de fantasmas",
                    "seasonCount": 4,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "3c82456e-877a-46a8-9c4e-63cdd0a5a849",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029674240000",
                    "title": "Absentia",
                    "seasonCount": 2,
                    "episodeCount": 19,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "ccc5f0e9-be21-43ef-97f8-0b878edaae25",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019869210000",
                    "title": "Acapulco Shore",
                    "seasonCount": 6,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "33c3d6cd-396c-4733-977c-2284f510773e",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029933580000",
                    "title": "Acceso Natgeo: Balmoral",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "921253b5-8f78-4e29-a1c4-4fa76ed42dd4",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024322390000",
                    "title": "Acumuladores compulsivos",
                    "seasonCount": 10,
                    "episodeCount": 25,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "14c70f42-21ea-48ce-a9db-a5a175731125",
                    "published": true,
                    "seasonCount": 10,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029684540000",
                    "title": "Aerial America",
                    "seasonCount": 7,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "cd37ffd9-5fa3-4b05-a668-f9c7990df0ae",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030209770000",
                    "title": "Aerial Cities",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "09116e8f-dbf1-4627-82ae-fd72c230fa9a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031355610000",
                    "title": "Aeropuerto 24/7: Miami",
                    "seasonCount": 3,
                    "episodeCount": 19,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "922924d2-2dab-4af9-afcf-870bf8214c99",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031654500000",
                    "title": "Aeropuerto bajo cero",
                    "seasonCount": 1,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "87eb6695-e313-4ab3-9210-6b04f5759b8d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030024710000",
                    "title": "Alaska Aircrash Investigations",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "b484b35f-b0c1-4d86-91fb-2ec04aba7d96",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022875330000",
                    "title": "Alaska Escalofriante",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "b9a91de9-648b-405d-96bc-12c026de6d58",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021492170000",
                    "title": "Alaska: Hombres primitivos",
                    "seasonCount": 10,
                    "episodeCount": 30,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "8c51cb83-482e-469c-9bd0-292fb4d30e50",
                    "published": true,
                    "seasonCount": 10,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017294260000",
                    "title": "Alaska: la última frontera",
                    "seasonCount": 8,
                    "episodeCount": 52,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 34
                },
                "resource": {
                    "id": "31e3a6bf-7bd7-4f94-8748-e881252250a7",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 34
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028059390000",
                    "title": "Alerta Aeropuerto 4",
                    "seasonCount": 2,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "00527d84-f33e-4c12-aae0-178fffb7a1a2",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028062650000",
                    "title": "Alerta Aeropuerto: Madrid",
                    "seasonCount": 2,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "08c66b08-bfc7-48e1-bebb-856aadfd761a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025381490000",
                    "title": "Alerta aeropuerto 3",
                    "seasonCount": 1,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "bb7d1925-e41f-46de-833d-89fb9a8b0fc8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031748420000",
                    "title": "Alerta aeropuerto 6",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "ed1bac6e-873f-41dc-a373-a4c875b0881e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029229820000",
                    "title": "Alerta aeropuerto: San Pablo",
                    "seasonCount": 2,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "05ebd351-0d8f-4736-8bc0-38841edc1f08",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013171430000",
                    "title": "Alienígenas Ancestrales",
                    "seasonCount": 14,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "0342ba74-ca9f-4671-864d-e80a433e47da",
                    "published": true,
                    "seasonCount": 14,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015898740000",
                    "title": "All Access",
                    "seasonCount": 26,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "09277791-84bf-4aa7-8c0e-91b365b87f6d",
                    "published": true,
                    "seasonCount": 26,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030294200000",
                    "title": "All American",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "85dc5206-f963-4d72-9a9b-06af4a557234",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022802800000",
                    "title": "Allí abajo",
                    "seasonCount": 5,
                    "episodeCount": 65,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 52
                },
                "resource": {
                    "id": "a775490d-eb25-4b63-acb1-68d6cf943ec5",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 52
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030668340000",
                    "title": "Amanda al rescate",
                    "seasonCount": 2,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "9bbfceb4-a46b-4300-956d-f7a2e4d224fe",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026365040000",
                    "title": "Amar después de Amar",
                    "seasonCount": 1,
                    "episodeCount": 60,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 60
                },
                "resource": {
                    "id": "96420bf4-34d4-4e3a-aff8-8de2cf5594e8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 60
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026544360000",
                    "title": "Amar después de Amar",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "d3c69c91-886c-4b0f-a230-6c4facac67c9",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016673410000",
                    "title": "Amar es para siempre",
                    "seasonCount": 1,
                    "episodeCount": 107,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 70
                },
                "resource": {
                    "id": "cec72a2c-d693-45d0-9314-d0f6d60d3a97",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 70
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH001788440000",
                    "title": "America Undercover",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "3fd8241e-6f7a-48de-bac2-e1bb822a9182",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH010654800000",
                    "title": "America's Got Talent",
                    "seasonCount": 14,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "4da30e63-cb6a-4aea-81cb-1c885ebd0058",
                    "published": true,
                    "seasonCount": 14,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007157520000",
                    "title": "American Chopper",
                    "seasonCount": 12,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "74abbdb6-dfa0-426e-9a64-21b6cf78b96d",
                    "published": true,
                    "seasonCount": 12,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007351390000",
                    "title": "American Dad",
                    "seasonCount": 14,
                    "episodeCount": 46,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "b23e58ea-a127-4dc6-b4c4-bee06dfc38d7",
                    "published": true,
                    "seasonCount": 14,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014712090000",
                    "title": "American Horror Story",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "7fb9b542-9283-48c4-8eb8-1d82ca46e690",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030454210000",
                    "title": "American Horror Story: Apocalipsis",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "916fd74a-3d7e-428f-9593-6d7f734b5a93",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030122870000",
                    "title": "American Horror Story: Apocalypse",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "1be46474-05e5-4dc9-9345-d75bfd509367",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017774010000",
                    "title": "American Horror Story: Coven",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "323205cb-63b4-4a7f-8ace-998863cd61f1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027436260000",
                    "title": "American Horror Story: Cult",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "440d5a3d-b6f1-4fbc-a66f-3e8180e17885",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH006045890000",
                    "title": "American Idol",
                    "seasonCount": 16,
                    "episodeCount": 38,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 25
                },
                "resource": {
                    "id": "6977f1c4-f017-4666-a3ba-7de3ce7250b4",
                    "published": true,
                    "seasonCount": 16,
                    "episodeCount": 25
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013166560000",
                    "title": "Amistades insólitas",
                    "seasonCount": 4,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "5031da09-6adb-42f4-8fd3-a8933b69d312",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015281690000",
                    "title": "Amor asesino",
                    "seasonCount": 6,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "130f4a0b-d670-433b-80d7-0da54ceeaaf9",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019475140000",
                    "title": "América: ¿Realidad o mito?",
                    "seasonCount": 4,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "8d19ab1d-d07b-4915-8395-d4a8cc352232",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH011031290000",
                    "title": "Anatomía según Grey",
                    "seasonCount": 16,
                    "episodeCount": 28,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "4352040a-69d0-4127-9b01-6b5142553eca",
                    "published": true,
                    "seasonCount": 16,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015081300000",
                    "title": "Angry Boys",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "a06978a6-6a4f-456f-a24f-47766bb3495d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030241980000",
                    "title": "Animal manía",
                    "seasonCount": 2,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "26078f76-edb3-451f-9ce2-3bd6690e5aa5",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023330250000",
                    "title": "Animals.",
                    "seasonCount": 3,
                    "episodeCount": 30,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 30
                },
                "resource": {
                    "id": "95f42c3b-e8e9-405d-88d5-80b4a5d54d8f",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 30
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027819590000",
                    "title": "Apaches",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "8479eaa7-19b0-4d69-b40d-9a1b178f5e5d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032485560000",
                    "title": "Apolo: Llegamos a la Luna",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "9ebce5f9-c8bb-4f0c-8347-6834caca02b1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026602730000",
                    "title": "Apple Tree Yard",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "75649ccc-2f64-4627-8255-16cdd558fe13",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029202340000",
                    "title": "Aquí en la Tierra",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "52b64ccf-d451-46fa-baf8-fc688d86671f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018535490000",
                    "title": "Are You the One?",
                    "seasonCount": 8,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "a32a758d-60fb-42be-85da-4b1b61ae6ea0",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023453570000",
                    "title": "Arréglame la Vida",
                    "seasonCount": 5,
                    "episodeCount": 39,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "98262208-b7ee-4652-8c5a-df0fae7982d6",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017388760000",
                    "title": "Asesinatos en familia",
                    "seasonCount": 6,
                    "episodeCount": 42,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 24
                },
                "resource": {
                    "id": "3394bca1-03c1-462f-bfae-e108ec4061b6",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 24
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028079500000",
                    "title": "Asesinos legendarios",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "ed5f6cd6-bb32-4fb3-9b43-402541468b52",
                    "published": false,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022526100000",
                    "title": "Ash vs Evil Dead",
                    "seasonCount": 3,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 42
                },
                "resource": {
                    "id": "2a00eae3-44ae-4fea-81f4-513576953561",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 42
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022217120000",
                    "title": "Asombrosamente",
                    "seasonCount": 2,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "f333e5e1-36a8-413f-8588-4a5bc0da3afd",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028473670000",
                    "title": "Atchoo!",
                    "seasonCount": 1,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "2d5703a1-0835-4906-b54c-598ed5c4258a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024673510000",
                    "title": "Atlanta",
                    "seasonCount": 2,
                    "episodeCount": 25,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 27
                },
                "resource": {
                    "id": "5832dc26-b07d-47ca-bb7b-45d0f432cdf8",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 27
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014166270000",
                    "title": "Aventuras con los Kratt",
                    "seasonCount": 6,
                    "episodeCount": 44,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "3ba19f5e-6250-4f48-9c7a-f38d48bb90c7",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH002106400000",
                    "title": "Aventuras en Pañales",
                    "seasonCount": 9,
                    "episodeCount": 59,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 59
                },
                "resource": {
                    "id": "c1376cca-b5c8-437d-8715-ad9f0e58f0ad",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 59
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029274310000",
                    "title": "Averiguando cosas",
                    "seasonCount": 3,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "2303ddf4-171c-4b7b-8b0f-59f511b6b8c2",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030713710000",
                    "title": "Axios",
                    "seasonCount": 2,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "b5a01883-9d5e-45c1-834c-2fda03e1412e",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032740110000",
                    "title": "Ayúdame con mi cocina",
                    "seasonCount": 8,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "dd0f503e-eaad-4931-b7c3-fae4d3b9e4bd",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025030990000",
                    "title": "Ayúdame, June",
                    "seasonCount": 0,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "edf9adff-a25b-4139-81b2-f6212a699267",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016663660000",
                    "title": "BAFTA: A Life in Pictures",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "17ee14ee-94a6-438e-a6ff-7538603cfee8",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021729390000",
                    "title": "Ballers",
                    "seasonCount": 5,
                    "episodeCount": 48,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 73
                },
                "resource": {
                    "id": "c63f90d1-8fcc-4f9d-afd4-91cbb030e7ff",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 73
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH004978780000",
                    "title": "Band of Brothers",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "e23a2640-15af-4f81-a344-ec2d4fbcae5e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012916480000",
                    "title": "Banged Up Abroad",
                    "seasonCount": 11,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "d3078e66-dff9-4c2b-88b2-1cf62ec194eb",
                    "published": true,
                    "seasonCount": 11,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023587070000",
                    "title": "Bar Central",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "84010043-2870-49ee-8f09-755e8ccf5025",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028634110000",
                    "title": "Barry",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "e5a6fc34-8935-4f16-840f-6e9ab35426b3",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032740210000",
                    "title": "Baños asombrosos",
                    "seasonCount": 12,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "8b3d8bf4-e2c9-4170-b5fd-89b5b6e45351",
                    "published": true,
                    "seasonCount": 12,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027476570000",
                    "title": "Bebés tras las rejas",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "0a1943b2-2924-4034-a7e0-14cf8cd66583",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030043710000",
                    "title": "Bellevue",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "4a153061-d093-4712-bee6-a369bc7aaf22",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026414560000",
                    "title": "Ben 10",
                    "seasonCount": 3,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "9a062d7d-396c-4941-9d75-1e414ab1ff22",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031090730000",
                    "title": "Beyblade Burst",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "d1f9f88e-e416-43d3-88d0-ff5414f99e69",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025762910000",
                    "title": "Big Little Lies",
                    "seasonCount": 2,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "33a2e00e-20bc-4a97-a63a-814750b927bf",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH008134280000",
                    "title": "Big Love",
                    "seasonCount": 5,
                    "episodeCount": 53,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 62
                },
                "resource": {
                    "id": "7730446d-f1d3-4403-bc38-a9e544cb3b17",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 62
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028412110000",
                    "title": "Big Top Academy",
                    "seasonCount": 1,
                    "episodeCount": 50,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 46
                },
                "resource": {
                    "id": "7853e060-c01d-4a74-9b13-6f166cfccabe",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 46
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030786900000",
                    "title": "Bios: Vidas que marcaron la tuya",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "4857ab94-2eea-4166-81eb-30cb08035e13",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032340770000",
                    "title": "Bitz y Bob",
                    "seasonCount": 2,
                    "episodeCount": 43,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 34
                },
                "resource": {
                    "id": "9290ad34-87fa-4c9f-b9fd-361657c530d8",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 34
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032296720000",
                    "title": "Bitz y Bob: ¡tú también lo puedes hacer!",
                    "seasonCount": 2,
                    "episodeCount": 42,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 41
                },
                "resource": {
                    "id": "0be50e0f-562c-4e39-91b9-6866a6f728e7",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 41
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029780740000",
                    "title": "Black Market con Michael K. Williams",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "e3c7d6dd-b387-411c-a820-b34431e273ef",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031382580000",
                    "title": "Black Market: Dispatches",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "4352d3cf-5f81-408d-8080-a3b45b55a86a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018283390000",
                    "title": "Black Sails",
                    "seasonCount": 4,
                    "episodeCount": 38,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 49
                },
                "resource": {
                    "id": "be7c64e3-b382-44a3-bc9c-98a2e84bbb62",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 49
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024191500000",
                    "title": "Blaze y los Monster Machines",
                    "seasonCount": 5,
                    "episodeCount": 33,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "705e2a57-cb11-494b-808f-cd39a9b299a8",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022107760000",
                    "title": "Blunt Talk",
                    "seasonCount": 2,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "99029a06-fefe-4db8-9b37-b92a3e028c93",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018662260000",
                    "title": "Boardwalk Empire - El Imperio del Contrabando",
                    "seasonCount": 5,
                    "episodeCount": 56,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 53
                },
                "resource": {
                    "id": "6bce22f2-85bc-46bd-8c6e-2ed384fbd53c",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 53
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH003561370000",
                    "title": "Bob Esponja",
                    "seasonCount": 12,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "563fb658-5177-4981-b45c-975329f5ebb8",
                    "published": true,
                    "seasonCount": 12,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030157080000",
                    "title": "Bodas arregladas",
                    "seasonCount": 2,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "2986c42f-ebe1-4e5a-9bdd-20684a3444ac",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027400910000",
                    "title": "Borderland: La travesía de los migrantes",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "6f3f8e26-5e26-462a-8f30-7e9a09fea782",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012029880000",
                    "title": "Bored to Death",
                    "seasonCount": 3,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 24
                },
                "resource": {
                    "id": "f35d6fc9-5e51-4ce9-a980-90f6e65af31a",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 24
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031846540000",
                    "title": "Botswana: zona de depredadores",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "32dcfeff-a14e-4619-afca-dfd45f5f110f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018710640000",
                    "title": "Breadwinners",
                    "seasonCount": 2,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "5f6d2b67-f8b4-4113-b39d-891330987a06",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028979580000",
                    "title": "Brian Johnson's A Life On The Road",
                    "seasonCount": 2,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "2f129f5f-0f9e-4b79-a46f-826a91f3ddea",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018743570000",
                    "title": "Bring It!",
                    "seasonCount": 6,
                    "episodeCount": 56,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 24
                },
                "resource": {
                    "id": "71e66334-6de8-40d7-ae50-4e09bf047c8f",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 24
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029455100000",
                    "title": "Britannia",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "fbf3e7ce-43e6-4905-82b4-566f949b3de7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018336280000",
                    "title": "Broad City",
                    "seasonCount": 5,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "10bd7fa2-afb0-4a54-9cc9-66c69b877481",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017660560000",
                    "title": "Brooklyn Nine-Nine",
                    "seasonCount": 6,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "e0f7e0cc-6284-4d41-a64c-06a5b53194b1",
                    "published": false,
                    "seasonCount": 6,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026876990000",
                    "title": "Buckeye, médico veterinario",
                    "seasonCount": 3,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "612643fd-d307-4d0a-a923-48a4b94e0a70",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024727910000",
                    "title": "Bull",
                    "seasonCount": 4,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "95dd5ecd-dc88-43e7-82ab-2c398262f83d",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025859270000",
                    "title": "Bunsen Is a Beast!",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "c57ba1f9-e128-4a09-8e92-8ac12e21a63b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030014790000",
                    "title": "Bunsen es una bestia",
                    "seasonCount": 1,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "8cd9bdfa-02ad-44d6-b5ff-690242442896",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031404190000",
                    "title": "Buscadores de mascotas",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "c864d67c-5768-4fed-901d-8a0508d223d1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023702190000",
                    "title": "Buscando el norte",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "7449c59d-5661-4d49-8d21-d954cbedb462",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030522640000",
                    "title": "Butterfly",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "6b61e8af-62f2-40a5-aaea-7cad4c42279e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028503300000",
                    "title": "Buzzu en la escuela intergaláctica",
                    "seasonCount": 2,
                    "episodeCount": 48,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 28
                },
                "resource": {
                    "id": "9c4dbd06-c11e-48a0-ad8a-08f4b521eb03",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 28
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012009120000",
                    "title": "CSI",
                    "seasonCount": 15,
                    "episodeCount": 174,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 45
                },
                "resource": {
                    "id": "a76fa9f3-01dd-4db9-9118-549fb56876aa",
                    "published": true,
                    "seasonCount": 15,
                    "episodeCount": 45
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024374550000",
                    "title": "CSI: Escena del Crimen",
                    "seasonCount": 15,
                    "episodeCount": 94,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 65
                },
                "resource": {
                    "id": "27822c99-736f-4b18-ab17-ab9a386b3095",
                    "published": true,
                    "seasonCount": 15,
                    "episodeCount": 65
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH005409540000",
                    "title": "CSI: Miami",
                    "seasonCount": 10,
                    "episodeCount": 152,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 94
                },
                "resource": {
                    "id": "f040afd0-cefd-4414-b42e-7bee8273df50",
                    "published": true,
                    "seasonCount": 10,
                    "episodeCount": 94
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH006970990000",
                    "title": "CSI: NY",
                    "seasonCount": 9,
                    "episodeCount": 85,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 47
                },
                "resource": {
                    "id": "5d5a93f4-90df-4c7f-b375-fc8c45d32331",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 47
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022968110000",
                    "title": "Calculadora Humana",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "f1a0edea-43ca-47e5-a1dd-c9dedb1c26f7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030511440000",
                    "title": "Campamento de verano",
                    "seasonCount": 2,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "d11a89af-191e-448d-8f5d-1bedbe4d8d7a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030341420000",
                    "title": "Camping",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "86686a44-35fc-45af-8aa6-13704cf8ab7c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH010267790000",
                    "title": "Capadocia",
                    "seasonCount": 3,
                    "episodeCount": 39,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 39
                },
                "resource": {
                    "id": "2f0db5cb-1ce9-4d04-8e71-71e61efb6f6b",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 39
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030525390000",
                    "title": "Captain Tsubasa",
                    "seasonCount": 1,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "9a59bc51-0c88-4a78-b8d7-6299c82a3938",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024807900000",
                    "title": "Cara a Cara",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "81dc5ea1-55e6-4f57-b081-ec3fb16b24dd",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH005983970000",
                    "title": "Carnivale",
                    "seasonCount": 2,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 24
                },
                "resource": {
                    "id": "e42cd8f0-ed16-4184-9c8e-d98108d6701a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 24
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029658280000",
                    "title": "Casas diseño y estilo",
                    "seasonCount": 1,
                    "episodeCount": 35,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 30
                },
                "resource": {
                    "id": "0708159c-ad2b-430e-8a39-c57448a9abfc",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 30
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023125370000",
                    "title": "Catastrophe",
                    "seasonCount": 4,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "c5869581-b926-4e98-b0f6-7e218ed71677",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026006270000",
                    "title": "Catfish Brasil",
                    "seasonCount": 3,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "026ccaff-85c5-45a7-87b6-dbb1359fc209",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016921150000",
                    "title": "Catfish: mentiras en la Red",
                    "seasonCount": 7,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "d1ef2379-dab0-45ff-9437-83da8597293d",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016777610000",
                    "title": "Cazadores de Serpientes",
                    "seasonCount": 3,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "34ff8b11-949a-445a-995a-700fa59d3498",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013496180000",
                    "title": "Cazadores de tesoros",
                    "seasonCount": 18,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "0ae92f54-6c09-4c3f-823a-9f9e34c28282",
                    "published": true,
                    "seasonCount": 18,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031702640000",
                    "title": "Cazadores retro tech",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "2a2f1bfa-b389-4568-a113-1fe647c69f5c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032068220000",
                    "title": "Cazadores salvajes",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "576c8bee-307a-43ae-95fa-74604fa20c4c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032492860000",
                    "title": "Celebrando China",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "f3bbe464-fadf-4bb8-8ecb-3eff545af834",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030511790000",
                    "title": "Celebrity Mysteries",
                    "seasonCount": 0,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "b7786e67-f38b-4197-9bf8-f5d6e777a241",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018883100000",
                    "title": "Cesar 911",
                    "seasonCount": 4,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "0db1bbed-97da-4fe1-baf4-d8496b42a6ba",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028408890000",
                    "title": "Chain of Command",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "ba18f2b9-25ce-4cc5-8097-47ca46c90259",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025980360000",
                    "title": "Chance",
                    "seasonCount": 2,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "38dc4ba0-3ebf-4531-ab60-eb3931f32763",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032503530000",
                    "title": "Chasing The Moon",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "0121a7df-26d0-478b-a48c-8ff7fba8e88c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031836360000",
                    "title": "Chernobyl",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "75c4f454-2b11-4df7-bcdb-99219b9eca3d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030025430000",
                    "title": "Chile salvaje y extremo",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "7454637c-0252-46f2-8333-18ad6283b110",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030521460000",
                    "title": "China al extremo",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "2120419c-bc0f-4586-8122-d8a68dfa093f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030328720000",
                    "title": "China's Dragon Emperor",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "ef45abc2-2467-4e56-9559-a74ed0360e6d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023418650000",
                    "title": "Chiringuito de Pepe",
                    "seasonCount": 2,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 15
                },
                "resource": {
                    "id": "4e8ffc0c-721c-4442-a1a6-5fa1b74aa98f",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 15
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026243040000",
                    "title": "Chopped: Eliminado",
                    "seasonCount": 43,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "aa3f9650-8da4-4dc8-bcfb-3d77cee56c8f",
                    "published": true,
                    "seasonCount": 43,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027097540000",
                    "title": "Chuck's Choice",
                    "seasonCount": 1,
                    "episodeCount": 40,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 32
                },
                "resource": {
                    "id": "c01404b9-f5be-43df-8033-dbe46b028f13",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 32
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024691610000",
                    "title": "Chumel con Chumel Torres",
                    "seasonCount": 4,
                    "episodeCount": 106,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 86
                },
                "resource": {
                    "id": "b9843828-71e6-4dd7-8855-f7ddac9e493f",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 86
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026543410000",
                    "title": "Cirugías en altamar",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "60a9b775-1b80-4081-8de5-0b9b91d375ce",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018698010000",
                    "title": "Clarence",
                    "seasonCount": 4,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "39e47c57-304e-4970-acbc-e48ac1090494",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032387060000",
                    "title": "Cleo y Cuquín: Familia Telerín",
                    "seasonCount": 1,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "e9b9fc08-544f-4b1d-bcc0-26610d42208e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029941900000",
                    "title": "Cocinando con Ina Garten",
                    "seasonCount": 26,
                    "episodeCount": 44,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "655a78f3-23c1-44b9-b1e2-9b5326e72668",
                    "published": true,
                    "seasonCount": 26,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032062780000",
                    "title": "Colgados",
                    "seasonCount": 0,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "608a3ef0-191f-47d1-abf4-0b8a6ab3f132",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023147320000",
                    "title": "Colony",
                    "seasonCount": 3,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "93019fe6-9ecd-4ee7-8928-e0e6db254bad",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023192540000",
                    "title": "Comandancias",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "19aed5c3-88c3-4c3a-856f-a7db645b507f",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023458550000",
                    "title": "Comandancias",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "7a078558-6e8c-4ceb-aae2-9a1d58f67f96",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031787210000",
                    "title": "Come Home",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "2f8a2c08-246d-48b4-8276-0cb8f900e0fd",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022997610000",
                    "title": "Comedy Central Stand Up",
                    "seasonCount": 4,
                    "episodeCount": 30,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 30
                },
                "resource": {
                    "id": "f6b83609-019b-4a49-b75b-2967a9901706",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 30
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024543840000",
                    "title": "Comedy Central Stand Up",
                    "seasonCount": 6,
                    "episodeCount": 50,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 50
                },
                "resource": {
                    "id": "0b1bd0fc-f22e-466f-95fa-d96de83569ba",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 50
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026280970000",
                    "title": "Comedy Central Stand Up",
                    "seasonCount": 3,
                    "episodeCount": 40,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "ad2801cc-8cc7-4c69-964f-967412309501",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015600960000",
                    "title": "Con el agua al cuello",
                    "seasonCount": 14,
                    "episodeCount": 49,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "59a0b668-88c5-44cc-bae3-29eb66df2b7b",
                    "published": true,
                    "seasonCount": 14,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015479970000",
                    "title": "Con el culo al aire",
                    "seasonCount": 3,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "95d3e477-e735-4e38-ad0f-636edb2c7443",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030608840000",
                    "title": "Condor",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "ccc2d246-5067-4eca-98d2-c32d12eb035c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030264860000",
                    "title": "Conquistadores Adventvm",
                    "seasonCount": 0,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "9e519fb8-1059-4b8b-8d47-5e4388ad4bf7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032325650000",
                    "title": "Construyendo gigantes",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "9e4606b1-3343-44cf-b864-23b7588687ea",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024669070000",
                    "title": "Conviction",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "b5325e30-06cb-4d9d-b880-7b6c5bdb156f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH008837470000",
                    "title": "Correccionales",
                    "seasonCount": 4,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "f3d640b5-2d7a-4c8a-b5da-cc4417e747d6",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028275700000",
                    "title": "Counterpart",
                    "seasonCount": 2,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "c9079dff-c9ba-42e0-9bd9-d5a566dee31d",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015424500000",
                    "title": "Crashbox",
                    "seasonCount": 2,
                    "episodeCount": 38,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 39
                },
                "resource": {
                    "id": "1d0f05b1-14e1-4a8d-8426-684a68e586c7",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 39
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025762940000",
                    "title": "Crashing",
                    "seasonCount": 3,
                    "episodeCount": 25,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "4bbb2a2f-8cc7-4392-9f6b-682189dbe874",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031672820000",
                    "title": "Criaturas adorables",
                    "seasonCount": 1,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "1b9c9051-caaf-40a6-bc40-9f39e9b127b2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020465350000",
                    "title": "Crimen Casi Perfecto",
                    "seasonCount": 5,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "25232446-a2c4-4395-b3c8-818bb3a11ace",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH008446890000",
                    "title": "Criminal Minds",
                    "seasonCount": 14,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "4c86ca5c-c213-4a50-a218-acd84a4e9e5b",
                    "published": false,
                    "seasonCount": 14,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018545030000",
                    "title": "Crímenes del pasado",
                    "seasonCount": 5,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "f46d705f-48ab-4573-a1cc-068ed72e1711",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026587600000",
                    "title": "Crímenes no resueltos",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "1228caf5-2c72-4a1b-adf0-42ca4d4c09c1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017520150000",
                    "title": "Cuando los tiburones atacan",
                    "seasonCount": 5,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "b1f15c0b-90db-4d3c-8d42-1f577826ffa4",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021131390000",
                    "title": "Cuidado Animal",
                    "seasonCount": 3,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "6b675378-2d4b-40db-9d98-8a40b0c80aee",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017752690000",
                    "title": "Cumbia ninja",
                    "seasonCount": 3,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "92b03f58-1333-46a6-9745-e41ec9bcfffb",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013333610000",
                    "title": "Cupcake Wars",
                    "seasonCount": 9,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "922fb1a4-ad35-4d06-a758-218f034a278c",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH005720900000",
                    "title": "Curb Your Enthusiasm",
                    "seasonCount": 9,
                    "episodeCount": 90,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 97
                },
                "resource": {
                    "id": "7a3c5f89-3b3a-48c7-849d-315ba17b6238",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 97
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032076010000",
                    "title": "Cuál es mi nombre: Muhammad Ali",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "c2c81128-3d54-4f58-b6e0-f9a17e22de25",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028893530000",
                    "title": "Cyberwar",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "a231fe64-7aaf-4e29-95de-584e2343819b",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026400410000",
                    "title": "Cyrus vs. Cyrus: Design and Conquer",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "1ae8d171-7dd3-43e1-8dc2-31a5cd39f124",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013214140000",
                    "title": "Cómo Funciona el Universo",
                    "seasonCount": 7,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "c4d16476-da58-44c1-bbf3-335bd862b28a",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017044110000",
                    "title": "Da Vinci's Demons",
                    "seasonCount": 3,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 37
                },
                "resource": {
                    "id": "960d50bf-500b-4832-b9a6-40e53f7aa791",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 37
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH009253710000",
                    "title": "Dane Cook's Tourgasm",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "b585da61-f0d0-4392-a74b-63d33d341ec3",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029758900000",
                    "title": "David Rocco: Dulce África",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "2896b0b6-cf81-4a38-be93-30314dca8e08",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH003138070000",
                    "title": "De la Tierra a la Luna",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "cf1e4fcb-29d0-4f95-9d0e-bc6d74f0e38a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031029540000",
                    "title": "Deadly Class",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "3d1bef78-b1e9-4d83-bba1-a7043b9c6788",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030971880000",
                    "title": "Decades Remixed",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "f4ae2809-4b03-4083-bfb9-40b4082234a8",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024968030000",
                    "title": "Decorando con Candice",
                    "seasonCount": 6,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "987e0522-632b-4ffc-8883-dce6ebbba716",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026057980000",
                    "title": "Depredadores africanos",
                    "seasonCount": 3,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "22c620e4-28e0-4909-bb8a-78d96d4421e5",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031846580000",
                    "title": "Depredadores en el paraíso",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "454a141c-9129-4d4b-9f5f-b6ed72b35b68",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025114410000",
                    "title": "Desafío sobre fuego",
                    "seasonCount": 6,
                    "episodeCount": 51,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 22
                },
                "resource": {
                    "id": "1cae7b3b-59eb-48a7-a205-86700fe5fc03",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 22
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013479830000",
                    "title": "Desaparecidos",
                    "seasonCount": 9,
                    "episodeCount": 19,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "4c10b1c4-0ea8-46e5-9188-575b0c0136f9",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030162870000",
                    "title": "Descubriendo enigmas",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "62fbf554-028f-46be-b5d5-c7e42c03e8c3",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028850180000",
                    "title": "Desde el frente de batalla",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "7891af26-203a-492c-8e72-8d9da9d6f9db",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012546750000",
                    "title": "Destino Deporte",
                    "seasonCount": 4,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "3333f455-f3c7-4bc5-8596-d5f7d417f2da",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029830920000",
                    "title": "Destino Wild: Estados Unidos",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "45d561fc-dd51-4c4f-b508-2164a96d090a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031852560000",
                    "title": "Destino Wild: Gran Bretaña",
                    "seasonCount": 0,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "cbd899b6-8c70-46c4-a0b3-ddb40ad39834",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030851990000",
                    "title": "Destino wild: Perú",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "bd0d87d8-647d-4b73-8bfb-2c1a0164d1c2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030851880000",
                    "title": "Destino wild: Yellowstone",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "c304dc52-7c2d-422a-b34b-c280801b71c2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028435110000",
                    "title": "Destino: Salvador",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "5a48f1c1-4ffa-480f-898f-f3b2991a5ba5",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032080670000",
                    "title": "Destinos salvajes de Estados Unidos",
                    "seasonCount": 7,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "107168bd-63d8-4041-bc4a-e657b7c393bc",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031378800000",
                    "title": "Deutschland 86",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "979f0405-5f88-4465-b035-db726caac4a6",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022687920000",
                    "title": "Diagnóstico Misterioso",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "8e2fc421-86cf-4f22-8006-89f82bc9ad6b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030757720000",
                    "title": "Dictadores",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "d969b485-1f2c-4caa-8bc0-6d779d4d361e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023164590000",
                    "title": "Dios Inc.",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "d51702b9-11f6-4259-82d8-a9a166b32eb5",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024883340000",
                    "title": "Divorce",
                    "seasonCount": 3,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "9fd6687a-5099-440b-9a98-8d74c40e668d",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021711620000",
                    "title": "Doctor Mateo",
                    "seasonCount": 5,
                    "episodeCount": 43,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 43
                },
                "resource": {
                    "id": "0fdfc6d6-8d56-455a-b6ee-f89a6ad3b8a4",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 43
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026437910000",
                    "title": "Domador de cocodrilos",
                    "seasonCount": 4,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "cf21b230-2010-48a5-852d-53230b85015e",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH003862370000",
                    "title": "Dora, la Exploradora",
                    "seasonCount": 8,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "78f900bd-b0c6-4092-8780-3fb5ebcd2ef1",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029076320000",
                    "title": "Dot",
                    "seasonCount": 2,
                    "episodeCount": 68,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 47
                },
                "resource": {
                    "id": "b05dc2df-172b-4729-9b4f-caf4079f22b3",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 47
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032411780000",
                    "title": "Dot: Construyendo un jardín",
                    "seasonCount": 2,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "3b7d0aea-41a1-456c-a3f4-8ce4007a4f5e",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030513250000",
                    "title": "Dr. Brown: Veterinario sin fronteras",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "18d220ed-b548-4227-8a11-fbc29ede4320",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022861640000",
                    "title": "Dr. Jeff, Veterinario",
                    "seasonCount": 6,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "40aebf80-c875-479c-a299-7a3678aca2db",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032101970000",
                    "title": "Dr. Pie",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "a407f495-d624-433b-beea-ad3b982d5f81",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029814160000",
                    "title": "Dra. K animales extremos",
                    "seasonCount": 8,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "c2d69f66-3b03-4d6e-9561-8075588e1dd1",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020619930000",
                    "title": "Dra. K: Animales exóticos",
                    "seasonCount": 8,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "9c667d49-4811-4171-85ac-dd212dcdd4e8",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030704960000",
                    "title": "Dra. Sandra Lee: Especialista en piel",
                    "seasonCount": 3,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "bc09feb4-34b2-4854-98bc-2e85a5b23a77",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH010187100000",
                    "title": "Drake y Josh",
                    "seasonCount": 4,
                    "episodeCount": 60,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 60
                },
                "resource": {
                    "id": "5942a564-75dd-4abe-bd6c-a1d53aebc2ed",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 60
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031809080000",
                    "title": "Drama total: La guardería",
                    "seasonCount": 1,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "e0482c50-209b-4b68-bc5d-0dae64195d06",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH006703160000",
                    "title": "Duelo animal",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "711a4552-5fd3-4309-8cb1-cf9154cfdcb2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030253160000",
                    "title": "Duelo de comediantes",
                    "seasonCount": 2,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "c277e62e-2efe-4249-9f10-308f7c15d2ca",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026478780000",
                    "title": "Dulces Tentaciones",
                    "seasonCount": 7,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "116cccaf-51b7-4179-ad1d-279f3ab5d391",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH011521120000",
                    "title": "Eastbound & Down",
                    "seasonCount": 4,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 29
                },
                "resource": {
                    "id": "eb15b16e-115c-4ee3-a1a8-05db16208b4a",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 29
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024060330000",
                    "title": "Educando a Nina",
                    "seasonCount": 1,
                    "episodeCount": 133,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 134
                },
                "resource": {
                    "id": "97210e24-b904-4d7a-a2ff-61c4acf680dc",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 134
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030548160000",
                    "title": "El Continental",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "86bc3f48-566e-40d2-b224-2f56a3144f93",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012214800000",
                    "title": "El Efecto Nostradamus",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "039c8eec-1654-4606-b9f2-3ca0a58de915",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022730950000",
                    "title": "El Hipnotizador",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "eb3660de-4d12-455f-80d7-47cc7448ed51",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015389220000",
                    "title": "El Hormiguero",
                    "seasonCount": 5,
                    "episodeCount": 36,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "fb17dad9-fafb-4d3d-b7ca-2001a21dd896",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015203940000",
                    "title": "El Increíble Dr. Pol",
                    "seasonCount": 15,
                    "episodeCount": 45,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "0e065590-a955-4457-9e3c-670e315fc6d9",
                    "published": true,
                    "seasonCount": 15,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027250460000",
                    "title": "El Laboratorio secreto de Thomas Edison",
                    "seasonCount": 1,
                    "episodeCount": 46,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 46
                },
                "resource": {
                    "id": "5503ea4b-7546-4caa-b6fb-1f2935052b55",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 46
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018213070000",
                    "title": "El Peso De La Nación: Especial Niños",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "7e2186e9-d7a3-4628-a133-321547f0349c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015606480000",
                    "title": "El Peso de una Nación",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "caca9be9-54bd-4728-8705-6871d4ac06f8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014837620000",
                    "title": "El Proyecto Alzheimer",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "d71b422f-01b6-4562-a5f2-4717bcae57e4",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021708040000",
                    "title": "El Socio",
                    "seasonCount": 6,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "72cf8508-85e6-4375-99c3-ec1b1bca2d41",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032366490000",
                    "title": "El Tigre Verón",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "bdbbcca8-0462-4c25-bec1-2880ae3ec736",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030539750000",
                    "title": "El accidente",
                    "seasonCount": 1,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "0bfc5733-ab4c-4080-8865-7a93ebe7d8ac",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028200860000",
                    "title": "El asesinato de Laci Peterson",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "7ec8aaa2-49a1-4da0-a8cf-600778294ace",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015098640000",
                    "title": "El barco",
                    "seasonCount": 3,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "0d862f98-b00b-4570-818c-d884da8bf796",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031240930000",
                    "title": "El boom de Silicon Valley",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "e0b0b61e-feef-491f-9089-1e4bec9754a8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022713730000",
                    "title": "El bosque de Karadima: La serie",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "2ef8d0e7-6f81-43be-95f8-c41d9cd69a35",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021508950000",
                    "title": "El capitán Camacho",
                    "seasonCount": 1,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "a69af14a-88c6-4a36-801f-8112986b2126",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027280970000",
                    "title": "El caso de Casey Anthony",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "fbca6a18-88d1-44a2-8bc2-fe4b92e84fd4",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029837020000",
                    "title": "El caso del asesino de la escalera",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "975ba7ee-a1e4-4434-a4f7-8ed39dd0b0e4",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022582150000",
                    "title": "El chiringuito de Pepe",
                    "seasonCount": 2,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "b15751bd-64bb-45f0-b572-a8cb8128e415",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020604400000",
                    "title": "El chiringuito de jugones",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "1466259d-3972-47a5-b041-0cf5dacb7844",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028800510000",
                    "title": "El chiringuito de jugones",
                    "seasonCount": 1,
                    "episodeCount": 54,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 52
                },
                "resource": {
                    "id": "df1a5bb6-1116-486c-ab18-82a17647751c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 52
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023369970000",
                    "title": "El club de la pelea animal",
                    "seasonCount": 6,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "1c31b5cf-724e-450d-a43b-bcf428ba4827",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030625770000",
                    "title": "El cuento de la criada",
                    "seasonCount": 3,
                    "episodeCount": 40,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 29
                },
                "resource": {
                    "id": "fb3baec1-f6eb-4f9a-b633-51ace5d06c0b",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 29
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032067450000",
                    "title": "El diario de Bita y Cora",
                    "seasonCount": 1,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 26
                },
                "resource": {
                    "id": "e8382a74-949a-45be-be50-bbf24c9526df",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 26
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023456640000",
                    "title": "El estado de juego",
                    "seasonCount": 2,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "4d2c8c2a-20de-410b-802a-1d63e3c497bf",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032056910000",
                    "title": "El general Naranjo",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "cf22b2ca-3644-4f5e-a7a6-ace2b87b4494",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026243710000",
                    "title": "El gran apetito de Guy",
                    "seasonCount": 19,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "6f9027b3-fcbb-49ff-b67a-9fdc1b5e028c",
                    "published": true,
                    "seasonCount": 19,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030083670000",
                    "title": "El host",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "0af3563a-ef06-4e69-9410-3834fec9efc8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027740550000",
                    "title": "El incidente",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "97fee483-a312-4b5d-be16-92199e277c25",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH009654770000",
                    "title": "El internado",
                    "seasonCount": 7,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 32
                },
                "resource": {
                    "id": "ea169227-bf4a-4fa7-a016-a5ccf6db1aaa",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 32
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026583120000",
                    "title": "El jardín de bronce",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 22
                },
                "resource": {
                    "id": "f9d97a11-cbfa-4f1f-b4aa-b23e19c777e3",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 22
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031028480000",
                    "title": "El lado salvaje de África",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "6955e1fb-7fc5-4982-af24-bc03ec89db54",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029933430000",
                    "title": "El manual del dictador",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "2b8de668-ceea-48b8-9c55-a4d85befc2ba",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030774980000",
                    "title": "El misterio de los Hunter",
                    "seasonCount": 3,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "7a610a0a-eec8-4bc3-aea3-f54c54a48cf0",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029832680000",
                    "title": "El mundo de Craig",
                    "seasonCount": 2,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "f3b9841d-ca0e-47b1-8ce3-eb9eb80dbb88",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022598580000",
                    "title": "El mundo de Luna",
                    "seasonCount": 5,
                    "episodeCount": 71,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "2c1d7ec7-6349-4ddb-8f35-761f59df21f5",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017630470000",
                    "title": "El negocio",
                    "seasonCount": 4,
                    "episodeCount": 73,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 54
                },
                "resource": {
                    "id": "a07f7db4-3247-4e63-886a-c1ad92c62c38",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 54
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018959530000",
                    "title": "El otro sueño",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "dd052c05-a056-4fea-8e95-c3a107f4ffc2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029265490000",
                    "title": "El padre de Caín",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "cb13586c-0041-4606-bab9-8e41921749ae",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013171790000",
                    "title": "El precio de la historia",
                    "seasonCount": 16,
                    "episodeCount": 33,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "d618d2e7-084d-4692-a53d-89d645f702c6",
                    "published": true,
                    "seasonCount": 16,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028274230000",
                    "title": "El reino del león",
                    "seasonCount": 2,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "71c2a36e-036a-4daa-8a71-f3f05790066a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030272580000",
                    "title": "El rey del valle",
                    "seasonCount": 2,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "cdb73928-3371-4b02-a7ed-8b34df69a40e",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026475150000",
                    "title": "El zoológico del Bronx",
                    "seasonCount": 3,
                    "episodeCount": 19,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "0b53a83b-058d-4598-b838-299a3ff8e1fa",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026909420000",
                    "title": "El árbol de tu vida",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "aa0eebf3-2f21-4d6b-9209-7eb6a0fffa4d",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030223550000",
                    "title": "El último bastión de Hitler",
                    "seasonCount": 2,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "285a18de-0af2-440b-9ccf-865f0d9c24ac",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021724560000",
                    "title": "Emergencias Extremas",
                    "seasonCount": 0,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "bef94a8f-77d3-485b-803c-d938d81369f0",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031355150000",
                    "title": "En busca de la verdad",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "7a84651b-aac0-4274-981a-5c3e6b2ce6cf",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030753760000",
                    "title": "En la cocina",
                    "seasonCount": 22,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "f492e358-7688-483f-bdf6-057d8856af14",
                    "published": true,
                    "seasonCount": 22,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032341220000",
                    "title": "En primera persona",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "e86ebac1-08c5-4338-943c-747873ea66c0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027376750000",
                    "title": "En un millón de años",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "d1169e6b-2d3c-4e64-b348-4b4ceccb5418",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032117670000",
                    "title": "Encantadoras",
                    "seasonCount": 1,
                    "episodeCount": 57,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 55
                },
                "resource": {
                    "id": "12c04673-912c-4066-8777-8a33b10186f1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 55
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017977800000",
                    "title": "Enchufe TV",
                    "seasonCount": 3,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 24
                },
                "resource": {
                    "id": "d460fa09-70a5-49e6-ad46-382e94f1afda",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 24
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024461390000",
                    "title": "Encierro Paranormal",
                    "seasonCount": 3,
                    "episodeCount": 27,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 26
                },
                "resource": {
                    "id": "2da82832-22ae-4f07-9c20-5b0322cd62ee",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 26
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014686410000",
                    "title": "Enlightened",
                    "seasonCount": 2,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 31
                },
                "resource": {
                    "id": "185eb0b2-bf6c-4704-8a51-281b22a1d1c5",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 31
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH006670150000",
                    "title": "Entourage",
                    "seasonCount": 8,
                    "episodeCount": 96,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 121
                },
                "resource": {
                    "id": "036b3eba-2cf8-416b-a508-58e13ad55ae4",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 121
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024502000000",
                    "title": "Entrenadores Fuera de Línea",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "9a332b9e-3969-463b-bee9-cd5dc687faeb",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023677780000",
                    "title": "Enviado especial",
                    "seasonCount": 2,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "66b89235-2aad-4866-8a93-c57d7461a375",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032209650000",
                    "title": "Epic Warrior Women",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "daea7087-10e8-43ad-b8ca-edf6794e445d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH008062440000",
                    "title": "Epitafios",
                    "seasonCount": 2,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 27
                },
                "resource": {
                    "id": "ee81d462-35b9-435f-b74d-f234e72cd1bb",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 27
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030355390000",
                    "title": "Errar es humano",
                    "seasonCount": 1,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "00213362-274b-4c76-91f2-d6d90847c224",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022542860000",
                    "title": "Escandalosos",
                    "seasonCount": 4,
                    "episodeCount": 25,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "1bacb87f-808a-43d7-b68c-a005d21ab410",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026220810000",
                    "title": "Esclavos de la cienciología",
                    "seasonCount": 3,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "24b552cc-be8a-45d2-99d3-7b1bd03322d1",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031736020000",
                    "title": "Escuadrón del tiempo",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "7e770fd2-9173-423c-8085-e5ac21fe3dc2",
                    "published": false,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028053700000",
                    "title": "Escuela de juguetes",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "91416636-44a6-4f66-a926-efebef77a0a7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027862450000",
                    "title": "Escuela de rock",
                    "seasonCount": 3,
                    "episodeCount": 39,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 39
                },
                "resource": {
                    "id": "bdabe087-20c1-4576-a419-1ea8b0b15022",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 39
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024950590000",
                    "title": "Escuela para Maridos México",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "6c00e900-7fc4-4fa2-91dc-453206a2abcd",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021405000000",
                    "title": "Escuela para maridos",
                    "seasonCount": 2,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "b557efd0-f48e-4900-8e19-da85e02985c6",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017996890000",
                    "title": "Especiales Realeza",
                    "seasonCount": 0,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "055709b2-886c-4ddb-a377-e44616d66b34",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021840360000",
                    "title": "Especiales ¡HOLA! TV",
                    "seasonCount": 0,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "069d7a58-3db0-40b5-aa76-ee8ed98ee0f1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029993620000",
                    "title": "Estación 19",
                    "seasonCount": 2,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "bbe8ec51-c4d3-41bc-bbed-8cbafcb2889d",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032045860000",
                    "title": "Euphoria",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "a3bffbe9-58f7-480a-8612-6856fcbd308d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029323480000",
                    "title": "Ex on the Beach",
                    "seasonCount": 3,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "a92ac66b-d367-4cf6-9cf8-a724e8fae48c",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030112850000",
                    "title": "Ex on the beach: La venganza de los ex",
                    "seasonCount": 3,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "01ff3c7f-ba30-445b-9116-01549963f98b",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019589690000",
                    "title": "Exploradores espaciales",
                    "seasonCount": 3,
                    "episodeCount": 38,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "af0310be-050d-4d87-9cb2-89bbe969ef09",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007424450000",
                    "title": "Explorer",
                    "seasonCount": 11,
                    "episodeCount": 21,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "5add72c2-cb1e-4aef-a9e2-14ae5a8ac080",
                    "published": true,
                    "seasonCount": 11,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030339200000",
                    "title": "Explorer Investigation",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "f8515709-941e-4818-89ae-1cd79fa42956",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027106960000",
                    "title": "Familia de Hierro",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "9a4b646f-fd51-44a2-b06a-f427d3f8cfa1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031974830000",
                    "title": "Familia de veterinarios",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "54ae10a8-39e7-4740-be28-65773eff94ea",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018824610000",
                    "title": "Fargo",
                    "seasonCount": 3,
                    "episodeCount": 36,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 34
                },
                "resource": {
                    "id": "5c5b00bb-ae3d-4c8e-8f3d-b55c113489c1",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 34
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026911370000",
                    "title": "Fear Factor",
                    "seasonCount": 3,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "77dd3981-f86a-4705-bb88-d495a98b25a7",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022293440000",
                    "title": "Fear the Walking Dead",
                    "seasonCount": 5,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "4ef90c42-7f74-4810-ab9d-eb2ac395695e",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029099730000",
                    "title": "Felices para siempre",
                    "seasonCount": 3,
                    "episodeCount": 40,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 56
                },
                "resource": {
                    "id": "d9473df5-3cc1-4544-a9c6-1fd72921fd3a",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 56
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027362160000",
                    "title": "Festival Internacional del Humor 2017",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "4067daf2-0f23-45ee-836e-027495f87027",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026039260000",
                    "title": "Feud: Bette and Joan",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "1246ea60-7f7b-4618-890c-45a94bfb1464",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029146570000",
                    "title": "Fiebre del oro: río revuelto",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "d9245650-e0e5-47e1-990a-055312909315",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030322940000",
                    "title": "First Ladies Revealed",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "c3382db9-b01b-4c70-9d6e-c3e8f927dbea",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023252260000",
                    "title": "Fit to Fat to Fit",
                    "seasonCount": 2,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "9e4e47e8-e778-4d3c-ab98-a35d9bd887d0",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH009646730000",
                    "title": "Five Days",
                    "seasonCount": 2,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "a8593f09-aa3c-43fe-8450-cb21d3de4f86",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH009250170000",
                    "title": "Flight of the Conchords",
                    "seasonCount": 2,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 27
                },
                "resource": {
                    "id": "6616af76-2bfa-471e-b8e1-3ef7e3901390",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 27
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028195900000",
                    "title": "Floribama Shore",
                    "seasonCount": 2,
                    "episodeCount": 19,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "27079e28-1d69-4c73-bfdf-0809a9bc4baf",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029633560000",
                    "title": "Food truck challenge",
                    "seasonCount": 2,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "4f51fac5-aec4-42ff-8136-30dd3618362a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023306130000",
                    "title": "Fortitude",
                    "seasonCount": 3,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "1e31727f-c9ee-43d7-aca8-b1d1b55f8d55",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023149500000",
                    "title": "Fronteras Peligrosas",
                    "seasonCount": 4,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "1bb75f64-bb2f-429d-9cf9-5bef21319cc1",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031877530000",
                    "title": "Fronteras al límite",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "ebcaad76-e3e4-493c-8709-a62ab7a95f51",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030921540000",
                    "title": "Fuera del armario",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "1e09841e-0259-4627-9512-6c5b8838dd4d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027791880000",
                    "title": "Fugitivos",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "eba5d750-3613-4bfb-9ce3-506d541fbc2c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012410320000",
                    "title": "Funny or Die Presents",
                    "seasonCount": 2,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "4e531c36-b75a-4cdb-ab2b-a6e52cff5658",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030765250000",
                    "title": "Furiki Wheels",
                    "seasonCount": 1,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "1b8ae90d-aac8-4396-a50d-4e52cf72e3f9",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028190060000",
                    "title": "Future Man",
                    "seasonCount": 2,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 26
                },
                "resource": {
                    "id": "4910f7fc-7db1-4e4d-bb73-75c05d8d822b",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 26
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029748090000",
                    "title": "Gallina Pintadita",
                    "seasonCount": 3,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "9a5f92a1-1a06-47d3-ae1b-a43c013347aa",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030719770000",
                    "title": "Gallina pintadita mini",
                    "seasonCount": 2,
                    "episodeCount": 34,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "0401e1a7-50c0-4a90-b7f6-5554e4316129",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022544450000",
                    "title": "Game Shakers",
                    "seasonCount": 3,
                    "episodeCount": 37,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "044b16a0-ce04-476d-8b43-4bd057336bfb",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013898090000",
                    "title": "Game of Thrones",
                    "seasonCount": 8,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "aa52cf82-d196-483d-a3f1-bb09b3e8c54f",
                    "published": false,
                    "seasonCount": 8,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013939150000",
                    "title": "Game of Thrones",
                    "seasonCount": 8,
                    "episodeCount": 73,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 77
                },
                "resource": {
                    "id": "bc190fcf-4eab-4197-8d6d-01b0fbcf448e",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 77
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015353080000",
                    "title": "Generador Rex",
                    "seasonCount": 3,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "a3e5eab0-508b-4d5c-8d27-dad2d86231c2",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH010696960000",
                    "title": "Generation Kill",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 15
                },
                "resource": {
                    "id": "5b9fcc2a-867d-4600-969b-11f794ddf64b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 15
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031868750000",
                    "title": "Gentleman Jack",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "d53caa75-af2d-40e1-817e-b76714af9e89",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016751530000",
                    "title": "Geordie Shore",
                    "seasonCount": 19,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "456ac8e6-8b0f-4daa-b27e-753e0ea0ce31",
                    "published": true,
                    "seasonCount": 19,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032067560000",
                    "title": "Get a room con Carson y Thom",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "6130a1f8-f477-4e8a-a70a-135a0560d340",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018033780000",
                    "title": "Getting On",
                    "seasonCount": 3,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "d4ea22c0-9c2f-45fb-bce8-e89a8086f7a0",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026243930000",
                    "title": "Giada en Italia",
                    "seasonCount": 3,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "f86086dc-4fa4-451a-ae19-bbe9f88c074a",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015401630000",
                    "title": "Girls",
                    "seasonCount": 6,
                    "episodeCount": 64,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 64
                },
                "resource": {
                    "id": "4c975e24-3145-46f4-a6ea-c71dbd84b3e2",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 64
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028908370000",
                    "title": "Gone",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "e64c878a-3fb7-454a-9b5e-d7460477bcd7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019574650000",
                    "title": "Gotham",
                    "seasonCount": 5,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "20cd0051-c633-4c79-b055-55d86440d37f",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018198480000",
                    "title": "Gran Hotel",
                    "seasonCount": 3,
                    "episodeCount": 39,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 47
                },
                "resource": {
                    "id": "54b3257a-e9a0-418f-9fef-9081c26408e9",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 47
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030505810000",
                    "title": "Greyzone",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "70c2e97a-7052-4976-be35-63db95f3aa2e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020582970000",
                    "title": "Guerra en Dos Ruedas",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "aaae86d2-8fac-4599-a39e-c0d59767189e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021589030000",
                    "title": "Hablemos del Cosmos",
                    "seasonCount": 5,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "a5d7a0da-9403-4088-b4be-a288b6d0c7e0",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017974830000",
                    "title": "Había una Vez...un Homicidio",
                    "seasonCount": 3,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "af4ecd57-a414-4545-a5b8-6125da79ebe8",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028730180000",
                    "title": "Hamilton's Pharmacopeia",
                    "seasonCount": 2,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "66e76951-1d62-4b71-aeac-a5255a816a82",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027527550000",
                    "title": "Harlots",
                    "seasonCount": 3,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "d618dcd2-7c8c-48d9-99be-4518889d18de",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024392140000",
                    "title": "Hawai 5.0",
                    "seasonCount": 10,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "a486b070-5e91-45be-8445-a3d56fd2804d",
                    "published": true,
                    "seasonCount": 10,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017726990000",
                    "title": "Hello Ladies",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "9c96d774-e83a-47d1-b35e-e7950bd1dd35",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019534320000",
                    "title": "Henry Danger",
                    "seasonCount": 5,
                    "episodeCount": 87,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "f7799879-7cae-4ef3-b3c4-9d75e87e6489",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028481810000",
                    "title": "Here and Now",
                    "seasonCount": 1,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "58fdd96a-8925-4699-86d5-44bb8bb4d9f5",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018042590000",
                    "title": "Hermanas Gitanas",
                    "seasonCount": 3,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "92cdb39e-0580-4071-b238-0ac11a2d9443",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021164950000",
                    "title": "Hermano de Jorel",
                    "seasonCount": 3,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "e0ad3dbf-6122-4881-8cf0-72d2ddc1ecd4",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024497530000",
                    "title": "Hermanos cazafantasmas",
                    "seasonCount": 2,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "2da4e406-bf03-463b-bcee-56751114215e",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027579720000",
                    "title": "Hierro y fuego",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "a1e80558-c25d-4185-b07d-844b85356b0d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024723690000",
                    "title": "High Maintenance",
                    "seasonCount": 3,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "5b0d3820-1e72-449c-8317-92b958f7c258",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026957160000",
                    "title": "Hijas de la poligamia",
                    "seasonCount": 4,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "d439de42-6b60-4778-83e1-151147296c8e",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027587840000",
                    "title": "Hitler vs. Churchill: El águila y el león",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "9c6e5cb7-1720-4de1-a7d9-6d60a9499d15",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028626350000",
                    "title": "Hombre de armas",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "0668da4a-9d5a-4e03-a3a3-27f2d0e8830e",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023546560000",
                    "title": "Hombre vs. universo",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "9407907c-018e-4c7d-a902-6204e47db549",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014785690000",
                    "title": "Homeland",
                    "seasonCount": 7,
                    "episodeCount": 91,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 82
                },
                "resource": {
                    "id": "a1b8f0cd-01d9-4607-8fb5-4676e3885e29",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 82
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012258630000",
                    "title": "How to Make It in America",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "54f9fd36-7ed2-43db-844f-3bb0b62101a0",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028749690000",
                    "title": "Huang's World",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "d68b63f6-e219-4f74-aecc-18a82f417cae",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017156540000",
                    "title": "Humanidad Decodificada",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "f0636b7d-8b7f-48d7-94f8-f01ae8f8abb1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH011530560000",
                    "title": "Hung",
                    "seasonCount": 3,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 39
                },
                "resource": {
                    "id": "ee0224f7-8e50-49b8-a855-a9b391952709",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 39
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026327680000",
                    "title": "Hunter Street",
                    "seasonCount": 3,
                    "episodeCount": 21,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "988bcdde-49de-4b9d-b476-b0af256e4930",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020232790000",
                    "title": "Héroes cotidianos",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "08105f29-d408-4135-a4bf-08a3ca7976b0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032250870000",
                    "title": "Héroes de la conservación",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "5cae8a7a-957d-4662-815e-7c44ecff74b4",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031053560000",
                    "title": "I Am the Night",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "5bec4972-60bd-40d4-a77e-28aef4fa1d2c",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028076620000",
                    "title": "I'm Sorry",
                    "seasonCount": 2,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 25
                },
                "resource": {
                    "id": "d9a21fed-c8e8-4c25-99cb-023d04118779",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 25
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031283000000",
                    "title": "Imperio",
                    "seasonCount": 1,
                    "episodeCount": 90,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "69735918-12af-4480-b786-88b281aeb7d9",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025367150000",
                    "title": "Imperio salvaje",
                    "seasonCount": 3,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "b28d7837-99a1-41f0-8ae0-4a27db0abd13",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029506590000",
                    "title": "Imperios en juego",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "04512084-9af6-4230-8e0f-2a9d0e827409",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030550330000",
                    "title": "Impuros",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "df6e0b45-a2e0-4cce-a809-ae201a0cfb7e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031283010000",
                    "title": "Império",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "d8974d36-d8b3-489b-aa85-a54e5c291c39",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH010203400000",
                    "title": "In Treatment",
                    "seasonCount": 3,
                    "episodeCount": 106,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 138
                },
                "resource": {
                    "id": "30a69cf2-cf58-46ec-b2e7-c94a297fd2fd",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 138
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032236420000",
                    "title": "Informer",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "bc6d26df-369b-41ce-8093-d9fc1410d89b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029859200000",
                    "title": "Innocent",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "7a0c5342-035c-41e6-a1f5-efd5550cda9b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024883020000",
                    "title": "Insecure",
                    "seasonCount": 3,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 24
                },
                "resource": {
                    "id": "9ad42ae1-3a22-49da-b85e-0a11c6d1e98e",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 24
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029262220000",
                    "title": "Instinto diabólico",
                    "seasonCount": 2,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "5cbe45f0-00a9-4c7a-9f5a-a28a12ad6e30",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022782790000",
                    "title": "Into the Badlands",
                    "seasonCount": 3,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "048cde3b-0c76-4d44-98bf-7985d64e1da2",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031214810000",
                    "title": "Invasión animal",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "5162739d-f9d9-4547-a3fd-00f7d1477d07",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025969400000",
                    "title": "Inventos Legendarios",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "7ca21d18-e525-48fc-8977-8b84f338f1af",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022042160000",
                    "title": "Ironías de la Historia",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "b940a027-46ce-48ea-b80b-5073fca53b36",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016134120000",
                    "title": "Isabel",
                    "seasonCount": 3,
                    "episodeCount": 40,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 57
                },
                "resource": {
                    "id": "3695f7da-af4a-43c5-a8fc-226617c01a98",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 57
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031853850000",
                    "title": "Isla salvaje Alaska",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "de438ae4-ed9c-49f2-95b3-84ffafd1c595",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030626930000",
                    "title": "Island of the Monsoon",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "c201972a-0895-4055-8a8b-082ea787c1c5",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018033790000",
                    "title": "Ja'mie: Private School Girl",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "e47247e6-533d-4019-a899-c441404f318b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027247940000",
                    "title": "Jaime y sus tentáculos",
                    "seasonCount": 2,
                    "episodeCount": 81,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 72
                },
                "resource": {
                    "id": "677cd4e2-c06f-4da8-bbcd-4933a02c2fd4",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 72
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027116440000",
                    "title": "Jamie's Got Tentacles!",
                    "seasonCount": 2,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "0ac70d4f-0fb2-4811-98f8-5cf6aea54033",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031427020000",
                    "title": "Japón desde el espacio",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "0eb6c60c-ada8-46a8-90f4-8db67fbc7884",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027378400000",
                    "title": "Javi y el Club del árbol",
                    "seasonCount": 2,
                    "episodeCount": 25,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "e91c27b8-5884-49aa-be97-2adab113edd3",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012491840000",
                    "title": "Jersey Shore",
                    "seasonCount": 6,
                    "episodeCount": 47,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 47
                },
                "resource": {
                    "id": "be01559a-a7ac-419c-ac73-f62d8f51d1b9",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 47
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029335470000",
                    "title": "Jersey Shore: Vacaciones en familia",
                    "seasonCount": 3,
                    "episodeCount": 27,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "08286698-720d-4634-ab0d-80e29bdeb8dd",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032080570000",
                    "title": "JingleKids",
                    "seasonCount": 1,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "7032eff7-f608-4f4c-a28a-b1ebc3585386",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH010290590000",
                    "title": "John Adams",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "afadf3bc-8304-4f6c-b2d4-0373fde72eed",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH009249940000",
                    "title": "John From Cincinnati",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "fe5529d7-0e69-48c1-9947-1a40ce8e5e71",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019421540000",
                    "title": "Jonah From Tonga",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "d05de600-439b-4905-9939-a4f8e52588a5",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019556810000",
                    "title": "Jonah from Tonga",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "ecece68b-43a5-4b04-8154-6374be56f207",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026243790000",
                    "title": "Juegos en el Súper con Guy",
                    "seasonCount": 20,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "c7162f70-4295-4e7b-9882-31fde6f88250",
                    "published": true,
                    "seasonCount": 20,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026774110000",
                    "title": "Just Tattoo Of Us",
                    "seasonCount": 4,
                    "episodeCount": 27,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "4c927377-9006-4b06-8bbd-817fc62227d9",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031404340000",
                    "title": "Just Tattoo of Us USA",
                    "seasonCount": 2,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "2442855c-3b27-424c-bd65-e51ae301ef14",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029869310000",
                    "title": "Justicia salvaje",
                    "seasonCount": 13,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "2bcb1b48-30e4-4ae9-b9eb-0c1f4f92f171",
                    "published": true,
                    "seasonCount": 13,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027805900000",
                    "title": "Kally's MashUp",
                    "seasonCount": 2,
                    "episodeCount": 45,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 49
                },
                "resource": {
                    "id": "d74c565e-232c-4e91-ba31-d3f69496e651",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 49
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH003120180000",
                    "title": "Karlos Arguiñano en tu cocina",
                    "seasonCount": 0,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "659568cc-95df-401f-b50e-5bb45fc05190",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020483910000",
                    "title": "Karlos Arguiñano en tu cocina",
                    "seasonCount": 0,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "ef69fdb5-59ce-436c-b3a8-9089452c350d",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031180090000",
                    "title": "Killing Eve",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "466c273a-d5fc-4f73-a2ae-4e7d41119b66",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029498740000",
                    "title": "Kiri",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "df802ce9-cc23-4b3a-acd6-8ec8be6b36d2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027880510000",
                    "title": "Knightfall",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "976832fa-a4ec-4476-9dab-0d3907d54a91",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH011292950000",
                    "title": "La Casa de Saddam",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "9e4f938f-ec06-4726-869a-7ea07d4fb727",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007375290000",
                    "title": "La Casa de los Dibujos",
                    "seasonCount": 3,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "530ccebb-d3ca-498c-bb14-a944d3a83f92",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032515500000",
                    "title": "La Costa Salvaje de Colombia",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "7a8c64eb-056a-4ad0-be0c-ce781d9c09d9",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031473010000",
                    "title": "La Guzmán",
                    "seasonCount": 1,
                    "episodeCount": 54,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 45
                },
                "resource": {
                    "id": "be37bba4-2c9e-4992-9818-0008c8837d88",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 45
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024481790000",
                    "title": "La Hermandad",
                    "seasonCount": 2,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "6a104271-db4a-4511-8b55-6035703d3bd8",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019325340000",
                    "title": "La Maldición de la Isla",
                    "seasonCount": 6,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "41eb962c-f26f-4c36-980e-73c7c6fc6191",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022798730000",
                    "title": "La Maldición: La Vida y Muertes de Robert Durst",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "3e03f8ce-2e2b-4850-918e-dfa6c90c7028",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024920060000",
                    "title": "La Rebelión de los Bárbaros",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "9cbe5549-3996-4807-8471-943d2006070f",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021656820000",
                    "title": "La casa del mar",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "fe0d83d6-118f-48c0-98bc-c44e66b516cb",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019495710000",
                    "title": "La ciencia de lo absurdo",
                    "seasonCount": 6,
                    "episodeCount": 93,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 37
                },
                "resource": {
                    "id": "ca21b827-4116-407b-9385-728512023d34",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 37
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021736210000",
                    "title": "La ciencia de lo absurdo",
                    "seasonCount": 6,
                    "episodeCount": 82,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 27
                },
                "resource": {
                    "id": "ebb2e8f5-158d-4df2-a394-ef48a943c5c1",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 27
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022186400000",
                    "title": "La culpa es de Colón",
                    "seasonCount": 3,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 22
                },
                "resource": {
                    "id": "5af902f5-e423-4014-a95a-4d2b4c9929e4",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 22
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027436170000",
                    "title": "La culpa es de Colón",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "bdb4843b-ae5e-4746-b894-72ce896c5a94",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029148590000",
                    "title": "La culpa es de Colón: Edición mujeres",
                    "seasonCount": 2,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "07a7f367-481b-4f3d-9ce0-0927f6c4686b",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026835660000",
                    "title": "La culpa es de Cortés",
                    "seasonCount": 4,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "5b0badd9-e1c6-4d3d-90c4-998b8da53271",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028258060000",
                    "title": "La culpa es de Llorente",
                    "seasonCount": 2,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "7cfbbbfa-aa66-4ac3-86fb-f0341f86efd0",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH001490540000",
                    "title": "La dueña",
                    "seasonCount": 1,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 32
                },
                "resource": {
                    "id": "13119116-6b01-4d8f-bb66-34e4426fc707",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 32
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029320760000",
                    "title": "La era del terrorismo",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "c64052b3-fe2f-49de-9554-40f8d2383d45",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017315410000",
                    "title": "La familia del barrio",
                    "seasonCount": 5,
                    "episodeCount": 30,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "cf9141f4-86e8-436d-a908-195398528a2b",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032651570000",
                    "title": "La fiesta",
                    "seasonCount": 1,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "48b27ba3-6a76-458c-be2c-f4a984678ecd",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023817190000",
                    "title": "La historia de Dios",
                    "seasonCount": 3,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "630480c0-cb99-48a4-a914-97d31c496725",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016257390000",
                    "title": "La humanidad: Historia de todos nosotros",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "ff241b91-4c77-4b8f-bf2d-dc2965ef60d4",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030355650000",
                    "title": "La maldad en control",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "7a1064ad-644c-44a5-a81b-4d5d58eb1740",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025322730000",
                    "title": "La maldición de Shepherdstown",
                    "seasonCount": 2,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "1bf3c6de-4fe3-4964-9d06-44bb3bd1a1f3",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027587980000",
                    "title": "La maquinaria de la muerte nazi",
                    "seasonCount": 0,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "bca1c850-f9c0-445d-afec-6b39c2579b2e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027625660000",
                    "title": "La pandilla de la selva",
                    "seasonCount": 2,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "841ca80a-69a6-4d20-98c5-95ab77c9f359",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030338750000",
                    "title": "La venganza de los ex",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "58a50e49-085e-4411-83ce-5c890fcf7fd8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031378810000",
                    "title": "La verdad",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "6680a935-abdc-42f0-8e20-e097372b14ff",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027383540000",
                    "title": "La vida secreta de las parejas",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "69346c0e-d251-4965-8e4d-1a69acc287cb",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031933920000",
                    "title": "Lado a lado",
                    "seasonCount": 1,
                    "episodeCount": 96,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "f0cee9de-4597-43e6-a976-b3701420c13f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031702470000",
                    "title": "Las 9 caras de Jane",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "fd177352-cc7a-4221-85f1-cc0dafe269ff",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027112500000",
                    "title": "Las aventuras de Blinky Bill",
                    "seasonCount": 1,
                    "episodeCount": 55,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 58
                },
                "resource": {
                    "id": "a1aec410-68c2-45c3-ad68-d4c8871b8d2e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 58
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012842550000",
                    "title": "Las aventuras de Jimmy Neutron: el niño genio",
                    "seasonCount": 3,
                    "episodeCount": 61,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 60
                },
                "resource": {
                    "id": "c1c72b62-4968-4783-91b7-cd22206c076c",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 60
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024273240000",
                    "title": "Las chicas superpoderosas",
                    "seasonCount": 3,
                    "episodeCount": 39,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "16e44228-5e61-4de9-a5af-72169a80bc02",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030350700000",
                    "title": "Las reinas del shopping",
                    "seasonCount": 1,
                    "episodeCount": 25,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "c2cc2dc8-8553-440a-8432-9801283d3bdd",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018833490000",
                    "title": "Last Week Tonight With John Oliver",
                    "seasonCount": 6,
                    "episodeCount": 166,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 138
                },
                "resource": {
                    "id": "bf38d249-7e8e-45a7-bf90-76d5ebc353bd",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 138
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030311780000",
                    "title": "Legacies",
                    "seasonCount": 2,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "47bb7597-9fab-4fcf-8fb6-b8959979ce5e",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025730610000",
                    "title": "Legion",
                    "seasonCount": 3,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "2a13612f-1564-4084-95e3-ba90f21fdb39",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029389750000",
                    "title": "Liar",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "2508302c-777c-4657-bd99-b717a675aa4d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030043130000",
                    "title": "Lilybuds",
                    "seasonCount": 1,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 24
                },
                "resource": {
                    "id": "054cd8a3-eed5-4903-8f68-ce01a51604ad",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 24
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031363530000",
                    "title": "Lindsay Lohan: La dueña de la playa",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "d028c858-b942-4286-9d60-b47bfabe3ad2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016690460000",
                    "title": "Line of Duty",
                    "seasonCount": 5,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "450173d5-980b-48dc-a870-e009dbfb97ad",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025624330000",
                    "title": "Llámame Bruna",
                    "seasonCount": 3,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 26
                },
                "resource": {
                    "id": "a69d84bb-9418-4c7c-913c-3b57b8845659",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 26
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026377120000",
                    "title": "Lo mejor de La hora Hola",
                    "seasonCount": 1,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "56ec1990-c6fb-4b4c-8d19-05c7fa17ed4a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025938750000",
                    "title": "Lo que escondían sus ojos",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "d17c6d6f-9b40-41d2-9cd8-cf39ceb0e028",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016751400000",
                    "title": "Locos por los Autos",
                    "seasonCount": 8,
                    "episodeCount": 28,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "68491828-1996-436e-ad48-866d2201e810",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018328980000",
                    "title": "Looking",
                    "seasonCount": 2,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "a0eea14e-198a-47ce-bf69-17b9abb0bcc4",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024436520000",
                    "title": "Los 7 Pecados Capitales",
                    "seasonCount": 0,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "4279edf5-d56c-4239-8ec2-e525541bf59a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029528630000",
                    "title": "Los 8 escalones: Camino al Mundial",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "22400230-c569-4b03-b883-a36c07cda793",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025406070000",
                    "title": "Los Busby",
                    "seasonCount": 5,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 26
                },
                "resource": {
                    "id": "d9ca342a-cf84-4295-8abe-b660c6363e78",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 26
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032128660000",
                    "title": "Los Espookys",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "6d0378a8-6bf3-4efb-a4d5-b3711a898c0d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031853830000",
                    "title": "Los Fiennes redescubren Egipto",
                    "seasonCount": 0,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "0f72ca92-966c-41ed-8cf6-7aaebdf28c37",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028797150000",
                    "title": "Los Fixies",
                    "seasonCount": 2,
                    "episodeCount": 52,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 33
                },
                "resource": {
                    "id": "d5afe1fb-69e4-4402-9048-e46c45600085",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 33
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017961230000",
                    "title": "Los Jóvenes Titanes en acción",
                    "seasonCount": 5,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "7485104c-5da2-4715-bfb7-18b7fd905bbc",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030884410000",
                    "title": "Los Kim: radiografía de Corea del Norte",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "b8eecbbb-ce9f-4a60-9fac-73fd77abb521",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032207880000",
                    "title": "Los Polos",
                    "seasonCount": 1,
                    "episodeCount": 41,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 36
                },
                "resource": {
                    "id": "5ea37454-0784-4939-bbc7-b49616a1e8e1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 36
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH009360990000",
                    "title": "Los Soprano",
                    "seasonCount": 6,
                    "episodeCount": 86,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 120
                },
                "resource": {
                    "id": "744ddf8a-1acd-455f-a6f1-7cc7d0b62d8d",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 120
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021223440000",
                    "title": "Los animales más peligrosos",
                    "seasonCount": 7,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "fcc00a23-9725-47a5-80cb-4d46edaba753",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031241040000",
                    "title": "Los condenados",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "95ee643d-9c05-44ac-b356-7816fa5598dd",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026437840000",
                    "title": "Los depredadores más peligrosos de África",
                    "seasonCount": 4,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "b40e0156-2cf1-4055-be6f-53fbfbe052b2",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029853170000",
                    "title": "Los diarios zen de Garry Shandling",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "46bd132b-8e2a-4d59-9944-811cc4a3a90b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029125770000",
                    "title": "Los hermanos Menéndez: la historia jamás contada",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "b1d76d9a-3835-473e-92bb-0037e8a1ea6d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007882620000",
                    "title": "Los hombres de Paco",
                    "seasonCount": 9,
                    "episodeCount": 109,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 127
                },
                "resource": {
                    "id": "29838806-8777-46e0-8569-65a7c2a83f85",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 127
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027745870000",
                    "title": "Los más lindos",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "ab33124d-b45d-488c-904f-36b93c945e67",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH005454650000",
                    "title": "Los padrinos mágicos",
                    "seasonCount": 10,
                    "episodeCount": 56,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 57
                },
                "resource": {
                    "id": "7fc9a61b-861b-42a5-8f22-8c577b57d839",
                    "published": true,
                    "seasonCount": 10,
                    "episodeCount": 57
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030119450000",
                    "title": "Los secretos de La Biblia",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "a9a1e443-0272-4be4-8fcc-022612dbda03",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH009471020000",
                    "title": "Los secretos de la historia",
                    "seasonCount": 6,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "f5e07d72-44e9-4782-b4bc-efc5dbc589f5",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017252840000",
                    "title": "Los vecinos en guerra",
                    "seasonCount": 1,
                    "episodeCount": 129,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 138
                },
                "resource": {
                    "id": "533190f9-2900-4457-86b4-d5154739f0fa",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 138
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022469440000",
                    "title": "Los últimos días de los Nazis",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "f6c52df2-4610-4fc3-af40-8d8d60baa317",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH000524230000",
                    "title": "Lucha Libre AAA",
                    "seasonCount": 2,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "92833dee-f588-443d-9f09-ffc3c70f0ac9",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014936960000",
                    "title": "Luck",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "6e52d956-f3c0-4f96-b533-9ef90a212f1f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026172720000",
                    "title": "Lucky Ladies México",
                    "seasonCount": 3,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "8c39f5b9-3ea4-44b5-a438-a9770c96f2ae",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017434950000",
                    "title": "Luna, el misterio de Calenda",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "d59a9251-564c-41ff-9c9f-819948dc7489",
                    "published": false,
                    "seasonCount": 2,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031474390000",
                    "title": "MTV Acaplay",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "a45d6b29-2af1-4a57-a994-797a44cd6472",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027800960000",
                    "title": "MTV Caniggia libre",
                    "seasonCount": 3,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "3f466982-0ec9-4de6-ab22-23c7a67d7ec8",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025971220000",
                    "title": "Madiba",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "f8c88864-c7aa-4780-88d2-f1e8a9c8954e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032476810000",
                    "title": "Maestros del ceviche",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "39fb09bc-f1af-4cb0-b959-0aba767e614d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022107530000",
                    "title": "Magnífica 70",
                    "seasonCount": 3,
                    "episodeCount": 57,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 46
                },
                "resource": {
                    "id": "aa0b773c-1c38-49fc-8ea6-a36c08e2011e",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 46
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028898080000",
                    "title": "Mama June: la transformación",
                    "seasonCount": 3,
                    "episodeCount": 27,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "6579ea98-dd71-4fcc-b535-90fb7777029d",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019256530000",
                    "title": "Manhattan",
                    "seasonCount": 2,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 41
                },
                "resource": {
                    "id": "002e2921-4751-4dd0-9320-f3cb25ae138b",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 41
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018576480000",
                    "title": "Mansiones en los Árboles",
                    "seasonCount": 11,
                    "episodeCount": 48,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "01d772f0-2749-46d4-9ecc-feb90fa339bd",
                    "published": true,
                    "seasonCount": 11,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030649330000",
                    "title": "Mansión para reptiles",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "f2214a13-1eac-4007-b074-9a7785395485",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029530880000",
                    "title": "Manzana y Cebollín",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "73871fb9-3dc6-481b-ada7-9d501f26b3d0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH002519530000",
                    "title": "Maravillas modernas",
                    "seasonCount": 19,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "fda48733-1daf-4207-97b5-166c85268f2d",
                    "published": true,
                    "seasonCount": 19,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023188650000",
                    "title": "Marcus Level",
                    "seasonCount": 1,
                    "episodeCount": 27,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 15
                },
                "resource": {
                    "id": "1afa8f55-1d04-4fa1-ac1f-f5fc2db12be8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 15
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025290550000",
                    "title": "Mars",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "f91d5b8b-e556-412e-b774-06d0984d2c15",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029530170000",
                    "title": "Marvel's Cloak & Dagger",
                    "seasonCount": 2,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "319378d6-b514-4dfe-8e38-863ec5823e86",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028503760000",
                    "title": "Marvel's Runaways",
                    "seasonCount": 3,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "15ae9609-8986-4553-a7f0-9cb06d575729",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026265140000",
                    "title": "Mary Kills People",
                    "seasonCount": 3,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "608f168a-5369-4596-8b47-6986acc8d798",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032296780000",
                    "title": "Masters de la reforma",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "2c28221f-6b5b-4523-aaad-1fad929948ab",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031543790000",
                    "title": "Matadero",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "5da9d580-1721-445e-a690-059cecb1bca4",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021798810000",
                    "title": "Matrimonio a primera vista",
                    "seasonCount": 9,
                    "episodeCount": 19,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "e25e7031-b91b-4624-97ec-ba96e3ddf92e",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030085840000",
                    "title": "Mayans M.C.",
                    "seasonCount": 2,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 28
                },
                "resource": {
                    "id": "18d42e98-8a45-4f66-adc5-dfe9ee36392c",
                    "published": false,
                    "seasonCount": 2,
                    "episodeCount": 28
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012565010000",
                    "title": "Mayday: Catástrofes aéreas",
                    "seasonCount": 19,
                    "episodeCount": 36,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "20cf2aed-6d1a-48ae-a95a-bde839d14ef6",
                    "published": true,
                    "seasonCount": 19,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030522180000",
                    "title": "Mayday: Informe especial",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "c9ca7b1d-16d2-4fd5-a897-d67dd70de1b5",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024857020000",
                    "title": "Me Chama de Bruna",
                    "seasonCount": 3,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "e0613d9d-858b-43e6-9f26-b937c00f06ea",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026985760000",
                    "title": "Medici",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "dce77aec-e24b-4b3e-9274-ff311d703c2d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018544410000",
                    "title": "Megaestructuras Nazis",
                    "seasonCount": 4,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "d3e27db6-680c-484a-ad36-f906c2e6b998",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031448390000",
                    "title": "Megaestructuras nazis",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "1f25923c-3f22-4923-8a9f-ae6a92042126",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031657190000",
                    "title": "Megaestructuras nazis: Grandes batallas",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "975d64a9-d9ad-42e4-9347-10d874778239",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032208740000",
                    "title": "Megaestructuras: maravillas de la ingeniería",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "85e6e3b4-6bf3-402f-aa1e-ff64491f9be8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031232580000",
                    "title": "Mi casa es la tuya",
                    "seasonCount": 7,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "40e22238-7852-4c14-b4e2-cdb1fcea8720",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015696450000",
                    "title": "Mi gato endemoniado",
                    "seasonCount": 10,
                    "episodeCount": 49,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "9979f141-fc12-4e20-bc9f-ad7366d3f04e",
                    "published": true,
                    "seasonCount": 10,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031393250000",
                    "title": "Mi mitad + hot",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "046a4018-8712-4d67-82b0-4a83a2ea71c1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029674680000",
                    "title": "Mi perro Pat",
                    "seasonCount": 1,
                    "episodeCount": 62,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "cf62dc70-aa2c-48f1-b0c9-c1a965196034",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030884490000",
                    "title": "Michael Palin en Corea del Norte",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "50f9fcea-6ae7-425b-832a-ee4a03556c98",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013857120000",
                    "title": "Mildred Pierce",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "5862a410-7234-4aa3-8d2d-a4d48c74e25c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018140250000",
                    "title": "Mineros del Hielo",
                    "seasonCount": 3,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "7a245b06-8084-449c-a140-efde9a9a55fa",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027331580000",
                    "title": "Mini Beat Power Rockers",
                    "seasonCount": 2,
                    "episodeCount": 72,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "2455c69e-de41-4b76-b482-d6f696ee50e9",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031127120000",
                    "title": "Miracle Workers",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "33decc62-ad31-4377-a4fc-4bd1a29a20d5",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028477420000",
                    "title": "Misión América",
                    "seasonCount": 2,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "f566b3a9-d5d2-4a51-a3a1-cde9c1b5b091",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024889480000",
                    "title": "Misión Conservación",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "3e514335-d8e7-4b1b-bbd9-0395af90efac",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026901010000",
                    "title": "Misión canina",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "901fe761-09a8-45ba-a6b0-8f5f011aa0c0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024720620000",
                    "title": "Miss Moon",
                    "seasonCount": 1,
                    "episodeCount": 52,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 52
                },
                "resource": {
                    "id": "bf9439b8-4711-48a7-90fd-0f714e3f6f50",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 52
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014346070000",
                    "title": "Mitos del Universo",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "79699bb9-d372-4c89-b3b7-256d7c535766",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012201780000",
                    "title": "Modern Family",
                    "seasonCount": 11,
                    "episodeCount": 38,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "7c16305c-8f1c-4174-aa25-ced90f52cbcf",
                    "published": true,
                    "seasonCount": 11,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029190710000",
                    "title": "Monchhichi",
                    "seasonCount": 0,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "ad41cb06-9ada-4392-881c-995c62fd9b66",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027600280000",
                    "title": "Monstruomecánicos",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "02ee4717-f26d-4c5f-9b59-99e9d8812ed9",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023441410000",
                    "title": "Monstruos Reales",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "d072855f-e0e6-4e40-a69b-cd43abaecd9c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032081460000",
                    "title": "Monzón",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "2d915cb4-eda7-4a8b-8492-df5a115ca819",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028253950000",
                    "title": "Mosaic",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "a6e31d77-06f1-4cd3-ac6f-b52f32d0c0ae",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032137390000",
                    "title": "Most Expensivest",
                    "seasonCount": 3,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "93439c3d-8f94-4e7a-951c-dc71201909cd",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031798840000",
                    "title": "Mr. Magoo",
                    "seasonCount": 1,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "54f58386-618e-4c02-9426-f1a7fcf9ac7c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019882070000",
                    "title": "Mr. Pickles",
                    "seasonCount": 3,
                    "episodeCount": 30,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 39
                },
                "resource": {
                    "id": "a673357b-0d7c-48e4-ae99-862be19eaa3a",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 39
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031777390000",
                    "title": "Mrs Wilson",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "c1ee0e17-fc24-42aa-9698-989003130c34",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029335830000",
                    "title": "Muerde, pica, mata",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "495f69ad-b1d4-48be-ae29-e1716fc60a89",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031672070000",
                    "title": "Muerto al amanecer",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "1b4b3830-ef05-48e6-bb7e-a25669a38625",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013903520000",
                    "title": "Mujer de Fases",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "cb19f31a-446e-4f88-9dc8-ce52899dd0c7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013938910000",
                    "title": "Mulher de Fases",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "49905c47-821e-46bd-b95c-70dcf27b412e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025308690000",
                    "title": "My Little Pony",
                    "seasonCount": 9,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "d709ff6e-80ae-4853-9e94-ba8c8eaacae3",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032342580000",
                    "title": "Máquinas increíbles",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "49bb99f5-060d-4021-bebc-38f204ab9b18",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026785010000",
                    "title": "Máxima seguridad: Cárceles extremas",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "09086f72-871c-46b8-9440-57583a6fef61",
                    "published": false,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026042210000",
                    "title": "Médicos milagrosos",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "bba037ce-ad7e-4463-a023-8c8b28558f6d",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024016220000",
                    "title": "NCIS: Los Ángeles",
                    "seasonCount": 11,
                    "episodeCount": 141,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 113
                },
                "resource": {
                    "id": "bcc26bbc-05ca-4005-8b5b-17051996d80e",
                    "published": true,
                    "seasonCount": 11,
                    "episodeCount": 113
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019595360000",
                    "title": "NCIS: New Orleans",
                    "seasonCount": 6,
                    "episodeCount": 21,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "9e121ed5-b32f-48c9-ba97-efcfabbca00f",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023800860000",
                    "title": "NCIS: Nueva Orleáns",
                    "seasonCount": 6,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "0df2ddd4-8e45-42dd-a2e7-5aa962e00257",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032034140000",
                    "title": "NOS4A2",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "7d07af4e-d0de-4cd4-9463-91589ffc147c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031282590000",
                    "title": "Nacidos en África",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "d1c7118d-888a-41fc-acec-3fc8e32a4e05",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029984170000",
                    "title": "Nat Geo Lab",
                    "seasonCount": 1,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "bfe768ef-c136-4755-a9bb-ec43c755088f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027777700000",
                    "title": "National Treasure",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "234074a9-f47e-4c94-91f0-5196eeaf00fa",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027416130000",
                    "title": "Navy Seals: fuerza de combate",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "3cb652fe-f4c8-49f0-bae9-2e7e54b89303",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026514940000",
                    "title": "Nella, una princesa valiente",
                    "seasonCount": 2,
                    "episodeCount": 37,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "56830eb0-de0f-4fc9-a561-b26c4d12d8eb",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026670690000",
                    "title": "Neruda",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "ab7312f5-c0f9-49ef-858f-7a9b277e05fb",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030355720000",
                    "title": "Nikola Tesla: archivos perdidos",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "98547ba9-0d5a-4816-9b9b-ed76d0927f47",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024442050000",
                    "title": "Noisey",
                    "seasonCount": 2,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "b0557ba3-1a53-489d-bac5-58cfe5d4ba3c",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029933830000",
                    "title": "Nuestro hogar en la isla",
                    "seasonCount": 17,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "a29dfc4b-fa2d-456f-99b2-3b587bb1e1d2",
                    "published": true,
                    "seasonCount": 17,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028765670000",
                    "title": "Nuts & Bolts",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "4ee5d511-9d36-4942-8e6f-628b9ef856f0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028112140000",
                    "title": "Oggy y las cucarachas",
                    "seasonCount": 7,
                    "episodeCount": 74,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 66
                },
                "resource": {
                    "id": "6e020a26-8493-4831-9641-5ff81192e744",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 66
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025195780000",
                    "title": "Ojos Sin Culpa",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "39595e1f-db99-41a5-a6f8-466fc654a359",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020104940000",
                    "title": "Olive Kitteridge",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "68ba5985-e02d-4df5-80c5-c0d10670ddc0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027798960000",
                    "title": "Ollie y Moon",
                    "seasonCount": 1,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 31
                },
                "resource": {
                    "id": "ca52f0b0-12a2-457b-8eca-922b22a7d3ae",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 31
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015116310000",
                    "title": "On Freddie Roach",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "dc268a32-7959-489a-8a2c-9d43762ee7ea",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018275070000",
                    "title": "OnCINEMA",
                    "seasonCount": 1,
                    "episodeCount": 30,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 21
                },
                "resource": {
                    "id": "96aebdd9-a301-437b-ab11-72547f2c7a33",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 21
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022377650000",
                    "title": "OnStage",
                    "seasonCount": 0,
                    "episodeCount": 163,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 143
                },
                "resource": {
                    "id": "098f9c4b-2f54-46de-8ee4-aac19be3b779",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 143
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028895990000",
                    "title": "One Strange Rock",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "bfb9ceed-3522-40d7-b7cb-62a79b0afcfb",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031366260000",
                    "title": "Opa Popa Dupa",
                    "seasonCount": 1,
                    "episodeCount": 21,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "8b2907bd-ba3e-4f1f-ae65-242ce0560051",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032349750000",
                    "title": "Opaventuras",
                    "seasonCount": 1,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "4d6d3078-14df-40ac-a1f1-6b7e65a59db7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024293200000",
                    "title": "Orfanato de rinocerontes",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "40fc5b5e-9e91-40dc-a0a1-4dd1ccf5def4",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026242800000",
                    "title": "Otra copa con Jack Maxwell",
                    "seasonCount": 4,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "65d86453-946a-4c4c-9802-7740f6bb11ac",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030382150000",
                    "title": "Otros pecados",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "55a69ae3-379d-4e9e-90b7-cbf62f682cf7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026703280000",
                    "title": "Ouro",
                    "seasonCount": 2,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "da5a4e8d-d272-440a-be30-4cebafcf6b02",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019382240000",
                    "title": "Outlander",
                    "seasonCount": 5,
                    "episodeCount": 55,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 53
                },
                "resource": {
                    "id": "c1a917e0-e65f-4baf-8472-fbfaa31d9954",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 53
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007532220000",
                    "title": "P. Diddy Presents The Bad Boys of Comedy",
                    "seasonCount": 2,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "d2a57470-5583-4a73-b4a8-fa5852731b49",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018844250000",
                    "title": "PSI",
                    "seasonCount": 4,
                    "episodeCount": 41,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 26
                },
                "resource": {
                    "id": "6381ce99-bc2c-418a-855d-b3a919999c1f",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 26
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029574820000",
                    "title": "Pablo",
                    "seasonCount": 1,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "6b761372-efe9-402b-843f-14c985ecfaa2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH003367240000",
                    "title": "Padre de familia",
                    "seasonCount": 18,
                    "episodeCount": 81,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "47ac5e52-e9b5-4358-ab84-4e796f125fef",
                    "published": true,
                    "seasonCount": 18,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019777560000",
                    "title": "Palabra de Ladrón",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "780957d3-c82c-4bce-b444-411f3467ba1a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031312380000",
                    "title": "Paraíso ahumado",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "8a3eb0a7-154e-41df-93e9-009a0a91ce33",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018690660000",
                    "title": "Parientes Perversos",
                    "seasonCount": 4,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "0873db51-51ca-41d7-a32a-6b47110d6a1b",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032351510000",
                    "title": "Parques nacionales",
                    "seasonCount": 3,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "3f5245a2-65d4-41bf-9971-859df64805b0",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028034000000",
                    "title": "Pasarela 24hs",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "8169ec6a-0e08-4fb1-a774-0598a661497d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029368480000",
                    "title": "Patrick Melrose",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "8b87fb1a-2a0a-4827-a8d6-2a51a8ef755b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018503700000",
                    "title": "Patrulla de cachorros",
                    "seasonCount": 6,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 26
                },
                "resource": {
                    "id": "1491a1fe-5f43-45d8-b44e-ad445462f6d9",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 26
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027720090000",
                    "title": "Paul Hollywood: un panadero en la ciudad",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "d3a4e7e4-8df8-46f2-976d-8ca86487c35d",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029143680000",
                    "title": "Paula",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "da4288d1-a442-4851-8f32-5844201f403e",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024651200000",
                    "title": "Peace 'n' Pop",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "43fe5734-6a9a-4358-8c76-c58208429592",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025008350000",
                    "title": "Pecado Original",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "6de9643e-b1ec-4205-8a52-60e509bf31ec",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015779970000",
                    "title": "Pecados mortales",
                    "seasonCount": 6,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "2d347822-a34e-411c-b8b4-d41067d3ae0a",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030281700000",
                    "title": "Peces en la ciudad",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "a76c1ba5-2aa1-4b1d-b675-a63d1c80ee29",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031831090000",
                    "title": "Peces legendarios",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "1be5de42-25d4-429f-90a2-4b676d736a39",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012665670000",
                    "title": "Peces monstruosos",
                    "seasonCount": 7,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "2f3b3663-e41b-466f-bba8-527de71983ab",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029813940000",
                    "title": "Peligros de la naturaleza",
                    "seasonCount": 7,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "d3febdb0-10ce-4c4b-ad12-dcdcd73200c7",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017240460000",
                    "title": "Peppa",
                    "seasonCount": 7,
                    "episodeCount": 153,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "1c798b20-47ef-4a00-bd37-f2a2c412d286",
                    "published": false,
                    "seasonCount": 7,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024239000000",
                    "title": "Pequeñas Grandes Mujeres Atlanta",
                    "seasonCount": 5,
                    "episodeCount": 28,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "4b12dc69-f012-404e-911f-12e5e428c497",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020234500000",
                    "title": "Pequeñas grandes mujeres",
                    "seasonCount": 8,
                    "episodeCount": 43,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "421a98ff-9d6e-4800-bc3e-aea39be953aa",
                    "published": false,
                    "seasonCount": 8,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026243130000",
                    "title": "Pequeños reposteros",
                    "seasonCount": 7,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "86ad1232-06a3-46b0-8829-8a62b30123cd",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031581560000",
                    "title": "Perdidos en Oz",
                    "seasonCount": 1,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "f1ad79da-3b8f-471c-ac68-95551b5f3081",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028822540000",
                    "title": "Perdóname, Señor",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "c9b2d170-747e-4b9a-a9ff-925693e86f6e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025068590000",
                    "title": "Pesca Mortal",
                    "seasonCount": 15,
                    "episodeCount": 38,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "3010f8b4-6174-42ab-a26f-747b003281b2",
                    "published": true,
                    "seasonCount": 15,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015866300000",
                    "title": "Pesca pesada",
                    "seasonCount": 8,
                    "episodeCount": 28,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "34d3ecb8-5290-4906-9fa1-d08390a1b0fe",
                    "published": true,
                    "seasonCount": 8,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029828810000",
                    "title": "Phenoms: Road to Russia",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "2c5532c7-ecc6-46a7-8157-f6ea6a23cda7",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027586730000",
                    "title": "Photo Ark, especies en peligro",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "0b037bf7-0250-4cc6-80a0-455a3cd0aa3f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030513700000",
                    "title": "Picnic at Hanging Rock",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "4d7808e6-1480-4a18-89e0-8b3d595eded2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030929820000",
                    "title": "Pioneros de Polonia",
                    "seasonCount": 3,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "06bf1392-65ac-422e-bf4e-a10f57cbac58",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013827690000",
                    "title": "Pit Bulls y Convictos",
                    "seasonCount": 10,
                    "episodeCount": 34,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "5d501139-691d-4b32-87f0-267f6d07d3c6",
                    "published": true,
                    "seasonCount": 10,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031830810000",
                    "title": "Planeta hostil",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "9ec95988-dc7b-4205-9b5a-32b3d3975e75",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029927480000",
                    "title": "Pokémon",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "c675101d-681d-4f00-83cb-a3a445345034",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030590580000",
                    "title": "Pokémon",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "032db518-9447-444a-9632-c0190477fb42",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027027230000",
                    "title": "Pokémon: sol y luna",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "bba079b4-c0e0-4885-bb24-6c8206393633",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028713620000",
                    "title": "Policías en vivo: Live PD",
                    "seasonCount": 4,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "ebc1f043-46f6-416b-af93-d03a55d03670",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030655560000",
                    "title": "Polly Pocket",
                    "seasonCount": 1,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "5d887948-822e-48a5-9ac0-2758eb9e8554",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029075940000",
                    "title": "Pope: The Most Powerful Man in History",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "b96c0d01-01aa-48eb-82dc-a7d6a5418fb0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020779170000",
                    "title": "Portales Hacia la Muerte",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "7233e12d-91f6-47ba-9334-d85eead5e84d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029337300000",
                    "title": "Pose",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 15
                },
                "resource": {
                    "id": "3f63fdc1-4ec0-4b15-b084-9a8b550d08f9",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 15
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019051030000",
                    "title": "Power",
                    "seasonCount": 6,
                    "episodeCount": 52,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 86
                },
                "resource": {
                    "id": "8ad06ef5-5c49-4522-b1a5-1c26551ddbe8",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 86
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024821220000",
                    "title": "Premier Champions Series Boxing",
                    "seasonCount": 0,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "9cb7aac5-cd63-4916-8c5f-d7af348281dc",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032330370000",
                    "title": "Presidentes: decisiones de guerra",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "eebcbf2b-d0b7-4d0a-b33b-e28cb6ffaf93",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013461240000",
                    "title": "Preso en el extranjero",
                    "seasonCount": 11,
                    "episodeCount": 39,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "c05167f5-d982-40ae-9417-66a2fe6f563d",
                    "published": true,
                    "seasonCount": 11,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032224950000",
                    "title": "Primos para siempre",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "d18e63e0-06f6-48e3-a8fe-5d08196913a9",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027488110000",
                    "title": "Private Eyes",
                    "seasonCount": 3,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "b5468b46-1697-4596-961f-398b1d67fcd4",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH005206490000",
                    "title": "Project Greenlight",
                    "seasonCount": 4,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "3085ca35-861d-4160-9f12-801bff2a089b",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022877720000",
                    "title": "Project Runway: Junior",
                    "seasonCount": 2,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "91ea0ca0-eebf-4770-9aef-12eb4d617419",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014424050000",
                    "title": "Prófugos",
                    "seasonCount": 2,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 49
                },
                "resource": {
                    "id": "470c4c56-b66e-471e-9909-5307cb933ab3",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 49
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023212220000",
                    "title": "Puerto Papel",
                    "seasonCount": 3,
                    "episodeCount": 19,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "a269ef45-9363-40db-9e77-fe9a6df5505c",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031852520000",
                    "title": "Pupparazzi",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "79c481a8-601c-4819-bae0-e588e51ac971",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026916690000",
                    "title": "Rare -- Creatures of the Photo Ark",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "f29c09cf-7b34-4f33-a8de-fea954b2544b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032140930000",
                    "title": "Rastreando el pasado - explorando lo desconocido",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "e2ea2b57-9d73-4b8f-b33c-0e9e55170c43",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023306570000",
                    "title": "Ready Jet Go!",
                    "seasonCount": 2,
                    "episodeCount": 87,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 69
                },
                "resource": {
                    "id": "de121305-d347-4ac3-ad79-101aac320d7a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 69
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH006876770000",
                    "title": "Real Time With Bill Maher",
                    "seasonCount": 17,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 32
                },
                "resource": {
                    "id": "f750b61d-cdaa-4a6d-8a5a-e49dc191adf2",
                    "published": true,
                    "seasonCount": 17,
                    "episodeCount": 32
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH011556060000",
                    "title": "Recetas de familia",
                    "seasonCount": 4,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "2e9483d0-0a2a-4f81-9d58-a291aa71d99b",
                    "published": false,
                    "seasonCount": 4,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026243660000",
                    "title": "Recetas en 30 Minutos",
                    "seasonCount": 29,
                    "episodeCount": 42,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "d283de96-615c-467f-a7f3-2a12ae0bb785",
                    "published": true,
                    "seasonCount": 29,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019523520000",
                    "title": "Red de Mentiras",
                    "seasonCount": 6,
                    "episodeCount": 29,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "1ebd42ce-c7ec-42a0-83be-be29b69ed358",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031672550000",
                    "title": "Redecora con tus manos",
                    "seasonCount": 1,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "096dbb82-a6c9-4613-84bb-4c6b06c030de",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019026290000",
                    "title": "Reinas Caídas",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "498f45b2-a22b-4ed0-b619-11edc4970178",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029935450000",
                    "title": "Reino Animal - Nat Geo Kids",
                    "seasonCount": 1,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 24
                },
                "resource": {
                    "id": "06c5254b-0ba3-413e-84e3-72d089ba19a0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 24
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029007890000",
                    "title": "Rellik",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "28c406f3-98da-4c02-982a-8ad6c147a4e3",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031559960000",
                    "title": "Renovando mi ciudad",
                    "seasonCount": 3,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "5db9ef7b-d78d-47fa-a8a9-af5e3306f140",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026244310000",
                    "title": "Rescata mi Restaurante",
                    "seasonCount": 15,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "1bac5689-bb61-4b8e-b2e3-abdd48c62c94",
                    "published": true,
                    "seasonCount": 15,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029668770000",
                    "title": "Rescatando propiedades",
                    "seasonCount": 9,
                    "episodeCount": 27,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "a43275bf-17fc-4ba6-965f-b44c1072b120",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031428170000",
                    "title": "Resistiré",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "6ed5c63e-5983-4fa0-a4c0-1d01be640a6f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032179330000",
                    "title": "Resistiré: El rincón sin censura",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "3deede6a-3c89-4a7f-acf2-7e7e834f9a49",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014865320000",
                    "title": "Ridiculousness",
                    "seasonCount": 13,
                    "episodeCount": 36,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "16a2a4f5-29aa-4cb1-8415-be05e078208a",
                    "published": true,
                    "seasonCount": 13,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028635850000",
                    "title": "Rio Heroes",
                    "seasonCount": 2,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "f9b03ae8-1d38-4d07-aa33-afb25b603e0a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030068790000",
                    "title": "Rise of the Teenage Mutant Ninja Turtles",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "c15eace9-15f4-4c37-8b04-dc60fddefe28",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027320770000",
                    "title": "Riviera",
                    "seasonCount": 2,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "653fdb1b-4ecb-4567-83f9-231cb7682fc9",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027259560000",
                    "title": "Robin Hood",
                    "seasonCount": 2,
                    "episodeCount": 61,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "4a592a68-17be-4a37-a744-a1a2ed85e8a6",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030138740000",
                    "title": "Robin Hood, travesuras en Sherwood",
                    "seasonCount": 2,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "c54b9a77-999f-44ce-bc37-94f2617b4ff4",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007894960000",
                    "title": "Roma",
                    "seasonCount": 2,
                    "episodeCount": 28,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "3d71c817-5b3c-4e53-a008-0beb528ec26c",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017156170000",
                    "title": "Roma: Auge y Caída",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "b063947a-eeec-4fee-bfc9-c6f7332aa9ac",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007641880000",
                    "title": "Rome",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "ee928584-5c71-43f1-b01f-c5add361d5f2",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027018710000",
                    "title": "Room 104",
                    "seasonCount": 3,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 26
                },
                "resource": {
                    "id": "83ed2323-befc-445d-adef-2c798809ccad",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 26
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020178140000",
                    "title": "Roommates",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "f4930cd8-e464-45ec-b038-6dc3f472a1af",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026609650000",
                    "title": "Rosario Tijeras",
                    "seasonCount": 2,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "b88291bd-d3c3-4e09-a4ea-e1c574fbb8c7",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031083380000",
                    "title": "Rubirosa",
                    "seasonCount": 1,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "23bb4064-2ed3-45bc-b21d-5a9cb0e244e8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026703780000",
                    "title": "Run Coyote Run",
                    "seasonCount": 2,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "18bb57cf-4d36-4fee-a6cf-f5f83f82286e",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024544540000",
                    "title": "Rusty Rivets",
                    "seasonCount": 3,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "63aaa36f-2ff6-4543-8073-c9d7ab7bf7eb",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019042240000",
                    "title": "Rutas Mortales",
                    "seasonCount": 11,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "2e63407f-7244-4ac2-b9cc-244d8b9ad4f9",
                    "published": true,
                    "seasonCount": 11,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027590240000",
                    "title": "S.W.A.T.",
                    "seasonCount": 3,
                    "episodeCount": 41,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 46
                },
                "resource": {
                    "id": "1306628c-9710-4fe9-a3ba-c6d45f7c840a",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 46
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027382450000",
                    "title": "SEAL Team",
                    "seasonCount": 3,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "aff288f5-6207-4956-bada-494054af5a82",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032147390000",
                    "title": "Safari Live: The Gauntlet",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "242de735-5a98-4d47-af9d-f476cfc779fe",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030413230000",
                    "title": "Sally4Ever",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "c1f667a5-5829-436f-8b7b-49d097ca7b3a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016397220000",
                    "title": "Salvados",
                    "seasonCount": 10,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "c8a5a720-b79c-48f2-aef4-0b9353af9b5d",
                    "published": false,
                    "seasonCount": 10,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024009630000",
                    "title": "Salvando Mi Mañana",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "0171f75d-f7c1-4005-b748-9e19ceaba3e2",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022932450000",
                    "title": "Sam y Cat",
                    "seasonCount": 1,
                    "episodeCount": 35,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 35
                },
                "resource": {
                    "id": "59131594-3bdf-446d-81a4-fb3086493ec9",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 35
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030667550000",
                    "title": "Save Me",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "68b7f045-f60b-478f-b9a6-fe0c654b6b24",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023742230000",
                    "title": "School of Rock",
                    "seasonCount": 3,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "a82d4099-9196-48f8-a349-830d89dd5260",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015302820000",
                    "title": "Schoolbreak",
                    "seasonCount": 14,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "ca4cf6c9-e6e2-4b7f-835a-e78cd33bcfd9",
                    "published": true,
                    "seasonCount": 14,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029973160000",
                    "title": "Scoop",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "10ba2fa8-ac58-42bb-9833-5df6b226fa4d",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025216220000",
                    "title": "Search Party",
                    "seasonCount": 2,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "68e8121f-b201-4fdf-a921-0fb9e8aeeb27",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030085530000",
                    "title": "Secreto en los océanos",
                    "seasonCount": 2,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "c6c9d68d-e108-4c3c-a27c-493baba65ce5",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027476800000",
                    "title": "Secretos bajo tierra",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "0e7364ac-5efb-438d-bbed-3b114df71369",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017859400000",
                    "title": "Secretos de Estado",
                    "seasonCount": 3,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "af6f09cb-9c60-44fa-a891-45da600033d8",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031748610000",
                    "title": "Secretos de los mayas",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "c4d45e45-8d0b-4274-be57-59962e87ba16",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020863290000",
                    "title": "Secuestrados",
                    "seasonCount": 3,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "96f41f01-aefb-43ee-887e-a5d4bb41d465",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026774630000",
                    "title": "Segunda Guerra: Infierno submarino",
                    "seasonCount": 2,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "a2d703d4-97f7-4c2e-8d12-513a67800b8a",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH006170790000",
                    "title": "Sexo Urbano",
                    "seasonCount": 2,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "f421e9a1-e5a6-4bbf-8b56-d2570e0e9ca3",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012255470000",
                    "title": "Shark Tank",
                    "seasonCount": 11,
                    "episodeCount": 48,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "dc856955-1410-45c4-b2c4-ec5dcd49fa5c",
                    "published": true,
                    "seasonCount": 11,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024405290000",
                    "title": "Shark Tank México",
                    "seasonCount": 4,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "1a72c420-c716-4a76-8774-2f463d611d74",
                    "published": false,
                    "seasonCount": 4,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029702170000",
                    "title": "Sharp Objects",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "4185f355-75fd-4ddf-9b72-894fac794647",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028306690000",
                    "title": "Shimmer y Shine",
                    "seasonCount": 4,
                    "episodeCount": 46,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "4fb9fb1f-5742-4223-8193-04f5b8901a16",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH022167110000",
                    "title": "Show Me a Hero",
                    "seasonCount": 1,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "b4b38c0f-eaac-4b88-9a39-2ee3f5e30e6d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028218530000",
                    "title": "Shut Eye",
                    "seasonCount": 2,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "6d8cea4a-4fdf-4878-94b2-01fba0a0b02c",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027402010000",
                    "title": "Siesta Key",
                    "seasonCount": 2,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "a0d85d6e-b1f7-4c6c-af86-3f6ff778e1bc",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018833420000",
                    "title": "Silicon Valley",
                    "seasonCount": 6,
                    "episodeCount": 46,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 47
                },
                "resource": {
                    "id": "72003f41-f3ab-4135-9751-2314fa1ac629",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 47
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019126080000",
                    "title": "Sin identidad",
                    "seasonCount": 2,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 15
                },
                "resource": {
                    "id": "901a1992-2318-47cf-8679-5fcdc52a98b6",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 15
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028793330000",
                    "title": "Siren",
                    "seasonCount": 2,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "122c0880-6f79-44d8-bf35-5cd6f4b5045c",
                    "published": false,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019802790000",
                    "title": "Sitiados",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "b9099f57-4fcc-427d-9512-c74741cdb728",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH004928120000",
                    "title": "Six Feet Under",
                    "seasonCount": 5,
                    "episodeCount": 63,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 69
                },
                "resource": {
                    "id": "4b623034-15f4-446c-b914-9c00216aa0f1",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 69
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023226420000",
                    "title": "Solo Contra el Mundo",
                    "seasonCount": 4,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "7c93d50e-a332-475e-89ea-23fd46662fbb",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025010620000",
                    "title": "Spawn",
                    "seasonCount": 3,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "c8cc86b3-775a-4736-b014-7d953ac537cb",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027262710000",
                    "title": "Splash y Bubbles",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "ccb00587-91f7-4cb7-8044-540d004afb6e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027482270000",
                    "title": "Spying on the Royals",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "68f93df1-2f7a-4710-afb0-620cb410fb70",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017194730000",
                    "title": "Sr. Ávila",
                    "seasonCount": 4,
                    "episodeCount": 56,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 41
                },
                "resource": {
                    "id": "31e0e77c-2426-450b-be66-af0d8b6c7a64",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 41
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030473040000",
                    "title": "Stan Against Evil",
                    "seasonCount": 3,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "a92b5e02-985f-43b6-a269-6fa8bdb8e4aa",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017902400000",
                    "title": "Stand Up Sin Fronteras",
                    "seasonCount": 0,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "254ca35c-0f9b-4c67-8f9f-63fcd17ed507",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029162460000",
                    "title": "Star Falls",
                    "seasonCount": 1,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "3d615d1b-fd78-4492-9ef2-a396cff60d9a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031796920000",
                    "title": "Strangers",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "c733dd00-2cce-4a25-85a8-6ff40d945047",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029440330000",
                    "title": "Succession",
                    "seasonCount": 2,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "f1d31a56-d536-4d0b-b747-ebfed687b00d",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025741310000",
                    "title": "Summer House",
                    "seasonCount": 3,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "a531472d-fb4d-407e-82ac-9c3d8b1b0dd1",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027232480000",
                    "title": "Sunny Day",
                    "seasonCount": 2,
                    "episodeCount": 21,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 18
                },
                "resource": {
                    "id": "b8219a41-1f28-4951-90f3-193c51c331b6",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 18
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023586750000",
                    "title": "Super Shore",
                    "seasonCount": 3,
                    "episodeCount": 43,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 37
                },
                "resource": {
                    "id": "7d70dc4d-185e-4f00-bd6e-5ead9fc62e0b",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 37
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024173630000",
                    "title": "Supervivencia al Desnudo: Edición Extrema",
                    "seasonCount": 5,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "d286fbef-2636-452e-8bac-7500819d096b",
                    "published": false,
                    "seasonCount": 5,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019733620000",
                    "title": "Survivor's Remorse",
                    "seasonCount": 4,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "cdc8df0d-5735-4961-bf3d-feeded51eabf",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027038060000",
                    "title": "Sé quién eres",
                    "seasonCount": 1,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "ff06e17f-733f-4aed-a31d-e5c1d9329519",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025576470000",
                    "title": "Taboo",
                    "seasonCount": 1,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "158e8a42-99cc-48cd-9a08-60a6bbdfbf44",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030249890000",
                    "title": "Talento Fox",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "ffaae402-d446-4001-8faf-4c52d1548f62",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014791120000",
                    "title": "Talking Dead",
                    "seasonCount": 9,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "3a637c37-ecf2-4f95-8664-d43db898bba7",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028766150000",
                    "title": "Tattoo Age",
                    "seasonCount": 2,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "cde222ea-7ddc-496b-a147-052f015710dc",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023392900000",
                    "title": "Teachers",
                    "seasonCount": 3,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "998e3da7-d2db-4637-aeec-1c2593e4bf59",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032237660000",
                    "title": "Ted Bundy: Serial Monster",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "cd502d3e-b50f-4b57-bdd8-75f52b81a614",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013881970000",
                    "title": "Teen Mom 2",
                    "seasonCount": 9,
                    "episodeCount": 21,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "c3ccc56f-5127-4c9c-b2dc-09101f50eb82",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024045100000",
                    "title": "Teen Mom OG",
                    "seasonCount": 4,
                    "episodeCount": 23,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "c4b1da3d-d5d5-43a4-b6f3-4e3d041f1efc",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015495980000",
                    "title": "Terapia de Shock",
                    "seasonCount": 9,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "ad61975b-de73-41a4-86e1-0de8b63f7272",
                    "published": true,
                    "seasonCount": 9,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032315570000",
                    "title": "Territorio depredador",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "d53dc733-3c18-43ba-ae35-4b0000e6f381",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030993950000",
                    "title": "Tesoro del garaje",
                    "seasonCount": 6,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 15
                },
                "resource": {
                    "id": "f837db5b-9df6-4969-afa0-3f4c0d5ebd2d",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 15
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031383300000",
                    "title": "Tesoros perdidos de Egipto",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "4a6b1d03-e61f-4d5e-a6c5-1b29e93e5191",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018599970000",
                    "title": "The 100",
                    "seasonCount": 6,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "6697afe5-a708-42f6-8362-238995a893fa",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031266230000",
                    "title": "The Bi Life",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "2dbec507-5176-48e9-9dc2-589bda7a8bd6",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH000274040000",
                    "title": "The Big Bang Theory",
                    "seasonCount": 12,
                    "episodeCount": 95,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "f65164c8-3197-4024-a216-6ec26b5a78c5",
                    "published": false,
                    "seasonCount": 12,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031642170000",
                    "title": "The Bisexual",
                    "seasonCount": 1,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "ad7f4995-e4ae-409d-8c3c-9a4b70d3162b",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017686570000",
                    "title": "The Blacklist",
                    "seasonCount": 7,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 14
                },
                "resource": {
                    "id": "21c05763-ff10-44d3-83c3-c301677e3e5e",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 14
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018991230000",
                    "title": "The Bridge",
                    "seasonCount": 4,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "0906f080-b516-4094-969c-18f19d32fe2b",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021729400000",
                    "title": "The Brink",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "09b2fa4e-c5a9-4e75-a824-89b971d7ad7c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031608620000",
                    "title": "The Case Against Adnan Syed",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "350edde5-276f-4ffd-8579-29f1b4588118",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026101370000",
                    "title": "The Challenge",
                    "seasonCount": 6,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "4913c9d6-05d9-44da-ab60-fa8123e85884",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030711330000",
                    "title": "The Clinton Affair",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "58dde70b-46cd-454b-850b-925de8a3b4e8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH007472850000",
                    "title": "The Comeback",
                    "seasonCount": 2,
                    "episodeCount": 21,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 27
                },
                "resource": {
                    "id": "b813165d-941d-4f7c-b895-da23c4af7465",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 27
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031571260000",
                    "title": "The Cry",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "3423dffd-f865-4d10-97ef-ba702bdb9ae0",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027353090000",
                    "title": "The Deuce",
                    "seasonCount": 3,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "6fa8698b-050a-44f4-b48e-76a2c612bc0c",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025669930000",
                    "title": "The Durrells",
                    "seasonCount": 4,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "761771ab-4597-4499-ab38-5b3ad85e1617",
                    "published": false,
                    "seasonCount": 4,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031267740000",
                    "title": "The Enemy Within",
                    "seasonCount": 1,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 22
                },
                "resource": {
                    "id": "489bb028-23b0-4f39-82ca-1020a49777b1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 22
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031363920000",
                    "title": "The Facebook Dilemma",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "839c8d4e-1366-4477-97a2-140c33350892",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031367730000",
                    "title": "The Fix",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "4e6a823c-479a-4e81-a195-d351bf462b4c",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027387090000",
                    "title": "The Gifted",
                    "seasonCount": 2,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "4291f357-b3ea-4252-9e42-b77d12ac5388",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023670280000",
                    "title": "The Girlfriend Experience",
                    "seasonCount": 2,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "eb7a02df-118a-4c62-98fb-57059ad341c7",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026406820000",
                    "title": "The Halcyon",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "2f50be4a-d415-4a17-ad37-638f31210bf9",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029128770000",
                    "title": "The Handmaid's Tale",
                    "seasonCount": 3,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "7e5ec818-1b75-4ce5-b718-43a25995a2b1",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031929660000",
                    "title": "The Hot Zone",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "088b2398-eb7d-43b6-a446-fb2b8c2b974d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023298520000",
                    "title": "The Jungle Bunch",
                    "seasonCount": 2,
                    "episodeCount": 86,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 34
                },
                "resource": {
                    "id": "033e135e-55ef-4678-9d99-7849dd174a92",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 34
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029320020000",
                    "title": "The Kennedys: After Camelot",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "50f4a0e6-ac39-4777-95bb-53a34a32737f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019377630000",
                    "title": "The Knick",
                    "seasonCount": 2,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "3ac1c403-2ebf-448c-9b2d-715180616ead",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027965650000",
                    "title": "The Long Road Home",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "e1b74fac-0cb4-48e9-856a-186899df1f12",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029849750000",
                    "title": "The Miniaturist",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "4e64d283-6f3b-4098-b29f-d64746e287e1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031964800000",
                    "title": "The Miracle",
                    "seasonCount": 1,
                    "episodeCount": 7,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "4ade50e8-f9a8-4f37-a894-ff03bc0a1667",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015619210000",
                    "title": "The Newsroom",
                    "seasonCount": 3,
                    "episodeCount": 25,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 27
                },
                "resource": {
                    "id": "a8512c95-3a58-43a8-afc8-b9d639859284",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 27
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024279930000",
                    "title": "The Night Of",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "21a8e04d-cee5-4db3-997a-03ecd2ae7d0c",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031075040000",
                    "title": "The Owl & Co",
                    "seasonCount": 2,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "95567898-e64a-4842-b05c-dd81110a14b3",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012380840000",
                    "title": "The Pacific",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "96874add-d70c-4397-99a3-7a502a4b1cea",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016920410000",
                    "title": "The Passion",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "297aa9cc-dc18-46a0-8cf9-48f2d74bf16f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028778900000",
                    "title": "The Radical Story of Patty Hearst",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "e9ef6b9c-5559-4f49-955e-903932387979",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028275600000",
                    "title": "The Resident",
                    "seasonCount": 3,
                    "episodeCount": 42,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 23
                },
                "resource": {
                    "id": "29e7f2ec-99a4-4ab0-a5e2-0244f1135dd0",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 23
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030084920000",
                    "title": "The Royal Wives of Windsor",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "f852a75b-fe0b-4e48-88ad-e7194db27a2b",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030940940000",
                    "title": "The Royal World",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "70ccc2fc-b448-4060-9452-094b485cb855",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028101560000",
                    "title": "The Secret Agent",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "9659bc6f-11bc-4294-acb9-ce5e5e05c91a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030193800000",
                    "title": "The Shop",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "efe4af3c-18ce-4cab-b40c-d4a8eb9618e1",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032260980000",
                    "title": "The Shop: Uninterrupted",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "db6afc9c-1c0c-4401-831b-23db08b5dc09",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026285450000",
                    "title": "The Son",
                    "seasonCount": 2,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "a53b887f-411b-44ff-9017-d82c5b484ebf",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027576250000",
                    "title": "The State",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "9a5e25a6-b692-47f9-90d8-f1b5a23be117",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028764500000",
                    "title": "The Story of Us con Morgan Freeman",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "77b36f8e-61df-45a4-b016-ed105b619e47",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018076480000",
                    "title": "The Thundermans",
                    "seasonCount": 4,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 29
                },
                "resource": {
                    "id": "bdbff3a1-2d3b-4771-ae08-e873f7540abc",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 29
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013921620000",
                    "title": "The Voice",
                    "seasonCount": 17,
                    "episodeCount": 139,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 60
                },
                "resource": {
                    "id": "2d25302d-39d9-4bae-b3c1-660014313127",
                    "published": true,
                    "seasonCount": 17,
                    "episodeCount": 60
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013359690000",
                    "title": "The Walking Dead",
                    "seasonCount": 10,
                    "episodeCount": 141,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 167
                },
                "resource": {
                    "id": "f7ffbf81-22ea-4374-8503-1ba6dae00ebc",
                    "published": true,
                    "seasonCount": 10,
                    "episodeCount": 167
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026254420000",
                    "title": "The White Princess",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "ba2c2046-dd40-4d42-bd72-ff5e60224629",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017593660000",
                    "title": "The White Queen",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "7af312c0-5ebc-42bf-95c4-0c183d9c6c48",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH005099320000",
                    "title": "The Wire",
                    "seasonCount": 5,
                    "episodeCount": 60,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 99
                },
                "resource": {
                    "id": "a4b407b2-9cc8-4c94-8465-fdf2ccb89301",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 99
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025577620000",
                    "title": "The Young Pope",
                    "seasonCount": 1,
                    "episodeCount": 11,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "92b890d8-3276-4ef5-abb7-effad78b9b48",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024707740000",
                    "title": "This Is Us",
                    "seasonCount": 4,
                    "episodeCount": 55,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 45
                },
                "resource": {
                    "id": "0eff2372-305f-40db-adc8-aaf55f3b5635",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 45
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023707400000",
                    "title": "Those Who Can't",
                    "seasonCount": 3,
                    "episodeCount": 38,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 19
                },
                "resource": {
                    "id": "344db36a-d548-4fad-859b-97dce3783a0e",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 19
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013452760000",
                    "title": "Tiempo final",
                    "seasonCount": 3,
                    "episodeCount": 54,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 51
                },
                "resource": {
                    "id": "98becf24-c00e-420c-91b2-6bcaba65c9ea",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 51
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026243850000",
                    "title": "Tiffani te Invita",
                    "seasonCount": 3,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "c8b69e35-ceb1-4533-8dc0-a3712cfbaec8",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029388970000",
                    "title": "Tin Star",
                    "seasonCount": 2,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "d880beb3-1f74-4ef2-a134-27f616e51408",
                    "published": false,
                    "seasonCount": 2,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH013367370000",
                    "title": "Titán Sim-Biónico",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "1c13da99-ae74-4962-b310-cf8a28d769a3",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH019967920000",
                    "title": "Todo en 90 Días",
                    "seasonCount": 6,
                    "episodeCount": 28,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "fc9c2da1-5e1d-4360-8499-f5595c4c7eaa",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029885840000",
                    "title": "Todo por el juego",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "4f9b3d93-257e-4025-8697-73233dcea033",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020612150000",
                    "title": "Togetherness",
                    "seasonCount": 2,
                    "episodeCount": 16,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 17
                },
                "resource": {
                    "id": "9e87867e-5206-4d2e-afd1-206ec1cde790",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 17
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032739980000",
                    "title": "Top 10: Espacios eficientes",
                    "seasonCount": 0,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "e807246d-22c5-4066-a558-ff5fd53644d6",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028004280000",
                    "title": "Top Wing",
                    "seasonCount": 2,
                    "episodeCount": 22,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 10
                },
                "resource": {
                    "id": "b30b70f3-efbe-47d6-b2ce-db29a14a57a6",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 10
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030830990000",
                    "title": "Transbordador: triunfo y tragedia",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "c46591f9-15d1-4c0a-b08e-fcdb08bf581f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026870530000",
                    "title": "Tras la pista del oro",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "53c5670c-7bfd-46b6-a2c5-80b241631f68",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029849830000",
                    "title": "Trauma",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "1f415d4b-7480-4d46-8434-6347a2f0280f",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012459850000",
                    "title": "Treme",
                    "seasonCount": 4,
                    "episodeCount": 36,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 43
                },
                "resource": {
                    "id": "7a8937cc-a068-4a23-8283-6abae2a775d6",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 43
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023414390000",
                    "title": "Trucktown",
                    "seasonCount": 2,
                    "episodeCount": 39,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 39
                },
                "resource": {
                    "id": "c6691608-03a0-417d-be45-4498c25cb9b1",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 39
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH010773990000",
                    "title": "True Blood",
                    "seasonCount": 7,
                    "episodeCount": 81,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 115
                },
                "resource": {
                    "id": "eae59211-1b14-4f87-91f0-5f696a2ba64c",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 115
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH018323770000",
                    "title": "True Detective",
                    "seasonCount": 3,
                    "episodeCount": 24,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 32
                },
                "resource": {
                    "id": "5da44639-d975-4655-a735-598bc875619e",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 32
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029324560000",
                    "title": "Trust Me",
                    "seasonCount": 2,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "7b3783c4-a66a-49fb-8346-c2d45d3e67e4",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015295600000",
                    "title": "Tsunami, the Aftermath",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "ab675a26-f915-45f3-867e-55d17b34112a",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028101480000",
                    "title": "Tutankhamun",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "0fd0f985-ec79-4b90-8ce1-8c5f4af51f84",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026487270000",
                    "title": "Tía Mowry en Casa",
                    "seasonCount": 3,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "c36f0928-8bcf-4365-b1ff-7b9f7e182d15",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024784150000",
                    "title": "Um Contra Todos",
                    "seasonCount": 3,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "dc5510c5-f53f-4839-bc24-9cbbef261d0f",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014728600000",
                    "title": "Un año para recordar",
                    "seasonCount": 1,
                    "episodeCount": 91,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 91
                },
                "resource": {
                    "id": "e55819a4-0d81-46ca-8dd9-e58817fb69fb",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 91
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027134270000",
                    "title": "Un gallo para Esculapio",
                    "seasonCount": 2,
                    "episodeCount": 15,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 15
                },
                "resource": {
                    "id": "ab6fd4c1-6446-4edb-bf72-ec0ab71531cc",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 15
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH000224110000",
                    "title": "Un gran mundo pequeño",
                    "seasonCount": 19,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "8891ec4a-1c0a-4fee-9d60-6baf3ab10dd8",
                    "published": true,
                    "seasonCount": 19,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH026288150000",
                    "title": "Un nuevo look para una nueva vida",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "a77c78b1-8968-48dd-827c-e22fa147e434",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021802640000",
                    "title": "UnREAL",
                    "seasonCount": 4,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "ee90c4fd-9bcb-4d83-adbd-9770a80eae65",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028061610000",
                    "title": "Unikitty",
                    "seasonCount": 2,
                    "episodeCount": 31,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "e4db3530-f70f-492e-ae86-0d30c8702a0c",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031379140000",
                    "title": "United Kingdom of Pop",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "ec5acafe-5f31-4185-8be5-64e3b73835b4",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017024710000",
                    "title": "VICE",
                    "seasonCount": 6,
                    "episodeCount": 113,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 147
                },
                "resource": {
                    "id": "24bfe823-c317-4de7-b4ab-9072097c21ce",
                    "published": true,
                    "seasonCount": 6,
                    "episodeCount": 147
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031168840000",
                    "title": "Valley of the Boom",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "81dfc667-e6d6-4e8f-a57c-d3a1d78ee466",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023237630000",
                    "title": "Vanity Fair Confidential",
                    "seasonCount": 4,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 9
                },
                "resource": {
                    "id": "beed9baa-86a5-4c83-a72a-3e6dd07dfd8c",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 9
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015769430000",
                    "title": "Vecino Asesino",
                    "seasonCount": 10,
                    "episodeCount": 32,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "30b3af66-ed18-4d17-8782-a8fabbad81df",
                    "published": false,
                    "seasonCount": 10,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015401670000",
                    "title": "Veep",
                    "seasonCount": 7,
                    "episodeCount": 65,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 77
                },
                "resource": {
                    "id": "11f4f120-ec89-48ac-9aa5-d0dedde9aaf7",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 77
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030513670000",
                    "title": "Versailles",
                    "seasonCount": 3,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "6a856779-90c7-4b2f-b474-ecc57fd05524",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH014219680000",
                    "title": "Vestido de Novia",
                    "seasonCount": 18,
                    "episodeCount": 30,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "207f23b2-c75b-44ec-8096-28c7c68bdc53",
                    "published": false,
                    "seasonCount": 18,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025254180000",
                    "title": "Vice Guide to Film",
                    "seasonCount": 2,
                    "episodeCount": 14,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 11
                },
                "resource": {
                    "id": "a57e4a3c-614d-4cda-a1c5-54a56f3bc983",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 11
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024316740000",
                    "title": "Vice Principals",
                    "seasonCount": 2,
                    "episodeCount": 18,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 36
                },
                "resource": {
                    "id": "ffb32b12-edf2-40b6-92f3-2faedb3fcc2e",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 36
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031719180000",
                    "title": "Victor and Valentino en español",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 16
                },
                "resource": {
                    "id": "96576570-9a00-45d2-959a-fea3dd0b8858",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 16
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH025519900000",
                    "title": "Victoria",
                    "seasonCount": 3,
                    "episodeCount": 26,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 27
                },
                "resource": {
                    "id": "10502e87-3bc3-4c83-bd54-95f686ad731b",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 27
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012419190000",
                    "title": "Victorious",
                    "seasonCount": 4,
                    "episodeCount": 67,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 63
                },
                "resource": {
                    "id": "7a55334a-91c0-46bb-b6ae-32343eb33fbc",
                    "published": true,
                    "seasonCount": 4,
                    "episodeCount": 63
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027449140000",
                    "title": "Video Killed the Radio Star",
                    "seasonCount": 7,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "c1e5c4a9-ec66-42f2-8202-5bf749b917bb",
                    "published": true,
                    "seasonCount": 7,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH023331840000",
                    "title": "Vinyl",
                    "seasonCount": 1,
                    "episodeCount": 10,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "a2fbc27e-869d-4b2f-80fd-33058ded7403",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031854060000",
                    "title": "Vive libre o muere",
                    "seasonCount": 3,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "5ff31e9e-fe6e-467c-8dc1-e319e0f11c8a",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028090970000",
                    "title": "Wanted",
                    "seasonCount": 3,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "b61af0fc-6504-480b-965d-ebfccabe8bc4",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024882790000",
                    "title": "Westworld",
                    "seasonCount": 2,
                    "episodeCount": 20,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 20
                },
                "resource": {
                    "id": "8a96f9e4-0819-41ee-9b89-7292bc5bb1c0",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 20
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH008473400000",
                    "title": "When the Levees Broke: A Requiem in Four Acts",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "8ee551ed-be99-4580-8ed1-be2be9195099",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031197840000",
                    "title": "Whiskey Cavalier",
                    "seasonCount": 1,
                    "episodeCount": 9,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 8
                },
                "resource": {
                    "id": "6b1551a1-b421-40e0-8c5e-d9d582216d36",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 8
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027072760000",
                    "title": "Wild Argentina",
                    "seasonCount": 1,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "f6e491f4-40e8-43d2-bdf1-5be5d4989f75",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH029830720000",
                    "title": "Wild Filipinas",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "266aa339-8360-4ad9-9d0f-27d69a325e02",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031440160000",
                    "title": "Wild Mongolia",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "7dfe147c-dab9-493b-bf76-fcc238304bb9",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH021598050000",
                    "title": "Wild Sri Lanka",
                    "seasonCount": 0,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "4a590693-2275-4c21-a8af-3fa661071ddb",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH016257190000",
                    "title": "Witness",
                    "seasonCount": 1,
                    "episodeCount": 4,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 4
                },
                "resource": {
                    "id": "7c0acff6-f7cb-40d8-8cb6-31b7f47352b8",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 4
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH024377680000",
                    "title": "Woman",
                    "seasonCount": 1,
                    "episodeCount": 8,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 7
                },
                "resource": {
                    "id": "ae4fd023-5f71-4d8b-b0d1-1c969223170e",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 7
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH032133210000",
                    "title": "Years and Years",
                    "seasonCount": 1,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "86562aa3-ca83-4dd7-894b-3d5530a48390",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031473460000",
                    "title": "Yo, Chef",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "a168d4d8-e611-4a0b-b7c0-4b6348df7cc2",
                    "published": false,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028354000000",
                    "title": "Yoko",
                    "seasonCount": 2,
                    "episodeCount": 44,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "f9fbf95e-2715-4037-ace7-f028d5617767",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027382400000",
                    "title": "Young Sheldon",
                    "seasonCount": 3,
                    "episodeCount": 6,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 6
                },
                "resource": {
                    "id": "147982ac-17fd-4ec1-819e-68573d1594dd",
                    "published": false,
                    "seasonCount": 3,
                    "episodeCount": 6
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028912530000",
                    "title": "Zafari",
                    "seasonCount": 2,
                    "episodeCount": 38,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 22
                },
                "resource": {
                    "id": "43462541-4767-400c-9386-2e0e7d144a02",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 22
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027231690000",
                    "title": "Zak Storm",
                    "seasonCount": 2,
                    "episodeCount": 34,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 22
                },
                "resource": {
                    "id": "b969f159-2105-483e-9a9c-778e5bac66b2",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 22
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH012008540000",
                    "title": "iCarly",
                    "seasonCount": 5,
                    "episodeCount": 70,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 27
                },
                "resource": {
                    "id": "a5576cdf-5405-4ef3-8935-57f9762a0013",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 27
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH017588320000",
                    "title": "iCarly",
                    "seasonCount": 5,
                    "episodeCount": 59,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 82
                },
                "resource": {
                    "id": "0eec21ba-bc1b-4248-8b50-9213c34c7b4d",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 82
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH020378850000",
                    "title": "¡HOLA! TV Fashion",
                    "seasonCount": 1,
                    "episodeCount": 17,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 13
                },
                "resource": {
                    "id": "503a52e5-8c4d-4244-b0ba-de7df580089d",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 13
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH027540670000",
                    "title": "¡OK K.O.! Seamos héroes",
                    "seasonCount": 3,
                    "episodeCount": 5,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 5
                },
                "resource": {
                    "id": "24f52175-66ad-4ddc-961d-2d96d68ed176",
                    "published": true,
                    "seasonCount": 3,
                    "episodeCount": 5
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH002471030000",
                    "title": "¡Oye Arnold!",
                    "seasonCount": 5,
                    "episodeCount": 76,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 75
                },
                "resource": {
                    "id": "3e32e98a-7dab-4499-a02f-0bd19012dbf6",
                    "published": true,
                    "seasonCount": 5,
                    "episodeCount": 75
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH015495850000",
                    "title": "¿Quién da más?",
                    "seasonCount": 12,
                    "episodeCount": 12,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "0242f140-db99-4e4e-a4b7-d383ab78b83d",
                    "published": false,
                    "seasonCount": 12,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH028459480000",
                    "title": "¿Quién imita a quién?",
                    "seasonCount": 0,
                    "episodeCount": 3,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 3
                },
                "resource": {
                    "id": "53405405-9db3-4bc1-9aa7-5bbf1b86ed97",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 3
                },
                "seasonDifference": -1,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH030947020000",
                    "title": "¿Te lo vas a comer?",
                    "seasonCount": 2,
                    "episodeCount": 13,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 12
                },
                "resource": {
                    "id": "30ffd8bd-e2be-4b81-8878-484557627fe5",
                    "published": true,
                    "seasonCount": 2,
                    "episodeCount": 12
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031440200000",
                    "title": "África: Reinos mortales",
                    "seasonCount": 1,
                    "episodeCount": 2,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 2
                },
                "resource": {
                    "id": "662e0db5-f319-434a-aa24-d8a3458c32b4",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 2
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            },
            {
                "show": {
                    "id": "SH031681190000",
                    "title": "Ártico salvaje",
                    "seasonCount": 1,
                    "episodeCount": 1,
                    "mappeEpisodeCount": 0,
                    "resourceEpisodeCount": 1
                },
                "resource": {
                    "id": "c41ee081-360b-4b63-b013-21c617708205",
                    "published": true,
                    "seasonCount": 1,
                    "episodeCount": 1
                },
                "seasonDifference": 0,
                "episodeDifference": 0
            }
        ]
    }
}
```



### Get show group report

Returns metadata provider shows grouped by shared season ID. 

<!--This view was added to help troubleshoot the shared season problem, but it may still be useful. -->
<!-- Original endpoint: {{CMRServer}}/cmr/v1/report/showgroups/5909?exclude=episodes -->


<br>

The group ID for a show is provided at the bottom of the [show report](https://docs.dtc.istreamplanet.net/?version=latest#c8ba54e7-847c-4324-b0bd-52f1bb8ca4a9).
See the bottom of the example.

##### Path Parameters
|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|groupID|string |required	|Group ID for the target show.|

<br/>

<!-- Original endpoint: {{CMRServer}}/cmr/v1/report/showgroups/5909?exclude=episodes -->


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{CMRServer}}/cmr/v1/report/showgroups/{{groupID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| exclude | episodes | Optional. Omits the flat list of metadata provider episodes. The only valid value is __episodes__. |



***Responses:***


Status: Get Show Group Report | Code: 200



```js
{
    "requestID": "5549881d-c65b-4d7f-a677-32ee881a840d",
    "timestamp": "2019-08-22T00:15:04.020317532Z",
    "item": {
        "id": 5909,
        "showIDs": [
            "SH026958340000"
        ],
        "total": 1,
        "published": 0,
        "shows": [
            {
                "id": "SH026958340000",
                "title": "Vida no Pântano",
                "mapId": "79687ea3-ea5e-4bba-9fe7-b5b2d7ffd5b4",
                "seasons": [
                    {
                        "seasonId": "13603490",
                        "seasonNumber": "1",
                        "mapId": "a8c33cd7-7da4-4fdb-8cd4-48bcafadcc25",
                        "episodeCount": 0,
                        "mappedEpisodeCount": 0,
                        "episodeResourceCount": 0
                    }
                ],
                "resources": [
                    {
                        "id": "79687ea3-ea5e-4bba-9fe7-b5b2d7ffd5b4",
                        "resourceType": 8,
                        "publishStart": "0001-01-01T00:00:00Z",
                        "publishEnd": "0001-01-01T00:00:00Z",
                        "published": false,
                        "contentLock": false,
                        "name": "Vida no Pântano",
                        "shortName": "Vida no Pântano",
                        "seasonIDs": [
                            "a8c33cd7-7da4-4fdb-8cd4-48bcafadcc25"
                        ],
                        "language": "pt",
                        "providerUID": "SH026958340000",
                        "seasons": [
                            {
                                "id": "a8c33cd7-7da4-4fdb-8cd4-48bcafadcc25",
                                "resourceType": 7,
                                "publishStart": "0001-01-01T00:00:00Z",
                                "publishEnd": "0001-01-01T00:00:00Z",
                                "published": false,
                                "contentLock": false,
                                "name": "Vida no Pântano, 1",
                                "shortName": "",
                                "showID": "79687ea3-ea5e-4bba-9fe7-b5b2d7ffd5b4",
                                "seasonNumber": 1,
                                "vod/episodeIDs": [],
                                "episodeCount": 0
                            }
                        ],
                        "seasonCount": 1,
                        "episodeCount": 0
                    }
                ],
                "seasonCount": 1,
                "episodeCount": 0,
                "mappedEpisodeCount": 0,
                "episodeResourceCount": 0
            }
        ]
    }
}
```



### Get show report

Returns a detailed view of metadata provider and OCM show information for side-by-side comparison. 

<!-- Original endpoint: {{CMRServer}}/cmr/v1/report/shows/SH004928120000?exclude=episodes -->

<br>

This view has three main sections to help troubleshoot shows for which OCM resources do not precisely match with their metadata provider counterparts:

* __seasons__ <br>
 The metadata provider view of a show and its seasons and episodes to which OCM episode resources are joined by TMS ID.

* __episodes__ <br>
 The flat list of metadata provider episodes for a show to which OCM episode resources are joined. 
 This field is provided primarily for the case where a metadata provider show doesn't have seasons.

* __resources__ <br>
 The list of OCM resources for the metadata provider show joined by TMS ID.

<br>

##### Path Parameters
|Field	|Type	|Required	|Description	|
|---	|---	|---		|---			|
|showID	|string |required	|ID for the target show.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{CMRServer}}/cmr/v1/report/shows/{{showID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| exclude | episodes | Optional. Omits the  flat list of Gracenote episodes. The only valid value is __episodes__. |



***Responses:***


Status: Sample Get Show Report | Code: 200



```js
{
    "requestID": "2bd38700-484b-4606-beac-bb4f0e0c316d",
    "timestamp": "2019-08-20T21:57:50.895471053Z",
    "item": {
        "id": "SH031569960000",
        "title": "Gearing Up",
        "mapId": "11f1efe7-9854-4334-97b4-01b37dee005c",
        "seasons": [
            {
                "seasonId": "17222360",
                "seasonNumber": "1",
                "mapId": "f540a1ce-faaa-4ee7-a499-979aeae13fd4",
                "episodes": [
                    {
                        "id": "EP031569960005",
                        "connectorId": "SH031569960000",
                        "title": "",
                        "seasonId": "17222360",
                        "season": "1",
                        "number": "3",
                        "programmappings": [],
                        "mapId": []
                    },
                    {
                        "id": "EP031569960006",
                        "connectorId": "SH031569960000",
                        "title": "",
                        "seasonId": "17222360",
                        "season": "1",
                        "number": "2",
                        "programmappings": [],
                        "mapId": []
                    },
                    {
                        "id": "EP031569960009",
                        "connectorId": "SH031569960000",
                        "title": "",
                        "seasonId": "17222360",
                        "season": "1",
                        "number": "5",
                        "programmappings": [],
                        "mapId": []
                    },
                    {
                        "id": "EP031569960008",
                        "connectorId": "SH031569960000",
                        "title": "",
                        "seasonId": "17222360",
                        "season": "1",
                        "number": "4",
                        "programmappings": [],
                        "mapId": []
                    },
                    {
                        "id": "EP031569960007",
                        "connectorId": "SH031569960000",
                        "title": "",
                        "seasonId": "17222360",
                        "season": "1",
                        "number": "1",
                        "programmappings": [],
                        "mapId": []
                    }
                ],
                "episodeCount": 5,
                "mappedEpisodeCount": 0,
                "episodeResourceCount": 0
            }
        ],
        "resources": [
            {
                "id": "11f1efe7-9854-4334-97b4-01b37dee005c",
                "resourceType": 8,
                "publishStart": "2019-01-01T15:00:00Z",
                "publishEnd": "2100-01-01T00:00:00Z",
                "published": true,
                "contentLock": false,
                "name": "Gearing Up",
                "shortName": "Gearing Up",
                "seasonIDs": [
                    "8c1e9659-3de9-4a2f-be5f-403b412a4cbf",
                    "f540a1ce-faaa-4ee7-a499-979aeae13fd4"
                ],
                "language": "en",
                "providerUID": "SH031569960000",
                "seasons": [
                    {
                        "id": "8c1e9659-3de9-4a2f-be5f-403b412a4cbf",
                        "resourceType": 7,
                        "publishStart": "2019-01-01T15:00:00Z",
                        "publishEnd": "2100-01-01T00:00:00Z",
                        "published": true,
                        "contentLock": false,
                        "name": "Gearing Up",
                        "shortName": "",
                        "showID": "11f1efe7-9854-4334-97b4-01b37dee005c",
                        "seasonNumber": 0,
                        "vod/episodeIDs": [],
                        "episodeCount": 0
                    },
                    {
                        "id": "f540a1ce-faaa-4ee7-a499-979aeae13fd4",
                        "resourceType": 7,
                        "publishStart": "0001-01-01T00:00:00Z",
                        "publishEnd": "0001-01-01T00:00:00Z",
                        "published": false,
                        "contentLock": false,
                        "name": "Gearing Up, 1",
                        "shortName": "",
                        "showID": "11f1efe7-9854-4334-97b4-01b37dee005c",
                        "seasonNumber": 1,
                        "vod/episodeIDs": [],
                        "episodeCount": 0
                    }
                ],
                "seasonCount": 2,
                "episodeCount": 0
            }
        ],
        "seasonCount": 1,
        "episodeCount": 5,
        "mappedEpisodeCount": 0,
        "episodeResourceCount": 0,
        "group": 41
    }
}
```



### Get shows report

Returns overall quality metrics for:

* __resourceTotals__ <br>
 The total number of resources from GI and OCM accessed to generate the reports.

* __showsWithVodEpisodes__ <br>
 Quality metrics for shows, seasons, and episodes for published and unpublished shows that have VOD episodes. The individual data points are documented in Postman.

* __allShows__ <br>
 Quality metrics for all shows and seasons. The individual data points are documented in Postman.

<br>

#### Resource Totals

| Field | Description |
|---------------------------|------------------------------------------------------------------------------------------------|
| numEpisodeResources       | OCM VOD/episodes (11) with metadata and with a non-empty metadata id |
| numPubEpisodeResources    | Published OCM VOD/episode |
| numSeasonResources        | OCM season (7) |
| numShowResources          | OCM show (8) with a provider id that starts with SH |
| numPubShowResources       | Published OCM shos |
| numShows                  | Metadata provider programs (shows) with a TMS ID that starts with SH |
| numEpisodes               | Metadata provider programs (episodes) with a TMS ID that starts with EP |
| numJoinedEpisodeResources | OCM VOD/episodes joined to metadata provider episodes by TMS ID |
| numJoinedShowResources    | OCM shows joined to metadata provider shows by TMS ID |
| numJoinedSeasonEpisodes   | Metadata provider episodes joined to seasons |
| numJoinedShowEpisodes     | Metadata provider episodes joined to shows without seasons |

#### Shows With VOD Episodes

|Parent | Field | Description |
|-------|-------|-------------|
|showsWithVodEpisodes| numShows                  | Metadata provider shows |
|showsWithVodEpisodes| numShowResources          | OCM shows |
|showsWithVodEpisodes| numUnmappedShows          | Metadata provider shows not mapped to an OCM show by GI |
|showsWithVodEpisodes| numShowsWithDupResource   | Metadata provider shows that have duplicate OCM shows |
|showsWithVodEpisodes| numLockedShowResources    | OCM locked shows |
|| unmappedShows             | List of show TMS IDs for numUnmappedShows |
|| showsWithDupResources     | List of show TMS IDs for numShowsWithDupResource |
|| seasons                   | Seasons report |
|| episodes                  | Episodes report |

#### Seasons

| Field | Description |
|--------------------------------------|-------------------------------------------------------------------------------------|
| numShowsWithSeasons                  | Metadata provider shows that have seasons |
| numShowsWithMissingSeasons           | Metadata provider shows that have more seasons than the OCM show |
| numShowsWithExtraSeasons             | Metadata provider shows that have fewer seasons than the OCM show |
| numShowsWithMismatchedSeasonNumbers  | Metadata provider shows that have season numbers mismatched with the OCM show seasons |
| numShowsWithUnmappedSeasons          | Metadata provider shows that have seasons not mapped to OCM seasons by GI |
| numSeasons                           | Metadata provider seasons |
| numUnmappedSeasons                   | Metadata provider seasons not mapped to an OCM season by GI |
| numSeasonsWithMismatchedShowID       | OCM seasons with incorrect show uplink |
| showsWithMissingSeasons              | List of show TMS IDs for numShowsWithMissingSeasons |
| showsWithExtraSeasons                | List of show TMS IDs for numShowsWithExtraSeasons |
| showsWithMismatchedSeasonNumbers     | List of show TMS IDs for numShowsWithMismatchedSeasonNumbers |
| ShowsWithUnmappedSeasons             | List of show TMS IDs for numShowsWithUnmappedSeasons |
| showsWithSeasonsWithMismatchedShowID | List of show TMS IDs for numSeasonsWithMismatchedShowID |

#### Episodes
| Field | Description |
|--------------------------------------|-------------------------------------------------------------------------------------|
| numEpisodes                          | Metadata provider episodes |
| numEpisodesWithPaid                  | Metadata provider episodes with a PAID |
| numEpisodesResources                 | OCM episode resources |
| numUnmappedEpisodes                  | Metadata provider episodes not mapped to an OCM resource by GI |
| numLockedEpisodes                    | OCM locked episode resources |
| numShowsWithMissingEpisodes          | Metadata provider shows that have more episodes than the OCM show resource |
| numShowsWithExtraEpisodes            | Metadata provider shows that have fewer episodes than the OCM show resource |
| numShowsWithMissingEpisodeIDs        | Metadata provider shows that have mapped OCM episodes missing from the OCM show VOD/episodes | 
| numShowsWithExtraEpisodeIDs          | OCM show with VOD/episodes missing from the metadata provider show mapped episodes |
| numEpisodesWithDupResources          | Metadata provider episodes with duplicate OCM episodes |
| numEpisodesWithDupPublishedResources | Metadata provider episodes with duplicate published OCM episodes |
| numShowsWithDupEpisodes              | Metadata provider shows that have duplicate OCM episodes |
| numShowsWithDupPublishedEpisodes.    | Metadata provider shows that have duplicate published OCM episodes |
| numEpisodesWithMismatchedShowID      | OCM episodes with incorrect show uplink |
| numEpisodesWithMismatchedSeasonID    | OCM episodes with incorrect season uplink |
| numEpisodesMissingRegions            | OCM episodes with missing regions |
| numShowsWithEpisodesMissingRegions   | OCM shows that have episodes missing regions |
| numEpisodesWithMismatchedPaid        | OCM episodes with PAID that does not match the metadata provider episode PAID |
| numShowsWithEpisodesWithMismatchedPaid | OCM shows that have episodes with mismatch PAID |
| showsWithMissingEpisodes             | List of show TMS IDs for numShowsWithMissingEpisodes |            
| showsWithExtraEpisodes               | List of show TMS IDs for numShowsWithExtraEpisodes |
| showsWithMissingEpisodeIDs           | List of show TMS IDs for numShowsWithMissingEpisodeIDs |
| showsWithExtraEpisodeIDs             | List of show TMS IDs for numShowsWithExtraEpisodeIDs |
| showsWithDupEpisodes                 | List of show TMS IDs for numShowsWithDupEpisodes |
| episodesMissingRegions               | List of show TMS IDs for numEpisodesMissingRegions |
| showsWithEpisodesMissingRegions      | List of show TMS IDs for numShowsWithEpisodesMissingRegions |
| episodesWithMismatchedPaid           | List of episode TMS IDs for numEpisodesWithMismatchedPaid |
| showsWithEpisodesWithMismatchedPaid  | List of show TMS IDs for numShowsWithEpisodesWithMismatchedPaid |

<br>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{CMRServer}}/cmr/v1/report/shows
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Accept | application/json |  |



***Responses:***


Status: Get Shows Report-1 | Code: 200



```js
{
    "requestID": "5e5aaf07-b40c-4cb6-aeb6-01f36b3ee56e",
    "timestamp": "2019-08-21T20:47:41.987717383Z",
    "item": {
        "updated": "2019-08-21T09:12:27.097Z",
        "type": "all",
        "resourceTotals": {
            "numEpisodeResources": 0,
            "numPubEpisodeResources": 0,
            "numSeasonResources": 966,
            "numShowResources": 490,
            "numPubShowResources": 206,
            "numShows": 584,
            "numEpisodes": 515,
            "numJoinedEpisodeResources": 0,
            "numJoinedShowResources": 490,
            "numJoinedSeasonEpisodes": 114,
            "numJoinedShowEpisodes": 382
        },
        "showsWithVodEpisodes": {
            "numShows": 0,
            "numShowResources": 0,
            "numUnmappedShows": 0,
            "numShowsWithDupResources": 0,
            "numLockedShowResources": 0,
            "seasons": {
                "numShowsWithSeasons": 0,
                "numShowsWithMissingSeasons": 0,
                "numShowsWithExtraSeasons": 0,
                "numShowsWithMismatchedSeasonNumbers": 0,
                "numShowsWithUnmappedSeasons": 0,
                "numSeasons": 0,
                "numUnmappedSeasons": 0,
                "numSeasonsWithMismatchedShowID": 0
            },
            "episodes": {
                "numEpisodes": 0,
                "numEpisodesWithPaid": 0,
                "numEpisodesResources": 0,
                "numUnmappedEpisodes": 0,
                "numLockedEpisodes": 0,
                "numShowsWithMissingEpisodes": 0,
                "numShowsWithExtraEpisodes": 0,
                "numShowsWithMissingEpisodeIDs": 0,
                "numShowsWithExtraEpisodeIDs": 0,
                "numEpisodesWithMismatchedShowID": 0,
                "numEpisodesWithMismatchedSeasonID": 0,
                "numEpisodesMissingRegions": 0,
                "numShowsWithEpisodesMissingRegions": 0,
                "numEpisodesWithMismatchedPaid": 0,
                "numShowsWithEpisodesWithMismatchedPaid": 0,
                "numEpisodesWithDupPublishedResources": 0,
                "numEpisodesWithDupResources": 0,
                "numShowsWithDupPublishedEpisodes": 0,
                "numShowsWithDupEpisodes": 0
            }
        },
        "allShows": {
            "numShows": 584,
            "numShowResources": 490,
            "numUnmappedShows": 0,
            "numShowsWithDupResources": 0,
            "numLockedShowResources": 0,
            "seasons": {
                "numShowsWithSeasons": 43,
                "numShowsWithMissingSeasons": 0,
                "numShowsWithExtraSeasons": 2,
                "numShowsWithMismatchedSeasonNumbers": 2,
                "numShowsWithUnmappedSeasons": 2,
                "numSeasons": 270,
                "numUnmappedSeasons": 2,
                "numSeasonsWithMismatchedShowID": 0,
                "showsWithExtraSeasons": [
                    "SH027290310000",
                    "SH031569960000"
                ],
                "showsWithMismatchedSeasonNumbers": [
                    "SH027290310000",
                    "SH031569960000"
                ],
                "showsWithUnmappedSeasons": [
                    "SH027290310000",
                    "SH031569960000"
                ]
            }
        }
    }
}
```



---
[Back to top](#content-reporting)
> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2020-04-08 15:58:57 by [docgen](https://github.com/thedevsaddam/docgen)