# Geo

> Geo 

```json
{
  "Children": [],
  "Id": 83745,
  "Name": "Gothenburg"
}
```

Localized version of the geos tree for the organization owning the API key.

<aside class="notice">
The header <code>Accept-Language</code> is used to know which language to query. It uses <a href="https://msdn.microsoft.com/en-us/library/ee825488(v=cs.20).aspx">CultureInfo code</a>.
</aside>

## Get Geo Tree

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/geo'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/geo",
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
  "Children": [
    {
      "Children": [
        {
          "Children": [],
          "Id": 83745,
          "Name": "Gothenburg"
        },
        {
          "Children": [],
          "Id": 105270,
          "Name": "Linköping"
        },
        {
          "Children": [],
          "Id": 104662,
          "Name": "Malmö"
        },
        {
          "Children": [],
          "Id": 94466,
          "Name": "Stockholm"
        }
      ],
      "Id": 105375,
      "Name": "Sweden"
    }
  ],
  "Id": 4852,
  "Name": "Visit Group"
}
```

Get the geo tree in the specified language.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/geo`

### Query Parameters

Parameter | Description
--------- | -----------
Accept-Language | The language.

## Search Geos

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/geo/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/geo/search/{search}",
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
    "Id": 83745,
    "Name": "Gothenburg"
  }
]
```

Search geos, and return the matching ones.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/geo/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string to look for.
Accept-Language | The language.

## Geos in use

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	"Search":"Ewok"
  }'	 
  'https://cbis-rest-api.citybreak.com/v1/api/geo/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/geo/product",
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
{
  "Children": [
    {
      "Children": [
        {
          "Children": [],
          "References": 1,
          "Id": 83745,
          "Name": "Gothenburg"
        },
        {
          "Children": [],
          "References": 0,
          "Id": 105270,
          "Name": "Linköping"
        },
        {
          "Children": [],
          "References": 0,
          "Id": 104662,
          "Name": "Malmö"
        },
        {
          "Children": [],
          "References": 1,
          "Id": 94466,
          "Name": "Stockholm"
        }
      ],
      "References": 2,
      "Id": 105375,
      "Name": "Sweden"
    }
  ],
  "References": 2,
  "Id": 4852,
  "Name": "Visit Group"
}
```

Filters products matching the supplied filter and return the geos with a counter of references, telling how many products matching the filter are using the geo.
The filter is passed through the body part of the request.
You can supply an empty filter to get the geo tree and the number of products using each one.

### HTTP Request

`POST https://cbis-rest-api.citybreak.com/v1/api/geo/product`

### Query Parameters

Parameter | Description
--------- | -----------
filter | The <a href="https://visit.github.io/api-doc/#filter">product filter</a>.
Accept-Language | The language.