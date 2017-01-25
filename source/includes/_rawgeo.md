# Raw Geo

> Raw Geo

```json
{
  "Id": 83745,
  "Name": "Göteborg",
  "Translations": {
    "sv-SE": "Göteborg",
    "en-US": "Gothenburg",
    "es-ES": "Gotemburgo"
  },
  "Path": [
    4852,
    105375,
    83745
  ]
}
```

All the geos in use in CBIS for the organization owning the API key, with your own translations as well.

## Get Geo

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/geo/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/geo/{id}",
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
  "Id": 83745,
  "Name": "Göteborg",
  "Translations": {
    "sv-SE": "Göteborg",
    "en-US": "Gothenburg",
    "es-ES": "Gotemburgo"
  },
  "Path": [
    4852,
    105375,
    83745
  ]
}
```

Get a specific geo and all its translations.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/geo/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | The geo id.

## Get Paged

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getpaged/{pageSize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getpaged/{pageSize}",
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
      "Id": 4852,
      "Name": "[Visit Group]",
      "Translations": {},
      "Path": [
        4852
      ]
    },
    {
      "Id": 105375,
      "Name": "Sverige",
      "Translations": {
        "sv-SE": "Sverige",
        "en-US": "Sweden",
        "es-ES": "Suecia"
      },
      "Path": [
        4852,
        105375
      ]
    },
    {
      "Id": 83745,
      "Name": "Göteborg",
      "Translations": {
        "sv-SE": "Göteborg",
        "en-US": "Gothenburg",
        "es-ES": "Gotemburgo"
      },
      "Path": [
        4852,
        105375,
        83745
      ]
    }
  ]
}
```

Get a page of raw geos.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getpaged/{pageSize}`

### Query Parameters

Parameter | Description
--------- | -----------
pageSize | Should be a page size lower than 50 and greater than 0.


<aside class="notice">
Use the <a href="https://visit.github.io/api-doc/#continue15">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Continue

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getnext/{continueToken}",
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
      "Id": 4852,
      "Name": "[Visit Group]",
      "Translations": {},
      "Path": [
        4852
      ]
    },
    {
      "Id": 105375,
      "Name": "Sverige",
      "Translations": {
        "sv-SE": "Sverige",
        "en-US": "Sweden",
        "es-ES": "Suecia"
      },
      "Path": [
        4852,
        105375
      ]
    },
    {
      "Id": 83745,
      "Name": "Göteborg",
      "Translations": {
        "sv-SE": "Göteborg",
        "en-US": "Gothenburg",
        "es-ES": "Gotemburgo"
      },
      "Path": [
        4852,
        105375,
        83745
      ]
    }
  ]
}
```

Get the next page of raw geos, you need to provide a token obtained from <a href="https://visit.github.io/api-doc/#get-paged14">Get Paged</a>.
Tokens are valid for 1 minute, extended for aonother minute each time you use it.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/raw/geo/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | A token to retrieve the next page.


<aside class="notice">
Use the <a href="https://visit.github.io/api-doc/#continue15">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Search Geos

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/geo/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/geo/search/{search}",
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
    "Id": 83745,
    "Name": "Göteborg",
    "Translations": {
      "sv-SE": "Göteborg",
	  "en-US": "Gothenburg",
	  "es-ES": "Gotemburgo"
    },
    "Path": [
	  4852,
	  105375,
	  83745
    ]
  }
]
```

Search for a match or more in geos translations.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/geo/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string you are looking for.