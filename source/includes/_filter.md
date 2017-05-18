# Filter

> Filter

```json
{
  "Sort": {},
  "Page": 0,
  "PageSize": 0,
  "Fields": [],
  "Relations": {},
  "Search": "",
  "Position": {},
  "GeoBox": {},
  "ProductIds": [],
  "Categories": [],
  "Geos": [],
  "Pois": [],
  "Occasions": {},
  "Information": {},
  "PublishAt": {},
  "ExpiresAt": {}
}
```

Filter used to query products.

<aside class="notice">
<code>Sort</code>, <code>Page</code>, <code>PageSize</code> and <code>Fields</code> are only used when querying for products or arenas.
</aside>

## Categories, Geonodes, Pois

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "Categories": [
		123, 124
	  ],
	  "Geos": [
	  	123, 124
	   ],
	  "Pois": [
		123, 124
	  ]
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Categories": [
		123, 124
	  ],
	  "Geos": [
	  	123, 124
	   ],
	  "Pois": [
		123, 124
	  ]
  })
});
```

Categories, Geonodes and Pois are list of integers. The example query can be translated to products (in category 123 **OR** 124) **AND** (in geonode 123 **OR** 124) **AND** (in poi 123 **OR** 124).

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
Categories | int[] | List of categories Ids.
Geos | int[] | List of geonodes Ids.
Pois | int[] | List of pois Ids.

## Expires and Publish

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "PublishAt": {
	    "After": "2016-09-08T07:09:44.042Z",
		"Before": "2016-09-08T07:09:44.042Z"
	  },
	  "ExpiresAt": {
	    "After": "2016-09-08T07:09:44.042Z",
		"Before": "2016-09-08T07:09:44.042Z"
	  }
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Publish": {
	    "After": "2016-09-08T07:09:44.042Z",
		"Before": "2016-09-08T07:09:44.042Z"
	  },
	  "Expires": {
	    "After": "2016-09-08T07:09:44.042Z",
		"Before": "2016-09-08T07:09:44.042Z"
	  }
  })
});
```

Allow you to override the default filters on `ExpiresAt` and `PublishAt`.
If not supplied, the default value will be `"PublishAt": {"After": "NOW"}`, and `"ExpiresAt": {"After": "NOW"}`.

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
Before | DateTime | Before which date.
After | DateTime | After which date.


## Search in Name

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "Search": "string"
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Search": "string"
  })
});
```

Shorthand to search in products name.

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
Search | string | String you are looking for, handles typos.

## Position

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "Position": {
		"Latitude": 0,
		"Longitude": 0,
		"Distance": 0
	  }
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Position": {
		"Latitude": 0,
		"Longitude": 0,
		"Distance": 0
	  }
  })
});
```

Filter products by their position. You need to supply a reference point and a `Distance` (radius in Km).

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
Latitude | double | Latitude of reference point.
Longitude | double | Longitude of reference point.
Distance | int | Distance from reference point (km).

## GeoBox

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "GeoBox": {
		"TopLeftLat": 0,
		"TopLeftLng": 0,
		"BottomRightLat": 0,
		"BottomRightLng": 0
	  }
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "GeoBox": {
		"TopLeftLat": 0,
		"TopLeftLng": 0,
		"BottomRightLat": 0,
		"BottomRightLng": 0
	  }
  })
});
```

Filter products by their position. You need to supply the coordinates of the top left point and the bottom right one.
Products included in the geographic box will be returned.

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
TopLeftLat | double | Latitude of the top left point.
TopLeftLng | double | Longitude of the top left point.
BottomRightLat | double | Latitude of the bottom right point.
BottomRightLng | double | Longitude of the bottom right point.

## ProductIds

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "ProductIds": [
		"cbis:123456", "cbis:987654"
	  ]
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "ProductIds": [
		"cbis:123456", "cbis:987654"
	  ]
  })
});
```

Only return the products matching the ids supplied in `ProductIds`.

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
ProductIds | string[] | The productIds.

## Occasions

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "Occasions": {
            "After": "2016-09-08T07:09:44.042Z",
            "Before": "2016-09-08T07:09:44.042Z",
            "ArenaIds": [
              "cbis:12345"
            ]
	   }
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Occasion": {
            "After": "2016-09-08T07:09:44.042Z",
            "Before": "2016-09-08T07:09:44.042Z",
            "ArenaIds": [
              "cbis:12345"
            ]
	   }
  })
});
```

Filter products by their occasions. Supply the fields you need.

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
After | DateTime | Occasion is after this date.
Before | DateTime | Occasion is after this date.
ArenaIds | string[] | Occasion occurs in one of the arenas.


## Information

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "Information": {
		"Operator": "AND",
		"Queries": [
		  {
			"Id": 0,
			"Type": "Value",
			"Value": "string",
			"SubQuery": {
				"Operator": "OR",
				"Queries": [
				   {
					  "Id": 100059,
					  "Type": "Value",
					  "Value": "true"
				  },
				"SubQuery": {}
			}
		  }
		]
	  }
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Information": {
		"Operator": "AND",
		"Queries": [
		  {
			"Id": 0,
			"Type": "Value",
			"Value": "string",
			"SubQuery": {
				"Operator": "OR",
				"Queries": [
				   {
					  "Id": 100059,
					  "Type": "Value",
					  "Value": "true"
				  },
				"SubQuery": {}
			}
		  }
		]
	  }
  })
});
```

