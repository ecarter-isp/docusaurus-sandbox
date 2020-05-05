---
id: test-output
title: epgManifest v1.0
---


> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Provides a manifest of resources that are needed to build out an Electronic Program Guide (EPG). This API requires:
* authenticated access
* geographic context for the user.

Base URLs:

* <a href="https://{{orbisEndpoint}}">https://{{orbisEndpoint}}</a>

Email: <a href="mailto:api@istreamplanet.com">iStreamPlanet</a> Web: <a href="https://api.istreamplanet.com">iStreamPlanet</a> 

## Authentication

* API Key (customerApiKey)
    - Parameter Name: **API Key**, in: header. The Orbis API key of the customer that the account belongs to.

## Default

### get-epg-epgManifest

<a id="opIdget-epg-epgManifest"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://{{orbisEndpoint}}/epg/epgManifest \
  -H 'Accept: application/vnd.istreamplanet.epgmanifest+json;version=1.0' \
  -H 'Accept: application/vnd.istreamplanet.epgmanifest+json;version=1.0' \
  -H 'API Key: API_KEY'

```

```http
GET https://{{orbisEndpoint}}/epg/epgManifest HTTP/1.1

Accept: application/vnd.istreamplanet.epgmanifest+json;version=1.0
Accept: application/vnd.istreamplanet.epgmanifest+json;version=1.0

```

```javascript

const headers = {
  'Accept':'application/vnd.istreamplanet.epgmanifest+json;version=1.0',
  'Accept':'application/vnd.istreamplanet.epgmanifest+json;version=1.0',
  'API Key':'API_KEY'
};

fetch('https://{{orbisEndpoint}}/epg/epgManifest',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.istreamplanet.epgmanifest+json;version=1.0',
  'Accept' => 'application/vnd.istreamplanet.epgmanifest+json;version=1.0',
  'API Key' => 'API_KEY'
}

result = RestClient.get 'https://{{orbisEndpoint}}/epg/epgManifest',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/vnd.istreamplanet.epgmanifest+json;version=1.0',
  'Accept': 'application/vnd.istreamplanet.epgmanifest+json;version=1.0',
  'API Key': 'API_KEY'
}

r = requests.get('https://{{orbisEndpoint}}/epg/epgManifest', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/vnd.istreamplanet.epgmanifest+json;version=1.0',
    'Accept' => 'application/vnd.istreamplanet.epgmanifest+json;version=1.0',
    'API Key' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://{{orbisEndpoint}}/epg/epgManifest', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://{{orbisEndpoint}}/epg/epgManifest");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.istreamplanet.epgmanifest+json;version=1.0"},
        "Accept": []string{"application/vnd.istreamplanet.epgmanifest+json;version=1.0"},
        "API Key": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://{{orbisEndpoint}}/epg/epgManifest", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /epg/epgManifest`

*Retrieve EPG resources for a user account*

Requests the information describing the resources for an account Electronic Program Guide (EPG). A successful GET request returns a resource listing the channel fragments (if any) that are in their content. The resource listing document is called an "EPG Manifest" and reflects the EPG components, if any, that an authenticated user has available to them. Note that depending on business rules, this may return no items.

The user-agent may use the returned epgFragments to request resources that build an EPG rendering.

*Requirements:*

* An authenticated session.

*Interaction:*

Uses the geographic information in the users token to ensure that a lineup is correct for their location, including blackout information.

#### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|Accept|header|string|false|Allows versioning support|

> Example responses

> 200 Response

```json
{
  "manifestId": "f2e5ad45-331f-4c08-8b1a-f5876b4dc52f",
  "epgFragments": [
    {
      "uri": "http://example.com",
      "utcStartDateTime": "string"
    }
  ],
  "epgMetadata": [
    {
      "channelPictureId": "string",
      "channelName": "string",
      "channelId": "string"
    }
  ]
}
```


#### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|



#### Response Schema

Status Code **200**

*https://istreamplanet.com/schemas/public/epgmanifest.v1.json*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» manifestId|string(uuid)|true|none|none|
|» epgFragments|[object]|false|none|An optional array of URIs pointing to valid fragments of an EPG.|
|»» uri|string(uri)|false|none|none|
|»» utcStartDateTime|string|false|none|none|
|» epgMetadata|[object]|false|none|An optional array of metadata related to the EPG|
|»» channelPictureId|string|false|none|URI of a picture for the channel if available|
|»» channelName|string|false|none|Name of the channel|
|»» channelId|string|false|none|Name of the Channel|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
customerApiKey
</aside>

