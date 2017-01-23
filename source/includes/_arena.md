# Arena

> Arena 

```json
{
  "Relations": [],
  "RelationsContent": [],
  "Id": "cbis:1245084",
  "References": [
    "cbis:1245084"
  ],
  "Name": "Ewok",
  "Geos": [],
  "Categories": [
    {
	  "Path": [
	    {
		  "Id": 5946,
	      "Section": "Visit Group"
	    },
	    {
		  "Id": 30701,
		  "Section": "Thibault"
	    }
	  ]
    }
  ],
  "ExpiresAt": "2018-07-01T01:00:00",
  "PublishAt": "2000-01-01T00:00:00",
  "Information": [
    {
	  "Id": 101,
      "Name": "Introduction",
	  "Value": "Strongest animal ever, by far!",
	  "Type": "String"
    },
    {
	  "Id": 102,
	  "Name": "Description",
	  "Value": "Ewoks were a diminutive species of furry bipeds native to the forest moon of Endor. They were most notable for helping the Rebel Alliance defeat the forces of the Galactic Empire at the Battle of Endor, allowing the shield generator there to be destroyed, and in turn, the Death Star II.\r\n\r\nEwoks were individuals that stood about one meter tall; they used spears, slings, and knives as weapons; they also used hang gliders as vehicles. Although skilled in forest survival and the construction of primitive technology, the Ewoks had yet to progress past stone-level technology when discovered by the Empire. They were quick learners, however, when exposed to advanced technology with simple mechanical processes and concepts.",
	  "Type": "String"
    },
    {
	  "Id": 105,
	  "Name": "Entrance",
	  "Value": "In an animal? Really?",
	  "Type": "String"
    },
    {
	  "Id": 106,
	  "Name": "Price information",
	  "Value": "Priceless",
	  "Type": "String"
    }
  ],
  "Position": null,
  "Media": [
    {
	  "Name": null,
	  "Copyright": null,
	  "Description": null,
	  "Type": "MainImage",
	  "Url": "http://images.citybreak.com/image.aspx?ImageId=4161317"
    },
    {
	  "Name": null,
	  "Copyright": null,
	  "Description": null,
	  "Type": "Image",
	  "Url": "http://images.citybreak.com/image.aspx?ImageId=4223191"
    }
  ],
  "Occasions": [],
  "Pois": [],
  "Type": "Arena"
}
```

Localized version of a arena.

<aside class="notice">
The header <code>Accept-Language</code> is used to know which language to query. It uses <a href="https://msdn.microsoft.com/en-us/library/ee825488(v=cs.20).aspx">CultureInfo code</a>.
</aside>

## Get Arena

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/arena/{id}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/arena/{id}",
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
    "Relations": [],
    "RelationsContent": [],
    "Id": "cbis:1245084",
    "References": [
      "cbis:1245084"
    ],
    "Name": "Ewok",
    "Geos": [],
    "Categories": [
      {
        "Path": [
          {
            "Id": 5946,
            "Section": "Visit Group"
          },
          {
            "Id": 30701,
            "Section": "Thibault"
          }
        ]
      }
    ],
    "ExpiresAt": "2018-07-01T01:00:00",
    "PublishAt": "2000-01-01T00:00:00",
    "Information": [
      {
        "Id": 101,
        "Name": "Introduction",
        "Value": "Strongest animal ever, by far!",
        "Type": "String"
      },
      {
        "Id": 102,
        "Name": "Description",
        "Value": "Ewoks were a diminutive species of furry bipeds native to the forest moon of Endor. They were most notable for helping the Rebel Alliance defeat the forces of the Galactic Empire at the Battle of Endor, allowing the shield generator there to be destroyed, and in turn, the Death Star II.\r\n\r\nEwoks were individuals that stood about one meter tall; they used spears, slings, and knives as weapons; they also used hang gliders as vehicles. Although skilled in forest survival and the construction of primitive technology, the Ewoks had yet to progress past stone-level technology when discovered by the Empire. They were quick learners, however, when exposed to advanced technology with simple mechanical processes and concepts.",
        "Type": "String"
      },
      {
        "Id": 105,
        "Name": "Entrance",
        "Value": "In an animal? Really?",
        "Type": "String"
      },
      {
        "Id": 106,
        "Name": "Price information",
        "Value": "Priceless",
        "Type": "String"
      }
    ],
    "Position": null,
    "Media": [
      {
        "Name": null,
        "Copyright": null,
        "Description": null,
        "Type": "MainImage",
        "Url": "http://images.citybreak.com/image.aspx?ImageId=4161317"
      },
      {
        "Name": null,
        "Copyright": null,
        "Description": null,
        "Type": "Image",
        "Url": "http://images.citybreak.com/image.aspx?ImageId=4223191"
      }
    ],
    "Occasions": [],
    "Pois": [],
    "Type": "Arena"
  }
]
```

Search for arenas responding to the id supplied, might be more than 1.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/arena/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | The id you are looking for.
Accept-Language | The language.

## Get paged

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/arena/getpaged/{pagesize}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/arena/getpaged/{pagesize}",
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
  "ContinueToken": "c2NhbjswOzE7dG90YWxfaGl0czozOw==",
  "TotalResults": 3,
  "Result": [
    {
      "Arena"
    },
    {
	  "Arena"
	},
	{
	  "Arena"
    }
  ]
}
```

