---
id: api-sports
title: Sports - v1
sidebar_label: Sports 
---

The _sports_ endpoints allow applications to create and manage sports-related entities such as leagues, teams, players, games, and scores.

--------


## Games


### Create game

Creates a game entry.

<br/>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|title	|	|string	|required	|Start time for the game in ISO-8601 format.|
|`descriptions`	|	|list	|required	|Start time for the game in ISO-8601 format.|
|length		|`descriptions`|string	|required	|Text length descriptor--for example, *long* or *short*. |
|text		|`descriptions`|string	|required	|Descriptive text for the game. |
|language	|`descriptions`|string	|required	|Language of the descriptive text--for example, *en-us*, *es*, or *ja*. |
|startTime	|	|string	|required	|Start time for the game in ISO-8601 format.|
|status	|	|string	|required	|Game stream status--May be *SCHEDULED* before it starts, *STARTED* when it is running, or *STOPPED* when it has ended.|
|`venue`|	|object	|required	|Description of the game location.|
|name		|`venue`|string	|required	|Name of the stadium, field, or park.|
|location	|`venue`|string	|required	|Geographic location: district, city, county/state/province, and country.|
|timezone	|`venue`|string	|required	|Timezone abbreviation. |
|tournament	|	|string	|required	|Name of the game tournament.|
|leagueID	|	|string	|required	|ID of the sport league.|
|sportID	|	|string	|required	|ID of the sport.|
|`homeTeam`	|	|object	|required	|Home team description.|
|teamID	|`homeTeam`	|string	|required	|ID for the home team in this game.|
|name	|`homeTeam`	|string	|required	|Name of the home team.|
|`picture`	|`homeTeam`	|object	|optional	|Team picture.|
|pictureID	|`picture`	|string	|required	|Generated ID for the team picture.|
|url	|`picture`	|string		|required	|URL to display the team picture.|
|height	|`picture`	|integer	|required	|Height of the team picture.|
|width	|`picture`	|integer	|required	|Width of the team picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`awayTeam`	|	|object	|required	|Away team description.|
|teamID	|`awayTeam`	|string	|required	|ID for the away team in this game.|
|name	|`awayTeam`	|string	|required	|Name of the away team.|
|`picture`	|`awayTeam`	|object	|optional	|Team picture.|
|pictureID	|`picture`	|string	|required	|Generated ID for the team picture.|
|url	|`picture`	|string		|required	|URL to display the team picture.|
|height	|`picture`	|integer	|required	|Height of the team picture.|
|width	|`picture`	|integer	|required	|Width of the team picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`players`		|	|list	|required	|List of players in this game.|
|playerID	|`players`	|string	|required	|ID for a player in this game.|
|teamID		|`players`	|string	|required	|ID for the player's team in this game.|
|firstName	|`players`	|string	|required	|Player's first name.|
|lastName	|`players`	|string	|required	|Player's last name.|
|scores	|	|list	|optional	|List of game scores.|
|`resourceIDs`|	|list	|optional	|List of placeholder resource IDs.|
|PlaceholderResourceID	|`resourceIDs`	|string	|optional	|Placeholder resource ID.|
|`pictures`	|		|list	|optional	|Pictures of the player.|
|pictureID	|`pictures`	|string	|required	|Generated ID for the player's picture.|
|url	|`pictures`	|string		|required	|URL to display the player's picture.|
|height	|`pictures`	|integer	|required	|Height of the player's picture.|
|width	|`pictures`	|integer	|required	|Width of the player's picture.|
|type	|`pictures`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>


