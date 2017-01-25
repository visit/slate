# Raw POI

> Raw POI

```json
{
  "Id": 16,
  "Name": "Leksand",
  "Translation": {
    "sv-SE": "Leksand"
  },
  "Position": {
    "Longitude": 15.0032043457031,
    "Latitude": 60.7338905334473
  }
}
```

All the POIs in use in CBIS for the organization owning the API key, with your own translations as well.

## Get POI

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/poi/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/poi/{id}",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
{
  "Id": 16,
  "Name": "Leksand",
  "Translation": {
    "sv-SE": "Leksand"
  },
  "Position": {
    "Longitude": 15.0032043457031,
    "Latitude": 60.7338905334473
  }
}
```

Get a specific POI and all its translations.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/poi/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | The POI id.

## Get Paged

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getpaged/{pageSize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getpaged/{pageSize}",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
{
  "ContinueToken": "c2NhbjsxOzY4MDQwODYxOkM2a0hnTFpmUUVLeHNlSUhoc0d5clE7MTt0b3RhbF9oaXRzOjI4NzQ7",
  "TotalResults": 2874,
  "Result": [
    {
      "Id": 100566,
      "Translations": {
        "sv-SE": "Bowling",
        "en-US": "Bowling"
      },
      "Name": "bowling",
      "Type": "Boolean"
    },
    {
      "Id": 100567,
      "Translations": {
        "sv-SE": "Cykel till förfogande",
        "en-US": "Bikes available"
      },
      "Name": "cykel",
      "Type": "Boolean"
    }
  ]
}
```

Get a page of raw POIs.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getpaged/{pageSize}`

### Query Parameters

Parameter | Description
--------- | -----------
pageSize | Should be a page size lower than 50 and greater than 0.


<aside class="notice">
Use the <a href="https://visit.github.io/api-doc/#continue10">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Continue

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getnext/{continueToken}",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
{
  "ContinueToken": "c2NhbjswOzE7dG90YWxfaGl0czo2Ow==",
  "TotalResults": 6,
  "Result": [
    {
      "Id": 18,
      "Name": "Borlänge (Dala Airport)",
      "Translation": {
        "sv-SE": "Borlänge (Dala Airport)"
      },
      "Position": {
        "Longitude": 15.5104637145996,
        "Latitude": 60.4233436584473
      }
    },
    {
      "Id": 8133,
      "Name": "WEQWEQWEQWE",
      "Translation": {
        "en-US": "WEQWEQWEQWE"
      },
      "Position": {
        "Longitude": 15.2551183700562,
        "Latitude": 54.5259628295898
      }
    },
    {
      "Id": 8305,
      "Name": "Inlandsbanan",
      "Translation": {
        "sv-SE": "Inlandsbanan"
      },
      "Position": {
        "Longitude": 16.2033634185791,
        "Latitude": 64.113899230957
      }
    }
  ]
}
```

Get the next page of raw POIs, you need to provide a token obtained from <a href="https://visit.github.io/api-doc/#get-paged9">Get Paged</a>.
Tokens are valid for 1 minute, extended for aonother minute each time you use it.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | A token to retrieve the next page.


<aside class="notice">
Use the <a href="https://visit.github.io/api-doc/#continue10">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Search POIs

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/poi/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/poi/search/{search}",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
[
  {
    "Id": 18,
    "Name": "Borlänge (Dala Airport)",
    "Translation": {
      "sv-SE": "Borlänge (Dala Airport)"
    },
    "Position": {
      "Longitude": 15.5104637145996,
      "Latitude": 60.4233436584473
    }
  }
]
```

Search for a match or more in POIs translations.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/poi/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string you are looking for.