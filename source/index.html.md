---
title: API Reference

language_tabs:
  - shell
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the CBIS REST API Reference.
If you don't have an API key, visit <a href='https://support.citybreak.com/'>Citybreak Support</a> to get one.

The API is divided into 2 parts, 'Raw' and 'Localized'. The first one is designed to get all the data we have about something, when the second one is designed to print data in real time.

# Authentication

> To authorize, you will need to use basic authentication.

```shell
curl --header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
```

```javascript
var r = fetch('https://cbis-rest-api.citybreak.com/v1/,
{
    headers: {
		'Authorization': 'Basic '+btoa('username:APIKEY132456789EWOK')
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

All the attributes in use in CBIS for the organization owning the APIKEY, with your own translations as well.

## Get Paged

```shell
curl -X GET 
--header 'Authorization: Basic dXNlcm5hbWU6QVBJS0VZMTMyNDU2Nzg5RVdPSw=='
--header 'Accept: application/json' 
'https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getPaged/50'
```

```javascript
var r = fetch('https://cbis-rest-api.citybreak.com/v1/api/raw/attribute/getPaged/50,
{
    headers: {
		'Authorization': 'Basic '+btoa('username:APIKEY132456789EWOK'),
		'Accept': 'application/json'
    }  
});
```

> The above command returns JSON structured like this:

```json
{
  "ContinueToken": "c2NhbjsxOzY3NzQ1NzUxOmp3dldQd215UU1Hc3p5NHVVTXZJMkE7MTt0b3RhbF9oaXRzOjI4NzQ7",
  "TotalResults": 2874,
  "Result": [
    {
      "Id": 100001,
      "Names": {
        "0": "Food/Fun",
        "1": "Mat & Nöje",
        "2": "Food/Fun",
        "3": "Food/Fun",
        "4": "Mad/Sjov",
        "5": "Mat og moro",
        "6": "Food/Fun",
        "9": "Food/Fun",
        "13": "Gastronomia/ Rozrywka",
        "21": "Food/Fun"
      },
      "Name": "foodnfun",
      "Type": "Boolean"
    },
    {
      "Id": 100002,
      "Names": {
        "0": "Sun/Beaches",
        "1": "Sol & Stränder",
        "2": "Sun/Beaches",
        "3": "Sun/Beaches",
        "5": "Sun/Beaches",
        "6": "Sun/Beaches",
        "9": "Sun/Beaches",
        "13": "Słońce/ plaża",
        "21": "Sunshine/Beaches"
      },
      "Name": "sunandbeaches",
      "Type": "Boolean"
    },
	...
  ]
}
```

Get a page of Raw Attributes.

### HTTP Request

`GET https://cbis-rest-api.citybreak.com/v1/raw/attribute/getpaged/{pageSize}`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
pageSize | none | Should be a page size lower than 50 and greater than 0.

<aside class="notice">
Use the ContinueToken to get the next page.
</aside>

## Continue

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

