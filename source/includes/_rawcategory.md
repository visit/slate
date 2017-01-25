# Raw Category

> Raw Category

```json
{
  "Id": 30701,
  "Name": "Thibault",
  "Translations": {
    "sv-SE": "Thibault",
    "en-US": "Thibault"
  },
  "Path": [
    5946,
    30701
  ]
}
```

All the categories in use in CBIS for the organization owning the API key, with your own translations as well.

## Get Category

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/category/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/category/{id}",
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

Get a specific category and all its translations.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/category/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | The category id.

## Get Paged

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/category/getpaged/{pageSize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/category/getpaged/{pageSize}",
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

Get a page of raw categories.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/category/getpaged/{pageSize}`

### Query Parameters

Parameter | Description
--------- | -----------
pageSize | Should be a page size lower than 50 and greater than 0.


<aside class="notice">
Use the <a href="https://visit.github.io/api-doc/#continue20">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Continue

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/category/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/category/getnext/{continueToken}",
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
  "ContinueToken": "c2NhbjswOzE7dG90YWxfaGl0czoxMTs=",
  "TotalResults": 11,
  "Result": [
    {
      "Id": 5946,
      "Name": "Visit Group",
      "Translations": {
        "sv-SE": "Visit Group",
        "en-US": "Visit Group",
        "es-ES": "Visit Group"
      },
      "Path": [
        5946
      ]
    },
    {
      "Id": 26210,
      "Name": "Boende",
      "Translations": {
        "sv-SE": "Boende",
        "en-US": "Boende",
        "es-ES": "Hospedaje"
      },
      "Path": [
        5946,
        26210
      ]
    },
    {
      "Id": 26219,
      "Name": "b&b",
      "Translations": {
        "sv-SE": "b&b",
        "en-US": "b&b",
        "es-ES": "B&B"
      },
      "Path": [
        5946,
        26210,
        26219
      ]
    }
  ]
}
```

Get the next page of raw categories, you need to provide a token obtained from <a href="https://visit.github.io/api-doc/#get-paged19">Get Paged</a>.
Tokens are valid for 1 minute, extended for aonother minute each time you use it.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/category/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | A token to retrieve the next page.


<aside class="notice">
Use the <a href="https://visit.github.io/api-doc/#continue20">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Search Categories

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/category/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/category/search/{search}",
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
    "Id": 30701,
    "Name": "Thibault",
    "Translations": {
      "sv-SE": "Thibault",
      "en-US": "Thibault"
    },
    "Path": [
      5946,
      30701
    ]
  }
]
```

Search for a match or more in categories translations.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/category/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string you are looking for.