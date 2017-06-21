# Language

## Get Languages

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/language'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/language",
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
  "en-us",
  "fr-fr",
  "sv-se"
]
```

Get the available languages for the key.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/language`

### Query Parameters

None

## Check If Available

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/language/{culture}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/language/{culture}",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
true
```

Returns true if culture is available, false otherwise.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/language/{culture}`

### Query Parameters

Parameter | Description
--------- | -----------
culture | The culture to look for.