Filter products by the content of the Information they carry, by having an attribute or not having.

### Operator

* AND
* OR

### MatchType

* Value (exact match, requires `Value`)
* Fuzzy (approx match, requires `Value`)
* Range (mathematical range, requires `Value`: \[1:10\], \]1;10\[, >3, <10 etc...)
* Has (has the attribute)
* Hasnt (has not the attribute)

### Information & SubQuery objects

Parameter | Type | Description
--------- | ---- | -----------
Operator | Operator | The operator to apply between the queries.
Queries | Query[] | A list of query.

### Query object

Parameter | Type | Description
--------- | ---- | -----------
Id | int | Attribute Id.
Type | MatchType | See above.
Value | string | The value.
SubQuery | SubQuery | See above.


## Relations

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "Relations": {
		"Operator": "AND",
		"Queries": [
		  {
			"Type": "Has",
			"RelationType": "Parent",
			"Filter": {
			},
			"SubQuery": {
				"Operator": "AND",
				"Queries": [
				  {
					"Type": "Value",
					"RelationType": "None",
					"Filter": {
						"Occasion": {
							"After": "2016-09-08T07:09:44.042Z",
							"Before": "2016-09-08T07:09:44.042Z",
							"ArenaIds": [
							  "cbis:12345"
							]
					   }
					},
					"SubQuery": {}	
				  }
				]
		    }
		  }	
	  }
    ]
  }'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Relations": {
		"Operator": "AND",
		"Queries": [
		  {
			"Type": "Has",
			"RelationType": "Parent",
			"Filter": {
			},
			"SubQuery": {
				"Operator": "AND",
				"Queries": [
				  {
					"Type": "Value",
					"RelationType": "None",
					"Filter": {
						"Occasion": {
							"After": "2016-09-08T07:09:44.042Z",
							"Before": "2016-09-08T07:09:44.042Z",
							"ArenaIds": [
							  "cbis:12345"
							]
					   }
					},
					"SubQuery": {}	
				  }
				]
		    }
		  }	
	  }
  })
});
```

Filter products by the products related to the product, apply filters to related products.

### Operator

* AND
* OR

### MatchType

* Value (relation match the filter)
* Has (has the relation)
* Hasnt (has not the relation)

### RelationType

* Child 
* Parent
* None (products matching filter in subqueries)

### Relations & SubQuery objects

Parameter | Type | Description
--------- | ---- | -----------
Operator | Operator | The operator to apply between the queries.
Queries | Query[] | A list of query.

### Query object

Parameter | Type | Description
--------- | ---- | -----------
Type | MatchType | See above.
RelationType | RelationType | See above.
Filter | Filter | The <a href="https://visit.github.io/api-doc/#filter">product filter</a>.
SubQuery | SubQuery | See above.

## Fields

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "Fields": ["Id", "Name"]
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Fields": ["Id", "Name"]
  })
});
```

Only populate a subset of fields.

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
Fields | string[] | Name of the fields you want populated, required if pagesize >= 50.

## Sorting & Paging

```shell
curl -X POST 
  --header 'ApiKey: APIKEY132456789EWOK'
  --header 'Accept: application/json' 
  --header 'Accept-Language: en-US'
  --header 'Content-Type: application/json'
  -d '{
	  "Page": 0,
	  "PageSize": 20,
	  "Sort": {
		"Field": "Name",
		"Order": "Asc"
	  },
	}'	 
  'https://cbis-rest-api.citybreak.com/v1/api/product'
```

```javascript
var r = fetch("https://cbis-rest-api.citybreak.com/v1/api/product",
{
  method: "POST",
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	"Accept-Language": "en-US",
	"Content-Type": "application/json"
  },
  body: JSON.stringify({
	  "Page": 0,
	  "PageSize": 20,
	  "Sort": {
		"Field": "Name",
		"Order": "Asc"
	  },
  })
});
```

Order products by the supplied field.
Supported fields are:

* Name 
* Id 
* ExpiresAt 
* PublishAt
* ProductIds (follow order from array of ids in ProductIds field) 
* Occasions
* Information (need to supply AttributeId)
* Position (need to supply Latitude & Longitude)

### Sort Object

Parameter | Type | Description
--------- | ---- | -----------
Field | string | Name of the field you want to order by.
Order | Order | Either `Asc` or `Desc`
AttributeId | int | The attribute id of the information field you want to sort on
Latitude | double | The latitude of the reference point to sort on position
Longitude | double | The longitude of the reference point to sort on position

### Paging
Parameter | Type | Description
--------- | ---- | -----------
Page | int | The page, starting at 0.
PageSize | int | The size of the page.