#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to create a game.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{SportsServer}}/sports/v1/games
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
    "title": "Aresenal vs Chelsea",
    "descriptions": [
        {
            "length": "short",
            "text": "The rivalry between Arsenal and Chelsea is a football local derby in London between the two clubs. Arsenal play their home games at the Emirates Stadium, while Chelsea play their home games at Stamford Bridge.",
            "language": "en-us"
        },
        {
            "length": "long",
            "text": "While they never considered each other primary rivals, as two of the biggest and most successful clubs in London there has always been strong needle between the fans dating back to the 1930s. Matches between them would often attract large attendances. The Arsenal and Chelsea rivalry has been more recently considered an important derby, after Chelsea's rise to the top class of the Premier League in the 2000s, when the two started to compete constantly for the Premier League title.",
            "language": "en-us"
        }
    ],
    "startTime": "2019-01-28T21:00:00.000Z",
    "status": "scheduled",
    "venue": {
        "name": "Emirates Stadium",
        "location": "Holloway, London, England",
        "timezone": "GMT"
    },
    "tournament": "Premier League 2017/2018 Season",
    "leagueID": "c3c39f64-ed87-41df-aa2f-70a849749b9e",
    "sportID": "ea3c8187-0f9f-4f75-b947-cc5762765546",
    "homeTeam": {
        "teamID": "e73d46c3-7fba-40a9-92c1-0443f612394a",
        "name": "Arsenal F.C.",
        "picture": {
            "pictureID": "944e68e7-7146-406c-ac8d-df379c894d86",
            "url": "https://en.wikipedia.org/wiki/Arsenal_F.C.#/media/File:Arsenal_FC.svg",
            "height": 1410,
            "width": 1200,
            "type": "logo"
        }
    },
    "awayTeam": {
        "teamID": "7f91dd36-9821-44d9-a9b2-aed464996049",
        "name": "Chelsea F.C.",
        "picture": {
            "pictureID": "88d421d1-7f19-4f0e-aa8a-e0d0533342f9",
            "url": "https://en.wikipedia.org/wiki/Chelsea_F.C.#/media/File:Chelsea_FC.svg",
            "height": 1200,
            "width": 1200,
            "type": "logo"
        }
    },
    "players": [
        {
            "playerID": "42283f0f-b6ae-4e0e-a7cc-dced1acf24b7",
            "teamID": "e73d46c3-7fba-40a9-92c1-0443f612394a",
            "firstName": "Robert",
            "lastName": "Holding"
        },
        {
            "playerID": "c6c4b479-64e1-420d-9394-d74fbbd21380",
            "teamID": "e73d46c3-7fba-40a9-92c1-0443f612394a",
            "firstName": "Eddie",
            "lastName": "Nketiah"
        },
        {
            "playerID": "b8ac9aed-008d-43eb-95f9-1de9a6813285",
            "teamID": "e73d46c3-7fba-40a9-92c1-0443f612394a",
            "firstName": "Henrikh",
            "lastName": "Mkhitaryan"
        },
        {
            "playerID": "3618fdbf-3775-44d8-8ff2-93e8d5d2cfe4",
            "teamID": "7f91dd36-9821-44d9-a9b2-aed464996049",
            "firstName": "Ethan",
            "lastName": "Ampadu"
        },
        {
            "playerID": "c6e3d9fe-1d1c-43d8-88c0-30fdcda6ee33",
            "teamID": "7f91dd36-9821-44d9-a9b2-aed464996049",
            "firstName": "Victor",
            "lastName": "Moses"
        },
        {
            "playerID": "243806ae-44f3-4ccb-8f82-58b128b0aefb",
            "teamID": "7f91dd36-9821-44d9-a9b2-aed464996049",
            "firstName": "Gary",
            "lastName": "Cahill"
        }
    ],
    "scores": [],
    "resourceIDs": [
        "PlaceholderResourceID"
    ],
    "pictures": [
        {
            "pictureID": "0b4b0e15-ad2f-4599-9136-fd5ff011ac32",
            "url": "http://itaa.ie/wp-content/uploads/2018/08/arsenal-chelsea.jpg",
            "height": 260,
            "width": 610,
            "type": "banner"
        }
    ],
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Create game | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "games": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "title": "University of Washington Huskies vs Seattle Seahawks",
            "descriptions": [
                {
                    "length": "short",
                    "language": "en-us",
                    "text": "Seattle's college football team faces off against it's NFL team."
                }
            ],
            "startTime": "2018-01-01T01:00:00Z08:00",
            "status": "stopped",
            "venue": {
                "name": "CenturyLink Field",
                "location": "Seattle, WA",
                "timezone": "PDT"
            },
            "tournament": "College vs Pro League",
            "leagueID": "87654321-dead-beef-9012-deadbeef1234",
            "sportID": "12341234-1234-1234-9012-deadbeef1234",
            "homeTeam": {
                "teamID": "12341234-dead-beef-9012-deadbeef1234",
                "name": "University of Washington Huskies",
                "picture": {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            },
            "awayTeam": {
                "teamID": "12341234-dead-beef-9012-deadbeef1234",
                "name": "University of Washington Huskies",
                "picture": {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            },
            "players": [
                {
                    "playerID": "11223344-3333-4444-9012-deadbeef1234",
                    "firstName": "Russel",
                    "lastName": "Wilson",
                    "teamID": "12341234-dead-beef-9012-deadbeef1234"
                },
                {
                    "playerID": "31223344-3333-5555-9012-deadbeef1234",
                    "firstName": "Aaron",
                    "lastName": "Fuller",
                    "teamID": "12341234-dead-beef-9012-deadbeef1234"
                }
            ],
            "scores": [
                {
                    "teamID": "12341234-dead-beef-9012-deadbeef1234",
                    "points": 48
                },
                {
                    "teamID": "12341234-dead-beef-9012-deadbeef1234",
                    "points": 3
                }
            ],
            "resourceIDs": [
                "12345678-beef-1234-1234-111222333444",
                "87654321-beef-1234-4321-111222333444"
            ],
            "pictures": [
                {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                },
                {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            ]
        }
    ]
}
```



### Update game

Updates information for the specified game.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|gameID |string |required	|ID for the target game to be updated.|

<br/>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|title	|	|string	|required	|Start time for the game in ISO-8601 format.|
|`descriptions`	|	|list	|required	|Start time for the game in ISO-8601 format.|
|length		|`descriptions`|string	|required	|Text length descriptor--for example, *long* or *short*. |
|text		|`descriptions`|string	|required	|Descriptive text for the game. |
|language	|`descriptions`|string	|required	|Language of the descriptive text--for example, *en-us*, *es*, or *ja*. |
|startTime	|	|string	|required	|Start time for the game in ISO-8601 format.|
|status	|	|string	|required	|Game stream status--May be *SCHEDULED* before it starts, *STARTED* when it is running, or *STOPPED* when it has ended.|
|`venue`|	|object	|required	|Description of the game location.|
|name		|`venue`|string	|required	|Name of the stadium, field, or park.|
|location	|`venue`|string	|required	|Geographic location: district, city, county/state/province, and country.|
|timezone	|`venue`|string	|required	|Timezone abbreviation. |
|tournament	|	|string	|required	|Name of the game tournament.|
|leagueID	|	|string	|required	|ID of the sport league.|
|sportID	|	|string	|required	|ID of the sport.|
|`homeTeam`	|	|object	|required	|Home team description.|
|teamID	|`homeTeam`	|string	|required	|ID for the home team in this game.|
|name	|`homeTeam`	|string	|required	|Name of the home team.|
|`picture`	|`homeTeam`	|object	|optional	|Team picture.|
|pictureID	|`picture`	|string	|required	|Generated ID for the team picture.|
|url	|`picture`	|string		|required	|URL to display the team picture.|
|height	|`picture`	|integer	|required	|Height of the team picture.|
|width	|`picture`	|integer	|required	|Width of the team picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`awayTeam`	|	|object	|required	|Away team description.|
|teamID	|`awayTeam`	|string	|required	|ID for the away team in this game.|
|name	|`awayTeam`	|string	|required	|Name of the away team.|
|`picture`	|`awayTeam`	|object	|optional	|Team picture.|
|pictureID	|`picture`	|string	|required	|Generated ID for the team picture.|
|url	|`picture`	|string		|required	|URL to display the team picture.|
|height	|`picture`	|integer	|required	|Height of the team picture.|
|width	|`picture`	|integer	|required	|Width of the team picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`players`		|	|list	|required	|List of players in this game.|
|playerID	|`players`	|string	|required	|ID for a player in this game.|
|teamID		|`players`	|string	|required	|ID for the player's team in this game.|
|firstName	|`players`	|string	|required	|Player's first name.|
|lastName	|`players`	|string	|required	|Player's last name.|
|scores	|	|list	|optional	|List of game scores.|
|`resourceIDs`|	|list	|optional	|List of placeholder resource IDs.|
|PlaceholderResourceID	|`resourceIDs`	|string	|optional	|Placeholder resource ID.|
|`pictures`	|		|list	|optional	|Pictures of the player.|
|pictureID	|`pictures`	|string	|required	|Generated ID for the player's picture.|
|url	|`pictures`	|string		|required	|URL to display the player's picture.|
|height	|`pictures`	|integer	|required	|Height of the player's picture.|
|width	|`pictures`	|integer	|required	|Width of the player's picture.|
|type	|`pictures`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
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
URL: {{SportsServer}}/sports/v1/games/{{gameID}}
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
    "title": "Aresenal vs Chelsea",
    "descriptions": [
        {
            "length": "short",
            "text": "The rivalry between Arsenal and Chelsea is a football local derby in London between the two clubs. Arsenal play their home games at the Emirates Stadium, while Chelsea play their home games at Stamford Bridge.",
            "language": "en-us"
        },
        {
            "length": "long",
            "text": "While they never considered each other primary rivals, as two of the biggest and most successful clubs in London there has always been strong needle between the fans dating back to the 1930s. Matches between them would often attract large attendances. The Arsenal and Chelsea rivalry has been more recently considered an important derby, after Chelsea's rise to the top class of the Premier League in the 2000s, when the two started to compete constantly for the Premier League title.",
            "language": "en-us"
        }
    ],
    "startTime": "2019-01-28T21:00:00.000Z",
    "status": "scheduled",
    "venue": {
        "name": "Emirates Stadium",
        "location": "Holloway, London, England",
        "timezone": "GMT"
    },
    "tournament": "Premier League 2017/2018 Season",
    "leagueID": "c3c39f64-ed87-41df-aa2f-70a849749b9e",
    "sportID": "ea3c8187-0f9f-4f75-b947-cc5762765546",
    "homeTeam": {
        "teamID": "e73d46c3-7fba-40a9-92c1-0443f612394a",
        "name": "Arsenal F.C.",
        "picture": {
            "pictureID": "944e68e7-7146-406c-ac8d-df379c894d86",
            "url": "https://en.wikipedia.org/wiki/Arsenal_F.C.#/media/File:Arsenal_FC.svg",
            "height": 1410,
            "width": 1200,
            "type": "logo"
        }
    },
    "awayTeam": {
        "teamID": "7f91dd36-9821-44d9-a9b2-aed464996049",
        "name": "Chelsea F.C.",
        "picture": {
            "pictureID": "88d421d1-7f19-4f0e-aa8a-e0d0533342f9",
            "url": "https://en.wikipedia.org/wiki/Chelsea_F.C.#/media/File:Chelsea_FC.svg",
            "height": 1200,
            "width": 1200,
            "type": "logo"
        }
    },
    "players": [
        {
            "playerID": "42283f0f-b6ae-4e0e-a7cc-dced1acf24b7",
            "teamID": "e73d46c3-7fba-40a9-92c1-0443f612394a",
            "firstName": "Robert",
            "lastName": "Holding"
        },
        {
            "playerID": "c6c4b479-64e1-420d-9394-d74fbbd21380",
            "teamID": "e73d46c3-7fba-40a9-92c1-0443f612394a",
            "firstName": "Eddie",
            "lastName": "Nketiah"
        },
        {
            "playerID": "b8ac9aed-008d-43eb-95f9-1de9a6813285",
            "teamID": "e73d46c3-7fba-40a9-92c1-0443f612394a",
            "firstName": "Henrikh",
            "lastName": "Mkhitaryan"
        },
        {
            "playerID": "3618fdbf-3775-44d8-8ff2-93e8d5d2cfe4",
            "teamID": "7f91dd36-9821-44d9-a9b2-aed464996049",
            "firstName": "Ethan",
            "lastName": "Ampadu"
        },
        {
            "playerID": "c6e3d9fe-1d1c-43d8-88c0-30fdcda6ee33",
            "teamID": "7f91dd36-9821-44d9-a9b2-aed464996049",
            "firstName": "Victor",
            "lastName": "Moses"
        },
        {
            "playerID": "243806ae-44f3-4ccb-8f82-58b128b0aefb",
            "teamID": "7f91dd36-9821-44d9-a9b2-aed464996049",
            "firstName": "Gary",
            "lastName": "Cahill"
        }
    ],
    "scores": [],
    "resourceIDs": [
        "PlaceholderResourceID"
    ],
    "pictures": [
        {
            "pictureID": "0b4b0e15-ad2f-4599-9136-fd5ff011ac32",
            "url": "http://itaa.ie/wp-content/uploads/2018/08/arsenal-chelsea.jpg",
            "height": 260,
            "width": 610,
            "type": "banner"
        }
    ],
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Update game | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "games": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "title": "University of Washington Huskies vs Seattle Seahawks",
            "descriptions": [
                {
                    "length": "short",
                    "language": "en-us",
                    "text": "Seattle's college football team faces off against it's NFL team."
                }
            ],
            "startTime": "2018-01-01T01:00:00Z08:00",
            "status": "stopped",
            "venue": {
                "name": "CenturyLink Field",
                "location": "Seattle, WA",
                "timezone": "PDT"
            },
            "tournament": "College vs Pro League",
            "leagueID": "87654321-dead-beef-9012-deadbeef1234",
            "sportID": "12341234-1234-1234-9012-deadbeef1234",
            "homeTeam": {
                "teamID": "12341234-dead-beef-9012-deadbeef1234",
                "name": "University of Washington Huskies",
                "picture": {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            },
            "awayTeam": {
                "teamID": "12341234-dead-beef-9012-deadbeef1234",
                "name": "University of Washington Huskies",
                "picture": {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            },
            "players": [
                {
                    "playerID": "11223344-3333-4444-9012-deadbeef1234",
                    "firstName": "Russel",
                    "lastName": "Wilson",
                    "teamID": "12341234-dead-beef-9012-deadbeef1234"
                },
                {
                    "playerID": "31223344-3333-5555-9012-deadbeef1234",
                    "firstName": "Aaron",
                    "lastName": "Fuller",
                    "teamID": "12341234-dead-beef-9012-deadbeef1234"
                }
            ],
            "scores": [
                {
                    "teamID": "12341234-dead-beef-9012-deadbeef1234",
                    "points": 48
                },
                {
                    "teamID": "12341234-dead-beef-9012-deadbeef1234",
                    "points": 3
                }
            ],
            "resourceIDs": [
                "12345678-beef-1234-1234-111222333444",
                "87654321-beef-1234-4321-111222333444"
            ],
            "pictureIDs": [
                {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                },
                {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            ]
        }
    ]
}
```



