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

Possible types are:

* String
* Integer
* Boolean
* Double
* DateTime

## Get Attribute

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/{id}",
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

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | The attribute id.

## Get Paged

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getpaged/{pageSize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getpaged/{pageSize}",
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

Get a page of raw attributes.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getpaged/{pageSize}`

### Query Parameters

Parameter | Description
--------- | -----------
pageSize | Should be a page size lower than 50 and greater than 0.


<aside class="notice">
Use the <a href="https://visit.github.io/api-doc/#continue">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Continue

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getnext/{continueToken}",
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

Get the next page of raw attributes, you need to provide a token obtained from <a href="https://visit.github.io/api-doc/#get-paged">Get Paged</a>.
Tokens are valid for 1 minute, extended for aonother minute each time you use it.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | A token to retrieve the next page.


<aside class="notice">
Use the <a href="https://visit.github.io/api-doc/#continue">ContinueToken</a> to grab the next page until you get an <b>empty</b> result set.
</aside>

## Search Attributes

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/search/{search}",
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