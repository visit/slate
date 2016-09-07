---
title: CBIS API Reference

language_tabs:
  - shell
  - javascript

toc_footers:
  - <a href='https://support.citybreak.com/'>Citybreak Support</a> 
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the CBIS REST API Reference.
If you don't have an API key, visit <a href='https://support.citybreak.com/'>Citybreak Support</a> to get one.

The API is divided into 2 parts, **raw** and **Localized**. The first one is designed to get all the data we have about something, when the second one is designed to print data in real time.

# Authentication

> To authorize, you will need to use basic authentication.

```shell
curl --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api",
{
    headers: {
		"Authorization": "Basic " + btoa("username:APIKEY132456789EWOK")
    }
});
```
> Make sure to replace `APIKEY132456789EWOK` with your API key.

If you don't have an API key, visit <a href='https://support.citybreak.com/'>Citybreak Support</a> to get one.

CBIS REST API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Basic base64encode(APIKEY132456789EWOK)`

<aside class="notice">
You must replace <code>APIKEY132456789EWOK</code> with your personal API key.
</aside>

# Raw Attribute

> Raw Attribute 

```json
{
  "Id": 102,
  "Translations": {
    "sv-SE": "Beskrivning",
    "en-US": "Description"
  },
  "Name": "Description",
  "Type": "String"
}
```

All the attributes in use in CBIS for the organization owning the API key, with your own translations as well.

## Get Attribute

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/{id}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
{
  "Id": 102,
  "Translations": {
    "sv-SE": "Beskrivning",
    "en-US": "Description",
    "de-DE": "Beschreibung",
    "da-DK": "Beskrivelse",
    "nb-NO": "Description",
    "fr-FR": "Description",
    "es-ES": "Description",
    "fi-FI": "Kuvaus",
    "pl-PL": "Opis",
    "en-GB": "Description"
  },
  "Name": "Description",
  "Type": "String"
}
```

Get a specific attribute and all its translations.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/raw/attribute/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | The attribute id.

## Get Paged

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getpaged/{pageSize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getpaged/{pageSize}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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

Get a page of raw attributes.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getpaged/{pageSize}`

### Query Parameters

Parameter | Description
--------- | -----------
pageSize | Should be a page size lower than 50 and greater than 0.


<aside class="notice">
Use the <a href="https://bqk-.github.io/slate/#continue">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Continue

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getnext/{continueToken}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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

Get the next page of raw attributes, you need to provide a token obtained from <a href="https://bqk-.github.io/slate/#get-paged">Get Paged</a>.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | A token to retrieve the next page.


<aside class="notice">
Use the <a href="https://bqk-.github.io/slate/#continue">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Search Attributes

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/search/{search}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
[
  {
    "Id": 100691,
    "Translations": {
      "sv-SE": "Pentry/Kokvrå",
      "en-US": "Kitchenette"
    },
    "Name": "PentryKokvra",
    "Type": "Boolean"
  },
  {
    "Id": 100265,
    "Translations": {
      "sv-SE": "Pentry",
      "en-US": "Kitchenette"
    },
    "Name": "pentry",
    "Type": "Boolean"
  }
]
```

Search for a match or more in attributes translations.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string you are looking for.











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
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/poi/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/poi/{id}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getpaged/{pageSize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getpaged/{pageSize}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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
Use the <a href="https://bqk-.github.io/slate/#continue10">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Continue

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/poi/getnext/{continueToken}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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

Get the next page of raw POIs, you need to provide a token obtained from <a href="https://bqk-.github.io/slate/#get-paged9">Get Paged</a>.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/raw/poi/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | A token to retrieve the next page.


<aside class="notice">
Use the <a href="https://bqk-.github.io/slate/#continue10">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Search POIs

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/poi/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/poi/search/{search}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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

`GET https://cbis-rest-api.citybreak.com/v1/raw/poi/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string you are looking for.











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
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/geo/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/geo/{id}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getpaged/{pageSize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getpaged/{pageSize}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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
Use the <a href="https://bqk-.github.io/slate/#continue15">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Continue

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/geo/getnext/{continueToken}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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

Get the next page of raw geos, you need to provide a token obtained from <a href="https://bqk-.github.io/slate/#get-paged14">Get Paged</a>.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/raw/geo/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | A token to retrieve the next page.


<aside class="notice">
Use the <a href="https://bqk-.github.io/slate/#continue15">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Search Geos

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/geo/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/geo/search/{search}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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

`GET https://cbis-rest-api.citybreak.com/v1/raw/geo/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string you are looking for.











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
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/category/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/category/{id}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/category/getpaged/{pageSize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/category/getpaged/{pageSize}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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
Use the <a href="https://bqk-.github.io/slate/#continue20">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Continue

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/category/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/category/getnext/{continueToken}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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

Get the next page of raw categories, you need to provide a token obtained from <a href="https://bqk-.github.io/slate/#get-paged19">Get Paged</a>.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/raw/category/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | A token to retrieve the next page.


<aside class="notice">
Use the <a href="https://bqk-.github.io/slate/#continue20">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Search Categories

```shell
curl -X GET 
  --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/category/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/category/search/{search}",
{
  headers: {
    "Authorization": "Basic " + btoa("username:APIKEY132456789EWOK"),
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

`GET https://cbis-rest-api.citybreak.com/v1/raw/category/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string you are looking for.