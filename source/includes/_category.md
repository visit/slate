# Category

> Category 

```json
{
  "Children": [],
  "Id": 83745,
  "Name": "Gothenburg"
}
```

Localized version of the category tree for the organization owning the API key.

<aside class="notice">
The header <code>Accept-Language</code> is used to know which language to query. It uses <a href="https://msdn.microsoft.com/en-us/library/ee825488(v=cs.20).aspx">CultureInfo code</a>.
</aside>

## Get Category Tree

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/category'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/category",
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
          "Children": [
            {
              "Children": [],
              "Id": 26218,
              "Name": "Hotel"
            }
          ],
          "Id": 26219,
          "Name": "B&B"
        },
        {
          "Children": [],
          "Id": 26217,
          "Name": "Husvagnscamping"
        },
        {
          "Children": [
            {
              "Children": [],
              "Id": 30610,
              "Name": "Test"
            }
          ],
          "Id": 26220,
          "Name": "vandrarhem"
        }
      ],
      "Id": 26210,
      "Name": "Accommodation"
    },
    {
      "Children": [
        {
          "Children": [
            {
              "Children": [],
              "Id": 32541,
              "Name": "Grill"
            }
          ],
          "Id": 32540,
          "Name": "Activities"
        }
      ],
      "Id": 32538,
      "Name": "To-do"
    },
    {
      "Children": [],
      "Id": 30701,
      "Name": "Thibault"
    }
  ],
  "Id": 5946,
  "Name": "Visit Group"
}
```

Get the category tree in the specified language.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/category`

### Query Parameters

Parameter | Description
--------- | -----------
Accept-Language | The language.

## Search Categories

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/category/search/{search}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/category/search/{search}",
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
    "Id": 30701,
    "Name": "Thibault"
  }
]
```

Search categories, and return the matching ones.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/category/search/{search}`

### Query Parameters

Parameter | Description
--------- | -----------
search | The string to look for.
Accept-Language | The language.

## Categories in use

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	"Search":"Ewok"
  }'	 
  'https://cbis-rest-api.citybreak.com/v1/api/category/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/category/product",
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
          "Children": [
            {
              "Children": [],
              "References": 0,
              "Id": 26218,
              "Name": "Hotel"
            }
          ],
          "References": 0,
          "Id": 26219,
          "Name": "B&B"
        },
        {
          "Children": [],
          "References": 0,
          "Id": 26217,
          "Name": "Husvagnscamping"
        },
        {
          "Children": [
            {
              "Children": [],
              "References": 0,
              "Id": 30610,
              "Name": "Test"
            }
          ],
          "References": 0,
          "Id": 26220,
          "Name": "vandrarhem"
        }
      ],
      "References": 0,
      "Id": 26210,
      "Name": "Accommodation"
    },
    {
      "Children": [
        {
          "Children": [
            {
              "Children": [],
              "References": 0,
              "Id": 32541,
              "Name": "Grill"
            }
          ],
          "References": 0,
          "Id": 32540,
          "Name": "Activities"
        }
      ],
      "References": 0,
      "Id": 32538,
      "Name": "To-do"
    },
    {
      "Children": [],
      "References": 1,
      "Id": 30701,
      "Name": "Thibault"
    }
  ],
  "References": 1,
  "Id": 5946,
  "Name": "Visit Group"
}
```

Filters products matching the supplied filter and return the categories with a counter of references, telling how many products matching the filter are using the category.
The filter is passed through the body part of the request.
You can supply an empty filter to get the category tree and the number of products using each one.

### HTTP Request

`POST https://cbis-rest-api.citybreak.com/v1/api/category/product`

### Query Parameters

Parameter | Description
--------- | -----------
filter | The <a href="https://visit.github.io/api-doc/#filter">product filter</a>.
Accept-Language | The language.