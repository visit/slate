# Webhooks

We provide Webhooks (<a href="https://en.wikipedia.org/wiki/Webhook">Wikipedia</a>) for your API keys on demand. 
Contact our <a href="http://help.citybreak.com/">support</a> if you wish to use this option.

We support the following authentication methods:

 * Basic Authentication
 * Cusom Header Authentication
 * No authentication

We also handle automatic retries if your endpoint is unavailable.

```json
{
	"Key" : "APIKEY132456789EWOK",
	"HasLog" : true,
	"Attribute" : {
		"AffectedProducts" : ["cbis:355699", "cbis:1245084", "cbis:1268500", "cbis:1270889"],
		"Date" : "2016-11-03T12:38:09.7400589Z",
		"Changes" : {
			"99" : "Updated",
			"102727" : "Created",
			"102728" : "Deleted"
		}
	},
	"Cat" : null,
	"Geo" : null,
	"Poi" : null,
	"Product" : {
		"AffectedProducts" : ["cbis:355699", "cbis:1245084", "cbis:1268500", "cbis:1270889"],
		"Date" : "2016-11-03T12:38:08.1485162Z",
		"Changes" : {
			"cbis:355699" : "Created",
			"cbis:1245084" : "Created",
			"cbis:1268500" : "Created",
			"cbis:1270889" : "Created"
		}
	},
	"Arena" : null
}
```