Get a page of localized arena, and a token to fetch the next page.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/arena/getpaged/{pagesize}`

### Query Parameters

Parameter | Description
--------- | -----------
pagesize | Should be a page size lower than 50 and greater than 0.
Accept-Language | The language.

## Continue

```shell
curl -X GET 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  'https://cbis-rest-api.citybreak.com/v1/api/arena/getnext/{continueToken}'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/arena/getnext/{continueToken}",
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
  "ContinueToken": "c2NhbjswOzE7dG90YWxfaGl0czozOw==",
  "TotalResults": 3,
  "Result": [
    {
      "Arena"
    },
    {
	  "Arena"
	},
	{
	  "Arena"
    }
  ]
}
```

Get a page of localized arena, and a token to fetch the next page.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/api/arena/getnext/{continueToken}`

### Query Parameters

Parameter | Description
--------- | -----------
continueToken | The token obtained from a getpaged request.
Accept-Language | The language.

## Filter Arenas

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	"Search":"Ewok",
	"Page": 0,
	"PageSize": 10
  }'	 
  'https://cbis-rest-api.citybreak.com/v1/api/arena'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/arena",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	 Search: "Ewok",
	 "Page": 0,
	 "PageSize": 10
  })
});
```

> Example of response:

```json
{
  "Page": 0,
  "PageSize": 10,
  "TotalResults": 1,
  "Result": [
    {
      "Relations": [],
      "RelationsContent": [],
      "Id": "cbis:1245084",
      "References": [
        "cbis:1245084"
      ],
      "Name": "Ewok",
      "Geos": [],
      "Categories": [
        {
          "Path": [
            {
              "Id": 5946,
              "Section": "Visit Group"
            },
            {
              "Id": 30701,
              "Section": "Thibault"
            }
          ]
        }
      ],
      "ExpiresAt": "2018-07-01T01:00:00",
      "PublishAt": "2000-01-01T00:00:00",
      "Information": [
        {
          "Id": 101,
          "Name": "Introduction",
          "Value": "Strongest animal ever, by far!",
          "Type": "String"
        },
        {
          "Id": 102,
          "Name": "Description",
          "Value": "Ewoks were a diminutive species of furry bipeds native to the forest moon of Endor. They were most notable for helping the Rebel Alliance defeat the forces of the Galactic Empire at the Battle of Endor, allowing the shield generator there to be destroyed, and in turn, the Death Star II.\r\n\r\nEwoks were individuals that stood about one meter tall; they used spears, slings, and knives as weapons; they also used hang gliders as vehicles. Although skilled in forest survival and the construction of primitive technology, the Ewoks had yet to progress past stone-level technology when discovered by the Empire. They were quick learners, however, when exposed to advanced technology with simple mechanical processes and concepts.",
          "Type": "String"
        },
        {
          "Id": 105,
          "Name": "Entrance",
          "Value": "In an animal? Really?",
          "Type": "String"
        },
        {
          "Id": 106,
          "Name": "Price information",
          "Value": "Priceless",
          "Type": "String"
        }
      ],
      "Position": null,
      "Media": [
        {
          "Name": null,
          "Copyright": null,
          "Description": null,
          "Type": "MainImage",
          "Url": "http://images.citybreak.com/image.aspx?ImageId=4161317"
        },
        {
          "Name": null,
          "Copyright": null,
          "Description": null,
          "Type": "Image",
          "Url": "http://images.citybreak.com/image.aspx?ImageId=4223191"
        }
      ],
      "Occasions": [],
      "Pois": [],
      "Type": "Arena"
    }
  ]
}
```

Filter arenas using a filter, see <a href="https://visit.github.io/api-doc/#filter">POST Fitler</a> for more information about it.

### HTTP Request

`POST https://cbis-rest-api.citybreak.com/v1/api/arena`

### Query Parameters

Parameter | Description
--------- | -----------
filter | The <a href="https://visit.github.io/api-doc/#filter">filter</a>.
Accept-Language | The language.