### Retrieve game

Retrieves the specified game.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|gameID |string |required	|ID for the target game to be viewed.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target game content.|
|404		|1040	|*Not Found*: Target game not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/games/{{gameID}}/
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
| include | scores | Optionally fetches related entities [*teams, players, leagues, sports, scores*] when specified. |



***Responses:***


Status: Get game | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "games": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "title": "University of Washington Huskies vs Seattle Seahawks",
            "descriptions": [
                {
                    "length": "short",
                    "language": "en-us",
                    "text": "Seattle's college football team faces off against it's NFL team."
                }
            ],
            "startTime": "2018-01-01T01:00:00Z08:00",
            "status": "stopped",
            "venue": {
                "name": "CenturyLink Field",
                "location": "Seattle, WA",
                "timezone": "PDT"
            },
            "tournament": "College vs Pro League",
            "leagueID": "87654321-dead-beef-9012-deadbeef1234",
            "sportID": "12341234-1234-1234-9012-deadbeef1234",
            "homeTeam": {
                "teamID": "12341234-dead-beef-9012-deadbeef1234",
                "name": "University of Washington Huskies",
                "picture": {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            },
            "awayTeam": {
                "teamID": "12341234-dead-beef-9012-deadbeef1234",
                "name": "University of Washington Huskies",
                "picture": {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            },
            "players": [
                {
                    "playerID": "11223344-3333-4444-9012-deadbeef1234",
                    "firstName": "Russel",
                    "lastName": "Wilson",
                    "teamID": "12341234-dead-beef-9012-deadbeef1234"
                },
                {
                    "playerID": "31223344-3333-5555-9012-deadbeef1234",
                    "firstName": "Aaron",
                    "lastName": "Fuller",
                    "teamID": "12341234-dead-beef-9012-deadbeef1234"
                }
            ],
            "scores": [
                {
                    "teamID": "12341234-dead-beef-9012-deadbeef1234",
                    "points": 48
                },
                {
                    "teamID": "12341234-dead-beef-9012-deadbeef1234",
                    "points": 3
                }
            ],
            "resourceIDs": [
                "12345678-beef-1234-1234-111222333444",
                "87654321-beef-1234-4321-111222333444"
            ],
            "pictures": [
                {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                },
                {
                    "pictureID": "12341234-0000-beef-9992-deadbeef1234",
                    "url": "https://images.com/img124",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            ]
        }
    ]
}
```



### List games

Lists all games sorted by start time that match the specified sport, league, team, and other query parameters.

All query parameters are optional unless otherwise indicated.

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target sport, league, or team.|
|404		|1040	|*Not Found*: Target sport, league, or team not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/games/
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
| startTimeGte | 2018-11-20T15:00:00.000Z | Start of time range in ISO-8601 format: lists events that begin  _at or after_ the specified date and time. |
| startTimeLte | 2019-11-20T15:00:00.000Z | End of time range in ISO-8601 format: lists events that begin _at or before_ the specified date and time. |
| include | players,teams,scores | Optionally fetches related entities [*teams, players, leagues, sports, scores*] when specified. |
| query | chelsea | Query string to search for within the game title, tournament, player names, or team names. |
| status | SCHEDULED | Stream status. The status may be *SCHEDULED* before the stream has started, *STARTED* when the stream is running, or *STOPPED* when the stream has ended. |
| sportID | {{sportID}} | ID of the desired sport to list games for. |
| leagueID | {{leagueID}} | ID of the desired league to list games for. |
| teamID | {{teamID}} | ID of the desired team to list games for. |
| count | 25 | Maximum number of results returned per call. Default is 50. |
| offset | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |



***Responses:***


Status: List games | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "games": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "title": "University of Washington Huskies vs Seattle Seahawks",
            "descriptions": [
                {
                    "length": "short",
                    "language": "en-us",
                    "text": "Seattle's college football team faces off against it's NFL team."
                }
            ],
            "startTime": "2018-01-01T01:00:00Z08:00",
            "status": "stopped",
            "venue": {
                "name": "CenturyLink Field",
                "location": "Seattle, WA",
                "timezone": "PDT"
            },
            "tournament": "College vs Pro League",
            "leagueID": "87654321-dead-beef-9012-deadbeef1234",
            "sportID": "12341234-1234-1234-9012-deadbeef1234",
            "homeTeam": {
                "teamID": "12341234-dead-beef-9012-deadbeef1234",
                "name": "University of Washington Huskies",
                "picture": {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            },
            "awayTeam": {
                "teamID": "12341234-dead-beef-9012-deadbeef1234",
                "name": "University of Washington Huskies",
                "picture": {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            },
            "players": [
                {
                    "playerID": "11223344-3333-4444-9012-deadbeef1234",
                    "firstName": "Russel",
                    "lastName": "Wilson",
                    "teamID": "12341234-dead-beef-9012-deadbeef1234"
                },
                {
                    "playerID": "31223344-3333-5555-9012-deadbeef1234",
                    "firstName": "Aaron",
                    "lastName": "Fuller",
                    "teamID": "12341234-dead-beef-9012-deadbeef1234"
                }
            ],
            "scores": [
                {
                    "teamID": "12341234-dead-beef-9012-deadbeef1234",
                    "points": 48
                },
                {
                    "teamID": "12341234-dead-beef-9012-deadbeef1234",
                    "points": 3
                }
            ],
            "resourceIDs": [
                "12345678-beef-1234-1234-111222333444",
                "87654321-beef-1234-4321-111222333444"
            ],
            "pictures": [
                {
                    "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                    "url": "https://images.com/img123",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                },
                {
                    "pictureID": "12341234-0000-beef-9992-deadbeef1234",
                    "url": "https://images.com/img124",
                    "height": 1024,
                    "width": 1920,
                    "type": "banner"
                }
            ]
        }
    ]
}
```



