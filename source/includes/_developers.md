# Developers
## Showing developer info

Allows you to view developer info such as Company name and ID which can be used in creating/updating an approval or updating permissions for a device.

```shell
curl -X GET "https://api.coposition.com/v1/developers/DEVELOPER_ID"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/v1/developers/DEVELOPER_ID',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "email": "orland@kulasrolfson.net",
  "company_name": "Fakebook",
  "tagline": null,
  "redirect_url": "http://kaulkerenner.biz/"
}
```
### HTTP Request
`GET https://api.coposition.com/v1/developers/DEVELOPER_ID`

List of all developers

`GET https://api.coposition.com/v1/developers`

### Headers

`X-Api-Key`
`Content-Type`
`Cache-Control`
