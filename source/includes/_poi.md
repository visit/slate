# POI

> POI 

```json
{
  "Position": {
    "Longitude": 15.2551183700562,
    "Latitude": 54.5259628295898
  },
  "Name": "WEQWEQWEQWE",
  "Id": 8133
}
```

Localized version of the POI for the organization owning the API key.

<aside class="notice">
The header <code>Accept-Language</code> is used to know which language to query. It uses <a href="https://msdn.microsoft.com/en-us/library/ee825488(v=cs.20).aspx">CultureInfo code</a>.
</aside>


## Get POI

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/poi/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/poi/{id}",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US"
  }  
});
```

> Example of response:

```json
{
  "Position": {
    "Longitude": 15.2551183700562,
    "Latitude": 54.5259628295898
  },
  "Name": "WEQWEQWEQWE",
  "Id": 8133
}
```

Get a specific POI in the specified language.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/poi/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | The POI id.
Accept-Language | The language.

## Get POIs

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: sv-SE'
  'https://cbis-rest-api.citybreak.com/v1/api/poi'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/poi",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "sv-SE"
  }  
});
```

> Example of response:

```json
[
  {
    "Position": {
      "Longitude": 15.0032043457031,
      "Latitude": 60.7338905334473
    },
    "Name": "Leksand",
    "Id": 16
  },
  {
    "Position": {
      "Longitude": 14.5049390792847,
      "Latitude": 60.958568572998
    },
    "Name": "Mora (Mora-Siljan flygplats)",
    "Id": 17
  },
  {
    "Position": {
      "Longitude": 15.5104637145996,
      "Latitude": 60.4233436584473
    },
    "Name": "Borlänge (Dala Airport)",
    "Id": 18
  },
  {
    "Position": {
      "Longitude": 15.2551183700562,
      "Latitude": 54.5259628295898
    },
    "Name": "WEQWEQWEQWE",
    "Id": 8133
  }
]
```

Get all the POIs of the organization owning the API key in a specific language.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/poi`

### Query Parameters

Parameter | Description
--------- | -----------
Accept-Language | The language.

## Search POIs

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/poi/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/poi/search/{search}",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US"
  }  
});
```

> Example of response:

```json
[
  {
    "Position": {
      "Longitude": 15.5104637145996,
      "Latitude": 60.4233436584473
    },
    "Name": "Borlänge (Dala Airport)",
    "Id": 18
  }
]
```

Search POIs, and return the matching ones.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/poi/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string to look for.
Accept-Language | The language.

## POIs in use

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	"Search":"Ewok"
  }'	 
  'https://cbis-rest-api.citybreak.com/v1/api/poi/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/poi/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	 Search: "Ewok"
  })
});
```

> Example of response:

```json
[
  {
    "Id": 17,
    "Name": "Mora (Mora-Siljan flygplats)",
    "References": 2
  },
  {
    "Id": 18,
    "Name": "Borlänge (Dala Airport)",
    "References": 0
  },
  {
    "Id": 8133,
    "Name": "WEQWEQWEQWE",
    "References": 1
  },
]
```

Filters products matching the supplied filter and return the POIs with a counter of references, telling how many products matching the filter are using the POI.
The filter is passed through the body part of the request.
You can supply an empty filter to get all the POIs and the number of products using each one.

### HTTP Request

`POST https://cbis-rest-api.citybreak.com/v1/api/poi/product`

### Query Parameters

Parameter | Description
--------- | -----------
filter | The <a href="https://visit.github.io/api-doc/#filter">product filter</a>.
Accept-Language | The language.