### Delete game

Deletes the specified game.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|gameID |string |required	|ID for the target game to be deleted.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target game.|
|404		|1040	|*Not Found*: Target game not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{SportsServer}}/sports/v1/games/{{gameID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



## Leagues



### Create league

Creates a sports league.

<br/>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|name	|	|string	|required	|Name of the league.|
|sportID|	|string	|required	|Generated ID for the sport this league plays.|
|`picture`	|		|object	|optional	|Picture for the league.|
|pictureID	|`picture`	|string	|required	|Generated ID for the picture.|
|url	|`picture`	|string		|required	|URL to display the picture.|
|height	|`picture`	|integer	|required	|Height of the picture.|
|width	|`picture`	|integer	|required	|Width of the picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to create a sports league.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{SportsServer}}/sports/v1/leagues
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
    "name": "Premier League",
    "sportID": "ea3c8187-0f9f-4f75-b947-cc5762765546",
    "picture": {
        "pictureID": "e25c328f-7ad9-4c75-a225-e55a0902acbd",
        "url": "http://a1.espncdn.com/combiner/i?img=%2Fi%2Fleaguelogos%2Fsoccer%2F500%2F23.png",
        "height": 500,
        "width": 500,
        "type": "logo"
    },
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Create league | Code: 0



```js
{
    "requestId": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "leagues": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "PAC-12",
            "sportID": "12345678-1234-5678-9012-deadbeef1234"
        }
    ],
    "picture": {
        "pictureID": "12341234-dead-beef-9992-deadbeef1234",
        "url": "https://images.com/img123",
        "height": 1024,
        "width": 1920,
        "type": "banner"
    }
}
```



### Update league

Updates information for the specified league.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|leagueID |string |required	|ID for the target league to be updated.|

<br/>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|name	|	|string	|required	|Name of the league.|
|sportID|	|string	|required	|Generated ID for the sport this league plays.|
|`picture`	|		|object	|optional	|Picture for the league.|
|pictureID	|`picture`	|string	|required	|Generated ID for the picture.|
|url	|`picture`	|string		|required	|URL to display the picture.|
|height	|`picture`	|integer	|required	|Height of the picture.|
|width	|`picture`	|integer	|required	|Width of the picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target league.|
|404		|1040	|*Not Found*: Target league not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{SportsServer}}/sports/v1/leagues/{{leagueID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Body:***

```js        
{
    "name": "Premier League",
    "sportID": "ea3c8187-0f9f-4f75-b947-cc5762765546",
    "picture": {
        "pictureID": "e25c328f-7ad9-4c75-a225-e55a0902acbd",
        "url": "http://a1.espncdn.com/combiner/i?img=%2Fi%2Fleaguelogos%2Fsoccer%2F500%2F23.png",
        "height": 500,
        "width": 500,
        "type": "logo"
    },
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Update league | Code: 0



```js
{
    "requestId": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "leagues": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "PAC-12",
            "sportID": "12345678-1234-5678-9012-deadbeef1234"
        }
    ],
    "picture": {
        "pictureID": "12341234-dead-beef-9992-deadbeef1234",
        "url": "https://images.com/img123",
        "height": 1024,
        "width": 1920,
        "type": "banner"
    }
}
```



### Retrieve league

Retrieves content for the specified league.

All query parameters are optional unless otherwise indicated.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|leagueID |string |required	|ID for the target league to be viewed.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target league.|
|404		|1040	|*Not Found*: Target league not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/leagues/{{leagueID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Accept | application/json |  |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| include | teams,sports | Optionally fetches related *teams* and *sports* when specified. |



***Responses:***


Status: Get league | Code: 0



```js
{
    "requestId": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "leagues": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "PAC-12",
            "sportID": "12345678-1234-5678-9012-deadbeef1234",
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### List leagues

Lists all leagues that match the query specification sorted by name.

All query parameters are optional unless otherwise indicated.

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target content.|
|404		|1040	|*Not Found*: Target sport not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/leagues/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Accept | application/json |  |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| sportID | {{sportID}} | ID of the desired sport to list leagues for. |
| query |  | Query string to search for within the league name. |
| include | teams | Optionally fetches related entities [*teams, sports*] when specified. |
| count | 25 | Maximum number of results returned per call. Default is 50. |
| offset | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |



***Responses:***


Status: List leagues | Code: 0



```js
{
    "requestId": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata":
    {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "leagues": [
    {
        "id": "deadbeef-1234-5678-9012-deadbeef1234",
        "source": {
            "name" : "GraceNote",
            "id" : "87654321-4321-4321-098765432100"
        },
        "name": "PAC-12",
        "sportID": "12345678-1234-5678-9012-deadbeef1234",
        "picture":{
            "pictureID": "12341234-dead-beef-9992-deadbeef1234",
            "url": "https://images.com/img123",
            "height": 1024,
            "width": 1920,
            "type": "banner"
        }
    }
    ]
}
```



### Delete league

Deletes the specified league.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|leagueID |string |required	|ID for the target league to be deleted.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target league.|
|404		|1040	|*Not Found*: Target league not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{SportsServer}}/sports/v1/leagues/{{leagueID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



## Players



### Create player

Creates a player.

<br>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|firstName	|	|string	|required	|Player's first name.|
|lastName	|	|string	|required	|Player's last name.|
|gender		|	|string	|required	|Player's gender.|
|`height`	|	|object	|required	|Player's height measurement; must specify either *inches* or *cm*.|
|inches	|`height`	|integer	|optional	|Player's height in inches.|
|cm		|`height`	|integer	|optional	|Player's height in centimeters.|
|`weight`	|	|object	|required	|Player's weight measurement; must specify either *pounds* or *kg*.|
|pounds	|`weight`	|integer	|optional	|Player's weight in pounds.|
|kg		|`weight`	|integer	|optional	|Player's weight in kilograms.|
|birthplace	|	|string	|required	|Player's location--city, state/province, country.|
|`picture`	|		|object	|optional	|Picture of the player.|
|pictureID	|`picture`	|string	|required	|Generated ID for the player's picture.|
|url	|`picture`	|string		|required	|URL to display the player's picture.|
|height	|`picture`	|integer	|required	|Height of the player's picture.|
|width	|`picture`	|integer	|required	|Width of the player's picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to create a player.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{SportsServer}}/sports/v1/players
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
    "firstName": "Victor",
    "lastName": "Moses",
    "gender": "Male",
    "height": {
        "inches": 70
    },
    "weight": {
        "pounds": 168
    },
    "birthplace": "Kaduna, Nigeria",
    "picture": {
        "pictureID": "fa94abdf-2e02-4097-918e-68d50b1be636",
        "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/FWC_2018_-_Group_D_-_NGA_v_ISL_-_Photo_38_%28cropped%29.jpg/220px-FWC_2018_-_Group_D_-_NGA_v_ISL_-_Photo_38_%28cropped%29.jpg",
        "height": 346,
        "width": 220,
        "type": "portrait"
    },
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Create player | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "players": [
        {
            "id": "11223344-3333-4444-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "firstName": "Russell",
            "lastName": "Wilson",
            "gender": "Male",
            "height": {
                "inches": 71,
                "millimeters": 1803
            },
            "weight": {
                "pounds": 206,
                "grams": 93440
            },
            "birthplace": "Cincinnati, Ohio",
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### Update player

Updates information for the specified player.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|playerID |string |required	|ID for the target player to be updated.|

<br/>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|firstName	|	|string	|required	|Player's first name.|
|lastName	|	|string	|required	|Player's last name.|
|gender		|	|string	|required	|Player's gender.|
|`height`	|	|object	|required	|Player's height measurement; must specify either *inches* or *cm*.|
|inches	|`height`	|integer	|optional	|Player's height in inches.|
|cm		|`height`	|integer	|optional	|Player's height in centimeters.|
|`weight`	|	|object	|required	|Player's weight measurement; must specify either *pounds* or *kg*.|
|pounds	|`weight`	|integer	|optional	|Player's weight in pounds.|
|kg		|`weight`	|integer	|optional	|Player's weight in kilograms.|
|birthplace	|	|string	|required	|Player's location--city, state/province, country.|
|`picture`	|		|object	|optional	|Picture of the player.|
|pictureID	|`picture`	|string	|required	|Generated ID for the player's picture.|
|url	|`picture`	|string		|required	|URL to display the player's picture.|
|height	|`picture`	|integer	|required	|Height of the player's picture.|
|width	|`picture`	|integer	|required	|Width of the player's picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target player.|
|404		|1040	|*Not Found*: Target player not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{SportsServer}}/sports/v1/players/{{playerID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Body:***

```js        
{
    "firstName": "Victor",
    "lastName": "Moses",
    "gender": "Male",
    "height": {
        "inches": 70
    },
    "weight": {
        "pounds": 168
    },
    "birthplace": "Kaduna, Nigeria",
    "picture": {
        "pictureID": "fa94abdf-2e02-4097-918e-68d50b1be636",
        "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/FWC_2018_-_Group_D_-_NGA_v_ISL_-_Photo_38_%28cropped%29.jpg/220px-FWC_2018_-_Group_D_-_NGA_v_ISL_-_Photo_38_%28cropped%29.jpg",
        "height": 346,
        "width": 220,
        "type": "portrait"
    },
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Update player | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "players": [
        {
            "id": "11223344-3333-4444-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "firstName": "Russell",
            "lastName": "Wilson",
            "gender": "Male",
            "height": {
                "inches": 71,
                "millimeters": 1803
            },
            "weight": {
                "pounds": 206,
                "grams": 93440
            },
            "birthplace": "Cincinnati, Ohio",
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### Retrieve player

Retrieves the specified player.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|playerID |string |required	|ID for the target player to be viewed.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target player.|
|404		|1040	|*Not Found*: Target player not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/players/{{playerID}}/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Accept | application/json |  |
| Content-Type | application/json |  |



***Responses:***


Status: Get player | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata":
    {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "players": 
    [
    	{
        "id": "11223344-3333-4444-9012-deadbeef1234",
        "source": {
            "name" : "GraceNote",
            "id" : "87654321-4321-4321-098765432100"
        },
        "firstName": "Russell",
        "lastName": "Wilson",
        "gender": "Male",
        "height": {
            "inches": 71,
            "millimeters": 1803
        },
        "weight": {
            "pounds": 206,
            "grams": 93440
        },
        "birthplace": "Cincinnati, Ohio",
        "picture":{
            "pictureID": "12341234-dead-beef-9992-deadbeef1234",
            "url": "https://images.com/img123",
            "height": 1024,
            "width": 1920,
            "type": "banner"
            } 
    		
    	}
    ]
}
```



### List players

Lists all players that match the query specification sorted by player name.

All query parameters are optional unless otherwise indicated.

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target content.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/players/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Accept | application/json |  |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| count | 25 | Maximum number of results returned per call. Default is 50. |
| offset | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |
| query | Duran | Query string matched against the first and last names of the players. |



### Delete player

Deletes the specified player.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|playerID |string |required	|ID for the target player to be deleted.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target player.|
|404		|1040	|*Not Found*: Target player not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{SportsServer}}/sports/v1/players/{{playerID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



## Scores



### Create score

Creates a game score.

<br/>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|gameID	|	|string	|required	|ID for the target game.|
|teamID	|	|string	|required	|ID for the target team.|
|points	|		|integer|required	|Current total points for this team in this game.|
|position	|	|integer|optional	|Current team position.|
|clock	|		|string	|required	|Current amount of time remaining on the game clock.|
|timestampUTC	|	|string	|required	|Current time in ISO-8601 format.|
|periodNumber	|	|integer|optional	|Game period--the current half or quarter.|
|periodType	|	|string	|optional	|Type of period--regular or overtime.|
|possession	|	|string	|optional	|Team's percentage of time in control of the ball or puck.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to create a game score.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{SportsServer}}/sports/v1/scores
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
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    },
    "gameID": "12345678-1234-5678-9012-deadbeef1234",
    "teamID": "12345678-1234-5678-9012-deadbeef1239",
    "points": 7,
    "position": 1,
    "clock": "10:00",
    "timestampUTC": "2018-11-20T15:00:00.000Z",
    "periodNumber": 1,
    "periodType": "regular",
    "possession": "60%"
}
```



***Responses:***


Status: Create score | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "scores": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "gameID": "12345678-1234-5678-9012-deadbeef1234",
            "home": 36,
            "away": 7,
            "clock": "PTmmMss.ccS",
            "timestampUTC": "2018-10-08T18:34:10+00:00",
            "periodNumber": 1,
            "periodType": "REGULAR",
            "possession": "deadbeef-4321-5678-9012-deadbeef1234"
        }
    ]
}
```



### Update score

Updates information for the specified game score.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|scoreID |string |required	|ID for the target score to be updated.|

<br/>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|gameID	|	|string	|required	|ID for the target game.|
|teamID	|	|string	|required	|ID for the target team.|
|points	|		|integer|required	|Current total points for this team in this game.|
|position	|	|integer|optional	|Current team position.|
|clock	|		|string	|required	|Current amount of time remaining on the game clock.|
|timestampUTC	|	|string	|required	|Current time in ISO-8601 format.|
|periodNumber	|	|integer|optional	|Game period--the current half or quarter.|
|periodType	|	|string	|optional	|Type of period--regular or overtime.|
|possession	|	|string	|optional	|Team's percentage of time in control of the ball or puck.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target score.|
|404		|1040	|*Not Found*: Target score not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{SportsServer}}/sports/v1/scores/{{scoreID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Body:***

```js        
{
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    },
    "gameID": "12345678-1234-5678-9012-deadbeef1234",
    "teamID": "12345678-1234-5678-9012-deadbeef1239",
    "points": 7,
    "position": 1,
    "clock": "10:00",
    "timestampUTC": "2018-11-20T15:00:00.000Z",
    "periodNumber": 1,
    "periodType": "regular",
    "possession": "60%"
}
```



***Responses:***


Status: Update score | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "scores": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "gameID": "12345678-1234-5678-9012-deadbeef1234",
            "home": 36,
            "away": 7,
            "clock": "PTmmMss.ccS",
            "timestampUTC": "2018-10-08T18:34:10+00:00",
            "periodNumber": 1,
            "periodType": "REGULAR",
            "possession": "deadbeef-4321-5678-9012-deadbeef1234"
        }
    ]
}
```



### Retrieve score

Retrieves the specified game score.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|scoreID |string |required	|ID for the target score to be viewed.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target score.|
|404		|1040	|*Not Found*: Target score not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/scores/{{scoreID}}/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Responses:***


Status: Get score | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "scores": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "gameID": "12345678-1234-5678-9012-deadbeef1234",
            "teamID": "deadbeef-4321-5678-9012-deadbeef1234",
            "points": 36,
            "clock": "PTmmMss.ccS",
            "timestampUTC": "2018-10-08T18:34:10+00:00",
            "periodNumber": 1,
            "periodType": "REGULAR",
            "possession": "deadbeef-4321-5678-9012-deadbeef1234"
        }
    ]
}
```



### List scores

Lists all scores for the specified game. If no GameID is specified, scores are listed without any particular context.

All query parameters are optional unless otherwise indicated.

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target game.|
|404		|1040	|*Not Found*: Target game not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/scores/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| GameID | {{gameID}} | ID of the desired game to list scores for. *Required*. |



***Responses:***


Status: List scores | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "scores": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "gameID": "12345678-1234-5678-9012-deadbeef1234",
            "teamID": "deadbeef-4321-5678-9012-deadbeef1234",
            "points": 36,
            "clock": "PTmmMss.ccS",
            "timestampUTC": "2018-10-08T18:34:10+00:00",
            "periodNumber": 1,
            "periodType": "REGULAR",
            "possession": "deadbeef-4321-5678-9012-deadbeef1234"
        }
    ]
}
```



### Delete score

Deletes the specified score.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|scoreID|string |required	|ID for the target score to be deleted.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target score.|
|404		|1040	|*Not Found*: Target score not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{SportsServer}}/sports/v1/scores/{{scoreID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |




## Sport Types

### Create sport

Creates a sport.

<br>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|name	|	|string	|required	|Name of the sport.|
|`picture`	|		|object	|optional	|Picture for the sport.|
|pictureID	|`picture`	|string	|required	|Generated ID for the picture.|
|url	|`picture`	|string		|required	|URL to display the picture.|
|height	|`picture`	|integer	|required	|Height of the picture.|
|width	|`picture`	|integer	|required	|Width of the picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to create a sport.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{SportsServer}}/sports/v1/sports
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
    "name": "Football",
    "picture": {
        "pictureID": "7f5c3689-9b53-4125-8887-a91f0bc68d61",
        "url": "https://blog.oxforddictionaries.com/wp-content/uploads/football-1-1200x330.jpg",
        "height": 330,
        "width": 1222,
        "type": "portrait"
    },
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Create sport | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "sports": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "Football (American)",
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### Update sport

Updates information for the specified sport.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|sportID |string |required	|ID for the target sport to be updated.|

<br/>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|name	|	|string	|required	|Name of the sport.|
|`picture`	|		|object	|optional	|Picture for the sport.|
|pictureID	|`picture`	|string	|required	|Generated ID for the picture.|
|url	|`picture`	|string		|required	|URL to display the picture.|
|height	|`picture`	|integer	|required	|Height of the picture.|
|width	|`picture`	|integer	|required	|Width of the picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target sport.|
|404		|1040	|*Not Found*: Target sport not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{SportsServer}}/sports/v1/sports/{{sportID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Body:***

```js        
{
    "name": "Football",
    "picture": {
        "pictureID": "7f5c3689-9b53-4125-8887-a91f0bc68d61",
        "url": "https://blog.oxforddictionaries.com/wp-content/uploads/football-1-1200x330.jpg",
        "height": 330,
        "width": 1222,
        "type": "portrait"
    },
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Update sport | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "sports": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "Football (American)",
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### Retrieve sport

Retrieves information for the specified sport.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|sportID |string |required	|ID for the target sport content to be viewed.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target sport content.|
|404		|1040	|*Not Found*: Target sport not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/sports/{{sportID}}/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Responses:***


Status: Get sport | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "teams": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "University of Washington Huskies",
            "abbreviation": "UW",
            "city": "Seattle, WA",
            "players": [
                {
                    "playerID": "11223344-3333-4444-9012-deadbeef1234",
                    "firstName": "Russel",
                    "lastName": "Wilson"
                }
            ],
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### List sports

Lists all sports that match the query specification sorted by name.

All query parameters are optional unless otherwise indicated.

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target content.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/sports/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{sessiontoken}} |  |
| Accept | application/json |  |
| Content-Type | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| count | 25 | Maximum number of results returned per call. Default is 50. |
| offset | 0 | Number of items to skip at the start of the returned result set; used for pagination. Default is 0. |
| query | foot | Query string to search for within the sport name. |



