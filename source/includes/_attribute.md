# Attribute

> Attribute 

```json
{
  "Id": 102,
  "Name": "Description",
  "Type": "String"
}
```

Localized version of the attributes for the organization owning the API key.

<aside class="notice">
The header <code>Accept-Language</code> is used to know which language to query. It uses <a href="https://msdn.microsoft.com/en-us/library/ee825488(v=cs.20).aspx">CultureInfo code</a>.
</aside>

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
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/attribute/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/attribute/{id}",
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
  "Id": 102,
  "Name": "Description",
  "Type": "String"
}
```

Get a specific attribute in the specified language.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/attribute/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | The attribute id.
Accept-Language | The language.

## Get Attributes

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/attribute'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/attribute",
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
    "Id": 99,
    "Name": "Name",
    "Type": "String"
  },
  {
    "Id": 101,
    "Name": "Introduction",
    "Type": "String"
  },
  {
    "Id": 102,
    "Name": "Description",
    "Type": "String"
  },
  {
    "Id": 103,
    "Name": "Directions",
    "Type": "String"
  },
  {
    "Id": 104,
    "Name": "Opening hours",
    "Type": "String"
  }
]
```

Get all the attributes of the organization owning the API key in a specific language.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/attribute`

### Query Parameters

Parameter | Description
--------- | -----------
Accept-Language | The language.

## Search Attributes

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/attribute/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/attribute/search/{search}",
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
    "Id": 102569,
    "Name": "Lots with drain for waste water",
    "Type": "Boolean"
  },
  {
    "Id": 100600,
    "Name": "À la carte",
    "Type": "Boolean"
  },
  {
    "Id": 100215,
    "Name": "Cable TV",
    "Type": "Boolean"
  }
]
```

Search attributes, and return the matching ones.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/attribute/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string to look for.
Accept-Language | The language.

## Attributes in use

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	"Search":"Ewok"
  }'	 
  'https://cbis-rest-api.citybreak.com/v1/api/attribute/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/attribute/product",
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
    "Id": 101,
    "Name": "Introduction",
    "References": 1
  },
  {
    "Id": 102,
    "Name": "Description",
    "References": 1
  },
  {
    "Id": 103,
    "Name": "Directions",
    "References": 0
  },
  {
    "Id": 104,
    "Name": "Opening hours",
    "References": 0
  },
  {
    "Id": 105,
    "Name": "Entrence",
    "References": 1
  },
  {
    "Id": 106,
    "Name": "Price information",
    "References": 1
  },
  {
    "Id": 107,
    "Name": "Phone number",
    "References": 0
  }
]
```

Filters products matching the supplied filter and return the attributes with a counter of references, telling how many products matching the filter are using the attribute.
The filter is passed through the body part of the request.
You can supply an empty filter to get all the attributes and the number of products using each one.

### HTTP Request

`POST https://cbis-rest-api.citybreak.com/v1/api/attribute/product`

### Query Parameters

Parameter | Description
--------- | -----------
filter | The <a href="https://visit.github.io/api-doc/#filter">product filter</a>.
Accept-Language | The language.