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

If you don't have an API key, visit <a href="https://support.citybreak.com/">Citybreak Support</a> to get one.

CBIS REST API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Basic base64encode('username:APIKEY132456789EWOK')`

<aside class="notice">
You must replace <code>APIKEY132456789EWOK</code> with your personal API key.
</aside>