***Responses:***


Status: List sports | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "sports": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "Football (American)",
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### Delete sport

Deletes the specified sport.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|sportID |string |required	|ID for the target sport to be deleted.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target sport.|
|404		|1040	|*Not Found*: Target sport not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{SportsServer}}/sports/v1/sports/{{sportID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |



## Teams

### Create team

Creates a sports team.

<br>

#### Body Parameters
|Field		|Parent |Type	|Required	|Description	|
|---		|---	|---	|---		|---			|
|name		|	|string	|required	|Name of the sports team.|
|abbreviation|	|string	|required	|Abbreviation for the sports team name.|
|city		|	|string	|required	|Team's home location--city, district/province/state, and country.|
|`players`	|	|list	|optional	|List of players on the team.|
|playerID	|`players`	|string	|required	|Player's ID.|
|firstName	|`players`	|string	|required	|Player's first name.|
|lastName	|`players`	|string	|required	|Player's last name.|
|`picture`	|		|object	|optional	|Picture of the player.|
|pictureID	|`picture`	|string	|required	|Generated ID for the player's picture.|
|url	|`picture`	|string		|required	|URL to display the player's picture.|
|height	|`picture`	|integer	|required	|Height of the player's picture.|
|width	|`picture`	|integer	|required	|Width of the player's picture.|
|type	|`picture`	|string		|required	|Picture orientation description. Possible choices include *portrait*, *logo*, *banner*, etc.|
|`source`	|		|object	|optional	|Source of the picture.|
|name	|`source`	|string	|optional	|Name of the picture source.|
|id		|`source`	|string	|optional	|ID for the picture source.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|400		|1050	|*Bad request*: Malformed request body.|
|403		|1004	|*Forbidden*: Caller not authorized to create a team.|

<br/>


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{SportsServer}}/sports/v1/teams
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
    "name": "Arsenal Football Club",
    "abbreviation": "Arsenal F.C.",
    "city": "Islington, London, England",
    "players": [
        {
            "playerID": "b8ac9aed-008d-43eb-95f9-1de9a6813285",
            "firstName": "Henrikh",
            "lastName": "Mkhitaryan"
        },
        {
            "playerID": "c6c4b479-64e1-420d-9394-d74fbbd21380",
            "firstName": "Eddie",
            "lastName": "Nketiah"
        },
        {
            "playerID": "42283f0f-b6ae-4e0e-a7cc-dced1acf24b7",
            "firstName": "Robert",
            "lastName": "Holding"
        }
    ],
    "picture": {
        "pictureID": "944e68e7-7146-406c-ac8d-df379c894d86",
        "url": "https://en.wikipedia.org/wiki/Arsenal_F.C.#/media/File:Arsenal_FC.svg",
        "height": 1410,
        "width": 1200,
        "type": "logo"
    },
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Create team | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "teams": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "University of Washington Huskies",
            "abbreviation": "UW",
            "city": "Seattle, WA",
            "players": [
                {
                    "playerID": "11223344-3333-4444-9012-deadbeef1234",
                    "firstName": "Russel",
                    "lastName": "Wilson"
                }
            ],
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### Update team

Updates information for the specified team.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|teamID |string |required	|ID for the target team to be updated.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to write or update the target team.|
|404		|1040	|*Not Found*: Target team not found.|

<br/>


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{SportsServer}}/sports/v1/teams/{{teamID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Body:***

```js        
{
    "name": "Arsenal Football Club",
    "abbreviation": "Arsenal F.C.",
    "city": "Islington, London, England",
    "players": [
        {
            "playerID": "b8ac9aed-008d-43eb-95f9-1de9a6813285",
            "firstName": "Henrikh",
            "lastName": "Mkhitaryan"
        },
        {
            "playerID": "c6c4b479-64e1-420d-9394-d74fbbd21380",
            "firstName": "Eddie",
            "lastName": "Nketiah"
        },
        {
            "playerID": "42283f0f-b6ae-4e0e-a7cc-dced1acf24b7",
            "firstName": "Robert",
            "lastName": "Holding"
        }
    ],
    "picture": {
        "pictureID": "944e68e7-7146-406c-ac8d-df379c894d86",
        "url": "https://en.wikipedia.org/wiki/Arsenal_F.C.#/media/File:Arsenal_FC.svg",
        "height": 1410,
        "width": 1200,
        "type": "logo"
    },
    "source": {
        "name": "DIRECTINSERT",
        "id": "-1"
    }
}
```



***Responses:***


Status: Update team | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "teams": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "University of Washington Huskies",
            "abbreviation": "UW",
            "city": "Seattle, WA",
            "players": [
                {
                    "playerID": "11223344-3333-4444-9012-deadbeef1234",
                    "firstName": "Russel",
                    "lastName": "Wilson"
                }
            ],
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### Retrieve team

Retrieves content for the specified team.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|teamID |string |required	|ID for the target sports team to be viewed.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target sports team.|
|404		|1040	|*Not Found*: Target sports team not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/teams/{{teamID}}/
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Responses:***


Status: Get team | Code: 0



```js
{
    "requestID": "abcdef01-abcd-def01-2345-01234567789abcd",
    "timestamp": "2018-01-01T12:00:00.353226Z",
    "metadata": {
        "count": 1,
        "totalCount": 1,
        "offset": 0
    },
    "teams": [
        {
            "id": "deadbeef-1234-5678-9012-deadbeef1234",
            "source": {
                "name": "GraceNote",
                "id": "87654321-4321-4321-098765432100"
            },
            "name": "University of Washington Huskies",
            "abbreviation": "UW",
            "city": "Seattle, WA",
            "players": [
                {
                    "playerID": "11223344-3333-4444-9012-deadbeef1234",
                    "firstName": "Russel",
                    "lastName": "Wilson"
                }
            ],
            "picture": {
                "pictureID": "12341234-dead-beef-9992-deadbeef1234",
                "url": "https://images.com/img123",
                "height": 1024,
                "width": 1920,
                "type": "banner"
            }
        }
    ]
}
```



### List teams

Lists all teams matching the query specification.

All query parameters are optional unless otherwise indicated.

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to view the target content.|
|404		|1040	|*Not Found*: Target content not found.|

<br/>


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{SportsServer}}/sports/v1/teams
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| include | players |  |



### Delete team

Deletes the specified team.

<br/>

#### Path Parameters
|Label	|Type	|Required	|Description|
|---	|---	|---		|---		|
|teamID |string |required	|ID for the target team to be deleted.|

<br/>

#### Error Responses
|HTTP Code	|Error	|Description|
|---		|---	|---		|
|403		|1004	|*Forbidden*: Caller not authorized to delete the target team.|
|404		|1040	|*Not Found*: Target team not found.|

<br/>


***Endpoint:***

```bash
Method: DELETE
Type: RAW
URL: {{SportsServer}}/sports/v1/teams/{{teamID}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Accept | application/json |  |
| Content-Type | application/json |  |
| Authorization | Bearer {{sessiontoken}} | Requires the user's session token to authenticate the request. |

---

[Back to top](api-sports)
